# Task Manager

This skill turns a work item into a tracked task in the right system, OR updates an existing task in place. Two systems. One rule: dev and UI design go to Linear. Everything else goes to Supabase `public.tasks`.

Routing matters because Linear and Supabase serve different audiences. Linear is the dev board — Codex and technical work live there. Supabase is the operational layer — everything else gets managed there. Mixing them creates noise in both.

This skill operates in three modes:
- **CREATE mode** (default): turns a work brief into a new task row.
- **UPDATE mode**: changes an existing task's due date, priority, or status. Invoked by EA Mode 4 mid-day reprioritization, or by Ben directly.
- **RESOLVE mode**: helper that takes a free-text priority title and finds matching existing task IDs. Used by EA Mode 4 before it invokes UPDATE mode.

---

## Routing Logic

**→ Linear** when the work is:
- Software development (features, bug fixes, backend, API)
- UI design (mockups, Figma, design system)
- Mobile app work (Flutter, SIPP mobile, any app-native task)
- Technical integrations or infrastructure

**→ Supabase `public.tasks`** when the work is:
- Content creation (writing, emails, newsletters, social posts)
- Business operations (client outreach, proposals, calls, follow-ups)
- Marketing and campaigns
- Strategy and planning
- Research and analysis
- Administrative
- Anything that doesn't involve writing or shipping code or design

**CC client work** follows the same rule — content/ops/strategy tasks go to `public.tasks` with `venture='cc'`. Never route CC client data to Linear (client confidentiality).

When in doubt, ask one question: "Does this require a developer or designer to complete?" Yes → Linear. No → Supabase.

---

## CREATE Mode

### Step 1 — Receive input

Input can be:
- A structured work brief from Inbox or Backlog Manager
- A direct task spec from Ben or a BA
- A project plan from Strategy Builder (creates multiple tasks)

Extract from input: Venture, Work Type, Title, What, Why, Done When, Dependencies, Due Date, Urgency, Effort, optional Project link.

### Step 2 — Map urgency and effort to enum values

The new tasks schema uses tight enums. Translate input labels to enum values:

**Urgency → `priority` enum:**

| Input label | priority value |
|---|---|
| 🔴 Hot | urgent |
| 🟡 This Week | high |
| 🟢 Backlog | medium |
| Later / Long-horizon | low |

**Effort label → `effort` enum:**

| Input label | effort value |
|---|---|
| Quick (<1hr) | xs |
| Half Day | s |
| Full Day | m |
| Multi-Day | l |
| Project (>1 week) | xl |

If urgency or effort is not provided in the input, leave `priority`/`effort` as NULL — the schema permits it.

### Step 3 — Set due date

**Chained invocation** (brief contains `[CHAINED — skip confirmation checkpoints]`): infer due date from urgency. Never ask. Never block.
- urgent → tomorrow
- high → next Friday
- medium → 14 days from today
- low → 30 days from today

**Standalone invocation** (Ben or BA called Task Manager directly): due date is required. If missing, ask once: "What's the due date for [title]?" Then proceed.

### Step 4 — Route

Apply the routing logic above. Binary. If something genuinely sits between dev and ops, route to Supabase (operational is default).

### Step 5a — Insert into Supabase `public.tasks`

Generate a task ID using format `task-XXXXXXXX` (8 hex chars, lowercase). Then execute via Supabase MCP `execute_sql`:

```sql
INSERT INTO public.tasks (
  id, title, description, due_date, done,
  venture, venture_id, project_id, priority, effort,
  skill_chain, created_at
) VALUES (
  'task-<8 hex chars>',
  '<Title from brief>',
  '<What + Why + Done When + Dependencies, combined as readable prose>',
  '<YYYY-MM-DD>',
  false,
  '<venture slug — sipp | wic | cc | bennovative | benos-ops>',
  '<venture slug — same as venture>',
  '<project_id if applicable, else NULL>',
  '<urgent | high | medium | low | NULL>',
  '<xs | s | m | l | xl | NULL>',
  '[]'::jsonb,
  now()
);
```

Venture slug must be lowercase and match a valid value: `sipp`, `wic`, `cc`, `bennovative`, `benos-ops`. If the venture in the brief uses a different label (e.g., "SIPP" or "Who Is Coffee"), normalize before insert.

### Step 5b — Insert into Linear (dev/UI route)

Use Linear MCP `save_issue` (no ID passed = create):
- title: from brief
- description: full context block using the template below
- dueDate: from brief
- team: appropriate team for the venture
- labels: relevant labels by work type

Description template:
```
## What
[From brief]

## Why
[From brief]

## Done when
[From brief]

## Dependencies
[From brief]
```

### Step 6 — Confirm creation

After creating each task, output one line:

- Supabase: `✅ Task created — "[Title]" | id: task-xxxxxxxx | Due: YYYY-MM-DD | venture: [slug] | priority: [enum]`
- Linear: `✅ Linear issue created — "[Title]" | id: [LIN-id] | Due: YYYY-MM-DD | Team: [team]`

Nothing more. The task is created. Ben moves on.

---

## UPDATE Mode

Triggered when input contains `[UPDATE]` flag with task IDs and dispositions. Most common caller: EA Mode 4 (mid-day reprioritization).

### Input format

```
[UPDATE]
task-XXXXXXXX: <disposition>
task-YYYYYYYY: <disposition>
LIN-123: <disposition>            # Linear IDs also supported
```

