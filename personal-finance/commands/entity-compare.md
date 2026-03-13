---
description: Compare S-Corp vs Schedule C tax treatment
allowed-tools: Read, Write, Bash, Edit, Glob, Grep
argument-hint: [income] [state]
---

Run a side-by-side S-Corp vs Schedule C comparison using the entity-compare skill.

If $ARGUMENTS is provided, parse it for income amount and state. Ask for any missing required inputs.

Load the entity-compare skill and follow its full comparison workflow. Output the comparison table, breakeven analysis, and recommendation directly in chat.

Read references/tax-parameters.md in the plugin root for tax data and skills/entity-compare/references/entity-comparison.md for entity-specific rules and costs.
