# Capture

**Skill:** `capture`
**Status:** Live
**Last Updated:** 2026-05-08

---

## Purpose

Zero-friction idea capture for BenOS. Ben types an idea naturally — anywhere, in any format. The skill classifies, enriches, and writes a new row to the Idea Bank silently, with one confirmation line back. The work is invisible. Ben never has to think about how to format an idea or reach for a command.

## Triggers

- "Idea —"
- "Capture —"
- "Add to idea bank"
- "/capture"
- Any message that is clearly a raw idea being dropped into chat

Trigger sensitivity is HIGH. Missing an idea is worse than an occasional false positive.

## Scope

**Handles:** preserving the exact verbatim raw text, duplicate-checking against the Idea Bank, classifying business unit / content pillar / type / priority, enriching with a polished summary and 2–3 implementation paths, writing to the Idea Bank, and a single one-line confirmation.

**Does NOT:**
- Ask more than one clarifying question per capture (only when business unit is genuinely ambiguous)
- Modify the Raw Idea field after writing
- Present options or alternatives
- Produce lengthy output
- Create multiple rows for one idea
- Overwrite existing rows
- Proceed if Craft MCP is unavailable — hold in chat and notify Ben instead

## Inputs

- Raw idea text typed by Ben (one line, paragraph, or voice transcript — no structure required)
- BenOS / 00 — North Star / BEN.md
- BenOS / 05 — Content Pillars
- BenOS / 06 — Audiences
- BenOS / 04 — Idea Inbox / Idea Bank (duplicate check)

## Outputs

- One new row in BenOS / 04 — Idea Inbox / Idea Bank with Title, Raw Idea (verbatim), Polished Summary, Implementation Ideas, Business Unit, Content Pillar, Type, Priority, Status = Fresh, Captured Date
- Exactly one confirmation line in chat: `Captured → [Business Unit] / [Type] / [Pillar] → Idea Bank`

## Integration

**Reads from:** BEN.md, Content Pillars, Audiences, Idea Bank
**Writes to:** Idea Bank (new row)
**Called by:** Ben directly
**Frequency:** On-demand, multiple times daily
**MCPs required:** Craft MCP

## Full Instructions

# Capture

Zero-friction idea capture for BenOS. Ben types an idea naturally. This skill does all the work. One confirmation line. Nothing else.

Read first: BenOS / 00 — North Star / BEN.md
Read second: BenOS / 05 — Content Pillars
Read third: BenOS / 06 — Audiences
Read fourth: BenOS / 04 — Idea Inbox / Idea Bank (duplicate check)

## Input

Raw idea text typed by Ben in Claude chat. Format: freeform — one line, paragraph, or voice transcript. No structure required. No command format required. Ben should never have to think about how to format an idea.

## Process

### Step 1 — Capture Raw Text

Preserve the exact verbatim input. This becomes the Raw Idea field. Never modify it. Never summarize it here. Save it exactly as typed.

### Step 2 — Duplicate Check

Scan BenOS / 04 — Idea Inbox / Idea Bank for similar existing entries.

If a strong match exists (same core idea, same business unit):
→ Surface it: "This looks similar to [existing idea title] captured on [date]. Merge or keep separate?"
→ Wait for one-word response. Then proceed.

If no match: proceed silently.

### Step 3 — Classify

**Business Unit:** Map to one or more of:
- SIPP — water quality, hardware, smart home, environment
- Who Is Coffee — coffee, DTC, wholesale, farmers, conservation
- Catalyzing Concepts — commercialization, R&D, grants, consulting
- Bidsters — construction, preconstruction, CRM, contractors
- Clubhouse — fantasy golf, sports, gaming
- Bennovative — personal brand, stoicism, content, doing hard things
- Cross-venture — serves multiple units equally

If genuinely ambiguous: ask ONE question. "Which business is this for — [option A] or [option B]?" Never ask more. Never ask about anything else. Write immediately on response.

**Content Pillar:** Map to one of:
- Doing Hard Things
- Stoicism Applied
- Water & Conservation
- Builder Community
- Coffee & Ritual
- Tech & Society

If idea does not map cleanly to a pillar: leave blank.

**Type:**
- Content — blog post, video, newsletter, social content
- Product — feature, hardware, software, new product
- Strategic — business model, partnership, positioning
- Campaign — multi-piece coordinated marketing effort

**Priority:** Score 1-5 based on:
- 5: Directly serves current Q objective, high urgency
- 4: Serves current Q objective, not urgent
- 3: Serves a business goal, not current Q priority
- 2: Good idea, no clear home right now
- 1: Speculative, long horizon

### Step 4 — Enrich

**Polished Summary:** Restate the idea cleanly in one paragraph. Remove filler, clarify intent, make it readable six months from now. This is the skill's interpretation — Ben edits it freely.

**Implementation Ideas:** Generate 2-3 concrete execution paths. Specific enough to act on. Not commitments — possibilities.

Examples of good implementation ideas:
- "Write a Herk's Hits issue pairing this track with the concept"
- "Build as a Linear feature ticket for the next SIPP sprint"
- "Draft a cold email sequence targeting this specific audience"

### Step 5 — Write to Idea Bank

Create a new row in BenOS / 04 — Idea Inbox / Idea Bank with:

```
Title              [concise, specific, derived from idea]
Raw Idea           [verbatim original — never modified]
Polished Summary   [clean restatement from Step 4]
Implementation     [2-3 execution paths from Step 4]
Ideas
Business Unit      [from Step 3]
Content Pillar     [from Step 3]
Type               [from Step 3]
Priority           [from Step 3]
Status             Fresh
Captured Date      [today's date]
Revisit Date       [blank]
Reactivation       [blank]
Signal
Linked Output      [blank]
Notes              [any additional context worth preserving]
```

### Step 6 — Confirm

Output exactly one line to Ben:
"Captured → [Business Unit] / [Type] / [Pillar] → Idea Bank"

Nothing else. No summary. No options. No follow-up questions. The work is done. Ben moves on.

## Output

One confirmation line in chat. One new row in BenOS / 04 — Idea Inbox / Idea Bank.

## BenOS Integration

**Reads from:**
- BenOS / 00 — North Star / BEN.md
- BenOS / 05 — Content Pillars
- BenOS / 06 — Audiences
- BenOS / 04 — Idea Inbox / Idea Bank (duplicate check)

**Writes to:**
- BenOS / 04 — Idea Inbox / Idea Bank (new row)

Called by: Ben directly
Frequency: On-demand, multiple times daily
MCPs required: Craft MCP

## Output Format Rules

No options. No first-pass alternatives. This skill has one output format always. Fast, silent, invisible enrichment. One confirmation line. Done.

## Success Criteria

≥90% of captured ideas appear in Idea Bank with correct business unit and type without manual correction by Ben.
30-day evaluation date: 2026-06-07

## What This Skill Does NOT Do

- Ask more than one clarifying question per capture
- Modify the Raw Idea field after writing
- Present options or alternatives
- Produce lengthy output
- Create multiple rows for one idea
- Overwrite existing rows
- Proceed if Craft MCP is unavailable (hold in chat, notify Ben instead)

EOF
