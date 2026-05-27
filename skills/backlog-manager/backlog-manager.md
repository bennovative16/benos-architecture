# Backlog Manager

This skill is the sequencer. Work comes in from Inbox, Strategy Builder, EA, or Ben directly. The Idea Bank gets checked for items that are aging out. Everything gets scored. An ordered list comes out. Task Manager takes it from there.

The goal is not to create the perfect backlog — it's to make sure the next thing Ben or a BA works on is the right thing, given venture priorities, revenue impact, and urgency.

---

## Input sources

Backlog Manager accepts work from:
- **Inbox** — one or more work briefs (may include `[CHAINED]` flag)
- **Strategy Builder** — a project plan with a handoff block
- **EA Monday planning** — "load the week" request (see EA mode below)
- **EA Mode 4 (Reprioritize)** — revised priorities for today, already resolved to task IDs where applicable
- **Ben directly** — a list of items to sequence, or "what should we work on?"
- **Idea Bank** — surfaced automatically when Fresh/high-priority items are aging (see below)

---

## Context reads

Before scoring, load (graceful-degrade if missing — never block):

1. **BEN.md / North Star** → Supabase
   ```sql
   SELECT content FROM public.knowledge_base WHERE slug = 'ben';
   ```
   If thin, fall back to venture priority order known from prior context.

2. **Quarter objectives** → no Supabase home yet. Skip and note the gap. Do not block.

3. **Venture priority order** — derived from BEN.md if available, otherwise default:
   - Catalyzing Concepts (CC) — revenue + relaunch priority
   - Who Is Coffee (WIC) — revenue scale
   - SIPP — pre-revenue, milestone-driven
   - Bennovative — content + audience
   - BenOS Ops — infrastructure
   - Bidsters / Clubhouse — parked

---

## Priority Scoring

Score every item before ordering. Apply in sequence.

**Base score:**
- Urgency: Hot=3 | This Week=2 | Backlog=1

**Venture multiplier** (multiply urgency score by):
- Catalyzing Concepts: ×1.5
- Who Is Coffee: ×1.3
- SIPP: ×1.2
- Bennovative: ×1.0
- Bidsters / Clubhouse (parked): ×0.5
- BenOS Ops: ×1.0

**Revenue bonus:** +0.5 if item directly generates or protects revenue in the current quarter.

**Effort adjustment:** −0.3 for Multi-Day or larger items (l, xl in the tasks effort enum) — unless they are the only path forward. When applying, flag explicitly.

**Final score** = (Urgency × Venture Multiplier) + Revenue Bonus − Effort Penalty

Round to one decimal. Ties go to higher venture priority.

**Worked example:**
- "Draft Catalyzing Concepts proposal for new client" | Hot | Deliverable | Half Day → (3 × 1.5) + 0.5 = 5.0
- "Write SIPP email sequence for waitlist" | This Week | Content | Full Day → (2 × 1.2) + 0.5 = 2.9

---

## Idea Bank check

Before finalizing the backlog, scan Supabase `idea_bank` for items that are aging:

```sql
SELECT id, title, business_unit, priority, captured_date,
       CURRENT_DATE - captured_date AS days_old
FROM public.idea_bank
WHERE status = 'Fresh'
  AND priority >= 4
  AND captured_date < CURRENT_DATE - INTERVAL '7 days'
ORDER BY priority DESC, captured_date ASC
LIMIT 10;
```

For each match, surface a one-line activation prompt:

`💡 Idea Bank: "[Title]" ([business_unit], Priority [N], captured [days_old] days ago) — worth activating this week?`

Present these below the main backlog, as a separate section. Ben responds yes/no per item. Do not auto-activate.

