---
name: virtueasy-brand
description: Applies Virtueasy's brand guidelines, voice, content rules, and product details to any output. Use this skill whenever writing anything for Virtueasy — captions, emails, product copy, hooks, blog posts, VA content, MailerLite sequences, social posts, or any asset associated with the Virtueasy brand or its products. Trigger on: "Virtueasy," "VA content," "virtual assistant caption," "email for the funnel," "VA Blueprint," "30-Day VA System," or any task producing content for the Virtueasy audience.
---

# Virtueasy Brand

## Identity

Virtueasy is a **faceless brand** and platform for virtual assistants who want to work smarter, earn more, and build a sustainable freelance business. It is a resource hub and education platform — not just a single product page.

**Morgan's name never appears in Virtueasy content.** Sign off as "Virtueasy" or leave unsigned. No exceptions.

---

## Visual Identity

| Element | Value |
|---|---|
| Hot pink | `#FF1F7A` |
| Near-black | `#0A0A0A` |
| Off-white | `#F8F8F8` |
| Display font | Bebas Neue |
| Body font | Barlow |

---

## Voice and Tone

- Direct, practical, and skepticism-aware.
- This audience has been burned by "guru" content and MLM-adjacent promises. They need specificity, real proof, and honesty about the effort required.
- No hype. No vague promises. No "change your life" language without grounding it in something concrete.
- Conversational but confident. Lowercase text-overlay style works well for short-form.
- Hooks should create tension or discomfort before delivering value.

---

## Hard Rules (Never Break)

- **No em dashes** — use a comma, period, or restructure.
- **Morgan's name never appears** in any Virtueasy content, emails, or copy.
- **Never use "roadmap," "plan," or "blueprint"** as generic format descriptors. The product is called the 30-Day VA System — "blueprint" is only used when referencing that specific product by name (VA Blueprint is an acceptable short form).
- **"System" is the preferred framing word** for products and processes.
- Sign off as **"Virtueasy"** or leave unsigned. Never sign as Morgan.

---

## Target Audience: VA Veronica

| Attribute | Detail |
|---|---|
| Gender | Primarily women |
| Age | 25-44 |
| Location | US-based |
| Pre-VA income | $35-65k household |
| Motivation | Financial (not passion-driven) |
| Non-negotiable | Flexibility and schedule control |
| Mindset | Skeptical of hype, learns by doing |
| Needs | Systems and templates she can use immediately |
| Trust triggers | Specificity, proof, honesty about effort |

---

## Products and Infrastructure

### 30-Day VA System (flagship product)
- **Also called:** VA Blueprint (acceptable short form)
- **Tagline:** 30 Days to Your First High-Ticket Client
- **Format:** 30-day interactive HTML workbook
- **Hosted at:** blueprint.virtueasy.com
- **Access code:** BLUEPRINT2026
- **Price:** $43 retail
- **Discount code:** PREVIEW30 (brings to ~$13 via preview module)
- **Stripe:** buy.stripe.com/6oU3cxeav7xyaft8iE63K05
- **Features:** localStorage auto-save, journal prompts, AI generation on Day 11 via Vercel proxy, per-day note downloads, progress bar, home screen dashboard

### Preview Module
- **URL:** virtueasyproducts-cmd.github.io/va-blueprint-preview
- **Covers:** Days 10-12
- **AI gen:** Day 11 (5-gen cap)
- **Sticky banner** with PREVIEW30 code

### Vercel Proxy (AI generation)
- **URL:** workbook-theta.vercel.app/api/generate
- **Model:** Claude Sonnet 4 (edge function)
- **Repo:** virtueasyproducts-cmd/workbook

### MailerLite
- **Sender:** hello@virtueasy.com
- Strong open rates; click-through drops after Email 1
- Emails 3-7 updated with preview module links and PREVIEW30 code
- Form snippet: `data-form="XGmyJK"`

### Free Resource
- 260 ChatGPT Prompts for VAs at virtueasy.com/260-prompts-download

---

## Brand Positioning

Virtueasy is a **platform brand** and VA resource hub. The 30-Day VA System is the first product in the ecosystem, not the only one. All messaging should reflect the broader platform vision while driving product sales.

Do not position Virtueasy as just a Blueprint page or a single-product brand.

---

## Caption and Content Formula

For social captions (Instagram, TikTok, Facebook, Pinterest):

1. **Opening claim** — strong, specific, slightly provocative
2. **Lifestyle scene** — concrete, sensory, relatable moment
3. **Contrast beat** — what everyone else is doing vs. the VA life
4. **Identity reframe** — this isn't luck or a perk, it's available
5. **CTA** — close with `virtueasy.com` or a specific product link

Lowercase text-overlay style for short-form hooks. No em dashes anywhere.

---

## MailerLite Email Rules

- Never include Morgan's name
- Sign as "Virtueasy" or leave unsigned
- Tone: direct, warm, practical
- Include preview module link and PREVIEW30 code in emails 3-7
- Goal: move subscribers from open to click to purchase
