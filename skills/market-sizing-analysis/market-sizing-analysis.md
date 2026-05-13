# market-sizing-analysis

| Field | Value |
|---|---|
| **Skill Name** | market-sizing-analysis |
| **Source** | Antigravity |
| **BenOS Fit** | 5/5 |
| **Ventures** | CC, SIPP, WIC |
| **API Status** | Green |
| **Voice Injection** | Light |
| **Group** | MARKETING |
| **Risk** | safe |
| **Customize Level** | LIGHT |

## Purpose

Comprehensive market sizing methodologies for calculating Total Addressable Market (TAM), Serviceable Available Market (SAM), and Serviceable Obtainable Market (SOM) for startup opportunities. Produces credible, investor-ready market analyses using three complementary approaches: top-down, bottom-up, and value theory.

## Triggers

Use this skill when the user says or asks about:
- "market sizing"
- "TAM SAM SOM"
- "market opportunity"
- "addressable market"
- "market analysis"
- Working on market sizing analysis tasks or workflows
- Needing guidance, best practices, or checklists for market sizing analysis

## Inputs

- Problem statement and product/service category
- Target customer definition (segment, geography, size)
- Time horizon (typically 3–5 years)
- Available data sources (industry reports, customer data, competitive intel)
- Audience for the output (investors, internal strategy, SBIR reviewers)

## Outputs

- TAM/SAM/SOM calculations with documented methodology and assumptions
- Triangulated results across two or more methodologies
- Formatted market sizing narrative ready for pitch decks, SBIR commercialization plans, or strategy documents
- Stored as a Craft document for the relevant venture

## BenOS Integrations

- **Craft**: Store completed market analyses as Craft documents. Title format: `[Venture] Market Sizing — [Date]`. Link from venture workspace.
- **Linear**: If market sizing is part of a larger initiative (e.g., SBIR Phase II application), create a Linear issue for tracking and link the Craft doc.
- **Pairs with**: `startup-business-analyst-business-case` — market sizing is a required input section for full business case builds.
- **Primary deliverable for**: CC TABA engagements — every TABA proposal requires a TAM/SAM/SOM section. Use this skill to produce it.

## Customization Notes

- Tool references updated: "your project tool" → Linear; "docs" → Craft.
- Venture-specific callout blocks added after the TAM/SAM/SOM framework section.
- Venture-specific examples added to each of the three sizing methodologies.
- Generic examples (email marketing SaaS) retained as methodology illustrations; venture examples provide additional context.

---

## Instructions

### Overview

Market sizing provides the foundation for startup strategy, fundraising, and business planning. Calculate market opportunity using three complementary methodologies: top-down (industry reports), bottom-up (customer segment calculations), and value theory (willingness to pay).

---

### The Three-Tier Market Framework

**TAM (Total Addressable Market)**
- Total revenue opportunity if achieving 100% market share
- Defines the universe of potential customers
- Used for long-term vision and market validation
- Example: All email marketing software revenue globally

**SAM (Serviceable Available Market)**
- Portion of TAM targetable with current product/service
- Accounts for geographic, segment, or capability constraints
- Represents realistic addressable opportunity
- Example: AI-powered email marketing for e-commerce in North America

**SOM (Serviceable Obtainable Market)**
- Realistic market share achievable in 3-5 years
- Accounts for competition, resources, and market dynamics
- Used for financial projections and fundraising
- Example: 2-5% of SAM based on competitive landscape

---

> **For CC SBIR Engagements:**
> Market sizing in SBIR commercialization plans requires "market pull" framing, not just size. Agencies want evidence that the market is ready to adopt the technology NOW. Structure: (1) total market size, (2) addressable segment with current procurement patterns, (3) specific Phase II awardee's realistic initial market share with timeline. Use bottom-up + value-theory approaches — top-down alone is insufficient for SBIR reviewers.