**Chained mode exception:** Skip the Idea Bank check when called with `[CHAINED]`. The chained path is for processing a specific work brief, not full backlog review. Idea Bank surfacing happens in EA standup mode and EA Monday mode only.

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
- [items if any — omit section in chained mode]
──────────────────────────────────────
[Standalone: "Ready to pass to Task Manager. Confirm or reorder?"]
[Chained: pass to Task Manager immediately — no confirmation prompt]
```

Urgency labels in output use the readable form (Hot / This Week / Backlog). Task Manager translates these to the `priority` enum (urgent / high / medium / low) when writing to `public.tasks`. Effort labels can be either the readable form (Quick / Half Day / Full Day / Multi-Day) or the new enum (xs / s / m / l / xl) — Task Manager accepts both.

**Chained mode:** When the input includes `[CHAINED — skip confirmation checkpoints]`, omit the "Confirm or reorder?" prompt entirely. Score and sequence, pass immediately to Task Manager.

Cap at 10 items per output. If more exist, note the count held for next session.

---

## EA Monday Planning Mode

When called by EA for the Monday brief, the output format shifts:
- Group by themed day (Mon/Tue = Content, Wed = Dev Review, Thu = Ads/Outreach, Fri = Ops/Catalyzing)
- Show which items belong to which themed day based on work type
- Surface the week's top 3 priorities in bold at the top
- Still cap at 10 items total for the week

This gives EA what it needs to populate the Monday standup without re-sorting.

---

## EA Mode 4 (Reprioritize) Handoff

When called by EA Mode 4, input arrives with revised priorities already resolved to task IDs (or marked "no match — create new"). Backlog Manager's role in Mode 4 is light:

1. Re-score the revised three using the same logic
2. Output the ordered list with task IDs preserved
3. Hand off to Task Manager with `[UPDATE]` flag for items with existing IDs, `[CHAINED]` flag for new items

Example output for Mode 4:

```
REVISED PRIORITIES — [date HH:MM]
──────────────────────────────────────
1. [Title] | [Venture] | task-abc12345 | → Task Manager [UPDATE: due_date today]
2. [Title] | [Venture] | NEW            | → Task Manager [CHAINED, CREATE]
3. [Title] | [Venture] | task-def67890 | → Task Manager [UPDATE: priority urgent]

Deferred:
- task-ghi54321 → Task Manager [UPDATE: defer_tomorrow]

Dropped:
- task-jkl98765 → Task Manager [UPDATE: drop]
──────────────────────────────────────
Passing to Task Manager.
```

No Idea Bank check in Mode 4 — same as chained mode.

---

## BenOS Integration

Reads from:
- Work briefs from Inbox, Strategy Builder, or EA
- Supabase `knowledge_base` (BEN.md content via slug='ben')
- Supabase `idea_bank` (Fresh/aging items — standalone and EA-Monday modes only)

Writes to:
- Chat only (the prioritized backlog)
- Passes ordered list to Task Manager (CREATE for new items, UPDATE for resolved task IDs)

Called by: EA (Monday planning + Mode 4), Inbox (chained), Strategy Builder, Ben directly
Frequency: Weekly (EA-driven) + Mode 4 (on-demand) + ad-hoc
MCPs required: Supabase MCP

---

## What this skill does NOT do

- Create or update tasks in Supabase or Linear — that's Task Manager
- Auto-activate Idea Bank items — surface and ask (standalone and EA-Monday modes only)
- Build execution plans — that's Strategy Builder
- Deprioritize revenue-generating work without flagging the trade-off
- Present more than 10 items in a single output
- Reorder items after passing to Task Manager — Ben reorders before confirming
- Ask for confirmation when in chained mode or in EA Mode 4 handoff

---

## Success Criteria

Backlog order adopted without resequencing ≥80% of the time.
Idea Bank activation rate: ≥1 item surfaces per week when qualifying items exist.
Chained mode: 0 confirmation pauses.
EA Mode 4 handoff: 100% of task IDs preserved through to Task Manager.
30-day evaluation date: 2026-06-22

---

## HANDOFF

**Receives from:** EA Mode 4 (primary) | Strategy Builder (post-plan cascade) | Ben directly
**Input:** raw task list or project handoff block + venture context from BEN.md
**Produces:** sequenced, prioritized backlog with effort tags — ordered list ready for Task Manager
**Passes to:** Task Manager (to create Supabase task rows from the ordered list)
**Completion log:** Output delivered in chat or as chained input to Task Manager. No direct database write.
