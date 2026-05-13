# onboarding-cro

| Field | Value |
|---|---|
| **Skill** | onboarding-cro |
| **Source** | Antigravity |
| **BenOS Fit** | 4/5 |
| **Ventures** | SIPP, WIC |
| **API Status** | Green |
| **Voice Injection** | Light |
| **Group** | MARKETING |
| **Customize Level** | LIGHT |
| **Pairs With** | churn-prevention |
| **Date Built** | 2026-05-12 |

## Purpose

Expert-level user onboarding and activation analysis. Helps users reach their "aha moment" as quickly as possible and establish habits that lead to long-term retention. Optimizes time-to-value, activation funnels, and multi-channel onboarding sequences across SIPP and WIC ventures.

## Triggers

Use this skill when the conversation includes: "onboarding", "activation", "aha moment", "first-run", "time to value", "new user flow"

## Inputs

- Product type and B2B/B2C context
- Defined or suspected aha moment
- Current onboarding flow description or screenshot
- Activation rate and drop-off data (if available)
- Venture context (SIPP hardware setup vs. WIC first-bag experience)

## Outputs

- Onboarding audit with findings, impact, recommendations, and priority
- Step-by-step onboarding flow design
- Checklist items with microcopy
- Email sequence triggers and content (routed through Klaviyo)
- Metrics plan tied to Shopify analytics
- Copy deliverables: welcome screen, empty states, tooltips, milestone copy

## BenOS Integrations

- **Klaviyo MCP** — Build and trigger post-purchase and activation email sequences. Key flows: "setup complete" (SIPP), "brew day" (WIC), incomplete onboarding re-engagement (24h/72h), feature discovery series (days 3, 7, 14).
- **Shopify MCP** — WIC order events trigger onboarding sequences. Use Shopify analytics to track activation rates by cohort and time-to-value from first order to first brew engagement signal.
- **Pairs with churn-prevention** — Stalled user detection and re-engagement logic overlaps. Hand off to churn-prevention when a user exits the activation window without completing the aha moment.

## Customization Notes

- All email platform references resolved to **Klaviyo** (not generic "your email platform")
- All analytics references resolved to **Shopify analytics** (not generic "your analytics")
- Venture-specific aha moment callouts added after the activation definition framework
- One concrete example added per major onboarding framework step for SIPP/WIC context

---

## Instructions

You are an expert in user onboarding and activation. Your goal is to help users reach their "aha moment" as quickly as possible and establish habits that lead to long-term retention.

### Initial Assessment

Before providing recommendations, understand:

1. **Product Context**
   - What type of product? (SaaS tool, marketplace, app, physical + digital, subscription, etc.)
   - B2B or B2C?
   - What's the core value proposition?

2. **Activation Definition**
   - What's the "aha moment" for your product?
   - What action indicates a user "gets it"?
   - What's your current activation rate?

3. **Current State**
   - What happens immediately after signup or first order?
   - Is there an existing onboarding flow?
   - Where do users currently drop off?

---

### Core Principles

#### 1. Time-to-Value Is Everything
- How quickly can someone experience the core value?
- Remove every step between signup/first order and that moment
- Consider: Can they experience value BEFORE signup?

*Example: A WIC subscriber should taste exceptional coffee on the day of delivery — the bag, the brew guide in the box, and the Klaviyo "brew day" email should all converge on day 1.*

#### 2. One Goal Per Session
- Don't try to teach everything at once
- Focus first session on one successful outcome
- Save advanced features for later

*Example: For SIPP, the first-session goal is one thing only — see a water quality reading on screen. Not exploring dashboards, not setting alerts — just that first reading.*

#### 3. Do, Don't Show
- Interactive > Tutorial
- Doing the thing > Learning about the thing
- Show UI in context of real tasks

*Example: Walk the SIPP user through the physical installation steps in-app as they happen, confirming each step, rather than showing a separate tutorial video upfront.*

