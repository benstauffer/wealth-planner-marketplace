---
name: projection
description: >
  Build multi-year tax and cash flow projections for business owners. Use when
  the user asks for "5-year projection", "tax projection", "cash flow forecast",
  "multi-year model", "income projection", "net worth projection", "how will my
  taxes change", "project my finances", or wants to model income growth, tax
  liability, savings, and net worth over 3-10 years.
version: 0.1.0
---

# Multi-Year Projection Model

Build a year-by-year financial projection covering business income, taxes, retirement savings, and net worth accumulation. Default to 5 years. Always output both chat tables AND an Excel workbook.

## Required Inputs

Gather from the user (ask if not provided):

- **Current year business income** (net profit)
- **Filing status**: single, mfj, mfs, hoh
- **Entity type**: Schedule C or S-Corp
- **State of residence**
- **Age** (for retirement contribution limits and catch-up eligibility)
- **Projection horizon**: default 5 years (allow 1-10)

### Growth & Inflation Assumptions (use defaults if not provided)
- **Income growth rate**: default 5% annually
- **Inflation rate**: default 2.5%
- **Expense growth rate**: default 3%
- **Investment return**: default 7% nominal (for net worth accumulation)

### Current Financial Position (for net worth tracking)
- **Current investable assets** (retirement accounts, brokerage, savings)
- **Current retirement account balances** (by type: 401k, IRA, Roth, taxable)
- **Annual living expenses**
- **Annual retirement contributions** (or "maximize" flag)

## Projection Engine

For each year in the projection:

### Step 1: Project Business Income
```
Year N income = Year (N-1) income × (1 + growth rate)
```

Allow the user to specify different growth rates per year or income targets for specific years.

### Step 2: Optimize Retirement Contributions
If "maximize" is set:
- Calculate max Solo 401(k) employee deferral ($24,500 base + catch-up if eligible)
- Calculate max employer contribution (25% of W-2 for S-Corp, or 20% of net SE income for Schedule C after SE deduction)
- Apply total annual limit ($72,000 under 50, $80,000 age 50-59, $83,250 age 60-63)
- Include HSA if eligible ($4,400 individual / $8,750 family + $1,000 catch-up 55+)

### Step 3: Run Tax Estimate
Use the estimate skill's calculation methodology for each year:
- Adjust brackets for inflation (use 2.5% annual bracket inflation as proxy, or use actual 2026 brackets for all years as conservative approach)
- Calculate SE tax / payroll tax
- Calculate AGI after retirement deductions
- Apply QBI deduction (check if income crosses threshold boundaries year-over-year)
- Calculate federal income tax
- Calculate NIIT if applicable
- Calculate state income tax

### Step 4: Cash Flow
```
After-tax income = business income - total taxes - retirement contributions
Discretionary cash flow = after-tax income - living expenses
Savings rate = discretionary cash flow / business income
```

### Step 5: Net Worth Accumulation
```
Beginning portfolio = prior year ending portfolio
+ Retirement contributions (tax-advantaged)
+ After-tax savings (taxable account)
+ Investment returns (apply return rate to beginning balance + 50% of new contributions)
= Ending portfolio

Net worth = ending portfolio + other assets - liabilities
```

### Step 6: Key Threshold Tracking
Flag when income crosses critical thresholds:
- QBI full deduction threshold ($201,750 / $403,500)
- QBI phase-out completion ($276,750 / $553,500)
- SSTB QBI cliff (if applicable)
- Additional Medicare threshold ($200,000 / $250,000)
- NIIT threshold ($200,000 / $250,000)
- SALT phase-out ($505,000 MAGI)
- Top federal bracket ($640,601 / $768,701)
- Social Security wage base ($184,500)

## Output Format

### Chat Output

**Year-by-Year Summary Table:**

| | Year 1 | Year 2 | Year 3 | Year 4 | Year 5 |
|---|--------|--------|--------|--------|--------|
| Business Income | | | | | |
| W-2 Wages (S-Corp) | | | | | |
| Retirement Contributions | | | | | |
| Federal Income Tax | | | | | |
| SE / Payroll Tax | | | | | |
| State Tax | | | | | |
| **Total Tax** | | | | | |
| **Effective Rate** | | | | | |
| After-Tax Income | | | | | |
| Living Expenses | | | | | |
| Net Savings | | | | | |
| **Ending Net Worth** | | | | | |

