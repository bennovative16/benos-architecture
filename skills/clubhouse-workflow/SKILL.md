---
name: clubhouse-workflow
description: >
  Development workflow manager for The Clubhouse fantasy golf app (BEN project in Linear).
  Trigger this skill whenever the user says a BEN issue or task is done, finished, complete,
  or asks "what's next" / "move on" / "next issue" during app development sessions.
  The skill marks the current Linear issue as Done, generates the exact git commit command,
  finds and queues the next highest-priority issue, moves it to In Progress, and produces
  a ready-to-paste Claude Code prompt for the next feature. Always use this skill proactively
  the moment a BEN issue completion is confirmed — don't wait for the user to ask.
---

Read `clubhouse-workflow.md` in this directory for the full skill instructions, scope, inputs, outputs, and integration details.
