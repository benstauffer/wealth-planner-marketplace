# Personal Finance

Client-facing tax analysis and planning for business owners. Upload an IRS transcript for instant situation review, identify optimization opportunities with dollar-quantified savings, run tax estimates with actionable recommendations, compare entity structures with implementation roadmaps, and build multi-year projections with year-by-year action plans.

## Commands

| Command | What it does |
|---------|-------------|
| `/personal-finance:tax-review` | Upload an IRS transcript → get a full situation summary, opportunity analysis, and prioritized action plan |
| `/personal-finance:estimate` | Calculate a full tax liability estimate with actionable recommendations — what to change and how much it saves |
| `/personal-finance:entity-compare` | S-Corp vs Schedule C comparison with breakeven analysis and step-by-step implementation roadmap |
| `/personal-finance:projection` | 5-year income, tax, and net worth projection with year-by-year action items at every threshold crossing |

## Workflow

The skills are designed to flow together for client engagements:

1. **Tax Review** — Start here. Upload the client's IRS transcript. Get a situation summary, identify every missed opportunity, and build an action plan.
2. **Estimate** — Model the current year with optimizations applied. See the dollar savings from each recommendation.
3. **Entity Compare** — If the client has business income, compare structures with a full implementation roadmap and timeline.
4. **Projection** — Show how changes compound over 5 years. Flag inflection points and tell the client exactly what to do in each year.

The Tax Review skill automatically pre-populates data for the other skills — no re-entering information.

## Skills

- **tax-review** — Parses IRS transcripts (Form 1040 Record of Account), extracts all income, deduction, credit, and payment data, then runs a systematic opportunity analysis across retirement contributions, HSA, capital gains strategy, business structure, QBI, withholding, deductions, and credits. Each finding is rated by impact and includes the specific dollar savings and action steps.
- **estimate** — Step-by-step tax calculation with correct dependency ordering (SE tax → AGI → QBI → taxable income → brackets). Now includes an actionable recommendations section: bracket management, retirement optimization, estimated payment scheduling, and threshold proximity warnings.
- **entity-compare** — S-Corp vs Schedule C comparison including payroll tax savings, QBI deduction interaction, the 2/7 rule, administrative costs, and state-specific entity taxes. Now includes a full implementation roadmap with timeline, costs, and next steps — or a clear "not yet" with the income level to revisit.
- **projection** — Year-by-year modeling with income growth, inflation, retirement optimization, and net worth accumulation. Now includes inflection point actions: specific guidance for every threshold crossing with dollar impacts, recommended moves, and deadlines.

## Output

Every command produces both:
1. **Chat output** — Formatted tables, analysis, and actionable recommendations directly in the conversation
2. **Excel workbook** — Multi-tab spreadsheet saved to your outputs folder (generated via Python/openpyxl)

## Tax Data

All skills reference comprehensive 2026 tax parameters including:
- Federal income tax brackets (all filing statuses)
- Self-employment and payroll tax rates
- QBI deduction thresholds (OBBBA-expanded phase-outs)
- Solo 401(k), SEP-IRA, IRA, HSA contribution limits
- NIIT, AMT, SALT cap ($40,400)
- All 50 states + DC brackets and rates
- PTET rates and eligibility
- Section 179 and bonus depreciation
- 62 verified IRS source citations

## Usage Examples

```
/personal-finance:tax-review            (then upload IRS transcript PDF)
/personal-finance:estimate 300000 mfj california
/personal-finance:entity-compare 200000 texas
/personal-finance:projection 250000 5
```

Or just run the command and answer the prompts for the inputs you want to provide.
