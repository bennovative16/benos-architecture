# Churn Prevention

| Field | Value |
|---|---|
| **Skill** | churn-prevention |
| **Source** | Antigravity |
| **BenOS Fit** | 4/5 |
| **Ventures** | WIC, SIPP |
| **API Status** | Green |
| **Voice Injection** | Light |
| **Group** | MARKETING |
| **Triggers** | "churn", "cancel flow", "dunning", "retention", "subscription lapse", "win-back" |
| **Version** | 1.1.0 (BenOS customized) |

## Purpose

Reduce voluntary and involuntary churn with cancel flows, save offers, dunning sequences, win-back campaigns, and proactive retention strategy. Covers WIC coffee subscriptions on Shopify and SIPP app subscriptions post-launch.

## Triggers

Use this skill when:
- Customers are cancelling or at risk of cancelling a subscription
- Failed payments are rising and dunning needs to be set up or improved
- You want to design or optimize a cancel flow with save offers
- Subscription retention metrics need attention
- A win-back campaign is needed for lapsed subscribers
- The word "churn," "cancel flow," "dunning," "retention," "subscription lapse," or "win-back" comes up

## Inputs

- Venture context (WIC or SIPP)
- Current churn rate (voluntary vs. involuntary if known)
- Active subscriber count and MRR per customer
- Whether a cancel flow exists today
- Shopify Subscriptions data for WIC (billing intervals, pause/downgrade support)
- Cancel reason data from past churns (if available)
- Desired brand tone for offboarding (empathetic, direct, sensory for WIC)

## Outputs

- Cancel flow design (survey → dynamic offer → confirmation → post-cancel)
- Dynamic save offer strategy matched to cancel reason
- Dunning email sequence (timing, tone, content per email)
- Win-back campaign brief (hook, copy angle, offer)
- Klaviyo flow specs ready to build via Klaviyo MCP
- Proactive churn signal triggers and health score framework
- Metrics dashboard spec (save rate, recovery rate, reactivation rate)

## BenOS Integrations

- **Klaviyo MCP** — Build and trigger dunning sequences and win-back flows directly; use `klaviyo_create_email_template`, `klaviyo_get_flows`, and related tools
- **Shopify MCP** — Pull WIC subscription billing data, subscription status, pause/cancel history; use `get-order`, `graphql_query` for subscription details
- **Pairs with `onboarding-cro`** — Preventing churn starts at activation; run onboarding-cro first when early churn (sub-60-day) is the problem

## Customization Notes

- All email platform references resolve to **Klaviyo MCP** (not generic "your email platform")
- All subscription billing references resolve to **Shopify Subscriptions** for WIC; SIPP billing TBD post-launch
- WIC and SIPP have distinct cancel flow logic, copy angles, and dunning strategies — see venture callout blocks in the Instructions section
- Save offer depth: avoid 50%+ discounts; WIC primary save path is pause, not discount
- SIPP cancel flow leads with data loss framing ("your water quality readings"), not price

---

# Churn Prevention — Full Instructions

You are an expert in subscription retention and churn prevention. Your goal is to help reduce both voluntary churn (customers choosing to cancel) and involuntary churn (failed payments) through well-designed cancel flows, dynamic save offers, proactive retention, and dunning strategies.

## BenOS Workflow

**Before:** Run `onboarding-cro` first if churn is concentrated in the first 60 days — early churn is almost always an activation failure, not a retention failure. Fix the activation gap before building a cancel flow.

**After:** Wire Klaviyo flows via Klaviyo MCP once the email sequence is designed. Use `klaviyo_create_email_template` and `klaviyo_get_flows` to build out dunning and win-back sequences.

**Inputs by venture:**
- **WIC:** Shopify Subscriptions data (billing intervals, skip history, pause status, last order date). Use Shopify MCP `graphql_query` to pull subscription records.
- **SIPP (post-launch):** App subscription data from SIPP billing infrastructure (TBD). Hardware + app bundle — treat hardware issues as a primary churn signal.

## When to Use
- Use when churn is rising or cancellation behavior needs intervention.
- Use when designing cancel flows, save offers, dunning, or retention programs.
- Use when the user wants to reduce either voluntary or involuntary churn.

## Before Starting

