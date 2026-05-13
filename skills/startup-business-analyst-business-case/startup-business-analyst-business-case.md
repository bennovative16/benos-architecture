# startup-business-analyst-business-case

| Field | Value |
|-------|-------|
| **Source** | Antigravity |
| **BenOS Fit** | 4/5 |
| **Ventures** | CC, SIPP |
| **API Status** | Green |
| **Voice Injection** | Light |
| **Group** | MARKETING |
| **Triggers** | "business case", "commercialization plan", "investor brief", "Phase II narrative", "business analysis" |
| **Pairs With** | market-sizing-analysis, sales-enablement, cold-email |
| **Customization Level** | MEDIUM |

## Purpose

Generate a comprehensive, investor-ready business case document covering market opportunity, solution, competitive landscape, financial projections, team, risks, and funding ask. For CC engagements, this maps to SBIR commercialization plan structure. For SIPP, it reflects hardware + SaaS hybrid economics.

## Triggers

Invoke when the user says: "business case", "commercialization plan", "investor brief", "Phase II narrative", "business analysis", or requests a structured go-to-market or funding document for a BenOS venture.

## Inputs

- Company or venture name and elevator pitch
- Stage (pre-seed, seed, SBIR Phase I/II, pre-launch hardware)
- Intended audience (VCs, SBIR reviewers, strategic partners, internal)
- Existing materials: pitch deck, market sizing data, financial model, competitive analysis
- Venture context: CC (TABA/SBIR) or SIPP (hardware + SaaS)

## Outputs

- Complete business case document (10 sections, 15–20 pages)
- Executive summary (1-page version for quick review)
- Saved as: `business-case-[venture]-YYYY-MM-DD.md` in Craft or local

## BenOS Integrations

- **Before:** Run `market-sizing-analysis` for the venture to produce the TAM/SAM/SOM input; have `product-marketing-context` ready if available.
- **After:** Feed completed business case into `sales-enablement` for pitch deck formatting, or into `cold-email` as a referenced deliverable.
- **Craft:** Store final deliverables in the relevant venture folder in Craft for version history.
- **Primary CC role:** This is the primary CC TABA deliverable tool — the structured output maps directly to what TABA analysts and SBIR reviewers evaluate.

## Customization Notes

- CC engagements require SBIR-specific framing (see CC TABA callout below). Never use VC pitch language for SBIR audiences.
- SIPP engagements require hardware BOM vs. subscription margin analysis (see SIPP callout below).
- For internal planning use, sections 8 (Traction) and 10 (Funding Ask) may be repurposed as milestone tracking and budget justification.
- Financial tables should pull from any existing SIPP or CC financial models rather than being built from scratch.

---

## BenOS Workflow

### Before Running This Skill
1. Run `market-sizing-analysis` for the venture — output the TAM/SAM/SOM and paste results into context.
2. Check if `product-marketing-context` exists for the venture; if so, reference it for positioning language.
3. Confirm audience: SBIR reviewer, VC, strategic partner, or internal. This determines tone and structure emphasis.

### After Running This Skill
- Feed completed business case into `sales-enablement` to generate pitch deck structure or one-pager.
- Reference the completed business case as a source document in `cold-email` outreach (e.g., "our commercialization plan, available on request").
- Archive in Craft under the venture folder with date-stamped filename.

---

> **For CC TABA Engagements:**
> SBIR business cases differ fundamentally from VC pitch business cases. Structure must reflect:
> (1) Technology Readiness Level (TRL) and path to TRL 9
> (2) Market pull evidence — not just TAM, but specific procurement patterns and buyer readiness
> (3) Risk framing: technology risk + market risk, not just market risk
> (4) Transition plan: Phase II → Phase III (commercial) path, including potential DoD/civilian acquisition pathways
> (5) Team credentials: PI background, industry partners, letters of support
> Language: "Phase II awardee", "commercialization plan", "market pull", "transition partner". Never use VC pitch language.
> Output maps to SBIR commercialization plan sections reviewers look for.

> **For SIPP:**
> Business case framing: hardware + subscription SaaS hybrid. Key sections: hardware BOM vs subscription margin analysis, IoT market sizing, smart home adoption curve positioning, go-to-market (waitlist → pre-order → subscription), competitive differentiation from Flume/Moen/Flo.

---

## Full Instructions

### Step 1: Gather Context

Ask the user for key information:

