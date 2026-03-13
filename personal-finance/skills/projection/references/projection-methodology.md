# Projection Methodology

## Overview

Multi-year projections model deterministic (single-path) financial outcomes for business owners. Unlike Monte Carlo analysis, projections use fixed growth assumptions and show a single expected trajectory. They are best for understanding how income growth, tax brackets, retirement contributions, and net worth interact over a planning horizon.

## Projection Defaults

| Parameter | Default | Adjustable Range |
|-----------|---------|-----------------|
| Projection horizon | 5 years | 1-10 years |
| Income growth | 5% annually | 0-20% |
| Inflation | 2.5% | 1-5% |
| Expense growth | 3% | 1-8% |
| Investment return | 7% nominal | 3-12% |
| Tax bracket inflation | 2.5% | 1-4% |

## Income Modeling

### Default: Constant Growth
```
Income(year) = Income(base) × (1 + growth_rate)^(year - base_year)
```

### Custom Growth Schedules
Users may specify:
- Different rates for different years (e.g., 10% year 1-2, then 5%)
- Specific income targets for specific years
- Step-function income (e.g., income jumps when a contract starts)
- Income plateau (growth stops at a ceiling)

## Tax Bracket Treatment for Future Years

**Conservative approach (recommended):** Use 2026 brackets for all projection years. This avoids speculating on future legislation and provides a worst-case baseline.

**Inflation-adjusted approach:** Increase bracket thresholds by the assumed inflation rate annually. This better models real purchasing power but introduces assumption risk.

Always note which approach is being used and why.

## Key Threshold Tracking

The most valuable insight from a projection is when income crosses a threshold that changes the tax calculus. Track these:

### QBI Thresholds (2026)
| Filing Status | Full Deduction Below | Phase-Out Starts | Phase-Out Ends |
|--------------|---------------------|-----------------|----------------|
| Single | $201,750 | $201,750 | $276,750 |
| MFJ | $403,500 | $403,500 | $553,500 |

When income enters the phase-out zone, the marginal tax rate spikes because each additional dollar reduces the QBI deduction AND is taxed at the regular rate. For SSTBs, crossing the upper threshold eliminates QBID entirely.

### Additional Medicare Threshold
$200,000 single / $250,000 MFJ — adds 0.9% on earned income above this level.

### NIIT Threshold
$200,000 single / $250,000 MFJ — adds 3.8% on net investment income.

### Social Security Wage Base
$184,500 for 2026 — earnings above this are exempt from the 12.4% SS tax (but not Medicare).

### SALT Deduction Phase-Out
$505,000 MAGI — the $40,400 SALT cap starts phasing down.

### Top Federal Bracket
$640,601 single / $768,701 MFJ — income above this is taxed at 37%.

## Retirement Contribution Optimization

### "Maximize" Mode

When the user wants to maximize retirement savings, calculate the highest allowed contribution each year:

**Solo 401(k) (Schedule C):**
```
Net SE income = business profit × 92.35% - (SE tax / 2)
Max employer = 20% × net SE income (capped at $72,000 total - employee deferral)
Max employee = $24,500 + catch-up
Total max = min(employee + employer, annual limit)
```

**Solo 401(k) (S-Corp):**
```
Max employer = 25% × W-2 wages (capped at $72,000 total - employee deferral)
Max employee = $24,500 + catch-up
Total max = min(employee + employer, annual limit)
```

Annual limits by age (2026):
| Age | Employee | Catch-Up | Employer Max | Total Max |
|-----|----------|----------|-------------|-----------|
| Under 50 | $24,500 | $0 | up to $47,500 | $72,000 |
| 50-59 | $24,500 | $8,000 | up to $47,500 | $80,000 |
| 60-63 | $24,500 | $11,250 | up to $47,500 | $83,250 |
| 64+ | $24,500 | $8,000 | up to $47,500 | $80,000 |

**HSA (if eligible):**
$4,400 individual / $8,750 family + $1,000 catch-up at 55+

### Cash Balance Plan Stacking (High Income)
For incomes above $400K, note the option to add a cash balance plan:
- Additional $60K-$350K+ depending on age
- Requires 3-5 year commitment
- Setup cost $1,500-$3,000, annual admin $1,500-$7,000
- Best for sustained high earners age 45+

## Net Worth Accumulation

### Simple Growth Model
```
Beginning balance = prior year ending balance
+ New contributions (retirement + taxable)
× (1 + return rate)
- Withdrawals (if any)
= Ending balance
```

For more accuracy, apply the mid-year convention:
```
Ending = Beginning × (1 + return) + contributions × (1 + return/2)
```

### Account Type Tracking
Track growth separately by account type:
- **Pre-tax (401k, traditional IRA)**: contributions reduce current tax, taxed as ordinary income on withdrawal
- **Roth**: no current deduction, tax-free growth and withdrawal
- **Taxable**: no deduction, but favorable capital gains rates
- **HSA**: triple tax benefit (deduction + tax-free growth + tax-free withdrawal for medical)

## Output Structure

### Year-by-Year Table (required)
One row per metric, one column per year. Include:
- Business income
- W-2 wages (S-Corp)
- Retirement contributions (by type)
- Federal tax
- SE/payroll tax
- State tax
- NIIT
- Total tax
- Effective rate
- After-tax income
- Living expenses
- Net savings
- Ending portfolio
- Ending net worth

### Threshold Alert Callouts
For each year where a threshold is crossed, generate a callout:
```
⚠️ Year 3: Income of $215,000 enters QBI phase-out zone.
   QBI deduction reduced from $40,000 to $32,000.
   Marginal impact: $1,600 additional tax.
```

### Cumulative Summary
At the end, show:
- Total taxes paid over projection period
- Total retirement contributions
- Net worth growth (beginning to end)
- Average effective tax rate
- Cumulative savings from entity choice (if S-Corp)
