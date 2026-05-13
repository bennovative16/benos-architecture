# Email Sequence

## BenOS Metadata

| Field | Value |
|-------|-------|
| Source | Antigravity |
| BenOS Fit | 5/5 |
| Ventures | WIC, SIPP, Bennovative |
| API Status | Green |
| Voice Injection | Heavy |
| Group | MARKETING |

## Purpose
Welcome, nurture, re-engagement, and post-purchase email frameworks for all three active BenOS ventures. Wired to Klaviyo MCP for WIC and SIPP execution; Substack for Bennovative newsletter flows.

## Triggers
Invoke this skill when:
- Designing an email sequence, flow, or automation
- Building a welcome series, nurture sequence, or re-engagement campaign
- Setting up Klaviyo flows for WIC or SIPP
- Planning a Bennovative Substack series
- Phrases: "email sequence", "email flow", "welcome series", "nurture sequence", "Klaviyo flow", "email automation", "post-purchase email", "win-back email"

## Inputs
- Venture name (WIC, SIPP, or Bennovative)
- Sequence type (welcome, nurture, post-purchase, re-engagement, winback)
- Trigger event (signup, purchase, abandonment, inactivity)
- `.agents/product-marketing-context-[venture].md` (run product-marketing-context first if missing)

## Outputs
- Complete email sequence with subject lines, preview text, and body copy per email
- Klaviyo flow setup steps (WIC/SIPP) or Substack series structure (Bennovative)
- Timing/delay map between emails
- Segment conditions and exit criteria

## BenOS Integrations
- **Klaviyo MCP**: Primary execution for WIC and SIPP flows — use `klaviyo_get_flows`, `klaviyo_create_email_template`, `klaviyo_get_lists`, `klaviyo_get_segments`
- **Shopify MCP**: WIC post-purchase triggers, subscription billing events
- **product-marketing-context**: Read `.agents/product-marketing-context-[venture].md` before generating any copy — customer language and positioning should come from this file
- **Pairs with**: onboarding-cro (email supports in-app/unboxing), churn-prevention (dunning and win-back flows), popup-cro (email capture that feeds these sequences), lead-magnets (what triggers the nurture)

## Customization Notes
Full rewrite of source instructions with 4-venture awareness. All templates have venture-specific variants. Voice profiles embedded explicitly in BenOS Voice Profiles section. Two execution paths defined: Klaviyo MCP (WIC/SIPP) and Substack (Bennovative). Source sequence types preserved; all copy examples replaced with venture-specific copy.

---

# Full Instructions

## BenOS Workflow

**Before this skill:** Run `product-marketing-context` for the venture. Load `.agents/product-marketing-context-[venture].md` for customer language, positioning, and voice.

**Execution paths:**
- WIC and SIPP → Klaviyo MCP (automated flows, triggered by Shopify events or signup forms)
- Bennovative → Substack (newsletter series, scheduled sends)

**After this skill:** Wire Klaviyo flows using the Klaviyo MCP tools. For Bennovative, draft in Substack editor.

**Klaviyo MCP quick reference:**
- List available flows: `klaviyo_get_flows`
- Check lists: `klaviyo_get_lists`
- Check segments: `klaviyo_get_segments`
- Create template: `klaviyo_create_email_template`
- Review performance: `klaviyo_get_flow_report`

---

## BenOS Voice Profiles

Identify the venture before writing any copy. Apply the matching profile to every email in the sequence.

### CC (Catalyzing Concepts)
*Not in this skill's venture scope — use cold-email skill for CC outreach.*

### WIC (Who Is Coffee)
Playful, sensory, direct. Coffee-forward. Farmer stories. Conservation angle. Short sentences. Ritual and relationship are the emotional cores.

**Use:** Sensory language — smell, taste, ritual, warmth. Farmer names and origin country. "Your morning" not "our product". Active verbs. Sentence fragments are fine.

**Avoid:** Corporate language. Long paragraphs. Generic coffee clichés ("wake up and smell the coffee"). Discount-first framing.

**Example sentence:** "This one smells like brown sugar before you even grind it."

### SIPP
Technical, aspirational. IoT + smart home. Water quality + environmental stewardship. Trust through data. Aspirational about what "knowing your water" enables.

**Use:** Data-backed statements. "Your water story." Smart home category framing. Lead/PFAS/contaminant specifics where relevant. "Home" and "family" as emotional anchors.

**Avoid:** Fearmongering without solutions. Overly technical without warmth. Generic smart home buzzwords without substance.

