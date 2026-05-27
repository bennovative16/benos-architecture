# Context Onboarding Engine

Initializes any entity — venture, client, or project — into BenOS with a complete context
package stored in Supabase `knowledge_base`. One skill handles all entity types. The context
package it produces is the foundational record that Business Assistant skills read before
acting on behalf of that entity.

Supersedes client-onboarding skill. Use this for everything.

---

## Step 0 — No Setup Required

`knowledge_base` is the destination for all entity records. No collections to create or
verify — skip directly to Step 1. Entity slugs follow this naming convention:
- Venture: `context-[venture-name]` (type: `venture`)
- Client: `client-[client-name]` (type: `client`)
- Project: `project-[project-name]` (type: `manifest`)

---

## Step 1 — Determine Entity Type

If the entity type was explicit in the trigger ("new client", "new project for SIPP"), proceed.

If not, ask one question:
> "Are we onboarding a venture, a client (CC engagement), or a project?"

Entity types and their paths:
- **Venture** → full five-question intake → `knowledge_base` slug `context-[name]`, type `venture`
- **Client** → full five-question intake → `knowledge_base` slug `client-[name]`, type `client` (always under Catalyzing Concepts)
- **Project** → three-question intake → `knowledge_base` slug `project-[name]`, type `manifest`
  - Follow-up: "Is this under a specific venture, or a standalone project?"

---

## Step 2 — Check for Existing Item

Before creating anything, check for an existing record in `knowledge_base` using the
Supabase MCP `execute_sql` tool (project_id: tedpbnotgirjatlqkjxw):

```sql
SELECT slug, content, updated_at
FROM knowledge_base
WHERE slug = '[entity-slug]'
LIMIT 1
```

**If found:** Surface the existing record.
> "I found an existing [entity type] called [name] — last updated [date]. Want to update the
> existing context, or is this a different [entity type] that happens to share the name?"

If updating: load the current content, identify gaps, run a confirmation/gap-fill pass
instead of a full intake. Preserve everything that's still accurate.

**If not found:** Proceed to Step 3.

---

## Step 3A — Venture or Client Intake

Read BEN.md first via Supabase MCP:
```sql
SELECT content FROM knowledge_base WHERE slug = 'ben'
```
For the four active Bennovative ventures (SIPP, Who Is Coffee, Catalyzing Concepts,
Bennovative), pre-load answers from BEN.md and present them for confirmation.
This turns a 20-minute intake into a 5-minute confirmation pass.

For each of the five questions, present the pre-loaded answer if available:
> "For [question], I have: [pre-loaded answer from BEN.md]. Does this still hold,
> or has anything changed?"

For new ventures or clients not in BEN.md, ask each question fresh.

**The Five Questions:**

**Why** — What is the mission, purpose, or reason this exists?
*For clients: Why are they seeking help now? What's driving the engagement?*

**What 1** — What is the problem or current market condition that creates the opportunity?
*Describe the pain, gap, or friction in the customer's world today.*

**What 2** — What will we do differently to solve it?
*The differentiated approach, product, or solution.*

**Who** — Who is the customer? Describe the ICP specifically.
*Demographics, psychographics, job title, stage of business — whatever applies.*

**How** — How do we reach them and convert? What's the commercialization or go-to-market path?

After all five answers are confirmed, ask three quick inventory questions:

1. "What products or services exist today?" (Asset Inventory)
2. "What's the current status — revenue, active milestone, biggest open loop?"
3. "What are the 90-day goals?"

---

## Step 3B — Project Intake

First, confirm the parent venture (or standalone flag).

If under a venture: retrieve the parent's `knowledge_base` record to establish inherited context:
```sql
SELECT content FROM knowledge_base WHERE slug = 'context-[parent-venture-name]'
```
The project inherits Why, What 1, and Who from the parent — don't re-ask these.

Ask the three project questions:

**What are we trying to do?**
*The goal of this project in plain language. One or two sentences.*

**What's the strategy to execute?**
*Key moves, sequencing, how we're approaching it.*

**What does success look like?**
*Specific and measurable where possible. What's the done condition?*

Also capture:
- Project type (Content Campaign / Product Sprint / Marketing Launch / Partnership /
  Operational Buildout / Standalone)