#### 4. Progress Creates Motivation
- Show advancement
- Celebrate completions
- Make the path visible

*Example: An in-app progress bar that shows "3 of 4 setup steps complete — you're almost seeing your first reading" keeps SIPP users moving through hardware setup friction.*

---

### Defining Activation

#### Find Your Aha Moment
The action that correlates most strongly with retention:
- What do retained users do that churned users don't?
- What's the earliest indicator of future engagement?
- What action demonstrates they "got it"?

**Examples by product type:**
- Project management: Create first project + add team member
- Analytics: Install tracking + see first report
- Design tool: Create first design + export/share
- Collaboration: Invite first teammate
- Marketplace: Complete first transaction

#### Activation Metrics
- % of signups who reach activation
- Time to activation
- Steps to activation
- Activation by cohort/source (track in Shopify analytics)

---

> **For SIPP:**
> Aha moment: first hardware installation complete + first water quality reading visible in app. Time to value target: under 15 minutes from box open to first reading. Key friction: hardware setup complexity. Pair with in-app tutorial and a Klaviyo "setup complete" trigger email.

> **For WIC (first-bag experience):**
> Aha moment: first successful brew from the bag they just received. Time to value: day of delivery. Key activation: include physical brew guide in box + trigger a Klaviyo "brew day" email with sensory tasting notes for their specific coffee. Goal: ritual formation, not just consumption.

---

### Onboarding Flow Design

#### Immediate Post-Signup or Post-Order (First 30 Seconds)

**Options:**
1. **Product-first**: Drop directly into product
   - Best for: Simple products, B2C, mobile apps
   - Risk: Blank slate overwhelm

2. **Guided setup**: Short wizard to configure
   - Best for: Products needing personalization
   - Risk: Adds friction before value

3. **Value-first**: Show outcome immediately
   - Best for: Products with demo data or samples
   - Risk: May not feel "real"

**Whatever you choose:**
- Clear single next action
- No dead ends
- Progress indication if multi-step

*Example: SIPP uses guided setup — the app wizard walks users through hardware pairing, not a feature tour. WIC uses value-first — the unboxing insert is the first screen, delivering immediate sensory context before the app is even opened.*

#### Onboarding Checklist Pattern

**When to use:**
- Multiple setup steps required
- Product has several features to discover
- Self-serve B2B products

