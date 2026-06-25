---
name: remotion-workflow
description: Handles Remotion (programmatic React video) work on Morgan's Windows machine via Claude Code, for motion graphics exported into CapCut for Messick Marketing and Virtueasy. Use whenever Morgan is setting up Remotion, previewing a composition, rendering output (especially transparent ProRes for CapCut), or troubleshooting the Remotion + Claude Code + PowerShell workflow. Trigger on: "Remotion," "remotion studio," "render this composition," "transparent video for CapCut," "motion graphic," "lower third," "preview the animation," or any Remotion project task. Always load this before giving Remotion setup or render commands - it contains the Windows-specific gotchas that otherwise get rediscovered every session.
---

# Remotion + Claude Code Workflow (Windows)

Morgan builds motion graphics with Remotion, scaffolded and edited via Claude Code, then exports to CapCut. Machine is Windows; commands run in PowerShell or the Claude Code desktop app. **Python is NOT available on Morgan's machine** - use pure PowerShell for any scripting.

---

## Hard-won gotchas (read first - these waste the most time)

- **Paste commands ONE AT A TIME.** Pasting multiple lines at once causes the next command (e.g. `cd ...`) to be swallowed as the answer to npm's `Ok to proceed? (y)` prompt, which cancels the install. One line, enter, wait.
- **Run `npm install` from inside the project folder, not the parent.** Running it from `C:\Users\morga` instead of the project dir is a recurring error. Always `cd` into the project first.
- **Open the project SUBFOLDER in Claude Code desktop, not the parent.** The Remotion skill is only detected when the actual project folder (e.g. `my-motion-graphics`) is open, not its container.
- **`npx remotion studio` before `npm install` fails.** Dependencies must be installed first.

---

## One-time setup (already done once; reference if setting up a new machine or project)

Standard install follows remotion.dev. The Windows-specific break is the skills installer:

1. **`npx remotion skills add` fails with `spawn EINVAL`** - a known Windows/Node security restriction. Do not retry it.
2. Use the direct form instead: `npx skills add remotion-dev/skills`
3. If that still fails to write project-scoped files, manual workaround:
   ```
   git clone https://github.com/remotion-dev/skills.git temp-skills
   ```
   then create the target dir, `xcopy` the rule files into `.claude\skills\remotion-best-practices\`, then `rmdir` the temp clone.
4. Success state: 37 rule files installed at `.claude\skills\remotion-best-practices\`, including `transparent-videos.md`.

cmd/PowerShell is only needed for this one-time setup. Daily use runs through the Claude Code desktop app, which can run `npm run dev` and render commands itself.

---

## Daily preview workflow (fastest path)

```powershell
cd <path-to-project>
npx remotion studio
```

Launches the live editor at `localhost:3000` in ~10 seconds. That's the whole workflow after a reboot - no need to reopen Claude Code just to preview.

**If the project path is unknown**, locate it from PowerShell:
```powershell
Get-ChildItem -Recurse -Filter "<project-name>" -Directory
```

Projects have lived in a few places (`...\Desktop\Claude Code Projects\`, `...\Downloads\`), so don't assume one fixed location - search if unsure.

---

## Rendering

**Transparent overlay for CapCut (lower-thirds, title cards) - ProRes 4444 with alpha:**
```powershell
npx remotion render <CompositionId> out/<filename>.mov --codec=prores --prores-profile=4444
```

**Standard video (mp4, h264):**
```powershell
npx remotion render <CompositionId> out/<filename>.mp4
```

Output lands in the project's `out/` folder.

---

## Conventions

- **Versioned output filenames:** v2, v3, etc. Morgan iterates by targeted edits/diffs against the prior version, not full rewrites - frame work as a diff list when prompting Claude Code.
- **Output folder:** `out/`
- **Brand specs carry into compositions:** Messick uses Cormorant Garamond (weight 600) in steel blue `#3a6b8a`; Virtueasy uses Bebas Neue / Barlow in hot pink `#FF1F7A`. Pull exact tokens from the brand skills.

---

## Licensing flag

Remotion's free tier covers 3 people. The Messick team (Morgan, Rida, Jacob, Sanam) is 4, which may exceed it. Review remotion.dev/license before commercial client use. Flag this to Morgan rather than assuming the free tier covers the team.