- Target completion date
- Key dependencies

---

## Step 4 — Upsert into knowledge_base

Use the Supabase MCP `execute_sql` tool (project_id: tedpbnotgirjatlqkjxw) to upsert the
full context package. Build the `content` field using the template in
`references/templates.md`, filled with all answers from the intake.

```sql
INSERT INTO knowledge_base (slug, content, type, updated_at)
VALUES (
  '[entity-slug]',
  '[full context package markdown]',
  '[venture|client|manifest]',
  NOW()
)
ON CONFLICT (slug) DO UPDATE SET
  content = EXCLUDED.content,
  updated_at = NOW()
RETURNING slug, type, updated_at;
```

Slug and type conventions:
- Venture: `slug = 'context-[venture-name]'`, `type = 'venture'`
- Client: `slug = 'client-[client-name]'`, `type = 'client'`
- Project: `slug = 'project-[project-name]'`, `type = 'manifest'`

---

## Step 5 — Seed .agents/ Context File

After the knowledge_base record is created (Step 4), write a condensed context file to the
BenOS .agents/ directory. This is what downstream marketing skills (social-content,
email-sequence, copy-editing, paid-ads) read automatically.

File path: `.agents/[entity-name]-context.md`

Format:
```markdown
# [Entity Name] — Agent Context
Type: [Venture / Client / Project]
Last updated: [YYYY-MM-DD]

## Why
[1-2 sentences]

## What 1 — Problem
[1-2 sentences]

## What 2 — Solution
[1-2 sentences]

## Who
[ICP description, 2-3 sentences]

## How
[GTM approach, 2-3 sentences]

## Voice
[Known voice characteristics or "See Voice Guide — not yet completed"]

## Current Status
[1 sentence]

## 90-Day Goals
[Bullet list]
```

Keep this file concise — it's loaded into context on every skill run that references it.
Rich detail lives in the `knowledge_base` record (queryable via Supabase MCP).

---

## Step 6 — Output the Onboarding Summary

Conclude with a single-screen confirmation:

```
✅ [Entity Name] onboarded — [Date]

Type: [Venture / Client / Project]
knowledge_base slug: [entity-slug] (type: [venture|client|manifest])
.agents/ file: .agents/[entity-name]-context.md

Five questions captured: ✅
Brand / Voice / VoC stubs: ✅ (ready to complete)
Asset inventory: ✅

[For projects:]
Parent venture: [name]
Success criteria: [one sentence]

Gaps to close:
- [anything marked incomplete during intake]

BA note: [Venture] context package is ready. BA-[Venture] can be initialized.
```

---

## Routing Rules

- Venture data → `knowledge_base` slug `context-[name]`, type `venture` + .agents/ file
- Client data → `knowledge_base` slug `client-[name]`, type `client` + .agents/ file. NEVER to Linear.
- Project data → `knowledge_base` slug `project-[name]`, type `manifest`. Links to parent via content.
- Standalone project → same slug pattern, note "Parent: Standalone" in content header
- File-based deliverables for CC clients → iCloud /Bennovative Empire/Catalyzing Concepts/
  Client Deliverables/[Client Name]/ (create via bash if needed)

---

## Pre-Population Sources

| Venture | Source |
|---|---|
| SIPP | BEN.md — SIPP section |
| Who Is Coffee | BEN.md — WIC section |
| Catalyzing Concepts | BEN.md — CC section |
| Bennovative | BEN.md — Bennovative section |
| New ventures / clients | Fresh intake — no pre-population |

---

## What This Skill Does NOT Do

- Build the BA skill — it initializes the context the BA will read. BA skills are built separately.
- Create tasks — that's Task Manager. Context onboarding sets the foundation; task creation is next.
- Replace Strategy Builder — context onboarding captures what an entity is; Strategy Builder
  plans what to do about it.
- Run multiple entity intakes in one session — one entity per run. Clean slate each time.

---

## Success Criteria

Onboarding is complete when:
- Collection item exists with all five (or three) questions answered
- Item page populated with full context package
- .agents/ context file written
- Gaps identified and surfaced
- Summary output delivered

30-day evaluation date: 2026-06-13
