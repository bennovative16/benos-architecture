---
name: backlog-manager
description: "Backlog prioritization skill for BenOS. Use this skill whenever work items need to be ordered before task creation/update, or when Ben or the EA wants to know what to work on next. Triggers on: 'Backlog Manager —', 'prioritize the backlog', 'what should we work on next', 'sequence these items', 'order this work', 'what is the priority', or whenever Inbox, Strategy Builder, or EA produces a work list that needs sequencing. Also triggered by EA during Monday planning to load the week and by EA Mode 4 (mid-day reprioritization). Reads BEN.md from Supabase knowledge_base (slug='ben') and queries Supabase idea_bank for Fresh items aging >7 days before handing off to Task Manager. Does NOT create or update tasks — produces an ordered list and routes to Task Manager (CREATE for new items, UPDATE for items with existing task IDs)."
---

For full instructions, read backlog-manager.md in this directory.