**Example sentence:** "Your first SIPP reading took 4 minutes. That data is now yours — forever."

### Bennovative
Stoic. Candid. Builder. No hedging. No performative humility. No motivational filler ("You've got this!", "Believe in yourself!"). No corporate email opener ("I hope this email finds you well").

**Voice synthesis:** Mark Manson (cuts through noise, direct) × Jocko Willink (ownership, declarative, no excuses) × Ryan Holiday (stoic lens, historically anchored, long view).

**Use:** Declarative statements. First-person ownership. Observations about the hard thing. Short, punchy paragraphs. Historical or philosophical reference if it lands naturally.

**Avoid:** Hedging language. Humble bragging. Empty encouragement. Any opener that sounds like a newsletter template.

**Example sentence:** "Most people quit here. That's not a tragedy — it's information."

---

## Initial Assessment

Before writing, confirm:

1. **Venture** — WIC, SIPP, or Bennovative?
2. **Sequence type** — welcome, nurture, post-purchase, re-engagement, winback?
3. **Trigger event** — what puts someone into this sequence?
4. **Execution platform** — Klaviyo (WIC/SIPP) or Substack (Bennovative)?
5. **Context file** — is `.agents/product-marketing-context-[venture].md` available?

---

## Core Principles

### 1. One Email, One Job
Each email has one primary purpose. One main CTA. Do not combine a product education email with a discount offer.

### 2. Value Before Ask
Lead with usefulness. Build trust. Earn the right to sell.

### 3. Relevance Over Volume
Fewer, better emails win. For WIC: 5-7 emails beats 12 mediocre ones. For SIPP pre-launch: 3-4 emails max until product ships.

### 4. Voice Consistency
Every email in a sequence must sound like it was written by the same person. Read the sequence out loud end-to-end before finalizing.

---

## Sequence Length & Timing

| Sequence type | Length | Timing |
|---------------|--------|--------|
| Welcome | 3–5 emails | Every 1–2 days |
| Lead nurture | 5–8 emails | Every 2–3 days |
| Post-purchase | 3–5 emails | Day 0, 2, 5, 10, 21 |
| Re-engagement | 3–4 emails | Day 0, 3, 7, 14 |
| Win-back | 3 emails | Day 30, 60, 90 |

---

## Welcome Sequence Templates

### WIC Welcome Sequence (Post-Signup or First Purchase)

**Email 1: Welcome — Immediate**
Subject: `Your coffee is already on its way.`
Preview: `Here's what makes it different.`

Body: Lead with the origin of the specific coffee they're getting (or the current featured roast). Name the farm or region. One sensory detail. Single CTA: "Track your order" or "Meet your coffee."

**Email 2: The Farm — Day 2**
Subject: `Meet the people who grew it`
Preview: `3,200 feet above sea level in [Country].`

Body: Farmer story. Two sentences on the growing conditions. One sentence on why this particular lot ended up in your bag. Photo if possible. No CTA needed — this is pure relationship-building.

**Email 3: How to Brew It — Day 4**
Subject: `Don't mess this one up`
Preview: `(Kidding. Mostly.)`

Body: Short brew guide specific to the roast level and processing method of their coffee. Playful tone. One specific tip that most people skip. CTA: "Watch the brew video" or link to recipe.

**Email 4: The Why — Day 7**
Subject: `Why we only sell coffee we'd drink ourselves`
Preview: `It's a short list for a reason.`

Body: WIC origin story — brief. The quality standard. The conservation angle (if applicable to current offering). Why that matters. CTA: "See our current lineup."

**Email 5: Come Back — Day 14 (for non-repurchasers)**
Subject: `Running low yet?`
Preview: `Most bags last about 2 weeks.`

Body: Light reorder nudge. Sensory language about the next bag. New arrival if available. CTA: "Reorder or try something new."

---

### SIPP Welcome Sequence (Waitlist Signup)

**Email 1: Welcome — Immediate**
Subject: `You're on the list. Here's what that means.`
Preview: `We'll tell you when your number comes up.`

Body: Confirm signup. Explain what the waitlist is for — early access, not just notification. One data point that frames the problem (e.g., EPA PFAS findings, lead pipe stats). No oversell. CTA: "Follow our progress" (link to X or Substack if applicable).

**Email 2: The Problem — Day 3**
Subject: `Most people have no idea what's in their water`
Preview: `Including people who filter it.`

Body: Two specific water quality facts. The gap between "filtered" and "tested." Why a filter isn't the same as a monitor. How SIPP closes that gap. CTA: "See how SIPP works."

