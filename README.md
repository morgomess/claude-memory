# claude-memory

Persistent store for Claude across sessions. Not human-facing - formatted for Claude to read and write quickly. Morgan points Claude here when she wants it used.

## Layout

| Folder | Holds |
|---|---|
| `/sops/` | Standard operating procedures, one `.md` per SOP |
| `/skills/` | Backup copies of skills (NOT canonical - skills load natively in Claude's skill system; this is backup only) |
| `/data/` | Small structured files (json, csv). Heavy/binary files go to R2, not here. |
| `/sessions/` | Session notes, dated `YYYY-MM-DD-slug.md` |
| `/reference/` | Standing context: client facts, brand rules, recurring constants |

## Rules

- One concept per file. No giant catch-all docs.
- No secrets. No API keys, tokens, or credentials, even in private repos.
- Queryable/relational data belongs in Airtable, not here.
- Heavy or binary files (images, video, large datasets) belong in R2, not here.
- Predictable internal format: consistent headers and key order for anything updated repeatedly.

## How Claude uses this

At session start (when pointed here): read this README, then the relevant folder.
At session end: write session notes to `/sessions/` and update `/reference/` or `/sops/` if anything changed.
