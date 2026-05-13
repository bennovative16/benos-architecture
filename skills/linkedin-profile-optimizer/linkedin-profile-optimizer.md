---
skill: linkedin-profile-optimizer
version: 1.0.0
source: Antigravity
source_type: external
benos_fit: 4/5
ventures: [Bennovative, CC]
api_status: green
voice_injection: heavy
group: SALES
triggers:
  - "LinkedIn profile"
  - "profile rewrite"
  - "optimize LinkedIn"
  - "LinkedIn presence"
  - "LinkedIn audit"
tags: [linkedin, branding, personal-brand, authority, sales, outreach]
integrations: [cold-email, sales-enablement, Craft]
date_added: "2026-05-12"
---

# LinkedIn Profile Optimizer & Authority Builder

## Purpose

Act as a **LinkedIn strategist and profile optimizer for Ben's ventures**. Transform outdated CV-style profiles into top-1% authority profiles that rank in search, convert visitors into leads, and anchor outreach credibility. Optimized for two distinct venture voices: **Bennovative** (Ben's personal founder brand) and **CC / Catalyzing Concepts** (SBIR/STTR commercialization consultancy).

## Triggers

Invoke this skill when Ben says any of:
- "LinkedIn profile" / "optimize LinkedIn" / "LinkedIn presence"
- "profile rewrite" / "LinkedIn audit"
- Asking to improve headline, About section, Featured, or Experience

## Inputs

- LinkedIn profile URL or handle (public profiles only)
- Pasted profile text (About, Headline, Experience)
- CV or resume (PDF/text)
- Portfolio or website links
- Which venture context: **Bennovative** or **CC**

## Outputs

- Rewritten Headline (one or more variants)
- Rewritten About section with SEO-tuned first two lines
- Featured section recommendations with specific links
- Experience bullets in Action-Result format
- Skills audit (remove filler, merge clusters, top 10 strategic)
- Content pillar recommendations (3 topics)
- Ready-to-paste copy blocks

## BenOS Integrations

- **cold-email skill** — Optimized LinkedIn headline and About summary serve as the credibility anchor for outreach sequences. After a profile rewrite, feed the new positioning statement directly into cold-email skill as the sender bio.
- **sales-enablement skill** — Profile authority signals (featured case studies, result metrics) feed CC's sales materials and proposal intros.
- **Craft** — Store profile draft variants (Bennovative vs CC) as Craft notes for version control and iteration. Link to active profile URLs so rewrites stay synced.

## Customization Notes

- **MEDIUM CUSTOMIZE** applied: generic tool references replaced with BenOS stack; venture-specific keyword lists and voice profiles added; concrete BenOS examples replace all original placeholder examples.
- Source skill: `linkedin-profile-optimizer` via Antigravity registry.
- Voice injection is **heavy** — all outputs must match Ben's established voice (stoic, direct, no hedging for Bennovative; professional authority with result-first framing for CC).

---

## BenOS Workflow

### Before You Optimize — Pick the Profile Variant

This is the first question to resolve before any rewrite:

> **Which profile?**
> - **Bennovative** — Ben's personal founder/builder brand. Target: investors, collaborators, community, press, potential hires.
> - **CC (Catalyzing Concepts)** — Consultancy identity. Target: SBIR/STTR awardees, federal program managers, university TTO offices, biomedical Phase II teams.

These require different keywords, voice, and CTAs. Never blend them. If Ben doesn't specify, ask.

### After You Optimize — Push to Downstream Skills

Once the profile is optimized:
1. Extract the new **headline + first 2 sentences of About** → feed to **cold-email skill** as sender credibility block.
2. Extract any **quantified results** (e.g., "200+ Phase II awardees") → add to **sales-enablement** battle card.
3. Save both profile variants in **Craft** under `LinkedIn / [venture name] / [date]`.

---

## Full Instructions

### Phase 0: Input Analysis

Analyze what Ben provides before proceeding:

- **LinkedIn URL/handle**: Confirm profile is publicly accessible. If private or inaccessible, ask Ben to paste the About section and current headline before proceeding. Do not guess or hallucinate profile content.
- **CV / resume**: Extract measurable achievements, role titles, tenure, and scope.
- **Portfolio link**: Identify projects, technical stacks, and proof points.
- **Multiple sources**: Cross-reference to find the "Red Thread" — the unifying throughline across roles.

