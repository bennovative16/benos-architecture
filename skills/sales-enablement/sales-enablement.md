# Sales Enablement Skill

| Field | Value |
|-------|-------|
| **Skill ID** | sales-enablement |
| **Source** | Antigravity |
| **BenOS Fit** | 4/5 |
| **Ventures** | CC, WIC |
| **API Status** | Green |
| **Voice Injection** | Light |
| **Group** | SALES |
| **Version** | 1.1.0 |
| **Date Added** | 2026-03-21 |

---

## Purpose

Create sales collateral that reps (or founders) actually use — pitch decks, one-pagers, objection-handling docs, proposal templates, and playbooks. Tailored for the BenOS venture stack: CC's federal commercialization motion and WIC's wholesale coffee motion.

## Triggers

Activate this skill when the conversation includes: "sales deck", "pitch deck", "one-pager", "objection handling", "wholesale pitch", "sales collateral"

## Inputs

- Venture context (CC or WIC) — read from `.agents/product-marketing-context-[venture].md` before asking
- Collateral type (deck, one-pager, objection doc, proposal, playbook, persona card)
- Target audience / buyer persona
- Deal stage (prospecting, discovery, demo, negotiation, close)
- Any existing materials to iterate from

## Outputs

| Asset | Deliverable |
|-------|-------------|
| Sales deck | Slide-by-slide outline with headline, body copy, and speaker notes |
| One-pager | Full copy with layout guidance (visual hierarchy, sections) |
| Objection doc | Table format: objection, response, proof point, follow-up |
| Proposal | Section-by-section copy with customization notes |
| Playbook | Structured document with table of contents and sections |
| Persona card | One-page card format per persona |

## BenOS Integrations

- **Craft**: Store finalized sales collateral (decks, one-pagers, objection docs) in the relevant venture's Craft workspace for rep/founder access
- **Pairs with**: `cold-email` skill — after building a deck or one-pager, feed it into cold-email as the "asset being referenced" in outreach sequencing; `apollo-outreach` skill for distribution targeting
- **Reads**: `.agents/product-marketing-context-[venture].md` — always load this before asking intake questions; it contains positioning, differentiators, and buyer language for CC and WIC

## Customization Notes

- CC uses a federal SBIR commercialization framing — never default to VC pitch structure
- WIC leads with the coffee and the farmer story — the company is secondary
- Generic B2B buyer persona language (CTO, VP Sales, CFO) applies to neither venture; use venture-specific buyer maps below
- Replace any generic tool references with BenOS stack: Craft for storage, cold-email for follow-up sequencing, apollo-outreach for targeting

---

## BenOS Workflow

### Before Running This Skill

1. Run the `product-marketing-context` skill (or read `.agents/product-marketing-context-[venture].md`) for the relevant venture — CC or WIC
2. Identify which cold-email sequences are currently active in `apollo-outreach`; the collateral you build here should be referenced in those sequences
3. Confirm the buyer stage and persona so the asset is built for the right moment in the motion

### After Running This Skill

1. Feed the completed deck or one-pager into the `cold-email` skill as the "asset being referenced" — the email should tease/reference the collateral without reproducing it
2. Store the final file in the venture's Craft workspace under the Sales Enablement section
3. If building an objection doc, cross-reference it against any active apollo-outreach sequences and flag objections that aren't addressed in current email copy

---

## Venture Callouts

> **For CC (Catalyzing Concepts):**
> Primary collateral: SBIR Phase II pitch deck + TABA proposal template + objection-handling guide for federal procurement hesitations.
> Deck structure follows commercialization plan narrative: technology readiness → market pull → go-to-market → team. NOT a VC pitch structure.
> Key objections to preemptively handle: "We already have a commercialization plan from SBIR", "We can do this ourselves", "What's the ROI of TABA?", "How is this different from our SBIR program manager's guidance?"
> Language: "Phase II awardee", "commercialization plan", "market pull", "technology readiness level (TRL)". Never: "client", "business plan", "pitch".

