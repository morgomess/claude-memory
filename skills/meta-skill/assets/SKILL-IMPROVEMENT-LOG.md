# Skill Improvement Log

Single source of truth for skill improvement opportunities across all of Morgan's skills (including the meta-skill itself).

**How to use:** Claude appends entries during work sessions (Capture mode). Morgan runs an Improvement Session on a cadence (suggest: first work-block of the month) to apply them. Every applied edit is reviewed by Morgan before install. Statuses move: `logged` → `applied` / `rejected` / `deferred`.

**Capture types:** `TRIGGER-MISS` · `STALE-INFO` · `GAP` · `FRICTION` · `CORRECTION` · `NEW-SKILL`

---

## Open (logged, not yet applied)

### [2026-06-25] NEW-SKILL · remotion-workflow
- **Observation:** Across 5+ sessions Morgan re-hit the same Windows-specific Remotion + Claude Code obstacles (spawn EINVAL on skills add, skills-installer workaround, paste-one-command-at-a-time, wrong-directory npm install, transparent ProRes render command). No skill covered it, so each was rediscovered from scratch.
- **Evidence:** Sessions: Remotion install walkthrough, messick-intro preview, ig-frame-animation, chat-bubbles render, Remotion project ideas.
- **Proposed change:** New skill `remotion-workflow` created (repo + live mount this session). Captures gotchas, one-time setup, daily preview, render commands, conventions, licensing flag.
- **Action needed:** Morgan to install via skill manager for cross-session persistence.
- **Status:** logged

### [2026-06-25] virtueasy-brand · STALE-INFO
- **Observation:** Skill described the 30-Day VA System / VA Blueprint as the flagship product, but it is retired. Virtueasy's only product is now the VA Starter Kit ($27, 6 modules, lifetime).
- **Evidence:** Skill listed blueprint.virtueasy.com, access code BLUEPRINT2026, discount PREVIEW30, $43 price, and "emails 3-7 with PREVIEW30" - all dead. Contradicted standing instructions.
- **Proposed change:** Corrected version written to repo backup (skills/virtueasy-brand/SKILL.md): Starter Kit as sole product, lead magnets (Job Board, Pricing Tool, Blog), Blueprint refs moved to an explicit "Retired" block, naming-protection hard rule replaced with "no hype/guru framing." Flagged for confirmation: Starter Kit Stripe URL, 260-prompts status, current MailerLite sequence, AI-tools specifics.
- **Action needed:** Morgan to update the LIVE skill via skill manager to match the repo backup (container mount is read-only, cannot push to live from here).
- **Status:** logged

<!-- New entries go here. Template:

### [YYYY-MM-DD] <target-skill or "NEW-SKILL"> · <TYPE>
- **Observation:** what happened, plainly
- **Evidence:** the correction / misfire / repeated task
- **Proposed change:** the specific edit, if known (else "diagnose in session")
- **Status:** logged

-->

---

## Applied

<!-- Move entries here after install, with the date applied. -->

---

## Rejected / Deferred

<!-- Move entries here with a one-line reason so the same idea isn't re-proposed. -->
