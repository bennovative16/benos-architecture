
# TABA Proposal Package Generator

Builds the complete 3-document TABA proposal package for a Catalyzing Concepts client:
1. **Client-Facing Proposal** (.docx) — Branded proposal with methodology, Communication Policy, Infrastructure Scenarios A & B, 4 Work Packages, budget
2. **TABA Budget Spreadsheet** (.xlsx) — Option A ($35k) and Option B ($50k) with live formulas
3. **Letters Document** (.docx) — TABA Vendor Quote (LOC) with full line-item budget breakdown + Acknowledgement Letter

All outputs use the Catalyzing Concepts brand palette, logo, and the Push + Pull Commercialization Engine framework.

---

## Step 1 — Client Intake

Before writing any code, gather the following via AskUserQuestion or by reading the conversation. Ask in 2–3 rounds maximum.

### Round 1 (Required)
- **Client company name** (full + abbreviation)
- **Primary contact** (name, title)
- **Address** (street, city, state, zip)
- **Technology description** — one sentence
- **IP status**: pre-patent | utility filed | provisional filed | patent issued | trade secret
- **Agency**: NASA | DOE | NSF | DoD — drives all agency-specific language throughout the documents; default to NASA if not specified

### Round 2 (Scope)
- **Budget**: Default $50k. Ask if $35k or custom.
- **Year 1 / Year 2 split**: Standard ($28k/$22k) or even ($25k/$25k)?
- **Proposal number**: or use `[INSERT PROPOSAL NUMBER]`
- **Client website URL** (for Infrastructure Scenario A)

### Round 3 (Content)
- **Three target market segments / ICP groups**
- **Key conferences or BD channels**
- **Work package adjustments**

> **If the user says "just get started"**, approximate from the technology description and mark gaps with `[PLACEHOLDER]`.

---

## Step 2 — Set Up the Build Environment

```bash
node -e "require('docx'); console.log('docx OK')" 2>/dev/null || npm install docx
python3 -c "import openpyxl; print('openpyxl OK')" 2>/dev/null || pip install openpyxl --break-system-packages

WORKSPACE="/sessions/[SESSION_ID]/mnt/Catalyzing Concepts"
ls "$WORKSPACE/CatCon_CommercializationEngine.png" && echo "Engine diagram: FOUND" || echo "MISSING — will skip"
ls "$WORKSPACE/Logo Files/CatalyzingConcept Horizontal.png" && echo "Logo: FOUND" || echo "MISSING — will use text fallback"
```

Infrastructure diagrams (`infra-A.png`, `infra-B.png`) are optional — set paths to `null` and the sections build without images.

---

## Step 3 — Customize and Run the Template Scripts

Read the three template scripts from `scripts/`. Edit ONLY the `CLIENT CONFIG` block.

### Full CLIENT CONFIG reference

```javascript
const CLIENT = {
  companyFull:    "Full Company Name, Inc.",
  companyShort:   "ABC",
  contactName:    "Jane Smith",
  contactTitle:   "Vice President of Commercialization",
  address:        "123 Main St, Cambridge, MA 02139",
  proposalNum:    "[INSERT PROPOSAL NUMBER]",
  techFocus:      "One-sentence technology focus for cover page",
  ipStatus:       "utility patent filed",

  // Budget
  totalBudget:    50000,
  wp1Total:       "$16,250",
  wp2Total:       "$10,000",
  wp3Total:       "$13,000",
  wp4Total:       "$10,750",
  yr1Std:         "$28,000 — Work Packages 1 & 2 plus core WP3 assets",
  yr2Std:         "$22,000 — WP3 execution and full WP4 outreach and pipeline management",

  // ICPs
  icp1Name:   "ICP 1\nSegment Name",
  icp1Who:    "Who they are...",
  icp1Msg:    "What they need to hear...",
  icp2Name:   "ICP 2\nSegment Name",
  icp2Who:    "Who they are...",
  icp2Msg:    "What they need to hear...",
  icp3Name:   "ICP 3\nSegment Name",
  icp3Who:    "Who they are...",
  icp3Msg:    "What they need to hear...",

  // Executive summary
  execPara1:  "Technology description and differentiation...",
  execPara2:  "The commercialization challenge and what Catalyzing Concepts will do...",

  // Infrastructure scenarios
  clientWebsite:   "yourclient.com",
  catconSubdomain: "yourclient.catalyzingconcepts.com",
  infraAPath:      null,   // full path to infra-A.png, or null to skip
  infraBPath:      null,   // full path to infra-B.png, or null to skip

  // Asset paths
  diagramPath: '/sessions/[SESSION]/mnt/Catalyzing Concepts/CatCon_CommercializationEngine.png',
  logoPath:    '/sessions/[SESSION]/mnt/Catalyzing Concepts/Logo Files/CatalyzingConcept Horizontal.png',

  // Deliverable overrides — leave [] to use defaults
  wp1Deliverables: [],
  wp2Deliverables: [],
  wp3Deliverables: [],
  wp4Deliverables: [],

  outputPath: '/sessions/[SESSION]/mnt/outputs/[CLIENT]_TABA_Proposal.docx',
};
```

