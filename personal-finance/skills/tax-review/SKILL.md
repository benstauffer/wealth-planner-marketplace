---
name: tax-review
description: >
  Analyze an IRS transcript to produce a client-ready tax situation summary, identify missed
  opportunities and optimization strategies, and prepare data for running estimates and projections.
  Use when the user uploads an IRS transcript, asks to "review my taxes", "analyze my return",
  "what am I missing", "tax review", "transcript analysis", "tax opportunities", "tax checkup",
  "look at my transcript", or wants a professional assessment of a client's prior-year filing
  with actionable next steps.
version: 0.1.0
---

# IRS Transcript Tax Review

Parse an uploaded IRS transcript (Form 1040 Record of Account), extract all relevant financial data, produce a client-ready situation summary, and deliver prioritized actionable recommendations. This is the entry point for new client engagements — it feeds directly into the estimate, entity-compare, and projection skills.

## Step 0: Read the Transcript

Use pdfplumber or pypdf to extract text from the uploaded PDF. IRS transcripts follow a consistent format. Extract ALL of the following fields by parsing the text line by line.

### Fields to Extract

**Header / Account Info:**
- Tax period ending (year)
- Filing status
- Account balance (amount owed or refund)
- Accrued interest and penalty
- Processing date

**Income (from "Information from the return" section):**
- Total wages / Form W-2 wages
- Taxable interest income
- Ordinary dividend income
- Qualified dividends
- Business income or loss (Schedule C)
- Capital gain or loss (Schedule D)
- Rent/royalty/partnership/estate (Schedule E)
- Partnership/S-Corp income/loss
- Farm income or loss (Schedule F)
- Total IRA distributions / taxable IRA distributions
- Total pensions and annuities / taxable amount
- Unemployment compensation
- Social Security benefits / taxable amount
- Other income
- **Total income**

**Adjustments:**
- HSA deduction
- Self-employment tax deduction
- Keogh/SEP contribution deduction
- Self-employment health insurance deduction
- IRA deduction
- Student loan interest deduction
- Total adjustments
- **Adjusted gross income (AGI)**

**Tax & Credits:**
- Standard deduction (per computer)
- Taxable income
- Tentative tax
- Alternative minimum tax (Form 6251)
- Foreign tax credit
- Child & dependent care credit
- Education credit
- Retirement savings contribution credit
- Child and other dependent credit
- Residential clean energy credit
- Total credits
- Income tax after credits

**Other Taxes:**
- Self-employment tax
- Additional Medicare tax (Form 8959)
- Net investment income tax (Form 8960)
- Total tax liability

**Payments:**
- Federal income tax withheld
- Estimated tax payments
- Earned income credit
- Additional child tax credit
- Total payments
- Amount owed or overpayment

**Penalty Info:**
- Estimated tax penalty amount

**Schedule D (if present):**
- Net short-term gain/loss
- Short-term sales amount and cost basis
- Net long-term gain/loss
- Long-term sales amount and cost basis

**Form 8889 / HSA (if present):**
- High deductible health plan indicator (self-only or family)
- HSA contributions
- Employer HSA contributions
- HSA contributions limit
- HSA deduction amount
- Taxable HSA distributions

**Schedule C (if present):**
- Gross receipts
- Net profit/loss

**QBI:**
- Qualified business income deduction

## Step 1: Client Situation Summary

Present a clean, professional summary. This is the "here's where you stand" overview.

### Chat Output — Situation Summary

**Tax Year [YEAR] Summary for [FIRST NAME]**

| Category | Amount |
|----------|--------|
| **Income** | |
| W-2 Wages | |
| Business Income (Sched C) | |
| Capital Gains (Short-Term) | |
| Capital Gains (Long-Term) | |
| Investment Income (Interest + Dividends) | |
| Other Income | |
| **Total Income** | |
| | |
| **Deductions & Adjustments** | |
| Standard / Itemized Deduction | |
| HSA Deduction | |
| Retirement Contributions | |
| SE Tax Deduction | |
| Other Above-the-Line | |
| QBI Deduction | |
| | |
| **Tax** | |
| Federal Income Tax | |
| Self-Employment Tax | |
| Additional Medicare Tax | |
| Net Investment Income Tax | |
| **Total Federal Tax** | |
| | |
| **Effective Federal Rate** | |
| **Marginal Federal Bracket** | |
| | |
| **Payments & Balance** | |
| Withholding | |
| Estimated Payments | |
| Amount Owed / (Refund) | |
| Underpayment Penalty | |