> **For WIC (Who Is Coffee):**
> Primary collateral: wholesale pitch one-pager + café/hotel/office buyer deck.
> Targets: specialty coffee shops wanting to add rotating single-origin, boutique hotels, co-working spaces, corporate offices.
> Key objections: "We already have a roaster", "Your MOQ is too high", "How do you handle logistics?", "What's your consistency?"
> Language: sensory, farmer story, conservation angle. Lead with the coffee, not the company.

---

## Before Starting

**Always read venture context first.** If `.agents/product-marketing-context-[venture].md` exists, read it before asking any questions. Only ask for information not already covered or specific to this task.

Gather this context if not covered:

1. **Value Proposition & Differentiators**
   - What do you sell and who is it for?
   - What makes you different from the next best alternative?
   - What outcomes can you prove?

2. **Sales Motion**
   - How do you sell? (direct outreach, inbound, partnerships, hybrid)
   - Average deal size and cycle length
   - Key decision-makers in the buying process

3. **Collateral Needs**
   - What specific asset do you need?
   - What stage of the motion is it for?
   - Who will use it — founder, rep, or the buyer themselves?

4. **Current State**
   - What materials exist today?
   - What's working and what's not?
   - What questions or objections keep coming up?

---

## Core Principles

### Use What Gets Used
Involve the person doing the selling in creation. Use their language. If a founder rewrites the one-pager before sending it, the wrong one-pager was built. Test drafts against real scenarios first.

### Situation-Specific, Not Generic
Tailor to persona, deal stage, and venture. A CC deck for a Phase II PI looks nothing like a WIC one-pager for a boutique hotel buyer. Generic templates fail both.

### Scannable Over Comprehensive
A founder or rep needs the answer in 3 seconds during a live call. Bold headers, short bullets, visual hierarchy. If the answer is buried, the doc has failed.

### Tie Back to the Outcome That Matters
Every claim connects to what the buyer actually cares about. For CC buyers: does this accelerate commercialization and reduce risk? For WIC buyers: will this coffee delight their customers and make their program feel curated?

---

## Sales Deck / Pitch Deck

### 10-12 Slide Framework

1. **Current World Problem** — The pain your buyer lives with today
2. **Cost of the Problem** — What inaction costs (time, money, risk, missed mission)
3. **The Shift Happening** — Market or policy change creating urgency
4. **Your Approach** — How you solve it differently
5. **Proof of Capability** — 3-4 key workflows or service components
6. **Proof Points** — Metrics, case references, relevant recognition
7. **Case Story** — One real story told well
8. **Implementation / Timeline** — How they get from here to working
9. **ROI / Value** — Expected return and payback framing
10. **Investment Overview** — Transparent, structured if tiered
11. **Next Steps / CTA** — Clear action with timeline

**For CC:** Slide order follows commercialization plan narrative — technology readiness → market pull → go-to-market → team. The "problem" is the gap between breakthrough technology and commercial adoption, not a generic pain point. Slide 1 should speak to the Phase II awardee's situation: you've done the science, now the hardest part begins.

**Example CC Slide 1 headline:** "Most Phase II awardees never reach commercial scale — not because the technology fails, but because the commercialization plan does."

**For WIC:** Slide order for a wholesale buyer deck leads with the coffee — origin, process, sensory profile — before talking about the company or program structure. The buyer needs to taste it on the page before they care about logistics. Slide 1 sets the scene with the origin story or a single standout coffee.

**Example WIC Slide 1 headline:** "This coffee came from a farmer in [origin] who has been growing on the same mountain for three generations. Your customers will ask where it came from."

### Deck Principles

- **Story arc, not feature tour.** Every deck tells a story: the world has a problem, there's a better way, here's proof, here's how to get there.
- **One idea per slide.** If you need two points, use two slides.
- **Design for presenting, not reading.** Slides support the conversation — they don't replace it. Minimal text, strong visuals.

