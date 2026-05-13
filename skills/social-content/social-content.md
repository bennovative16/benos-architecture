# Social Content

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
Multi-platform social content (LinkedIn, X, Instagram) with 4 distinct BenOS venture voice profiles explicitly embedded. Creates on-brand posts, threads, carousels, and content calendars for all active ventures.

## Triggers
Invoke this skill when:
- Writing any social media post for any BenOS venture
- Building a content calendar
- Creating X threads, LinkedIn posts, or Instagram captions
- Phrases: "social post", "social content", "write for Instagram", "LinkedIn post", "X post", "X thread", "social media", "content calendar", "write a tweet"

## Inputs
- Venture name (SIPP, WIC, CC, or Bennovative)
- Platform (LinkedIn, X, Instagram — or "all")
- Topic or angle (optional — can be derived from product-marketing-context)
- `.agents/product-marketing-context-[venture].md` (run product-marketing-context first if missing)
- Optional: x-research output (outlier analysis) to inform topic selection

## Outputs
- Ready-to-publish post copy per platform
- Subject line / hook variants
- Hashtag recommendations (Instagram only)
- Optional: content calendar grid

## BenOS Integrations
- **product-marketing-context**: Read `.agents/product-marketing-context-[venture].md` for customer language, positioning, and tone before writing
- **x-research**: Feed outlier analysis output as topic input — surface what's already performing in venture-adjacent conversations
- **content-repurposing**: After creating a high-performing post, use content-repurposing to extend it across formats
- **content-creator**: Pairs as the brand_voice_analyzer output informs this skill's voice calibration
- **Higgsfield MCP**: For video creative briefs — hand off Reels/video hooks generated here to Higgsfield for production

## Customization Notes
Full rewrite. Source platform strategy preserved (LinkedIn, X, Instagram best practices). All voice/tone sections replaced with the 4 BenOS venture voice profiles below. Every post framework has 4 venture variants. Source content type templates (thought leadership, story, how-to, etc.) preserved and annotated with per-venture guidance.

---

# Full Instructions

## BenOS Workflow

**Before this skill:** Run `product-marketing-context` for the venture. Load the context file. Optionally run `x-research` to surface high-performing angles in your niche.

**After this skill:** For video content, hand off the hook/script to Higgsfield MCP. For repurposing strong posts, use `content-repurposing`. Log planned posts in Linear or Craft for scheduling.

---

## BenOS Voice Profiles

**Identify the venture first.** Every post must be written in its venture's voice. These are not adjustable — they are brand identities.

### CC (Catalyzing Concepts) — LinkedIn Primary
Professional authority. Deep-tech commercialization expert. SBIR/STTR domain language.

**Language rules:**
- Use: "Phase II awardee", "commercialization plan", "market pull", "technology readiness level", "TABA", "federal program"
- Never use: "client" (use "awardee" or "team"), "business plan" (use "commercialization plan"), "pitch" (use "proposal")

**Tone:** Authoritative but approachable. The voice of someone who has been in 200+ SBIR engagements and has specific things to say about what works. Never generic. Never motivational filler.

**Platform priority:** LinkedIn (primary), occasional X for SBIR policy commentary.

**Example post opener:** "Most Phase II commercialization plans fail before they start. Not because the technology isn't ready — because the market pull section is written to satisfy reviewers, not to guide actual decisions."

---

### WIC (Who Is Coffee) — Instagram Primary, X Secondary
Playful, sensory, direct. Coffee-forward. Farmer stories. Conservation angle. Short sentences. Ritual and relationship.

**Language rules:**
- Use sensory language: smell, taste, texture, temperature, ritual
- Farmer names and origin country/region
- "Your morning" not "our product"
- Active verbs and sentence fragments are welcome

**Tone:** Like a coffee-obsessed friend texting you about a bag they just tried. Not a brand. A person.

**Platform priority:** Instagram (primary), X for quick sensory takes and DTC conversation.

**Example post opener:** "This one smells like brown sugar and dried apricot before you even grind it. Marisol Choc, Guatemala. 1,800 meters."

---

### SIPP — X Primary, LinkedIn Secondary
Technical, aspirational. IoT + smart home. Water quality + environmental stewardship. Trust through data. Aspirational about what "knowing your water" enables.

**Language rules:**
- Data-backed statements: reference EPA findings, contaminant types, health thresholds
- "Your water story" — the idea that your home's water has a history
- Smart home category framing without buzzword overload
- "Home" and "family" as emotional anchors without fear-mongering

**Tone:** The engineer who also cares about their kids. Technical credibility + genuine concern for what matters at home.

