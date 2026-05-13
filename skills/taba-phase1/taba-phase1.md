# TABA Phase I Proposal Package Generator

**Skill:** `taba-phase1`
**Status:** Live
**Last Updated:** 2026-05-08

---

## Purpose

Generate a complete NASA TABA Phase I proposal package for a new Catalyzing Concepts client. Phase I engagements are $6,500, ~6 months, strategy-only — no infrastructure buildout, no outreach execution. The output feeds directly into the client's Phase II proposal; the Commercialization Plan is the anchor deliverable. Use the `taba-proposal` skill instead for Phase II ($50k) engagements.

## Triggers

- "Phase I TABA"
- "new Phase I client"
- "make a Phase I proposal"
- "build a Phase I package"
- Mention of an SBIR/STTR Phase I awardee that needs commercialization support to strengthen their Phase II application

## Scope

**Handles:** 3-round client intake, customizing the three template scripts in `scripts/` (`build-proposal.js`, `build-budget.py`, `build-letters.js`) only at the `// ── CLIENT CONFIG ──` block, running them, validating the outputs (XML validity, paragraph/table counts, budget math), and copying to the Catalyzing Concepts workspace under the standard `[CLIENT_ABBREV]_TABA_P1_*` filenames. Phase I framing language casts the engagement as building the strategic foundation for Phase II.

**Does NOT:**
- Build infrastructure (Phase II only)
- Build content/outreach scenarios (Phase II only)
- Use three ICPs — Phase I targets one primary market segment
- Edit anything outside the CLIENT CONFIG block in the template scripts

## Inputs

### Round 1 (Required)
- Client company name (full + abbreviation)
- Primary contact (name, title)
- Address
- Technology description (one sentence)
- IP status: pre-patent | provisional filed | utility filed | patent issued | trade secret
- Target market — primary buyer / application area

### Round 2 (Scope)
- NASA proposal number (or `[INSERT PROPOSAL NUMBER]`)
- Agency (NASA default; note if DOE / NSF / DoD)
- WP budget split (default WP1 $3,000 / WP2 $3,500)

### Round 3 (Content)
- Primary ICP (single segment + brief description)
- Key Phase II ambition (frames the Commercialization Plan)

If user says "just get started" → use approximations and tag `[PLACEHOLDER]`.

## Outputs

Three files generated and copied to `/sessions/.../mnt/Catalyzing Concepts/`:
1. **`[CLIENT_ABBREV]_TABA_P1_Proposal.docx`** — branded client proposal with methodology, 2 Work Packages (Strategy + Commercialization Plan), budget, 6-month sprint timeline
2. **`[CLIENT_ABBREV]_TABA_P1_Budget.xlsx`** — single tab with live formulas summing to $6,500
3. **`[CLIENT_ABBREV]_TABA_P1_Letters.docx`** — NASA TABA Vendor Quote (LOC) + Acknowledgement Letter

Validation expectations:
- Proposal: XML VALID, 180+ paragraphs, 18+ tables
- Letters: XML VALID, 100+ paragraphs, 5+ tables
- Budget: WP1 + WP2 = $6,500; line items sum to WP totals

## Integration

**Reads from:** template scripts under `scripts/`, optional engine diagram, dynamically resolved Logo Files directory
**Writes to:** `/sessions/.../mnt/outputs/` (build outputs) and `/sessions/.../mnt/Catalyzing Concepts/` (final delivery names)
**Called by:** Ben directly when starting a new Phase I client engagement
**MCPs required:** none — uses Node (`docx`) and Python (`openpyxl`) toolchains

## Full Instructions

# TABA Phase I Proposal Package Generator

Builds the complete 3-document TABA Phase I proposal package for a Catalyzing Concepts client:
1. **Client-Facing Proposal** (.docx) — Branded proposal with methodology, 2 Work Packages, budget
2. **TABA Budget Spreadsheet** (.xlsx) — Single tab with live formulas
3. **Letters Document** (.docx) — NASA TABA Vendor Quote (LOC) + Acknowledgement Letter

**Phase I vs. Phase II key differences:**
- Budget: $6,500 (vs. $50,000 Phase II)
- Timeline: ~6 months (vs. 12–18 months)
- Work Packages: 2 (Strategy + Commercialization Plan) — no infrastructure, content, or outreach WPs
- ICP: One primary market segment (vs. three) — Phase I is typically in response to a specific grant opportunity
- No infrastructure scenarios (Scenario A/B) — no buildout in Phase I
- Purpose: The output feeds directly into the client's Phase II proposal; the Commercialization Plan is the anchor deliverable

---

## Step 1 — Client Intake

### Round 1 (Required)
- **Client company name** (full + abbreviation)
- **Primary contact** (name, title)
- **Address**
- **Technology description** — one sentence: what they built, problem it solves, what makes it differentiated
- **IP status**: pre-patent | provisional filed | utility filed | patent issued | trade secret
- **Target market** — who is the primary buyer / application area this Phase I is aimed at?