### Customization by Buyer Type

| Buyer | Emphasize | De-emphasize |
|-------|-----------|--------------|
| CC: Phase II PI | Commercialization expertise, market pull validation, TABA ROI | Generic consulting deliverables, VC-style metrics |
| CC: Federal program stakeholder | Risk reduction, compliance alignment, commercialization outcome data | Internal process details, team bios |
| WIC: Café buyer | Coffee quality, origin story, differentiation for their menu | Company history, logistics details upfront |
| WIC: Hotel/Office buyer | Curation value, consistency, ease of program management | Deep sensory language, single-origin complexity |

---

## One-Pagers / Leave-Behinds

### When to Use

- **Post-meeting recap** — Reinforce what you discussed, keep momentum
- **Champion internal selling** — Arm your buyer to sell internally for you
- **Cold outreach attachment** — Quick intro that earns a conversation

### Structure

1. **Problem statement** — The pain in one sentence
2. **Your solution** — What you do and how
3. **3 differentiators** — Why you vs. alternatives
4. **Proof point** — One strong metric or real-world result
5. **CTA** — Clear next step with contact info

**CC One-Pager Example:**
- Problem: "Phase II awardees average 3.2 years from award to commercial revenue — most never get there."
- Solution: "CC embeds with Phase II teams to build the commercialization infrastructure SBIR requires but doesn't teach."
- Differentiators: TABA-eligible, market validation methodology, go-to-market execution (not just planning)
- Proof: "[X] Phase II clients, [Y]% reached target commercialization milestones within 18 months"
- CTA: "Book a 30-minute commercialization readiness call"

**WIC One-Pager Example:**
- Problem: "Most wholesale roasters offer the same blends. Your customers notice."
- Solution: "WIC supplies rotating single-origin coffees with full farmer provenance — differentiated for cafés and hospitality buyers who want a program, not just a product."
- Differentiators: Rotating single-origin, conservation sourcing, full storytelling assets included
- Proof: "Currently served in [X] locations across [markets]"
- CTA: "Request a sample set and wholesale pricing sheet"

### Design Principles

- One page, literally. Front only, or front and back maximum.
- Scannable in 30 seconds. Bold headers, short bullets, whitespace.
- Include logo, website, and a specific contact — not a generic inbox.
- Match brand but keep it clean — this is a sales tool, not a brand piece.

---

## Objection Handling Docs

### Objection Categories

| Category | Examples |
|----------|----------|
| Redundancy | "We already have X" |
| Timing | "Not the right time," "Too busy right now" |
| Self-sufficiency | "We can do this ourselves" |
| Value / ROI | "What's the ROI?", "How do we justify the cost?" |
| Authority | "I need to check with my team / program manager" |
| Status quo | "What we have works fine" |

### Response Framework

For each objection, document:

1. **Objection statement** — Exactly how you hear it
2. **Why they say it** — The real concern behind the words
3. **Response approach** — How to acknowledge and redirect
4. **Proof point** — Specific evidence that addresses the concern
5. **Follow-up question** — Keep the conversation moving forward

### CC Objection Handling

| Objection | Real Concern | Response Approach | Follow-up Question |
|-----------|-------------|-------------------|-------------------|
| "We already have a commercialization plan from SBIR" | They think a document = a plan | "A commercialization plan in an SBIR proposal is a requirement — executing one is a different undertaking. What's your current timeline to first commercial revenue?" | "What's the biggest gap between your current plan and actual market traction?" |
| "We can do this ourselves" | Cost / control concern | "Most Phase II teams can. The question is whether the time cost of doing it yourself is the best use of your technical team's capacity during this window." | "What part of commercialization are you most confident in right now?" |
| "What's the ROI of TABA?" | Skeptical of consulting value | "TABA is funded by the award — the ROI question is really about whether the work moves the needle on commercialization outcomes. Our clients have [specific metric]." | "What would a successful commercialization outcome look like for you at the end of Phase II?" |
| "How is this different from our program manager's guidance?" | They value their existing relationship | "Program managers are experts in the SBIR process. We're specialists in what comes after — market validation, go-to-market execution, and partner development. We work alongside that relationship, not against it." | "What's your program manager's guidance on your target market right now?" |

