# Migration: schema.org/JobPosting to OJP

## Field mapping

| schema.org Property | OJP Field | Notes |
|---------------------|-----------|-------|
| `title` | `role.title` | Direct |
| `description` | `role.description` | Direct |
| `datePosted` | `meta.created_at` | Direct |
| `validThrough` | `meta.expires_at` | Direct |
| `hiringOrganization.name` | `organization.name` | Direct |
| `hiringOrganization.url` | `organization.url` | Direct |
| `hiringOrganization.logo` | `organization.logo_url` | Direct |
| `industry` | `organization.industry` | Direct |
| `employmentUnit` | `organization.department` | Direct |
| `jobLocation` | `offering.location.onsite_address` | Expand to object |
| `jobLocationType` | `offering.location.model` | Map TELECOMMUTE → remote |
| `applicantLocationRequirements` | `offering.location.remote_regions` | Array of region codes |
| `employmentType` | `role.employment_type` | Map FULL_TIME → full_time |
| `baseSalary` | `offering.compensation.salary` | MonetaryAmount → {min, max, currency, period} |
| `salaryCurrency` | `offering.compensation.salary.currency` | Direct |
| `incentiveCompensation` | `offering.compensation.equity/bonus` | Parse into structured objects |
| `skills` | `requirements.must_have.skills[].name` | Flatten DefinedTerm to string |
| `qualifications` | `requirements.nice_to_have.credentials` | Direct |
| `educationRequirements` | `requirements.must_have.education` | Direct |
| `experienceRequirements` | `requirements.must_have.experience` | Direct |
| `experienceInPlaceOfEducation` | `requirements.nice_to_have.experience_in_place_of_education` | Direct |
| `responsibilities` | `role.description` (embed) | Inline or separate field |
| `jobBenefits` | `offering.benefits` | Parse into category/description objects |
| `occupationalCategory` | `role.function` | O*NET-SOC code or free text |
| `workHours` | `offering.work_schedule.hours_per_week` | Parse |
| `jobStartDate` | `role.start_date` | Direct |
| `jobImmediateStart` | `role.start_date` = now | Derive |
| `totalJobOpenings` | `meta.total_openings` | Direct |
| `directApply` | `process.direct_apply` | Direct |
| `eligibilityToWorkRequirement` | `requirements.must_have.legal.work_authorization` | Direct |
| `securityClearanceRequirement` | `requirements.must_have.legal.security_clearance` | Direct |
| `physicalRequirement` | `requirements.must_have.legal.physical_requirements` | Direct |
| `specialCommitments` | `culture.special_commitments` | Direct |
| `employerOverview` | `culture.employer_overview` | Direct |

## Notes

- OJP is a strict superset of schema.org/JobPosting. Every schema.org field has an OJP equivalent.
- OJP adds sections with no schema.org equivalent: `team`, `process` (stages), `culture` (values, work_style), `visibility`.
- Converting schema.org → OJP is lossless. Converting OJP → schema.org drops the extension sections.
