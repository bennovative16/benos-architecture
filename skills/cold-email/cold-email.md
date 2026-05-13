# Cold Email

## BenOS Metadata

| Field | Value |
|-------|-------|
| Source | Antigravity |
| BenOS Fit | 5/5 |
| Ventures | CC |
| API Status | Green |
| Voice Injection | Heavy |
| Group | SALES |

## Purpose
Anti-template cold outreach framework for CC (Catalyzing Concepts) relaunch. Peer-not-vendor positioning for SBIR/STTR outreach — reactivating 200+ prior engagements and targeting new Phase I awardees for TABA.

## Triggers
Invoke this skill when:
- Writing cold emails for CC prospect outreach
- Building a CC reactivation sequence for prior clients
- Creating SBIR Phase I awardee targeting emails
- Writing follow-up sequences for CC consultancy
- Phrases: "cold email", "outreach sequence", "prospect email", "CC outreach", "SBIR outreach", "reactivate clients", "TABA outreach"

## Inputs
- Prospect type: reactivation (prior engagement contact) or new (Phase I awardee)
- Prospect data: PI name, institution, agency, award date, solicitation number, project title (from sbir.gov)
- `.agents/product-marketing-context-cc.md` (run product-marketing-context for CC if missing)
- Optional: Apollo.io enrichment data (role, LinkedIn, company updates)

## Outputs
- First-touch email (150 words or fewer)
- 3–4 follow-up sequence with angle rotation
- Subject lines for each email
- Personalization notes for each prospect type

## BenOS Integrations
- **apollo-outreach skill**: Upstream — apollo-outreach finds and scores prospects; cold-email writes the sequence
- **sales-enablement skill**: Downstream — after a reply, feed prospect into sales-enablement for pitch materials
- **Linear MCP**: Log replied prospects as Linear issues for pipeline tracking
- **Craft**: Store approved sequence templates for reuse
- **product-marketing-context**: Read `.agents/product-marketing-context-cc.md` before writing

## Customization Notes
Full rewrite of source instructions for CC SBIR/STTR context. Two CC use cases explicitly built out: reactivation of 200–250 prior engagements and new Phase I awardee targeting. SBIR-specific personalization signals defined. Hard ban list enforced. Pairs explicitly with apollo-outreach.

---

# Full Instructions

## BenOS Workflow

**Before this skill:** Run `apollo-outreach` to build your prospect list and scoring. Load `.agents/product-marketing-context-cc.md` for CC positioning, voice, and proof points.

**After this skill:** Log replied prospects as Linear issues. When a prospect responds positively, hand off to `sales-enablement` for pitch deck and proposal materials.

**Two CC use cases — identify which one you're writing for:**

1. **Reactivation:** Prior CC engagement contacts (200–250 people). These people already know CC. They've worked with Ben before or have been in a TABA engagement. The email acknowledges the prior relationship and offers a reason to reconnect.

2. **New SBIR Phase I awardees:** No prior relationship. Cold outreach based on recent award data from sbir.gov. TABA eligibility is the hook.

---

## CC Voice Profile

CC outreach sounds like a **peer expert** reaching out, not a vendor pitching.

**Core positioning:** Ben is a commercialization expert who has done this 200+ times. He is not a consultant trying to win business. He is a specialist who knows what Phase II awardees need before they know they need it.

**Language rules:**
- Use: "Phase II awardee", "commercialization plan", "market pull", "technology readiness", "transition partner", "TABA engagement"
- Never use: "client", "business plan", "pitch", "leverage", "synergy", "best-in-class", "solutions", "circle back", "reach out"
- "I hope this email finds you well" is a hard ban
- "My name is X and I work at Y" as an opener is a hard ban

**Tone calibration:**
- PI (Principal Investigator): Peer-to-peer. Respect their technical expertise. Don't explain what SBIR is.
- Program manager or tech transfer office: Slightly more process-aware. They care about compliance and deliverables.
- First-time awardee: More educational. They may not know what TABA is or why it matters.

