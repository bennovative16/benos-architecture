# Capture

Zero-friction idea capture for BenOS.
Ben types an idea naturally. This skill does all the work.
One confirmation line. Nothing else.

**Read first:** Supabase `knowledge_base` row where `slug = 'ben'` (BEN.md / North Star content)
**Read second:** Inline Content Pillars list (below) — no external read needed
**Read third:** Inline Audiences list (below) — no external read needed
**Read fourth:** Supabase `idea_bank` table (duplicate check)

If `knowledge_base` row for `'ben'` is empty or thin, proceed using only the user's stated venture priorities. Do not block.

---

## Input

Raw idea text typed by Ben in chat.
Format: freeform — one line, paragraph, or voice transcript.
No structure required. No command format required.
Ben should never have to think about how to format an idea.

---

## Process

### Step 1 — Capture Raw Text

Preserve the exact verbatim input. This becomes the `raw_idea` field.
Never modify it. Never summarize it here. Save it exactly as typed.

### Step 2 — Duplicate Check

Query the idea_bank table for similar existing entries:

```sql
SELECT id, title, captured_date, status
FROM public.idea_bank
WHERE business_unit = '<inferred venture, if obvious>'
  AND status IN ('Fresh', 'Active')
  AND (
    title ILIKE '%' || '<key terms from raw_idea>' || '%'
    OR raw_idea ILIKE '%' || '<key terms>' || '%'
    OR polished_summary ILIKE '%' || '<key terms>' || '%'
  )
ORDER BY captured_date DESC
LIMIT 3;
```

If a strong match exists (same core idea, same business unit):
→ Surface: `"This looks similar to [existing title] captured on [date]. Merge or keep separate?"`
→ Wait for one-word response. Then proceed.

If no match: proceed silently.

### Step 3 — Classify

**Business Unit (maps to `business_unit` column):**

| Slug | Triggers |
|---|---|
| `sipp` | water quality, hardware, smart home, environment, sensors |
| `wic` | coffee, DTC, wholesale, farmers, conservation |
| `cc` | commercialization, R&D, grants, SBIR/STTR, consulting, TABA |
| `bidsters` | construction, preconstruction, CRM, contractors |
| `clubhouse` | fantasy golf, sports, gaming |
| `bennovative` | personal brand, stoicism, content, doing hard things |
| `cross-venture` | serves multiple units equally |

If genuinely ambiguous: ask ONE question.
`"Which business is this for — [option A] or [option B]?"`
Never ask more. Never ask about anything else.
Write immediately on response.

**Content Pillar (maps to `content_pillar` column):**

- Doing Hard Things
- Stoicism Applied
- Water & Conservation
- Builder Community
- Coffee & Ritual
- Tech & Society

If idea does not map cleanly to a pillar: leave NULL.

**Type (maps to `type` column — must be one of):**

- `Content` — blog post, video, newsletter, social
- `Product` — feature, hardware, software, new product
- `Strategic` — business model, partnership, positioning
- `Campaign` — multi-piece coordinated marketing effort

**Priority (maps to `priority` integer, 1–5):**

- 5: Directly serves current Q objective, high urgency
- 4: Serves current Q objective, not urgent
- 3: Serves a business goal, not current Q priority
- 2: Good idea, no clear home right now
- 1: Speculative, long horizon

### Step 4 — Enrich

**Polished Summary (maps to `polished_summary`):**
Restate the idea cleanly in one paragraph.
Remove filler, clarify intent, make it readable six months from now.
This is the skill's interpretation — Ben edits it freely after.

**Implementation Ideas (maps to `implementation_ideas` jsonb array):**
Generate 2–3 concrete execution paths. Specific. Not commitments — possibilities.

Examples of good implementation ideas:
- "Write a Herk's Hits issue pairing this track with the concept"
- "Build as a Linear feature ticket for the next SIPP sprint"
- "Draft a cold email sequence targeting this specific audience"

Store as: `'["idea 1", "idea 2", "idea 3"]'::jsonb`

### Step 5 — Write to idea_bank

Generate an ID using format `idea-XXXXXXXX` (8 hex chars, lowercase). Then execute via Supabase MCP `execute_sql`:

```sql
INSERT INTO public.idea_bank (
  id, title, raw_idea, polished_summary, implementation_ideas,
  business_unit, content_pillar, type, priority, status,
  captured_date, notes
) VALUES (
  'idea-<8 hex chars>',
  '<Title — concise, specific, derived from idea>',
  '<Raw idea — verbatim, never modified>',
  '<Polished summary>',
  '<implementation_ideas as jsonb array>'::jsonb,
  '<business unit slug>',
  '<Content Pillar | NULL>',
  '<Content | Product | Strategic | Campaign>',
  <priority integer 1-5>,
  'Fresh',
  CURRENT_DATE,
  '<any additional context worth preserving, or NULL>'
);
```

### Step 6 — Confirm

Output exactly one line to Ben:
`Captured → [Business Unit] / [Type] / [Pillar | "—"] → Idea Bank (idea-xxxxxxxx)`

Nothing else. No summary. No options. No follow-up questions. The work is done. Ben moves on.

---

## Output

One confirmation line in chat.
One new row in `public.idea_bank`.

---

## BenOS Integration

Reads from:
- Supabase `knowledge_base` where slug='ben' (North Star context)
- Supabase `idea_bank` (duplicate check)
- Inline content pillars and audience lists (no external read)

Writes to:
- Supabase `public.idea_bank` (one new row per invocation)

Called by: Ben directly
Frequency: On-demand, multiple times daily
MCPs required: Supabase MCP

---

## Output Format Rules

No options. No first-pass alternatives.
This skill has one output format always.
Fast, silent, invisible enrichment.
One confirmation line. Done.

---

## Success Criteria

≥90% of captured ideas appear in `idea_bank` with correct business_unit and type without manual correction by Ben.
30-day evaluation date: 2026-06-22

---

## What This Skill Does NOT Do

- Ask more than one clarifying question per capture
- Modify the `raw_idea` field after writing
- Present options or alternatives
- Produce lengthy output
- Create multiple rows for one idea
- Overwrite existing rows
- Proceed if Supabase MCP is unavailable
  (hold in chat, notify Ben instead)