### Budget math rule
WP1 + WP2 + WP3 + WP4 must equal totalBudget. Line items within each WP must sum to their WP total.

### Default deliverables

**WP1 — Commercialization Strategy** ($16,250 default)
| Deliverable | Default Price |
|---|---|
| Five Questions Synthesis | $3,000 |
| ICP Development — Three Profiles | $3,000 |
| Voice of Customer Messaging | $2,250 |
| Go-to-Market Strategy Document | $3,000 |
| Licensing Strategy & Revenue Forecast | $5,000 |

**WP2 — Digital Infrastructure & Brand** ($10,000 default)
| Deliverable | Default Price |
|---|---|
| Product Branding & Identity | $2,500 |
| Website Enhancement & Integration | $1,500 |
| GoHighLevel CRM Setup | $3,000 |
| Automation Flow Build | $3,000 |

**WP3 — Strategy Execution & Core Content** ($13,000 default)
| Deliverable | Default Price |
|---|---|
| Technology Brief / One-Pager (2 versions) | $1,500 |
| Pitch Deck | $2,500 |
| Conference & Event Strategy | $2,250 |
| Core Content Strategy + 90-Day Calendar | $2,250 |
| Newsletter Setup + Initial Issues | $2,000 |
| LinkedIn Content Foundation | $2,500 |

**WP4 — Ongoing Outreach & Pipeline Management** ($10,750 default)
| Deliverable | Default Price |
|---|---|
| Cold Email Campaigns per ICP | $3,750 |
| ICP-Specific LinkedIn Content Production | $3,250 |
| CRM & Pipeline Management | $3,750 |

---

## Step 4 — Run the Scripts

```bash
cd /sessions/[SESSION]/mnt/outputs
node build-[client]-proposal.js
python3 build-[client]-budget.py
node build-[client]-letters.js
```

---

## Step 5 — Validate

### Proposal
```bash
unzip -p [client]-proposal.docx word/document.xml | python3 -c "
import sys, xml.etree.ElementTree as ET, re
data = sys.stdin.buffer.read()
bad = re.findall(rb'<[0-9][^>]*/?>', data)
print('Bad XML tags:', bad)
try:
    ET.fromstring(data); print('XML: VALID')
except ET.ParseError as e: print('XML ERROR:', e)
xml = data.decode('utf-8', errors='replace')
print('Paragraphs:', len(re.findall(r'<w:p[ >]', xml)))
print('Tables:', len(re.findall(r'<w:tbl[ >]', xml)))
print('Images:', len(re.findall(r'<a:blip ', xml)))
"
```
Expected: XML VALID, 300+ paragraphs, 35+ tables, 2+ images (logo + engine diagram).

**Common errors:**
- `<0/>` bad tag → `rows: [array]` double-wrapped; remove outer `[...]`
- `]),` closing TableRow → missing `}` → change to `]}),`

### Budget
Math validation prints automatically — all three checks must say OK.

### Letters
Same XML validation. Expected: 130+ paragraphs, 10+ tables.

---

## Step 6 — Copy to Workspace

```bash
cp "[client]-proposal.docx" "/sessions/[SESSION]/mnt/Catalyzing Concepts/[CLIENT]_TABA_Proposal.docx"
cp "[client]-budget.xlsx"   "/sessions/[SESSION]/mnt/Catalyzing Concepts/[CLIENT]_TABA_Budget.xlsx"
cp "[client]-letters.docx"  "/sessions/[SESSION]/mnt/Catalyzing Concepts/[CLIENT]_TABA_Letters.docx"
```

---

## Key Rules and Brand Standards

### Catalyzing Concepts Brand Palette
```
PRIMARY  = "00A94F"  // Emerald Green  — headers, section markers, WP accents
ACCENT   = "004A23"  // Forest Green   — callout borders, WP header top rule
STEEL    = "B6D3C4"  // Sage Green     — secondary accents, timeline phases
OFFWHITE = "F4F4F9"  // Near-white     — alternating table rows
DARK     = "292E2B"  // Charcoal       — all body text
WHITE    = "FFFFFF"
MID      = "888888"  // Gray           — captions, footer text
LPRIMARY = "E8F5EE"  // Light Green    — section banner bg, WP header bg
LSTEEL   = "D6EAE0"  // Light Sage     — budget box bg
LACCENT  = "EDF7F2"  // Very Light Green — callout bg
```