> **For SIPP (IoT/Smart Home):**
> Relevant market frames: smart home device market ($135B+ globally), water quality monitoring market, home services subscription market. Use bottom-up: # US homeowners × concern rate for water quality × willingness to pay. Reference EPA data on PFAS/lead contamination as market pull evidence.

> **For WIC (Specialty Coffee DTC):**
> Market frame: US specialty coffee market (~$50B), DTC coffee subscription segment. Use bottom-up: target metro areas × coffee-enthusiast household % × subscription willingness. Reference SCA (Specialty Coffee Association) reports for category data.

---

### When to Use Each Methodology

**Top-Down Analysis**
- Use when established market research exists
- Best for mature, well-defined markets
- Validates market existence and growth
- Starts with industry reports and narrows down

**Bottom-Up Analysis**
- Use when targeting specific customer segments
- Best for new or niche markets
- Most credible for investors
- Builds from customer data and pricing

**Value Theory**
- Use when creating new market categories
- Best for disruptive innovations
- Estimates based on value creation
- Calculates willingness to pay for problem solution

---

### Three-Methodology Framework

#### Methodology 1: Top-Down Analysis

Start with total market size and narrow to addressable segments.

**Process:**
1. Identify total market category from research reports
2. Apply geographic filters (target regions)
3. Apply segment filters (target industries/customers)
4. Calculate competitive positioning adjustments

**Formula:**
```
TAM = Total Market Category Size
SAM = TAM × Geographic % × Segment %
SOM = SAM × Realistic Capture Rate (2-5%)
```

**When to use:** Established markets with available research (e.g., SaaS, fintech, e-commerce)

**Strengths:** Quick, uses credible data, validates market existence

**Limitations:** May overestimate for new categories, less granular

**Venture Example — CC (SBIR):**
TAM = $4.2B federal environmental monitoring market (EPA + DoD + DOE combined budget lines). Apply segment filter: water quality instrumentation = 22% = $924M SAM. Apply geographic/procurement filter: SBIR-eligible small business addressable contracts = ~8% = $74M SOM universe. Note: top-down alone is insufficient for SBIR reviewers — always pair with bottom-up.

---

#### Methodology 2: Bottom-Up Analysis

Build market size from customer segment calculations.

**Process:**
1. Define target customer segments
2. Estimate number of potential customers per segment
3. Determine average revenue per customer
4. Calculate realistic penetration rates

**Formula:**
```
TAM = Σ (Segment Size × Annual Revenue per Customer)
SAM = TAM × (Segments You Can Serve / Total Segments)
SOM = SAM × Realistic Penetration Rate (Year 3-5)
```

**When to use:** B2B, niche markets, specific customer segments

**Strengths:** Most credible for investors, granular, defensible

**Limitations:** Requires detailed customer research, time-intensive

**Venture Example — SIPP (IoT/Smart Home):**
- US homeowners: ~84M households
- % with expressed concern about water quality (EPA survey data on PFAS/lead): ~34% = 28.6M households
- % willing to pay for a connected monitoring device (survey proxy): ~12% = 3.4M households
- Average annual subscription + device revenue: $180/year
- TAM = 3.4M × $180 = $612M
- SAM (initial launch metros, Midwest + Sun Belt focus): ~15% of TAM = $92M
- SOM Year 3 (2% penetration of SAM): $1.8M; Year 5 (5%): $4.6M

---

#### Methodology 3: Value Theory

Calculate based on value created and willingness to pay.

**Process:**
1. Identify problem being solved
2. Quantify current cost of problem (time, money, inefficiency)
3. Calculate value of solution (savings, gains, efficiency)
4. Estimate willingness to pay (typically 10-30% of value)
5. Multiply by addressable customer base

**Formula:**
```
Value per Customer = Problem Cost × % Solved by Solution
Price per Customer = Value × Willingness to Pay % (10-30%)
TAM = Total Potential Customers × Price per Customer
SAM = TAM × % Meeting Buy Criteria
SOM = SAM × Realistic Adoption Rate
```

