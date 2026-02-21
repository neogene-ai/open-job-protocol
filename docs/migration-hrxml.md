# Migration: HR-XML to OJP

## Conceptual mapping

HR-XML's PositionOpening schema uses a hierarchical structure. OJP flattens this into top-level sections.

| HR-XML Element | OJP Section | Notes |
|----------------|-------------|-------|
| PositionOpening | Root document | — |
| PositionOpening.status | `meta.status` | Map status codes |
| PositionProfile | `role` + `requirements` | Split into role content and qualifications |
| PositionDetail.title | `role.title` | Direct |
| PositionDetail.description | `role.description` | Direct |
| PositionDetail.industry | `organization.industry` | Direct |
| PositionOrganization | `organization` | Flatten hierarchy |
| PositionLocation | `offering.location` | Flatten to model + address |
| Competency | `requirements.must_have.skills` | Map competency nodes to skill objects |
| PositionSchedule | `offering.work_schedule` | Map schedule type |
| PositionCompensation | `offering.compensation` | Map pay ranges |
| QualificationsRequired | `requirements.must_have` | Split must/nice based on priority |
| QualificationsPreferred | `requirements.nice_to_have` | Direct |

## Notes

- HR-XML internal fields (recruiter notes, workflow state, approval chains) are intentionally not mapped to OJP. OJP represents the public-facing job opportunity, not internal ATS workflow.
- OJP extends HR-XML with modern fields: `team`, `process` (with interview stages), `culture`, `visibility`, and `work_arrangement` (remote/hybrid/onsite).
