---
name: skill-importer
description: Import, assess, and adapt third-party or external skills into BenOS. Use this skill whenever the user says "import this skill", "onboard this skill", "fast-track this skill", "skill-importer", or drops a skill file/URL/pasted content and wants it integrated into BenOS. The skill runs a 5-step pipeline: ingest → COO assessment → adaptation → file generation → MANIFEST registration. Use it proactively when the user shares any external skill package (.skill file, SKILL.md, or pasted skill content) and wants it to work inside BenOS.
compatibility: Requires Supabase MCP (project_id: tedpbnotgirjatlqkjxw) for manifest and tool-registry reads. Requires filesystem access to write skill files at BenOS/skills/.
---

For full instructions, read skill-importer.md in this directory.
