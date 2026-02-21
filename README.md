# Open Job Protocol (OJP)

A machine-first, vendor-neutral JSON standard for job opportunities — designed for employers, agents, and the agentic talent marketplaces of tomorrow.

**The employer-side counterpart to [Open Talent Protocol](https://opentalentprotocol.org).**

- **Website:** [openjobprotocol.org](https://openjobprotocol.org)
- **Schema:** [`schema/openjob-protocol.schema.json`](schema/openjob-protocol.schema.json)
- **License:** MIT

## Quick start

```bash
# Validate a document
cd tools/validator-cli
npm install && npm run build
node dist/index.js ../../examples/backend-engineer-senior.json
```

## Design principles

| Principle | Description |
|-----------|-------------|
| **Machine-first** | JSON is canonical; rendering is downstream |
| **Employer-controlled** | Granular visibility controls |
| **Agent-ready** | `must_have` / `nice_to_have` requirement split |
| **OTP-complementary** | Bilateral matching with Open Talent Protocol |
| **Vendor-neutral** | MIT licensed, no required platform |
| **Interoperable** | Maps to schema.org, Google for Jobs, LinkedIn API, HR-XML |

## Schema sections

| Section | Required | Description |
|---------|----------|-------------|
| `meta` | Yes | Identifiers & lifecycle |
| `role` | Yes | Title, description, employment type |
| `organization` | Yes | Company identity |
| `requirements` | Yes | must_have / nice_to_have skills, experience, credentials |
| `offering` | Yes | Compensation, location, benefits, growth |
| `team` | No | Team composition (OJP extension) |
| `process` | No | Hiring process transparency (OJP extension) |
| `culture` | No | Culture signals (OJP extension) |
| `visibility` | No | Privacy controls (OJP extension) |
| `extensions` | No | Domain-specific fields |

## Examples

- [`backend-engineer-senior.json`](examples/backend-engineer-senior.json) — Hybrid Go role in Berlin
- [`product-manager-mid.json`](examples/product-manager-mid.json) — Remote B2B SaaS product role
- [`nurse-practitioner.json`](examples/nurse-practitioner.json) — Onsite clinical role

## Related

- [Open Talent Protocol](https://opentalentprotocol.org) — The candidate-side counterpart
- [JobGrow](https://jobgrow.ai) — AI career assistant (initial sponsor)