After the table, provide 2-3 sentences of plain-English context:
- Where the client's income sits relative to key thresholds (QBI phase-out, NIIT, bracket boundaries)
- Whether they owed or got a refund and why
- Any notable patterns (heavy short-term trading, no retirement savings, etc.)

## Step 2: Opportunity Analysis

This is the core value. Systematically check every optimization lever and flag what's relevant to this client.

### Opportunity Checklist

Run through each category below. For each finding, rate it:
- **High Impact** — saves $1,000+ or is a major structural change
- **Medium Impact** — saves $200-$1,000 or is a meaningful behavioral change
- **Low Impact** — saves under $200 but worth noting

Skip categories that clearly don't apply (e.g., don't discuss S-Corp election for someone with no business income).

#### A. Retirement Contributions
Check:
- Were any retirement contributions made? (IRA deduction, Keogh/SEP, HSA deduction fields)
- If none: calculate tax savings from maxing out available options based on their income sources
- If some: calculate remaining room and incremental tax savings
- Is the client eligible for Solo 401(k), SEP-IRA, traditional IRA, Roth IRA based on income type?
- For business owners: calculate max Solo 401(k) based on their net profit
- For W-2 employees: note that employer 401(k) contributions don't appear on transcript — ask if they're contributing

**Output format for each finding:**
> **[HIGH/MEDIUM/LOW IMPACT] — [Title]**
> What the transcript shows: [observation]
> What's available: [the opportunity]
> Potential tax savings: $X,XXX (show the calculation)
> Action required: [specific steps and deadlines]

#### B. HSA Optimization
Check:
- Is there a Form 8889? (indicates HDHP eligibility)
- Compare actual contributions vs. limit ($4,400 individual / $8,750 family for 2026, + $1,000 catch-up at 55+)
- Factor in employer contributions to calculate remaining personal contribution room
- If no Form 8889 but client could qualify: flag as potential opportunity
- HSA is triple tax advantaged — quantify the full benefit (deduction + tax-free growth + tax-free qualified withdrawals)

#### C. Capital Gains Strategy
Check:
- Ratio of short-term vs long-term gains — quantify the tax cost of short-term treatment
- Calculate what the tax would have been if short-term gains were instead long-term (show the spread)
- Total trading volume vs. net gains — high volume with modest gains suggests churn or poor risk/reward
- Wash sale adjustments present? (appears in "basis adjustments" on Schedule D)
- If significant capital gains: flag tax-loss harvesting as a strategy for current year
- Are capital gains pushing them toward the NIIT threshold ($200K single / $250K MFJ)?

#### D. Business Structure
Check:
- Is there Schedule C income? If yes, how much SE tax are they paying?
- If SE tax is material (> ~$4,000-$5,000): flag entity comparison as worth exploring, estimate potential SE tax savings from S-Corp
- Is there S-Corp income (Schedule E, Partnership/S-Corp line)? Check if reasonable comp looks appropriate relative to distributions
- If W-2 only but client has side income or freelance potential: flag business formation opportunity and what it unlocks (QBI, retirement plans, deductions)

#### E. QBI Deduction
Check:
- Was a QBI deduction taken? If yes, was it the full 20% or was it limited?
- If no QBI and there's business income: identify why (income too high? SSTB above threshold? No qualifying income?)
- Is AGI near the QBI phase-out ($201,750 single / $403,500 MFJ)? If so, can retirement contributions or other adjustments reduce AGI below it?
- Quantify the QBI deduction value: 20% of QBI × marginal rate = tax savings

