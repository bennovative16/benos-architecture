---
name: task-manager
description: "Task creation, update, and resolve skill for BenOS. Three modes: CREATE (turn a work brief into a new task row), UPDATE (change an existing task's due_date / priority / status), RESOLVE (match a free-text priority title to existing task IDs). Triggers on: 'create a task for', 'log this as a task', 'add to Linear', 'task this out', 'update task', 'reschedule task', 'reprioritize task', '[UPDATE]', '[RESOLVE]', or any request to track or modify work. Also triggered automatically by Backlog Manager (CREATE), EA Mode 4 (UPDATE + RESOLVE), Inbox (chained), and any BA. Routes to Linear for dev/UI design work, Supabase public.tasks for everything else. CREATE mode always sets a due date — refuses to create without one. Always applies a venture. If called by a BA or from a work brief, venture context is already known — never ask Ben for it again."
---

For full instructions, read task-manager.md in this directory.
