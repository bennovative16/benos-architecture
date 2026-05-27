# Capture — Cowork Adapter

References: skills/capture/SKILL.md (read that file first for full scope)

## Scheduled Tasks

None. Capture is on-demand only. Ideas are captured when Ben has them — not on a schedule.

## On-Demand Invocation

Same trigger phrases as the Claude Code adapter. Capture works identically in Cowork and Claude Code. SKILL.md is the single source of logic.

## Cowork Specific Notes

- Ensure Supabase MCP is connected before invoking
- If Supabase MCP fails: hold the raw idea text visibly on screen and notify Ben before closing the session — do not lose the verbatim input
- Capture should feel instant in Cowork — no loading indicators or lengthy processing messages
- One confirmation line only — same as Claude Code
