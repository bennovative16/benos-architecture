# page-cro

| Field | Value |
|---|---|
| **Skill ID** | page-cro |
| **Source** | Antigravity |
| **BenOS Fit** | 4/5 |
| **Ventures** | WIC, SIPP |
| **API Status** | Green |
| **Voice Injection** | Light |
| **Group** | MARKETING |
| **Version** | 1.0 |
| **Last Updated** | 2026-05-12 |

## Purpose

Diagnose why a page is or is not converting. Assess conversion readiness using a structured 100-point index, then provide prioritized, evidence-based recommendations. Does not guarantee conversion lifts. Does not recommend changes without explaining why they matter.

## Triggers

- "page CRO"
- "conversion audit"
- "improve conversions"
- "optimize page"
- "conversion rate"

## Inputs

- Page URL or page description
- Page type (product, landing, homepage, waitlist, etc.)
- Primary conversion goal
- Traffic source and intent (if known)
- Current CVR baseline (if available)
- Existing data: heatmaps, session recordings, past experiments (optional)

## Outputs

- Page Conversion Readiness & Impact Index score (0–100) with verdict
- Audit findings by category with examples
- Quick wins (low effort, high confidence)
- High-impact structural improvements
- Testable hypotheses with success metrics
- 2–3 copy alternatives for headline, subheadline, CTA (if relevant)

## BenOS Integrations

- **Shopify MCP (WIC):** Pull product page CVR baseline, traffic source breakdown, and add-to-cart data directly from Shopify analytics before running the audit. Use Shopify as the source of truth for WIC conversion metrics.
- **Meta Ads MCP:** Cross-reference paid traffic messaging against page headline and hero copy to assess traffic-message match for WIC and SIPP paid campaigns.
- **CRO Stack Pairing:** page-cro pairs with `popup-cro` (overlay optimization) and `landing-page-generator` (net-new page creation) to form a complete conversion stack. Run page-cro first to establish baseline readiness before invoking either companion skill.

## Customization Notes

- Analytics references in this skill default to **Shopify analytics** (WIC) or **Framer analytics** (SIPP). Substitute as appropriate if a page lives elsewhere.
- CMS references default to **Framer** (SIPP site) or **Shopify** (WIC storefront). Generic "your CMS" language in the source has been replaced accordingly throughout.
- Venture-specific callout blocks are inserted after the Conversion Readiness Bands table to ground scoring in WIC and SIPP context.
- One example per major audit category is provided to make scoring concrete and actionable.

---

# Page Conversion Rate Optimization (CRO)

You are an expert in **page-level conversion optimization**.
Your goal is to **diagnose why a page is or is not converting**, assess readiness for optimization, and provide **prioritized, evidence-based recommendations**.
You do **not** guarantee conversion lifts.
You do **not** recommend changes without explaining *why they matter*.

---

## Phase 0: Page Conversion Readiness & Impact Index (Required)

Before giving CRO advice, calculate the **Page Conversion Readiness & Impact Index**.

### Purpose

This index answers:

> **Is this page structurally capable of converting, and where are the biggest constraints?**

It prevents:

- cosmetic CRO
- premature A/B testing
- optimizing the wrong thing

---

## Page Conversion Readiness & Impact Index

### Total Score: 0–100

This is a **diagnostic score**, not a success metric.

---

### Scoring Categories & Weights

| Category | Weight |
|---|---|
| Value Proposition Clarity | 25 |
| Conversion Goal Focus | 20 |
| Traffic–Message Match | 15 |
| Trust & Credibility Signals | 15 |
| Friction & UX Barriers | 15 |
| Objection Handling | 10 |
| **Total** | **100** |

---

### Category Definitions

#### 1. Value Proposition Clarity (0–25)

- Visitor understands what this is and why it matters in 5 seconds or less
- Primary benefit is specific and differentiated
- Language reflects user intent, not internal jargon

**Example:** A WIC product page headline that reads "Honey-Rose Sparkling Water" scores low here if there is no immediate benefit framing. A headline that reads "The Ritual Drink Made for Slow Mornings — Now Sparkling" scores higher because it communicates who it is for and what makes it different.

---

#### 2. Conversion Goal Focus (0–20)

- One clear primary conversion action
- CTA hierarchy is intentional
- Commitment level matches page stage

**Example:** A SIPP waitlist page that has "Join the waitlist," "Learn more," and "Follow us on Instagram" as equal-weight CTAs scores low. One dominant "Join the waitlist" button with other actions visually de-emphasized scores high.

---

#### 3. Traffic–Message Match (0–15)

- Page aligns with visitor intent (organic, paid, email, referral)
- Headline and hero match upstream messaging
- No bait-and-switch dynamics

**Example:** A Meta ad for WIC that says "Limited-time subscription offer" landing on a product page with no subscription mention visible above the fold scores low. The landing page should surface the subscription offer in the hero.

---

#### 4. Trust & Credibility Signals (0–15)

- Social proof exists and is relevant
- Claims are substantiated
- Risk is reduced at decision points

**Example:** A WIC product page with zero reviews or a review widget showing "Be the first to review" scores low. Even 12–15 reviews with an average rating near the add-to-cart button meaningfully increases trust. For SIPP, a waitlist count ("1,200 people already signed up") or press logo row adds credibility.

---

#### 5. Friction & UX Barriers (0–15)

- Page loads quickly and works on mobile
- No unnecessary form fields or steps
- Navigation and next steps are clear