**Company/Venture Basics:**
- Venture name and elevator pitch (e.g., CC: "AI-enabled acoustic sensing for HVAC fault detection"; SIPP: "Smart water flow monitor with leak prevention subscription")
- Stage (pre-seed, seed, Series A — or for CC: SBIR Phase I awardee, Phase II applicant)
- Problem being solved
- Target customers (e.g., CC: DoD facility managers, civilian agency procurement; SIPP: homeowners with high water bills or flood risk)

**Audience:**
- Who will read this? (SBIR reviewers, VCs, angels, strategic partners, internal planning)
- What is the primary goal? (SBIR Phase II application, fundraising, partnership, internal roadmap)

**Available Materials:**
- Existing pitch deck or docs?
- Market sizing data from `market-sizing-analysis`?
- Financial model?
- Competitive analysis?

### Step 2: Activate Relevant BenOS Skills

Reference BenOS stack skills for comprehensive analysis:
- **market-sizing-analysis** — TAM/SAM/SOM calculations (run this first)
- **startup-financial-modeling** — Financial projections
- **competitive-landscape** — Competitive analysis frameworks
- **team-composition-analysis** — Organization planning
- **startup-metrics-framework** — Key metrics and benchmarks

### Step 3: Structure the Business Case

Create a comprehensive document with these sections. Apply CC TABA or SIPP framing where noted.

---

## Business Case Document Structure

### Section 1: Executive Summary (1–2 pages)

**Company/Venture Overview:**
- One-sentence description
- Founded, location, stage
- Team highlights

*CC Example:* "Cascadia Concepts is a Phase I SBIR awardee developing acoustic-based HVAC fault detection for DoD facility management, currently at TRL 4 with a clear path to TRL 7 under Phase II."

*SIPP Example:* "SIPP is a pre-launch smart water monitor combining a hardware device (BOM ~$38) with a $9/month leak prevention subscription, targeting the 140M US homeowner market."

**Problem Statement:**
- Core problem being solved (2–3 sentences)
- Market pain quantified

*CC Example:* "DoD facilities spend $2.1B annually on reactive HVAC maintenance; 40% of failures are detectable 30+ days in advance using acoustic signatures. No deployed solution currently provides real-time acoustic fault detection at scale."

*SIPP Example:* "The average US home water leak costs $11,000 in damage and goes undetected for 70+ days. Existing solutions (Flume, Flo by Moen) require professional installation or plumbing modification, limiting adoption to <2% of addressable households."

**Solution:**
- How the product solves it (2–3 sentences)
- Key differentiation

**Market Opportunity:**
- TAM: $X.XB
- SAM: $X.XM
- SOM (Year 5): $X.XM

*CC Example:* "TAM: $4.2B (US government HVAC maintenance spend). SAM: $680M (DoD facilities with acoustic sensor-compatible HVAC systems). SOM: $42M by Year 5 (Phase II awardee → contract vehicle → 6% SAM penetration)."

*SIPP Example:* "TAM: $3.8B (US smart home water management). SAM: $420M (tech-forward homeowners in high water-cost markets). SOM: $28M by Year 5 (85K subscribers at $9/month + device revenue)."

**Traction:**
- Current metrics (MRR, customers, growth rate, TRL, pilot deployments)
- Key milestones achieved

**Financial Snapshot:**
```
| Metric      | Current | Year 1 | Year 2 | Year 3 |
|-------------|---------|--------|--------|--------|
| ARR/Revenue | $X      | $Y     | $Z     | $W     |
| Customers   | X       | Y      | Z      | W      |
| Team Size   | X       | Y      | Z      | W      |
```

**Funding Ask / SBIR Request:**
- Amount seeking (or Phase II award amount)
- Use of proceeds / budget justification (top 3–4)
- Expected milestones at end of period

---

### Section 2: Problem & Market Opportunity (2–3 pages)

**The Problem:**
- Detailed problem description
- Who experiences this problem
- Current solutions and their limitations
- Cost of the problem (quantified)

**Market Landscape:**
- Industry overview
- Key trends driving opportunity

*CC Framing:* Lead with procurement trends — Congressional mandates, DoD energy efficiency initiatives, facility modernization budgets. Reference specific programs (e.g., ESTCP, MILCON, DLA facility contracts).

*SIPP Framing:* Lead with smart home adoption curve, IoT penetration data, insurance incentive trends, and municipal water conservation mandates that create regulatory tailwinds.