**Threshold Alerts:** Call out any year where income crosses a key threshold and what changes as a result.

**5-Year Totals:**
- Total taxes paid
- Total retirement contributions
- Total net worth growth
- Average effective tax rate

### Excel Output
Create an Excel workbook with tabs:
1. **Dashboard** — summary table above + key metrics
2. **Year-by-Year Detail** — full calculation for each year (one column per year)
3. **Tax Detail** — bracket-by-bracket breakdown per year
4. **Retirement** — contribution calculations and account growth
5. **Net Worth** — portfolio accumulation with beginning/ending balances
6. **Assumptions** — all inputs, growth rates, and parameters
7. **Threshold Map** — shows each threshold and which year it's crossed

Generate the workbook using a Python script via Bash (openpyxl). Apply conditional formatting to highlight threshold crossings. Include simple charts for income growth, tax burden, and net worth trajectory.

## Reference Data

Tax parameters are in `references/tax-parameters.md`. Projection methodology details are in `references/projection-methodology.md`.

## Step 7: Inflection Point Actions

After the projection, ALWAYS analyze threshold crossings and provide specific, actionable guidance for each year.

### Threshold Action Map

For each threshold crossed during the projection, present:

| Year | Threshold Crossed | Dollar Impact | Recommended Action | Deadline |
|------|-------------------|--------------|-------------------|----------|
| [Year] | [Threshold] | +$[additional tax] | [Specific action] | [When to act] |

### Common Inflection Points and What to Do

**QBI Phase-Out ($201,750 single / $403,500 MFJ):**
- Quantify the lost deduction in dollars
- Action: "Increase retirement contributions by $[X] in Year [N] to stay below the threshold" or "If growth makes staying under impractical, shift focus to maximizing retirement and [other strategies]"

**NIIT Threshold ($200K / $250K):**
- Quantify the additional 3.8% tax on investment income
- Action: "Before Year [N], consider shifting taxable investments to Roth, tax-exempt bonds, or harvesting losses"

**Federal Bracket Jumps:**
- Show the marginal rate increase and dollar impact
- Action: "Maximizing deductions becomes [X]% more valuable starting Year [N]"

**Retirement Catch-Up Eligibility (age 50, 60-63):**
- Flag the year and the additional contribution room
- Action: "Plan to increase 401(k) contributions by $[X] starting January of Year [N]"

**S-Corp Breakeven (if on Schedule C):**
- If income growth crosses the S-Corp breakeven point
- Action: "Year [N] is when S-Corp election starts saving money. File Form 2553 by March 15 of that year."

### Chat Output — Year-by-Year Action Items

After the projection table, always add:

**Key Actions by Year:**

**Year 1 ([YEAR]):** [Highest-impact action with dollar amount]
**Year 2:** [Action or "No threshold crossings — stay the course"]
**Year 3:** [Proactive preparation for upcoming thresholds]
...

**Biggest Opportunity Over [N] Years:**
> The single highest-impact move across this projection is [specific action], which saves approximately $[total cumulative savings] in taxes over [N] years.

**Cumulative Impact of All Recommendations:**
> Implementing all recommended actions saves an estimated $[total] over [N] years compared to maintaining the status quo.

### Excel Output — Action Plan Tab

Add an 8th tab:
8. **Action Plan** — Year-by-year recommended actions, threshold crossings, dollar impacts, and deadlines. Color-code: red = act this year, yellow = next 1-2 years, green = plan ahead.

## Transcript Input Support

If the user provides data from an IRS transcript (via the tax-review skill), accept all pre-populated fields as the Year 1 baseline. Ask only:
- "What income growth rate should I assume? (default: 5% annually)"
- "Should I maximize retirement contributions in the projection, or use a specific amount?"
- "What are your approximate annual living expenses?"
- "How old are you? (for retirement limit calculations)"

## Important Notes

- For projections beyond 2026, note that tax parameters may change. Use 2026 rates as baseline with inflation adjustments, and caveat that future legislation could alter results.
- The QBI deduction is now permanent under OBBBA, so it's safe to project forward.
- If income growth pushes someone across the QBI phase-out, highlight the marginal impact — this is often the most valuable insight.
- Always caveat: "Projections are based on stated assumptions. Actual results will vary with income changes, legislation, and market performance."
