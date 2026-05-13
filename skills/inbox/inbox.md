# Inbox

When work lands in chat, this skill catches it, structures it, and hands it off ready for execution. Ben shouldn't have to think about how to format a work item — that's the skill's job.

**The distinction that matters:**
Capture → raw ideas, observations, thoughts → Idea Bank
Inbox → work items, requests, tasks, deliverables → Backlog Manager

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

### Step 3 — Write the work brief

Use this template exactly:

```
WORK BRIEF
──────────────────────────────────────
Venture:        [venture name]
Type:           [work type]
Urgency:        [🔴/🟡/🟢 + label]
Effort:         [estimate]
Blocking:       [Yes / No]

Title:          [concise, action-oriented]

What:           [1-2 sentences — what needs doing]
Why:            [1 sentence — what this unlocks or protects]
Done When:      [clear completion signal — no vague phrases like "when it's ready"]
Dependencies:   [what needs to exist first, or "None"]
Next Step:      [the single first action to start moving]

Hashtags:       #[Venture] #[WorkType]
──────────────────────────────────────
Routing →       [destination]
```

"Done When" is non-negotiable. Work without a clear completion signal cannot be routed accurately.

The hashtag block is the venture tag that Task Manager uses to auto-tag all downstream tasks. Never omit it.

### Step 4 — Declare routing

| Work Type | Routes to |
|-----------|-----------|
| Task or Deliverable | Backlog Manager → Task Manager |
| Project | Backlog Manager |
| Strategic | Strategy Builder |
| Campaign | Strategy Builder → Campaign Designer |
| Onboarding | Onboarding skill |

State it at the bottom of the brief: `Routing → [destination]`

- **Standalone invocation**: output the brief and stop. Ben or a BA handles the next step.
- **Chained invocation** (called by a BA or another skill): pass the brief directly to the routed destination.

---

## Output

One work brief in chat. Routing declaration at the bottom. Nothing else — no commentary, no options, no follow-up questions.

The brief must be good enough to hand to any BA and have them start immediately without asking clarifying questions.

---

## BenOS Integration

Reads from:
- Venture context from calling BA or conversation
- BEN.md if venture context requires lookup

Writes to:
- Chat only (the brief)
- Downstream: Backlog Manager, Strategy Builder, or Onboarding will write to Craft/Linear

Called by: Ben directly, or any BA when work surfaces in their domain
Frequency: On-demand, multiple times daily
MCPs required: None (Craft MCP only if BA context lookup is needed)

---

## Valid venture hashtags
#SIPP | #WhoIsCoffee | #CatalyzingConcepts | #Bidsters | #Clubhouse | #Bennovative

## Valid type hashtags
#Deliverable | #Task | #Project | #Campaign | #Strategic | #Onboarding

---

## What this skill does NOT do

- Write to the Idea Bank (that's Capture)
- Create tasks in Linear or Craft (that's Task Manager)
- Prioritize work (that's Backlog Manager)
- Build execution plans (that's Strategy Builder)
- Ask more than one clarifying question per item
- Produce multiple options or alternatives
- Proceed if venture context is required but cannot be determined

---

## Success Criteria

≥90% of work briefs correctly classified and routed without manual correction by Ben.
30-day evaluation date: 2026-06-07
