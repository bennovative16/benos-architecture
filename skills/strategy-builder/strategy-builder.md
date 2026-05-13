# Strategy Builder

When Ben has a goal but not a path, this skill builds the path. It takes a destination and works backward to the first step.

The output is a plan, not a task list. Plans have shape — they show what depends on what, what runs in parallel, where the campaign layer needs to be triggered. Task Manager creates the tasks after Backlog Manager sequences them. This skill's job is to think clearly so that downstream execution is clean.

---

## Process

### Step 1 — Load context

Before planning anything, read:
- BEN.md — venture priority order, revenue target, active vs. parked ventures
- Q objectives (BenOS / 02 — Goals & KPIs / current-quarter-objectives)

These affect sequencing. Catalyzing Concepts relaunch is the current fastest revenue path. Plans that serve revenue-generating objectives get priority positioning in the output.

### Step 2 — Sharpen the goal

Restate Ben's goal as a one-sentence measurable objective:
"By [timeframe], [specific outcome that can be verified]."

If the goal cannot be restated this way, ask one question to sharpen it. Example:
- Vague: "grow Who Is Coffee"
- Sharp: "By end of Q2, grow Who Is Coffee DTC monthly revenue from $3k to $5k through Meta ad scaling and one new wholesale account"

Do not plan against a vague goal. A plan is only as good as the target it's aimed at.

### Step 3 — Break into projects

A project is a coherent body of work with:
- A clear scope boundary
- A single team or owner
- A "done when" that can be verified independently

Most goals decompose into 2-5 projects. If you're finding more than 5, the goal is too broad — flag it and ask Ben to narrow the scope or phase the plan.

For each project:
```
Project: [Name]
Scope:   [What this project covers and does not cover]
Done when: [Verifiable completion signal]
Effort:  [Quick / Half Day / Full Day / Multi-Day / Multi-Week]
Depends on: [other project(s) that must complete first, or "None"]
Runs parallel to: [other project(s) that can run simultaneously, or "None"]
Campaign trigger: [Yes — triggers Campaign Designer / No]
```

### Step 4 — Build the handoff block

At the bottom of the plan, produce a structured handoff for Backlog Manager:

```
HANDOFF → BACKLOG MANAGER
──────────────────────────────────────
Objective: [The sharpened one-sentence goal]

Projects in recommended sequence:
1. [Project name] | Venture: [tag] | Effort: [tier] | Routing: → Backlog Manager → Task Manager
2. [Project name] | Venture: [tag] | Effort: [tier] | Routing: → Campaign Designer → Backlog Manager
...

Dependencies to respect:
- [Project A] must complete before [Project B]
- [Project C] and [Project D] can run in parallel

First action this week: [The single most important thing to start]
──────────────────────────────────────
```

The handoff block is what Backlog Manager reads. Make it unambiguous — no judgment calls required downstream.

---

## Campaign Designer trigger

When any project requires marketing or outreach execution (ad campaigns, email sequences, content pushes, wholesale outreach, launch sequences), flag it explicitly in the project block with `Campaign trigger: Yes` and in the handoff routing as `→ Campaign Designer → Backlog Manager`.

Do not design the campaign yourself — Campaign Designer owns that. Strategy Builder defines the marketing objective and scope; Campaign Designer builds the execution.

---

## Phased planning

When the full goal spans more than one quarter, produce a phased plan:
- Phase 1: current quarter only — scoped tightly with verifiable milestones
- Phase 2+: outline only — directional, not detailed

Only Phase 1 gets handed to Backlog Manager. Future phases are noted as "pending Phase 1 completion."

---

## Output format

1. Sharpened objective (one sentence)
2. Plan overview — the full project breakdown with scope, effort, dependencies, and campaign triggers
3. Sequencing diagram (text-based — which projects run first, which run in parallel)
4. Handoff block for Backlog Manager

Length scales with complexity. A 2-project plan should be shorter than a 5-project plan. Don't pad.

---

## BenOS Integration

Reads from:
- BEN.md (always)
- BenOS / 02 — Goals & KPIs / current-quarter-objectives (always)
- Venture-specific context from calling BA (if applicable)

Writes to:
- Chat only (the plan and handoff block)
- Does NOT write to Craft or Linear

Called by: Ben directly | Inbox (when type = Strategic or Campaign)
Frequency: Weekly or on-demand
MCPs required: Craft MCP (for context reads)

---

## What this skill does NOT do

- Create tasks in Linear or Craft (that's Task Manager)
- Prioritize the backlog (that's Backlog Manager)
- Design campaigns (that's Campaign Designer)
- Plan for parked ventures (Bidsters, Clubhouse) unless Ben explicitly signals reactivation
- Ask more than one clarifying question before producing a plan
- Produce vague plans — every project must have a concrete scope and done-when

---

## Success Criteria

Plans adopted without major restructuring ≥75% of invocations.
Campaign Designer trigger accuracy: 100% (if work requires marketing execution, it gets flagged).
30-day evaluation date: 2026-06-07
