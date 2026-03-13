---
name: estimate
description: >
  Calculate a complete federal and state tax liability estimate for a business owner.
  Use when the user asks to "estimate my taxes", "calculate tax liability", "what do I owe",
  "run a tax estimate", "how much in taxes", "tax bill", or provides business income and
  wants to know their total tax burden including self-employment tax, income tax, QBID, NIIT,
  and state taxes.
version: 0.1.0
---

# Tax Estimate for Business Owners

Produce a comprehensive tax liability estimate. Always output both a chat summary with formatted tables AND an Excel workbook.

## Required Inputs

Gather from the user (ask if not provided):

- **Filing status**: single, mfj, mfs, hoh
- **Entity type**: Schedule C (sole prop / SMLLC) or S-Corp
- **Net business income** (profit after ordinary business expenses)
- **State of residence**
- **W-2 wages paid** (S-Corp only — if not provided, calculate reasonable comp)
- **Filing year**: default 2026
- **Other income** (if any): W-2 from employer, investment income, rental income
- **Retirement contributions**: Solo 401(k), SEP-IRA, traditional IRA, HSA
- **Itemized deductions** (if applicable): mortgage interest, state/local taxes, charitable

## Calculation Order

Tax calculations have circular dependencies. Follow this exact sequence:

### Step 1: Self-Employment Tax (Schedule C only)
```
SE income = net profit × 92.35%
SS tax = min(SE income, $184,500) × 12.4%
Medicare tax = SE income × 2.9%
Additional Medicare = max(0, SE income - threshold) × 0.9%
Total SE tax = SS tax + Medicare tax + Additional Medicare
SE deduction = (SS tax + Medicare tax) / 2   ← Additional Medicare NOT deductible
```

Thresholds: $200,000 single / $250,000 MFJ

### Step 1 (S-Corp variant): Payroll Tax
```
Employer SS = min(wages, $184,500) × 6.2%
Employer Medicare = wages × 1.45%
Employee SS = min(wages, $184,500) × 6.2%
Employee Medicare = wages × 1.45%
Additional Medicare = max(0, wages - threshold) × 0.9%
```

### Step 2: Adjusted Gross Income
```
Gross income = business income + other income
Above-the-line deductions:
  - SE tax deduction (Step 1, Schedule C only)
  - Retirement contributions (Solo 401(k), SEP, IRA)
  - HSA contributions
  - Self-employed health insurance
AGI = Gross income - above-the-line deductions
```

For S-Corp: business income = distributions (profit minus wages minus employer payroll tax)
W-2 wages also included in gross income.

### Step 3: QBI Deduction (Section 199A)
```
QBI = net business income - reasonable comp (S-Corp) OR net profit - SE deduction (Sched C)

If taxable income < $201,750 (single) / $403,500 (MFJ):
  QBID = 20% × QBI (full deduction)

If above threshold, apply limitations:
  - W-2 wage limit: greater of (50% × W-2 wages) or (25% × W-2 + 2.5% × UBIA)
  - SSTB phase-out if applicable
  - Phase-out range: $75,000 single / $150,000 MFJ (OBBBA expanded)

QBID cap = min(20% × QBI, W-2 wage limit if applicable)
Final QBID = min(QBID cap, 20% × taxable income before QBID)
```

### Step 4: Taxable Income & Federal Tax
```
Deduction = max(standard deduction, itemized deductions)
  Standard: $16,100 single / $32,200 MFJ
Taxable income = AGI - deduction - QBID
Federal income tax = apply 2026 brackets to taxable income
```

### Step 5: NIIT (Net Investment Income Tax)
```
If MAGI > $200,000 (single) / $250,000 (MFJ):
  NIIT = 3.8% × min(net investment income, MAGI - threshold)
```

### Step 6: State Income Tax
Load state brackets and rules from reference data. Account for:
- State standard deduction or itemized
- PTET election if applicable (and SALT cap implications)
- State-specific entity taxes (e.g., CA $800 LLC fee, CA S-Corp 1.5%)
- Local taxes (NYC, Philadelphia, etc.)

### Step 7: Total Tax Summary

## Output Format

### Chat Output
Present a summary table:

| Category | Amount |
|----------|--------|
| Gross Business Income | |
| SE Tax Deduction / Payroll Tax | |
| Retirement Contributions | |
| AGI | |
| QBI Deduction | |
| Taxable Income | |
| Federal Income Tax | |
| SE Tax / Payroll Tax (employee share) | |
| NIIT | |
| State Income Tax | |
| Local Tax | |
| **Total Tax Liability** | |
| **Effective Tax Rate** | |
| **Marginal Tax Rate** | |

