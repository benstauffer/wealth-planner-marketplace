---
description: Analyze an IRS transcript and identify tax optimization opportunities
allowed-tools: Read, Write, Bash, Edit, Glob, Grep
argument-hint: [uploaded transcript PDF]
---

Analyze an uploaded IRS transcript to produce a client situation summary, identify missed tax optimization opportunities, and prepare actionable recommendations.

If $ARGUMENTS is provided, use it to locate the uploaded transcript file. If no file is referenced, ask the user to upload their IRS transcript PDF.

Load the tax-review skill and follow its full workflow:
1. Parse the transcript and extract all financial data
2. Present the client situation summary
3. Run the opportunity analysis across all categories
4. Deliver the prioritized action plan
5. Offer to run follow-up scenarios (estimate, entity-compare, projection) with the extracted data

Always read references/tax-parameters.md for current-year tax data when calculating savings opportunities. Do not guess any numbers.
