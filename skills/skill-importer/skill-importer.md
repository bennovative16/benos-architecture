# Skill Importer

Takes an external or downloaded skill and fast-tracks it into BenOS. Runs a 5-step intake pipeline: ingest → assess → adapt → generate files → register.

The goal is zero-friction integration: an external skill should work inside BenOS in one pass, with MCP mismatches corrected, Craft references removed, and routing rules injected — without Ben having to manually hunt through the file.

**Triggers:** "skill-importer", "import this skill", "onboard this skill", "fast-track this skill", or any time a .skill file, pasted skill content, or skill URL is provided with the intent to integrate it.

---

## BenOS Two-File Protocol

Every BenOS skill MUST be two files in the same directory:

- **`[skill-name].md`** — Full skill specification: all instructions, all logic, all output formats. This is the human-readable and agent-readable source of truth.
- **`SKILL.md`** — YAML frontmatter only (`name` + `description` + optional `compatibility`), followed by one line: `"For full instructions, read [skill-name].md in this directory."` Stays light so the triggering description loads fast.

A skill that stuffs the full body into SKILL.md is non-compliant. A skill with only one file is non-compliant. Both files must exist before a skill is considered imported.

Skills live at: `BenOS/skills/[skill-name]/`

---

## 5-Step Import Pipeline

### Step 1 — Ingest

Accept the source skill in any form:
- **File path** — Read the file directly
- **Pasted content** — Use what's in the conversation
- **URL** — Fetch if accessible; ask Ben to paste if not

Read the full content. Identify:
- Skill name (from frontmatter or file name)
- What it does (summarize in one sentence)
- MCPs it calls (grep for any `mcp__*` prefixes or named tool calls)
- Any Craft MCP calls (`craft_read`, `markdown_add`, `collectionItems_*`)
- Any hardcoded IDs, session tokens, or environment-specific paths

State your findings before proceeding. Format:
```
Name: [skill-name]
Does: [one sentence]
MCPs called: [list or "none"]
Craft calls: [list or "none found"]
Hardcoded values: [list or "none"]
```

---

### Step 2 — COO Assessment

Before touching anything, check two sources via Supabase MCP (project_id: tedpbnotgirjatlqkjxw):

**Duplicate check:**
```sql
SELECT content FROM knowledge_base WHERE slug = 'manifest'
```
Scan the manifest for a skill with the same name or overlapping purpose. If a duplicate exists, surface it: "BenOS already has `[existing-skill]` which does [X]. This import would [conflict / complement] it." Let Ben decide.

**MCP compatibility check:**
```sql
SELECT content FROM knowledge_base WHERE slug = 'tool-registry'
```
Cross-reference every MCP the incoming skill calls against tool-registry. Flag any tool that is:
- Not listed in tool-registry (unknown MCP — needs research before import)
- Listed but "Not connected" (import can proceed, but those steps must be skipped or noted)
- Listed under a different venture's account (wrong connection — flag which account the skill assumes)

**Verdict:** Output one of:
- `ADOPT AS-IS` — skill uses only known, connected MCPs and has no Craft calls
- `ADAPT WITH CHANGES` — [list specific changes needed]
- `SKIP` — [reason: duplicate / unknown MCP / fundamentally incompatible]

Do not proceed past this step without stating the verdict.

---

### Step 3 — Adaptation

Only runs if verdict is `ADOPT AS-IS` or `ADAPT WITH CHANGES`.

Make these changes in order:

**3A — Remove Craft calls:**
Any call to `craft_read`, `markdown_add`, `collectionItems_get`, `collectionItems_add`, or any `mcp__8b5d1d20-*` tool must be replaced:
- Context reads → `SELECT content FROM knowledge_base WHERE slug = '[slug]'` via Supabase MCP
- Content writes → `INSERT INTO knowledge_base ... ON CONFLICT DO UPDATE` or `INSERT INTO tasks ...` depending on what's being stored
- If the Craft call's purpose is unclear, add a comment: `[CRAFT CALL REMOVED — purpose unclear, verify before use]`

**3B — Fix MCP prefixes:**
If the skill references MCPs by name (e.g., "use the Supabase MCP") but uses wrong or stale tool prefixes, replace with the BenOS-standard prefix from tool-registry.

**3C — Inject BenOS routing rules:**
If the skill routes work items (tasks, briefs, content), add this rule where relevant:
- Dev / UI design work → Linear
- Everything else (ops, content, strategy, marketing) → Supabase tasks table

**3D — Strip hardcoded IDs:**
Remove any session IDs, user-specific doc IDs, or environment tokens that don't translate to BenOS. Replace with the BenOS equivalent (e.g., Supabase project_id: `tedpbnotgirjatlqkjxw`) or a clear placeholder.

**3E — Standardize SKILL.md:**
Ensure the SKILL.md will contain only frontmatter + one-line reference. Move any body content to `[skill-name].md`.

State what you changed before writing files.

---

### Step 4 — File Generation

Write two files to the BenOS skills directory.

**Directory:**
```
BenOS/skills/[skill-name]/
```

Use `mkdir -p` if the directory doesn't exist.

**SKILL.md** (frontmatter + one-line reference only):
```markdown
---
name: [skill-name]
description: [description from original, or rewritten to be accurate + trigger-clear]
compatibility: [MCPs required, or omit if none]
---

For full instructions, read [skill-name].md in this directory.
```

**[skill-name].md** (full skill body):
The adapted skill content from Step 3. Must include:
- Skill name as H1
- What it does and when to use it
- The full instruction set
- Any output formats, examples, or reference file pointers

Confirm both files are written before moving to Step 5.

---

### Step 5 — Registration

Update the MANIFEST in Supabase to record the new skill.

Read the current manifest:
```sql
SELECT content FROM knowledge_base WHERE slug = 'manifest'
```

Identify the correct category for the skill (ORCHESTRATION, BUSINESS ASSISTANTS, CONTENT & MARKETING, SALES & BUSINESS DEVELOPMENT, PRODUCT & STRATEGY, DESIGN & FRONTEND, OPERATIONS & SYSTEM, DOCUMENT GENERATION, UTILITY).

Append a row to the correct table in the manifest content:
```
| `[skill-name]` | [one-line purpose] | Active |
```

Write the updated manifest back:
```sql
UPDATE knowledge_base
SET content = '[updated content]', updated_at = NOW()
WHERE slug = 'manifest'
```

**If new MCPs are required** that aren't in tool-registry: do NOT auto-write tool-registry. Flag it explicitly:
```
NEW MCP NEEDED: [mcp-name] — [what it does] — add to tool-registry manually before using this skill
```

---

## What This Skill Does NOT Do

- Auto-approve a skill that conflicts with an existing one — always surfaces the conflict to Ben
- Auto-write to tool-registry — new MCPs get flagged, not silently registered
- Guess at Craft call intent — marks ambiguous replacements with a comment
- Import skills with `SKIP` verdict without Ben's explicit override

---

## Success Criteria

Both files written and non-empty.
MANIFEST updated with the new skill entry.
Zero Craft references in the output files.
All MCP calls either resolved to BenOS equivalents or flagged.
