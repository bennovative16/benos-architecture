# EA — Cowork Adapter

References: skills/ea/SKILL.md (read that file first for full scope)

## Scheduled Tasks

None currently. EA is on-demand. A future scheduled standup (e.g., auto-fire at 9:00am on weekdays) can be added via the schedule skill when ready.

## On-Demand Invocation

Same trigger phrases as the Claude Code adapter. EA works identically in Cowork and Claude Code. SKILL.md is the single source of logic.

## Cowork Specific Notes

- Ensure Craft MCP is connected before invoking — EA is Craft-dependent
- If Craft MCP fails: produce standup from BEN.md knowledge only, name all gaps, skip daily log write, notify Ben
- Standup output renders inline — no file creation needed for the brief itself
- Daily log is written to Craft, not to iCloud
- Option B BA loading applies in Cowork exactly as in Claude Code — no difference in behavior
- Trade-off surfacing rule: present Option A / Option B and stop. Do not resolve. Ben decides in the next message.
