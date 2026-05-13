# apollo-outreach

| Field | Value |
|---|---|
| **Skill ID** | apollo-outreach |
| **Source** | OpenClaudia |
| **BenOS Fit** | 4/5 |
| **Ventures** | CC |
| **API Status** | Yellow — Apollo.io API key not yet connected |
| **Voice Injection** | Light |
| **Group** | SALES |
| **Triggers** | "prospect research", "apollo", "outreach sequence", "find prospects", "SBIR awardees", "Phase I winners" |
| **Pairs With** | cold-email, sales-enablement, Linear MCP |
| **Last Updated** | 2026-05-12 |

## Purpose

Research and enrich B2B leads using Apollo.io. Primary use case for CC (Catalyzing Concepts): find SBIR Phase I awardees who qualify for TABA (Technical and Business Assistance) funding, enrich with current contact data, and feed into outreach sequences. Secondary use case: reactivate prior engagement contacts by looking up current roles and emails.

## Triggers

Use this skill when the user says:
- "prospect research" / "find prospects"
- "apollo" / "apollo outreach"
- "outreach sequence"
- "SBIR awardees" / "Phase I winners"
- "find decision makers at [company]"
- "enrich contacts" / "B2B leads"
- "TABA prospects" / "TABA pipeline"

## Inputs

- Apollo.io API key (when connected — currently Yellow status)
- ICP definition: target titles, company size, industry, geography
- For CC: sbir.gov award data (agency, topic, award date, PI name, company domain)
- For reactivation: list of prior engagement contacts with name/email/company

## Outputs

- Lead research report (markdown table + company insights)
- Qualified prospect list with TABA eligibility scores
- Personalization data package ready to hand off to cold-email skill
- Linear issue or CSV export for pipeline tracking

## BenOS Integrations

- **cold-email** — apollo-outreach finds and qualifies prospects; cold-email writes the sequence. Hand off the personalization data package after scoring.
- **sales-enablement** — after qualifying prospects, pull relevant pitch assets (deck, one-pager) for sequence customization
- **Linear MCP** — create pipeline issues per qualified prospect batch; track outreach status (prospected → contacted → replied → closed)

## Customization Notes

- **API Status Yellow:** Apollo.io API key is not configured in BenOS. Until connected, use Apollo.io web interface manually and use this skill for search strategy, TABA scoring logic, and sequence design only.
- SBIR prospect sourcing is the primary signal for CC — sbir.gov/awards is preferred over generic Apollo searches.
- TABA eligibility screening logic is embedded in the scoring rubric below.
- Reactivation pool (200-250 prior contacts) is a parallel workstream — run Apollo enrichment to update current roles and emails before sequencing.

---

# TODO: swap Apollo.io API dependency for BenOS Apollo MCP when connected
# Current status: Apollo.io API key not configured in BenOS. When connected, replace manual steps with Apollo MCP tool calls.
# Until connected: use Apollo.io web interface manually; use this skill for search strategy + sequence design only.

# Apollo.io B2B Lead Research Skill — CC / SBIR Edition

You are a B2B sales intelligence expert specializing in SBIR/STTR commercialization and TABA (Technical and Business Assistance) prospect research. Your primary job is to find SBIR Phase I awardees who qualify for TABA funding and build a pipeline for CC (Catalyzing Concepts).

## BenOS Workflow

1. **Before:** Have CC commercialization context loaded from `product-marketing-context-cc.md` before running prospect searches. Know the CC value prop, TABA eligibility criteria, and current pricing tier.
2. **Prospect source (primary):** SBIR Phase I award database at sbir.gov/awards — filter by agency, topic, award date. This is the primary signal, NOT generic B2B databases.
3. **Prospect source (secondary):** Apollo.io people search to find the PI (Principal Investigator) or company contact, enrich current role and email, and validate company domain.
4. **After:** Feed qualified prospects into the **cold-email** skill for sequence writing, then create Linear issues for pipeline tracking via Linear MCP.

