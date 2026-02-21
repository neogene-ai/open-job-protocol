# Migration: LinkedIn Job Posting API to OJP

## Field mapping

| LinkedIn Field | OJP Field | Notes |
|----------------|-----------|-------|
| `title` | `role.title` | Direct |
| `description` | `role.description` | Direct |
| `externalJobPostingId` | `meta.id` | Direct |
| `listedAt` | `meta.created_at` | Convert ms timestamp to ISO 8601 |
| `expireAt` | `meta.expires_at` | Convert ms timestamp to ISO 8601 |
| `jobPostingOperationType` | `meta.status` | Map CREATE/UPDATE/CLOSE |
| `companyName` | `organization.name` | Direct |
| `companyApplyUrl` | `process.apply_url` | Direct |
| `location` | `offering.location.onsite_address` | Parse location string |
| `alternateLocations` | `offering.location.alternate_locations` | Direct |
| `workplaceTypes` | `offering.location.model` | Map ON_SITE/HYBRID/REMOTE |
| `categories` | `role.function` | Map LinkedIn category URNs |
| `industries` | `organization.industry` | Map LinkedIn industry URNs |
| `experienceLevel` | `role.seniority_level` | Map ENTRY_LEVEL/ASSOCIATE/etc. |
| `compensation.baseSalary` | `offering.compensation.salary` | Direct |
| `compensation.bonusAmount` | `offering.compensation.bonus` | Direct |
| `compensation.stockOptions` | `offering.compensation.equity` | Direct |
| `skillsDescription` | `requirements.must_have.skills` | Parse from text to skill objects |

## Notes

- LinkedIn supports up to 25,000 characters for `description`. OJP has no character limit.
- LinkedIn's compensation schema supports multiple types (BASE_SALARY, BONUS, COMMISSION, STOCK_OPTIONS, etc.) which map to OJP's `offering.compensation` sub-objects.
- LinkedIn-specific fields (follower count, company page URL) are not mapped but can be stored in OJP's `extensions` section.
