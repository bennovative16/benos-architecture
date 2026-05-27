# Capture — Claude Code Adapter

References: skills/capture/SKILL.md (read that file first for full scope)

## Trigger Phrases

This skill must trigger on casual, natural input. Load and execute immediately on any of:
- "/capture [idea]"
- "Capture — [idea]"
- "Idea — [idea]"
- "Add to idea bank — [idea]"
- "Log this — [idea]"
- Any message that is clearly a raw idea being dropped into chat

Trigger sensitivity: HIGH. When in doubt, capture it. Missing an idea is worse than an occasional false positive.

## Invocation Pattern

```
Capture — [raw idea text]

Examples:
Capture — what if we did a Herk's Hits issue about
          the stoic concept of memento mori paired
          with a Johnny Cash track

Idea — SIPP could have a neighborhood water quality
       comparison feature so you can see how your
       water compares to your neighbors

/capture Who Is Coffee wholesale pitch deck needs
         a page specifically for boutique hotels
```

## Context to Load on Invocation

1. Supabase `knowledge_base` row where slug='ben' (North Star content)
2. Inline Content Pillars list (in SKILL body — no external read)
3. Inline Audiences list (in SKILL body — no external read)
4. Supabase `idea_bank` table (duplicate check via fuzzy ILIKE on title/raw_idea)

## Output Destination

New row → Supabase `public.idea_bank` (one INSERT via execute_sql per invocation)

## Claude Code Specific Notes

- Use Supabase MCP `execute_sql` to write to `idea_bank` and to query for duplicates
- If Supabase MCP unavailable: hold idea in chat, tell Ben "Supabase unavailable — idea held here. Run /capture again when reconnected." Do not lose the raw text.
- This skill fires mid-conversation without disrupting flow. Ben does not need to start a new session to capture.
- Confirmation line is the only output — do not add anything
- Session memory: no state between sessions. All state lives in `public.idea_bank`.
