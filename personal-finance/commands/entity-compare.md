---
description: Compare S-Corp vs Schedule C tax treatment
allowed-tools: Read, Write, Bash, Edit, Glob, Grep
argument-hint: [income] [state]
---

Run a side-by-side S-Corp vs Schedule C comparison using the entity-compare skill.

If $ARGUMENTS is provided, parse it for income amount and state. Ask for any missing required inputs.

Load the entity-compare skill and follow its full comparison workflow. Always produce:
1. A formatted chat summary with comparison table, breakeven analysis, and recommendation
2. An Excel workbook saved to the outputs folder (generated via Python/openpyxl using Bash)

Read references/tax-parameters.md for tax data and references/entity-comparison.md for entity-specific rules and costs.