**Platform priority:** X (building early community, technical audience), LinkedIn (smart home/IoT investors and partners).

**Example post opener:** "The EPA's updated PFAS limits take effect this year. Most home water filters weren't designed for PFAS. Most homeowners don't know if theirs are working."

---

### Bennovative — X Primary, LinkedIn Secondary
Stoic. Candid. Builder. No hedging. No performative humility. No motivational filler.

**Voice synthesis:** Mark Manson (cuts through noise, direct, willing to be unpopular) × Jocko Willink (ownership, declarative, no excuses) × Ryan Holiday (stoic lens, historically anchored, long view).

**"Doing hard things" is the anchor.** Posts emerge from real experiences building, shipping, failing, and continuing.

**Language rules:**
- Declarative statements over questions
- First-person ownership ("I built", "I decided", "I was wrong")
- Specific observations over general advice
- Historical or philosophical reference if it lands naturally — not forced

**Avoid:** "You've got this!", "Believe in yourself", "Here's what I learned 🧵", corporate LinkedIn motivational posts, humble bragging disguised as vulnerability.

**Platform priority:** X (primary — threads and quick takes), LinkedIn (longer essays with the stoic frame).

**Example post opener:** "Most people spend more time planning their vacation than their next five years. That's not a productivity problem. It's a values problem."

---

## Platform Strategy

### LinkedIn

**Best for:** CC (SBIR thought leadership), Bennovative (founder essays), SIPP (B2B/investor awareness)
**Frequency:** 3–5x per week per venture
**Best times:** Tue–Thu, 7–8am, 12pm, 5–6pm

**What works:**
- Personal stories with specific business lessons (Bennovative, SIPP)
- Contrarian takes on SBIR commercialization norms (CC)
- Behind-the-scenes of building hardware (SIPP)
- Data and original insights (SIPP, CC)
- Carousel posts for frameworks (CC market sizing, SIPP water data)

**Format rules:**
- First line is everything — it must earn the "see more" click
- Line breaks for readability — one idea per paragraph
- Links go in comments, not the post body
- 1,200–1,500 characters performs well
- Tag people sparingly and genuinely

---

### X (Twitter)

**Best for:** WIC (sensory takes, DTC conversation), SIPP (technical community, early waitlist), Bennovative (stoic observations, building in public)
**Frequency:** 3–10x per day (including replies)
**What works:** Hot takes, threads that teach, behind-the-scenes, real-time commentary
**Format rules:** Hook in tweet 1 of any thread. Under 100 characters for single tweets. Quote tweets with added insight over plain retweets.

---

### Instagram

**Best for:** WIC (primary brand channel), SIPP (aspirational lifestyle/smart home)
**Frequency:** 1–2 feed posts per day (WIC), 3–10 Stories
**What works:** High-quality visuals, Reels, carousels with value, UGC
**Format rules:** Reels get 2× reach. First line of caption must hook before the fold. Hashtags in first comment or end of caption (max 5–10 relevant ones for WIC specialty coffee).

---

## Post Frameworks — 4 Venture Variants

### Framework 1: Problem → Insight → Implication

**CC variant:**
> Most Phase II teams treat commercialization planning as a deliverable, not a strategy. The TABA engagement checks a box. The plan sits in a folder. Phase III doesn't happen.
> The plans that actually drive transition start with one question: who is already buying adjacent solutions and why are they underserved?
> That's market pull. Everything else is secondary.

**WIC variant:**
> Most coffee gets roasted to hide its flaws. High heat, fast roast. Consistent, forgettable.
> Single origin changes the equation. You can't hide behind the roast when the coffee has to stand on its own.
> Marisol's Guatemala does. Tasting notes tomorrow.

**SIPP variant:**
> Most home water filters reduce chlorine taste. That's it.
> They weren't designed for PFAS, lead, or the contaminants the EPA just updated limits for.
> You don't know what your filter is actually removing. Neither do most manufacturers.

**Bennovative variant:**
> Most people think they lack discipline. They don't.
> They lack clarity on what they're actually trying to build.
> Discipline without direction is just suffering with good optics.

---

### Framework 2: Story → Lesson

**CC variant:**
> A Phase I awardee came to us with a commercialization plan. 40 pages. Beautiful formatting.
> Not a single mention of who their first 10 customers would be or why those customers would switch from their current solution.
> That's the plan reviewers accept. It's not the plan that gets you to Phase III.
> The market pull section is the whole game.

**WIC variant:**
> We almost didn't buy this lot. The farm was new to us. No prior relationship.
> Then we saw the processing method — washed, 21-day fermentation, hand-sorted twice.
> That's not efficiency. That's care.
> First cup told us everything. Now it's in the bag that shipped this week.

