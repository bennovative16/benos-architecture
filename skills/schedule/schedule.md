# Schedule

**Skill:** `schedule`
**Status:** Live
**Last Updated:** 2026-05-08

---

## Purpose

Create a reusable shortcut from the current session — a scheduled task that can be run on demand or automatically on an interval. The skill distills the session's core repeatable objective into a self-contained prompt, names it, picks a schedule (recurring cron, one-time fireAt, or ad-hoc), and registers it with the `create_scheduled_task` tool.

## Triggers

- Any request to schedule a recurring task ("every morning", "weekdays at 5pm", "hourly")
- Any one-time scheduling request with a specific moment ("remind me in 5 minutes", "tomorrow at 3pm", "next Friday")
- Any request to create an ad-hoc shortcut from the current session that can be re-run later
- Any request to "save this as a recurring", "make this scheduled", or "turn this into a routine"

## Scope

**Handles:** session distillation into a self-contained future-runnable prompt, kebab-case taskName generation, scheduling-mode selection (cron / fireAt / ad-hoc), local-timezone cron expression authoring, ISO 8601 fireAt timestamps with offset, and the call to `create_scheduled_task`.

**Does NOT:**
- Reference "the current conversation" or any ephemeral context — future runs won't have it
- Use cron for one-time tasks (cron has no one-shot semantics)
- Proceed when scheduling intent is ambiguous — propose and confirm first

## Inputs

- The current session history (to identify the core repeatable objective)
- The user's stated cadence (if any)
- Local timezone (for cron and fireAt)

## Outputs

- A `create_scheduled_task` tool call with: a self-contained second-person imperative prompt; a kebab-case taskName; and one of `cronExpression` (recurring), `fireAt` ISO 8601 (one-time), or neither (ad-hoc / manual)

## Integration

**Reads from:** the session conversation
**Writes to:** the scheduled task system via `create_scheduled_task`
**Called by:** Ben directly when he wants to capture a session as a recurring or one-time task
**MCPs required:** none beyond the scheduled task tool

## Full Instructions

You are creating a reusable shortcut from the current session. Follow these steps:

## 1. Analyze the session

Review the session history to identify the core task the user performed or requested. Distill it into a single, repeatable objective.

## 2. Draft a prompt

The prompt will be used for future autonomous runs — it must be entirely self-contained. Future runs will NOT have access to this session, so never reference "the current conversation," "the above," or any ephemeral context.

Include in the description:
- A clear objective statement (what to accomplish)
- Specific steps to execute
- Any relevant file paths, URLs, repositories, or tool names
- Expected output or success criteria
- Any constraints or preferences the user expressed

Write the description in second-person imperative ("Check the inbox…", "Run the test suite…"). Keep it concise but complete enough that another Claude session could execute it cold.

## 3. Choose a taskName

Pick a short, descriptive name in kebab-case (e.g. "daily-inbox-summary", "weekly-dep-audit", "format-pr-description").

## 4. Determine scheduling

Pick one:
- **Recurring** ("every morning", "weekdays at 5pm", "hourly") → `cronExpression`
- **One-time with a specific moment** ("remind me in 5 minutes", "tomorrow at 3pm", "next Friday") → `fireAt` ISO timestamp
- **Ad-hoc** (no automatic run; user will trigger manually) → omit both
- **Ambiguous** → propose a schedule and ask the user to confirm before proceeding

**cronExpression:** Evaluated in the user's LOCAL timezone, not UTC. Use local times directly — e.g. "8am every Friday" → `0 8 * * 5`.

**fireAt:** Compute the exact moment and emit a full ISO 8601 string with timezone offset, e.g. `2026-03-05T14:30:00-08:00`. Never use cron for one-time tasks — cron has no one-shot semantics.

Finally, call the "create_scheduled_task" tool.
