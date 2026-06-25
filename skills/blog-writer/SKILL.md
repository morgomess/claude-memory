---
name: blog-writer
description: Writes structured blog outlines and full drafts for Messick Marketing clients. Use this skill whenever Morgan asks to write, draft, outline, or create a blog post for any client — including healthcare clients (ECCO Medical, Sound Vascular & Vein, Texas Vascular Institute, JVI, Desert Cardiovascular, Dr. Kelli/Brain Talk Foundation) and non-healthcare clients (BTTCF, and any future clients added). Trigger on: "write a blog," "draft a post," "blog outline," "monthly blog," "client blog," or any request to produce long-form written content for a Messick Marketing client. Always load healthcare-knowledge skill for healthcare clients before writing.
---

# Blog Writer

Produces structured blog outlines and full markdown drafts for Messick Marketing clients. Default output is an outline. Draft is written only when Morgan confirms or requests it.

---

## Step 1: Read the Brief

Every blog request requires a brief before writing begins. If Morgan has not provided one, ask for it using this format:

```
Before I start, I need a quick brief:

- Client:
- Topic / working title:
- Primary keyword (if known):
- Target word count:
- CTA goal (schedule, call, learn more, donate, etc.):
- Any specific angle, stat, or talking point to include:
- Tone notes (if different from default):
```

Do not proceed until the brief is provided. Do not guess at missing fields -- ask.

---

## Step 2: Confirm or Suggest Keyword

Once the brief is received:

- If Morgan provided a primary keyword, acknowledge it and optionally suggest 1-2 alternatives if a stronger option exists based on the topic and client niche.
- If no keyword was provided, suggest a primary keyword and 1-2 secondary keywords based on the topic.
- Keep this brief -- one short paragraph, no lists unless there are 3+ suggestions.

---

## Step 3: Produce the Outline

Output a structured outline using this format:

```
**TITLE:** [Working title optimized for primary keyword]

**INTRO HOOK:** [1-2 sentence description of the hook angle -- patient pain point, stat, myth bust, or question]

**H2 SECTIONS:**
1. [H2 title]
   - [Key point or subpoint]
   - [Key point or subpoint]
2. [H2 title]
   - [Key point or subpoint]
   - [Key point or subpoint]
3. [H2 title]
   - [Key point or subpoint]
   - [Key point or subpoint]
[Add more H2s as needed based on word count target]

**CTA:** [Describe the CTA approach -- what action, what language style, any specific link or phone number from brief/memory]

**WORD COUNT TARGET:** [From brief or estimated based on H2 count]
```

After the outline, ask: "Ready for the full draft?"

---

## Step 4: Write the Draft

Write only after Morgan confirms. Produce a complete markdown draft ready to paste into WordPress, Webflow, or wherever the client publishes.

### Draft structure

1. **Title** -- H1, keyword-forward, under 65 characters when possible
2. **Intro** -- 2-3 sentences. Lead with the patient perspective, a relatable problem, a surprising stat, or a direct question. No "In today's world" or similar filler openers.
3. **H2 sections** -- Follow the approved outline. Each section 100-200 words depending on total target. Use H3s sparingly and only when a section genuinely has sub-topics.
4. **CTA** -- Final section or closing paragraph. Varies by client and topic (see CTA guidance below).
5. **No closing sign-off** -- Do not add "Written by" or any byline.

### Writing rules (always apply)

- No em dashes -- use commas, periods, or restructure the sentence
- No filler phrases: "In today's world," "It's important to note," "At the end of the day," "When it comes to"
- No passive voice stacking
- Short paragraphs -- 2-4 sentences max
- Plain language -- 8th grade reading level for healthcare content
- Keyword appears naturally in title, intro, at least one H2, and conclusion -- never forced
- Internal link placeholder: [INTERNAL LINK: suggest anchor text + topic] when relevant
- Do not fabricate statistics -- use placeholders like [STAT: source type] if a stat would strengthen the section

---

## CTA Guidance by Client

Match CTA tone and action to the client and topic. Pull contact details from memory when available.

| Client | Default CTA approach |
|--------|----------------------|
| ECCO Medical | Schedule a consultation. Include location(s) relevant to topic. Phone + link. |
| Sound Vascular & Vein | Call or book online. Warm, approachable tone. Federal Way, WA focus. |
| Texas Vascular Institute | Book an appointment. Dallas/Plano/Hurst. Direct and confident tone. |
| JVI (Joint & Vascular Institute) | Schedule at nearest location. Rockford or Libertyville depending on topic. |
| Desert Cardiovascular | Contact or schedule. Warm, reassuring tone. |
| Dr. Kelli / Brain Talk Foundation | Learn more, attend an event, or support the foundation. Softer, mission-driven tone. |
| BTTCF | Community-first CTA -- get involved, share your story, support the cause. No hard sell. |
| Non-healthcare / future clients | Pull CTA goal from brief. Default to "learn more" or "get in touch" if unspecified. |

---

## Skill Loading Rules

- **Always load `healthcare-knowledge`** when the client is ECCO Medical, Sound Vascular & Vein, Texas Vascular Institute, JVI, Desert Cardiovascular, or any healthcare client added in the future.
- Load `messick-brand` if tone guidance is needed or if Morgan asks for a brand check.
- Do not load `social-caption` unless Morgan asks to repurpose the blog into social content.

---

## Word Count by Client (defaults if not specified in brief)

| Client | Default target |
|--------|---------------|
| ECCO Medical | 800-1000 |
| Sound Vascular & Vein | 700-900 |
| Texas Vascular Institute | 800-1000 |
| JVI | 700-900 |
| Desert Cardiovascular | 700-900 |
| Dr. Kelli / Brain Talk Foundation | 600-800 |
| BTTCF | 700-1000 (topic-dependent) |
| New/unspecified clients | Ask in brief |

---

## Non-Healthcare Client Notes

**BTTCF (bethetransformationalchange.org)**
- 4 posts/month
- Topics: LGBTQIA+ advocacy, identity, mental health, rights, community, lived experience
- This client has a full style guide. Before writing any BTTCF content, read: `references/bttc-style-guide.md`
- The guide covers required post structure, voice/tone, inclusive language rules, AI optimization, trauma-aware writing, length, and pre-publish checklist
- CTA: get involved, share, support -- never hard sell

**Future non-healthcare clients**
- Treat the brief as the sole source of truth for tone, audience, and CTA
- Do not apply healthcare writing rules (plain language, 8th grade reading level) unless the topic calls for it
- Ask about audience and tone if not specified in brief
