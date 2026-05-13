# Lead Magnets

| Field | Value |
|---|---|
| **Skill Name** | lead-magnets |
| **Source** | Antigravity |
| **BenOS Fit** | 5/5 |
| **Ventures** | SIPP, WIC, CC, Bennovative |
| **API Status** | Green |
| **Voice Injection** | Heavy |
| **Group** | MARKETING |
| **Triggers** | lead magnet, gated content, email capture, downloadable, opt-in offer, free resource |
| **Version** | 1.0.0 |
| **Date Added** | 2026-03-21 |

## Purpose

Plan and optimize lead magnets for email capture and lead generation. Use when designing gated content, checklists, templates, downloadable resources, or other offers that convert visitors into subscribers.

## Triggers

- "lead magnet"
- "gated content"
- "email capture"
- "downloadable"
- "opt-in offer"
- "free resource"

## Inputs

- Venture context (SIPP, WIC, CC, or Bennovative)
- Business context and ideal customer profile
- Existing content assets and expertise
- Current lead capture setup and conversion rates
- Goals: list growth, lead quality, or product education

## Outputs

- Lead magnet recommendation (format, topic, buyer stage)
- Content outline with scope and differentiators
- Gating and capture plan (form fields, landing page structure)
- Distribution plan (channels, content upgrades, paid amplification)
- Measurement plan (KPIs, A/B test priorities)

## BenOS Integrations

- **Product Marketing Context:** This skill reads `.agents/product-marketing-context-[venture].md` before asking questions. If that file is missing for your venture, run the `product-marketing-context` skill first to generate it. Older setups may use `.claude/product-marketing-context.md`.
- **Klaviyo MCP:** Used for email delivery of lead magnets — drip delivery sequences, thank-you confirmation emails, and post-capture nurture flows. Ensure Klaviyo MCP is connected before planning delivery method.
- **Shopify (WIC):** For WIC gated offers, the download gate can be embedded in a Shopify landing page or tied to a product page. Coordinate with the WIC Shopify store for form embed and redirect logic.

## Customization Notes

- All generic email delivery references use **Klaviyo** as the BenOS delivery platform.
- WIC gated offers are structured for Shopify page embeds.
- Venture-specific lead magnet types are listed in the callout block below the type selection framework.
- Product marketing context is read from `.agents/product-marketing-context-[venture].md`.
- Related skill references (free-tool-strategy, email-sequence, etc.) map to BenOS skill registry.

---

# Lead Magnets — Full Instructions

You are an expert in lead magnet strategy. Your goal is to help plan lead magnets that capture emails, generate qualified leads, and naturally lead to product adoption.

## When to Use
- Use when planning downloadable offers or gated resources for email capture.
- Use when the user wants a lead magnet strategy tied to conversion and product interest.
- Use when deciding what to give away, not just writing the asset itself.

## Before Planning

**Check for product marketing context first:**
If `.agents/product-marketing-context-[venture].md` exists (e.g., `.agents/product-marketing-context-wic.md`, `.agents/product-marketing-context-sipp.md`), read it before asking questions. If not found, check `.claude/product-marketing-context.md` as a fallback for older setups. Use that context and only ask for information not already covered or specific to this task.

Gather this context (ask if not provided):

### 1. Business Context
- What does the company do?
- Who is the ideal customer?
- What problems does your product solve?

*Example — SIPP: Homeowners concerned about tap water quality; SIPP solves the "I don't know what's in my water" problem with real-time monitoring.*

### 2. Current Lead Generation
- How do you currently capture leads?
- What lead magnets or offers do you have?
- What's your current conversion rate on email capture?

*Example — WIC: Currently capturing emails via pop-up at checkout; no lead magnets yet; conversion rate unknown.*

### 3. Content Assets
- What existing content could be repurposed? (blog posts, guides, data)
- What expertise can you package?
- What templates or tools do you use internally?