**Email 3: How It Works — Day 7**
Subject: `4 minutes. One reading. Permanent record.`
Preview: `That's the whole setup.`

Body: Hardware explanation, simple. The app's role. What the data looks like. The "water story" concept — your home's water history over time. CTA: "See the dashboard preview."

**Email 4: The Wait — Day 14**
Subject: `Still building. Still worth it.`
Preview: `Here's where we are.`

Body: Honest progress update. One thing you've solved. One thing still being refined. Reinforce why the waitlist exists (quality, not hype). CTA: "Refer a friend to move up the list" (if referral mechanic is active).

---

### Bennovative Welcome Sequence (Herk's Hits Newsletter)

**Email 1: Welcome — Immediate**
Subject: `Here's what you signed up for`
Preview: `And what you didn't.`

Body: Declarative description of what Herk's Hits is. What it isn't (not a motivational newsletter, not a listicle dump). What to expect in terms of cadence and content. One sentence on who Ben is — anchor to "doing hard things." No fluff. CTA: none needed, or "reply and tell me why you signed up."

**Email 2: The Frame — Day 3**
Subject: `The thing most people get wrong about hard work`
Preview: `It's not about effort.`

Body: First real content. A short stoic-framed observation or essay. 200-350 words. No CTA — this is trust-building through substance.

**Email 3: The Invitation — Day 7**
Subject: `One question worth asking yourself this week`
Preview: `No right answer. Just a useful one.`

Body: A single Socratic or stoic prompt. Two sentences of framing. Then the question. That's it. Optional: "Hit reply if you want to think through it." This is the email that separates the engaged from the passive.

---

## Post-Purchase Sequences

### WIC Post-Purchase (Non-Subscription)

**Email 1: Order Confirmation + Anticipation — Day 0**
Subject: `Order confirmed. The wait begins.`
Preview: `Here's what's coming your way.`

Body: Confirm order. Name the specific coffee. One sensory detail. Expected ship date. This email should feel like getting a text from a friend who's excited about what they're sending you.

**Email 2: Shipped — When Tracking Updates**
Subject: `It's on its way. Here's how to prepare.`
Preview: `Get your grinder ready.`

Body: Shipping confirmation. Brew gear recommendations for this specific roast. One-minute prep: rinse your equipment, use filtered water, don't grind until you're ready. CTA: tracking link.

**Email 3: Brew Day — Day of Delivery**
Subject: `It arrived. Don't rush the first cup.`
Preview: `This one deserves 10 minutes.`

Body: Short brew ritual prompt. The first cup should be black, no matter how they usually drink it — just to taste it. One sensory cue to notice. No CTA — this is pure experience.

**Email 4: How Was It? — Day 5**
Subject: `How was the first cup?`
Preview: `Seriously asking.`

Body: Short. Genuine question. Invite a reply. Light nudge to leave a review if they loved it. CTA: "Leave a review" + "Try our next roast."

**Email 5: Reorder Nudge — Day 12–14**
Subject: `Almost out?`
Preview: `Most bags last about two weeks.`

Body: Soft reorder prompt. Mention current new arrivals or seasonal offering. CTA: "Reorder" or "Try something different."

---

### SIPP Post-Purchase (Hardware + App — Post-Launch)

**Email 1: Order Confirmed — Immediate**
Subject: `SIPP is on its way.`
Preview: `Your water story starts soon.`

Body: Order confirmation. Estimated delivery. What's in the box. Link to the app download (so they can download before hardware arrives).

**Email 2: Setup Guide — Day of Delivery**
Subject: `Box arrived? Here's your first 4 minutes.`
Preview: `Step 1 takes about 30 seconds.`

Body: Link to setup guide or in-app tutorial. Emphasize: the first reading is the most important one — it establishes your baseline. CTA: "Start setup" → deep link to app.

**Email 3: First Reading — Day 2 (if not yet taken)**
Subject: `Haven't taken your first reading yet?`
Preview: `Your water is waiting.`

Body: Gentle nudge. One-line reminder of why the first reading matters. Link back to app. Offer support if stuck. CTA: "Open SIPP."

**Email 4: What Your Data Means — Day 5**
Subject: `Here's how to read your water score`
Preview: `And what to do if it's not great.`

Body: Brief explanation of the score scale. What "normal" looks like. What elevated readings mean and what to do. Reassurance that the data is informational, not alarming by itself. CTA: "View your full report."

