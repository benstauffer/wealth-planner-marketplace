---
description: Calculate tax liability estimate for a business owner
allowed-tools: Read, Write, Bash, Edit, Glob, Grep
argument-hint: [income] [filing-status] [state]
---

Run a comprehensive tax liability estimate for a business owner using the estimate skill.

If $ARGUMENTS is provided, parse it for income amount, filing status, and state. Ask for any missing required inputs.

Load the estimate skill and follow its full calculation workflow. Output a formatted chat summary with the full tax breakdown table and recommendations.

Read references/tax-parameters.md in the plugin root for all 2026 tax data. Do not guess any numbers.