**SIPP variant:**
> A homeowner in Flint thought their water was safe because they had a filter.
> It was a carbon block filter. Doesn't touch lead.
> The filter had been there for 11 years, unchanged.
> Knowing you have a filter isn't the same as knowing what it's doing.

**Bennovative variant:**
> I delayed shipping SIPP's waitlist page for three weeks because I wanted it to be "perfect."
> The version I finally pushed was version 1. Not perfect.
> Version 2 was better. Version 3 better still.
> The delay cost me three weeks of waitlist signups. Perfectionism is procrastination in a lab coat.

---

### Framework 3: Contrarian Take

**CC variant:**
> Hot take: most SBIR commercialization plans are written for the wrong audience.
> They're written for program managers. They should be written for the first customer.
> If you can't name the first company that will write you a check after Phase II, the plan isn't done.

**WIC variant:**
> You don't need a fancy grinder to brew good coffee.
> You need fresh beans, clean water, and a consistent ratio.
> The gear gap is smaller than the freshness gap. Buy fresher, not fancier.

**SIPP variant:**
> Smart home devices got popular because they're convenient. Not because they make homes safer.
> A smart lock doesn't prevent break-ins. A smart thermostat doesn't prevent house fires.
> Water quality monitoring is different. It's the first smart home category that directly affects your family's health.

**Bennovative variant:**
> "Work-life balance" is a millennial myth.
> Not because balance is bad — because the metaphor is wrong.
> Life and work aren't two sides of a scale. They're two things happening simultaneously.
> You don't balance them. You decide which one gets your best hours.

---

### Framework 4: Thread Hook (X)

**CC variant:**
Tweet 1: `Thread: The 5 things that separate Phase II commercialization plans that drive real transition from the ones that collect dust.`

**WIC variant:**
Tweet 1: `Why single origin coffee costs more and why it's worth it. A thread for skeptics.`

**SIPP variant:**
Tweet 1: `What I learned after testing 40 home water filters. Most of them don't do what the label says.`

**Bennovative variant:**
Tweet 1: `I've been building for 3 years with no outside funding. Here's what nobody tells you about staying solvent while building something real.`

---

## Content Types by Venture

### CC Content Mix (LinkedIn-first)
- 40%: SBIR/commercialization insight posts (the "market pull" type)
- 30%: Case studies or anonymized Phase II examples (what worked, what didn't)
- 20%: SBIR policy commentary (new solicitations, agency priorities, TABA program changes)
- 10%: CC company news or Ben's personal perspective on consultancy work

### WIC Content Mix (Instagram-first)
- 40%: Coffee origin stories and farm features
- 30%: Brew education and ritual content
- 20%: Product launches and new arrivals
- 10%: Behind-the-scenes of sourcing and roasting

### SIPP Content Mix (X-first)
- 40%: Water quality education and news commentary (EPA updates, contamination events)
- 30%: Building in public (hardware dev, app progress, waitlist milestones)
- 20%: Smart home category positioning
- 10%: Waitlist/early access content

### Bennovative Content Mix (X-first)
- 50%: Stoic observations about building, decision-making, and doing hard things
- 25%: Behind-the-scenes of the BenOS ventures (candid, specific, not curated)
- 25%: Herk's Hits newsletter excerpts and philosophy

---

## Output Format

For each post, provide:

```
Platform: [LinkedIn / X / Instagram]
Venture: [CC / WIC / SIPP / Bennovative]
Type: [Single post / Thread / Carousel / Reel script]
Hook/First line: [The opening line]
Body: [Full copy]
CTA: [If applicable]
Hashtags: [Instagram only, 5–10 max]
Notes: [Scheduling or visual direction if relevant]
```

---

## Quality Check

Before presenting:
1. Does it sound like the right venture's voice? Read it as if you're the audience.
2. Is the first line strong enough to earn the read?
3. Is there one clear point — not three?
4. For CC: does it use SBIR domain language correctly?
5. For WIC: is there at least one sensory detail?
6. For SIPP: is there a data anchor or specific technical claim?
7. For Bennovative: does it pass the "motivational filler" test? (Cut anything that sounds like a poster.)

---

## Related BenOS Skills

- **x-research**: Research high-performing X content before planning topics
- **content-repurposing**: Extend top posts across platforms and formats
- **content-creator**: Full brand voice engine — runs brand_voice_analyzer for deeper calibration
- **copy-editing**: Run finished drafts through Seven Sweeps for polish
- **Higgsfield MCP**: Hand off video hooks/scripts for Reels and short-form video production