### Round 2 (Scope)
- **NASA proposal number**: if available; otherwise `[INSERT PROPOSAL NUMBER]`
- **Agency**: NASA (default). Note if DOE, NSF, DoD
- **WP budget split**: Standard is WP1 $3,000 / WP2 $3,500. Ask if client wants different split.

### Round 3 (Content)
- **Primary ICP**: Who is the single most important buyer type for this technology? (name + brief description)
- **Key Phase II ambition**: What does success look like after Phase II? (informs commercialization plan framing)

> **If the user says "just get started"**, use reasonable approximations and flag `[PLACEHOLDER]` tags.

---

## Step 2 — Set Up the Build Environment

```bash
node -e "require('docx'); console.log('docx OK')" 2>/dev/null || npm install docx
python3 -c "import openpyxl; print('openpyxl OK')" 2>/dev/null || pip install openpyxl --break-system-packages

# Check for engine diagram (optional)
ls "/sessions/epic-intelligent-knuth/mnt/Catalyzing Concepts/CatCon_CommercializationEngine.png" && echo "Diagram found"
```

---

## Step 3 — Customize and Run the Template Scripts

Read the three template scripts from this skill's `scripts/` directory:
- `scripts/build-proposal.js`
- `scripts/build-budget.py`
- `scripts/build-letters.js`

Each has a `// ── CLIENT CONFIG ──` block at the top. **Only edit that block.**

### CONFIG fields to fill in

```javascript
const CLIENT = {
  companyFull:    "Full Company Name, Inc.",
  companyShort:   "ABC",
  contactName:    "Jane Smith",
  contactTitle:   "Principal Investigator",
  address:        "123 Main St, Cambridge, MA 02139",
  proposalNum:    "[INSERT PROPOSAL NUMBER]",
  techFocus:      "One-sentence technology focus for cover page",
  ipStatus:       "provisional patent filed",

  // Budget — must sum to totalBudget
  totalBudget:    6500,
  wp1Total:       "$3,000",
  wp2Total:       "$3,500",

  // Single ICP — Phase I targets the primary market segment
  icpName:   "Primary Market Segment\n[e.g., NASA & Government]",
  icpWho:    "Who they are...",
  icpMsg:    "What they need to hear...",

  // Executive summary
  execPara1: "[Company] has developed [technology]. With [IP status] and a NASA SBIR Phase I award, [company] is positioned to [opportunity].",
  execPara2: "The path from a promising Phase I result to a competitive Phase II application runs through a well-structured commercialization plan. [Company] needs a documented strategy that defines the market opportunity, articulates the value proposition for the primary buyer segment, and positions the technology for Phase II success.",

  // Work package deliverables — [name, description, cost]
  wp1Deliverables: [
    ["Five Questions Synthesis",              "...", "$1,500"],
    ["ICP Development — Primary Market Segment", "...", "$1,000"],
    ["Voice of Customer Messaging",           "...", "$500"],
  ],
  wp2Deliverables: [
    ["Commercialization Plan Document (Phase II-Ready)", "...", "$2,500"],
    ["Executive Commercialization Summary",   "...", "$500"],
    ["Strategy Review & Final Revisions",     "...", "$500"],
  ],

  outputPath: '/sessions/epic-intelligent-knuth/mnt/outputs/proposal-p1-output.docx',
  diagramPath: null,  // optional Push+Pull engine diagram
};
```

### Work Package budget math rule
WP1 + WP2 must equal `totalBudget` ($6,500). Line items within each WP must sum to their WP total.

### Default Work Package deliverables

**WP1 — Commercialization Strategy** ($3,000)
| Deliverable | Default Price |
|---|---|
| Five Questions Synthesis | $1,500 |
| ICP Development — Primary Market Segment | $1,000 |
| Voice of Customer Messaging | $500 |

**WP2 — Commercialization Plan Document** ($3,500)
| Deliverable | Default Price |
|---|---|
| Commercialization Plan Document (Phase II-Ready) | $2,500 |
| Executive Commercialization Summary | $500 |
| Strategy Review & Final Revisions | $500 |

---

## Step 4 — Run the Scripts

```bash
cd /sessions/epic-intelligent-knuth/mnt/outputs

node build-[client]-p1-proposal.js
python3 build-[client]-p1-budget.py
node build-[client]-p1-letters.js
```

---

## Step 5 — Validate Each Output