Disposition vocabulary:
- `keep_today` — no-op (acknowledge in output, no SQL)
- `defer_to YYYY-MM-DD` — set `due_date` to specified date
- `defer_tomorrow` — set `due_date` to (today + 1 day)
- `drop` — mark `done=true` with a note prefix `[Dropped via reprioritization YYYY-MM-DD]` added to `description`. Default behavior — preserves audit trail. To truly delete, use `delete` disposition instead.
- `delete` — `DELETE FROM public.tasks WHERE id = ?`. Use sparingly. Cannot be undone.
- `priority <urgent|high|medium|low>` — change `priority` enum
- `due_date YYYY-MM-DD` — set due_date directly (alias for defer_to)
- `complete` — mark `done=true` with no description change (clean completion)

### Process

For each row in the UPDATE block:

**1. Validate the ID.**

```sql
SELECT id, title, venture, due_date, priority, done
FROM public.tasks
WHERE id = '<id>';
```

If no row found: emit `⚠️ Task <id> not found — skipped.` Continue to next row.

**2. Apply disposition SQL.**

```sql
-- defer_to YYYY-MM-DD  /  defer_tomorrow  /  due_date YYYY-MM-DD
UPDATE public.tasks
SET due_date = '<new date>'
WHERE id = '<id>';

-- drop (mark done with audit note)
UPDATE public.tasks
SET done = true,
    description = '[Dropped via reprioritization ' || CURRENT_DATE::text || '] ' || COALESCE(description, '')
WHERE id = '<id>';

-- delete (permanent)
DELETE FROM public.tasks WHERE id = '<id>';

-- priority change
UPDATE public.tasks
SET priority = '<urgent | high | medium | low>'
WHERE id = '<id>';

-- complete (clean done)
UPDATE public.tasks
SET done = true
WHERE id = '<id>';
```

**3. Confirm.** One line per row:

`✅ Updated <id> — "[title]" — [disposition + new value]`

For `keep_today`: `↪ <id> — "[title]" — kept on today`

**4. Linear-routed IDs** (IDs not matching `task-XXXXXXXX` format): use Linear MCP `save_issue` with the issue ID passed in, translating the disposition to Linear semantics — `defer_to` → update dueDate, `drop` → state=cancelled, `complete` → state=done, `priority` → priority field.

---

## RESOLVE Mode

Called by EA Mode 4 when revised priorities arrive as free text and need to be matched to existing task IDs before UPDATE can run.

### Input format

```
[RESOLVE] venture=<slug>
- <priority title 1>
- <priority title 2>
- ...
```

### Process

For each title, run a fuzzy search against open tasks for that venture:

```sql
SELECT id, title, due_date, priority
FROM public.tasks
WHERE venture = '<slug>'
  AND done = false
  AND (
    title ILIKE '%' || '<key terms>' || '%'
    OR description ILIKE '%' || '<key terms>' || '%'
  )
ORDER BY
  CASE WHEN due_date IS NULL THEN 1 ELSE 0 END,
  due_date ASC
LIMIT 5;
```

Extract key terms from the priority title by removing stopwords and keeping the 2–3 most distinctive nouns/verbs.

### Output

One block per priority title:

```
"<priority title>" — venture: <slug>
  Candidates:
  - task-abc12345 — "<title>" (due YYYY-MM-DD, priority: high)
  - task-def67890 — "<title>" (due YYYY-MM-DD, priority: medium)
  - No matches — will create new task
```

Return candidates to caller (EA Mode 4). EA presents to Ben for confirmation. EA then calls UPDATE mode with the confirmed IDs.

---

## Batch mode (project briefs)

When receiving a project brief with multiple tasks, create them in dependency order. Confirm each as it's created. End with: `[N] tasks created for [Project Title]`.

---

## BenOS Integration

Reads from:
- Work briefs (Inbox, Backlog Manager, direct input)
- Project plans (Strategy Builder)
- Supabase `public.tasks` (UPDATE and RESOLVE modes)

Writes to:
- Supabase `public.tasks` (INSERT in CREATE, UPDATE/DELETE in UPDATE mode)
- Linear issues via Linear MCP (dev/UI work)

Called by: Backlog Manager (primary), Inbox (chained), EA Mode 4 (UPDATE + RESOLVE), Ben directly, any BA.

MCPs required: Supabase MCP (always) | Linear MCP (dev/UI tasks only).

---

## What this skill does NOT do

- Prioritize tasks — that's Backlog Manager
- Plan projects — that's Strategy Builder
- Create tasks without a due date in standalone CREATE mode — ask for it
- Create tasks without a venture
- Route dev work to Supabase or ops work to Linear
- Ask for due date when in chained CREATE mode — infer it from urgency
- Update a task without a valid existing ID — surface the failure, skip the row
- Hard-delete tasks unless the disposition is explicitly `delete` — default is `drop` (mark done with audit note)

---

## Success Criteria

100% of CREATE invocations produce tasks with due date and venture set.
Routing accuracy (Linear vs Supabase): ≥95% without manual correction.
UPDATE mode: 100% disposition coverage (no silently-failed updates).
RESOLVE mode: ≥80% of priority titles resolved to a single confident candidate.
Chained mode: 0 blocked invocations due to missing fields.
30-day evaluation date: 2026-06-22

---

## HANDOFF

**Receives from:** Backlog Manager (primary) | Inbox (chained) | EA Mode 4 (UPDATE + RESOLVE) | BA skills | Ben directly
**Input:** venture + title + description + priority/effort/due_date (optional) + task IDs if UPDATE/RESOLVE mode
**Produces:** Supabase task row (CREATE) or updated task row (UPDATE) — one confirmation line per task
**Passes to:** Ben — final output (task ID confirmation). In chained mode, passes task IDs back to calling skill.
**Completion log:** Task written to Supabase `public.tasks`. Linear issue created/updated for dev/UI tasks.