**Check for product marketing context first:**
If `.agents/product-marketing-context.md` exists (or `.claude/product-marketing-context.md` in older setups), read it before asking questions. Use that context and only ask for information not already covered or specific to this task.

Gather this context (ask if not provided):

### 1. Current Churn Situation
- What's the monthly churn rate? (Voluntary vs. involuntary if known)
- How many active subscribers?
- What's the average MRR per customer?
- Is there a cancel flow today, or does cancel happen instantly?

### 2. Billing & Platform
- **For WIC:** Shopify Subscriptions (confirmed). Pull data via Shopify MCP.
- Monthly, annual, or both billing intervals?
- Does WIC support plan pausing or frequency downgrades? (Yes — pause is the primary save path)
- Any existing retention tooling?

### 3. Product & Usage Data
- Can we identify engagement drop-offs? (WIC: skipped deliveries, low email open rate on brew content)
- Is there cancellation reason data from past churns?
- What's the activation metric for each venture? (WIC: first bag consumed + second order placed; SIPP: first water quality reading reviewed in app)

### 4. Constraints
- B2C for both WIC and SIPP
- Self-serve cancellation required on Shopify
- Brand tone: WIC = sensory, warm, craft-forward; SIPP = data-driven, health-conscious, calm

---

## How This Skill Works

Churn has two types requiring different strategies:

| Type | Cause | Solution |
|------|-------|----------|
| **Voluntary** | Customer chooses to cancel | Cancel flows, save offers, exit surveys |
| **Involuntary** | Payment fails | Dunning emails, smart retries, card updaters |

Voluntary churn is typically 50-70% of total churn. Involuntary churn is 30-50% but is often easier to fix.

This skill supports three modes:

1. **Build a cancel flow** — Design from scratch with survey, save offers, and confirmation
2. **Optimize an existing flow** — Analyze cancel data and improve save rates
3. **Set up dunning** — Failed payment recovery with retries and email sequences

---

## Cancel Flow Design

### The Cancel Flow Structure

Every cancel flow follows this sequence:

```
Trigger → Survey → Dynamic Offer → Confirmation → Post-Cancel
```

**Step 1: Trigger**
Customer clicks "Cancel subscription" in account settings.

**Step 2: Exit Survey**
Ask why they're cancelling. This determines which save offer to show.

**Step 3: Dynamic Save Offer**
Present a targeted offer based on their reason (pause, downgrade, discount, etc.)

**Step 4: Confirmation**
If they still want to cancel, confirm clearly with end-of-billing-period messaging.

**Step 5: Post-Cancel**
Set expectations, offer easy reactivation path, trigger win-back sequence.

### Exit Survey Design

The exit survey is the foundation. Good reason categories:

| Reason | What It Tells You |
|--------|-------------------|
| Too expensive | Price sensitivity, may respond to discount or downgrade |
| Not using it enough | Low engagement, may respond to pause or onboarding help |
| Missing a feature | Product gap, show roadmap or workaround |
| Switching to competitor | Competitive pressure, understand what they offer |
| Technical issues / bugs | Product quality, escalate to support |
| Temporary / seasonal need | Usage pattern, offer pause |
| Business closed / changed | Unavoidable, learn and let go gracefully |
| Other | Catch-all, include free text field |

**Survey best practices:**
- 1 question, single-select with optional free text
- 5-8 reason options max (avoid decision fatigue)
- Put most common reasons first (review data quarterly)
- Don't make it feel like a guilt trip
- "Help us improve" framing works better than "Why are you leaving?"

### Dynamic Save Offers

The key insight: **match the offer to the reason.** A discount won't save someone who isn't using the product. A feature roadmap won't save someone who can't afford it.

**Offer-to-reason mapping:**

| Cancel Reason | Primary Offer | Fallback Offer |
|---------------|---------------|----------------|
| Too expensive | Discount (20-30% for 2-3 months) | Downgrade to lower plan |
| Not using it enough | Pause (1-3 months) | Free onboarding session |
| Missing feature | Roadmap preview + timeline | Workaround guide |
| Switching to competitor | Competitive comparison + discount | Feedback session |
| Technical issues | Escalate to support immediately | Credit + priority fix |
| Temporary / seasonal | Pause subscription | Downgrade temporarily |
| Business closed | Skip offer (respect the situation) | — |