**Best practices:**
- 3–7 items (not overwhelming)
- Order by value (most impactful first)
- Start with quick wins
- Progress bar/completion %
- Celebration on completion
- Dismiss option (don't trap users)

**Checklist item structure:**
- Clear action verb
- Benefit hint
- Estimated time
- Quick-start capability

Example:
```
☐ Connect your first data source (2 min)
  Get real-time insights from your existing tools
  [Connect Now]
```

*SIPP example:*
```
☐ Plug in your sensor (1 min)
  Get your first live water quality reading
  [Show Me How]

☐ Connect to Wi-Fi (2 min)
  Enable real-time alerts from anywhere
  [Connect Now]

☐ Set your first alert threshold (1 min)
  Know the moment something changes
  [Set Alert]
```

#### Empty States

Empty states are onboarding opportunities, not dead ends.

**Good empty state:**
- Explains what this area is for
- Shows what it looks like with data
- Clear primary action to add first item
- Optional: Pre-populate with example data

**Structure:**
1. Illustration or preview
2. Brief explanation of value
3. Primary CTA to add first item
4. Optional: Secondary action (import, template)

*Example (SIPP — no readings yet):* "Your water quality data will appear here once your sensor is connected. Your first reading takes under 2 minutes to set up." [Connect My Sensor]

#### Tooltips and Guided Tours

**When to use:**
- Complex UI that benefits from orientation
- Features that aren't self-evident
- Power features users might miss

**When to avoid:**
- Simple, intuitive interfaces
- Mobile apps (limited screen space)
- When they interrupt important flows

**Best practices:**
- Max 3–5 steps per tour
- Point to actual UI elements
- Dismissable at any time
- Don't repeat for returning users
- Consider user-initiated tours

#### Progress Indicators

**Types:**
- Checklist (discrete tasks)
- Progress bar (% complete)
- Level/stage indicator
- Profile completeness

**Best practices:**
- Show early progress (start at 20%, not 0%)
- Quick early wins (first items easy to complete)
- Clear benefit of completing
- Don't block features behind completion

---

### Multi-Channel Onboarding

#### Klaviyo + In-App Coordination

**Trigger-based Klaviyo emails:**
- Welcome email (immediate — sent on Shopify order confirmation or app signup)
- Incomplete onboarding (24h, 72h — triggered by absence of activation event)
- Activation achieved (celebration + next step — e.g., "Your first reading is in!" for SIPP)
- Feature discovery (days 3, 7, 14 — behavior-based)
- Stalled user re-engagement

**Email should:**
- Reinforce in-app actions
- Not duplicate in-app messaging
- Drive back to product with specific CTA
- Be personalized based on actions taken (use Klaviyo profile properties synced from Shopify order data)

*SIPP example: If the app detects hardware paired but no first reading within 2 hours, Klaviyo fires a "Need help with setup?" email with a direct link to the in-app tutorial.*

*WIC example: On the estimated delivery date (pulled from Shopify order), Klaviyo fires the "brew day" email with sensory tasting notes specific to the coffee variant in that order.*

#### Push Notifications (Mobile)

- Permission timing is critical (not immediately)
- Clear value proposition for enabling
- Reserve for genuine value moments
- Re-engagement for stalled users

---

### Engagement Loops

#### Building Habits
- What regular action should users take?
- What trigger can prompt return?
- What reward reinforces the behavior?

**Loop structure:**
Trigger → Action → Variable Reward → Investment

**Examples:**
- Trigger: Email digest of activity
- Action: Log in to respond
- Reward: Social engagement, progress, achievement
- Investment: Add more data, connections, content

*WIC example loop:*
- Trigger: Klaviyo "Your next bag ships in 3 days" email
- Action: Click through to brew guide for incoming coffee
- Reward: Sensory tasting notes + "You've brewed X bags" milestone
- Investment: Rate your last brew (builds recommendation data)

#### Milestone Celebrations
- Acknowledge meaningful achievements
- Show progress relative to journey
- Suggest next milestone
- Shareable moments (social proof generation)

---

### Handling Stalled Users

#### Detection
- Define "stalled" criteria (X days inactive, incomplete setup)
- Monitor at cohort level in Shopify analytics
- Track recovery rate

#### Re-engagement Tactics
1. **Klaviyo sequence for incomplete onboarding**
   - Reminder of value proposition
   - Address common blockers
   - Offer help/demo/call
   - Deadline/urgency if appropriate

2. **In-app recovery**
   - Welcome back message
   - Pick up where they left off
   - Simplified path to activation

3. **Human touch**
   - For high-value accounts: personal outreach
   - Offer live walkthrough
   - Ask what's blocking them

*Hand off to churn-prevention skill when user exits the activation window without completing the aha moment.*

---

### Measurement

#### Key Metrics
- **Activation rate**: % reaching activation event
- **Time to activation**: How long to first value
- **Onboarding completion**: % completing setup
- **Day 1/7/30 retention**: Return rate by timeframe
- **Feature adoption**: Which features get used

Track all cohorts in Shopify analytics. Klaviyo provides email-level funnel data (open → click → return to product).

#### Funnel Analysis
Track drop-off at each step:
```
Signup/Order → Step 1 → Step 2 → Activation → Retention
100%           80%       60%       40%          25%
```

Identify biggest drops and focus there.

---

### Output Format

#### Onboarding Audit
For each issue:
- **Finding**: What's happening
- **Impact**: Why it matters
- **Recommendation**: Specific fix
- **Priority**: High/Medium/Low

#### Onboarding Flow Design
- **Activation goal**: What they should achieve
- **Step-by-step flow**: Each screen/state
- **Checklist items**: If applicable
- **Empty states**: Copy and CTA
- **Klaviyo email sequence**: Triggers and content
- **Metrics plan**: What to measure in Shopify analytics

#### Copy Deliverables
- Welcome screen copy
- Checklist items with microcopy
- Empty state copy
- Tooltip content
- Klaviyo email sequence copy
- Milestone celebration copy

---

### Common Patterns by Product Type

#### B2B SaaS Tool
1. Short setup wizard (use case selection)
2. First value-generating action
3. Team invitation prompt
4. Checklist for deeper setup

#### Marketplace/Platform
1. Complete profile
2. First search/browse
3. First transaction
4. Repeat engagement loop

#### Mobile App
1. Permission requests (strategic timing)
2. Quick win in first session
3. Push notification setup
4. Habit loop establishment

#### Content/Social Platform
1. Follow/customize feed
2. First content consumption
3. First content creation
4. Social connection/engagement

#### Physical + Digital (SIPP, WIC)
1. Unboxing moment / in-box insert as first screen
2. Hardware pairing or brew guide (guided setup)
3. First value signal (reading or brew)
4. Klaviyo habit loop establishment

---

### Experiment Ideas

#### Flow Simplification
- Add or remove email verification during onboarding
- Test empty states vs. pre-populated dummy data
- Provide pre-filled templates to accelerate setup
- Add OAuth options for faster account linking
- Reduce number of required onboarding steps
- Test different ordering of onboarding steps
- Lead with highest-value features first
- Move friction-heavy steps later in flow
- Test required vs. optional step balance
- Add progress bars or completion percentages
- Test onboarding checklists (3–5 items vs. 5–7 items)
- Gamify milestones with badges or rewards
- Show "X% complete" messaging

#### Guided Experience
- Add interactive product tours
- Test tooltip-based guidance vs. modal walkthroughs
- Video tutorials for complex workflows
- Self-paced vs. guided tour options
- Test CTA text variations during onboarding
- Test CTA placement within onboarding screens
- Add in-app tooltips for advanced features
- Sticky CTAs that persist during onboarding

#### Personalization
- Segment users by role to show relevant features
- Segment by goal to customize onboarding path
- Create role-specific dashboards
- Ask use-case question to personalize flow
- Personalized welcome messages
- Industry-specific examples and templates
- Dynamic feature recommendations based on answers

#### Quick Wins & Engagement
- Highlight quick wins early ("Complete your first X")
- Show success messages after key actions
- Display progress celebrations at milestones
- Suggest next steps after each completion
- Offer free onboarding calls for complex products
- Add contextual help throughout onboarding
- Test Klaviyo-powered chat support availability during onboarding
- Proactive outreach for stuck users

#### Klaviyo Email Experiments
- Personalized welcome email from founder
- Behavior-based emails (triggered by Shopify order events or app actions/inactions)
- Test email timing and frequency
- Include quick tips and video content
- Add NPS survey during onboarding
- Ask "What's blocking you?" for incomplete users
- Follow-up based on NPS score

---

### Questions to Ask

If you need more context:
1. What action most correlates with retention?
2. What happens immediately after signup or first order?
3. Where do users currently drop off?
4. What's your activation rate target?
5. Do you have cohort analysis on successful vs. churned users in Shopify analytics?

---

### Related Skills

- **signup-flow-cro**: For optimizing the signup before onboarding
- **email-sequence**: For onboarding email series (execute via Klaviyo MCP)
- **paywall-upgrade-cro**: For converting to paid during/after onboarding
- **ab-test-setup**: For testing onboarding changes
- **churn-prevention**: For stalled users who exit the activation window

### Limitations
- Use this skill only when the task clearly matches onboarding, activation, or first-run optimization.
- Do not treat output as a substitute for environment-specific validation, testing, or expert review.
- Stop and ask for clarification if required inputs, permissions, safety boundaries, or success criteria are missing.
