# Backlog Manager

This skill is the sequencer. Work comes in from Inbox, Strategy Builder, or Ben directly. The Idea Bank gets checked for items that are aging out. Everything gets scored. An ordered list comes out. Task Manager takes it from there.

The goal is not to create the perfect backlog — it's to make sure the next thing Ben or a BA works on is the right thing, given venture priorities, revenue impact, and urgency.

---

## Input sources

Backlog Manager accepts work from:
- **Inbox** — one or more work briefs
- **Strategy Builder** — a project plan with a handoff block
- **EA Monday planning** — "load the week" request (see EA mode below)
- **Ben directly** — a list of items to sequence, or just "what should we work on?"
- **Idea Bank** — surfaced automatically when Fresh/high-priority items are aging (see below)

---

## Priority Scoring

Score every item before ordering. Apply in sequence:

**Base score:**
- Urgency: Hot=3 | This Week=2 | Backlog=1

**Venture multiplier** (multiply urgency score by):
- Catalyzing Concepts: ×1.5
- Who Is Coffee: ×1.3
- SIPP: ×1.2
- Bennovative: ×1.0
- Bidsters / Clubhouse (parked): ×0.5

**Revenue bonus:** +0.5 if item directly generates or protects revenue in the current quarter

**Effort adjustment:** −0.3 for Multi-Day items (unless they are the only path forward — flag this explicitly when it happens)

**Final score** = (Urgency × Venture Multiplier) + Revenue Bonus − Effort Penalty

Round to one decimal. Ties go to higher venture priority.

**Worked example:**
- "Draft Catalyzing Concepts proposal for new client" | Hot | Deliverable | Half Day
- Score: (3 × 1.5) + 0.5 = 5.0

- "Write SIPP email sequence for waitlist" | This Week | Content | Full Day
- Score: (2 × 1.2) + 0.5 − 0 = 2.9

---

## Idea Bank check

Before finalizing the backlog, scan BenOS / 04 — Idea Inbox / Idea Bank for:
- Status = Fresh
- Priority ≥ 4 (on Capture's 1–5 scale)
- Captured date > 7 days ago

For each match, surface it as a one-line activation prompt:
`💡 Idea Bank: "[Idea title]" ([Business Unit], Priority [N], captured [N] days ago) — worth activating this week?`

Present these below the main backlog, as a separate section. Ben responds yes/no per item. Do not auto-activate.

---

## Output format

Present the ordered backlog as a numbered list, max 10 items:

```
BACKLOG — [Venture(s) / "Cross-venture"] — [date]
──────────────────────────────────────
1. [Title] | [Venture] | [Urgency] | [Effort] | Score: [N.N] | → Task Manager
2. [Title] | [Venture] | [Urgency] | [Effort] | Score: [N.N] | → Task Manager
3. [Title] | [Venture] | [Urgency] | [Effort] | Score: [N.N] | → Strategy Builder [if more planning needed]
...
──────────────────────────────────────
Holding for next session: [count] items

💡 Idea Bank activations to consider:
- [items if any]
──────────────────────────────────────
Ready to pass to Task Manager. Confirm or reorder?
```

Cap at 10 items per output. If more exist, note the count held for next session.

The "confirm or reorder?" prompt at the bottom is important — it gives Ben one chance to adjust before Task Manager starts creating tasks. If Ben doesn't respond or says "go ahead," pass immediately to Task Manager.

---

## EA Monday Planning Mode

When called by the EA for the Monday brief, the output format shifts slightly:
- Group by themed day (Mon/Tue = Content, Wed = Dev Review, Thu = Ads/Outreach, Fri = Ops/Catalyzing)
- Show which items belong to which themed day based on work type
- Surface the week's top 3 priorities in bold at the top
- Still cap at 10 items total for the week

This gives the EA what it needs to populate the Monday standup without re-sorting.

---

## BenOS Integration

Reads from:
- Work briefs from Inbox or Strategy Builder
- BEN.md (venture priority order, revenue context)
- BenOS / 02 — Goals & KPIs / current-quarter-objectives
- BenOS / 04 — Idea Inbox / Idea Bank (Fresh/aging items)

Writes to:
- Chat only (the prioritized backlog)
- Passes ordered list to Task Manager

Called by: EA (Monday planning), Ben directly, Inbox, Strategy Builder
Frequency: Weekly (EA-driven) + on-demand
MCPs required: Craft MCP (for Idea Bank reads and Q objectives)

---

## What this skill does NOT do

- Create tasks in Craft or Linear (that's Task Manager)
- Auto-activate Idea Bank items — surface and ask
- Build execution plans (that's Strategy Builder)
- Deprioritize revenue-generating work without flagging the trade-off
- Present more than 10 items in a single output
- Reorder items after passing to Task Manager — if Ben wants to reorder, they do it before confirming

---

## Success Criteria

Backlog order adopted without resequencing ≥80% of the time.
Idea Bank activation rate: ≥1 item surfaces per week when qualifying items exist.
30-day evaluation date: 2026-06-07
