---
name: entity-compare
description: >
  Compare S-Corp vs Schedule C (sole proprietorship) tax treatment for a business owner.
  Use when the user asks to "compare entities", "S-Corp vs sole prop", "should I elect S-Corp",
  "entity comparison", "S-Corp savings", "is S-Corp worth it", "Schedule C vs S-Corp",
  "LLC vs S-Corp", "entity selection", or wants to understand the tax impact of choosing
  one business structure over another.
version: 0.1.0
---

# Entity Comparison: S-Corp vs Schedule C

Run a side-by-side tax comparison to determine whether S-Corp election saves money at the user's income level. Always output both chat tables AND an Excel workbook.

## Required Inputs

Gather from the user (ask if not provided):

- **Net business income** (profit before owner compensation)
- **Filing status**: single, mfj, mfs, hoh
- **State of residence**
- **Business type**: SSTB (specified service trade/business) or non-SSTB
- **Age** (for retirement contribution limits)
- **Other income** (W-2 from employer, investment income)
- **Planned retirement contributions** (or "maximize" flag)
- **Current or planned reasonable salary** (S-Corp — if unsure, calculate it)

## SSTB Classification

SSTBs include: health, law, accounting, actuarial, performing arts, consulting, athletics, financial services, brokerage, and any business where the principal asset is the reputation or skill of employees/owners.

**NOT SSTBs** (even though they seem like services): engineering, architecture, real estate, manufacturing, construction, retail, restaurants.

SSTB status matters because QBI deduction phases out completely for SSTBs above the threshold.

## Comparison Framework

### Scenario A: Schedule C (Sole Prop / SMLLC)

Calculate:
```
Net profit = business income
SE tax base = net profit × 92.35%
SE tax = SS portion + Medicare portion + Additional Medicare
SE deduction = (SS + base Medicare) / 2

QBI = net profit - SE deduction
QBID = apply 199A rules (no W-2 wage limit issue for Schedule C below threshold)

AGI = net profit - SE deduction - retirement contributions
Taxable income = AGI - deduction - QBID
Federal tax = apply brackets
State tax = apply state rules
NIIT = if applicable

Total tax = SE tax + federal tax + state tax + NIIT
```

Retirement contributions (Schedule C):
- Employee deferral: up to $24,500 (+ catch-up)
- Employer contribution: 20% of (net profit - SE deduction)
- Total cap: $72,000 (under 50)

### Scenario B: S-Corp

Calculate reasonable compensation first.

**Reasonable Compensation Methodology:**
1. Start with comparable salary data for the role/industry
2. Apply IRS factors: training, experience, duties, time spent, comparable wages
3. Safe harbors:
   - At minimum: 40-50% of net profit for profits under $200K
   - The 2/7 rule for high incomes above QBI threshold: wages = 2/7 × net profit
   - Floor: what you'd pay someone to do the work
   - Ceiling: entire net profit

```
W-2 wages = reasonable compensation
Employer payroll tax = (6.2% SS on wages up to $184,500) + (1.45% Medicare on all wages)
Business profit after wages = net profit - W-2 wages - employer payroll tax
Distribution = business profit after wages

Employee payroll tax = (6.2% SS) + (1.45% Medicare) + (0.9% Additional Medicare if over threshold)

QBI = net profit - W-2 wages
QBID = apply 199A rules with W-2 wage limitation test:
  - Standard: 20% × QBI
  - Wage limit: greater of (50% × W-2) or (25% × W-2 + 2.5% × UBIA)
  - SSTB reduction if in phase-out range

AGI = W-2 wages + distribution - retirement contributions
Taxable income = AGI - deduction - QBID
Federal tax = apply brackets
State tax = apply state rules (watch for entity-level taxes)
NIIT = if applicable

Total tax = employee payroll + employer payroll + federal + state + entity fees + NIIT
```

S-Corp retirement contributions:
- Employee deferral: up to $24,500 (+ catch-up)
- Employer contribution: up to 25% of W-2 wages
- Total cap: $72,000 (under 50)

### S-Corp Additional Costs
Include in the comparison:
- Payroll processing: ~$1,200-$3,000/year
- Additional tax preparation (1120-S): ~$1,500-$3,000/year
- State entity taxes: CA $800 min + 1.5% net income, NY filing fees, etc.
- Registered agent: ~$100-$300/year
- Reasonable compensation documentation: built into prep cost
- **Total administrative overhead**: typically $3,000-$6,000/year

## Side-by-Side Comparison

### Chat Output

**Summary Comparison:**

| | Schedule C | S-Corp | Difference |
|---|-----------|--------|------------|
| Net Business Income | | | |
| W-2 Wages | N/A | | |
| Self-Employment / Payroll Tax | | | |
| Federal Income Tax | | | |
| QBI Deduction | | | |
| State Income Tax | | | |
| Entity-Level Taxes / Fees | | | |
| NIIT | | | |
| **Total Tax** | | | |
| Admin Costs | ~$500 | ~$4,500 | |
| **Net Cost (Tax + Admin)** | | | |
| **Annual Savings from S-Corp** | | | |

**Breakeven Analysis:**
Show the income level where S-Corp savings exceed administrative costs. Typically $80,000-$120,000 net profit depending on state.