**When to use:** New categories, disruptive innovations, unclear existing markets

**Strengths:** Shows value creation, works for new markets

**Limitations:** Requires assumptions, harder to validate

**Venture Example — WIC (Specialty Coffee DTC):**
- Problem: Coffee enthusiasts overpay for commodity beans or waste time sourcing specialty micro-roasters
- Current cost: ~$20–$28/lb for quality specialty coffee from local roasters + ~2 hrs/month sourcing time
- Value of WIC solution: curated access + discovery savings + time saved = ~$35/month equivalent value per subscriber
- Willingness to pay: 20% of value = $7/month subscription premium over commodity alternatives
- Total US specialty coffee households (SCA data proxy): ~18M
- % interested in DTC subscription with discovery/curation: ~8% = 1.44M households
- TAM = 1.44M × $84/year = $121M
- SAM (initial 5 launch metros): ~6% of TAM = $7.3M
- SOM Year 3: $730K; Year 5: $1.8M

---

### Step-by-Step Process

#### Step 1: Define the Market

Clearly specify what market is being measured.

**Questions to answer:**
- What problem is being solved?
- Who are the target customers?
- What's the product/service category?
- What's the geographic scope?
- What's the time horizon?

**Example:**
- Problem: E-commerce companies struggle with email marketing automation
- Customers: E-commerce stores with >$1M annual revenue
- Category: AI-powered email marketing software
- Geography: North America initially, global expansion
- Horizon: 3-5 year opportunity

#### Step 2: Gather Data Sources

Identify credible data for calculations.

**Top-Down Sources:**
- Industry research reports (Gartner, Forrester, IDC)
- Government statistics (Census, BLS, trade associations)
- Public company filings and earnings
- Market research firms (Statista, CB Insights, PitchBook)

**Bottom-Up Sources:**
- Customer interviews and surveys
- Sales data and CRM records
- Industry databases (LinkedIn, ZoomInfo, Crunchbase)
- Competitive intelligence
- Academic research

**Value Theory Sources:**
- Customer problem quantification
- Time/cost studies
- ROI case studies
- Pricing research and willingness-to-pay surveys

#### Step 3: Calculate TAM

Apply chosen methodology to determine total market.

**For Top-Down:**
1. Find total category size from research
2. Document data source and year
3. Apply growth rate if needed
4. Validate with multiple sources

**For Bottom-Up:**
1. Count total potential customers
2. Calculate average annual revenue per customer
3. Multiply to get TAM
4. Break down by segment

**For Value Theory:**
1. Quantify total addressable customer base
2. Calculate value per customer
3. Estimate pricing based on value
4. Multiply for TAM

#### Step 4: Calculate SAM

Narrow TAM to serviceable addressable market.

**Apply Filters:**
- Geographic constraints (regions you can serve)
- Product limitations (features you currently have)
- Customer requirements (size, industry, use case)
- Distribution channel access
- Regulatory or compliance restrictions

**Formula:**
```
SAM = TAM × (% matching all filters)
```

**Example:**
- TAM: $10B global email marketing
- Geographic filter: 40% (North America)
- Product filter: 30% (e-commerce focus)
- Feature filter: 60% (need AI capabilities)
- SAM = $10B × 0.40 × 0.30 × 0.60 = $720M

#### Step 5: Calculate SOM

Determine realistic obtainable market share.

**Consider:**
- Current market share of competitors
- Typical market share for new entrants (2-5%)
- Resources available (funding, team, time)
- Go-to-market effectiveness
- Competitive advantages
- Time to achieve (3-5 years typically)

**Conservative Approach:**
```
SOM (Year 3) = SAM × 2%
SOM (Year 5) = SAM × 5%
```

**Example:**
- SAM: $720M
- Year 3 SOM: $720M × 2% = $14.4M
- Year 5 SOM: $720M × 5% = $36M

#### Step 6: Validate and Triangulate

Cross-check using multiple methods.