### Excel Output
Create an Excel workbook with tabs:
1. **Summary** — the table above with formatting
2. **Federal Detail** — bracket-by-bracket calculation showing tax at each rate
3. **SE / Payroll** — full payroll tax breakdown
4. **QBI Worksheet** — QBI calculation with wage limit test
5. **State Tax** — state bracket calculation
6. **Assumptions** — all inputs and parameters used

Generate the workbook using a Python script via Bash (openpyxl). Apply currency formatting, bold headers, and highlight the total row.

## Reference Data

All 2026 tax parameters (federal brackets, state brackets, SE rates, QBID thresholds, retirement limits, SALT caps, NIIT thresholds) are in `references/tax-parameters.md`.

Read that file for any specific number. Do not guess or use outdated figures.

## Step 8: Actionable Recommendations

After presenting the tax summary, ALWAYS include a recommendations section. Analyze the estimate results and generate specific, dollar-quantified actions the client can take.

### What to Check

**Retirement Contribution Optimization:**
- Are they maximizing retirement contributions? If not, calculate the tax savings from contributing more.
- Show the specific dollar amount: "Contributing an additional $X to your Solo 401(k) would reduce your tax bill by $Y"
- If they said "maximize": confirm the max was applied and show the tax savings vs. contributing nothing

**Bracket Management:**
- What bracket are they in? How far are they from the next bracket boundary?
- "You're $X away from the [next]% bracket. An additional $X in deductions would keep you in the [current]% bracket, saving $Y."

**QBI Threshold Proximity:**
- If income is within $30K of the QBI phase-out threshold: flag it with specific guidance
- "Your taxable income is $X below the QBI phase-out. If income increases by more than $X, you'll begin losing the $Y QBI deduction."
- If above threshold: "You've exceeded the QBI phase-out. To recover the deduction, you'd need to reduce taxable income by $X through [specific strategies]."

**NIIT Exposure:**
- If MAGI is near or above $200K/$250K: quantify NIIT exposure
- "Your investment income of $X is subject to $Y in NIIT. Strategies to consider: [tax-loss harvesting, shifting to tax-exempt bonds, etc.]"

**Estimated Payment Schedule:**
- Calculate required quarterly estimated payments for the current year
- Base it on 110% safe harbor if AGI > $150K
- Provide the four quarterly amounts and due dates (April 15, June 15, Sept 15, Jan 15)
- If they were penalized last year: "To avoid the $X penalty you paid last year, make quarterly payments of $Y."

**HSA Opportunity:**
- If they have an HDHP but aren't maximizing HSA: quantify the triple tax benefit
- "You have $X of unused HSA contribution room. Contributing the full amount saves $Y in taxes this year, plus grows tax-free."

### Chat Output — Recommendations

After the summary table, add:

**What You Can Do:**

| Action | Tax Savings | Deadline |
|--------|-------------|----------|
| [Specific action 1] | $X,XXX | [Date] |
| [Specific action 2] | $X,XXX | [Date] |
| [Specific action 3] | $X,XXX | [Date] |

Then 1-2 sentences on the single highest-impact move.

### Excel Output — Recommendations Tab

Add a 7th tab to the workbook:
7. **Recommendations** — Each action, the before/after tax impact, and implementation notes

## Transcript Input Support

If the user provides data extracted from an IRS transcript (via the tax-review skill), accept all pre-populated fields without re-asking. The transcript data format is:

```
Extracted from [YEAR] IRS Transcript:
- Filing status: [status]
- W-2 wages: $[amount]
- Business income: $[amount]
- Capital gains: $[amount]
- Investment income: $[amount]
- State: [state]
- AGI: $[amount]
- Current retirement contributions: $[amount]
- HSA contributions: $[amount]
- Entity type: [type]
```

When receiving transcript data, use the prior year as baseline and model the CURRENT year estimate, asking only:
- "Has anything changed from last year?" (income, filing status, state, new business, etc.)
- "What assumptions should I use for this year's income?" (same, growth %, specific number)

## Important Notes

- Always show the SE tax deduction calculation explicitly — the additional Medicare tax (0.9%) is NOT included in the deductible portion
- For S-Corp, validate reasonable compensation against IRS factors before calculating
- SALT cap for 2026 is $40,400 (phases out for MAGI > $505,000)
- QBI phase-out ranges were expanded by OBBBA to $75K/$150K
- Always caveat: "This is an estimate for planning purposes. Consult a CPA for filing."
