---
description: Build multi-year tax and cash flow projections
allowed-tools: Read, Write, Bash, Edit, Glob, Grep
argument-hint: [income] [years]
---

Build a multi-year financial projection for a business owner using the projection skill.

If $ARGUMENTS is provided, parse it for starting income and projection horizon (years). Ask for any missing required inputs.

Load the projection skill and follow its full workflow. Default to 5 years if not specified. Output year-by-year tables, threshold alerts, and year-by-year action items directly in chat.

Read references/tax-parameters.md in the plugin root for all 2026 tax data and skills/projection/references/projection-methodology.md for projection defaults.