### Save Offer Types

**Pause subscription (WIC primary save path)**
- 1-3 month pause maximum (longer pauses rarely reactivate)
- 60-80% of pausers eventually return to active
- Auto-reactivation with advance notice email
- Keep their order history and preferences intact
- For WIC: frame as "take a break, your subscription will be here when you're ready"

**Discount**
- 20-30% off for 2-3 months is the sweet spot
- Avoid 50%+ discounts (trains customers to cancel for deals)
- Time-limit the offer ("This offer expires when you leave this page")
- Show the dollar amount saved, not just the percentage

**Frequency downgrade**
- Offer less frequent delivery (every 6 weeks instead of every 4)
- Position as "right-size your subscription" not "downgrade"
- Easy path back up when ready

**Personal outreach**
- For high-value accounts
- Route to customer success or founder for a call

### Cancel Flow UI Patterns

```
┌─────────────────────────────────────┐
│  We're sorry to see you go          │
│                                     │
│  What's the main reason you're      │
│  cancelling?                        │
│                                     │
│  ○ Too expensive                    │
│  ○ Not using it enough              │
│  ○ Missing a feature I need         │
│  ○ Switching to another coffee      │
│  ○ Technical issues                 │
│  ○ Temporary / don't need right now │
│  ○ Other: [____________]            │
│                                     │
│  [Continue]                         │
│  [Never mind, keep my subscription] │
└─────────────────────────────────────┘
         ↓ (selects "Not using it enough")
┌─────────────────────────────────────┐
│  Take a break instead?              │
│                                     │
│  Life gets busy. Pause your         │
│  subscription for up to 3 months    │
│  and pick back up whenever you're   │
│  ready.                             │
│                                     │
│  ┌───────────────────────────────┐  │
│  │  Pause for 1 month            │  │
│  │  Pause for 2 months           │  │
│  │  Pause for 3 months           │  │
│  │                               │  │
│  │  [Pause My Subscription]      │  │
│  └───────────────────────────────┘  │
│                                     │
│  [No thanks, continue cancelling]   │
└─────────────────────────────────────┘
```

**UI principles:**
- Keep the "continue cancelling" option visible (no dark patterns)
- One primary offer + one fallback, not a wall of options
- Show specific dollar savings, not abstract percentages
- Use the customer's name and order history when possible
- Mobile-friendly (many cancellations happen on mobile)

---

> **For WIC (Coffee Subscription):**
> WIC is on Shopify Subscriptions. Key churn signals: skipped delivery, 2+ bag pause, no reorder after 60 days, low email open rate on brew content.
> Cancel flow goal: offer a pause (not cancel) as the primary path. Secondary: downgrade delivery frequency.
> Dunning: Klaviyo failed payment sequence — 3 emails over 7 days (day 1: heads up, day 3: retry warning, day 7: final notice + save offer).
> Win-back: "Your coffee misses you" campaign at 45-day lapse. Sensory copy. Include a new single-origin teaser. Offer: free shipping on return order.

> **For SIPP (Post-Launch App Subscription):**
> SIPP subscription will be hardware + app bundle. Key churn risk: hardware stops working / user loses habit of checking app.
> Cancel flow: surface the water quality data they'd lose visibility into ("Your last 6 months of water readings"). Pair with a hardware support offer.
> Dunning: similar 3-email Klaviyo sequence. Lead with data loss framing, not discount.

---

## Churn Prediction & Proactive Retention

The best save happens before the customer ever clicks "Cancel."

### Risk Signals

Track these leading indicators of churn:

| Signal | Risk Level | Timeframe |
|--------|-----------|-----------|
| Skipped 1 delivery (WIC) | Medium | 2-4 weeks before cancel |
| Skipped 2+ deliveries (WIC) | High | 1-2 weeks before cancel |
| App opens drop 50%+ (SIPP) | High | 2-4 weeks before cancel |
| No water quality review in 30 days (SIPP) | High | 1-3 weeks before cancel |
| Email open rates decline | Medium | 2-6 weeks before cancel |
| Billing page visits increase | High | Days before cancel |
| NPS score drops below 6 | Medium | 1-3 months before cancel |

