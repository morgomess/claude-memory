---
name: youtube-metadata
description: Generates optimized YouTube titles, descriptions, and tag lists for any video in any niche or industry. Use this skill whenever a video title, YouTube description, or tag list is needed — for healthcare clients, VA content, fitness, legal, real estate, finance, or any other niche. Trigger on: "YouTube title," "video description," "optimize this video," "title and description," "tags for this video," any video transcript or brief where metadata output is the goal. Works from transcripts, video briefs, or topic summaries.
---

# YouTube Metadata Skill

## Input Modes

This skill accepts input in three forms:
1. **Transcript** — raw or timestamped video transcript (most common)
2. **Brief** — topic, speaker, key points, practice/brand info
3. **Topic only** — minimal input; skill will generate from niche + topic alone

Identify the input type and extract the necessary variables before writing.

---

## Step 1: Extract Core Variables

Before writing anything, identify:

| Variable | What to extract |
|---|---|
| **Topic** | The main subject or procedure being discussed |
| **Benefit** | What the viewer gains or the patient outcome |
| **Speaker/Brand** | Name, title, practice/company name |
| **Location** | City, state, or region (if local SEO applies) |
| **Niche** | Industry or specialty (healthcare, fitness, legal, VA, etc.) |
| **Audience** | Who this video is for (patients, VAs, homebuyers, etc.) |
| **Differentiator** | What makes this speaker, practice, or approach unique |

---

## Title Formula

### Structure
`[Topic or Procedure]: [Patient/Viewer Benefit] | [Brand or Speaker Name]`

### Rules
- 60-70 characters max (Google truncates beyond this)
- Lead with the topic or the benefit — whichever is more searchable
- Include location only if local SEO is a priority
- Do not keyword-stuff — one clear topic per title
- Use a colon or pipe to separate the value proposition from the brand

### Examples by Niche

**Healthcare (procedure-focused):**
> The Ellipsys Procedure: A Minimally Invasive Fistula Option for Dialysis Patients | Sound Vascular & Vein

**Healthcare (physician intro):**
> Leg Pain, Fibroids, Pelvic Pain. One Specialist Can Help. | Sound Vascular & Vein

**VA / education:**
> How to Land Your First High-Ticket VA Client in 30 Days | Virtueasy

**Finance:**
> How to Reduce Your Tax Burden as a Freelancer: What Most CPAs Don't Tell You | [Firm Name]

**Real estate:**
> What First-Time Buyers Get Wrong About Pre-Approval | [Agent/Brand Name]

**Fitness:**
> Why You're Not Building Muscle (And It's Not Your Workout) | [Coach/Brand]

### Title Option Variants
Always generate 3-5 title options. Label them:
- **Option A** — Procedure/topic-led (best for search)
- **Option B** — Benefit/outcome-led (best for click-through)
- **Option C** — Question format (best for problem-aware audiences)
- **Option D** — Physician/speaker-led (best for personal brand building)

---

## Description Formula

### Section 1: Hook (2-3 sentences)
Restate the core value of the video in plain language. No jargon. Answers "why should I watch this?"

### Section 2: What You'll Learn / What This Covers (3-5 sentences)
Expand on the key points from the video. Use the transcript to pull specific details — named procedures, statistics, patient outcomes, specific advice. Specific always beats general.

### Section 3: About the Speaker / Practice / Brand (2-3 sentences)
Credentials, specialty, location, years of experience, unique differentiator. For faceless brands, this is about the product or methodology.

### Section 4: CTA (1-3 lines)
Platform-appropriate call to action. Include:
- Website URL
- Phone number (if local business)
- Location (if applicable)
- Subscribe prompt (optional)

### Formatting
- No em dashes
- Use line breaks between sections for readability
- Emoji sparingly — one per CTA line max, only if on-brand
- 200-400 words total (long enough for SEO, short enough to read)

### Description Template

```
[Hook — 2-3 sentences explaining the video's value in plain language]

[2-4 sentences on what's covered — pull specific details from the transcript]

[About the speaker/brand — credentials, specialty, location, differentiator]

[CTA block]
📍 [Location if applicable]
🌐 [Website]
📞 [Phone if applicable]
```

---

## Tag List Formula

### Structure
Generate 15-25 tags organized in three tiers:

**Tier 1 — Exact match (5-7 tags)**
Specific to this video. Procedure name, physician name, brand name, location + specialty.
> `Dr. Peter Gregory Sound Vascular`, `Ellipsys procedure Federal Way WA`, `band-aid fistula dialysis`

**Tier 2 — Broad match (6-10 tags)**
General topic, specialty, condition, and symptom terms that match how real people search.
> `minimally invasive fistula`, `dialysis access options`, `hemodialysis fistula`, `interventional nephrology`

**Tier 3 — Audience match (4-8 tags)**
Who watches this and what problem they're solving. Less about the procedure, more about the viewer.
> `dialysis patient options`, `kidney disease treatment`, `vascular access surgery alternative`, `dialysis without surgery`

### Niche-Specific Tag Patterns

**Healthcare:**
- Procedure name (spelled out + acronym)
- Physician full name + practice name
- City + state + specialty
- Symptom-based terms ("knee pain without surgery")
- Comparison terms ("alternative to X")

**VA / Education / Digital Products:**
- Course or product name
- Outcome terms ("how to get VA clients," "VA business tips")
- Audience identity tags ("virtual assistant," "work from home")
- Platform tags ("VA TikTok," "VA Instagram")

**Local services (real estate, law, fitness):**
- City + service ("Denver real estate agent," "Austin personal trainer")
- Problem + location ("how to buy a home in Austin")
- Comparison terms ("vs." videos perform well)

---

## Output Format

Deliver in this order:

1. **Title Options** (A through D, labeled)
2. **Recommended Title** (with brief rationale)
3. **Description** (ready to paste)
4. **Tags** (comma-separated, ready to paste)
5. **Optional:** One-line hook for the video thumbnail text (if requested)

---

## Quality Checks Before Delivering

- Title is under 70 characters
- Description opens with a hook, not "In this video..."
- No em dashes anywhere
- At least one location reference if local SEO applies
- Tags include both procedure-specific and symptom/outcome terms
- Speaker credentials are accurate per the transcript (do not invent)
