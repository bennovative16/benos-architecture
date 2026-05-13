# Product Marketing Context

## BenOS Metadata

| Field | Value |
|-------|-------|
| Source | Antigravity |
| BenOS Fit | 5/5 |
| Ventures | SIPP, WIC, CC, Bennovative |
| API Status | Green |
| Voice Injection | Heavy |
| Group | CONTENT CREATION |

## Purpose
Keystone context generator. Produces a `.agents/product-marketing-context-[venture].md` file per venture that all downstream marketing skills read before firing. Run once per venture before using any marketing or content skills.

## Triggers
Invoke this skill when:
- Setting up marketing context for a venture
- Starting any marketing, content, or campaign work
- A downstream skill says "product-marketing-context.md not found"
- Running a venture onboarding or relaunch
- Updating brand positioning, ICP, or messaging
- Phrases: "venture context", "product context", "brand context file", "set up marketing context"

## Inputs
- Venture name (SIPP, WIC, CC, or Bennovative)
- Existing copy, landing pages, README, product docs (Claude auto-reads if available)
- Optional: existing `.agents/product-marketing-context-[venture].md` to update

## Outputs
One Markdown file per venture run:
- `.agents/product-marketing-context-sipp.md`
- `.agents/product-marketing-context-wic.md`
- `.agents/product-marketing-context-cc.md`
- `.agents/product-marketing-context-bennovative.md`

## BenOS Integrations
- **Klaviyo MCP**: email-sequence and churn-prevention skills read this file before generating flows
- **Shopify MCP**: paid-ads and popup-cro reference venture context for offer framing
- **Linear MCP**: product-manager-toolkit reads ICP and goals when writing PRDs
- **Craft (Knowledge layer)**: store the output as a Craft document for persistent reference
- **Downstream skills that REQUIRE this file first**: lead-magnets, email-sequence, social-content, content-creator, paid-ads, copy-editing, popup-cro, page-cro, onboarding-cro

## Customization Notes
Source copied verbatim with the following BenOS-specific additions:
1. BenOS metadata header
2. `## BenOS Usage` section added (run 4×, output paths, prerequisite warning)
3. Generic "project tool" references replaced with Linear; "email platform" with Klaviyo
4. No structural changes to the source workflow

---

# Full Instructions

# Product Marketing Context

You help users create and maintain a product marketing context document. This captures foundational positioning and messaging information that other marketing skills reference, so users don't repeat themselves.

## BenOS Usage

> **KEYSTONE SKILL — Run this before all marketing work.**

This skill must be run **4 times — once per BenOS venture**:

| Run | Venture | Output file |
|-----|---------|-------------|
| 1 | SIPP | `.agents/product-marketing-context-sipp.md` |
| 2 | WIC (Who Is Coffee) | `.agents/product-marketing-context-wic.md` |
| 3 | CC (Catalyzing Concepts) | `.agents/product-marketing-context-cc.md` |
| 4 | Bennovative | `.agents/product-marketing-context-bennovative.md` |

**Run `product-marketing-context` BEFORE using:**
- `lead-magnets`
- `email-sequence`
- `social-content`
- `content-creator`
- `paid-ads`
- `copy-editing`
- `popup-cro`
- `page-cro`
- `onboarding-cro`
- Any skill that asks about brand voice

If a downstream skill cannot find the context file for your venture, return here and run this skill first.

## When to Use
- Use when creating a reusable product, audience, and positioning context file.
- Use at the start of a marketing project before more specialized marketing skills.
- Use when the user wants to avoid re-explaining ICP, messaging, and product basics.

The document is stored at `.agents/product-marketing-context-[venture].md`.

## Workflow

### Step 1: Check for Existing Context

First, identify which venture is being run. Then check if `.agents/product-marketing-context-[venture].md` already exists. Also check `.claude/product-marketing-context.md` for older setups — if found there but not in `.agents/`, offer to move it.

**If it exists:**
- Read it and summarize what's captured
- Ask which sections they want to update
- Only gather info for those sections

**If it doesn't exist, offer two options:**

1. **Auto-draft from codebase** (recommended): Study the repo — README, landing pages, marketing copy, package.json, etc. — and draft a V1. The user then reviews, corrects, and fills gaps. Faster than starting from scratch.

2. **Start from scratch**: Walk through each section conversationally, one section at a time.

Most users prefer option 1. After presenting the draft, ask: "What needs correcting? What's missing?"

### Step 2: Gather Information

**If auto-drafting:**
1. Read the codebase: README, landing pages, marketing copy, about pages, meta descriptions, package.json, any existing docs
2. Draft all sections based on what you find
3. Present the draft and ask what needs correcting or is missing
4. Iterate until the user is satisfied

**If starting from scratch:**
Walk through each section below conversationally, one at a time. Don't dump all questions at once.

For each section:
1. Briefly explain what you're capturing
2. Ask relevant questions
3. Confirm accuracy
4. Move to the next