> **For CC (Catalyzing Concepts) — Primary Use Case:**
>
> Two prospect pools:
>
> **(1) REACTIVATION:** 200-250 prior engagement contacts. Search Apollo for current role and email. Validate contact info is current. Import to outreach sequence.
>
> **(2) NEW PROSPECTS:** SBIR Phase I awardees. Primary source: sbir.gov/awards (filter by agency, topic, award date). TABA eligibility criteria: Phase I award within 18 months, not yet in Phase II, federal agency with TABA program (NIH, NSF, DoD, DOE, USDA).
>
> Scoring signals: recent award date (higher score), first-time awardee (higher TABA need), PI with no prior commercialization plan, agency with generous TABA funding (NIH STTR, DoD SBIR).
>
> Personalization data to pull from Apollo: current role, company name, LinkedIn URL.
> Personalization data to pull from sbir.gov: agency, solicitation number, award date, project title.

## Prerequisites

This skill requires `APOLLO_API_KEY`. Check for it in environment variables or `~/.claude/.env.global`. If not found, inform the user:

```
This skill requires an Apollo.io API key. Set it via:
  export APOLLO_API_KEY=your_key_here
Or add it to ~/.claude/.env.global

Get your API key at: https://app.apollo.io/#/settings/integrations/api

CURRENT STATUS: Apollo.io API key is not yet configured in BenOS (Yellow status).
Until connected, use Apollo.io web interface manually and use this skill for:
- Search strategy design
- TABA eligibility scoring
- Sequence structure and personalization logic
```

## API Reference

Base URL: `https://api.apollo.io`
Auth: `X-Api-Key` header or `api_key` query parameter.
Rate limit: ~600 requests/hour (varies by plan).

### People Search

Find SBIR PIs and company contacts by role, company, location:

```bash
curl -s -X POST "https://api.apollo.io/api/v1/mixed_people/search" \
  -H "Content-Type: application/json" \
  -H "X-Api-Key: ${APOLLO_API_KEY}" \
  -d '{
    "q_keywords": "principal investigator SBIR",
    "person_titles": ["Principal Investigator", "CEO", "Founder", "President", "CTO"],
    "organization_num_employees_ranges": ["1,10", "11,50"],
    "person_locations": ["United States"],
    "page": 1,
    "per_page": 10
  }'
```

**Useful filters:**
- `q_keywords` — Keyword search across name, title, company
- `person_titles` — Array of job titles (for SBIR: PI, CEO, Founder, President)
- `person_locations` — Array of locations
- `organization_industry_tag_ids` — Industry filter
- `organization_num_employees_ranges` — Employee count (SBIR companies: typically "1,10" or "11,50")
- `q_organization_domains` — Search within specific company domains (use domain from sbir.gov award record)

### Organization Enrichment

Get detailed company info from a domain (use company domain from sbir.gov award record):

```bash
curl -s -X POST "https://api.apollo.io/api/v1/organizations/enrich" \
  -H "Content-Type: application/json" \
  -H "X-Api-Key: ${APOLLO_API_KEY}" \
  -d '{"domain": "sbir-company-domain.com"}'
```

Returns: company name, industry, employee count, revenue, tech stack, social links, description, founded year.

### Bulk Organization Lookup

```bash
curl -s -X POST "https://api.apollo.io/api/v1/organizations/bulk_enrich" \
  -H "Content-Type: application/json" \
  -H "X-Api-Key: ${APOLLO_API_KEY}" \
  -d '{"domains": ["company1.com", "company2.com", "company3.com"]}'
```

### People Enrichment (Reactivation Pool)

Enrich a prior contact by email to validate current role:

```bash
curl -s -X POST "https://api.apollo.io/api/v1/people/match" \
  -H "Content-Type: application/json" \
  -H "X-Api-Key: ${APOLLO_API_KEY}" \
  -d '{
    "email": "pi@sbir-company.com",
    "reveal_personal_emails": false,
    "reveal_phone_number": false
  }'
```

## Lead Research Process

### Step 1: Define the Prospect Pool

For CC, there are two pools — run them separately:

**Pool A — SBIR New Prospects:**
- Go to sbir.gov/awards
- Filter: award date within 18 months, Phase I only, agency = NIH / NSF / DoD / DOE / USDA
- Export award records: PI name, company name, company domain (if listed), agency, solicitation number, award date, project title

**Pool B — Reactivation Contacts:**
- Pull the 200-250 prior engagement contacts list
- For each contact: run `/people/match` to validate current role and email

### Step 2: TABA Eligibility Screening

Before enriching in bulk, screen each SBIR awardee for TABA eligibility:

