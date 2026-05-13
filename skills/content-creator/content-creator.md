# Content Creator

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
Full content engine with brand voice analysis, SEO optimization, and platform-specific content frameworks. Run `brand_voice_analyzer.py` on each venture's existing copy to lock 4 voice profiles before using downstream skills. The master content skill — everything else draws from it.

## Triggers
Invoke this skill when:
- Creating any long-form content for a BenOS venture
- Establishing or calibrating brand voice for a venture
- Writing SEO-optimized blog posts or articles
- Planning a content calendar or content engine
- Analyzing existing content for voice consistency
- Phrases: "create content", "content engine", "brand voice", "SEO content", "blog post", "write content", "content strategy", "brand voice analyzer", "content calendar"

## Inputs
- Venture name (SIPP, WIC, CC, or Bennovative)
- Content type (blog post, article, newsletter, landing page copy, etc.)
- Primary keyword (for SEO-optimized content)
- Existing content samples (for brand_voice_analyzer.py to analyze)
- `.agents/product-marketing-context-[venture].md` (run product-marketing-context first if missing)

## Outputs
- Brand voice profile (from analyzer) or new venture voice document
- SEO-optimized long-form content
- Content calendar grid (monthly/weekly)
- Platform-specific content adaptations
- Voice consistency score and recommendations

## BenOS Integrations
- **product-marketing-context**: Read `.agents/product-marketing-context-[venture].md` before any content creation — positioning and customer language are the foundation
- **social-content**: Downstream — this skill produces long-form; social-content adapts it to platform formats
- **content-repurposing**: Downstream — after creating a piece, use content-repurposing to extend it
- **copy-editing**: Run finished content through Seven Sweeps for final polish
- **x-research**: Upstream for Bennovative and WIC — surface what's performing before planning topics
- **Craft**: Store completed voice profiles and content calendar templates
- **Linear MCP**: Track content pipeline tasks

## Customization Notes
Full rewrite. Source scripts and workflow preserved. All voice/tone sections replaced with 4 BenOS venture voice profiles. SEO keyword clusters added per venture. brand_voice_analyzer.py usage instructions include venture-specific setup steps. Content calendar distribution ratios customized per venture. Examples throughout are venture-specific.

---

# Full Instructions

## BenOS Workflow

**Step 0 — One-time venture setup (do this first):**
Run `brand_voice_analyzer.py` on each venture's existing copy before using this skill for production content. This locks the voice profile so all future content is consistent.

**Before each content session:** Load `.agents/product-marketing-context-[venture].md` for the active venture.

**After creating content:**
- Long-form → `content-repurposing` to extend across platforms
- Draft copy → `copy-editing` for Seven Sweeps polish
- Social snippets → `social-content` for platform-specific formatting
- Store final pieces in Craft

---

## BenOS Voice Profiles

These profiles are the result of running `brand_voice_analyzer.py` against each venture's existing copy, combined with the explicit voice directives below. **Use these before the analyzer confirms them — they are known, not derived.**

### CC (Catalyzing Concepts)

**Archetype:** Trusted Expert / Advisor
**Tone attributes:** Authoritative, specific, professional, direct, domain-fluent
**Formality:** Professional — but not formal. Reads like a sharp practitioner, not an academic.
**Perspective:** First person ("We've found that...") or declarative observation ("Most Phase II awardees...")

**Brand voice summary:** The voice of someone who has been in 200+ SBIR commercialization engagements and has earned the right to say specific things with confidence. No hedging. No generic advice. Every sentence should only be writable by someone who has seen this pattern dozens of times.

**SEO keyword clusters (CC):**
- Primary: "SBIR commercialization", "TABA engagement", "Phase II commercialization plan"
- Secondary: "SBIR Phase II market strategy", "technology commercialization", "STTR commercialization", "federal technology transfer"
- LSI: "market pull evidence", "TRL progression", "go-to-market for deep tech", "Phase III transition planning"

**Content pillars:**
1. SBIR commercialization how-to (40%) — specific tactical guidance
2. Phase II case studies — anonymized patterns (30%)
3. SBIR ecosystem commentary — agency priorities, policy, funding (20%)
4. CC capabilities and proof points (10%)

---

### WIC (Who Is Coffee)

**Archetype:** Explorer / Creator
**Tone attributes:** Sensory, playful, direct, warm, story-driven
**Formality:** Casual — reads like a message from a coffee-obsessed friend
**Perspective:** Second person ("Your morning starts here") and first person ("We drove 14 hours to get this lot")

**Brand voice summary:** WIC writes the way a specialty coffee buyer talks to someone who just asked why coffee can taste like fruit. Specific. Sensory. Never pretentious. The farmer is the hero, not the brand. Conservation is woven in, not forced.