**Validation Techniques:**
1. Compare top-down and bottom-up results (should be within 30%)
2. Check against public company revenues in space
3. Validate customer count assumptions
4. Sense-check pricing assumptions
5. Review with industry experts
6. Compare to similar market categories

**Red Flags:**
- TAM that's too small (< $1B for VC-backed startups)
- TAM that's too large (unsupported by data)
- SOM that's too aggressive (> 10% in 5 years for new entrant)
- Inconsistency between methodologies (> 50% difference)

---

### Industry-Specific Considerations

#### SaaS Markets

**Key Metrics:**
- Number of potential businesses in target segment
- Average contract value (ACV)
- Typical market penetration rates
- Expansion revenue potential

**TAM Calculation:**
```
TAM = Total Target Companies × Average ACV × (1 + Expansion Rate)
```

#### Marketplace Markets

**Key Metrics:**
- Gross Merchandise Value (GMV) of category
- Take rate (% of GMV you capture)
- Total transactions or users

**TAM Calculation:**
```
TAM = Total Category GMV × Expected Take Rate
```

#### Consumer Markets

**Key Metrics:**
- Total addressable users/households
- Average revenue per user (ARPU)
- Engagement frequency

**TAM Calculation:**
```
TAM = Total Users × ARPU × Purchase Frequency per Year
```

#### B2B Services

**Key Metrics:**
- Number of target companies by size/industry
- Average project value or retainer
- Typical buying frequency

**TAM Calculation:**
```
TAM = Total Target Companies × Average Deal Size × Deals per Year
```

---

### Presenting Market Sizing

#### For Investors

**Structure:**
1. Market definition and problem scope
2. TAM/SAM/SOM with methodology
3. Data sources and assumptions
4. Growth projections and drivers
5. Competitive landscape context

**Key Points:**
- Lead with bottom-up calculation (most credible)
- Show triangulation with top-down
- Explain conservative assumptions
- Link to revenue projections
- Highlight market growth rate

#### For Strategy

**Structure:**
1. Addressable customer segments
2. Prioritization by opportunity size
3. Entry strategy by segment
4. Expected penetration timeline
5. Resource requirements

**Key Points:**
- Focus on SAM and SOM
- Show segment-level detail
- Connect to go-to-market plan
- Identify expansion opportunities
- Discuss competitive positioning

---

### Common Mistakes to Avoid

**Mistake 1: Confusing TAM with SAM**
- Don't claim entire market as addressable
- Apply realistic product/geographic constraints
- Be honest about serviceable market

**Mistake 2: Overly Aggressive SOM**
- New entrants rarely capture > 5% in 5 years
- Account for competition and resources
- Show realistic ramp timeline

**Mistake 3: Using Only Top-Down**
- Investors prefer bottom-up validation
- Top-down alone lacks credibility
- Always triangulate with multiple methods

**Mistake 4: Cherry-Picking Data**
- Use consistent, recent data sources
- Don't mix methodologies inappropriately
- Document all assumptions clearly

**Mistake 5: Ignoring Market Dynamics**
- Account for market growth/decline
- Consider competitive intensity
- Factor in switching costs and barriers

---

### Quick Start

To perform market sizing analysis:

1. **Define the market** — Problem, customers, category, geography
2. **Choose methodology** — Bottom-up (preferred) or top-down + triangulation
3. **Gather data** — Industry reports, customer data, competitive intelligence
4. **Calculate TAM** — Apply methodology formula
5. **Narrow to SAM** — Apply product, geographic, segment filters
6. **Estimate SOM** — 2-5% realistic capture rate
7. **Validate** — Cross-check with alternative methods
8. **Document** — Show methodology, sources, assumptions in Craft
9. **Present** — Structure for audience (investors, SBIR reviewers, strategy)

---

### Limitations

- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
- SBIR-specific framing (market pull, procurement evidence) is required for federal agency reviewers — generic top-down sizing alone will weaken a commercialization plan score.
