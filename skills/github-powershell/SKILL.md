---
name: github-powershell
description: Handles all GitHub repository file edits, commits, and pushes. Use this skill whenever Morgan needs to edit, update, add, or push files to a GitHub repository — including HTML edits, find-replace across files, footer/header injection, mass updates, or any repo commit task. Trigger on: "push to GitHub," "update the repo," "commit this," "add to the site," "edit the HTML on GitHub," or any task that requires modifying files in a GitHub repository. Always use this skill before writing any GitHub-related commands.
---

# GitHub Commit Skill

## CRITICAL: How Claude's Environment Works

**`api.github.com` is BLOCKED in Claude's container.** Do not attempt to use the GitHub REST API directly — it will always return 403. Do not waste time trying curl, Python urllib, or any HTTP client against api.github.com. It will never work.

**The correct approach from Claude's container is always git clone + edit + push.** This works because `github.com` (the git protocol over HTTPS) IS on the allowlist.

**Python IS available** in Claude's bash environment. Use it for file editing (string replacements, regex patches, etc.). The "Python not available" note below applies only to Morgan's local Windows machine.

---

## Claude's Container Workflow (DEFAULT — always use this first)

### Step 1: Clone the repo

```bash
git clone https://TOKEN@github.com/USER/REPO.git /tmp/repo
```

### Step 2: Edit the file with Python

```python
# Write a patch script at /tmp/patch.py
with open('/tmp/repo/path/to/file.html', 'r') as f:
    content = f.read()

# Use string replace — assert before replacing to catch mismatches early
old = 'exact string to find'
new = 'replacement string'
assert old in content, f"String not found: {old[:60]}"
content = content.replace(old, new)

with open('/tmp/repo/path/to/file.html', 'w') as f:
    f.write(content)

print("Done.")
```

Run it:
```bash
python3 /tmp/patch.py
```

### Step 3: Commit and push

```bash
cd /tmp/repo
git config user.email "morgan@messickmarketing.com"
git config user.name "Morgan"
git add -A
git commit -m "Your commit message"
git push origin main
```

That's it. All three steps together take under 30 seconds.

---

## Token Rules

Two tokens in play — use the correct one:

| Repo | Token to use |
|---|---|
| `virtueasyproducts-cmd/*` | virtueasyproducts-cmd **org token** |
| `morgomess/messick-marketing` | Personal account token |

Morgan will provide the token for the session. Never hardcode or assume a token — ask if not provided.

---

## Morgan's Local PowerShell Workflow (only for when Morgan runs commands herself)

This is for Morgan running commands locally on her Windows machine — NOT for Claude's container.

**Python is NOT available on Morgan's machine.** Use pure PowerShell.

### Step 1: Get the current file (to obtain SHA)

```powershell
$TOKEN = "YOUR_TOKEN_HERE"
$REPO = "org-or-user/repo-name"
$FILE = "path/to/file.html"
$HEADERS = @{
    Authorization = "token $TOKEN"
    "User-Agent"  = "PowerShell"
}

$RAW = Invoke-RestMethod `
    -Uri "https://api.github.com/repos/$REPO/contents/$FILE" `
    -Headers $HEADERS

$SHA = $RAW.sha
# Strip whitespace before decoding base64
$CONTENT = [System.Text.Encoding]::UTF8.GetString(
    [System.Convert]::FromBase64String(($RAW.content -replace '\s',''))
)
```

### Step 2: Make edits in PowerShell

```powershell
$UPDATED = $CONTENT -replace 'old string', 'new string'

# For multiline replacements, use here-strings:
$FOOTER = @'
<footer class="site-footer">
  ...footer content...
</footer>
'@
$UPDATED = $CONTENT -replace '</body>', "$FOOTER`n</body>"
```

### Step 3: Encode and commit

```powershell
$ENCODED = [System.Convert]::ToBase64String(
    [System.Text.Encoding]::UTF8.GetBytes($UPDATED)
)

$BODY = @{
    message = "Your commit message here"
    content = $ENCODED
    sha     = $SHA
    branch  = "main"
} | ConvertTo-Json

Invoke-RestMethod `
    -Uri "https://api.github.com/repos/$REPO/contents/$FILE" `
    -Method PUT `
    -Headers $HEADERS `
    -Body $BODY `
    -ContentType "application/json"
```

---

## Common Repos

| Repo | Purpose |
|---|---|
| `virtueasyproducts-cmd/virtueasyproducts-cmd.github.io` | Virtueasy main site |
| `virtueasyproducts-cmd/workbook` | Vercel proxy / AI generation |
| `morgomess/messick-marketing` | Messick Marketing site and tools |

---

## Error Checklist

**If git clone fails:** Check the token is correct and has repo write access.

**If python3 patch fails:** The assert will tell you exactly which string wasn't found. Check for whitespace differences or look at the actual line with `grep -n`.

**If git push fails:** Re-clone to get a fresh copy — someone may have pushed in the meantime.

**If on Morgan's local machine (PowerShell REST API):**
1. Confirm SHA is fresh — re-fetch if any time has passed since the initial GET
2. Confirm whitespace is stripped from base64: `($RAW.content -replace '\s','')`
3. Confirm correct token for the repo (org vs. personal)
4. Confirm branch is `main` not `master`
5. Confirm Content-Type is set to `application/json`