**Market Sizing (from market-sizing-analysis output):**
- TAM calculation and methodology
- SAM with filters applied
- SOM with assumptions
- Validation and data sources

**Target Customer Profile:**
- Primary segments
- Decision-makers and buying process

*CC Example:* "Primary buyer: DoD Base Operations Support contractors (BASOPS). Decision chain: Base Civil Engineer → Installation Commander → DLA or NAVFAC contracting officer. Procurement vehicle: SAT (<$250K direct award) for pilot; contract vehicle (SEWP, GSA Schedule) for scale."

*SIPP Example:* "Primary buyer: tech-forward homeowner, age 32–55, owns 2,000+ sq ft home, high water bill or prior leak experience. Purchase trigger: insurance discount offer, neighbor referral, or post-leak anxiety. Secondary buyer: property management companies (multi-unit commercial opportunity)."

---

### Section 3: Solution & Product (2–3 pages)

**Product Overview:**
- What it does (features and capabilities)
- How it works (architecture/approach)
- Key differentiators
- Technology advantages / TRL status

*CC TABA Note:* Include TRL assessment. Document current TRL, what was achieved under Phase I, what TRL 7+ demonstration will look like under Phase II. Reference any patents filed or pending.

*SIPP Note:* Describe hardware (sensor type, installation method — clamp-on, no plumbing modification required), firmware, mobile app, and subscription service tiers. Emphasize no-install-professional-required positioning vs. Flo by Moen.

**Value Proposition:**
- Benefits by customer segment
- ROI or value delivered
- Time to value

*CC Example:* "For DoD facility managers: 30–40% reduction in reactive maintenance costs; 15% energy savings from early fault correction; compliance with DoD Instruction 4165.14 facility performance requirements. Payback: 8–14 months."

*SIPP Example:* "For homeowners: average $340/year savings on water bills; $0 insurance deductible on covered leak events (partner program with Hippo, Lemonade); 5-minute DIY installation. Payback: 4 months at $9/month."

**Product Roadmap:**
- Current state
- Near-term (6 months)
- Medium-term (12–18 months)
- Vision (2–3 years)

**Intellectual Property:**
- Patents (filed, pending)
- Proprietary technology or data advantages
- Defensibility

---

### Section 4: Competitive Analysis (2 pages)

**Competitive Landscape:**
- Direct competitors
- Indirect competitors (alternatives)
- Adjacent players (potential entrants)

*CC Competitors:* Existing HVAC monitoring vendors (Intelligent Buildings, Honeywell Building Technologies), manual inspection contractors, incumbent BASOPS service holders. Differentiate on: non-invasive acoustic sensing (no retrofit), ML fault classification accuracy, SBIR-credentialed team.

*SIPP Competitors:* Flume (utility data only, no shutoff), Flo by Moen (professional install required, $500+ hardware), Phyn (plumbing-integrated, complex install), LeakSmart (shutoff only, no analytics). Differentiate on: DIY install, subscription-first pricing, insurance partner ecosystem.

**Competitive Matrix:**
```
| Feature/Factor       | [Venture] | Comp A | Comp B | Comp C |
|----------------------|-----------|--------|--------|--------|
| Feature 1            | ✓         | ✓      | ✗      | ✓      |
| Feature 2            | ✓         | ✗      | ✓      | ✗      |
| Pricing              | $X        | $Y     | $Z     | $W     |
```

**Differentiation:**
- 3–5 key differentiators
- Why these matter to customers
- Defensibility of advantages

**Barriers to Entry:**
- What protects against competition
- Network effects, switching costs, proprietary data moats

---

### Section 5: Business Model & Go-to-Market (2 pages)

**Business Model:**
- Revenue model

*CC Model:* Phase II SBIR award → cost-plus R&D → Phase III transition via OTA, IDIQ, or commercial contract vehicle. Revenue: government contract + licensing IP to BASOPS prime contractors.

*SIPP Model:* Hardware (one-time device revenue, ~$89 MSRP, ~$38 BOM) + subscription ($9/month or $89/year). Gross margin: hardware ~45%; subscription ~82%. Blended Year 3 gross margin target: 68%.

**Go-to-Market Strategy:**
- Customer acquisition channels
- Sales model

