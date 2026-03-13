---
description: Calculate tax liability estimate for a business owner
allowed-tools: Read, Write, Bash, Edit, Glob, Grep
argument-hint: [income] [filing-status] [state]
---

Run a comprehensive tax liability estimate for a business owner using the estimate skill.

If $ARGUMENTS is provided, parse it for income amount, filing status, and state. Ask for any missing required inputs.

Load the estimate skill and follow its full calculation workflow. Always produce:
1. A formatted chat summary with the tax breakdown table
2. An Excel workbook saved to the outputs folder (generated via Python/openpyxl using Bash)

Read references/tax-parameters.md in the estimate skill for all 2026 tax data. Do not guess any numbers.
