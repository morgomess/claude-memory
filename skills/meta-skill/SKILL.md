---
name: meta-skill
description: Watches Morgan's work sessions for ways her skills could be better, logs them, and applies the fixes in periodic improvement sessions. Also recommends brand-new skills when a repeating pattern has no skill covering it. Use this skill in two situations. (1) PASSIVELY, during any session - the moment Morgan corrects an output, a skill misfires or fails to fire, a skill turns out to contain stale info, or Morgan does repetitive work no skill covers, capture it. Also trigger on "log that," "that should be in the skill," "note that for later," or "anything for the skill log?" (2) ACTIVELY, when Morgan wants to work on the skills themselves - trigger on "skill improvement session," "review my skills," "improve my skills," "tune my skills," "what skills should I add," "skill audit," or any request to edit, fix, or create a skill. This is the meta-skill that manages all the other skills, including itself. Use it even when Morgan does not say the word "skill" - a correction to an output is a skill signal.
---

# Meta-Skill

This is the skill that improves the other skills. It runs in two modes: **Capture** (lightweight, happens while Morgan works) and **Improvement Session** (periodic, Morgan-initiated). It also flags **new-skill candidates** when work keeps happening that no skill covers.

## How this actually works (read this first)

Claude does not self-trigger on a schedule and does not silently edit skill files in the background. The realistic mechanics:

- **Capture** runs inside normal sessions. When Claude notices something, it logs it (see below). Logging is cheap and should happen often.
- **Improvement Sessions** happen on a cadence Morgan keeps (suggest: first work-block of each month). Morgan starts it; Claude then does everything - reads the log, diagnoses, drafts the edits, writes the updated files.
- **Every actual edit gets Morgan's approval before install.** Claude proposes; Morgan is the committer. This is the guardrail that makes it safe for the system to edit itself - unreviewed self-rewrites drift fast (a skill that learns to fire constantly, or quietly contradicts a hard rule like "no em dashes" or "Virtueasy stays faceless"). The log + Morgan's commit history is the audit trail.

Skill files live read-only in the session. Claude can read them to ground its edits, but applying a change = Claude writes the updated `SKILL.md`, Morgan re-installs it.

---

## Mode 1: Capture (during any session)

Watch for these six signals. When one fires, log it. Don't interrupt the actual work to do it - note it, and surface it at a natural break or when Morgan asks.

| Type | What it looks like |
|------|--------------------|
| `TRIGGER-MISS` | A skill should have fired and didn't, or fired when it shouldn't have |
| `STALE-INFO` | A skill contains something no longer true (retired product, old price, changed client package, dead link) |
| `GAP` | The skill was missing something Claude had to figure out, guess, or ask about |
| `FRICTION` | An instruction was unclear, contradictory, or actively produced a worse output |
| `CORRECTION` | Morgan corrected an output in a way that should be encoded so it doesn't recur |
| `NEW-SKILL` | Repeated work with no skill covering it (see Mode 3) |

**The strongest signal is a correction.** Any time Morgan fixes something Claude produced, ask silently: "is this a one-off, or should the skill learn this?" If it should stick, log a `CORRECTION`.

**How to surface during a session:** one line, no ceremony.
> Logged a skill note: `social-caption` is missing the Aspire purple-heart rule, that tripped me up just now. It's in the queue for the next improvement session.

If repo access is live in the session, append it to the log immediately. Otherwise hold the entries and present them as a copy-paste block when Morgan wraps up or asks "anything for the skill log?"

### Log entry format

```
### [YYYY-MM-DD] <target-skill or "NEW-SKILL"> · <TYPE>
- **Observation:** what happened, plainly
- **Evidence:** the correction / the misfire / the repeated task
- **Proposed change:** the specific edit, if known (else "diagnose in session")
- **Status:** logged
```

Keep observations concrete and tied to a real moment. "Improve the blog skill" is useless. "blog-writer produced a 2,400-word post when ECCO blogs run ~900; add a length spec per client" is actionable.

---

## Mode 2: Improvement Session (periodic, Morgan starts it)

When Morgan says "skill improvement session" (or similar), run this end to end. Don't ask a pile of setup questions - pull the log and go.