### Health Score Model

Build a simple health score (0-100) from weighted signals:

```
Health Score = (
  Order/usage frequency score  × 0.30 +
  Feature/content engagement   × 0.25 +
  Support sentiment            × 0.15 +
  Billing health               × 0.15 +
  Email engagement score       × 0.15
)
```

| Score | Status | Action |
|-------|--------|--------|
| 80-100 | Healthy | Upsell opportunities |
| 60-79 | Needs attention | Proactive check-in |
| 40-59 | At risk | Intervention campaign |
| 0-39 | Critical | Personal outreach |

### Proactive Interventions

| Trigger | Intervention |
|---------|-------------|
| WIC: first delivery skipped | "Did your last bag last longer? We can adjust your frequency." email |
| WIC: no reorder after 60 days | Win-back sequence starts |
| SIPP: no app open in 14 days | Re-engagement push notification + email |
| SIPP: hardware issue reported | Immediate support escalation |
| Any: NPS detractor (0-6) | Personal follow-up within 24 hours |
| Any: annual renewal in 30 days | Value recap email + renewal confirmation |

---

## Involuntary Churn: Payment Recovery

Failed payments cause 30-50% of all churn but are the most recoverable.

### The Dunning Stack

```
Pre-dunning → Smart retry → Dunning emails → Grace period → Hard cancel
```

### Pre-Dunning (Prevent Failures)

- **Card expiry alerts**: Email 30, 15, and 7 days before card expires (via Klaviyo MCP)
- **Pre-billing notification**: Email 3-5 days before charge for annual plans
- **Backup payment method**: Prompt for a second payment method at checkout

### Smart Retry Logic

| Decline Type | Examples | Retry Strategy |
|-------------|----------|----------------|
| Soft decline (temporary) | Insufficient funds, processor timeout | Retry 3-5 times over 7-10 days |
| Hard decline (permanent) | Card stolen, account closed | Don't retry — ask for new card |
| Authentication required | 3D Secure, SCA | Send customer to update payment |

**Retry timing:**
- Retry 1: 24 hours after failure
- Retry 2: 3 days after failure
- Retry 3: 5 days after failure
- After 3 retries: Hard cancel with reactivation path

### Dunning Email Sequence (WIC via Klaviyo)

| Email | Timing | Tone | Content |
|-------|--------|------|---------|
| 1 | Day 1 (failure) | Friendly heads-up | "Heads up — your WIC payment didn't go through. Update your card to keep your coffee coming." |
| 2 | Day 3 | Helpful reminder | "Your next bag is waiting — just update your payment method to keep your subscription active." |
| 3 | Day 7 | Urgency + save offer | "Last chance to keep your subscription. Update your card — or pause instead if now isn't the right time." |

**Dunning email best practices:**
- Direct link to payment update page (no extra login required)
- Show what they'll lose (next delivery, their preferred roast, their frequency settings)
- Don't blame ("your payment didn't go through" not "you failed to pay")
- Include support contact for help
- Plain text or minimal design performs better than heavily designed dunning emails

### Klaviyo MCP Steps: Building the Dunning Flow

1. Use `klaviyo_get_flows` to check if a failed payment flow already exists for WIC
2. Use `klaviyo_create_email_template` to create each of the 3 email templates with the copy above
3. Configure the flow trigger as "Shopify subscription payment failed" event
4. Set delays: 0 days (immediate), 3 days, 7 days
5. Use `klaviyo_get_flow_report` after 30 days to measure recovery rate

### Dunning Email Sequence (SIPP via Klaviyo — Post-Launch)

| Email | Timing | Tone | Content |
|-------|--------|------|---------|
| 1 | Day 1 | Friendly alert | "Your SIPP subscription payment didn't process. Update your card to keep monitoring your water." |
| 2 | Day 3 | Data framing | "Your water quality monitoring is on hold. A quick card update keeps your readings uninterrupted." |
| 3 | Day 7 | Data loss urgency | "Your last 6 months of water quality data will become inaccessible if your subscription lapses. Update your card or contact us for help." |

---

## Win-Back Campaigns

### WIC Win-Back: "Your coffee misses you"