---

## Before Writing

**Check product marketing context:**
Read `.agents/product-marketing-context-cc.md` for current CC positioning, proof points, and customer language before writing anything.

Then confirm:
1. Which use case — reactivation or new Phase I?
2. What personalization data is available?
3. What is the desired outcome — a reply, a call, a Calendly link click?
4. Any specific agency or solicitation context?

---

## Writing Principles

### Write like a peer, not a vendor
The email should read like it came from someone who has seen this exact situation dozens of times and has something genuinely useful to say. Use contractions. Read it aloud. If it sounds like marketing copy, start over.

### Every sentence must earn its place
Cold email is ruthlessly short. If a sentence doesn't move the reader toward replying, cut it. Target: under 150 words for first touch.

### Personalization must connect to the TABA opportunity
For new Phase I awardees: the personalization is the award itself — agency, date, project title. The insight is: "Phase I awardees at this stage often don't have a commercialization plan in place yet. That's exactly the window for TABA."

For reactivation: the personalization is the prior relationship. Reference the engagement, the timeframe, or what happened since.

### Lead with their world, not yours
The reader should see their own situation reflected back. "You/your" should dominate over "I/we."

### One ask, low friction
"Worth a quick conversation?" beats "Can we schedule a 30-minute call?" One CTA. Make it easy to say yes with a one-line reply.

---

## Use Case 1: New Phase I Awardee Outreach

**Personalization signals to pull from sbir.gov:**
- Award date (more recent = higher priority)
- Agency and program (NIH STTR, DoD SBIR, NSF SBIR, etc.)
- Solicitation number
- Project title (scan for technology type and application domain)
- PI name and institution

**Personalization signals to pull from Apollo/LinkedIn:**
- PI current role and institution
- Any prior SBIR history (first-time awardee vs. experienced)
- Recent publications or conference presentations

**Email Template — Phase I Awardee, First Touch:**

Subject: `[agency] Phase I — commercialization`
*(2-4 words, lowercase, internal-looking)*

---

> [First name],
>
> Congrats on the [Agency] Phase I award for [project title area — paraphrased, not copy-pasted]. That's a meaningful milestone.
>
> Phase I → Phase II is where commercialization planning either gets done right or gets bolted on last-minute. Most awardees don't have a formal plan in place at this stage — which is exactly when TABA funding is most useful.
>
> I've done 200+ TABA engagements across NIH, DoD, and NSF. Happy to share what a strong commercialization plan looks like for your technology area if that's useful.
>
> Worth a quick exchange?
>
> Ben

---

**Notes on this template:**
- Under 120 words
- Opens with a genuine congratulations that shows you saw their specific award
- The insight ("most awardees don't have a plan at this stage") frames the problem without assuming they have the problem
- Social proof is embedded naturally (200+ engagements), not featured
- CTA is low-friction: "worth a quick exchange" not "let's schedule a call"

---

## Use Case 2: Reactivation — Prior CC Engagement

**Personalization signals:**
- Prior engagement date and approximate scope
- Agency from their prior SBIR award (if known)
- Any public news since the engagement (Phase II award, publication, spin-out, acquisition)

**Email Template — Reactivation, First Touch:**

Subject: `catching up — [their company/institution abbreviated]`

---

> [First name],
>
> It's been a few years since we worked together on [vague reference to engagement — e.g., "your [agency] Phase II commercialization plan"]. Hope the technology has continued to progress.
>
> I've been building out CC's capacity for ongoing commercialization support — not just TABA engagements, but Phase II narrative work, market strategy, and transition planning.
>
> If you're in another award cycle or thinking about Phase III, worth catching up?
>
> Ben

---

**Notes:**
- Acknowledge the prior relationship without overselling it
- Give a reason to reconnect: expanded CC scope
- Don't assume they remember the details — keep the reference vague enough to be credible, specific enough to show you're not mass-spamming
- Under 100 words

