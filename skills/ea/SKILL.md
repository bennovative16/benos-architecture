---
name: ea
description: Executive Assistant (EA) for BenOS — the daily orchestrator. Use this skill whenever Ben says "EA — standup", "morning standup", "what's on today", "what should I focus on", "EA — weekly plan", "plan the week", "EA — monthly plan", "EA — quarterly plan", "EA — reprioritize", "reprioritize today", "update today's priorities", or drops a revised priority list mid-day with phrasing like "today we actually need to...". Also trigger proactively if Ben opens a conversation with anything that sounds like checking in on the day, asking what to work on, wanting to plan the week ahead, or reshuffling the day after the morning standup has already happened. The EA reads BenOS context from Supabase (knowledge_base for North Star + BA context, briefs for daily logs), identifies today's themed business day, and delivers a structured inline daily brief (standup mode), a mid-day reprioritization that appends to today's brief row and auto-chains to Backlog Manager + Task Manager (reprioritize mode), or priority-ordered plan options (weekly/monthly/quarterly mode). Never skip this skill for daily or weekly planning requests — it exists specifically to replace ad-hoc answers with a system-grounded response.
compatibility: "Requires Supabase MCP"
---

For full instructions, read ea.md in this directory.