#### F. Withholding & Estimated Payments
Check:
- Did they owe at filing? How much?
- Was there an underpayment penalty? If yes, quantify it.
- Were estimated payments made? (Check estimated tax payments field)
- Calculate the safe harbor for next year: 110% of prior year tax if AGI > $150K, divided by 4 quarters
- Recommend specific quarterly payment amounts and due dates
- If they had a large refund: suggest reducing withholding to improve cash flow

#### G. Deduction Strategy
Check:
- Standard vs itemized — which was used? What was the standard deduction amount?
- If standard: are they potentially close to itemizing? Could a bunching strategy help in alternating years?
- Student loan interest deduction — eligible but not claimed?
- Educator expenses — applicable?
- State tax situation — SALT cap impact?

#### H. Credits Review
Check:
- Retirement savings contribution credit (Saver's Credit) — eligible based on AGI?
- Education credits — any eligible education expenses not captured?
- Residential clean energy credits — any solar, EV, or energy improvements?
- Child-related credits — any dependents not captured?

### Chat Output — Opportunity Report

Present findings grouped by impact level. Only include categories where you found something actionable.

**Opportunities Identified:**

**High Impact** (list each with title, explanation, estimated savings, and specific action)

**Medium Impact** (list each)

**Low Impact / Good to Know** (list each)

**Estimated Total Annual Tax Savings: $X,XXX - $X,XXX**
(Range based on which opportunities are implemented)

## Step 3: Action Plan

Synthesize into a prioritized, time-bound plan. This is what the client walks away with.

### Chat Output — Recommended Actions

**Immediate Actions (this quarter):**
1. [Most impactful action] — [deadline if applicable, specific dollar amounts]
2. [Next action]
3. ...

**Before Year-End [CURRENT YEAR]:**
1. [Action with year-end deadline]
2. ...

**For Next Filing Season:**
1. [Changes to implement for next year's return]
2. ...

**Worth Exploring Further (needs more info):**
1. [Items requiring additional client data or professional consultation]
2. ...

## Step 4: Scenario Handoff

After presenting the review, offer to run scenarios using the extracted data. Frame it as the logical next step:

> **Ready to model the impact?** Based on this review, here's what I'd recommend running next:
>
> - **Tax Estimate** — Model [CURRENT YEAR] taxes with the optimizations above applied to see the actual savings
> [If business income or side income potential:]
> - **Entity Comparison** — Compare current structure vs S-Corp to quantify SE tax savings
> [Always:]
> - **5-Year Projection** — See how these changes compound, especially as income grows toward [relevant threshold]
>
> I already have all the data from the transcript — no need to re-enter anything.

When the user chooses a follow-up skill, pass the extracted data in this format:

```
Extracted from [YEAR] IRS Transcript:
- Filing status: [status]
- W-2 wages: $[amount]
- Business income (Sched C): $[amount]
- Capital gains: $[amount] (ST: $[amount], LT: $[amount])
- Investment income: $[amount] (interest: $[amount], dividends: $[amount])
- State: [state — ask if not on transcript]
- AGI: $[amount]
- Total tax: $[amount]
- Effective rate: [X]%
- Current retirement contributions: $[amount]
- HSA contributions: $[amount] (employer: $[amount], personal: $[amount])
- Entity type: [Schedule C / S-Corp / W-2 only]
- SE tax paid: $[amount]
```

## Important Notes

- **Privacy**: IRS transcripts contain SSNs and addresses. Never echo the full SSN. Only reference "XXX-XX-[last 4]" if needed. Do not repeat the full address.
- **Accuracy**: This analysis is based on the prior year's filing. The client's current year situation may differ. Always ask about changes (new job, marriage, home purchase, etc.).
- **Professional referral**: For complex situations (amended returns, audit notices, multi-state filing, international income, trust/estate income), recommend CPA involvement and flag it explicitly.
- **Tone**: This is client-facing. Be professional, clear, and direct. Use plain English. When a tax term is necessary, briefly explain it in parentheses.
- **Disclaimer**: Always include at the end: "This analysis is for planning and educational purposes. It is not tax advice. Consult a licensed tax professional before making decisions based on this review."