**SEO keyword clusters (WIC):**
- Primary: "specialty coffee", "single origin coffee", "DTC coffee subscription"
- Secondary: "best single origin coffee", "coffee bean subscription", "specialty coffee roaster"
- LSI: "natural process coffee", "washed process coffee", "coffee origin story", "direct trade coffee", "specialty coffee subscription box"

**Content pillars:**
1. Coffee origin stories and farm features (40%)
2. Brew education and ritual content (30%)
3. Product launches and new arrivals (20%)
4. Behind-the-scenes of sourcing (10%)

---

### SIPP

**Archetype:** Sage / Caregiver (technically grounded, but the care is real)
**Tone attributes:** Technical, aspirational, trustworthy, clear, specific
**Formality:** Semi-professional — reads like an engineer who also cares deeply about their family's health
**Perspective:** Second person ("Your water story") and first person when building in public ("We're still calibrating the sensor for...")

**Brand voice summary:** SIPP earns trust through data and specificity. Not through fear. The voice acknowledges that water quality is a real concern, gives the reader specific information they can act on, and positions SIPP as the tool that turns uncertainty into knowledge. "Your water story" is the emotional hook — the idea that your home has a water history worth knowing.

**SEO keyword clusters (SIPP):**
- Primary: "smart home water quality monitor", "home water quality test", "water quality sensor"
- Secondary: "water safety home", "PFAS home detection", "lead water test home", "IoT water monitor"
- LSI: "water quality app", "home water monitoring system", "smart water monitor", "EPA PFAS limits home", "water quality testing for home"

**Content pillars:**
1. Water quality education (EPA updates, contamination types, health impacts) (40%)
2. Building in public (hardware progress, waitlist milestones, app development) (30%)
3. Smart home category positioning (20%)
4. SIPP product and early access content (10%)

---

### Bennovative

**Archetype:** Outlaw / Explorer (stoic variant)
**Tone attributes:** Direct, candid, specific, philosophically grounded, no filler
**Formality:** Informal — but not casual in the lazy sense. Every word is deliberate.
**Perspective:** First person, always. "I built", "I decided", "I was wrong". Own everything.

**Brand voice summary:** Bennovative content emerges from real experience doing hard things. It is NOT motivational content. It is observational content about what building, failing, and continuing actually looks like — filtered through a stoic lens. Ryan Holiday's long view. Jocko's ownership. Manson's willingness to say the uncomfortable thing. The reader should feel like they just talked to someone who is figuring it out, not someone who has it figured out.

**SEO keyword clusters (Bennovative):**
- Primary: "stoic entrepreneur", "building in public", "founder philosophy"
- Secondary: "stoicism for entrepreneurs", "solo founder lessons", "doing hard things", "entrepreneurship stoicism"
- LSI: "Ryan Holiday", "stoic business principles", "founder mental models", "startup discipline", "building a company alone"

**Content pillars:**
1. Stoic observations about building, deciding, and continuing (50%)
2. Behind-the-scenes of SIPP/WIC/BenOS ventures — specific, candid (25%)
3. Herk's Hits newsletter content and philosophy (25%)

---

## Brand Voice Setup — Running brand_voice_analyzer.py

Run the analyzer on each venture's existing copy before your first content session:

```bash
# Analyze WIC product page copy
python scripts/brand_voice_analyzer.py wic_existing_copy.txt

# Analyze CC proposal/TABA narrative copy
python scripts/brand_voice_analyzer.py cc_existing_copy.txt

# Analyze Bennovative newsletter/X posts
python scripts/brand_voice_analyzer.py bennovative_existing_copy.txt

# Analyze SIPP website copy
python scripts/brand_voice_analyzer.py sipp_existing_copy.txt
```

The analyzer returns:
- Voice profile (formality, tone, perspective)
- Readability score
- Sentence structure analysis
- Improvement recommendations

**Compare output to the voice profiles above.** If there are gaps between the analyzer output and the intended voice profile, the written profiles above take precedence — they represent the aspirational standard, not just the average of existing copy.

---

## Blog Post Creation — 4 Venture Variants

### CC Blog Post Framework

**Target:** SBIR awardees, program managers, tech transfer offices
**Length:** 1,200–2,000 words
**Structure:**
1. Hook: a specific failure pattern in SBIR commercialization (not generic)
2. The root cause: why it happens systemically
3. What good looks like: specific, with examples
4. The framework: actionable steps
5. CTA: link to CC services or a relevant checklist

**SEO approach:** Primary keyword in title and first paragraph. Secondary keywords in H2s. LSI terms throughout.

**Example title:** "Why Most SBIR Phase II Commercialization Plans Fail Before They're Submitted"
**Example H2s:** "The Market Pull Problem", "What Program Reviewers Actually Want to See", "A Framework for Building the Plan That Gets You to Phase III"

---

### WIC Blog Post Framework

