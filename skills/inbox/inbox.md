# Inbox

When work lands in chat, this skill catches it, structures it, and cascades it downstream automatically. Ben shouldn't have to think about how to format a work item or manually hand it off — that's the skill's job end-to-end.

**The distinction that matters:**
Capture → raw ideas, observations, thoughts → Idea Bank
Inbox → work items, requests, tasks, deliverables → downstream execution

If it's something to act on: Inbox. If it's a thought to revisit later: Capture.

---

## Venture Context

Establish this before anything else — it propagates to every downstream skill through the hashtag block.

1. **Called by a BA** (BA-SIPP, BA-WhoIsCoffee, etc.): use that BA's venture automatically
2. **Venture is clear from the message** (mentions SIPP, Who Is Coffee, Catalyzing Concepts, etc.): infer it
3. **Genuinely ambiguous**: ask one question — "Which venture is this for?" — list only the plausible 2-3 options. Wait, then proceed.

Never ask for venture if you can figure it out. Ben should not have to repeat context he already gave.

---

## Process

### Step 1 — Capture the raw input
Take Ben's words exactly. Don't rewrite them here. This is the source.

### Step 2 — Classify

**Work Type** — pick the one that best fits:
- **Deliverable**: a concrete output (document, email, design, video, one-pager)
- **Task**: a discrete action (update, fix, send, review, respond)
- **Project**: multi-step effort needing planning and multiple tasks
- **Campaign**: coordinated marketing or outreach push
- **Strategic**: requires thinking before tasks can be defined
- **Onboarding**: new venture or new Catalyzing Concepts client setup

**Urgency**:
- 🔴 Hot — deadline within 48 hours or blocking something else
- 🟡 This Week — needs to land before end of the current work week
- 🟢 Backlog — no hard deadline, queued for prioritization

**Effort**:
- Quick (under 1 hour)
- Half Day (1–4 hours)
- Full Day (4–8 hours)
- Multi-Day (8+ hours — this likely needs to be scoped as a project)

**Blocking?** Does this prevent other work from moving? Yes / No.

**Dependencies?** Does anything need to exist first? List them, or "None."

### Step 3 — Write the work brief

Use this template exactly:

```
WORK BRIEF                                    [CHAINED — skip confirmation checkpoints]
──────────────────────────────────────
Venture:        [venture name]
Type:           [work type]
Urgency:        [🔴/🟡/🟢 + label]
Effort:         [estimate]
Blocking:       [Yes / No]
Dependencies:   [what needs to exist first, or "None"]

Title:          [concise, action-oriented]

What:           [1-2 sentences — what needs doing]
Why:            [1 sentence — what this unlocks or protects]
Done When:      [clear completion signal — no vague phrases like "when it's ready"]
Next Step:      [the single first action to start moving]

Hashtags:       #[Venture] #[WorkType]
──────────────────────────────────────
Routing →       [destination]
```

The `[CHAINED — skip confirmation checkpoints]` header tells every downstream skill to run straight through without stopping for confirmation. Always include it.

"Done When" is non-negotiable. Work without a clear completion signal cannot be routed accurately.

The hashtag block is the venture tag that Task Manager uses to auto-tag all downstream tasks. Never omit it.

### Step 4 — Route the work

Read the completed brief and apply the classifier before declaring routing. The classifier runs automatically — do not ask Ben which path to take.

**Short path — direct to Task Manager** (all four must be true):
- Type is Task or Deliverable
- Effort is Quick or Half Day
- Blocking is No
- Dependencies is None

**Long path — through Backlog Manager or Strategy Builder** (any one of these triggers it):
- Type is Project, Strategic, Campaign, or Onboarding
- Effort is Full Day or Multi-Day
- Blocking is Yes
- Dependencies exist

| Condition | Routes to |
|-----------|-----------|
| Task/Deliverable — Quick or Half Day, not blocking, no dependencies | → Task Manager → Tasks collection |
| Task/Deliverable — Full Day or Multi-Day, OR blocking, OR has dependencies | → Backlog Manager → Task Manager |
| Project | → Backlog Manager |
| Strategic | → Strategy Builder |
| Campaign | → Strategy Builder → Campaign Designer |
| Onboarding | → Onboarding skill |

State the result at the bottom of the brief: `Routing → [destination]`

### Step 5 — Execute (cascade downstream)

After producing the work brief, immediately read and execute the downstream skill in this same session. Do not stop. Do not ask Ben for confirmation. The `[CHAINED]` flag in the brief tells downstream skills to do the same — run straight through.

| Routing declared | What to do now |
|-----------------|----------------|
| → Task Manager | Read task-manager.md. Create the task immediately. Infer due date from urgency if not explicitly provided: Hot = tomorrow, This Week = next Friday, Backlog = 14 days from today. Confirm creation with one line. |
| → Backlog Manager → Task Manager | Read backlog-manager.md. Score and sequence the item(s). Pass immediately to Task Manager. Task Manager creates tasks. Confirm each. |
| → Strategy Builder | Read strategy-builder.md. Build the plan and handoff block. Pass handoff immediately to Backlog Manager. Backlog Manager passes to Task Manager. |
| → Strategy Builder → Campaign Designer | Read strategy-builder.md. Build plan. Flag campaign trigger. Pass handoff to Backlog Manager. |
| → Onboarding skill | Read context-onboarding.md. Begin onboarding sequence. |

**The only exception:** if Ben explicitly says "just show me the brief" or "don't process yet," stop after the brief. Default is always to cascade.

---

## BenOS Integration

Reads from:
- Venture context from calling BA or conversation
- BEN.md if venture context requires lookup
- Downstream skill .md files (executed inline after routing)

Writes to:
- Chat (the brief)
- Supabase tasks table (via Task Manager, short path)
- Supabase tasks table (via Backlog Manager, long path)

Called by: Ben directly, or any BA when work surfaces in their domain
Frequency: On-demand, multiple times daily
MCPs required: Supabase MCP | Linear MCP (if task routes to dev work)

---

## Valid venture hashtags
#SIPP | #WhoIsCoffee | #CatalyzingConcepts | #Bidsters | #Clubhouse | #Bennovative

## Valid type hashtags
#Deliverable | #Task | #Project | #Campaign | #Strategic | #Onboarding

---

## What this skill does NOT do

- Write to the Idea Bank (that's Capture)
- Stop at producing a brief — it always cascades unless Ben explicitly says otherwise
- Ask more than one clarifying question per item
- Produce multiple options or alternatives
- Proceed if venture context is required but cannot be determined
- Decide routing based on gut feel — the classifier rules above are the authority

---

## Success Criteria

≥90% of work briefs correctly classified, routed, and executed without manual correction by Ben.
Cascade execution rate: 100% (brief always followed by downstream action).
30-day evaluation date: 2026-06-07

---

## HANDOFF

**Receives from:** Ben directly (natural language — voice, text, or dump)
**Input:** raw input of any type — idea, task, project, campaign, strategic question, deliverable, or onboarding item
**Produces:** classified work brief per item (type + venture + title + body + done-when)
**Passes to:** BA skill (venture ops) | Strategy Builder (Strategic/Campaign) | Task Manager (Deliverable/Task) | context-onboarding (Onboarding) — always cascades without stopping
**Completion log:** Work briefs written to Supabase `public.tasks` (via Task Manager) or dispatched to downstream skill.
