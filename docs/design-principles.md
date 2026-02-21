# Design Principles

## 1. Machine-first

JSON is the canonical format. Rendering to career pages, PDFs, or job board listings is a downstream presentation concern. Every field is typed and structured for programmatic consumption.

## 2. Employer-controlled

Companies own their job data. The `visibility` section provides granular controls over what information is public vs. restricted to specific hiring stages.

## 3. Agent-ready

Requirements are split into `must_have` (hard constraints agents MUST filter on) and `nice_to_have` (soft preferences agents SHOULD rank on). This eliminates the ambiguity of free-text "requirements" sections.

## 4. OTP-complementary

OJP fields are explicitly designed to match against [Open Talent Protocol](https://opentalentprotocol.org) profile sections. Skills map to skills, salary preferences map to compensation ranges, location preferences map to arrangement types.

## 5. Vendor-neutral

MIT licensed. No required registry, platform, or ATS. Any system can produce or consume OJP documents.

## 6. Interoperable

Every field has a documented mapping to schema.org/JobPosting properties. OJP is a strict superset of the fields required by Google for Jobs, LinkedIn's Job Posting API, and HR-XML's PositionOpening schema.