*CC GTM:* SBIR Phase II → pilot deployment at 2–3 DoD installations → Phase III transition through AFWERX or NavalX accelerator programs → contract vehicle onboarding (SEWP V, GSA MAS) → BASOPS prime contractor partnerships (Fluor, AECOM, PAE).

*SIPP GTM:* Waitlist (owned audience, email capture) → pre-order campaign (Indiegogo or direct) → subscription launch (D2C via Shopify + Amazon) → insurance partner bundling (year 2) → property management B2B channel (year 3).

**Marketing Strategy:**
- Positioning and messaging
- Channel strategy
- Partnerships

**Customer Success:**
- Onboarding approach
- Retention strategy
- Net dollar retention target

---

### Section 6: Financial Projections (2–3 pages)

**Revenue Model:**
- Cohort-based projections
- Key assumptions
- Revenue breakdown by segment

*SIPP Specific — Hardware vs. Subscription Split:*
```
| Stream        | Year 1 | Year 2 | Year 3 |
|---------------|--------|--------|--------|
| Hardware Rev  | $X     | $X     | $X     |
| Sub Rev (MRR) | $X     | $X     | $X     |
| Total Rev     | $X     | $X     | $X     |
| Blended GM    | XX%    | XX%    | XX%    |
```

*CC Specific — Contract vs. Commercial Split:*
```
| Stream            | Phase II | Year 1 Post | Year 2 Post |
|-------------------|----------|-------------|-------------|
| SBIR Award        | $1.75M   | —           | —           |
| Phase III OTA     | —        | $X          | $X          |
| Commercial Rev    | —        | $X          | $X          |
| Total             | $1.75M   | $X          | $X          |
```

**3-Year Financial Summary:**
```
| Metric            | Year 1   | Year 2   | Year 3   |
|-------------------|----------|----------|----------|
| Revenue           | $X.XM    | $Y.YM    | $Z.ZM    |
| Gross Margin      | XX%      | XX%      | XX%      |
| Operating Expenses| $X.XM    | $Y.YM    | $Z.ZM    |
| Net Income        | ($X.XM)  | ($Y.YM)  | $Z.ZM    |
| EBITDA Margin     | (XX%)    | (XX%)    | XX%      |
```

**Unit Economics:**
- CAC: $X,XXX
- LTV: $X,XXX
- LTV:CAC ratio: X.X
- CAC Payback: XX months
- Gross margin: XX%

**Scenario Analysis:**
- Conservative, base, optimistic
- Key drivers and sensitivities

**Path to Profitability:**
- Break-even timeline
- Key milestones
- Unit economics at scale

---

### Section 7: Team & Organization (1–2 pages)

**Leadership Team:**
For each founder/executive:
- Name, title
- Relevant background (2–3 sentences)
- Key accomplishments
- Why uniquely qualified

*CC TABA Note:* Include PI credentials prominently. List relevant publications, prior SBIR experience, security clearance status if applicable, and industry partner relationships (letters of support). SBIR reviewers weight team heavily — PI background is often the deciding factor.

*SIPP Note:* Highlight hardware + SaaS hybrid experience. Note any IoT or consumer electronics supply chain relationships. Advisory board with insurance or smart home distribution experience adds credibility.

**Current Team:**
- Headcount by department
- Key hires and their backgrounds
- Advisory board

**Hiring Plan:**
- Year 1–3 headcount growth
- Key roles to fill

**Organization Evolution:**
```
Current (X people) → Year 1 (X) → Year 2 (X) → Year 3 (X)
Engineering:     X → X → X → X
Sales & Marketing: X → X → X → X
Operations:      X → X → X → X
```

---

### Section 8: Traction & Milestones (1 page)

**Current Traction:**
- Revenue or user metrics
- Growth rate
- Key customer wins or pilot deployments
- Product development progress / TRL status

**Milestones Achieved:**
- Product launches
- Funding rounds / SBIR awards
- Team hires
- Customer acquisition or pilot sign-offs
- Partnerships or letters of support

**Upcoming Milestones (12–18 months):**
- Product milestones / TRL advancement targets
- Revenue targets
- Customer or deployment goals
- Team goals
- Partnership or contract vehicle goals

---

### Section 9: Risks & Mitigation (1 page)

**Market Risks:**
- Market size assumptions
- Competitive intensity
- Substitute adoption
- Mitigation strategies

*CC Risk Note:* Include technology risk (TRL advancement timeline) and transition risk (Phase II → III is not guaranteed; mitigate with MOUs from transition partners and AFWERX/NavalX relationships).