**Email 5: One Month In — Day 30**
Subject: `30 days of water data. Here's what we see.`
Preview: `Your home has a pattern.`

Body: Summary of what 30 days of readings reveals. The value of the trend line, not just the single reading. Nudge to check the app. CTA: "See your 30-day history."

---

## Re-Engagement Sequences

### WIC Re-Engagement (60+ Days No Purchase)

**Email 1 — Day 60**
Subject: `It's been a while.`
Preview: `We've had some great coffees since you left.`

Body: Acknowledge the gap without guilt. 2-3 new arrivals since their last order. Sensory description of the current featured coffee. CTA: "See what's new."

**Email 2 — Day 67**
Subject: `Anything we got wrong?`
Preview: `Genuinely asking.`

Body: 3-4 sentences. Ask if the coffee, experience, or something else fell short. Invite a reply. No hard sell. This is listening, not selling.

**Email 3 — Day 74**
Subject: `Last one from us for a while.`
Preview: `Unless you want to hear more.`

Body: Honest. "We don't want to bother you." One final offer if appropriate (free shipping or a small discount). CTA to stay subscribed or to unsubscribe gracefully. Clean the list if no response.

---

### SIPP Re-Engagement (Waitlist — 90+ Days No Open)

**Email 1 — Day 90**
Subject: `Still there?`
Preview: `We're still building. Just checking.`

Body: Short. Progress update. One milestone hit since they signed up. Confirm they still want early access. CTA: "Yes, keep me on the list" (preference center link).

**Email 2 — Day 97**
Subject: `We'll take you off the list if we don't hear from you.`
Preview: `No hard feelings.`

Body: Two sentences. List hygiene honesty. CTA to stay or gracefully exit. Unsubscribe if no action.

---

### Bennovative Re-Engagement (Newsletter Inactive 60+ Days)

**Email 1 — Day 60**
Subject: `You haven't opened in a while. Honest question:`
Preview: `Is this still useful to you?`

Body: 3-4 sentences. Observation, not guilt. Ask if the content is still relevant to where they are. Option to change frequency or topic focus. CTA: "Reply or click here to stay" vs. natural unsubscribe.

---

## Email Copy Guidelines

### Structure
1. **Hook** — first line earns the read
2. **Context** — why this matters right now
3. **Value** — the substance
4. **CTA** — one thing, clearly stated
5. **Sign-off** — human, brief

### Length by email type
- WIC: 80–200 words. Short paragraphs. White space. Sensory images over explanations.
- SIPP: 100–250 words. Data + warmth. No bullet lists in emotional emails.
- Bennovative: 150–400 words. Essay-like. Dense but not padded.

### Subject line patterns that work
- **Direct:** `Your order shipped.`
- **Curiosity:** `The one thing most people skip on their first cup`
- **Story tease:** `The mistake we made with our first roast`
- **Question:** `Still struggling with bitter coffee?`
- **Number:** `3 things your water test won't tell you`

### CTA rules
- One primary CTA per email
- Button text = action + outcome: `"Read the brew guide"` not `"Click here"`
- If in doubt, make it shorter

---

## Klaviyo Execution Steps (WIC + SIPP)

After designing the sequence, use Klaviyo MCP to build it:

1. **Check existing flows**: `klaviyo_get_flows` — confirm no conflicting active flow for this trigger
2. **Identify the list or segment**: `klaviyo_get_lists` / `klaviyo_get_segments`
3. **Create email templates**: `klaviyo_create_email_template` for each email in the sequence
4. **Review flow performance** (existing flows): `klaviyo_get_flow_report`

For WIC flows triggered by Shopify events (purchase, subscription skip, cancellation): confirm the Shopify → Klaviyo integration is active before building.

---

## Testing & Metrics

| Metric | Benchmark |
|--------|-----------|
| Open rate | 30–45% (WIC/SIPP early audience), 35–50% (Bennovative permission-based) |
| Click rate | 3–8% |
| Unsubscribe rate | Keep under 0.5% per send |
| Sequence completion | Track % reaching email 5+ |

Test one variable at a time. Subject lines have the highest leverage. Run A/B for at least 500 recipients per variant.

---

## Related BenOS Skills

- **onboarding-cro**: Email supports the in-app or unboxing onboarding — don't duplicate, coordinate
- **churn-prevention**: Dunning and win-back sequences live there
- **popup-cro**: What feeds people into these sequences
- **lead-magnets**: What triggers the nurture sequence
- **product-marketing-context**: Source of truth for customer language and positioning