### WIC Objection Handling

| Objection | Real Concern | Response Approach | Follow-up Question |
|-----------|-------------|-------------------|-------------------|
| "We already have a roaster" | Switching cost / loyalty | "We work alongside existing programs — some buyers add WIC as a rotating single-origin option alongside their house blend. No switching required." | "Are your customers asking about origin or single-origin options?" |
| "Your MOQ is too high" | Volume uncertainty | "Our MOQ is [X] — let's talk about what your current usage looks like and whether a sample program makes sense first." | "How much coffee are you going through in a typical month?" |
| "How do you handle logistics?" | Operational uncertainty | "We ship [frequency] with [X] lead time. Here's what the onboarding looks like for a new wholesale account." | "What does your current ordering process look like with your roaster?" |
| "What's your consistency?" | Fear of variability with single-origin | "Single-origin does rotate by season — that's the point, and it's also the story your customers respond to. We brief you on each new coffee so your staff can tell the story." | "How does your team currently talk about coffee with customers?" |

---

## Proposal Templates

### CC Proposal Structure (TABA / Engagement Proposal)

1. **Executive Summary** — The Phase II awardee's current commercialization challenge, CC's proposed engagement, expected outcomes (1 page max)
2. **Commercialization Assessment** — Where they are on the TRL-to-market continuum, gaps identified
3. **Proposed Scope of Work** — Mapped to TABA-eligible activities: market validation, commercialization plan development, go-to-market execution, partner development
4. **Implementation Plan** — Milestone timeline, deliverables, responsibilities
5. **Investment** — TABA-eligible budget, payment structure, what's included
6. **Next Steps** — How to move forward, decision timeline

Language: "Phase II awardee", "commercialization plan", "market pull", "technology readiness level (TRL)", "transition to commercialization". Never: "client engagement", "business plan", "pitch deck", "startup advisory".

### WIC Proposal Structure (Wholesale Account Proposal)

1. **Introduction** — The coffee, the origin, why it fits their program
2. **Program Overview** — What a WIC wholesale account includes (rotating offerings, storytelling assets, ordering process)
3. **Selected Coffees** — Current available coffees with tasting notes and farmer provenance
4. **Logistics & Ordering** — MOQ, lead times, payment terms
5. **Pricing** — Transparent per-pound pricing by volume tier
6. **Next Steps** — Sample order CTA, account setup process

Language: sensory descriptors, farmer names/stories, origin geography, conservation sourcing. Lead with the coffee, close with the logistics.

### Customization Guidance

- Mirror language from the discovery conversation
- Reference specific things the buyer said about their program or challenge
- Include only relevant proof points (same venture context)
- Name the people you've spoken with

### Common Mistakes

- **Too long** — If it's over 7 pages, it won't get read. Aim for 4-6.
- **Too generic** — Templated proposals signal low effort. Customize the executive summary at minimum.
- **Burying the price** — Don't make them hunt for it. Be transparent and confident.

---

## Sales Playbooks

### What Goes in a Playbook

- **Buyer profile** — Who you're selling to, their goals and pains
- **Qualification criteria** — What makes a real opportunity vs. a tire-kicker
- **Discovery questions** — Organized by topic, not a script
- **Objection handling** — Top objections with full response framework
- **Competitive positioning** — How you win against each alternative
- **Collateral map** — Which asset to use at each stage
- **Email templates** — Follow-up, proposal, check-in, re-engage

### CC Playbook Snapshot

