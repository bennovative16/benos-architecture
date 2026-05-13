---
name: micro-saas-launcher
source: Antigravity
benos_fit: 4/5
ventures: Bennovative, SIPP
api_status: Green
voice_injection: Light
group: CONTENT CREATION
date_installed: 2026-05-12
base_skill: vibeship-spawner-skills (Apache 2.0)
customize_level: MEDIUM
---

# Micro-SaaS Launcher

**Purpose**: Expert in launching small, focused SaaS products fast — the indie hacker approach to building profitable software. Covers idea validation, MVP development, pricing, launch strategies, and growing to sustainable revenue. Ship in weeks, not months.

**Role**: Micro-SaaS Launch Architect — you ship fast and iterate. You know the difference between a side project and a business. You help Ben go from idea to paying customers in weeks, not years. You focus on sustainable, profitable businesses — not unicorn hunting.

## Triggers
- "launch a product"
- "new product idea"
- "MVP launch"
- "validate idea"
- "side project launch"
- micro saas, indie hacker, small saas, saas mvp, ship fast

## Inputs
- Product idea or problem statement
- Target audience / who experiences the pain
- Time and resource constraints (solo-founder defaults apply)
- Venture context (Bennovative or SIPP companion product)

## Outputs
- Validation framework with go/no-go signal
- MVP scope (2-week sprint plan)
- Pricing recommendation
- Launch channel prioritization
- Linear tasks for execution
- Craft doc for the product brief

## BenOS Integrations
- **Linear MCP** — create and track tasks for each phase (validation, MVP build, launch, growth)
- **Craft** — generate product brief document including problem statement, MVP scope, pricing, and launch plan
- **GitHub MCP** — initialize code repo with recommended stack structure
- **Pairs with**: `product-manager-toolkit` (RICE scoring pre-flight), `landing-page-generator` (post-validation build), `paid-ads` (validation traffic)

## Customization Notes
- All "project tool" references → Linear
- All "docs" references → Craft
- Stack defaults tuned for solo-founder / Bennovative constraints (Framer, Stripe, Claude API)
- SIPP companion products scoped to digital-only first (no hardware until validated)
- Reactivation threshold embedded: $8k/mo combined active venture revenue unlocks parked ventures

---

## BenOS Workflow

### Before This Skill Runs
Use **product-manager-toolkit** to run RICE scoring on the idea before committing to validation spend. If RICE score < 20, park the idea in the Craft backlog and stop.

### After This Skill Completes
1. Build landing page with **landing-page-generator** (Framer-first for Bennovative)
2. Run **paid-ads** skill to drive validation traffic (Meta or Google, $100–300 test budget)
3. If 3%+ email capture rate → proceed to MVP build sprint in Linear
4. If <3% → pivot or kill

### Reactivation Signal Context
> **BenOS Reactivation Threshold:**
> Parked ventures (CC, Bennovative content products) unlock when combined active venture revenue exceeds $8k/mo. Use this skill to evaluate if a new idea justifies early activation — run RICE first, then apply the reactivation gate before committing build cycles.

---

> **For Bennovative:**
> Use this skill when a new content product, tool, or micro-SaaS idea emerges from the Herk's Hits audience or Bennovative brand. Solo-founder constraints apply: validate demand before building. Stack: Framer (landing page), Stripe (payments), Claude API (if AI-powered). Distribution advantage: existing audience on Herk's Hits newsletter — use it for pre-sales and waitlists before writing a single line of code.

> **For SIPP:**
> SIPP itself is a hardware+app product — use micro-saas-launcher for digital companion products (e.g., water quality report generator, home water score API). Validate purely digital before adding hardware complexity. If a SIPP companion SaaS reaches $2k MRR standalone, it earns its own Linear project.

---

## Idea Validation

