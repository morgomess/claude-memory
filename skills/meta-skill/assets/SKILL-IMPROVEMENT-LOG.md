# Skill Improvement Log

Single source of truth for skill improvement opportunities across all of Morgan's skills (including the meta-skill itself).

**How to use:** Claude appends entries during work sessions (Capture mode). Morgan runs an Improvement Session on a cadence (suggest: first work-block of the month) to apply them. Every applied edit is reviewed by Morgan before install. Statuses move: `logged` → `applied` / `rejected` / `deferred`.

**Capture types:** `TRIGGER-MISS` · `STALE-INFO` · `GAP` · `FRICTION` · `CORRECTION` · `NEW-SKILL`

---

## Open (logged, not yet applied)

### [2026-06-25] social-caption · CORRECTION
- **Observation:** SVV voice note said "warm, women's health aware" but a review reply Morgan flagged as too sappy showed the voice needs a non-sentimental guard.
- **Evidence:** Rob Rossen FB review reply - first draft rejected as sappy; accepted version was warm, brief, direct.
- **Proposed change:** SVV voice note updated (repo + live) to "warm but NOT sappy - direct over sentimental," with a review-reply guidance note.
- **Status:** logged

### [2026-06-25] healthcare-knowledge · GAP
- **Observation:** HAE acronym was unknown when Morgan asked; PFE also absent. Both are TVI Q3 embolization focuses.
- **Evidence:** TVI campaign calendar (Lisa Albert) - PFE July, GAE Aug, HAE Sept.
- **Proposed change:** Added PFE (Plantar Fasciitis Embolization) and HAE (Hemorrhoid Artery Embolization) to the embolization knowledge (repo + live). GAE already present - deduped.
- **Status:** logged

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

### [2026-06-26] NEW-SKILL · cloudflare-worker-proxy · NEW-SKILL
- **Observation:** The messick-marketing-ai-proxy worker is a shared dependency for 4+ apps (AIOS, Content App, YouTube App, Dashboard, Leads App). When AIOS changes were added, the /imagen route had aspectRatio hardcoded to '3:4' and max_tokens limits were too low. This required a full audit this session that could have been avoided with documented worker architecture.
- **Evidence:** /imagen route ignored aspectRatio from body entirely — caused wrong-size images across all apps for multiple sessions. /claude route had no system prompt support. Both fixed this session.
- **Proposed change:** New skill or reference doc capturing the worker's route map, what each app sends/expects, the Imagen aspectRatio values per content type (4:5 graphic, 9:16 reel/cover, 16:9 YouTube), and the rule: "always destructure aspectRatio from body with a sensible default — never hardcode."
- **Status:** logged

### [2026-06-26] github-powershell · GAP
- **Observation:** Token expired/rate-limited on first attempt this session (api.github.com blocked in container). Skill already documents this correctly — but the session started with a wasted curl attempt anyway.
- **Evidence:** First action was curl to api.github.com, which failed. Skill says to use git clone over HTTPS instead.
- **Proposed change:** Add a bold "DO NOT try curl/api.github.com first" callout at the very top of the skill, above the workflow section.
- **Status:** logged

### [2026-06-26] NEW-SKILL · imagen-prompt-engineering · NEW-SKILL
- **Observation:** Across multiple sessions and multiple apps, the same Imagen prompt mistakes keep recurring: hex codes rendered as visible text, font names rendered as visible text, structural labels like "Line 1" / "Header:" appearing in images, wrong aspect ratios. Each time this is debugged from scratch.
- **Evidence:** This session: youtube app generated images with "#000D4D4", "Line 1", "Canva Sans Extra366" visible in the image. Root cause: image_prompt was embedded inside a JSON schema field description, causing Claude to blend design metadata into the prompt. Fix: always generate image prompts as plain text in a separate call, with explicit bans on hex codes, font names, and structural labels.
- **Proposed change:** New skill `imagen-prompt-engineering` capturing: (1) always generate as plain text, never embedded in JSON; (2) banned terms list (hex codes, font names, structural labels, placeholder text); (3) color description rule (by name only: "deep teal" not "#008080"); (4) text overlay rules (max 4 words, quoted with placement); (5) quality footer template; (6) 2026 best practices (70/30 split, rim light sticker effect, teal-orange grading, safe-zone layout).
- **Status:** logged

### [2026-06-26] messick-brand · STALE-INFO
- **Observation:** The YouTube app's Thumbnail Studio tab was still labeled "Reel Covers" — implying all thumbnails are 9:16 reels. Platform selectors had no 16:9 YouTube Thumbnail option. This reflects a gap in how the messick-brand or app-specific docs describe the thumbnail workflow.
- **Evidence:** Screenshot showed "Reel Covers" tab, platform dropdown with only Instagram/Facebook/TikTok/YouTube Shorts — no 16:9 YouTube option. Fixed this session.
- **Proposed change:** If a thumbnail workflow skill or app reference exists, update to clarify: YouTube thumbnails = 16:9 (1280x720), Shorts/Reels/Stories = 9:16 (1080x1920). Both formats should always be available.
- **Status:** logged

### [2026-06-26] NEW-SKILL · dashboard-feature-map · NEW-SKILL
- **Observation:** The Messick Marketing dashboard (/dashboard) has grown significantly — Today Bar, Top 3 focus slots, drag-and-drop between both, column view, Empire game, slot reel picker, AI quick-add, KV sync, task drawer. No single reference captures what exists and how it connects, causing re-discovery each session.
- **Evidence:** This session: added Today Bar → Top 3 drag, Top 3 click-to-open-drawer. Both were natural next features but required reading ~2500 lines of dashboard code each time to understand the existing patterns.
- **Proposed change:** New reference doc (not necessarily a triggerable skill) capturing the dashboard's feature map: data model (localStorage keys, focus pins format, today order format), rendering pipeline (renderTodayDue → renderFocus → renderColumns), drag state variables (tdDragId, focusDragSlot, dragState), and event flow. Would make future dashboard sessions much faster.
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