**QBI Impact Analysis:**
If income is near or above the QBI threshold, show:
- QBI deduction under each entity
- How the W-2 wage limitation affects S-Corp QBI
- Optimal wage level (2/7 rule if applicable)

**Recommendation:**
Based on the numbers, provide a clear recommendation:
- "At your income level, S-Corp saves approximately $X,XXX/year after admin costs."
- OR "At your income level, the savings don't justify the complexity. Stay on Schedule C."
- OR "You're at the breakeven point. S-Corp becomes clearly beneficial above $XXX,XXX."

**Multi-Year View:**
If income is growing, show when S-Corp becomes beneficial:

| Income Level | Schedule C Tax | S-Corp Tax | S-Corp Savings | Worth It? |
|-------------|---------------|------------|----------------|-----------|
| $100,000 | | | | |
| $150,000 | | | | |
| $200,000 | | | | |
| $300,000 | | | | |
| $500,000 | | | | |

### Excel Output
Create an Excel workbook with tabs:
1. **Comparison** — side-by-side summary (the main table)
2. **Schedule C Detail** — full tax calculation
3. **S-Corp Detail** — full tax calculation including payroll
4. **QBI Analysis** — QBI deduction under each entity with wage limitation test
5. **Breakeven** — chart data showing savings at different income levels
6. **Reasonable Comp** — salary analysis with IRS factors
7. **Assumptions** — all inputs and parameters

Generate the workbook using a Python script via Bash (openpyxl). Highlight the winning entity in green. Include a breakeven chart.

## State-Specific Considerations

Flag these state issues:
- **California**: $800 minimum franchise tax + 1.5% S-Corp tax on net income. SMLLC fee ($800+) based on gross receipts.
- **New York**: S-Corp filing fee based on NY receipts. NYC: additional 3.876% unincorporated business tax for Schedule C.
- **Texas**: No income tax but franchise tax applies to S-Corps with revenue > $2.47M.
- **Tennessee**: No income tax on earned income.
- **PTET eligibility**: S-Corp can elect PTET in most states; Schedule C/SMLLC eligibility varies by state. If PTET saves significant SALT, factor it in.

## Reference Data

Tax parameters in `references/tax-parameters.md`. Entity comparison details in `references/entity-comparison.md`.

## Implementation Roadmap

After the comparison, ALWAYS include a concrete implementation section if S-Corp is recommended or worth considering.

### If S-Corp is Recommended:

**Decision Summary:**
> Based on $[net income] in net business income, S-Corp election would save approximately $[savings]/year after admin costs of ~$[admin]. The payoff period is immediate / [X months].

**Step-by-Step Implementation:**

| Step | Action | Timeline | Cost |
|------|--------|----------|------|
| 1 | Form LLC (if not already) with state | 1-2 weeks | $[state fee] |
| 2 | File Form 2553 (S-Corp election) with IRS | Before March 15 or within 75 days of formation | $0 |
| 3 | Set up payroll service (Gusto, ADP, etc.) | 1 week | ~$[monthly cost]/mo |
| 4 | Open business bank account (if not already) | 1 day | $0 |
| 5 | Set reasonable compensation at $[amount]/year | Ongoing | Built into payroll |
| 6 | Engage CPA for 1120-S filing | Before year-end | ~$[prep cost] |

**Key Deadlines:**
- **March 15**: S-Corp election deadline for current tax year (Form 2553)
- **If past March 15**: Late election with reasonable cause, or plan for January 1 of next year
- **Quarterly**: Payroll tax deposits (Form 941)
- **March 15**: S-Corp tax return due (Form 1120-S), or extension to September 15

**What Changes Operationally:**
- Must run payroll at least quarterly (monthly recommended)
- Must file Form 1120-S annually (in addition to personal 1040)
- Must maintain corporate formalities (separate bank account, reasonable records)
- Distributions above salary must be documented

### If S-Corp is NOT Recommended (yet):

**Decision Summary:**
> At $[net income], the S-Corp savings of $[savings] don't exceed the ~$[admin] in annual admin costs. Stay on Schedule C for now.

**When to Revisit:**
> S-Corp becomes clearly beneficial when net profit consistently exceeds $[breakeven income]. If income is growing, plan to revisit when you're within $10-15K of that threshold.

**What to Do Instead:**
- Maximize retirement contributions (Solo 401(k) available on Schedule C too)
- Ensure you're claiming the QBI deduction
- Set up quarterly estimated payments to avoid penalties

## Transcript Input Support

If the user provides data extracted from an IRS transcript (via the tax-review skill), accept all pre-populated fields without re-asking. Use the prior year's Schedule C income as the baseline for comparison, and ask:
- "Is this year's business income expected to be similar, or should I model a different amount?"
- "Is your business an SSTB (service business like consulting, health, law, financial services)?"

## Important Notes

- S-Corp election deadline is March 15 (Form 2553). Late election possible with reasonable cause.
- The "savings" from S-Corp is primarily payroll tax savings on distributions — but those distributions don't earn Social Security credits either. Mention this trade-off.
- Reasonable compensation is the IRS's #1 audit trigger for S-Corps. Never recommend artificially low wages.
- Always caveat: "This comparison is for planning purposes. Consult a CPA before making entity elections."