1. **Read the log.** Group entries by target skill. Note anything marked `logged` (not yet applied).
2. **Read the current skill files** for every skill with open entries. Ground every proposed edit in what the file actually says now - quote the current line, then the replacement.
3. **Diagnose, don't just transcribe.** Several log entries often point at one root cause. A `TRIGGER-MISS` usually means the `description` needs tuning, not the body. A recurring `CORRECTION` means a missing rule. Cluster before you edit.
4. **Draft the edits.** For each skill, produce the updated `SKILL.md`. Follow skill-creator conventions: imperative voice, all "when to use" info in the `description`, explain *why* a rule matters instead of stacking MUSTs. Match Morgan's house style (direct, decision rules, "what NOT to do," quick-reference blocks).
5. **Show before/after per change** and get Morgan's yes/no/edit on each. Batch the small obvious ones; pause on anything that changes triggering behavior or touches a hard rule.
6. **Output the approved files** to a location Morgan can install from, and mark those log entries `applied` with the date. Leave rejected ones as `rejected` with a one-line reason so the same idea doesn't get re-proposed next month.
7. **Optionally validate triggering changes.** If a `description` was changed to fix a `TRIGGER-MISS`, write 2-3 realistic test prompts and check the skill would now fire (and still wouldn't on near-misses). Use the skill-creator eval flow if Morgan wants rigor; a quick sanity check is fine otherwise.

**Conflict check before any edit ships:** does the change contradict a Morgan hard rule (no em dashes / single hyphen only, Virtueasy faceless and unsigned, Dr. Kelli emoji order 💚🧠💙 with dark-skinned hands, Aspire 💜, client email tone short-and-direct) or Claude's own operating guidelines? If so, flag it rather than applying it. The skills serve the rules, not the other way around.

---

## Mode 3: New-Skill Recommendations

When the same kind of work shows up repeatedly with no skill behind it, that's a candidate. Log it as `NEW-SKILL` with the evidence (which sessions, what the recurring task was). In an improvement session, review candidates and, for the ones worth it, draft a new skill using skill-creator conventions:

- A pushy `description` carrying all the triggering (Claude tends to under-trigger skills, so lean toward firing).
- Imperative body, under ~300 lines, with the decision rules and quick-reference blocks Morgan's other skills use.
- Wire it into Morgan's actual stack (Airtable / GitHub / MailerLite / Metricool / Stripe) where relevant.

Don't propose a skill for a one-off. The bar is "this pattern will keep recurring and a skill would save real time or prevent a repeated correction."

---

## Self-improvement (the meta-skill on itself)

This skill logs entries about itself like any other - if it under-captures, over-captures, or its own format is clunky, that's a `meta-skill` log entry. Same approval gate applies: Claude proposes changes to this file, Morgan installs them. Extra caution on two things, because they're how a self-editing system goes wrong:

- **Don't let it loosen its own guardrails.** A proposed edit that removes the approval gate, the conflict check, or the audit trail should be flagged hard, not applied.
- **Don't let capture inflate.** If every session generates twenty trivial entries, the log becomes noise and real signals get buried. Tighten the bar before adding more triggers.

---

## Where the log lives

**Default: a markdown file in the messick-marketing repo** - `skills/SKILL-IMPROVEMENT-LOG.md` (repo: morgomess/messick-marketing). It's version-controlled, human-readable, and works with the existing github-powershell skill for commits. The commit history doubles as the audit trail. A starter template ships with this skill (`assets/SKILL-IMPROVEMENT-LOG.md`).

**Alternative: Airtable**, if Morgan wants it in the Virtueasy AIOS / central brain. Use a table with fields: Date, Target Skill, Type (single-select from the six), Observation, Evidence, Proposed Change, Status (logged / applied / rejected / deferred). Queryable and sortable, at the cost of being a click away during fast sessions.

Pick one and stick with it so there's a single source of truth.

---

## Decision rules

- **Capture vs. interrupt:** never derail live work to log. Note it, surface at a break.
- **Log vs. fix-now:** in a normal session, log. Only edit a skill mid-session if Morgan explicitly asks to.
- **Apply vs. flag:** apply small, obvious, rule-consistent edits after a quick yes. Flag anything that changes triggering or brushes a hard rule.
- **One-off vs. pattern:** correct one-offs in the moment; only log/encode things that will recur.
- **Diagnose before editing:** cluster related entries to a root cause; don't make ten edits where one rule fixes the lot.

## What NOT to do

- Don't claim to run on a schedule or edit skills silently - Morgan starts improvement sessions and approves installs.
- Don't apply any edit that loosens this skill's own guardrails.
- Don't ship an edit that contradicts a Morgan hard rule or Claude's operating guidelines - flag it.
- Don't log vague entries ("make it better"). Tie every entry to a real moment and a specific change.
- Don't propose new skills for one-off tasks.
- Don't let the log fill with trivia - protect the signal.

## Quick reference

**Six capture types:** `TRIGGER-MISS` · `STALE-INFO` · `GAP` · `FRICTION` · `CORRECTION` · `NEW-SKILL`

**Statuses:** logged → applied / rejected / deferred

**Cadence:** suggest a recurring reminder (e.g. first work-block of the month) - "Skill improvement session." Morgan triggers it; Claude runs Mode 2 end to end.

**Entry template:**
```
### [YYYY-MM-DD] <target-skill or "NEW-SKILL"> · <TYPE>
- **Observation:**
- **Evidence:**
- **Proposed change:**
- **Status:** logged
```
