# Client Onboarding — Catalyzing Concepts

This skill onboards a new CC client engagement from zero. It ingests all available
materials, runs a completeness checklist, surfaces gaps, creates the folder structure
in both storage systems, and routes content to the correct locations.

Belt-and-suspenders principle: CC client data lives in both Craft (operational access)
and iCloud (file backup). Sensitive client information never goes to Linear.

---

## Trigger Detection

Fire immediately when Ben says:
- "New client — [Name/Company]"
- "Onboard [client name]"
- "Set up [client name]"
- "Client intake — [details]"
- Drops raw client information into chat (Phase I abstract, award notice, company name,
  contact details, technology description, etc.)

---

## Step 1 — Collect Client Information

Ask for what's missing. Gather in one pass — don't ask question by question.

**Required to proceed:**
- Client / company name
- Primary contact name + email
- Technology area / description (1-3 sentences)
- SBIR/STTR Phase (I or II)
- Agency and solicitation (e.g., NASA SBIR Phase I, NIH STTR Phase II)
- Award amount (approximate is fine)
- Phase II application window / deadline (if known)
- How the engagement began (referral, outreach, inbound, prior relationship)

**Nice to have (surface gaps if missing, don't block):**
- Phase I abstract or executive summary
- Award notice document
- Prior commercialization plan or market research
- Website / LinkedIn
- Key competitors (if client has identified them)
- Ben's initial notes or observations

If Ben drops a brain dump or document, extract what you can and surface only the
remaining gaps. Never ask for something already provided.

---

## Step 2 — Run the Completeness Checklist

After gathering available info, evaluate against this checklist and surface gaps:

### Engagement Fundamentals
- [ ] Client / company name confirmed
- [ ] Primary contact name + email
- [ ] Agency + solicitation confirmed
- [ ] Award amount known
- [ ] Phase II deadline known or estimated
- [ ] Engagement type confirmed (Phase I TABA = $6,500 / Phase II TABA = $50k)

### Technology Context
- [ ] Technology description (1-3 sentences minimum)
- [ ] TRL (Technology Readiness Level) — current and target
- [ ] Problem being solved
- [ ] Differentiation from existing solutions

### Market Context
- [ ] Target market identified (even roughly)
- [ ] End users / customer segments named
- [ ] Known competitors or adjacent solutions

### Commercialization Context
- [ ] Phase II transition path (government customer, commercial market, or both)
- [ ] Existing customer or partner relationships (LOIs, MOUs, pilots)
- [ ] Revenue model hypothesis

### Engagement Logistics
- [ ] Kick-off call scheduled or pending
- [ ] Contract / SOW status
- [ ] Communication channel established (email, Slack, etc.)

Present checklist as:
✅ [item] — have it
⚠️ [item] — missing, need to gather
❓ [item] — unknown, low priority for now

Do not block setup on checklist completion. Create the folder structure regardless.
Surface gaps as action items for Ben to follow up on.

---

## Step 3 — Create Folder Structure in Craft

Create the following structure under BenOS / Clients / [Client Name] /:

```
BenOS
└── Clients
    └── [Client Name]
        ├── Client Brief          (document — populated in Step 5)
        ├── Engagement Log        (document — running notes, call summaries)
        ├── Commercialization Plan (document — built during engagement)
        ├── Market Research       (document — findings and sources)
        ├── Deliverables          (folder — final outputs for client)
        └── Tasks                 (Craft native tasks — created via Task Manager)
```

Use Craft MCP:
1. `folders_list` — find or confirm BenOS / Clients / exists. Create if missing.
2. `folders_create` — create `[Client Name]` folder inside Clients
3. `folders_create` — create `Deliverables` subfolder inside [Client Name]
4. `documents_create` — create Client Brief, Engagement Log, Commercialization Plan,
   Market Research documents inside [Client Name] folder
5. `markdown_add` — populate Client Brief immediately (Step 5)

---

## Step 4 — Create Folder Structure in iCloud

Create the following structure on iCloud Drive:

```
/Bennovative Empire/Catalyzing Concepts/Client Deliverables/
└── [Client Name]
    ├── /Brief
    ├── /Research
    ├── /Deliverables
    └── /Correspondence
```

Use bash to create:
```bash
BASE="/sessions/[session]/mnt/com~apple~CloudDocs/Bennovative Empire/Catalyzing Concepts/Client Deliverables/[Client Name]"
mkdir -p "$BASE/Brief"
mkdir -p "$BASE/Research"
mkdir -p "$BASE/Deliverables"
mkdir -p "$BASE/Correspondence"
```

Confirm creation. Any file-based deliverables (PDFs, decks, proposals) go here.
All operational/task tracking stays in Craft.

---

## Step 5 — Populate Client Brief in Craft

After creating the Client Brief document, populate it with all known information.
Use this template via `markdown_add`:

```markdown
# [Client Name] — Client Brief

**Engagement type:** [Phase I TABA ($6,500) / Phase II TABA ($50k)]
**Agency / solicitation:** [e.g., NASA SBIR Phase II]
**Award amount:** [$ amount]
**Phase II deadline:** [date or TBD]
**Primary contact:** [Name] — [email]
**Engagement started:** [date]
**Source:** [how Ben found / was found by this client]

---

## Technology

[2-4 sentence description of what the technology does, what problem it solves,
and what makes it distinct.]

**TRL:** [Current] → [Target at Phase II completion]

---

## Market

**Target market:** [description]
**End users:** [who actually uses it]
**Known competitors / adjacent solutions:** [list or "TBD"]

---

## Commercialization Path

**Phase II transition:** [Government customer / commercial market / both]
**Existing relationships:** [LOIs, MOUs, pilots — or "None identified yet"]
**Revenue model:** [hypothesis or "TBD"]

---

## Engagement Status

**Kick-off call:** [scheduled / pending / completed — date]
**Contract:** [signed / pending / verbal]
**Communication channel:** [email / Slack / other]

---

## Gaps to Close

[Bullet list of items from the checklist marked ⚠️ or ❓]

---

## Ben's Notes

[Any initial observations, flags, or context from intake conversation]
```

---

## Step 6 — Create Initial Tasks

After folders and brief are set up, create two standard opening tasks via Task Manager:

**Task 1 — Schedule Kick-off Call** (if not already scheduled)
- Venture: #CatalyzeCC
- Type: #ClientOps
- Due: within 5 business days of onboarding
- Route: Craft task inbox

**Task 2 — Complete Gap Analysis**
- Venture: #CatalyzeCC
- Type: #ClientOps
- Due: within 3 business days of kick-off call
- Route: Craft task inbox (linked to client folder)

Present both tasks for Ben to confirm before creating them.

---

## Step 7 — Output the Onboarding Summary

Conclude with a single-screen summary:

```
## ✅ [Client Name] Onboarded — [Date]

**Craft folder:** BenOS / Clients / [Client Name] /
**iCloud folder:** Bennovative Empire / Catalyzing Concepts / Client Deliverables / [Client Name] /
**Engagement type:** [Phase I / Phase II TABA]
**Phase II deadline:** [date or TBD]

**Checklist status:**
- ✅ [N] items complete
- ⚠️ [N] gaps to close

**Gaps:**
[List ⚠️ items from checklist]

**Next actions:**
1. [First task created]
2. [Second task created]
3. [Any critical gap Ben needs to address immediately]
```

---

## Routing Rules (enforced, non-negotiable)

- CC client data → Craft `Clients/[Client Name]/` ONLY
- CC client data → iCloud `Client Deliverables/[Client Name]/` for file backup
- CC client data → NEVER to Linear
- CC client tasks → Craft task inbox tagged `#CatalyzeCC #ClientOps`
- CC client files (PDFs, decks) → iCloud Deliverables subfolder

---

## BenOS Integration

Reads from:
- Ben's intake message or attached documents
- Craft BenOS / Clients / folder (checks for existing client first)
- iCloud Client Deliverables folder (checks for existing folder first)

Writes to:
- Craft: folder structure + Client Brief + Engagement Log shell
- iCloud: folder structure
- Task Manager: opening tasks (routed to Craft)

Called by: Ben directly, BA-Catalyzing
Frequency: Once per new client engagement
MCPs required: Craft MCP (always) | bash (iCloud folder creation)

---

## What this skill does NOT do

- Create deliverables (proposals, plans, decks) — that's TABA skill territory
- Run the engagement — it just sets it up
- Route any client data to Linear
- Create tasks without Ben confirming them first
- Assume engagement type without Ben confirming (Phase I vs Phase II = very different scope)

---

## Success Criteria

Onboarding complete when:
- Craft folder structure exists with populated Client Brief
- iCloud folder structure created
- Completeness checklist surfaced with gaps identified
- Opening tasks confirmed and created
- Ben has a clear picture of what's missing before kick-off call

30-day evaluation date: 2026-06-13