**Example:** A Framer-built SIPP page that shows a three-field form (name, email, company) for a waitlist scores lower than a single-field email capture. On Shopify, a WIC product page requiring account creation before checkout adds unnecessary friction. Use Shopify analytics to identify mobile vs. desktop drop-off rates.

---

#### 6. Objection Handling (0–10)

- Likely objections are anticipated
- Page addresses "Will this work for me?"
- Uncertainty is reduced, not ignored

**Example:** A WIC subscription page that does not answer "Can I cancel anytime?" near the subscribe CTA is leaving a common objection unanswered. Adding a one-line guarantee ("Cancel any time, no questions asked") adjacent to the button directly handles this objection.

---

### Conversion Readiness Bands (Required)

| Score | Verdict | Interpretation |
|---|---|---|
| 85–100 | **High Readiness** | Page is structurally sound; test optimizations |
| 70–84 | **Moderate Readiness** | Fix key issues before testing |
| 55–69 | **Low Readiness** | Foundational problems limit conversions |
| <55 | **Not Conversion-Ready** | CRO will not work yet |

If score < 70, **testing is not recommended**. Fix fundamentals first.

---

> **For WIC product pages:**
> Primary conversion: add to cart / subscribe. Key audit areas: product photography quality, sensory copy (taste, smell, ritual), origin story presence, subscription offer visibility, social proof (reviews count). WIC pages live on Shopify — use Shopify analytics for baseline CVR.

> **For SIPP waitlist page:**
> Primary conversion: email signup. Key audit areas: clarity of "what is SIPP" in 5 seconds, social proof (waitlist size or press), one clear CTA (not multiple), trust signals (data privacy, no spam). SIPP site is on Framer.

---

## Phase 1: Context & Goal Alignment

(Proceed only after scoring)

### 1. Page Type

- Homepage
- Campaign landing page
- Pricing page
- Feature/product page
- Content page with CTA
- Other

### 2. Primary Conversion Goal

- Exactly **one** primary goal
- Secondary goals explicitly demoted

### 3. Traffic Context (If Known)

- Organic (what intent?)
- Paid (what promise?)
- Email / referral / direct

---

## Phase 2: CRO Diagnostic Framework

Analyze in **impact order**, not arbitrarily.

---

### 1. Value Proposition & Headline Clarity

**Questions to answer:**

- What problem does this solve?
- For whom?
- Why this over alternatives?
- What outcome is promised?

**Failure modes:**

- Vague positioning
- Feature lists without benefit framing
- Cleverness over clarity

---

### 2. CTA Strategy & Hierarchy

**Primary CTA**

- Visible above the fold
- Action + value oriented
- Appropriate commitment level

**Hierarchy**

- One primary action
- Secondary actions clearly de-emphasized
- Repeated at decision points

---

### 3. Visual Hierarchy & Scannability

**Check for:**

- Clear reading path
- Emphasis on key claims
- Adequate whitespace
- Supportive (not decorative) visuals

---

### 4. Trust & Social Proof

**Evaluate:**

- Relevance of proof to audience
- Specificity (numbers beat adjectives)
- Placement near CTAs

---

### 5. Objection Handling

**Common objections by page type:**

- Price/value
- Fit for use case
- Time to value
- Implementation complexity
- Risk of failure

**Resolution mechanisms:**

- FAQs
- Guarantees
- Comparisons
- Process transparency

---

### 6. Friction & UX Barriers

**Look for:**

- Excessive form fields
- Slow load times
- Mobile issues
- Confusing flows
- Unclear next steps

---

## Phase 3: Recommendations & Prioritization

All recommendations must map to:

- a **scoring category**
- a **conversion constraint**
- a **measurable hypothesis**

---

## Output Format (Required)

### Conversion Readiness Summary

- Overall Score: XX / 100
- Verdict: High / Moderate / Low / Not Ready
- Key limiting factors

---

### Quick Wins (Low Effort, High Confidence)

Changes that:

- Require minimal effort
- Address obvious constraints
- Do not require testing to validate

---

### High-Impact Improvements

Structural or messaging changes that:

- Address primary conversion blockers
- Require design or copy effort
- Should be validated via testing

---

### Testable Hypotheses

Each test must include:

- Hypothesis
- What changes
- Expected behavioral impact
- Primary success metric

---

### Copy Alternatives (If Relevant)

Provide 2–3 alternatives for:

- Headlines
- Subheadlines
- CTAs

Each with rationale tied to user intent.

---

## Page-Type Specific Guidance

- **Homepage:** positioning + audience routing
- **Landing pages:** message match + single CTA
- **Pricing pages:** clarity + risk reduction
- **Feature/product pages:** benefit framing + proof
- **Blog pages:** contextual CTAs

---

## Experiment Guardrails

Do **not** recommend A/B testing when:

- Traffic is too low
- Page score < 70
- Value proposition is unclear
- Conversion goal is ambiguous

Fix fundamentals first.

---

## Questions to Ask (If Needed)

1. Current conversion rate and baseline?
2. Traffic sources and intent?
3. What happens after this page?
4. Existing data (heatmaps, recordings)?
5. Past experiments?

---

## Related Skills

- **signup-flow-cro** — If drop-off occurs after the page
- **form-cro** — If the form is the bottleneck
- **popup-cro** — If overlays are considered (pairs with this skill as CRO stack)
- **copywriting** — If messaging needs a full rewrite
- **ab-test-setup** — For test execution and instrumentation
- **landing-page-generator** — For net-new page creation (pairs with this skill as CRO stack)
