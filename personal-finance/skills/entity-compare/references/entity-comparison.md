# Entity Comparison Reference

## S-Corp vs Schedule C: Detailed Rules

### How S-Corp Tax Savings Work

The fundamental S-Corp advantage is payroll tax savings on distributions:

```
Schedule C: ALL net profit subject to 15.3% SE tax (up to SS wage base)
S-Corp:     Only W-2 wages subject to payroll tax. Distributions are NOT subject to SE/payroll tax.
```

At $300,000 net profit with $100,000 in wages:
- Schedule C SE tax: ~$29,000 (12.4% SS on $184,500 + 2.9% Medicare on all + 0.9% Additional Medicare)
- S-Corp payroll tax: ~$15,300 (on $100,000 wages only)
- Savings: ~$13,700 in payroll tax

But this must be offset against S-Corp costs and QBI implications.

### Reasonable Compensation

The IRS requires S-Corp owner-employees to pay themselves "reasonable compensation" for services rendered. Key factors from IRS guidance and case law:

**IRS Factors (Revenue Ruling 74-44, augmented by case law):**
1. Training and experience
2. Duties and responsibilities
3. Time and effort devoted
4. Comparable wages for comparable services
5. Dividend history
6. Compensation agreements
7. Use of a compensation formula
8. Amount of net profit
9. Whether the employee controls when to distribute dividends
10. Whether the employee could get comparable pay elsewhere

**Key Court Cases:**
- **Watson v. Commissioner (2012)**: Accountant paying himself $24K on $200K+ profits was deemed unreasonable. Court upheld IRS assessment of $91,044 in reasonable comp.
- **Radtke v. United States (1990)**: Zero salary treated as wages; 100% of distributions reclassified.
- **Veterinary Surgical Consultants (2003)**: Court looked at revenue per shareholder to determine reasonable comp.

**Safe Harbor Approaches:**
1. **Percentage method**: 40-60% of net profit at lower incomes, declining percentage at higher incomes
2. **Comparable salary**: BLS wage data for the occupation + premium for ownership responsibilities
3. **2/7 Rule**: At high incomes above QBI threshold, optimal salary ≈ 2/7 (28.57%) of total business income
4. **Three-test approach**: Take the highest of (a) comparable salary, (b) percentage of revenue, (c) minimum viable (what you'd pay a replacement)

### The 2/7 Rule Derivation

When income is fully above the QBI phase-out and the W-2 wage limitation applies:

```
QBI deduction limited to: max(50% × W-2, 25% × W-2 + 2.5% × UBIA)

Assuming UBIA = 0 (service business with no significant property):
QBI deduction = 50% × W-2 wages

But QBI = Profit - W-2 wages
QBID = 20% × QBI = 20% × (Profit - W-2)

Setting constraint: 20% × (Profit - W-2) ≤ 50% × W-2
Solve: W-2 ≥ 2/7 × Profit

At W-2 = 2/7 × Profit:
QBID = 20% × (Profit - 2/7 × Profit) = 20% × 5/7 × Profit = 10/7 × Profit ÷ 5 = 2/14 × Profit
Wage limit = 50% × 2/7 × Profit = 1/7 × Profit
Check: 20% × 5/7 × Profit = 1/7 × Profit ✓ (they match at the optimal point)
```

### QBI Deduction Interaction

**Schedule C:**
- QBI = net profit - (SE tax deduction)
- No W-2 wage limitation issue below threshold
- Above threshold: limited because there are NO W-2 wages (unless you have employees)
- This is the major disadvantage of Schedule C at high incomes

**S-Corp:**
- QBI = net profit - W-2 wages paid to owner
- Above threshold: W-2 wage limitation applies but is satisfied by owner wages
- The 2/7 rule optimizes this balance

**SSTB Impact:**
- Below threshold: full 20% QBI deduction regardless of entity
- In phase-out: partial deduction, percentage decreases linearly
- Above phase-out: ZERO QBI deduction for SSTBs (regardless of entity)

For SSTBs above the full phase-out, entity choice is purely about payroll tax savings (no QBI benefit either way).

### S-Corp Administrative Costs

| Cost Item | Annual Range | Notes |
|-----------|-------------|-------|
| Payroll processing | $1,200-$3,000 | Gusto, ADP, or accountant |
| Tax preparation (1120-S + K-1) | $1,500-$3,000 | On top of personal return |
| Registered agent | $100-$300 | Required in most states |
| State annual report | $0-$800 | Varies by state |
| State entity taxes | $0-$5,000+ | CA: $800 min + 1.5% net income |
| Bookkeeping premium | $500-$2,000 | More complex books than Schedule C |
| **Total annual overhead** | **$3,300-$9,100** | |

Conservative estimate for comparison: $4,500/year for typical S-Corp admin costs.

### State-Specific Entity Rules

**California:**
- S-Corp: $800 minimum franchise tax + 1.5% of net income
- LLC (Schedule C): $800 annual tax + LLC fee based on gross receipts ($0-$11,790)
- PTET: available for S-Corps, NOT for SMLLCs filing Schedule C
- Impact: S-Corp entity tax partially offsets payroll tax savings

**New York:**
- S-Corp: filing fee $25-$4,500 based on NY gross income
- NYC: 3.876% unincorporated business tax on Schedule C filers (above $95K exemption)
- PTET: available for S-Corps
- Impact: NYC UBT makes S-Corp MORE attractive for NYC residents

**Texas:**
- No income tax
- Franchise tax: 0.375-0.75% of margin for revenue > $2.47M
- Most solo businesses are under the threshold
- Impact: No income tax advantage either way; entity choice is purely federal

**Florida / Nevada / Wyoming / Other no-income-tax states:**
- No state income tax
- Minimal entity fees
- Impact: Entity choice is purely about federal tax savings

### PTET Considerations

Pass-Through Entity Tax allows the entity to pay state tax at the entity level, generating a federal deduction that bypasses the SALT cap.

- Available to S-Corps in most states with income tax
- NOT available to Schedule C / sole proprietors (they're not pass-through entities)
- SMLLC PTET eligibility varies: available in CA, NY, NJ, CT, and others; NOT available in many states
- If PTET saves significant tax (income > $500K in high-tax state), this becomes a major factor favoring S-Corp

### Breakeven Analysis Framework

S-Corp is worth it when:
```
Payroll tax savings + PTET savings (if applicable) + QBI optimization
> S-Corp admin costs + state entity taxes + complexity cost
```

Typical breakeven points:
| Scenario | Breakeven Income |
|----------|-----------------|
| No-tax state, non-SSTB | ~$80,000-$100,000 |
| No-tax state, SSTB | ~$80,000-$100,000 |
| High-tax state, non-SSTB | ~$100,000-$120,000 |
| High-tax state with PTET benefit | ~$60,000-$80,000 |
| California (high entity costs) | ~$120,000-$150,000 |

### Social Security Trade-Off

Lower payroll taxes = lower Social Security credits.

- SS benefits based on highest 35 years of earnings (up to wage base)
- If the owner is already maxing SS credits through prior employment, this is irrelevant
- If early in career or few working years, consider the benefit reduction
- At high income levels, the marginal SS benefit per dollar of payroll tax is very low (diminishing returns above bend points)

For most business owners earning $150K+, the SS trade-off is minimal compared to the payroll tax savings.