*SIPP Risk Note:* Include supply chain risk (hardware component sourcing), consumer adoption curve risk, and subscription churn risk. Mitigate with insurance partner bundling (reduces churn) and modular BOM design.

**Execution Risks:**
- Product development
- Go-to-market effectiveness
- Hiring and retention

**Financial Risks:**
- Burn rate management
- Fundraising market or SBIR award timeline
- Unit economics assumptions

**Regulatory/External Risks:**
- Compliance requirements (CC: cybersecurity, CMMC; SIPP: FCC, UL certification)
- Economic conditions

---

### Section 10: Funding Request & Use of Proceeds (1 page)

**Funding Ask / SBIR Budget:**
- Amount seeking: $X.XM (or Phase II award: $1.75M typical)
- Structure: Equity, SAFE, convertible note — or Phase II cost-plus budget
- Target valuation (if equity raise)

*CC TABA Note:* For SBIR Phase II, structure this as a budget justification: direct labor, indirect, materials, subcontractors, travel, fee. SBIR reviewers evaluate whether the budget is credible and appropriately scoped for the proposed work.

**Use of Proceeds:**
```
Total Raise / Award: $X.XM
- R&D / Product Development: $X.XM (XX%)
  • [Specific work items]

- Sales & Marketing / Transition Activities: $X.XM (XX%)
  • [Specific activities]

- Operations & G&A: $X.XM (XX%)
  • [Specific items]

- Working Capital / Buffer: $X.XM (XX%)
```

**Milestones to Achieve with This Funding:**
- Revenue: $X.XM ARR or contract value
- Customer/deployment: XXX customers or X pilot sites
- Product: Key features or TRL milestone
- Team: XX employees
- Next step: Series A readiness or Phase III transition

**Expected Timeline:**
- 18–24 month runway (or Phase II period of performance: 24 months)
- Achieve milestones in 15–18 months
- 6-month buffer for next raise or transition activities

---

### Step 4: Enhance with Visuals

Suggest including:
- Charts for market sizing (TAM funnel)
- Product screenshots or mockups
- Positioning maps
- Financial trend charts (revenue, customers, burn)
- Organization chart
- Timeline/roadmap
- Use of proceeds breakdown

### Step 5: Provide Additional Sections (Optional)

**If Relevant, Add:**
- Regulatory/Compliance section (CC: CMMC, ITAR; SIPP: FCC, UL)
- Technology Architecture (CC: acoustic sensor pipeline, ML stack; SIPP: IoT firmware, cloud backend)
- SBIR Commercialization History (CC only — required section in most Phase II applications)
- Unit Economics Deep Dive (SIPP: hardware margin + LTV analysis)
- Strategic Partnerships and Letters of Support (CC: transition partner MOUs)

### Step 6: Create Executive Summary Slide

One-page summary:
- Problem & Solution (3 bullets each)
- Market: TAM/SAM/SOM
- Traction: Key metrics or TRL status
- Team: Founders/PI
- Ask: Amount and use
- Contact information

### Step 7: Save Business Case

Save as markdown:
- Filename: `business-case-[venture]-YYYY-MM-DD.md`
- Store in Craft under venture folder
- Suggest converting to PDF for external sharing
- For SBIR: export sections as Word docs per agency template requirements

---

## Best Practices

**Do:**
- Lead with customer or government problem
- Quantify everything — procurement dollars, TRL gaps, water loss statistics
- Show market pull evidence, not just market size
- Be realistic on projections
- Acknowledge technology and transition risks honestly
- Cite all data sources
- Keep executive summary concise (2 pages max)
- Focus on differentiation and defensibility

**Don't:**
- Use VC pitch language for SBIR audiences
- Make unsupported claims about TAM without citing sources
- Ignore competition — especially incumbent BASOPS contractors (CC) or Flo/Flume (SIPP)
- Be overly optimistic on adoption curves
- Skip the "why now" — regulatory tailwinds, mandate timing, smart home inflection
- Use generic templates without venture-specific customization

## Limitations

- Business case creation takes 1–2 hours for a complete document.
- Output is a structured draft — validate all financial assumptions against actual models.
- SBIR commercialization plan sections require PI review before submission.
- Do not treat financial projections as substitutes for a dedicated financial model.
- Stop and ask for clarification if venture context, audience, or available materials are unclear.
