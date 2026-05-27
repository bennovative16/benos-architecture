---
name: capture
description: Zero-friction idea capture skill for BenOS. Use this skill whenever Ben types an idea, observation, or raw thought that should be saved. Triggers on: "Idea —", "Capture —", "Add to idea bank", "/capture", or any message that is clearly a raw idea being dropped into chat. Fire immediately and silently — do not ask for clarification unless business unit is genuinely ambiguous. Writes a new row to the Supabase `idea_bank` table with full classification and enrichment (raw_idea, polished_summary, implementation_ideas, business_unit, content_pillar, type, priority 1-5, status='Fresh'). Confirmation is one line only.
---

For full instructions, read capture.md in this directory.