---

## Follow-Up Sequences

**Principle:** Each follow-up adds a new angle. "Just checking in" is not a follow-up — it is noise.

**Phase I Awardee — 4-touch sequence:**

| Email | Timing | Angle |
|-------|--------|-------|
| 1 | Day 0 | Award + TABA framing |
| 2 | Day 4 | A specific insight for their technology domain or agency |
| 3 | Day 9 | A brief result from a comparable engagement |
| 4 | Day 16 | Breakup email — honest and brief |

**Email 2 — Domain Insight:**
Subject: `[agency] commercialization patterns`

> [First name],
>
> One thing I see often with [NIH/DoD/NSF] Phase I awardees: the commercialization plan gets written to satisfy the TABA requirement, not to actually guide go-to-market.
>
> The plans that hold up are the ones that start with market pull evidence — who is already buying adjacent solutions and why they're not fully served.
>
> Still happy to dig into this for your technology area. Just need 20 minutes.
>
> Ben

**Email 3 — Social Proof:**
Subject: `similar situation`

> [First name],
>
> Worked with a [similar tech domain] team at [institution type] last year — same stage, same agency. The key unlock for their Phase II commercialization plan was identifying a specific procurement channel that existing competitors weren't serving.
>
> Ended up with a 3-year transition plan that the program office was happy with.
>
> If that sounds useful, I'm available this week.
>
> Ben

**Email 4 — Breakup:**
Subject: `closing the loop`

> [First name],
>
> I've sent a few notes — clearly the timing isn't right, and that's fine.
>
> If you're back in an award cycle or the commercialization question becomes relevant, feel free to reach out: [email or Calendly].
>
> Good luck with the work.
>
> Ben

---

**Reactivation — 3-touch sequence:**

| Email | Timing | Angle |
|-------|--------|-------|
| 1 | Day 0 | Prior relationship + expanded CC scope |
| 2 | Day 5 | New CC capability or recent win relevant to their domain |
| 3 | Day 12 | Breakup — leave the door open |

---

## Hard Ban List

Never use these in CC cold emails:

- "I hope this email finds you well"
- "My name is X and I work at Y" (as an opener)
- "leverage"
- "synergy"
- "reach out" (say "email" or "call")
- "circle back"
- "best-in-class"
- "solutions" (as a standalone noun)
- "disruptive"
- "unique value proposition"
- "I wanted to follow up on my previous email"
- "just checking in"
- "touch base"

---

## Quality Check

Before presenting any email:

1. Does it sound like a human wrote it? Read it aloud.
2. Would YOU reply to this if you received it?
3. Is the personalization connected to the TABA opportunity or the prior relationship?
4. Is there one clear, low-friction ask?
5. Is it under 150 words (first touch)?
6. Does it use CC voice — peer expert, not vendor?
7. Did you check the ban list?

---

## Subject Line Rules

- 2–4 words, lowercase, no punctuation tricks
- Should look like it came from a colleague
- Examples: `phase i → phase ii`, `sbir commercialization`, `catching up`, `taba timing`, `[agency] phase i`
- Never: product pitch, urgency language, prospect's first name in subject line, emojis

---

## Metrics

| Metric | Target |
|--------|--------|
| Open rate | 40–60% (tight list, personalized) |
| Reply rate | 8–15% for reactivation, 3–8% for cold Phase I |
| Positive reply rate | 50%+ of all replies |

If reply rate is below 3% on cold Phase I, check: Is the personalization genuinely specific? Is the CTA friction too high? Is the subject line neutral enough?

---

## Related BenOS Skills

- **apollo-outreach**: Upstream — builds and scores the prospect list
- **sales-enablement**: Downstream — pitch materials after first reply
- **linkedin-profile-optimizer**: CC LinkedIn profile supports credibility; optimize before outreach
- **product-marketing-context**: Source of truth for CC positioning and proof points
