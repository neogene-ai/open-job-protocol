# Overview

Open Job Protocol (OJP) is a machine-first, vendor-neutral JSON standard for job opportunities. It is the employer-side counterpart to [Open Talent Protocol](https://opentalentprotocol.org).

## Problem

Job postings today are unstructured prose designed for human readers and SEO. AI agents must scrape and interpret free-text to extract requirements, compensation, and location data. Every ATS and job board uses a different format.

## Solution

OJP provides a structured JSON format with:

- **9 top-level sections** covering every aspect of a job posting
- **Hard/soft requirement split** (`must_have` / `nice_to_have`) for precise agent filtering
- **Bilateral matching** with OTP candidate profiles
- **Process transparency** including interview stages and timelines
- **Discovery** via `/.well-known/ojp.json`

## Coverage

The schema covers all 46 fields from the cross-reference of schema.org/JobPosting, Google for Jobs, LinkedIn Job Posting API, and HR-XML, plus 19 agent-first extensions for a total of 65 fields.

## Links

- [Website](https://openjobprotocol.org)
- [Schema](../schema/openjob-protocol.schema.json)
- [Examples](../examples/)
- [Open Talent Protocol](https://opentalentprotocol.org)