**Trigger:** 45 days since last active subscription or order
**Channel:** Klaviyo email sequence (2-3 emails)
**Copy angle:** Sensory + curiosity — lead with a new single-origin teaser, not a discount
**Offer:** Free shipping on return order (not a deep discount — protect margin)
**Email 1 subject:** "Something new just landed (and we thought of you)"
**Email 2 subject (7 days later):** "Your old frequency is still saved — just say the word"
**Email 3 subject (14 days later):** "Last call: free shipping if you come back this week"

**Klaviyo MCP steps:**
1. Use `klaviyo_get_segments` to find lapsed WIC subscribers (last order 45+ days ago, subscription cancelled or paused)
2. Use `klaviyo_create_email_template` for each win-back email
3. Build a Klaviyo flow triggered by segment entry
4. Use `klaviyo_get_campaign_report` to track open rate and reactivation rate

### SIPP Win-Back (Post-Launch)

**Trigger:** 30 days since subscription lapse
**Copy angle:** Lead with the data gap — "You've missed 30 days of water quality readings"
**Offer:** Hardware diagnostic check + 1 month free app access
**Goal:** Get user back to hardware + app habit before the data gap becomes a reason to never return

---

## Metrics & Measurement

### Key Churn Metrics

| Metric | Formula | Target |
|--------|---------|--------|
| Monthly churn rate | Churned customers / Start-of-month customers | <5% B2C |
| Cancel flow save rate | Saved / Total cancel sessions | 25-35% |
| Offer acceptance rate | Accepted offers / Shown offers | 15-25% |
| Pause reactivation rate | Reactivated / Total paused | 60-80% |
| Dunning recovery rate | Recovered / Total failed payments | 50-60% |
| Win-back reactivation rate | Reactivated / Total win-back recipients | 5-15% |

### Cancel Flow A/B Tests

Test one variable at a time:

| Test | Hypothesis | Metric |
|------|-----------|--------|
| Pause vs. discount as primary offer | Pause saves more for "not using it" reason | Save rate |
| Pause duration (1 vs 3 months) | Longer pause increases return rate | Reactivation rate |
| Survey placement (before vs after offer) | Survey-first personalizes offers better | Save rate |
| Copy tone (empathetic vs sensory for WIC) | Sensory copy reduces friction | Save rate |

Use the **ab-test-setup** skill to design statistically rigorous tests.

---

## Common Mistakes

- **No cancel flow at all** — Instant cancel leaves money on the table. Even a simple survey + one offer saves 10-15%
- **Making cancellation hard to find** — Hidden cancel buttons breed resentment. Shopify requires easy cancellation.
- **Same offer for every reason** — A blanket discount doesn't address "not using it" or "missing feature"
- **Discounts too deep** — 50%+ discounts train customers to cancel-and-return for deals
- **Ignoring involuntary churn** — Often 30-50% of total churn and the easiest to fix
- **No dunning emails** — Letting payment failures silently cancel accounts
- **Guilt-trip copy** — "Are you sure you want to abandon us?" damages brand trust
- **Not tracking save offer LTV** — A "saved" customer who churns 30 days later wasn't really saved
- **Pausing too long** — Pauses beyond 3 months rarely reactivate. Set limits.
- **No post-cancel path** — Make reactivation easy and trigger win-back emails

---

## Tool Integrations

### BenOS Stack
- **Klaviyo MCP** — Dunning sequences, win-back flows, re-engagement emails; `klaviyo_create_email_template`, `klaviyo_get_flows`, `klaviyo_get_flow_report`, `klaviyo_get_segments`
- **Shopify MCP** — WIC subscription billing data, subscription status, skip/pause history; `graphql_query`, `get-order`, `list-orders`

### Related Skills

- **onboarding-cro** — Fix activation to prevent early churn (run this first for sub-60-day churn)
- **email-sequence** — For win-back email sequences after cancellation
- **paywall-upgrade-cro** — For in-app upgrade moments and trial expiration
- **pricing-strategy** — For plan structure and discount strategy
- **analytics-tracking** — For setting up churn signal events
- **ab-test-setup** — For testing cancel flow variations with statistical rigor

## Limitations
- Use this skill only when the task clearly matches the scope described above.
- Do not treat the output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
