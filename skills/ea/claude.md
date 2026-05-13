# EA — Claude Code Adapter

References: skills/ea/SKILL.md (read that file first for full scope)

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
- Any message that sounds like checking in on the day or planning the week

Trigger sensitivity: HIGH. If Ben opens a session with anything that sounds like "what am I working on today" or "help me plan this week" — this skill fires. Do not wait for the exact phrase.

## Invocation Pattern

```
EA — standup
EA — standup — [optional context, e.g. "content day but SIPP email needs to go out"]
EA — weekly plan — [optional priority guidance]
```

## Context to Load on Invocation

Full read order defined in SKILL.md Mode 1 Step 1. In brief:
1. BenOS / 00 — North Star / BEN.md
2. BenOS / 02 — Goals & KPIs / current-quarter-objectives
3. BenOS / 03 — Planning / [most recent weekly plan]
4. BenOS / 03 — Planning / Daily Logs / [yesterday's date]
5. COO Monday brief (Mondays only)
6. BA briefs — Option B loading (see SKILL.md)

## Output Destination

- Standup output → inline in chat
- Daily log → new Craft document at BenOS / 03 — Planning / Daily Logs / [YYYY-MM-DD]

## Claude Code Specific Notes

- Use Craft MCP for all reads and the daily log write
- If Craft MCP unavailable: produce standup from BEN.md knowledge only, name every gap explicitly, skip the daily log write and notify Ben
- This skill fires at session start — no preamble, no "loading context" message. Output is the standup.
- Never ask Ben clarifying questions before producing the standup. Read, synthesize, output.
- Session memory: no state between sessions. All state lives in Craft.