**Target:** Specialty coffee enthusiasts, DTC coffee buyers, coffee education seekers
**Length:** 600–1,200 words (shorter, more sensory)
**Structure:**
1. Hook: a sensory or story detail that earns the read
2. The origin context: farm, region, altitude, processing method
3. What makes this lot different (specific, not generic)
4. How to brew it and what to taste for
5. CTA: shop link or subscribe CTA

**SEO approach:** Long-tail coffee keywords. Origin-specific terms. Avoid generic head terms ("best coffee") — compete on specificity.

**Example title:** "Marisol Choc's Natural Process Guatemala: What 1,800 Meters and 21-Day Fermentation Tastes Like"

---

### SIPP Blog Post Framework

**Target:** Homeowners concerned about water quality, smart home adopters, environmental health-conscious consumers
**Length:** 1,000–2,000 words
**Structure:**
1. Hook: a specific water quality fact or news item (EPA ruling, contamination event)
2. The knowledge gap: why most homeowners don't know their water status
3. What SIPP measures and why it matters
4. How to take action (SIPP waitlist + interim steps)
5. CTA: join waitlist

**SEO approach:** Lead with EPA/regulatory terms. Build content around specific contaminant types (PFAS, lead, nitrates). These are high-intent search terms.

**Example title:** "The New EPA PFAS Limits and What They Mean for Your Home Water Supply"

---

### Bennovative Blog / Newsletter Framework (Herk's Hits)

**Target:** Founders, builders, stoic-curious, people doing hard things
**Length:** 400–800 words (essay format, not listicle)
**Structure:**
1. Hook: a direct observation or declarative statement
2. The tension: the thing most people get wrong or avoid
3. The stoic lens: a principle, historical reference, or reframe
4. The application: what this means for building something real
5. No CTA needed — the essay is the value

**Voice test:** Would Ryan Holiday publish this? Would Jocko say this? Does it sound like something someone figured out, not something someone is performing?

**Example title:** "The Sunk Cost Fallacy Isn't About Money"

---

## SEO Optimization Workflow

```bash
# Step 1: Analyze content against primary keyword
python scripts/seo_optimizer.py blog_post.md "primary keyword" "secondary,keywords"

# Step 2: Apply recommendations
# - Adjust keyword density to 1–3%
# - Ensure keyword in title, first paragraph, 2–3 H2s
# - Add meta description (150–160 chars)
# - Check heading structure (one H1, multiple H2/H3)

# Step 3: Re-run to confirm score above 75/100
python scripts/seo_optimizer.py blog_post.md "primary keyword"
```

---

## Content Calendar Distribution

| Day | CC | WIC | SIPP | Bennovative |
|-----|-----|-----|------|-------------|
| Mon | SBIR insight (LinkedIn) | Origin story (Instagram) | Water quality fact (X) | Stoic observation (X) |
| Tue | — | Brew guide (Instagram) | Build update (X) | — |
| Wed | Case study (LinkedIn) | New arrival (Instagram) | Smart home angle (LinkedIn) | Essay (Substack/LinkedIn) |
| Thu | — | UGC / community (Instagram) | — | Behind-the-scenes (X) |
| Fri | SBIR commentary (LinkedIn) | Weekend ritual prompt (Instagram) | Waitlist update (X) | — |

**Monthly planning steps:**
1. Copy `assets/content_calendar_template.md`
2. Set monthly goals per venture (e.g., WIC: 3 origin stories, SIPP: 2 EPA commentary posts)
3. Map content to SEO keyword targets for the month
4. Batch-create: write all CC LinkedIn posts in one session, all WIC Instagram posts in another

---

## Performance Metrics

| Metric | Target |
|--------|--------|
| SEO score | 75+/100 per piece |
| Organic traffic growth | 10–20% MoM per venture (early stage) |
| Email click-through (Bennovative newsletter) | 8–15% |
| Instagram engagement rate (WIC) | 3–6% |
| LinkedIn impressions per post (CC/SIPP) | 500–2,000 in first 24 hours |

---

## Common Pitfalls to Avoid

- **Generic openings:** Never start with "In today's fast-paced world..." or any variation. Start with the specific thing.
- **Voice bleed:** CC voice bleeding into Bennovative content, or WIC voice bleeding into SIPP. Run the voice check.
- **Keyword stuffing:** 1–3% density max. If it reads unnaturally, it's too high.
- **Missing CTAs on commercial content:** WIC and SIPP posts that sell need a CTA. Bennovative posts generally don't.
- **Skipping the analyzer:** Don't create 10 pieces of content before running brand_voice_analyzer on the venture's existing copy. The first session calibration matters.

---

## Related BenOS Skills

- **product-marketing-context**: Keystone — run before this skill for each venture
- **social-content**: Downstream platform-specific content from the long-form produced here
- **content-repurposing**: Extend top-performing content across formats
- **copy-editing**: Seven Sweeps polish for all finished content
- **x-research**: Upstream topic research for Bennovative and WIC
- **Craft**: Store voice profiles, content calendars, and finished pieces
