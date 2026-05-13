
# Task Manager

This skill turns a work item into a real tracked task in the right system. Two systems. One rule: dev and UI design go to Linear. Everything else goes to Craft.

Getting this routing right matters because Linear and Craft serve different audiences and workflows. Linear is the dev board — it's where Codex and technical work lives. Craft is the operational layer — it's where everything else gets managed. Mixing them creates noise in both.

---

## Routing Logic

**→ Linear** when the work is:
- Software development (features, bug fixes, backend, API work)
- UI design (mockups, Figma work, design system updates)
- Mobile app work (Flutter, SIPP mobile, any app-native task)
- Technical integrations or infrastructure

**→ Craft native task** when the work is:
- Content creation (writing, emails, newsletters, social posts)
- Business operations (client outreach, proposals, calls, follow-ups)
- Marketing and campaigns
- Strategy and planning
- Research and analysis
- Administrative tasks
- Anything that doesn't involve writing or shipping code or design

When in doubt, ask one question: "Does this require a developer or designer to complete?" Yes → Linear. No → Craft.

---

## Process

### Step 1 — Receive input

Input can be:
- A structured work brief from Inbox (preferred — contains all fields)
- A direct task spec from Ben or a BA
- A project plan from Strategy Builder (creates multiple tasks)

Extract from input: Venture, Work Type, Title, What, Why, Done When, Dependencies, Due Date, Hashtags.

**Due date is required.** If it's missing from the input, ask: "What's the due date for [title]?" — one question, then proceed. Never create a task without one.

### Step 2 — Route

Apply the routing logic above. It's binary — no edge cases should require judgment calls. If something genuinely sits between dev and ops, route to Craft (operational tasks are the default).

### Step 3a — Create Craft native task

Use the Craft `tasks_add` tool with:

```
markdown:    [Rich task body — see template below]
deadlineDate: [YYYY-MM-DD]
scheduleDate: [YYYY-MM-DD — same as deadline unless specified otherwise]
location:    inbox
state:       open
```

**Craft task markdown template:**

```markdown
#[Venture] #[WorkType]

**What:** [1-2 sentences from brief]
**Why:** [1 sentence from brief]
**Done when:** [Clear completion signal from brief]
**Dependencies:** [From brief, or "None"]

---
Next step: [First action from brief]
```

The hashtags go at the top of the markdown body — this is what creates the tags in Craft's All Tasks view. They are the only way tasks get tagged by venture. Never skip them.

### Step 3b — Create Linear issue

Use Linear MCP with:
- **Title**: from brief
- **Description**: full context block (What + Why + Done When + Dependencies)
- **Due date**: from brief
- **Team**: appropriate team (SIPP, WIC, etc.)
- **Labels**: add relevant labels based on work type

Linear issue description template:
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

### Step 4 — Confirm creation

After creating each task, output one confirmation line:

For Craft: `✅ Craft task created — "[Title]" | Due: [date] | [#Venture] [#Type]`
For Linear: `✅ Linear issue created — "[Title]" | Due: [date] | [Team]`

Nothing more. The task is created. Ben moves on.

---

## Batch mode (project briefs)

When receiving a project brief with multiple tasks, create them in dependency order:
- Create task 1, confirm
- Create task 2, confirm
- Continue until all tasks are created
- End with: `[N] tasks created for [Project Title]`

Do not bundle all confirmations at the end — confirm each task as it's created so Ben can see progress.

---

## BenOS Integration

Reads from:
- Work brief from Inbox or Backlog Manager
- Direct input from Ben or a BA
- Project plan from Strategy Builder

Writes to:
- Craft native tasks (Craft MCP — `tasks_add`)
- Linear issues (Linear MCP)

Called by: Backlog Manager (primary), Ben directly, any BA
Frequency: On-demand, multiple times daily
MCPs required: Craft MCP (always) | Linear MCP (dev/UI tasks only)

---

## What this skill does NOT do

- Prioritize tasks — that's Backlog Manager
- Plan projects — that's Strategy Builder
- Create tasks without a due date
- Create tasks without venture hashtags
- Route dev work to Craft or ops work to Linear
- Ask for venture context if it's already in the brief or known from calling BA

---

## Success Criteria

100% of tasks created with due date set and venture hashtag applied.
Routing accuracy (Linear vs Craft): ≥95% correct without manual correction.
30-day evaluation date: 2026-06-07