### Proposal (.docx)
```bash
unzip -p [client]-p1-proposal.docx word/document.xml | python3 -c "
import sys, xml.etree.ElementTree as ET, re
data = sys.stdin.buffer.read()
bad = re.findall(rb'<[0-9][^>]*/?>', data)
print('Bad XML tags:', bad)
try:
    ET.fromstring(data)
    print('XML: VALID')
except ET.ParseError as e:
    print('XML ERROR:', e)
xml = data.decode('utf-8', errors='replace')
print('Paragraphs:', len(re.findall(r'<w:p[ >]', xml)))
print('Tables:', len(re.findall(r'<w:tbl[ >]', xml)))
"
```
Expected: XML VALID, 180+ paragraphs, 18+ tables.

### Budget (.xlsx)
```bash
python3 scripts/recalc.py [client]-p1-budget.xlsx 30
```

### Letters (.docx)
Same XML validation. Expected: 100+ paragraphs, 5+ tables.

---

## Step 6 — Copy to Workspace

```bash
cp "[client]-p1-proposal.docx" "/sessions/epic-intelligent-knuth/mnt/Catalyzing Concepts/[CLIENT]_TABA_P1_Proposal.docx"
cp "[client]-p1-budget.xlsx"   "/sessions/epic-intelligent-knuth/mnt/Catalyzing Concepts/[CLIENT]_TABA_P1_Budget.xlsx"
cp "[client]-p1-letters.docx"  "/sessions/epic-intelligent-knuth/mnt/Catalyzing Concepts/[CLIENT]_TABA_P1_Letters.docx"
```

---

## Key Rules and Brand Standards

### Firm Identity
- **Formal / first mention**: Catalyzing Concepts LLC
- **Informal / subsequent**: Catalyzing Concepts
- **Signer**: Ben Bickerstaff, Founder & Owner, Catalyzing Concepts LLC
- **Email**: bb@bhbickerstaff.com

### Catalyzing Concepts Brand Palette
```
PRIMARY  = "00A94F"  // Emerald Green  — headers, section banners, table headers
ACCENT   = "004A23"  // Forest Green   — WP tags, callout borders, dark emphasis
STEEL    = "B6D3C4"  // Sage Green     — secondary backgrounds, light accents
OFFWHITE = "F4F4F9"  // Off-White      — alternating table rows
DARK     = "292E2B"  // Charcoal       — all body text
WHITE    = "FFFFFF"
MID      = "888888"  // Neutral Gray   — captions, footer text
LPRIMARY = "D4EDE0"  // Light Emerald  — section banner bg, WP header bg
LSTEEL   = "E2EEE9"  // Light Sage     — budget box bg
LACCENT  = "E8F5EE"  // Very Light Green — callout bg
```

### Logo Files (resolved dynamically at runtime)
```javascript
const { execSync } = require('child_process');
function findLogoDir() {
  try {
    return execSync('find /sessions -maxdepth 6 -type d -name "Logo Files" 2>/dev/null | head -1', { encoding: 'utf8' }).trim();
  } catch(e) { return ''; }
}
const LOGO_DIR     = findLogoDir();
const LOGO_PRIMARY = LOGO_DIR ? `${LOGO_DIR}/CatalyzingConcept Horizontal_cropped.png` : '';
const LOGO_WHITE   = LOGO_DIR ? `${LOGO_DIR}/CatalyzingConcept White horizontal.png`   : '';
```

### Document Structure (Phase I Proposal)
1. Cover Page — logo, client info, prepared by block, tech focus
2. Section 01 — Executive Summary
3. Section 02 — Methodology (Push + Pull diagram → Five Questions → Single ICP Profile)
4. Section 03 — Communication Policy *(standard — same as Phase II)*
5. Section 04 — Scope of Work (2 Work Packages)
6. Section 05 — Engagement Timeline *(6-month sprint table, no roadmap graphic)*
7. Section 06 — About Catalyzing Concepts LLC
8. Section 07 — Next Steps

**Note:** No infrastructure scenarios (Scenario A/B) in Phase I. The commercialization plan is the product, not a marketing engine.

### Phase I Framing Language
- Exec summary: Frame the engagement as *building the strategic foundation for Phase II* — not executing a commercial engine
- WP1: Diagnostic and strategy work — same Five Questions backbone
- WP2: The Commercialization Plan document is the *anchor deliverable* — it goes into the Phase II proposal
- Timeline language: "6-month engagement," "Phase II proposal submission" as the terminal milestone
- Next Steps: Include a step for submitting the Commercialization Plan to the NASA program office with the Phase II application

### Letter Standards
- Same format as Phase II: LOC + Acknowledgement Letter
- LOC budget detail page: simpler (2 WPs, 6 line items)
- No client signature blocks — Ben signs only (attestation)
- Ack letter: Same 5-paragraph standard body
- Rate: $150/hr — same justification language

### Output File Naming Convention
```
[CLIENT_ABBREV]_TABA_P1_Proposal.docx
[CLIENT_ABBREV]_TABA_P1_Budget.xlsx
[CLIENT_ABBREV]_TABA_P1_Letters.docx
```
