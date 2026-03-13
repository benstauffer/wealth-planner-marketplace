---
name: estimate
description: >
  Calculate a complete federal and state tax liability estimate for a business owner.
  Use when the user asks to "estimate my taxes", "calculate tax liability", "what do I owe",
  "run a tax estimate", "how much in taxes", "tax bill", or provides business income and
  wants to know their total tax burden including self-employment tax, income tax, QBID, NIIT,
  and state taxes.
version: 0.2.0
---

# Tax Estimate for Business Owners

Produce a comprehensive tax liability estimate. Output all results as formatted tables with
every intermediate calculation shown — no skipping steps.

## Required Inputs

Gather ALL of the following before calculating. Ask for any missing items — do not assume or skip.

### Identity & Structure
- **Filing status**: single, mfj, mfs, hoh
- **Age** (owner's age — determines retirement catch-up eligibility at 50+, 60-63 super catch-up, HSA catch-up at 55+)
- **Entity type**: Schedule C (sole prop / SMLLC) or S-Corp
- **State of residence**
- **Filing year**: default 2026
- **Business type**: SSTB or non-SSTB (ask: "Is your business in consulting, law, health, finance, or other professional services?" — affects QBI deduction above threshold)

### Income
- **Net business income** (profit after ordinary business expenses, before owner compensation)
- **W-2 wages paid to yourself** (S-Corp only — if not yet set, calculate reasonable comp below)
- **W-2 wages from an employer** (if any — separate from S-Corp self-wages)
- **Short-term capital gains** (held ≤ 1 year — taxed as ordinary income)
- **Long-term capital gains** (held > 1 year — preferential rates)
- **Qualified dividends** (taxed at LTCG rates)
- **Ordinary dividends** (taxed as ordinary income)
- **Interest income** (taxed as ordinary income)
- **Rental income, net of expenses** (if any)
- **Other income** (1099-NEC side work, alimony received pre-2019, etc.)

### Deductions & Adjustments
- **Retirement contributions**: specify type and amount (Solo 401(k) employee deferral, employer contribution, SEP-IRA, traditional IRA, Roth IRA — Roth does NOT reduce taxable income)
- **Self-employed health insurance premiums** (monthly premium × 12 if paying out of pocket or through S-Corp)
- **HSA contributions**: amount contributed + coverage type (self-only or family HDHP)
- **Itemized deductions** (if potentially above standard): mortgage interest, state/local taxes paid, charitable contributions, medical expenses above 7.5% AGI

### Payments Already Made
- **Estimated tax payments** made so far this year (for balance due calculation)
- **W-2 withholding** from any employer wages (for balance due calculation)
- **Prior year total federal tax** (for safe harbor estimated payment calculation — 110% if AGI > $150K)

---

## Calculation Order

Tax calculations have circular dependencies. Follow this exact sequence and show every intermediate value.

### Step 1A: Self-Employment Tax (Schedule C only)
```
SE income         = net profit × 92.35%
SS tax            = min(SE income, $184,500) × 12.4%
Medicare tax      = SE income × 2.9%
Additional Med    = max(0, SE income − threshold) × 0.9%
                    [threshold: $200,000 single / $250,000 MFJ]
Total SE tax      = SS tax + Medicare tax + Additional Medicare
SE deduction      = (SS tax + Medicare tax) / 2
                    ← Additional Medicare is NOT deductible
```

### Step 1B: Payroll Tax (S-Corp only)
```
Employer SS       = min(W-2 wages, $184,500) × 6.2%
Employer Medicare = W-2 wages × 1.45%
Employer total    = Employer SS + Employer Medicare

Employee SS       = min(W-2 wages, $184,500) × 6.2%
Employee Medicare = W-2 wages × 1.45%
Additional Med    = max(0, W-2 wages − threshold) × 0.9%
Employee total    = Employee SS + Employee Medicare + Additional Med

S-Corp distribution = net profit − W-2 wages − Employer total
```

**S-Corp health insurance note:** If the S-Corp pays owner health insurance premiums,
those premiums are added to W-2 Box 1 (income tax wages) but NOT Box 3/5 (FICA wages).
This means: income tax is calculated on wages + premiums, but payroll tax is only on wages.
The owner then deducts the premiums above-the-line as self-employed health insurance.
Net effect on income tax = zero, but correct treatment matters for the payroll tax savings calculation.

### Step 2: Gross Income
```
Schedule C:
  Gross income = net profit + employer W-2 wages + STCG + LTCG + QD
                 + ordinary dividends + interest + rental income + other

S-Corp:
  Gross income = W-2 wages + health insurance premiums (if in W-2 box 1)
                 + distribution + employer W-2 wages (if any)
                 + STCG + LTCG + QD + ordinary dividends + interest
                 + rental income + other
```

### Step 3: Adjusted Gross Income
```
Above-the-line deductions:
  Schedule C:   SE deduction (Step 1A)
  S-Corp:       (no SE deduction)
  Both:         Solo 401(k) / SEP-IRA / traditional IRA deduction
                Self-employed health insurance premiums
                HSA contributions (within annual limit)

AGI = Gross income − above-the-line deductions
```

HSA limits (2026): $4,400 self-only / $8,750 family / +$1,000 catch-up age 55+
IRA deduction phases out for active plan participants — check phase-out range in tax-parameters.md.

### Step 4: Capital Gains Classification
```
Ordinary income  = AGI − LTCG − QD  (i.e., AGI minus preferential-rate income)

LTCG + QD are taxed at preferential rates — do NOT apply regular brackets to them.
They stack on TOP of ordinary income for rate determination:

  0% rate applies to LTCG/QD up to: [0% threshold from tax-parameters.md] − ordinary_taxable_income
  15% rate applies to LTCG/QD above 0% zone, up to: [15% threshold from tax-parameters.md]
  20% rate applies to LTCG/QD above the 15% threshold

STCG is ordinary income — included in brackets, not separated here.
```

Always show the split: how much LTCG/QD falls in each rate bucket.

### Step 5: QBI Deduction (Section 199A)
```
QBI base:
  Schedule C:  net profit − SE deduction
  S-Corp:      net profit − W-2 wages − employer payroll tax

Threshold check (use taxable income BEFORE QBI deduction):
  Tentative taxable income = AGI − max(standard, itemized)

If tentative taxable income ≤ $201,750 single / $403,500 MFJ:
  QBID = min(20% × QBI, 20% × tentative taxable income)   [full deduction]

If above threshold, enter phase-out range ($75,000 single / $150,000 MFJ wide):
  Apply W-2 wage limitation: greater of (50% × W-2) or (25% × W-2 + 2.5% × UBIA)
    UBIA = unadjusted basis of qualified property — default 0 for service businesses
  If SSTB: phase-out reduces QBI and W-2 limit proportionally; zero above phase-out top
  QBID = min(20% × QBI, W-2 wage limit) × phase-out percentage
  Final QBID = min(result, 20% × tentative taxable income)
```

**State QBID conformity:** Several states do NOT allow the federal QBI deduction on the state return.
Flag this for the user:
- California: no QBID — compute state tax WITHOUT the deduction
- Massachusetts: no QBID
- Connecticut: no QBID
- All other states: check tax-parameters.md for conformity status

### Step 6: Taxable Income & Federal Tax
```
Itemized deductions note: SALT cap = $40,400 (phases out MAGI > $505,000)
Deduction         = max(standard deduction, itemized)
  Standard 2026:  $16,100 single / $32,200 MFJ

Ordinary taxable income = AGI − deduction − QBID − LTCG − QD
  [back out LTCG/QD so regular brackets apply only to ordinary income]

Federal income tax on ordinary income = apply 2026 brackets to ordinary taxable income
Federal tax on LTCG/QD               = apply preferential rates from Step 4
Total federal income tax              = ordinary tax + LTCG/QD tax
```

### Step 7: NIIT (Net Investment Income Tax)
```
If MAGI > $200,000 single / $250,000 MFJ:
  NII = LTCG + QD + ordinary dividends + interest + net rental income
  NIIT = 3.8% × min(NII, MAGI − threshold)
```

### Step 8: State Income Tax
Load state brackets and rules from tax-parameters.md. Account for:
- State standard deduction (many states differ from federal)
- QBID conformity (Step 5 — do not apply if state doesn't conform)
- PTET election if applicable (deducted at entity level, reduces federal SALT exposure)
- State-specific entity taxes: CA $800 min franchise + 1.5% S-Corp net income; NY filing fees; etc.
- Local taxes: NYC 3.876% UBT on Schedule C, Philadelphia BIRT, etc.
- State capital gains rates (most states tax LTCG as ordinary income — no preferential rate)

### Step 9: Total Tax Summary

---

## Output Format

First show the calculation trace — every step labeled with its intermediate values.
Then present the summary table.

### Calculation Trace (required — show before summary table)

```
STEP 1: [SE Tax or Payroll Tax]
  [Show each line of the formula with actual numbers]

STEP 2-3: Gross Income → AGI
  [Show each income item added, each deduction subtracted]

STEP 4: Capital Gains Split
  [Show LTCG/QD rate buckets with amounts]

STEP 5: QBI
  [Show QBI base, threshold check, any wage limitation applied]

STEP 6: Taxable Income
  [Show deduction used, ordinary taxable income, LTCG/QD separation]

STEP 7-8: NIIT + State
  [Show NIIT calc if applicable; state brackets applied]
```

### Summary Table

| Category | Amount |
|----------|--------|
| Gross Business Income | |
| W-2 Wages (S-Corp) / SE Tax Deduction (Sched C) | |
| Other Income (W-2, interest, dividends, STCG) | |
| Long-Term Capital Gains + Qualified Dividends | |
| Retirement Contributions | |
| Health Insurance Deduction | |
| HSA Deduction | |
| **AGI** | |
| Standard / Itemized Deduction | |
| QBI Deduction | |
| **Ordinary Taxable Income** | |
| Federal Tax (ordinary brackets) | |
| Federal Tax (LTCG/QD preferential rates) | |
| SE Tax / Payroll Tax (total) | |
| NIIT | |
| State Income Tax | |
| State Entity Tax / Local Tax | |
| **Total Tax Liability** | |
| Withholding + Estimated Payments | |
| **Balance Due / (Refund)** | |
| **Effective Tax Rate** | |
| **Marginal Ordinary Rate** | |
| **Marginal LTCG Rate** | |

---

## Reference Data

All 2026 tax parameters (federal brackets, LTCG rate thresholds, state brackets, SE rates,
QBID thresholds, retirement limits, HSA limits, SALT caps, NIIT thresholds, state QBID
conformity) are in `../../references/tax-parameters.md`.

Read that file for every specific number. Do not guess or use figures from memory.

---

## Step 10: Actionable Recommendations

After the summary table, ALWAYS include a recommendations section with specific dollar-quantified actions.

**Retirement Optimization:**
- Are they at the contribution max? Show tax savings from contributing more.
- Age 50+: flag catch-up eligibility ($8,000 extra employee deferral)
- Age 60-63: flag super catch-up ($11,250 extra under SECURE 2.0)
- S-Corp: employer contribution limit is 25% of W-2 wages — show if there's room

**Capital Gains Strategy:**
- If significant STCG: "Holding until 1-year mark would change the rate from [X]% to [Y]%, saving $Z"
- If LTCG is pushing into 20% territory: flag tax-loss harvesting, installment sale options
- If LTCG/QD is in the 0% bucket: flag opportunity to realize more gains tax-free

**Bracket Management:**
- How far from the next bracket boundary?
- How far from the QBI phase-out threshold?
- Additional deductions (retirement, HSA) that would pull income below a boundary

**NIIT Exposure:**
- Quantify if MAGI is near or above threshold
- Strategies: Roth conversion timing, tax-exempt bonds, harvesting losses

**HSA:**
- If HDHP and not maxed: show full triple-tax benefit in dollars

**Estimated Payments:**
- Safe harbor: 100% of prior year tax (110% if prior AGI > $150K)
- Calculate quarterly amounts and due dates: Apr 15 / Jun 15 / Sep 15 / Jan 15
- Show balance due if payments already made

### Recommendations Table

| Action | Tax Savings | Deadline |
|--------|-------------|----------|
| [Specific action] | $X,XXX | [Date] |

---

## Transcript Input Support

If the user provides data from a tax-review transcript extraction, accept all pre-populated
fields without re-asking. Ask only:
- "Has anything changed from last year?"
- "What income should I assume for this year?"

Transcript format:
```
Extracted from [YEAR] IRS Transcript:
- Filing status: [status]
- W-2 wages: $[amount]
- Business income: $[amount]
- Short-term capital gains: $[amount]
- Long-term capital gains: $[amount]
- Qualified dividends: $[amount]
- Ordinary dividends + interest: $[amount]
- State: [state]
- AGI: $[amount]
- Retirement contributions: $[amount]
- HSA contributions: $[amount]
- Health insurance premiums: $[amount]
- Entity type: [type]
- Prior year total tax: $[amount]
```

---

## Important Notes

- Additional Medicare (0.9%) is NOT deductible — only the base SE tax halves are
- For S-Corp, validate reasonable comp before calculating — it's the #1 audit trigger
- SALT cap 2026: $40,400 (phases out MAGI > $505,000)
- QBI phase-out range expanded by OBBBA: $75K wide (single) / $150K wide (MFJ)
- QBI deduction is now permanent under OBBBA
- State capital gains: most states tax at ordinary rates — do not apply federal preferential rates to state calc unless state-specific rules say otherwise
- Always caveat: "This is an estimate for planning purposes. Consult a CPA for filing."