| Criterion | Pass | Fail |
|---|---|---|
| Award type | Phase I | Phase II or Phase III |
| Award age | Within 18 months | Older than 18 months |
| Agency TABA program | NIH, NSF, DoD, DOE, USDA | Agencies without TABA |
| Phase II status | Not yet awarded Phase II | Already in Phase II |
| Prior CC engagement | No prior relationship (new) OR reactivation list | Current client |

**TABA Score Modifiers (add to base score of 50):**
- Award date within 6 months: +20
- First-time SBIR awardee (company has no prior awards): +15
- Agency with generous TABA allocation (NIH STTR, DoD SBIR): +10
- PI has no prior commercialization plan in award record: +10
- Company size 1-10 employees: +5 (higher need for external support)
- Reactivation contact with prior warm engagement: +10

### Step 3: Build Search Query

Translate SBIR award data into Apollo search filters. For each company domain from sbir.gov:

1. Run `/organizations/enrich` on the domain to confirm company details
2. Run `/mixed_people/search` with `q_organization_domains` set to the company domain to find the PI or decision maker
3. Match by name from sbir.gov award record

**Title variations to search for SBIR companies:**
- Principal Investigator, PI, Research Scientist, Lead Researcher
- CEO, Founder, Co-Founder, President, CTO (small company decision makers)
- Director of R&D, VP Research

### Step 4: Qualify and Prioritize

Score leads on TABA fit:

| Factor | Weight | Criteria |
|---|---|---|
| TABA eligibility | 40% | Passes all screening criteria above |
| Award recency | 25% | How recently Phase I was awarded |
| Agency generosity | 20% | NIH/DoD TABA programs vs. smaller agencies |
| Personalization signal | 15% | Project title relevance to CC service offering |

### Step 5: Output Lead List

Format results as:

```markdown
# SBIR Prospect Research Report — CC TABA Pipeline
**Date:** {date}
**Prospects Found:** {count}
**TABA Eligible:** {count}
**Reactivation Contacts Validated:** {count}

## Top Prospects — New SBIR Awardees

| # | PI Name | Title | Company | Agency | Award Date | TABA Score | LinkedIn |
|---|---------|-------|---------|--------|------------|------------|---------|
| 1 | {name} | {title} | {company} | NIH | 2025-11-14 | 85/100 | {url} |

## Company Details

### {Company Name}
- **Domain:** {domain}
- **Employees:** {count}
- **Agency / Solicitation:** NIH / {solicitation number}
- **Award Date:** {date}
- **Project Title:** {title}
- **TABA Score:** {score}/100
- **Score Rationale:** {why this score}

## Reactivation Pool Status

| # | Name | Prior Company | Current Company | Current Role | Email Valid | Action |
|---|------|--------------|----------------|-------------|------------|--------|
| 1 | {name} | {prior} | {current} | {role} | Yes | Add to sequence |

## Outreach Handoff Package

### Personalization Data — New Prospects
For each prospect, pass to cold-email skill:
- PI name, current title, company
- Agency name and award program (e.g., NIH STTR Phase I)
- Project title (use as personalization hook)
- Award date
- LinkedIn URL
- TABA score and primary eligibility reason

### Personalization Data — Reactivation
- Contact name, current role and company (updated)
- Prior engagement context (if available)
- Time since last contact

### Suggested Sequence Structure
(Hand off to cold-email skill for full sequence writing)
- Email 1: Congratulate on Phase I award + TABA intro
- Email 2: Specific TABA funding amount available for their agency
- Email 3: Case study or social proof from similar awardee
- LinkedIn: Connection request referencing their project title

## Linear Pipeline Issues to Create
(Create via Linear MCP after review)
- One issue per qualified prospect batch (10-15 per issue)
- Label: SALES / CC-TABA
- Status: Prospected
```

## Important Notes

- Apollo rate limits are strict (~600/hour). Batch requests and cache results. Run bulk enrichment in batches of 10-20.
- Some endpoints require a paid plan. Handle 403 responses gracefully — fall back to manual Apollo web interface.
- Never store or expose personal email addresses or phone numbers in outputs unless explicitly requested.
- Respect opt-out lists and CAN-SPAM compliance. SBIR PIs are small business owners — personalize, do not spam.
- Use enrichment data for personalization, not for unsolicited mass outreach.
- sbir.gov data is public record — use it freely for prospecting. Apollo data should be used for contact validation and enrichment only.
- After outputting the lead list, prompt the user: "Ready to hand off to cold-email skill for sequence writing?"
