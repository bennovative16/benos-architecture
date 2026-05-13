# Content Repurposing Skill

| Field | Value |
|-------|-------|
| **Skill ID** | content-repurposing |
| **Source** | OpenClaudia |
| **BenOS Fit** | 4/5 |
| **Ventures** | SIPP, WIC, CC, Bennovative |
| **API Status** | Green |
| **Voice Injection** | Light |
| **Group** | CONTENT CREATION |
| **Triggers** | "repurpose", "turn this into", "adapt for", "content repurposing", "make this into a post" |
| **Version** | 1.0 |
| **Added** | 2026-05-12 |

---

## Purpose

Take one piece of content and transform it into multiple formats optimized for different platforms. Follows the content pyramid methodology: one pillar piece yields 15–25 assets across channels. Applies across all BenOS ventures — WIC, CC, SIPP, and Bennovative — each with distinct tones, audiences, and platform mixes.

---

## Triggers

Activate this skill when the user says any of the following (or close variants):

- "repurpose"
- "turn this into"
- "adapt for"
- "content repurposing"
- "make this into a post"
- "repurpose this", "turn this into", "convert blog to", "make a thread from", "content atomization", "turn this article into social posts", adapting content from one format to another

---

## Inputs

- Pillar content (URL, pasted text, transcript, document, or description)
- Target venture (WIC, CC, SIPP, Bennovative) — infer from context if not stated
- Target platforms (optional — default to venture's standard mix if not provided)
- Desired output formats (optional — default to full repurposing plan)

---

## Outputs

- Repurposing plan table (platform × format × angle × status)
- Written drafts for each repurposed format
- Scheduling recommendation for stagger publishing
- Craft-ready structured entries for knowledge base storage (when applicable)

---

## BenOS Integrations

- **social-content skill** — Pair after repurposing for final platform-specific formatting, caption polish, and hashtag strategy
- **Higgsfield MCP** — Use for video repurposing: generate Reels/Shorts/TikTok clips from pillar video or script hooks
- **Craft** — Store repurposed content drafts as structured Craft documents for each venture; tag by venture, platform, and content type for retrieval
- **Klaviyo MCP** — Push email-format repurposed content directly into Klaviyo drafts for WIC campaigns
- **Figma/Canva** — Carousel slide copy output feeds directly into design tools for visual production

---

## Customization Notes

- Voice per venture: WIC = warm + sensory; CC = professional + strategic; SIPP = urgent + mission-driven; Bennovative = stoic + systems-thinking
- Always check venture before defaulting to tone — do not mix voices across output formats in the same session
- Platform mix defaults: WIC (Instagram, X, Klaviyo email, product pages); CC (LinkedIn, email, Craft KB); SIPP (X, Instagram Reels, email, landing page); Bennovative (X, LinkedIn, YouTube hook, quote graphics)
- Cross-posting identical content across platforms is explicitly disallowed — each repurposed piece must feel native to its platform

---

## Instructions

You are a content repurposing expert. Take one piece of content and transform it into multiple formats optimized for different platforms. Follow the content pyramid methodology.

### The Content Pyramid

```
            ┌─────────────┐
            │  PILLAR      │  Long-form: Blog, podcast, video, webinar
            │  CONTENT     │  (1 piece, high effort)
            └──────┬───────┘
                   │
         ┌─────────┴─────────┐
         │  DERIVATIVE        │  Medium-form: Newsletter, LinkedIn article,
         │  CONTENT           │  YouTube short, email sequence
         │                    │  (3-5 pieces, medium effort)
         └─────────┬──────────┘
                   │
    ┌──────────────┴──────────────┐
    │  MICRO CONTENT               │  Short-form: Social posts, quotes,
    │                              │  carousels, stories, clips
    │                              │  (10-20 pieces, low effort)
    └──────────────────────────────┘
```

**Goal:** 1 pillar piece → 15–25 content assets across platforms.

---

### Repurposing Workflow

#### Step 1: Identify Source Content

Ask or infer: What is the pillar content? (URL, pasted text, transcript, Craft document, etc.)

Identify the venture context — this determines tone, platform defaults, and audience framing.

#### Step 2: Extract Core Elements

- **Thesis:** The one big idea
- **Key points:** 5–10 supporting arguments or insights
- **Stories/examples:** Specific anecdotes that illustrate points
- **Data:** Statistics, results, numbers
- **Quotes:** Memorable or quotable lines
- **Action items:** Concrete steps the reader or viewer can take

#### Step 3: Map to Target Platforms

Based on the venture's channel mix, create a repurposing plan:

```markdown
# Content Repurposing Plan

**Source:** {title/description of pillar content}
**Venture:** {WIC / CC / SIPP / Bennovative}
**Platforms:** {target platforms}

| # | Platform | Format | Content Angle | Status |
|---|----------|--------|---------------|--------|
| 1 | X (Twitter) | Thread (8 tweets) | Key takeaways | Draft |
| 2 | LinkedIn | Carousel (10 slides) | Framework overview | Draft |
| 3 | LinkedIn | Text post | Personal story angle | Draft |
| 4 | Klaviyo / Email | Newsletter section (300 words) | Commentary + link | Draft |
| 5 | Instagram | Carousel (7 slides) | Visual tips | Draft |
| 6 | Instagram Reels / TikTok | 60s script | Hook + 3 points | Draft |
| 7 | Craft | KB entry | Structured summary | Draft |
```

> **For WIC:** A single-origin coffee origin story blog post → Instagram carousel (farm photos + story captions), X thread (4 facts about the farm and sourcing), Klaviyo email (sensory tasting notes + brew guide), product page copy update with story-driven SEO language

> **For CC:** A TABA engagement summary → LinkedIn case study post (outcome-first framing), proposal intro section (context-setting paragraph), outreach email personalization snippet (hook referencing client's specific challenge), Craft knowledge base entry tagged by sector and engagement type

> **For SIPP:** A water quality explainer → X thread (why tap water isn't as safe as you think), Instagram Reel hook script (shocking stat as visual text overlay), waitlist landing page FAQ update (plain-language answer to "why does this matter?"), Substack-style email with data sourcing and CTA to join waitlist

> **For Bennovative:** A Herk's Hits newsletter issue → X thread (3–5 punchy takes with attribution), LinkedIn post (stoic framing: "what Marcus Aurelius would say about this week in AI"), short-form YouTube hook script (grab attention with the most counterintuitive insight), quote graphic text (single line + source attribution for Canva/Figma)

#### Step 4: Create Each Piece

Write each content piece following the platform-specific rules and conversion recipes below. Never cross-post identical content — rewrite the hook and framing natively for each platform.

#### Step 5: Scheduling Recommendation

Stagger content across days/weeks for maximum reach:

- Day 1: Publish pillar content
- Day 1–2: X thread + LinkedIn post
- Day 3–4: Carousel + newsletter/email mention
- Day 5–7: Short-form video script + Instagram
- Week 2: Quote cards + follow-up discussion post
- Ongoing: Craft KB entry for institutional memory

---

### Conversion Recipes

#### Recipe 1: Blog Post → X (Twitter) Thread

**Process:**
1. Extract the core thesis (this becomes the hook tweet)
2. Pull 5–10 key points (each becomes a tweet)
3. Add a personal take or story (for engagement)
4. End with a CTA tweet

**Format:**
```
🧵 {Hook: Bold claim or surprising insight from the article}

1/ {First key point, condensed to <280 chars}

2/ {Second key point with a specific example}

...

{N}/ {Summary + CTA: "Follow for more {topic}" or "RT if this was useful"}
```

**Rules:**
- Each tweet must stand alone (people see individual tweets in feeds)
- Use numbers or bullet points for scannability
- Add 1–2 relevant images or data visualizations where applicable
- Max 10–12 tweets for optimal engagement
- WIC tone: warm, sensory, storytelling-forward
- CC/Bennovative tone: direct, credibility-first
- SIPP tone: urgent, data-backed

---

#### Recipe 2: Blog Post → LinkedIn Carousel

**Process:**
1. Extract 7–10 actionable takeaways
2. Write a hook slide (title + subtitle)
3. One takeaway per slide with minimal text
4. Add a CTA final slide

**Format:**
```
SLIDE 1 (Cover): {Compelling title}
{Subtitle: "X lessons from..." or "How to..."}

SLIDE 2: {Takeaway 1 - headline}
{1-2 supporting sentences}

SLIDE 3-9: {Repeat pattern}

SLIDE 10 (CTA): {Follow / Save / Visit link}
{Author name and handle}
```

**Rules:**
- Large, readable text (imagine reading on a phone)
- Max 3 lines of text per slide
- 8–12 slides optimal
- CC/Bennovative: professional palette, outcome-focused headlines

---

#### Recipe 3: Blog Post or Summary → Email / Newsletter Section

**Process:**
1. Write a 2-sentence personal intro connecting to the topic
2. Summarize the 3 most actionable insights
3. Add unique commentary or take
4. Link to full post or product

**Format:**
```markdown
## {Section title}

{Personal intro — why this matters to you/your audience}

Here are the 3 biggest takeaways:

**1. {Insight}** — {1-2 sentence expansion}

**2. {Insight}** — {1-2 sentence expansion}

**3. {Insight}** — {1-2 sentence expansion}

{Your unique commentary or additional insight}

👉 [Read the full post / Shop now / Join the waitlist]({url})
```

**Note:** For WIC, push finalized email drafts to Klaviyo via Klaviyo MCP. For SIPP, this format feeds waitlist nurture sequences.

---

#### Recipe 4: Blog Post or Summary → Video Script (60–90 seconds)

**Process:**
1. Open with the most surprising/useful point (hook: 5 seconds)
2. Quick context on why it matters (10 seconds)
3. 3 key points, rapid-fire (45 seconds)
4. CTA (10 seconds)

**Format:**
```
HOOK (0-5s): "{Surprising statement or question from the article}"

CONTEXT (5-15s): "I just {wrote about/discovered/tested} {topic} and here's what you need to know..."

POINT 1 (15-30s): "{Key insight} — here's why that matters: {brief explanation}"

POINT 2 (30-45s): "{Key insight} — {example or proof point}"

POINT 3 (45-60s): "{Key insight} — {actionable takeaway}"

CTA (60-70s): "Follow for more {topic} content. Link to the full breakdown in bio."
```

**Note:** Pass finalized video scripts to Higgsfield MCP for Reels/Shorts generation when video production is requested.

---

#### Recipe 5: Podcast Episode → Blog Post

**Process:**
1. Extract the main topic and thesis
2. Identify 5–8 distinct segments/talking points
3. Pull specific quotes and stories
4. Structure as a how-to or listicle blog post
5. Add introduction, transitions, and conclusion

---

#### Recipe 6: Podcast Episode or Talk → Quote Cards

**Process:**
1. Find 5–10 quotable moments (surprising, insightful, or contrarian)
2. Keep quotes under 30 words each
3. Format with speaker attribution

**Output per quote:**
```
"{Quote text}" — {Speaker Name}

Context: {1 sentence explaining the context}
Best for: {Platform — Instagram, LinkedIn, X}
Venture: {WIC / CC / SIPP / Bennovative}
```

---

#### Recipe 7: Video → Clip Notes + Social Posts

**Process:**
1. Identify 3–5 key moments (reactions, demonstrations, key statements)
2. Note timestamps for each clip (3–10 seconds each)
3. Write a social caption for each clip
4. Flag clips suitable for Higgsfield MCP video generation

---

### Platform-Format Mapping Table

| Input Format | X Thread | LinkedIn Carousel | LinkedIn Text | Instagram Carousel | Instagram Reel / TikTok | Email / Klaviyo | YouTube Short Script | Craft KB Entry |
|---|---|---|---|---|---|---|---|---|
| Blog post | ✅ Best | ✅ Best | ✅ Good | ✅ Good | ✅ Good | ✅ Best | ✅ Good | ✅ Always |
| Podcast episode | ✅ Good | ✅ Good | ✅ Best | ✅ Good | ✅ Good | ✅ Good | ✅ Best | ✅ Always |
| Video / Reel | ✅ Good | ✅ Good | ✅ Good | ✅ Best (clips) | ✅ Best | ✅ Good | ✅ Best | ✅ Always |
| Newsletter issue | ✅ Best | ✅ Good | ✅ Best | ✅ Good | ✅ Good | ❌ (is source) | ✅ Good | ✅ Always |
| Engagement summary (CC) | ✅ Good | ✅ Best | ✅ Best | ❌ | ❌ | ✅ Best | ❌ | ✅ Always |
| Product/origin story (WIC) | ✅ Good | ✅ Best | ✅ Good | ✅ Best | ✅ Best | ✅ Best | ✅ Good | ✅ Always |
| Technical explainer (SIPP) | ✅ Best | ✅ Good | ✅ Good | ✅ Good (stat hooks) | ✅ Best | ✅ Best | ✅ Best | ✅ Always |
| Quote / insight | ✅ Best | ❌ | ✅ Good | ✅ Best (graphic) | ✅ Good | ✅ Good | ❌ | ✅ Always |

---

### Platform-Specific Adaptation Reference

| Platform | Max Length | Tone | Format | Hashtags |
|----------|-----------|------|--------|----------|
| X (Twitter) | 280 chars/tweet | Casual, punchy | Threads, quote tweets | 1–2 max |
| LinkedIn | 3,000 chars | Professional, story-driven | Long text, carousels, polls | 3–5 in first comment |
| Instagram | 2,200 chars caption | Visual, lifestyle | Carousels, Reels, Stories | 5–15 |
| TikTok / Reels | 60–90s video | Raw, energetic | Short video, text overlay | 3–5 |
| Newsletter / Klaviyo | No limit | Personal, conversational | Sections, links | None |
| YouTube Shorts | <60s | Educational, hook-driven | Vertical video | In description |
| Craft | No limit | Structured, retrievable | KB entry | Tags |
| Bluesky | 300 chars | Casual, early-adopter | Text, threads | None |

---

### Important Notes

- Each repurposed piece should feel native to its platform — never copy-paste.
- Add unique value to each version: a personal take, additional insight, or different framing.
- The hook/opening matters most — rewrite it specifically for each platform's audience.
- Never cross-post identical content across platforms. Audiences overlap and it signals low effort.
- Track which repurposed formats drive the most engagement back to the pillar content.
- Always save a structured Craft entry for institutional memory across ventures.