### The Validation Framework
| Question | How to Answer |
|----------|---------------|
| Problem exists? | Talk to 5+ potential users (use Herk's Hits audience for Bennovative) |
| People pay? | Pre-sell or find competitors paying customers already |
| You can build? | Can MVP ship in 2 weeks solo? |
| You can reach them? | Distribution channel exists before building |

### Quick Validation Methods

1. **Landing page test** (Bennovative example: "AI water report tool for SIPP users")
   - Build landing page in Framer (1 day)
   - Drive traffic via paid-ads skill ($100–200 Meta test)
   - Measure signups — 3%+ capture rate = green light

2. **Pre-sale** (Bennovative example: "Herk's Hits premium research digest")
   - Post to newsletter: "Join waitlist for 50% off founding member price"
   - If <10 responses from a 1,000-person list — pivot
   - If 30+ responses — ship it

3. **Competitor check** (SIPP example: checking water quality report SaaS market)
   - Competitors = validation of willingness to pay
   - No competitors = possibly no market or you're too early
   - Find gap: what do competitors not do for your specific audience?

### Red Flags
- "Everyone needs this" (too broad — SIPP sells to homeowners, not everyone)
- No clear buyer (who pays — homeowner, realtor, or inspector?)
- Requires marketplace dynamics to work
- Needs massive scale before unit economics work

### Green Flags
- Clear, specific pain point (e.g., "homeowners don't know if their water is safe")
- People already paying for alternatives (e.g., $30 mail-in water tests)
- You have domain expertise (SIPP's water quality knowledge)
- Distribution channel access (Herk's Hits newsletter, SIPP customer base)

---

## MVP Speed Run

### The Stack (Solo-Founder / Bennovative Optimized)
| Component | Choice | Why |
|-----------|--------|-----|
| Frontend | Next.js or Framer | Full-stack or no-code fast |
| Backend | Next.js API / Supabase | Fast, scalable, free tier |
| Database | Supabase Postgres | Free tier, auth included |
| Auth | Supabase / Clerk | Don't build auth |
| Payments | Stripe | Industry standard |
| Email | Resend / Loops | Transactional + marketing |
| Hosting | Vercel | Free tier generous |
| AI features | Claude API | Bennovative AI-powered tools |

### Week 1: Core (Bennovative example: AI water score generator for SIPP)
```
Day 1-2: Auth + basic UI (Supabase + Clerk)
Day 3-4: Core feature — one thing only (e.g., water score generation via Claude API)
Day 5-6: Stripe integration (single paid tier, $29/mo)
Day 7: Polish and bug fixes
```

### Week 2: Launch Ready
```
Day 1-2: Landing page (Framer for Bennovative — fast, no-code)
Day 3: Email flows (welcome, day-3 check-in, day-7 upsell)
Day 4: Legal (privacy policy + ToS — use templates)
Day 5: Final testing, Linear task closure
Day 6-7: Soft launch to Herk's Hits list / SIPP early adopters
```

### What to Skip in MVP
- Perfect design (Framer template is fine)
- All features (one core feature — the water score, the report, the tool)
- Scale optimization (worry at $5k MRR)
- Custom auth (Clerk or Supabase handles it)
- Multiple pricing tiers (start with one paid tier)

---

## Pricing Strategy

### Starting Price Framework
```
What's the alternative cost? (Competitor price or manual work cost)
Your price = 20-50% of alternative cost

Bennovative example (AI content research tool):
- Manual research takes 5 hours/month
- 5 hours × $75/hour = $375 value
- Price: $49-79/month (10-20% of value, audience is creators not enterprise)

SIPP example (water score API for inspectors):
- Home inspector spends 2 hours on water research per inspection
- 2 hours × $100/hour = $200 value
- Price: $29-49/month per inspector
```

### Common Micro-SaaS Prices
| Type | Price Range | Bennovative Fit |
|------|-------------|-----------------|
| Simple content tool | $9-29/month | Herk's Hits audience |
| Pro creator tool | $29-79/month | Bennovative brand tools |
| B2B inspector/pro tool | $49-199/month | SIPP companion products |
| Lifetime deal | 3-5x monthly | Launch + cash flow boost |

### Pricing Mistakes
- Too cheap (undervalues, attracts users who churn when a free alternative appears)
- Too complex (Bennovative audience wants one clear price)
- No free tier AND no trial (hard to sell a water score without showing one sample)
- Charging too late (use pre-sales and waitlists to validate willingness to pay early)

---

## Launch Playbook

### Pre-Launch (2 weeks before)
1. Build email list via Framer landing page
2. Post in relevant communities — give value first (indie hackers, SIPP-adjacent home forums)
3. Create launch assets: demo GIF, 3 screenshots, 1 explainer video
4. Line up 5–10 beta testers from existing audience

### Launch Day Channels (Bennovative-prioritized)
| Channel | Effort | Impact | Bennovative Use |
|---------|--------|--------|-----------------|
| Herk's Hits newsletter | Low | High | First launch always |
| Email list (product-specific) | Low | High | Pre-built waitlist |
| Product Hunt | Medium | High | Broader indie audience |
| Twitter/X | Low | Medium | Bennovative brand |
| Indie Hackers | Low | Medium | Credibility + feedback |
| Reddit (niche subs) | Medium | Medium | SIPP: r/homeimprovement |
| Hacker News | Low | Variable | If technically novel |

### Post-Launch
- Follow up personally with every signup (first 20 are gold)
- Ask for feedback in week 1 — Linear ticket for every actionable piece
- Fix critical bugs same day
- Start SEO/content — document the build process on Herk's Hits for distribution
- Don't stop marketing after launch day — schedule paid-ads skill follow-up

---

## Sharp Edges

### Great product, no way to reach customers

**Severity: HIGH**

Situation: Built product, can't get users.

Bennovative default fix: You have an audience advantage — Herk's Hits newsletter and SIPP customer base are distribution assets. Use them before spending on ads. If neither applies to the product, reconsider the idea.

### Distribution First

**Before building, answer:**
- Where do my customers hang out? (Herk's Hits readers? SIPP homeowners? Inspectors?)
- Can I reach them for free via existing channels?
- Does Bennovative or SIPP have an existing relationship with this audience?
- Is SEO viable, or is this a paid-acquisition play?

### Distribution Channels (Bennovative-tuned)
| Channel | Time to Results | Cost | Best For |
|---------|-----------------|------|----------|
| Herk's Hits newsletter | Immediate | Free | Bennovative products |
| SIPP customer base | Immediate | Free | SIPP companion products |
| SEO | 6–12 months | Low | Long-term organic |
| Paid ads (paid-ads skill) | Immediate | $100+ | Validation and launch |
| Community (Reddit, IH) | 1–3 months | Low | Credibility building |
| Product Hunt | One day | Free | Broader awareness |

### Building for a market that can't/won't pay

**Severity: HIGH**

Bennovative note: Herk's Hits audience skews consumer — test B2C price sensitivity early. SIPP companion products should target pros (inspectors, realtors) over consumers where possible for better price tolerance.

### Market Selection
| Factor | B2B (SIPP inspector tool) | B2C (Bennovative content tool) |
|--------|--------------------------|-------------------------------|
| Price tolerance | $50–200+/mo | $9–29/mo |
| Churn | Lower | Higher |
| Solo-founder friendly | Yes (fewer customers needed) | Harder (need volume) |
| Bennovative fit | SIPP companion products | Herk's Hits audience tools |

### New signups leaving as fast as they come

**Severity: HIGH**

Quick fix for Bennovative products: Onboarding email sequence is critical. Use Loops or Resend. Day 1 welcome, Day 3 check-in if inactive, Day 7 value email. Track in Linear as a recurring task.

---

## Validation Checks (Auto-flags before shipping)

| Check | Severity | Fix |
|-------|----------|-----|
| No payment integration | HIGH | Integrate Stripe — non-negotiable |
| No user authentication | HIGH | Supabase Auth or Clerk — don't build auth |
| No user onboarding | MEDIUM | Welcome flow + first-action prompt + email sequence |
| No product analytics | MEDIUM | PostHog (free tier) — track activation event |
| Missing legal pages | MEDIUM | Privacy policy + ToS — use templates, add before launch |

---

## Collaboration

### Delegation Triggers
- landing page / conversion / Framer → `landing-page-generator`
- stripe / payments / subscription → `stripe`
- SEO / content / organic → `seo`
- paid ads / validation traffic / Meta → `paid-ads`
- backend / API / database → `backend`
- email / newsletter / drip → `email`
- idea scoring / RICE / prioritization → `product-manager-toolkit`

### Bennovative Launch Workflow
```
1. Run RICE scoring via product-manager-toolkit (gate: score >= 20)
2. Validate idea — landing page + paid-ads test ($100-200)
3. If 3%+ capture rate: create Linear project + sprint
4. Build MVP (2-week sprint, solo-founder stack)
5. Build landing page via landing-page-generator (Framer)
6. Launch to Herk's Hits list first, then Product Hunt
7. Post-launch: onboarding, feedback loop, SEO content on Herk's Hits
```

### SIPP Companion Product Workflow
```
1. Identify digital companion idea (water score, report generator, API)
2. Run RICE — must score >= 25 given SIPP hardware complexity overhead
3. Validate digital-only first — no hardware dependencies in MVP
4. Build as standalone micro-SaaS with Stripe payments
5. If $2k MRR standalone → earns its own Linear project
6. Then evaluate hardware integration
```

## Related Skills
Works well with: `product-manager-toolkit`, `landing-page-generator`, `paid-ads`, `stripe`, `seo`, `backend`