Push for verbatim customer language — exact phrases are more valuable than polished descriptions because they reflect how customers actually think and speak, which makes copy more resonant.

---

## Sections to Capture

### 1. Product Overview
- One-line description
- What it does (2-3 sentences)
- Product category (what "shelf" you sit on — how customers search for you)
- Product type (SaaS, marketplace, e-commerce, service, etc.)
- Business model and pricing

### 2. Target Audience
- Target company type (industry, size, stage)
- Target decision-makers (roles, departments)
- Primary use case (the main problem you solve)
- Jobs to be done (2-3 things customers "hire" you for)
- Specific use cases or scenarios

### 3. Personas (B2B only)
If multiple stakeholders are involved in buying, capture for each:
- User, Champion, Decision Maker, Financial Buyer, Technical Influencer
- What each cares about, their challenge, and the value you promise them

### 4. Problems & Pain Points
- Core challenge customers face before finding you
- Why current solutions fall short
- What it costs them (time, money, opportunities)
- Emotional tension (stress, fear, doubt)

### 5. Competitive Landscape
- **Direct competitors**: Same solution, same problem
- **Secondary competitors**: Different solution, same problem
- **Indirect competitors**: Conflicting approach
- How each falls short for customers

### 6. Differentiation
- Key differentiators (capabilities alternatives lack)
- How you solve it differently
- Why that's better (benefits)
- Why customers choose you over alternatives

### 7. Objections & Anti-Personas
- Top 3 objections heard in sales and how to address them
- Who is NOT a good fit (anti-persona)

### 8. Switching Dynamics
The JTBD Four Forces:
- **Push**: What frustrations drive them away from current solution
- **Pull**: What attracts them to you
- **Habit**: What keeps them stuck with current approach
- **Anxiety**: What worries them about switching

### 9. Customer Language
- How customers describe the problem (verbatim)
- How they describe your solution (verbatim)
- Words/phrases to use
- Words/phrases to avoid
- Glossary of product-specific terms

### 10. Brand Voice
- Tone (professional, casual, playful, etc.)
- Communication style (direct, conversational, technical)
- Brand personality (3-5 adjectives)

### 11. Proof Points
- Key metrics or results to cite
- Notable customers/logos
- Testimonial snippets
- Main value themes and supporting evidence

### 12. Goals
- Primary business goal
- Key conversion action (what you want people to do)
- Current metrics (if known)

---

## Step 3: Create the Document

After gathering information, create `.agents/product-marketing-context-[venture].md` with this structure:

```markdown
# Product Marketing Context — [VENTURE NAME]

*Last updated: [date]*

## Product Overview
**One-liner:**
**What it does:**
**Product category:**
**Product type:**
**Business model:**

## Target Audience
**Target companies:**
**Decision-makers:**
**Primary use case:**
**Jobs to be done:**
-
**Use cases:**
-

## Personas
| Persona | Cares about | Challenge | Value we promise |
|---------|-------------|-----------|------------------|
| | | | |

## Problems & Pain Points
**Core problem:**
**Why alternatives fall short:**
-
**What it costs them:**
**Emotional tension:**

## Competitive Landscape
**Direct:** [Competitor] — falls short because...
**Secondary:** [Approach] — falls short because...
**Indirect:** [Alternative] — falls short because...

## Differentiation
**Key differentiators:**
-
**How we do it differently:**
**Why that's better:**
**Why customers choose us:**

## Objections
| Objection | Response |
|-----------|----------|
| | |

**Anti-persona:**

## Switching Dynamics
**Push:**
**Pull:**
**Habit:**
**Anxiety:**

## Customer Language
**How they describe the problem:**
- "[verbatim]"
**How they describe us:**
- "[verbatim]"
**Words to use:**
**Words to avoid:**
**Glossary:**
| Term | Meaning |
|------|---------|
| | |

## Brand Voice
**Tone:**
**Style:**
**Personality:**

## Proof Points
**Metrics:**
**Customers:**
**Testimonials:**
> "[quote]" — [who]
**Value themes:**
| Theme | Proof |
|-------|-------|
| | |

## Goals
**Business goal:**
**Conversion action:**
**Current metrics:**
```

---

## Step 4: Confirm and Save

- Show the completed document
- Ask if anything needs adjustment
- Save to `.agents/product-marketing-context-[venture].md`
- Tell them: "Other marketing skills will now use this context automatically. Run `product-marketing-context` anytime to update it."
- Remind them: "Run this skill for each remaining venture before using downstream marketing skills."

---

## Tips

- **Be specific**: Ask "What's the #1 frustration that brings them to you?" not "What problem do they solve?"
- **Capture exact words**: Customer language beats polished descriptions
- **Ask for examples**: "Can you give me an example?" unlocks better answers
- **Validate as you go**: Summarize each section and confirm before moving on
- **Skip what doesn't apply**: Not every product needs all sections (e.g., Personas for B2C)

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
