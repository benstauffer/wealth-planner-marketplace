---
description: Build multi-year tax and cash flow projections
allowed-tools: Read, Write, Bash, Edit, Glob, Grep
argument-hint: [income] [years]
---

Build a multi-year financial projection for a business owner using the projection skill.

If $ARGUMENTS is provided, parse it for starting income and projection horizon (years). Ask for any missing required inputs.

Load the projection skill and follow its full workflow. Default to 5 years if not specified. Always produce:
1. A formatted chat summary with year-by-year tables and threshold alerts
2. An Excel workbook saved to the outputs folder (generated via Python/openpyxl using Bash)

Read references/tax-parameters.md for all 2026 tax data and references/projection-methodology.md for projection defaults.