### Phase 1: Context & Identity

Confirm which venture before writing a single word of copy. Then confirm:

1. Primary goal for this profile right now (raise awareness, generate inbound leads, attract co-founders, recruit hires)?
2. One specific target audience (e.g., SBIR Phase II awardees, Alabama angel investors, specialty coffee operators)?
3. Any hard constraints (e.g., keep current job title visible, don't mention a specific company yet)?

### Phase 2: Profile Audit ("Roast")

Evaluate the profile like a high-ticket client scanning it for 8 seconds. Flag:

- **Weak credibility**: No metrics, no proof, no social validation
- **Generic wording**: "Passionate," "hardworking," "expert" without evidence — cut all of it
- **Brand confusion**: Multiple unrelated roles with no unifying narrative
- **Conversion drain**: No clear CTA, no link in top card, no "here's what to do next"
- **Mobile readability**: Headline cut-off risk, dense About paragraphs
- **SEO gaps**: Missing target keywords in Headline and first 2 lines of About
- **Featured section failures**: Broken links, no thumbnails, zero proof items
- **Contact hygiene**: Old emails, dead website links, missing contact methods

### Phase 3: Profile Optimization

#### 1. Headline & About

**Headline formula — Bennovative:**
`[Role] | [What you build] | [Anchor identity]`

> **Example (Bennovative):**
> `Founder | Building SIPP + Who Is Coffee | Doing Hard Things in Alabama`

**Headline formula — CC:**
`SBIR/STTR Commercialization Expert | [Specific credential/credibility signal]`

> **Example (CC):**
> `SBIR/STTR Commercialization Expert | 200+ TABA Engagements | Phase II Market Strategy`

**About — Bennovative voice:**
- Stoic, candid, no hedging. Zero humble openers ("I've always been passionate about…" is banned).
- First line: declarative statement of identity. Example: `I build things that are hard to build in places that are hard to build them.`
- Second line: what you're working on right now with specific names. Example: `Currently: SIPP (water quality for pools and spas) + Who Is Coffee (specialty coffee, Alabama).`
- Third line: why it matters / what you believe. Example: `Stoic. Builder. Not interested in easy problems.`
- End with a specific CTA: link to Herk's Hits Substack or SIPP waitlist.

> **Full About Example (Bennovative):**
> ```
> I build things that are hard to build in places that are hard to build them.
>
> Currently: SIPP (real-time water quality monitoring for pools and spas) + Who Is Coffee (specialty coffee with an Alabama soul). Both started from scratch. Both in markets that punish mediocrity.
>
> Engineering background. UAB. Alabama. Stoic operating philosophy — I don't talk about what I'm going to do, I talk about what I'm doing.
>
> If you're building something hard, or you want to understand how specialty coffee and hardware startups work, I write about it at Herk's Hits (link below). SIPP waitlist is open.
> ```

**About — CC voice:**
- Professional authority, result-first framing.
- First sentence must contain scope signal: "200+ Phase II awardees" or equivalent.
- Lead with what clients get, not what CC is.
- No first-person narrative opener — open with results or a bold claim.

> **Full About Example (CC):**
> ```
> 200+ Phase II SBIR/STTR awardees have used Catalyzing Concepts to build commercialization plans that satisfy federal reviewers and actually work in the market.
>
> We specialize in TABA (Technical and Business Assistance) engagements for deep-tech, biomedical, and federal R&D teams — from initial Phase II strategy through technology transfer and licensing.
>
> Our work sits at the intersection of federal compliance and real commercial traction. Program managers trust our deliverables. Awardees use them.
>
> If you're a Phase II awardee or university TTO office looking for TABA support, start with the CC website (link below) or reach out directly.
> ```

#### 2. Featured Section

**Bennovative Featured:**
- Item 1: Link to **Herk's Hits Substack** — title: "Herk's Hits: Notes from a Builder in Alabama" — thumbnail: latest issue cover or a clean product photo
- Item 2: **SIPP waitlist page** — title: "SIPP — Real-Time Water Quality Monitoring" — thumbnail: SIPP product image or logo
- Item 3 (optional): A high-performing LinkedIn post demonstrating the builder/stoic voice

**CC Featured:**
- Item 1: **CC website** — title: "Catalyzing Concepts — SBIR/STTR Commercialization" — thumbnail: CC logo or site screenshot
- Item 2: **Phase II success case study** — title: "Case Study: From Phase II Award to Market Entry" — thumbnail: chart or result visual
- Item 3 (optional): A published TABA deliverable excerpt or testimonial post

> **Featured Rule:** Every item must have a working link, a descriptive title (not the raw URL), and a thumbnail. Broken links are an instant credibility drain — verify all links before recommending.

#### 3. Experience Section

Use the formula: `[Action Verb] + [Metric/Scope] + to achieve [Impact/Result]`

**Bennovative Experience Example (SIPP):**
> Before: `Founder at SIPP Technologies`
> After: `Founded and built SIPP from concept to waitlist — hardware-software water quality monitoring for pools and spas — as a solo founder in Birmingham, Alabama.`

**CC Experience Example:**
> Before: `Consultant at Catalyzing Concepts`
> After: `Led 200+ TABA commercialization engagements for SBIR/STTR Phase II awardees across biomedical, deep-tech, and federal R&D sectors — delivering market entry strategies that satisfy program manager requirements.`

**Experience rules:**
- No passive voice. Every bullet starts with an action verb.
- Metrics first when available. Scope (200+ engagements, X awardees, $Xk grant) before description.
- For roles without hard numbers: use scope language (national, federal, multi-phase, cross-sector).

#### 4. Skills & SEO

**Bennovative Target Keywords:**
- founder, entrepreneur, hardware startup, water quality, IoT, pool and spa, specialty coffee, UAB, Alabama, Bennovative, builder, stoic, small batch, Herk's Hits

**CC Target Keywords:**
- SBIR, STTR, TABA, commercialization, Phase II, Phase III, federal R&D, deep-tech, biomedical, technology transfer, licensing, market strategy, NSF, NIH, DoD, university spin-out

**Skills audit rules:**
- Remove: "Teamwork," "Microsoft Office," "Communication," "Leadership," "Problem Solving" — all filler
- Merge low-scope skills into clusters:
  - `Electrical Engineering + Embedded Systems + Firmware` → `Hardware Systems Engineering`
  - `Grant Writing + Federal Compliance + Program Management` → `Federal R&D Commercialization`
- Keep top 10–15 strategic skills aligned to the venture's mission

### Phase 4: Engagement & Content Strategy

**Bennovative Content Pillars (post weekly):**
1. Builder updates — what's shipping, what broke, what's next on SIPP or Who Is Coffee
2. Stoic founder philosophy — decision-making, tradeoffs, doing hard things in underdog markets
3. Alabama / regional builder community — why the South is underrated, local scenes worth watching

**CC Content Pillars (post weekly):**
1. SBIR/STTR commercialization tactics — what Phase II teams get wrong, how to satisfy reviewers
2. Deep-tech market entry — case studies, lessons from 200+ engagements
3. Federal R&D ecosystem — TABA trends, program changes, what program managers actually want

**Engagement voice options:**
- **Professional (CC):** Insightful, result-oriented, cites data or scope
- **Direct/Candid (Bennovative):** Short, no hedging, sounds like Ben actually wrote it
- **Reflective (either):** Calm, principle-based, stoic framing — "The work is the answer."

---

## Best Practices

- Quantify everything possible. Numbers are credibility. Estimates are fine if labeled as such.
- One "Red Thread" per profile. Do not blend venture identities on the same profile.
- Every profile needs one clear CTA. Visitor should know exactly what to do next.
- No buzzwords without proof. "Expert" means nothing. "200+ Phase II awardees" means everything.
- Check all links. Broken Featured section links are worse than no Featured section.

## Common Pitfalls

- **Brand overlap**: Mixing SIPP + CC + Who Is Coffee into one profile without a clear anchor. Fix: pick one identity per profile and position others as supporting context only.
- **Generic About opener**: Starting with "I am passionate about…" or "With X years of experience…" — cut immediately.
- **Skill dumping**: Listing 40+ skills signals unfocused, not versatile. Curate to 10–15 max.
- **No CTA**: Profile ends with experience history and nothing tells the visitor what to do. Every About section ends with a link and an action.

## Limitations

- Cannot access private LinkedIn profiles or live LinkedIn data. Works from pasted text, public URLs, or uploaded PDFs.
- Cannot send messages or post content on Ben's behalf.
- Cannot generate banner/profile images (use Runway or a designer for visuals).
- Does not replace Ben's own voice review — always read the output aloud before publishing.
