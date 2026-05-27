# EA — Claude Code Adapter

References: skills/ea/SKILL.md (read that file first for full scope; body lives in `ea.md`).

## Trigger Phrases

Load and execute immediately on any of:
- "EA — standup"
- "morning standup"
- "what's on today"
- "what should I focus on"
- "EA — weekly plan"
- "plan the week"
- "EA — monthly plan"
- "EA — quarterly plan"
- "EA — reprioritize"
- "reprioritize today"
- "update today's priorities"
- "today we actually need to..."
- Any message that sounds like checking in on the day or planning the week

Trigger sensitivity: HIGH. If Ben opens a session with anything that sounds like "what am I working on today" or "help me plan this week" — this skill fires. Do not wait for the exact phrase.

## Invocation Pattern

```
EA — standup
EA — standup — [optional context, e.g. "content day but SIPP email needs to go out"]
EA — weekly plan — [optional priority guidance]
EA — reprioritize — [optional new priorities or trigger reason]
```

## Context to Load on Invocation (Mode 1)

Full read order defined in `ea.md` Mode 1 Step 1. In brief:
1. Supabase `knowledge_base` row where slug='ben' (BEN.md / North Star)
2. Quarter objectives — not yet in Supabase (graceful-degrade)
3. Weekly plan — not yet in Supabase (graceful-degrade)
4. Yesterday's brief: `SELECT * FROM public.briefs WHERE date = CURRENT_DATE - INTERVAL '1 day'`
5. COO Monday brief — not yet in Supabase (Mondays only; graceful-degrade)
6. BA briefs (knowledge_base Layer 1 + Layer 2) — see `ea.md` BA Brief Loading

## Output Destination

- Standup output → inline in chat
- Daily brief → `public.briefs` (upsert on `date` unique constraint)
- Mode 4 reprioritization → UPDATE today's brief row, appending a timestamped block

## Claude Code Specific Notes

- Use Supabase MCP `execute_sql` for all reads and writes
- If Supabase MCP unavailable: halt and notify Ben. Do not fabricate a brief from memory — the morning routine depends on real state, and a brief without source data is misleading.
- This skill fires at session start — no preamble, no "loading context" message. Output is the standup.
- Never ask Ben clarifying questions before producing the standup. Read, synthesize, output.
- Session memory: no state between sessions. All state lives in Supabase (project: `tedpbnotgirjatlqkjxw`, "Ben-OS").
- Mode 4 chains to Backlog Manager, which chains to Task Manager (UPDATE or CREATE per item). EA does not write directly to `public.tasks`.