### Logo
- File: `Logo Files/CatalyzingConcept Horizontal.png`
- In proposal header (small): `width: 160, height: 46` pts
- In cover page: `width: 240, height: 70` pts
- Logo is loaded via `logoPath` in CLIENT config; if null, header falls back to text

### Document Structure (Proposal)
```
Cover Page
Section 01 — Executive Summary
Section 02 — Methodology (Push+Pull diagram → Five Questions → ICP Profiles → Engine Map)
Section 03 — Communication Policy
Section 03 — Infrastructure — Scenario A        ← same "03" banner, sub-pages
Section 03 — Infrastructure — Scenario B
Section 04 — Scope of Work (4 Work Packages)
Section 05 — Engagement Timeline
Section 06 — About Catalyzing Concepts LLC
Section 07 — Next Steps
```

### Communication Policy (Section 03)
Intro: *"Catalyzing Concepts operates as a strategic partner, not a vendor. Clear communication standards protect the integrity of the work and ensure that every deliverable reflects the client's voice, market position, and strategic intent."*

8-row table (colWidths: 2600 | remainder):
| Policy Area | Standard |
|---|---|
| Review & Approval | All client-facing deliverables require review and written approval before publication. 5-business-day review window standard. |
| Voice & Messaging | Messaging matrix built in WP1. First two rounds of revision incorporated without change fees. |
| Client Contact Ownership | All CRM contacts, outreach lists, and pipeline data are client property. Full export provided at engagement close. |
| Confidentiality | All technology details, financial info, and strategic plans treated as confidential. NDA executed on request. |
| IP Sensitivity | Pre-patent/provisional IP framed commercially without technical disclosure. Catalyzing Concepts flags any disclosure risk. |
| Reporting Cadence | Monthly pipeline reports during WP4. Mid-engagement strategy review at end of WP2. All reports in writing. |
| Communication Channels | Primary via email. Strategy sessions via video call. Shared project management workspace set up at engagement start. |
| No Unauthorized Commitments | Catalyzing Concepts does not commit on the client's behalf to third parties without explicit written authorization. |

### Infrastructure Scenarios (Section 03 continued)
**Scenario A** — Client's existing website as commercial hub (uses `clientWebsite`)
**Scenario B** — Catalyzing Concepts dedicated subdomain (uses `catconSubdomain`)
Images: `infraAPath` / `infraBPath` — set to null to skip, section renders without image.
Image display size: `INFRA_W = 640, INFRA_H = 369`

### LOC Budget Table (Letter 1)
The Letter of Commitment must include a full line-item budget breakdown after the "Budget" heading — a condensed single-page version of the spreadsheet. Structure: WP header rows (PRIMARY bg) → deliverable rows (alternating WHITE/OFFWHITE) → WP subtotal rows (LPRIMARY bg) → grand total row. Three columns: Deliverable | Description | Investment (right-aligned).

### Signature Rules
- **Letter 1 (Vendor Quote / LOC):** Catalyzing Concepts (Ben Bickerstaff) is the primary signatory. Client countersigns at the bottom to acknowledge and accept.
- **Letter 2 (Acknowledgement):** The CLIENT is the primary signatory — this letter goes from the awardee to the program office. Client signature block first; Ben / Catalyzing Concepts countersigns below to confirm engagement.

### Five Questions (constant across all clients — only answers change)
1. Why does this problem exist?
2. What are current conditions on the ground?
3. What will [client] do differently?
4. Who experiences this problem?
5. How is this delivered as a business?

> **IP rule**: Pre-patent → value-framed, no technical detail. Utility filed / patent issued → full technical disclosure appropriate in government ICP messaging.

### Rate
$150/hr. No separate platform pass-throughs — GoHighLevel, Framer, tool costs bundled into deliverable pricing.

---

## Agency Variations

| Agency | Letter Header | Key Notes |
|---|---|---|
| NASA | NASA TABA Vendor Quote + Ack Letter | Proposal # required, TABA service taxonomy, Expected Outcome framing |
| DOE | DOE SBIR/STTR TABA Vendor Quote | Statutory ref: 15 U.S.C. § 638, DOE program office disbursement |
| NSF | Standard Vendor Quote | Less formal, no specific taxonomy required |
| DoD (AFWERX, etc.) | Program-specific | Check current program requirements |

---

## Output File Naming
```
[CLIENT_ABBREV]_TABA_Proposal.docx
[CLIENT_ABBREV]_TABA_Budget.xlsx
[CLIENT_ABBREV]_TABA_Letters.docx
```
