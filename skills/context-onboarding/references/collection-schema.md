# Collection Schema Reference

## Known Collection IDs
- **Project Pipeline** (Projects): `ed66aa75-337a-1eb4-13d2-0e16b1cdd59f`
- **Ventures**: create on first run — no existing collection
- **Clients**: create on first run — no existing collection

## Ventures Collection Schema
Fields to create:
| Field Name | Type | Notes |
|---|---|---|
| Venture Name | Text | Primary identifier |
| Type | Select | Options: Active, Parked |
| Status | Select | Options: Pre-revenue, Revenue, Scaling |
| Revenue Stage | Text | e.g., "$3k/month" |
| Priority | Select | Options: 1-Primary, 2-Secondary, 3-Parked |
| Date Onboarded | Date | Set at creation |
| BA Initialized | Checkbox | Check when BA skill is created |

Relation to add after creation:
- Field: "Projects" → relates to Projects collection (two-way)
- Related field on Projects side: "Parent Venture"

## Projects Collection Schema
Fields to add to existing Project Pipeline collection:
| Field Name | Type | Notes |
|---|---|---|
| Project Name | Text | Primary identifier |
| Project Type | Select | Options: Content Campaign, Product Sprint, Marketing Launch, Partnership, Operational Buildout, Standalone |
| Parent Venture | Relation | → Ventures collection (two-way) |
| Status | Select | Options: Planning, Active, Paused, Complete |
| Start Date | Date | |
| Target Completion | Date | |
| Success Criteria | Text | What "done" looks like |

## Clients Collection Schema
Fields to create:
| Field Name | Type | Notes |
|---|---|---|
| Client Name | Text | Primary identifier |
| Agency | Text | e.g., NASA, NIH, DoD |
| SBIR Phase | Select | Options: Phase I, Phase II |
| Award Amount | Text | Approximate is fine |
| Phase II Deadline | Date | |
| Engagement Type | Select | Options: Phase I TABA ($6.5k), Phase II TABA ($50k) |
| Status | Select | Options: Active, Complete, Paused |
| Date Onboarded | Date | |

Relation to add:
- Field: "Parent Venture" → relates to Ventures collection (Catalyzing Concepts record)
