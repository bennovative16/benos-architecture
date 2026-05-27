# EA — Cowork Adapter

References: skills/ea/SKILL.md (read that file first for full scope; body lives in `ea.md`).

## Scheduled Tasks

None currently. EA is on-demand. A future scheduled standup (e.g., auto-fire at 9:00am on weekdays) can be added via the schedule skill when ready.

## On-Demand Invocation

Same trigger phrases as the Claude Code adapter. EA works identically in Cowork and Claude Code. `ea.md` is the single source of logic.

## Cowork Specific Notes

- Ensure Supabase MCP is connected before invoking — EA is Supabase-dependent (project: `tedpbnotgirjatlqkjxw`, "Ben-OS")
- If Supabase MCP fails: halt and notify Ben. Do NOT produce a fabricated brief — the morning routine depends on real state, and a brief without source data is misleading.
- Standup output renders inline — no file creation needed for the brief itself
- Daily brief is written to `public.briefs` (one row per date, unique on `date` column — upsert pattern)
- BA brief loading queries `public.knowledge_base` (slugs: context-bennovative, context-sipp, context-wic, context-cc, ben)
- Trade-off surfacing rule: present Option A / Option B and stop. Do not resolve. Ben decides in the next message.
- Mode 4 (reprioritize) appends to today's brief row, does NOT create a new row. Always upserts on `date`.