- **Buyer profile**: Phase II SBIR awardees in technology sectors (cleantech, biotech, defense tech, advanced manufacturing); PI or CEO; funded but pre-commercial
- **Qualification**: Has a Phase II award active or recently completed; has a commercialization requirement; lacks internal commercial development capacity
- **Discovery questions**: "What does your commercialization plan say about your target market?" / "What's your timeline to first commercial revenue?" / "Have you engaged TABA before?"
- **Collateral map**: Cold outreach → CC one-pager; first call → commercialization readiness framework; proposal stage → TABA engagement proposal

### WIC Playbook Snapshot

- **Buyer profile**: Specialty café operators, boutique hotel F&B directors, co-working space operators, corporate office managers; decision-maker or influencer on coffee program
- **Qualification**: Currently has a coffee program; open to differentiation; volume sufficient for MOQ; values provenance or story
- **Discovery questions**: "How do you currently talk about your coffee with customers?" / "Are you hearing requests for single-origin or specialty options?" / "Who's your current roaster and what do you like about working with them?"
- **Collateral map**: Cold outreach → WIC one-pager with sample offer; first call → wholesale deck; proposal stage → account proposal with selected coffees

---

## Buyer Persona Cards

### CC Personas

| Field | Phase II PI / Founder | Federal Program Stakeholder |
|-------|-----------------------|----------------------------|
| Role | Principal Investigator or CEO of Phase II awardee | SBIR/STTR program manager or DoD/DOE commercialization office |
| Goals | Reach commercial revenue; fulfill SBIR commercialization requirement; protect technical team's time | Portfolio companies reach commercial milestones; federal investment translates to market impact |
| Pains | Gap between lab capability and commercial execution; no playbook for market validation; SBIR process ≠ commercialization process | Awardees stall post-Phase II; commercialization plans are documents, not execution |
| Top Objections | "We can do this ourselves"; "We already have a plan"; "What's the ROI?" | "Is this TABA-eligible?"; "What's your track record?" |
| Messaging Angle | "You've done the hard science. CC does the hard commercialization." | "We turn Phase II commercialization requirements into real market outcomes." |

### WIC Personas

| Field | Specialty Café Buyer | Hotel / Office Buyer |
|-------|---------------------|---------------------|
| Role | Owner or head barista making purchasing decisions | F&B director, office manager, or procurement lead |
| Goals | Differentiated menu; happy customers; program that tells a story | Easy, consistent program; positive guest/employee response; no operational headaches |
| Pains | All roasters starting to sound the same; customers ask where it's from | Current coffee is generic; hard to find a roaster who handles logistics cleanly |
| Top Objections | "We already have a roaster"; "Single-origin is inconsistent" | "Your MOQ is too high"; "How do you handle logistics?" |
| Messaging Angle | "Your customers will ask where it came from." | "A curated coffee program your team doesn't have to manage from scratch." |

---

## Task-Specific Questions

If context is missing, ask:

1. Which venture is this for — CC or WIC?
2. What collateral do you need? (deck, one-pager, objection doc, proposal, playbook)
3. Who will use it — founder doing outreach, or the buyer reviewing it?
4. What stage of the motion is this for? (prospecting, first call, proposal, close)
5. What are the top 2-3 objections coming up right now?

---

## Related Skills

- **cold-email**: For outbound prospecting emails that reference this collateral as the asset
- **apollo-outreach**: For distribution targeting and sequence management
- **product-marketing-context**: For foundational positioning and messaging by venture
- **taba-proposal**: For full TABA proposal generation (CC-specific)
- **copywriting**: For marketing website copy
- **competitor-alternatives**: For public-facing comparison pages

## Limitations

- Use this skill only when the task clearly matches the scope described above.
- Do not treat output as a substitute for environment-specific validation or expert review.
- Stop and ask for clarification if required venture context, permissions, or success criteria are missing.