*Example — CC: SBIR proposal templates, TABA eligibility checklists, and Phase II go-to-market frameworks built internally.*

### 4. Goals
- Primary goal: email list growth, lead quality, product education?
- Target audience stage: awareness, consideration, or decision?
- Timeline and resource constraints?

*Example — Bennovative: Goal is list growth for founders and operators; audience is at awareness stage; 1-week creation window.*

---

## Lead Magnet Principles

### 1. Solve a Specific Problem
- Address one clear pain point, not a broad topic
- "How to write cold emails that get replies" > "Marketing guide"

### 2. Match the Buyer Stage
- Awareness leads need education
- Consideration leads need comparison and evaluation
- Decision leads need implementation help

### 3. High Perceived Value, Low Time Investment
- Should look like it's worth paying for
- Consumable in under 30 minutes (ideally under 10)
- Immediate, actionable takeaway

### 4. Natural Path to Product
- Solves a problem your product also solves
- Creates awareness of a gap your product fills
- Demonstrates your expertise in the space

### 5. Easy to Consume
- One clear format (don't mix ebook + video + spreadsheet)
- Works on mobile
- No special software required

---

## Lead Magnet Types

| Type | Best For | Effort | Time to Create |
|------|----------|--------|----------------|
| Checklist | Quick wins, process steps | Low | 1-2 hours |
| Cheat sheet | Reference material, shortcuts | Low | 2-4 hours |
| Template (doc/spreadsheet/Notion) | Repeatable processes, workflows | Low-Med | 2-8 hours |
| Swipe file | Inspiration, examples | Medium | 4-8 hours |
| Ebook/guide | Deep education, authority | High | 1-3 weeks |
| Mini-course (email) | Education + nurture | Medium | 1-2 weeks |
| Mini-course (video) | Education + personality | High | 2-4 weeks |
| Quiz/assessment | Segmentation, engagement | Medium | 1-2 weeks |
| Webinar | Authority, live engagement | Medium | 1 week prep |
| Resource library | Ongoing value, return visits | High | Ongoing |
| Free trial/community access | Product experience | Varies | Varies |

> **BenOS Venture Lead Magnet Types:**
> - **CC:** Commercialization Readiness Audit checklist, SBIR Phase II Go-to-Market Checklist, TABA Eligibility Self-Assessment
> - **WIC:** Specialty Coffee Brew Guide, Coffee Origin & Farmer Story cards, Seasonal Brewing Ritual guide
> - **SIPP:** Home Water Quality Report template, Smart Home Water Safety Checklist, "Know Your Water" assessment
> - **Bennovative:** Stoic Principles for Builders guide, "Doing Hard Things" 30-day framework, Morning Clarity Protocol

---

## Matching Lead Magnets to Buyer Stage

### Awareness Stage
Goal: Educate on the problem. Attract people who don't know you yet.

| Format | Example |
|--------|---------|
| Checklist | "10-Point Website Audit Checklist" |
| Cheat sheet | "SEO Cheat Sheet for Beginners" |
| Ebook/guide | "The Complete Guide to Email Marketing" |
| Quiz | "What Type of Marketer Are You?" |

*Example — SIPP (Awareness): "Smart Home Water Safety Checklist" — educates homeowners on contaminant risks before they know SIPP exists.*

### Consideration Stage
Goal: Help evaluate solutions. Build trust and demonstrate expertise.

| Format | Example |
|--------|---------|
| Comparison template | "CRM Comparison Spreadsheet" |
| Assessment | "Marketing Maturity Assessment" |
| Case study collection | "5 Companies That 3x'd Their Pipeline" |
| Webinar | "How to Choose the Right Analytics Tool" |

*Example — CC (Consideration): "SBIR Phase II Go-to-Market Checklist" — helps research teams evaluate commercialization readiness and positions CC as the expert partner.*

### Decision Stage
Goal: Help implement. Remove friction to purchase.

| Format | Example |
|--------|---------|
| Template | "Ready-to-Use Sales Email Templates" |
| Free trial | "14-Day Free Trial" |
| Implementation guide | "Migration Checklist: Switch in 30 Minutes" |
| ROI calculator | "Calculate Your Savings" (→ see **free-tool-strategy**) |

*Example — WIC (Decision): "Specialty Coffee Brew Guide" — given at checkout or subscription signup to reinforce the purchase decision and reduce buyer's remorse.*

---

## Gating Strategy

### Gating Options

| Approach | When to Use | Trade-off |
|----------|-------------|-----------|
| **Full gate** | High-value content, bottom-funnel | Max capture, lower reach |
| **Partial gate** | Preview + full version | Balance of reach and capture |
| **Ungated + optional** | Top-funnel education | Max reach, lower capture |
| **Content upgrade** | Blog post + bonus | Contextual, high-intent |

### What to Ask For

- **Email only** — highest conversion, lowest friction
- **Email + name** — enables personalization, slight friction increase
- **Email + company/role** — better lead qualification, more friction
- **Multi-field** — only for high-value offers (webinars, demos)

Rule of thumb: Ask for the minimum needed. Every extra field reduces conversion by 5-10%.

### How to Frame the Exchange

- Make the value obvious: "Get the full 25-page guide free"
- Show a preview: table of contents, first page, sample results
- Add social proof: "Downloaded by 5,000+ marketers"
- Reduce risk: "No spam. Unsubscribe anytime."

*Example — Bennovative: For the "Doing Hard Things" 30-day framework, use full gate with email + first name only. Frame: "Get the framework 3,000+ builders use to stay consistent."*

**For form optimization**: See **form-cro** skill
**For popup implementation**: See **popup-cro** skill

---

## Landing Page & Delivery

### Landing Page Structure

1. **Headline** — Clear benefit: what they'll get and why it matters
2. **Preview/mockup** — Visual of the lead magnet (cover, screenshot, sample page)
3. **What's inside** — 3-5 bullet points of key takeaways
4. **Social proof** — Download count, testimonials, logos
5. **Form** — Minimal fields, clear CTA button
6. **FAQ** — Address hesitations (Is it really free? What format?)

*Example — WIC: Landing page for the Coffee Origin & Farmer Story cards should feature a mockup of the card design, a bullet list of the 5 origin stories included, and a "Free with your first order" CTA that gates with email only.*

**For landing page optimization**: See **page-cro** skill

### Delivery Methods

| Method | Pros | Cons |
|--------|------|------|
| **Instant download** | Immediate gratification | No email verification |
| **Email delivery** | Verifies email, starts relationship | Slight delay |
| **Thank you page + email** | Best of both—instant access + email copy | Slightly more complex |
| **Drip delivery** | Builds habit, multiple touchpoints | Only for courses/series |

**BenOS Delivery:** Use **Klaviyo** for all email delivery flows. Set up a Klaviyo automation triggered on form submit to send the asset link or attachment. For drip sequences (e.g., Bennovative's 30-day framework), configure a Klaviyo flow with timed sends. For WIC gated offers embedded in Shopify, use Klaviyo's Shopify integration to trigger delivery on form completion.

### Thank You Page Optimization

Don't waste the thank you page. After they've converted:
- Confirm delivery ("Check your inbox")
- Offer a next step (book a demo, start trial, join community)
- Share on social (pre-written tweet/post)
- Recommend related content

*Example — SIPP: Thank you page after "Know Your Water" assessment should link to the SIPP product page and offer a "See how SIPP monitors your home in real time" CTA.*

---

## Promotion & Distribution

### Blog CTAs & Content Upgrades

- Add relevant CTAs within blog posts (inline, end-of-post)
- Create post-specific content upgrades (bonus checklist for a how-to post)
- Content upgrades convert 2-5x better than generic sidebar CTAs

*Example — CC: A blog post on "Navigating SBIR Phase II Commercialization" should include an inline CTA for the Go-to-Market Checklist as a content upgrade.*

### Exit-Intent & Popups

- Trigger on exit intent or scroll depth
- Match the popup offer to the page content
- **See popup-cro** for implementation

### Social Media

- Share snippets and teasers from the lead magnet
- Create carousel posts from key points
- Use the lead magnet as the CTA in your bio/profile
- **See social-content** for social strategy

### Paid Promotion

- Facebook/Instagram lead ads for top-funnel lead magnets
- Google Ads for high-intent lead magnets (templates, tools)
- LinkedIn for B2B lead magnets (CC)
- Retarget blog visitors with lead magnet ads
- **See paid-ads** for campaign strategy

### Partner Co-Promotion

- Cross-promote with complementary brands
- Guest webinars with partner audiences
- Include in partner newsletters
- Bundle in resource collections

*Example — WIC: Partner with a specialty coffee equipment brand to co-promote the Brew Guide in their newsletter.*

---

## Measuring Success

### Key Metrics

| Metric | What It Tells You | Benchmark |
|--------|-------------------|-----------|
| **Landing page conversion rate** | Offer attractiveness | 20-40% (warm traffic), 5-15% (cold) |
| **Cost per lead** | Acquisition efficiency | Varies by channel and industry |
| **Lead-to-customer rate** | Lead quality | 1-5% (B2B), varies widely |
| **Email engagement** | Content relevance | 30-50% open, 2-5% click |
| **Time to conversion** | Nurture effectiveness | Track by lead magnet source |

*Track all metrics in Klaviyo by tagging leads with the lead magnet source at signup. Use Klaviyo's flow analytics to measure nurture sequence performance per venture.*

### A/B Testing Ideas

- **Headline**: Benefit-focused vs. curiosity-driven
- **Format**: Checklist vs. guide on same topic
- **Gate level**: Full gate vs. partial preview
- **Form fields**: Email-only vs. email + name
- **CTA copy**: "Download Free Guide" vs. "Get Your Copy"
- **Delivery**: Instant download vs. email delivery via Klaviyo

### Lead Quality Signals

Good lead magnet attracted quality leads if:
- Higher-than-average email engagement (measure in Klaviyo)
- Leads progress to trial/demo at expected rates
- Low unsubscribe rate after delivery
- Leads match ICP demographics

---

## Output Format

When creating a lead magnet strategy, provide:

### 1. Lead Magnet Recommendation
- Format and topic
- Target buyer stage
- Why this format for this audience
- Estimated creation effort

### 2. Content Outline
- Key sections/components
- Length and scope
- What makes it unique or valuable

### 3. Gating & Capture Plan
- What to gate and how
- Form fields
- Landing page structure

### 4. Distribution Plan
- Promotion channels
- Content upgrade opportunities
- Paid amplification (if applicable)

### 5. Measurement Plan
- KPIs and targets
- What to A/B test first

---

## Task-Specific Questions

1. What existing content or expertise could you turn into a lead magnet?
2. Where does your audience spend time online?
3. What's the most common question prospects ask before buying?
4. Do you have a Klaviyo email nurture sequence set up for new leads?
5. What's your budget for design and promotion?

---

## Related Skills

- **free-tool-strategy**: For interactive tools as lead magnets (calculators, graders, quizzes)
- **copywriting**: For writing the lead magnet content itself
- **email-sequence**: For nurture sequences after lead capture (deliver via Klaviyo)
- **page-cro**: For optimizing lead magnet landing pages
- **popup-cro**: For popup-based lead capture
- **form-cro**: For optimizing capture forms
- **content-strategy**: For content planning and topic selection
- **analytics-tracking**: For measuring lead magnet performance
- **paid-ads**: For paid promotion of lead magnets
- **social-content**: For social media promotion

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
