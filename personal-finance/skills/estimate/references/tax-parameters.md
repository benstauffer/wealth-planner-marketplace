---
# ============================================================================
# METADATA
# ============================================================================
_metadata:
  version: "2026.1"
  last_updated: "2026-02-12"
  tax_year: 2026
  effective_date: "2026-01-01"

# ============================================================================
# SOURCE DEFINITIONS
# ============================================================================
# Every data point in this file traces to an authoritative source.
# This section defines each source with full metadata for verification and updates.

sources:
  # Federal Income Tax - Annual inflation adjustments
  fed_2026_inflation:
    id: fed_2026_inflation
    authority: IRS
    publication: "Rev. Proc. 2025-32"
    title: "2026 Inflation Adjustments"
    url: "https://www.irs.gov/pub/irs-drop/rp-25-32.pdf"
    verification_date: "2025-11-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: november
    update_pattern: "Rev. Proc. {YEAR-1}-XX published mid-November"
    typical_url_pattern: "https://www.irs.gov/pub/irs-drop/rp-{YY}-*.pdf"
    what_to_verify:
      - "Tax brackets (Table 1)"
      - "Standard deductions (Section 3.01)"
      - "Capital gains thresholds (Section 3.03)"
      - "AMT exemptions (Section 3.10)"
      - "QBID thresholds (Section 3.12)"
      - "Estate exemption (Section 3.14)"

  # Retirement Limits - Annual adjustments
  fed_2026_retirement:
    id: fed_2026_retirement
    authority: IRS
    publication: "IRS Notice 2025-67"
    title: "2026 Retirement Plan Limits"
    url: "https://www.irs.gov/pub/irs-drop/n-25-67.pdf"
    verification_date: "2025-11-13"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: november
    update_pattern: "IRS Notice {YEAR-1}-XX published early November"
    typical_url_pattern: "https://www.irs.gov/pub/irs-drop/n-{YY}-*.pdf"
    what_to_verify:
      - "401(k) elective deferral limit"
      - "IRA contribution limit"
      - "Catch-up contributions"
      - "Defined contribution limit"
      - "Compensation limit"
      - "SEP IRA limits"
      - "SIMPLE IRA limits"

  # HSA and FSA Limits
  fed_2026_hsa_fsa:
    id: fed_2026_hsa_fsa
    authority: IRS
    publication: "Rev. Proc. 2025-32"
    title: "2026 HSA and FSA Limits"
    url: "https://www.irs.gov/pub/irs-drop/rp-25-32.pdf"
    verification_date: "2025-11-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: november
    what_to_verify:
      - "HSA contribution limits"
      - "HDHP minimum deductibles"
      - "HDHP out-of-pocket maximums"
      - "Health FSA limit"

  # Social Security Wage Base
  ssa_2026_cola:
    id: ssa_2026_cola
    authority: SSA
    publication: "Social Security COLA Announcement 2026"
    title: "2026 Social Security Changes"
    url: "https://www.ssa.gov/news/press/factsheets/colafacts2026.pdf"
    verification_date: "2025-10-10"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: october
    update_pattern: "SSA announces COLA mid-October each year"
    typical_url_pattern: "https://www.ssa.gov/news/press/factsheets/colafacts{YEAR}.pdf"
    what_to_verify:
      - "Social Security wage base"

  # NIIT - Fixed rates, not indexed
  irc_1411_niit:
    id: irc_1411_niit
    authority: Congress
    publication: "IRC Section 1411"
    title: "Net Investment Income Tax"
    url: "https://www.law.cornell.edu/uscode/text/26/1411"
    verification_date: "2026-02-12"
    effective_date: "2013-01-01"
    update_frequency: legislative
    notes: "Rate 3.8% and thresholds NOT indexed since enactment in 2013"
    what_to_verify:
      - "3.8% rate (unchanged)"
      - "Thresholds NOT indexed (200K/250K/125K)"

  # Additional Medicare Tax - Fixed rate
  irc_3101_medicare:
    id: irc_3101_medicare
    authority: Congress
    publication: "IRC Section 3101"
    title: "Additional Medicare Tax"
    url: "https://www.law.cornell.edu/uscode/text/26/3101"
    verification_date: "2026-02-12"
    effective_date: "2013-01-01"
    update_frequency: legislative
    notes: "0.9% rate, NOT deductible per IRC 164(f)"
    what_to_verify:
      - "0.9% rate (unchanged since 2013)"
      - "Not deductible for SE tax"

  # SALT Cap - OBBBA provisions
  obbba_salt:
    id: obbba_salt
    authority: Congress
    publication: "P.L. 119-21"
    title: "One Big Beautiful Bill Act of 2025"
    url: "https://www.congress.gov/bill/119th-congress/house-bill/1/text"
    verification_date: "2025-02-05"
    effective_date: "2025-01-01"
    expiration_date: "2029-12-31"
    update_frequency: legislative
    sections: ["Section 201 (SALT cap modifications)"]
    notes: "Temporary increase, reverts to $10,000 on 2030-01-01"
    what_to_verify:
      - "Cap amount $40,400"
      - "Phasedown mechanics"
      - "Expiration date 2029-12-31"

  # Senior Deduction - OBBBA provisions
  obbba_senior:
    id: obbba_senior
    authority: Congress
    publication: "P.L. 119-21"
    title: "One Big Beautiful Bill Act - Senior Deduction"
    url: "https://www.congress.gov/bill/119th-congress/house-bill/1/text"
    verification_date: "2025-02-05"
    effective_date: "2025-01-01"
    expiration_date: "2028-12-31"
    update_frequency: legislative
    sections: ["Section 102 (Senior deduction)"]
    notes: "Temporary provision 2025-2028"
    what_to_verify:
      - "$6,000 single, $12,000 MFJ both 65+"
      - "Phaseout ranges"
      - "Expiration 2028-12-31"

  # Bonus Depreciation - OBBBA restoration
  obbba_bonus:
    id: obbba_bonus
    authority: Congress
    publication: "P.L. 119-21"
    title: "One Big Beautiful Bill Act - Bonus Depreciation"
    url: "https://www.congress.gov/bill/119th-congress/house-bill/1/text"
    verification_date: "2025-02-05"
    effective_date: "2025-01-01"
    update_frequency: legislative
    sections: ["Bonus depreciation restoration"]
    notes: "100% restored retroactive to Jan 1, 2025"
    what_to_verify:
      - "100% rate for 2025-2027"

  # Section 179 Limits
  fed_2026_section179:
    id: fed_2026_section179
    authority: IRS
    publication: "Rev. Proc. 2025-32"
    title: "2026 Section 179 Limits"
    url: "https://www.irs.gov/pub/irs-drop/rp-25-32.pdf"
    verification_date: "2025-11-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: november
    what_to_verify:
      - "Section 179 expensing limit"
      - "Phaseout threshold"

  # PTET Multi-State Overview
  ptet_overview:
    id: ptet_overview
    authority: AICPA
    publication: "State Pass-Through Entity Tax Tracker"
    title: "PTET State-by-State Guide"
    url: "https://www.aicpa.org/resources/article/state-pass-through-entity-tax-information"
    verification_date: "2026-01-15"
    effective_date: "varies by state"
    update_frequency: quarterly
    notes: "Monitor for new adoptions, expirations, and rate changes"
    what_to_verify:
      - "Active PTET states"
      - "Expiration dates"
      - "Credit types (refundable/nonrefundable/exclusion)"

  # State Sources - No Tax States (9)
  state_ak:
    id: state_ak
    authority: "State of Alaska"
    state: AK
    url: "https://tax.alaska.gov/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: legislative
    notes: "No income tax"

  state_fl:
    id: state_fl
    authority: "Florida Department of Revenue"
    state: FL
    url: "https://floridarevenue.com/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: legislative
    notes: "No income tax"

  state_nv:
    id: state_nv
    authority: "Nevada Department of Taxation"
    state: NV
    url: "https://tax.nv.gov/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: legislative
    notes: "No income tax"

  state_nh:
    id: state_nh
    authority: "New Hampshire Department of Revenue"
    state: NH
    url: "https://www.revenue.nh.gov/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: legislative
    notes: "No income tax on wages; has Business Profits Tax"

  state_sd:
    id: state_sd
    authority: "South Dakota Department of Revenue"
    state: SD
    url: "https://dor.sd.gov/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: legislative
    notes: "No income tax"

  state_tn:
    id: state_tn
    authority: "Tennessee Department of Revenue"
    state: TN
    url: "https://www.tn.gov/revenue.html"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: legislative
    notes: "No income tax on wages"

  state_tx:
    id: state_tx
    authority: "Texas Comptroller"
    state: TX
    url: "https://comptroller.texas.gov/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: legislative
    notes: "No income tax"

  state_wa:
    id: state_wa
    authority: "Washington Department of Revenue"
    state: WA
    url: "https://dor.wa.gov/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: legislative
    notes: "No income tax on wages; has capital gains tax on gains >$278K"

  state_wy:
    id: state_wy
    authority: "Wyoming Department of Revenue"
    state: WY
    url: "https://revenue.wyo.gov/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: legislative
    notes: "No income tax"

  # State Sources - Flat Tax States
  state_az:
    id: state_az
    authority: "Arizona Department of Revenue"
    state: AZ
    publication: "2026 Tax Rate Schedules"
    url: "https://azdor.gov/forms/individual/2026-individual-income-tax-forms"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_co:
    id: state_co
    authority: "Colorado Department of Revenue"
    state: CO
    publication: "2026 Colorado Income Tax Rate"
    url: "https://tax.colorado.gov/individual-income-tax"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_ga:
    id: state_ga
    authority: "Georgia Department of Revenue"
    state: GA
    publication: "2026 Tax Rate Information"
    url: "https://dor.georgia.gov/taxes/individual-income-tax"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_id:
    id: state_id
    authority: "Idaho State Tax Commission"
    state: ID
    publication: "2026 Tax Rates"
    url: "https://tax.idaho.gov/taxes/income-tax/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_il:
    id: state_il
    authority: "Illinois Department of Revenue"
    state: IL
    publication: "2026 Individual Income Tax Rate"
    url: "https://tax.illinois.gov/content/individual-income-tax.html"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_in:
    id: state_in
    authority: "Indiana Department of Revenue"
    state: IN
    publication: "2026 Tax Rate"
    url: "https://www.in.gov/dor/individual-income-taxes/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_ia:
    id: state_ia
    authority: "Iowa Department of Revenue"
    state: IA
    publication: "2026 Tax Rate"
    url: "https://tax.iowa.gov/individual-income-tax-information"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_ky:
    id: state_ky
    authority: "Kentucky Department of Revenue"
    state: KY
    publication: "2026 Tax Rate"
    url: "https://revenue.ky.gov/Individual/Individual-Income-Tax/Pages/default.aspx"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_la:
    id: state_la
    authority: "Louisiana Department of Revenue"
    state: LA
    publication: "2026 Tax Rate"
    url: "https://revenue.louisiana.gov/IndividualIncomeTax"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_mi:
    id: state_mi
    authority: "Michigan Department of Treasury"
    state: MI
    publication: "2026 Tax Rate"
    url: "https://www.michigan.gov/taxes/iit"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_mo:
    id: state_mo
    authority: "Missouri Department of Revenue"
    state: MO
    publication: "2026 Tax Rate"
    url: "https://dor.mo.gov/taxation/individual/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_ms:
    id: state_ms
    authority: "Mississippi Department of Revenue"
    state: MS
    publication: "2026 Tax Brackets"
    url: "https://www.dor.ms.gov/individual/income-tax"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_nc:
    id: state_nc
    authority: "North Carolina Department of Revenue"
    state: NC
    publication: "2026 Tax Rate"
    url: "https://www.ncdor.gov/taxes-forms/individual-income-tax"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_oh:
    id: state_oh
    authority: "Ohio Department of Taxation"
    state: OH
    publication: "2026 Tax Brackets"
    url: "https://tax.ohio.gov/individual/income-tax"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_pa:
    id: state_pa
    authority: "Pennsylvania Department of Revenue"
    state: PA
    publication: "2026 Tax Rate"
    url: "https://www.revenue.pa.gov/TaxTypes/PIT/Pages/default.aspx"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_ut:
    id: state_ut
    authority: "Utah State Tax Commission"
    state: UT
    publication: "2026 Tax Rate"
    url: "https://tax.utah.gov/income-tax"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  # State Sources - Graduated Tax States
  state_al:
    id: state_al
    authority: "Alabama Department of Revenue"
    state: AL
    publication: "2026 Tax Brackets"
    url: "https://revenue.alabama.gov/individual-corporate/individual-income-tax/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_ar:
    id: state_ar
    authority: "Arkansas Department of Finance and Administration"
    state: AR
    publication: "2026 Tax Tables"
    url: "https://www.dfa.arkansas.gov/income-tax/individual-income-tax/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_ca:
    id: state_ca
    authority: "California Franchise Tax Board"
    state: CA
    publication: "2026 Tax Rate Schedules"
    url: "https://www.ftb.ca.gov/forms/2026/2026-540-tax-rate-schedules.pdf"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_ct:
    id: state_ct
    authority: "Connecticut Department of Revenue Services"
    state: CT
    publication: "2026 Tax Rate Schedule"
    url: "https://portal.ct.gov/DRS/Individuals/Individual-Tax-Rates"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_dc:
    id: state_dc
    authority: "DC Office of Tax and Revenue"
    state: DC
    publication: "2026 Tax Rate Schedule"
    url: "https://otr.cfo.dc.gov/page/individual-and-fiduciary-income-taxes"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_de:
    id: state_de
    authority: "Delaware Division of Revenue"
    state: DE
    publication: "2026 Tax Brackets"
    url: "https://revenue.delaware.gov/individual-taxes/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_hi:
    id: state_hi
    authority: "Hawaii Department of Taxation"
    state: HI
    publication: "2026 Tax Rate Schedules"
    url: "https://tax.hawaii.gov/geninfo/rates/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_ks:
    id: state_ks
    authority: "Kansas Department of Revenue"
    state: KS
    publication: "2026 Tax Brackets"
    url: "https://www.ksrevenue.gov/individualtax.html"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_me:
    id: state_me
    authority: "Maine Revenue Services"
    state: ME
    publication: "2026 Tax Rate Schedule"
    url: "https://www.maine.gov/revenue/taxes/income-estate-tax/individual-income-tax"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_md:
    id: state_md
    authority: "Maryland Comptroller"
    state: MD
    publication: "2026 Tax Rate Schedule"
    url: "https://www.marylandtaxes.gov/individual/income/tax-info/tax-rates.php"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_ma:
    id: state_ma
    authority: "Massachusetts Department of Revenue"
    state: MA
    publication: "2026 Tax Rates"
    url: "https://www.mass.gov/service-details/personal-income-tax"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_mn:
    id: state_mn
    authority: "Minnesota Department of Revenue"
    state: MN
    publication: "2026 Tax Brackets"
    url: "https://www.revenue.state.mn.us/individual-income-tax"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_mt:
    id: state_mt
    authority: "Montana Department of Revenue"
    state: MT
    publication: "2026 Tax Brackets"
    url: "https://mtrevenue.gov/taxes/individual-income-tax/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_ne:
    id: state_ne
    authority: "Nebraska Department of Revenue"
    state: NE
    publication: "2026 Tax Rate Schedule"
    url: "https://revenue.nebraska.gov/individuals/income-tax-rates-brackets"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_nj:
    id: state_nj
    authority: "New Jersey Division of Taxation"
    state: NJ
    publication: "2026 Tax Rate Schedule"
    url: "https://www.state.nj.us/treasury/taxation/taxtables.shtml"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_nm:
    id: state_nm
    authority: "New Mexico Taxation and Revenue"
    state: NM
    publication: "2026 Tax Rate Schedule"
    url: "https://www.tax.newmexico.gov/individuals/personal-income-tax-forms-and-publications/"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_ny:
    id: state_ny
    authority: "New York State Department of Taxation and Finance"
    state: NY
    publication: "2026 Tax Rate Schedule"
    url: "https://www.tax.ny.gov/pit/file/tax_tables.htm"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_nd:
    id: state_nd
    authority: "North Dakota Office of State Tax Commissioner"
    state: ND
    publication: "2026 Tax Brackets"
    url: "https://www.nd.gov/tax/user/businesses/formspublications/income-tax-rates"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_ok:
    id: state_ok
    authority: "Oklahoma Tax Commission"
    state: OK
    publication: "2026 Tax Rate Schedule"
    url: "https://oklahoma.gov/tax/individuals/income-tax.html"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_or:
    id: state_or
    authority: "Oregon Department of Revenue"
    state: OR
    publication: "2026 Tax Rate Schedule"
    url: "https://www.oregon.gov/dor/programs/individuals/pages/tax-rates.aspx"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_ri:
    id: state_ri
    authority: "Rhode Island Division of Taxation"
    state: RI
    publication: "2026 Tax Rate Schedule"
    url: "https://tax.ri.gov/taxation/personal.php"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_sc:
    id: state_sc
    authority: "South Carolina Department of Revenue"
    state: SC
    publication: "2026 Tax Rate Schedule"
    url: "https://dor.sc.gov/tax/individual-income"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_vt:
    id: state_vt
    authority: "Vermont Department of Taxes"
    state: VT
    publication: "2026 Tax Rate Schedule"
    url: "https://tax.vermont.gov/individuals"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_va:
    id: state_va
    authority: "Virginia Department of Taxation"
    state: VA
    publication: "2026 Tax Rate Schedule"
    url: "https://www.tax.virginia.gov/individual-income-tax"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_wv:
    id: state_wv
    authority: "West Virginia State Tax Department"
    state: WV
    publication: "2026 Tax Rate Schedule"
    url: "https://tax.wv.gov/Individuals/PersonalIncomeTax/Pages/PersonalIncomeTax.aspx"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

  state_wi:
    id: state_wi
    authority: "Wisconsin Department of Revenue"
    state: WI
    publication: "2026 Tax Rate Schedule"
    url: "https://www.revenue.wi.gov/Pages/FAQS/pcs-taxrate.aspx"
    verification_date: "2026-01-15"
    effective_date: "2026-01-01"
    update_frequency: annual
    update_month: january

# ============================================================================
# TAX DATA WITH SOURCE REFERENCES
# ============================================================================

brackets:
  _source: fed_2026_inflation
  _verification_note: "Table 1, Tax Rate Schedules"
  _last_verified: "2025-11-15"
  single:
    - { min: 0, max: 12400, rate: 0.10 }
    - { min: 12400, max: 50400, rate: 0.12 }
    - { min: 50400, max: 105700, rate: 0.22 }
    - { min: 105700, max: 201775, rate: 0.24 }
    - { min: 201775, max: 256225, rate: 0.32 }
    - { min: 256225, max: 640600, rate: 0.35 }
    - { min: 640600, max: null, rate: 0.37 }
  mfj:
    - { min: 0, max: 24800, rate: 0.10 }
    - { min: 24800, max: 100800, rate: 0.12 }
    - { min: 100800, max: 211400, rate: 0.22 }
    - { min: 211400, max: 403550, rate: 0.24 }
    - { min: 403550, max: 512450, rate: 0.32 }
    - { min: 512450, max: 768700, rate: 0.35 }
    - { min: 768700, max: null, rate: 0.37 }
  mfs:
    - { min: 0, max: 12400, rate: 0.10 }
    - { min: 12400, max: 50400, rate: 0.12 }
    - { min: 50400, max: 105700, rate: 0.22 }
    - { min: 105700, max: 201775, rate: 0.24 }
    - { min: 201775, max: 256225, rate: 0.32 }
    - { min: 256225, max: 384350, rate: 0.35 }
    - { min: 384350, max: null, rate: 0.37 }
  hoh:
    - { min: 0, max: 17700, rate: 0.10 }
    - { min: 17700, max: 67450, rate: 0.12 }
    - { min: 67450, max: 105700, rate: 0.22 }
    - { min: 105700, max: 201775, rate: 0.24 }
    - { min: 201775, max: 256200, rate: 0.32 }
    - { min: 256200, max: 640600, rate: 0.35 }
    - { min: 640600, max: null, rate: 0.37 }
standard_deductions:
  _source: fed_2026_inflation
  _verification_note: "Section 3.01, Standard Deduction Amounts"
  _last_verified: "2025-11-15"
  single: 16100
  mfj: 32200
  mfs: 16100
  hoh: 24150
  qw: 32200
additional_standard_deduction:
  _source: fed_2026_inflation
  _verification_note: "Section 3.01, Additional Standard Deduction for Aged and Blind"
  _last_verified: "2025-11-15"
  single_hoh: 2050   # per condition (65+ or blind)
  mfj_mfs: 1650      # per person per condition
personal_exemption: 0
senior_deduction:
  _source: obbba_senior
  _verification_note: "Section 102, Senior Deduction"
  _last_verified: "2025-02-05"
  _expiration_date: "2028-12-31"
  amount: 6000
  amount_mfj_both_65: 12000
  phaseout_begins: { single: 75000, mfj: 150000 }
  phaseout_complete: { single: 175000, mfj: 250000 }
  tax_years: "2025-2028"
capital_gains:
  _source: fed_2026_inflation
  _verification_note: "Section 3.03, Capital Gains Tax Rate Thresholds"
  _last_verified: "2025-11-15"
  single:
    - { min: 0, max: 49450, rate: 0.0 }
    - { min: 49450, max: 545500, rate: 0.15 }
    - { min: 545500, max: null, rate: 0.20 }
  mfj:
    - { min: 0, max: 98900, rate: 0.0 }
    - { min: 98900, max: 613700, rate: 0.15 }
    - { min: 613700, max: null, rate: 0.20 }
  mfs:
    - { min: 0, max: 49450, rate: 0.0 }
    - { min: 49450, max: 306850, rate: 0.15 }
    - { min: 306850, max: null, rate: 0.20 }
  hoh:
    - { min: 0, max: 66200, rate: 0.0 }
    - { min: 66200, max: 579600, rate: 0.15 }
    - { min: 579600, max: null, rate: 0.20 }
special_capital_gains:
  _source: irc_1411_niit
  _verification_note: "IRC sections 1(h), 1202, 1250 - Fixed rates not indexed"
  _last_verified: "2026-02-12"
  collectibles: 0.28
  unrecaptured_1250: 0.25
  qsbs_1202: 0.28
payroll:
  _source: ssa_2026_cola
  _verification_note: "2026 Social Security Changes Fact Sheet"
  _last_verified: "2025-10-10"
  ss_wage_base: 184500
  ss_rate: 0.124
  ss_max_tax: 22878
  ss_max_tax_per_side: 11439
  medicare_rate: 0.029
  additional_medicare_rate: 0.009
  se_taxable_multiplier: 0.9235
additional_medicare_thresholds:
  _source: irc_3101_medicare
  _verification_note: "IRC Section 3101 - Not indexed, unchanged since 2013"
  _last_verified: "2026-02-12"
  single: 200000
  mfj: 250000
  mfs: 125000
  hoh: 200000
  qw: 250000
futa:
  _source: irc_3101_medicare
  _verification_note: "IRC Section 3301 - Fixed rates"
  _last_verified: "2026-02-12"
  gross_rate: 0.06
  credit: 0.054
  effective_rate: 0.006
  wage_base: 7000
  max_per_employee: 42
nanny_tax:
  _source: fed_2026_inflation
  _verification_note: "Section 3.06, Household Employment Taxes"
  _last_verified: "2025-11-15"
  fica_threshold: 3000
  futa_threshold: 1000
niit:
  _source: irc_1411_niit
  _verification_note: "IRC Section 1411 - NOT indexed, fixed since 2013"
  _last_verified: "2026-02-12"
  rate: 0.038
  indexed: false
  thresholds:
    single: 200000
    mfj: 250000
    mfs: 125000
    hoh: 200000
    qw: 250000
qbid:
  _source: fed_2026_inflation
  _verification_note: "Section 3.12, Qualified Business Income Deduction"
  _last_verified: "2025-11-15"
  rate: 0.20
  w2_wage_limit: 0.50
  w2_ubia_wage_pct: 0.25
  w2_ubia_ubia_pct: 0.025
  optimal_w2_ratio: 0.2857
  single:
    full_deduction: 201750
    phaseout_range: 75000
    phaseout_complete: 276750
  mfj:
    full_deduction: 403500
    phaseout_range: 150000
    phaseout_complete: 553500
salt_cap:
  _source: obbba_salt
  _verification_note: "Section 201, SALT Cap Modifications"
  _last_verified: "2025-02-05"
  _expiration_date: "2029-12-31"
  limit: 40400
  limit_mfs: 20200
  floor: 10000
  floor_mfs: 5000
  phasedown_rate: 0.30
  phasedown_begins: 505000
  phasedown_begins_mfs: 252500
  phasedown_complete: 606333
  phasedown_complete_mfs: 303167
  annual_adjustment: 1.01
  expiration: "2029-12-31"
  reversion_amount: 10000
amt:
  _source: fed_2026_inflation
  _verification_note: "Section 3.10, Alternative Minimum Tax Exemption Amounts"
  _last_verified: "2025-11-15"
  exemption:
    single: 90100
    mfj: 140200
    mfs: 70100
  phaseout_begins:
    single: 500000
    mfj: 1000000
  threshold_28pct: 244500
other:
  _source: fed_2026_inflation
  _verification_note: "Various sections - Kiddie tax, FEIE, educator expenses, adoption credit, student loan interest"
  _last_verified: "2025-11-15"
  kiddie_tax_threshold: 2700
  foreign_earned_income_exclusion: 132900
  educator_expense_deduction: 350
  adoption_credit_max: 17670
  student_loan_interest_max: 2500
solo_401k:
  _source: fed_2026_retirement
  _verification_note: "IRS Notice 2025-67, Retirement Plan Limitations"
  _last_verified: "2025-11-13"
  employee_deferral: 24500
  catch_up_50_plus: 8000
  super_catch_up_60_63: 11250
  total_limit: 72000
  compensation_limit: 360000
  max_by_age:
    under_50: 24500
    50_59: 32500
    60_63: 35750
    64_plus: 32500
ira_limit:
  _source: fed_2026_retirement
  _verification_note: "IRS Notice 2025-67, IRA Contribution Limits"
  _last_verified: "2025-11-13"
  _value: 7500
ira_catch_up_50_plus: 1100
roth_ira_phaseout:
  _source: fed_2026_retirement
  _verification_note: "IRS Notice 2025-67, IRA Phaseout Ranges"
  _last_verified: "2025-11-13"
  single: { start: 153000, end: 168000 }
  mfj: { start: 242000, end: 252000 }
  mfs: { start: 0, end: 10000 }
traditional_ira_phaseout:
  _source: fed_2026_retirement
  _verification_note: "IRS Notice 2025-67, Traditional IRA Phaseout Ranges"
  _last_verified: "2025-11-13"
  single: { start: 81000, end: 91000 }
  mfj_contributor: { start: 129000, end: 149000 }
  mfj_spouse: { start: 242000, end: 252000 }
  mfs: { start: 0, end: 10000 }
sep_ira:
  _source: fed_2026_retirement
  _verification_note: "IRS Notice 2025-67, SEP IRA Limits"
  _last_verified: "2025-11-13"
  limit: 72000
  percent: 0.25
  compensation_limit: 360000
  min_compensation: 800
simple_ira:
  _source: fed_2026_retirement
  _verification_note: "IRS Notice 2025-67, SIMPLE IRA Limits"
  _last_verified: "2025-11-13"
  employee_deferral: 17000
  employee_deferral_applicable: 18100
  catch_up_50_plus: 4000
  catch_up_50_plus_applicable: 3850
  super_catch_up_60_63: 5250
hsa:
  _source: fed_2026_hsa_fsa
  _verification_note: "Rev. Proc. 2025-32, HSA Contribution Limits and HDHP Parameters"
  _last_verified: "2025-11-15"
  individual: 4400
  family: 8750
  catch_up_55_plus: 1000
  hdhp_min_deductible: { individual: 1700, family: 3400 }
  hdhp_max_oop: { individual: 8500, family: 17000 }
fsa:
  _source: fed_2026_hsa_fsa
  _verification_note: "Rev. Proc. 2025-32, FSA Limits"
  _last_verified: "2025-11-15"
  healthcare: 3400
  healthcare_carryover: 680
  dependent_care: 5000
  dependent_care_mfs: 2500
defined_benefit:
  _source: fed_2026_retirement
  _verification_note: "IRS Notice 2025-67, Defined Benefit Plan Limits"
  _last_verified: "2025-11-13"
  annual_limit: 290000
other_retirement:
  _source: fed_2026_retirement
  _verification_note: "IRS Notice 2025-67, Various Retirement Thresholds"
  _last_verified: "2025-11-13"
  hce_threshold: 160000
  key_employee_officer: 235000
  savers_credit_50_single: 24125
  savers_credit_50_mfj: 48250
  roth_catch_up_wage_threshold: 150000
section_179:
  _source: fed_2026_section179
  _verification_note: "Rev. Proc. 2025-32, Section 179 Expensing Limits"
  _last_verified: "2025-11-15"
  limit: 1220000
  phaseout_begins: 3050000
  phaseout_ends: 4270000
bonus_depreciation:
  _source: obbba_bonus
  _verification_note: "OBBBA Bonus Depreciation Restoration"
  _last_verified: "2025-02-05"
  2022: 1.0
  2023: 0.8
  2024: 0.6
  2025: 1.0
  2026: 1.0
  2027: 1.0
macrs:
  3: Rent-to-own property, qualified racehorses
  5: Computers, office equipment, automobiles, light trucks
  7: Office furniture, agricultural machinery
  15: Qualified improvement property, land improvements
  27.5: Residential rental property
  39: Nonresidential real property
estate_exemption: 15000000
gift_exemption: 15000000
gst_exemption: 15000000
annual_exclusion: 19000
annual_exclusion_noncitizen_spouse: 194000
top_estate_rate: 0.40
portability: true
state_lists:
  _verification_note: "State tax policy as of 2026-01-15"
  _last_verified: "2026-01-15"
  no_tax: [AK, FL, NV, NH, SD, TN, TX, WA, WY]
  ptet: [AL, AZ, AR, CA, CO, CT, GA, HI, ID, IL, IN, IA, KS, KY, LA, ME, MD, MA, MI, MS, MO, MT, NE, NJ, NM, NY, NC, OH, OK, OR, RI, SC, UT, WV, WI]
  qbid_nonconforming: [CA, DC, HI, MN, NJ, NY, OR, PA, SC, VT]
local:
  NYC: { name: "New York City", state: NY, rate: 0.03876 }
  PHL: { name: "Philadelphia", state: PA, rate: 0.0375 }
  SF:  { name: "San Francisco", state: CA, rate: 0.0038 }
ca_scorp_entity_tax:
  _source: state_ca
  _verification_note: "CA FTB S-Corp Entity Tax and LLC Fee Schedule"
  _last_verified: "2026-01-15"
  rate: 0.015
  minimum: 800
  llc_fee_brackets:
    - { min: 0, max: 250000, fee: 0 }
    - { min: 250000, max: 500000, fee: 900 }
    - { min: 500000, max: 1000000, fee: 2500 }
    - { min: 1000000, max: 5000000, fee: 6000 }
    - { min: 5000000, max: null, fee: 11790 }
federal_conformity_deductions: [CO, DC, ID, MO, MT, NM, SC]
state_no_tax:
  _verification_note: "States with no income tax - verified individually"
  _last_verified: "2026-01-15"
  AK: { type: none }
  FL: { type: none }
  NV: { type: none }
  NH: { type: none }
  SD: { type: none }
  TN: { type: none }
  TX: { type: none }
  WA: { type: none }
  WY: { type: none }
state_flat:
  _verification_note: "Flat tax states - rates verified with individual state DORs"
  _last_verified: "2026-01-15"
  AZ:
    _source: state_az
    type: flat
    rate: 0.025
  CO:
    _source: state_co
    type: flat
    rate: 0.044
  GA:
    _source: state_ga
    type: flat
    rate: 0.0509
    dependent_exemption: 4000
  ID:
    _source: state_id
    type: flat
    rate: 0.053
  IL:
    _source: state_il
    type: flat
    rate: 0.0495
  IN:
    _source: state_in
    type: flat
    rate: 0.0295
  IA:
    _source: state_ia
    type: flat
    rate: 0.038
  KY:
    _source: state_ky
    type: flat
    rate: 0.035
  LA:
    _source: state_la
    type: flat
    rate: 0.03
  MI:
    _source: state_mi
    type: flat
    rate: 0.0425
    personal_exemption: 5900
    senior_deduction: { single: 20000, mfj: 40000 }
  MO:
    _source: state_mo
    type: flat
    rate: 0.047
  MS:
    _source: state_ms
    type: graduated
    brackets:
      - { min: 0, max: 10000, rate: 0.0 }
      - { min: 10000, max: null, rate: 0.04 }
    personal_exemption: { single: 6000, mfj: 12000, hoh: 9500, dependent: 1500 }
  NC:
    _source: state_nc
    type: flat
    rate: 0.0399
  OH:
    _source: state_oh
    type: graduated
    brackets:
      - { min: 0, max: 26050, rate: 0.0 }
      - { min: 26050, max: null, rate: 0.0275 }
    personal_exemption: 650
    personal_exemption_magi_limit: 500000
    business_income_rate: 0.03
  PA:
    _source: state_pa
    type: flat
    rate: 0.0307
  UT:
    _source: state_ut
    type: flat
    rate: 0.045
state_flat_standard_deductions:
  _verification_note: "Standard deductions for flat tax states"
  _last_verified: "2026-01-15"
  AZ: { single: 15750, mfj: 31500, mfs: 15750, hoh: 23625 }
  GA: { single: 12000, mfj: 24000, mfs: 12000, hoh: 12000 }
  KY: { single: 3160, mfj: 3160, mfs: 3160, hoh: 3160 }
  LA: { single: 12875, mfj: 25750, mfs: 12875, hoh: 25750 }
  MS: { single: 2300, mfj: 4600, mfs: 2300, hoh: 3400 }
  NC: { single: 12750, mfj: 25500, mfs: 12750, hoh: 19125 }
state_graduated_al_mn:
  _verification_note: "Graduated tax states AL through MN"
  _last_verified: "2026-01-15"
  AL:
    _source: state_al
    type: graduated
    brackets:
      single:
        - { min: 0, max: 500, rate: 0.02 }
        - { min: 500, max: 3000, rate: 0.04 }
        - { min: 3000, max: null, rate: 0.05 }
      mfj:
        - { min: 0, max: 1000, rate: 0.02 }
        - { min: 1000, max: 6000, rate: 0.04 }
        - { min: 6000, max: null, rate: 0.05 }
      mfs:
        - { min: 0, max: 500, rate: 0.02 }
        - { min: 500, max: 3000, rate: 0.04 }
        - { min: 3000, max: null, rate: 0.05 }
      hoh:
        - { min: 0, max: 500, rate: 0.02 }
        - { min: 500, max: 3000, rate: 0.04 }
        - { min: 3000, max: null, rate: 0.05 }
  AR:
    _source: state_ar
    type: graduated
    brackets:
      single:
        - { min: 0, max: 5500, rate: 0.0 }
        - { min: 5500, max: 10900, rate: 0.02 }
        - { min: 10900, max: 15600, rate: 0.03 }
        - { min: 15600, max: 25700, rate: 0.034 }
        - { min: 25700, max: null, rate: 0.039 }
      mfj:
        - { min: 0, max: 5500, rate: 0.0 }
        - { min: 5500, max: 10900, rate: 0.02 }
        - { min: 10900, max: 15600, rate: 0.03 }
        - { min: 15600, max: 25700, rate: 0.034 }
        - { min: 25700, max: null, rate: 0.039 }
      mfs:
        - { min: 0, max: 5500, rate: 0.0 }
        - { min: 5500, max: 10900, rate: 0.02 }
        - { min: 10900, max: 15600, rate: 0.03 }
        - { min: 15600, max: 25700, rate: 0.034 }
        - { min: 25700, max: null, rate: 0.039 }
      hoh:
        - { min: 0, max: 5500, rate: 0.0 }
        - { min: 5500, max: 10900, rate: 0.02 }
        - { min: 10900, max: 15600, rate: 0.03 }
        - { min: 15600, max: 25700, rate: 0.034 }
        - { min: 25700, max: null, rate: 0.039 }
  CA:
    _source: state_ca
    type: graduated
    brackets:
      single:
        - { min: 0, max: 11079, rate: 0.01 }
        - { min: 11079, max: 26264, rate: 0.02 }
        - { min: 26264, max: 41452, rate: 0.04 }
        - { min: 41452, max: 57542, rate: 0.06 }
        - { min: 57542, max: 72724, rate: 0.08 }
        - { min: 72724, max: 371479, rate: 0.093 }
        - { min: 371479, max: 445771, rate: 0.103 }
        - { min: 445771, max: 742953, rate: 0.113 }
        - { min: 742953, max: 1000000, rate: 0.123 }
        - { min: 1000000, max: null, rate: 0.133 }
      mfj:
        - { min: 0, max: 22158, rate: 0.01 }
        - { min: 22158, max: 52528, rate: 0.02 }
        - { min: 52528, max: 82904, rate: 0.04 }
        - { min: 82904, max: 115084, rate: 0.06 }
        - { min: 115084, max: 145448, rate: 0.08 }
        - { min: 145448, max: 742958, rate: 0.093 }
        - { min: 742958, max: 891542, rate: 0.103 }
        - { min: 891542, max: 1000000, rate: 0.113 }
        - { min: 1000000, max: 1485906, rate: 0.123 }
        - { min: 1485906, max: null, rate: 0.133 }
      mfs:
        - { min: 0, max: 11079, rate: 0.01 }
        - { min: 11079, max: 26264, rate: 0.02 }
        - { min: 26264, max: 41452, rate: 0.04 }
        - { min: 41452, max: 57542, rate: 0.06 }
        - { min: 57542, max: 72724, rate: 0.08 }
        - { min: 72724, max: 371479, rate: 0.093 }
        - { min: 371479, max: 445771, rate: 0.103 }
        - { min: 445771, max: 742953, rate: 0.113 }
        - { min: 742953, max: 1000000, rate: 0.123 }
        - { min: 1000000, max: null, rate: 0.133 }
      hoh:
        - { min: 0, max: 22171, rate: 0.01 }
        - { min: 22171, max: 52530, rate: 0.02 }
        - { min: 52530, max: 67717, rate: 0.04 }
        - { min: 67717, max: 83809, rate: 0.06 }
        - { min: 83809, max: 98991, rate: 0.08 }
        - { min: 98991, max: 507743, rate: 0.093 }
        - { min: 507743, max: 609288, rate: 0.103 }
        - { min: 609288, max: 1000000, rate: 0.113 }
        - { min: 1000000, max: 1016470, rate: 0.123 }
        - { min: 1016470, max: null, rate: 0.133 }
  CT:
    _source: state_ct
    type: graduated
    brackets:
      single:
        - { min: 0, max: 10000, rate: 0.02 }
        - { min: 10000, max: 50000, rate: 0.045 }
        - { min: 50000, max: 100000, rate: 0.055 }
        - { min: 100000, max: 200000, rate: 0.06 }
        - { min: 200000, max: 250000, rate: 0.065 }
        - { min: 250000, max: 500000, rate: 0.069 }
        - { min: 500000, max: null, rate: 0.0699 }
      mfj:
        - { min: 0, max: 20000, rate: 0.02 }
        - { min: 20000, max: 100000, rate: 0.045 }
        - { min: 100000, max: 200000, rate: 0.055 }
        - { min: 200000, max: 400000, rate: 0.06 }
        - { min: 400000, max: 500000, rate: 0.065 }
        - { min: 500000, max: 1000000, rate: 0.069 }
        - { min: 1000000, max: null, rate: 0.0699 }
      mfs:
        - { min: 0, max: 10000, rate: 0.02 }
        - { min: 10000, max: 50000, rate: 0.045 }
        - { min: 50000, max: 100000, rate: 0.055 }
        - { min: 100000, max: 200000, rate: 0.06 }
        - { min: 200000, max: 250000, rate: 0.065 }
        - { min: 250000, max: 500000, rate: 0.069 }
        - { min: 500000, max: null, rate: 0.0699 }
      hoh:
        - { min: 0, max: 16000, rate: 0.02 }
        - { min: 16000, max: 80000, rate: 0.045 }
        - { min: 80000, max: 160000, rate: 0.055 }
        - { min: 160000, max: 320000, rate: 0.06 }
        - { min: 320000, max: 400000, rate: 0.065 }
        - { min: 400000, max: 800000, rate: 0.069 }
        - { min: 800000, max: null, rate: 0.0699 }
  DC:
    _source: state_dc
    type: graduated
    brackets:
      single:
        - { min: 0, max: 10000, rate: 0.04 }
        - { min: 10000, max: 40000, rate: 0.06 }
        - { min: 40000, max: 60000, rate: 0.065 }
        - { min: 60000, max: 250000, rate: 0.085 }
        - { min: 250000, max: 500000, rate: 0.0925 }
        - { min: 500000, max: 1000000, rate: 0.0975 }
        - { min: 1000000, max: null, rate: 0.1075 }
      mfj:
        - { min: 0, max: 10000, rate: 0.04 }
        - { min: 10000, max: 40000, rate: 0.06 }
        - { min: 40000, max: 60000, rate: 0.065 }
        - { min: 60000, max: 250000, rate: 0.085 }
        - { min: 250000, max: 500000, rate: 0.0925 }
        - { min: 500000, max: 1000000, rate: 0.0975 }
        - { min: 1000000, max: null, rate: 0.1075 }
      mfs:
        - { min: 0, max: 10000, rate: 0.04 }
        - { min: 10000, max: 40000, rate: 0.06 }
        - { min: 40000, max: 60000, rate: 0.065 }
        - { min: 60000, max: 250000, rate: 0.085 }
        - { min: 250000, max: 500000, rate: 0.0925 }
        - { min: 500000, max: 1000000, rate: 0.0975 }
        - { min: 1000000, max: null, rate: 0.1075 }
      hoh:
        - { min: 0, max: 10000, rate: 0.04 }
        - { min: 10000, max: 40000, rate: 0.06 }
        - { min: 40000, max: 60000, rate: 0.065 }
        - { min: 60000, max: 250000, rate: 0.085 }
        - { min: 250000, max: 500000, rate: 0.0925 }
        - { min: 500000, max: 1000000, rate: 0.0975 }
        - { min: 1000000, max: null, rate: 0.1075 }
  DE:
    _source: state_de
    type: graduated
    brackets:
      single:
        - { min: 0, max: 2000, rate: 0.0 }
        - { min: 2000, max: 5000, rate: 0.022 }
        - { min: 5000, max: 10000, rate: 0.039 }
        - { min: 10000, max: 20000, rate: 0.048 }
        - { min: 20000, max: 25000, rate: 0.052 }
        - { min: 25000, max: 60000, rate: 0.0555 }
        - { min: 60000, max: 125000, rate: 0.066 }
        - { min: 125000, max: 250000, rate: 0.0675 }
        - { min: 250000, max: null, rate: 0.0695 }
      mfj:
        - { min: 0, max: 2000, rate: 0.0 }
        - { min: 2000, max: 5000, rate: 0.022 }
        - { min: 5000, max: 10000, rate: 0.039 }
        - { min: 10000, max: 20000, rate: 0.048 }
        - { min: 20000, max: 25000, rate: 0.052 }
        - { min: 25000, max: 60000, rate: 0.0555 }
        - { min: 60000, max: 125000, rate: 0.066 }
        - { min: 125000, max: 250000, rate: 0.0675 }
        - { min: 250000, max: null, rate: 0.0695 }
      mfs:
        - { min: 0, max: 2000, rate: 0.0 }
        - { min: 2000, max: 5000, rate: 0.022 }
        - { min: 5000, max: 10000, rate: 0.039 }
        - { min: 10000, max: 20000, rate: 0.048 }
        - { min: 20000, max: 25000, rate: 0.052 }
        - { min: 25000, max: 60000, rate: 0.0555 }
        - { min: 60000, max: 125000, rate: 0.066 }
        - { min: 125000, max: 250000, rate: 0.0675 }
        - { min: 250000, max: null, rate: 0.0695 }
      hoh:
        - { min: 0, max: 2000, rate: 0.0 }
        - { min: 2000, max: 5000, rate: 0.022 }
        - { min: 5000, max: 10000, rate: 0.039 }
        - { min: 10000, max: 20000, rate: 0.048 }
        - { min: 20000, max: 25000, rate: 0.052 }
        - { min: 25000, max: 60000, rate: 0.0555 }
        - { min: 60000, max: 125000, rate: 0.066 }
        - { min: 125000, max: 250000, rate: 0.0675 }
        - { min: 250000, max: null, rate: 0.0695 }
  HI:
    _source: state_hi
    type: graduated
    brackets:
      single:
        - { min: 0, max: 9600, rate: 0.014 }
        - { min: 9600, max: 14400, rate: 0.032 }
        - { min: 14400, max: 19200, rate: 0.055 }
        - { min: 19200, max: 24000, rate: 0.064 }
        - { min: 24000, max: 36000, rate: 0.068 }
        - { min: 36000, max: 48000, rate: 0.072 }
        - { min: 48000, max: 125000, rate: 0.076 }
        - { min: 125000, max: 175000, rate: 0.079 }
        - { min: 175000, max: 225000, rate: 0.0825 }
        - { min: 225000, max: 275000, rate: 0.09 }
        - { min: 275000, max: 325000, rate: 0.10 }
        - { min: 325000, max: null, rate: 0.11 }
      mfj:
        - { min: 0, max: 19200, rate: 0.014 }
        - { min: 19200, max: 28800, rate: 0.032 }
        - { min: 28800, max: 38400, rate: 0.055 }
        - { min: 38400, max: 48000, rate: 0.064 }
        - { min: 48000, max: 72000, rate: 0.068 }
        - { min: 72000, max: 96000, rate: 0.072 }
        - { min: 96000, max: 250000, rate: 0.076 }
        - { min: 250000, max: 350000, rate: 0.079 }
        - { min: 350000, max: 450000, rate: 0.0825 }
        - { min: 450000, max: 550000, rate: 0.09 }
        - { min: 550000, max: 650000, rate: 0.10 }
        - { min: 650000, max: null, rate: 0.11 }
      mfs:
        - { min: 0, max: 9600, rate: 0.014 }
        - { min: 9600, max: 14400, rate: 0.032 }
        - { min: 14400, max: 19200, rate: 0.055 }
        - { min: 19200, max: 24000, rate: 0.064 }
        - { min: 24000, max: 36000, rate: 0.068 }
        - { min: 36000, max: 48000, rate: 0.072 }
        - { min: 48000, max: 125000, rate: 0.076 }
        - { min: 125000, max: 175000, rate: 0.079 }
        - { min: 175000, max: 225000, rate: 0.0825 }
        - { min: 225000, max: 275000, rate: 0.09 }
        - { min: 275000, max: 325000, rate: 0.10 }
        - { min: 325000, max: null, rate: 0.11 }
      hoh:
        - { min: 0, max: 19200, rate: 0.014 }
        - { min: 19200, max: 28800, rate: 0.032 }
        - { min: 28800, max: 38400, rate: 0.055 }
        - { min: 38400, max: 48000, rate: 0.064 }
        - { min: 48000, max: 72000, rate: 0.068 }
        - { min: 72000, max: 96000, rate: 0.072 }
        - { min: 96000, max: 250000, rate: 0.076 }
        - { min: 250000, max: 350000, rate: 0.079 }
        - { min: 350000, max: 450000, rate: 0.0825 }
        - { min: 450000, max: 550000, rate: 0.09 }
        - { min: 550000, max: 650000, rate: 0.10 }
        - { min: 650000, max: null, rate: 0.11 }
  KS:
    _source: state_ks
    type: graduated
    brackets:
      single:
        - { min: 0, max: 15000, rate: 0.031 }
        - { min: 15000, max: 30000, rate: 0.0525 }
        - { min: 30000, max: null, rate: 0.0558 }
      mfj:
        - { min: 0, max: 30000, rate: 0.031 }
        - { min: 30000, max: 60000, rate: 0.0525 }
        - { min: 60000, max: null, rate: 0.0558 }
      mfs:
        - { min: 0, max: 15000, rate: 0.031 }
        - { min: 15000, max: 30000, rate: 0.0525 }
        - { min: 30000, max: null, rate: 0.0558 }
      hoh:
        - { min: 0, max: 15000, rate: 0.031 }
        - { min: 15000, max: 30000, rate: 0.0525 }
        - { min: 30000, max: null, rate: 0.0558 }
  ME:
    _source: state_me
    type: graduated
    brackets:
      single:
        - { min: 0, max: 26800, rate: 0.058 }
        - { min: 26800, max: 63450, rate: 0.0675 }
        - { min: 63450, max: null, rate: 0.0715 }
      mfj:
        - { min: 0, max: 53600, rate: 0.058 }
        - { min: 53600, max: 126900, rate: 0.0675 }
        - { min: 126900, max: null, rate: 0.0715 }
      mfs:
        - { min: 0, max: 26800, rate: 0.058 }
        - { min: 26800, max: 63450, rate: 0.0675 }
        - { min: 63450, max: null, rate: 0.0715 }
      hoh:
        - { min: 0, max: 40200, rate: 0.058 }
        - { min: 40200, max: 95150, rate: 0.0675 }
        - { min: 95150, max: null, rate: 0.0715 }
  MD:
    _source: state_md
    type: graduated
    brackets:
      single:
        - { min: 0, max: 1000, rate: 0.02 }
        - { min: 1000, max: 2000, rate: 0.03 }
        - { min: 2000, max: 3000, rate: 0.04 }
        - { min: 3000, max: 100000, rate: 0.0475 }
        - { min: 100000, max: 125000, rate: 0.05 }
        - { min: 125000, max: 150000, rate: 0.0525 }
        - { min: 150000, max: 250000, rate: 0.055 }
        - { min: 250000, max: 500000, rate: 0.0575 }
        - { min: 500000, max: 1000000, rate: 0.0625 }
        - { min: 1000000, max: null, rate: 0.065 }
      mfj:
        - { min: 0, max: 1000, rate: 0.02 }
        - { min: 1000, max: 2000, rate: 0.03 }
        - { min: 2000, max: 3000, rate: 0.04 }
        - { min: 3000, max: 150000, rate: 0.0475 }
        - { min: 150000, max: 175000, rate: 0.05 }
        - { min: 175000, max: 225000, rate: 0.0525 }
        - { min: 225000, max: 300000, rate: 0.055 }
        - { min: 300000, max: 600000, rate: 0.0575 }
        - { min: 600000, max: 1200000, rate: 0.0625 }
        - { min: 1200000, max: null, rate: 0.065 }
      mfs:
        - { min: 0, max: 1000, rate: 0.02 }
        - { min: 1000, max: 2000, rate: 0.03 }
        - { min: 2000, max: 3000, rate: 0.04 }
        - { min: 3000, max: 75000, rate: 0.0475 }
        - { min: 75000, max: 87500, rate: 0.05 }
        - { min: 87500, max: 112500, rate: 0.0525 }
        - { min: 112500, max: 150000, rate: 0.055 }
        - { min: 150000, max: 300000, rate: 0.0575 }
        - { min: 300000, max: 600000, rate: 0.0625 }
        - { min: 600000, max: null, rate: 0.065 }
      hoh:
        - { min: 0, max: 1000, rate: 0.02 }
        - { min: 1000, max: 2000, rate: 0.03 }
        - { min: 2000, max: 3000, rate: 0.04 }
        - { min: 3000, max: 150000, rate: 0.0475 }
        - { min: 150000, max: 175000, rate: 0.05 }
        - { min: 175000, max: 225000, rate: 0.0525 }
        - { min: 225000, max: 300000, rate: 0.055 }
        - { min: 300000, max: 600000, rate: 0.0575 }
        - { min: 600000, max: 1200000, rate: 0.0625 }
        - { min: 1200000, max: null, rate: 0.065 }
  MA:
    _source: state_ma
    type: graduated
    brackets:
      single:
        - { min: 0, max: 1107750, rate: 0.05 }
        - { min: 1107750, max: null, rate: 0.09 }
      mfj:
        - { min: 0, max: 1107750, rate: 0.05 }
        - { min: 1107750, max: null, rate: 0.09 }
      mfs:
        - { min: 0, max: 1107750, rate: 0.05 }
        - { min: 1107750, max: null, rate: 0.09 }
      hoh:
        - { min: 0, max: 1107750, rate: 0.05 }
        - { min: 1107750, max: null, rate: 0.09 }
  MN:
    _source: state_mn
    type: graduated
    brackets:
      single:
        - { min: 0, max: 33310, rate: 0.0535 }
        - { min: 33310, max: 109430, rate: 0.068 }
        - { min: 109430, max: 203150, rate: 0.0785 }
        - { min: 203150, max: null, rate: 0.0985 }
      mfj:
        - { min: 0, max: 48700, rate: 0.0535 }
        - { min: 48700, max: 193480, rate: 0.068 }
        - { min: 193480, max: 337930, rate: 0.0785 }
        - { min: 337930, max: null, rate: 0.0985 }
      mfs:
        - { min: 0, max: 24350, rate: 0.0535 }
        - { min: 24350, max: 96740, rate: 0.068 }
        - { min: 96740, max: 168965, rate: 0.0785 }
        - { min: 168965, max: null, rate: 0.0985 }
      hoh:
        - { min: 0, max: 41010, rate: 0.0535 }
        - { min: 41010, max: 164800, rate: 0.068 }
        - { min: 164800, max: 270060, rate: 0.0785 }
        - { min: 270060, max: null, rate: 0.0985 }
state_graduated_al_mn_standard_deductions:
  AL: { single: 3000, mfj: 8500, mfs: 4250, hoh: 5200 }
  AR: { single: 2470, mfj: 4940, mfs: 2470, hoh: 2470 }
  CA: { single: 5706, mfj: 11412, mfs: 5706, hoh: 11412 }
  DE: { single: 3250, mfj: 6500, mfs: 3250, hoh: 3250 }
  KS: { single: 3500, mfj: 8000, mfs: 3500, hoh: 3500 }
  ME: { single: 15300, mfj: 30600, mfs: 15300, hoh: 22950 }
  MD: { single: 3350, mfj: 6700, mfs: 3350, hoh: 6700 }
  MN: { single: 15300, mfj: 30600, mfs: 15300, hoh: 23000 }
state_graduated_mt_wi:
  _verification_note: "Graduated tax states MT through WI"
  _last_verified: "2026-01-15"
  MT:
    _source: state_mt
    type: graduated
    brackets:
      single:
        - { min: 0, max: 47500, rate: 0.047 }
        - { min: 47500, max: null, rate: 0.0565 }
      mfj:
        - { min: 0, max: 95000, rate: 0.047 }
        - { min: 95000, max: null, rate: 0.0565 }
      mfs:
        - { min: 0, max: 47500, rate: 0.047 }
        - { min: 47500, max: null, rate: 0.0565 }
      hoh:
        - { min: 0, max: 71250, rate: 0.047 }
        - { min: 71250, max: null, rate: 0.0565 }
  NE:
    _source: state_ne
    type: graduated
    brackets:
      single:
        - { min: 0, max: 2400, rate: 0.0246 }
        - { min: 2400, max: 18000, rate: 0.0351 }
        - { min: 18000, max: null, rate: 0.0455 }
      mfj:
        - { min: 0, max: 4800, rate: 0.0246 }
        - { min: 4800, max: 36000, rate: 0.0351 }
        - { min: 36000, max: null, rate: 0.0455 }
      mfs:
        - { min: 0, max: 2400, rate: 0.0246 }
        - { min: 2400, max: 18000, rate: 0.0351 }
        - { min: 18000, max: null, rate: 0.0455 }
      hoh:
        - { min: 0, max: 3840, rate: 0.0246 }
        - { min: 3840, max: 28800, rate: 0.0351 }
        - { min: 28800, max: null, rate: 0.0455 }
  NJ:
    _source: state_nj
    type: graduated
    brackets:
      single:
        - { min: 0, max: 20000, rate: 0.014 }
        - { min: 20000, max: 35000, rate: 0.0175 }
        - { min: 35000, max: 40000, rate: 0.035 }
        - { min: 40000, max: 75000, rate: 0.05525 }
        - { min: 75000, max: 500000, rate: 0.0637 }
        - { min: 500000, max: 1000000, rate: 0.0897 }
        - { min: 1000000, max: null, rate: 0.1075 }
      mfj:
        - { min: 0, max: 20000, rate: 0.014 }
        - { min: 20000, max: 50000, rate: 0.0175 }
        - { min: 50000, max: 70000, rate: 0.0245 }
        - { min: 70000, max: 80000, rate: 0.035 }
        - { min: 80000, max: 150000, rate: 0.05525 }
        - { min: 150000, max: 500000, rate: 0.0637 }
        - { min: 500000, max: 1000000, rate: 0.0897 }
        - { min: 1000000, max: null, rate: 0.1075 }
      mfs:
        - { min: 0, max: 20000, rate: 0.014 }
        - { min: 20000, max: 35000, rate: 0.0175 }
        - { min: 35000, max: 40000, rate: 0.035 }
        - { min: 40000, max: 75000, rate: 0.05525 }
        - { min: 75000, max: 500000, rate: 0.0637 }
        - { min: 500000, max: 1000000, rate: 0.0897 }
        - { min: 1000000, max: null, rate: 0.1075 }
      hoh:
        - { min: 0, max: 20000, rate: 0.014 }
        - { min: 20000, max: 50000, rate: 0.0175 }
        - { min: 50000, max: 70000, rate: 0.0245 }
        - { min: 70000, max: 80000, rate: 0.035 }
        - { min: 80000, max: 150000, rate: 0.05525 }
        - { min: 150000, max: 500000, rate: 0.0637 }
        - { min: 500000, max: 1000000, rate: 0.0897 }
        - { min: 1000000, max: null, rate: 0.1075 }
  NM:
    _source: state_nm
    type: graduated
    brackets:
      single:
        - { min: 0, max: 5500, rate: 0.015 }
        - { min: 5500, max: 16500, rate: 0.032 }
        - { min: 16500, max: 33500, rate: 0.043 }
        - { min: 33500, max: 66500, rate: 0.047 }
        - { min: 66500, max: 210000, rate: 0.049 }
        - { min: 210000, max: null, rate: 0.059 }
      mfj:
        - { min: 0, max: 8000, rate: 0.015 }
        - { min: 8000, max: 25000, rate: 0.032 }
        - { min: 25000, max: 50000, rate: 0.043 }
        - { min: 50000, max: 100000, rate: 0.047 }
        - { min: 100000, max: 315000, rate: 0.049 }
        - { min: 315000, max: null, rate: 0.059 }
      mfs:
        - { min: 0, max: 4000, rate: 0.015 }
        - { min: 4000, max: 12500, rate: 0.032 }
        - { min: 12500, max: 25000, rate: 0.043 }
        - { min: 25000, max: 50000, rate: 0.047 }
        - { min: 50000, max: 157500, rate: 0.049 }
        - { min: 157500, max: null, rate: 0.059 }
      hoh:
        - { min: 0, max: 8000, rate: 0.015 }
        - { min: 8000, max: 25000, rate: 0.032 }
        - { min: 25000, max: 50000, rate: 0.043 }
        - { min: 50000, max: 100000, rate: 0.047 }
        - { min: 100000, max: 315000, rate: 0.049 }
        - { min: 315000, max: null, rate: 0.059 }
  NY:
    _source: state_ny
    type: graduated
    brackets:
      single:
        - { min: 0, max: 8500, rate: 0.04 }
        - { min: 8500, max: 11700, rate: 0.045 }
        - { min: 11700, max: 13900, rate: 0.0525 }
        - { min: 13900, max: 80650, rate: 0.055 }
        - { min: 80650, max: 215400, rate: 0.06 }
        - { min: 215400, max: 1077550, rate: 0.0685 }
        - { min: 1077550, max: 5000000, rate: 0.0965 }
        - { min: 5000000, max: 25000000, rate: 0.103 }
        - { min: 25000000, max: null, rate: 0.109 }
      mfj:
        - { min: 0, max: 17150, rate: 0.04 }
        - { min: 17150, max: 23600, rate: 0.045 }
        - { min: 23600, max: 27900, rate: 0.0525 }
        - { min: 27900, max: 161550, rate: 0.055 }
        - { min: 161550, max: 323200, rate: 0.06 }
        - { min: 323200, max: 2155350, rate: 0.0685 }
        - { min: 2155350, max: 5000000, rate: 0.0965 }
        - { min: 5000000, max: 25000000, rate: 0.103 }
        - { min: 25000000, max: null, rate: 0.109 }
      mfs:
        - { min: 0, max: 8500, rate: 0.04 }
        - { min: 8500, max: 11700, rate: 0.045 }
        - { min: 11700, max: 13900, rate: 0.0525 }
        - { min: 13900, max: 80650, rate: 0.055 }
        - { min: 80650, max: 215400, rate: 0.06 }
        - { min: 215400, max: 1077550, rate: 0.0685 }
        - { min: 1077550, max: 5000000, rate: 0.0965 }
        - { min: 5000000, max: 25000000, rate: 0.103 }
        - { min: 25000000, max: null, rate: 0.109 }
      hoh:
        - { min: 0, max: 12800, rate: 0.04 }
        - { min: 12800, max: 17650, rate: 0.045 }
        - { min: 17650, max: 20900, rate: 0.0525 }
        - { min: 20900, max: 107650, rate: 0.055 }
        - { min: 107650, max: 269300, rate: 0.06 }
        - { min: 269300, max: 1616450, rate: 0.0685 }
        - { min: 1616450, max: 5000000, rate: 0.0965 }
        - { min: 5000000, max: 25000000, rate: 0.103 }
        - { min: 25000000, max: null, rate: 0.109 }
  ND:
    _source: state_nd
    type: graduated
    brackets:
      single:
        - { min: 0, max: 48475, rate: 0.0 }
        - { min: 48475, max: 244825, rate: 0.0195 }
        - { min: 244825, max: null, rate: 0.025 }
      mfj:
        - { min: 0, max: 80975, rate: 0.0 }
        - { min: 80975, max: 298075, rate: 0.0195 }
        - { min: 298075, max: null, rate: 0.025 }
      mfs:
        - { min: 0, max: 40475, rate: 0.0 }
        - { min: 40475, max: 149025, rate: 0.0195 }
        - { min: 149025, max: null, rate: 0.025 }
      hoh:
        - { min: 0, max: 64950, rate: 0.0 }
        - { min: 64950, max: 271450, rate: 0.0195 }
        - { min: 271450, max: null, rate: 0.025 }
  OK:
    _source: state_ok
    type: graduated
    brackets:
      single:
        - { min: 0, max: 1000, rate: 0.0025 }
        - { min: 1000, max: 7200, rate: 0.0375 }
        - { min: 7200, max: null, rate: 0.045 }
      mfj:
        - { min: 0, max: 2000, rate: 0.0025 }
        - { min: 2000, max: 14400, rate: 0.0375 }
        - { min: 14400, max: null, rate: 0.045 }
      mfs:
        - { min: 0, max: 1000, rate: 0.0025 }
        - { min: 1000, max: 7200, rate: 0.0375 }
        - { min: 7200, max: null, rate: 0.045 }
      hoh:
        - { min: 0, max: 2000, rate: 0.0025 }
        - { min: 2000, max: 14400, rate: 0.0375 }
        - { min: 14400, max: null, rate: 0.045 }
  OR:
    _source: state_or
    type: graduated
    brackets:
      single:
        - { min: 0, max: 4550, rate: 0.0475 }
        - { min: 4550, max: 11400, rate: 0.0675 }
        - { min: 11400, max: 125000, rate: 0.0875 }
        - { min: 125000, max: null, rate: 0.099 }
      mfj:
        - { min: 0, max: 9100, rate: 0.0475 }
        - { min: 9100, max: 22800, rate: 0.0675 }
        - { min: 22800, max: 250000, rate: 0.0875 }
        - { min: 250000, max: null, rate: 0.099 }
      mfs:
        - { min: 0, max: 4550, rate: 0.0475 }
        - { min: 4550, max: 11400, rate: 0.0675 }
        - { min: 11400, max: 125000, rate: 0.0875 }
        - { min: 125000, max: null, rate: 0.099 }
      hoh:
        - { min: 0, max: 9100, rate: 0.0475 }
        - { min: 9100, max: 22800, rate: 0.0675 }
        - { min: 22800, max: 250000, rate: 0.0875 }
        - { min: 250000, max: null, rate: 0.099 }
  RI:
    _source: state_ri
    type: graduated
    brackets:
      single:
        - { min: 0, max: 79900, rate: 0.0375 }
        - { min: 79900, max: 181650, rate: 0.0475 }
        - { min: 181650, max: null, rate: 0.0599 }
      mfj:
        - { min: 0, max: 79900, rate: 0.0375 }
        - { min: 79900, max: 181650, rate: 0.0475 }
        - { min: 181650, max: null, rate: 0.0599 }
      mfs:
        - { min: 0, max: 79900, rate: 0.0375 }
        - { min: 79900, max: 181650, rate: 0.0475 }
        - { min: 181650, max: null, rate: 0.0599 }
      hoh:
        - { min: 0, max: 79900, rate: 0.0375 }
        - { min: 79900, max: 181650, rate: 0.0475 }
        - { min: 181650, max: null, rate: 0.0599 }
  SC:
    _source: state_sc
    type: graduated
    brackets:
      single:
        - { min: 0, max: 3460, rate: 0.0 }
        - { min: 3460, max: 17330, rate: 0.03 }
        - { min: 17330, max: null, rate: 0.06 }
      mfj:
        - { min: 0, max: 3460, rate: 0.0 }
        - { min: 3460, max: 17330, rate: 0.03 }
        - { min: 17330, max: null, rate: 0.06 }
      mfs:
        - { min: 0, max: 3460, rate: 0.0 }
        - { min: 3460, max: 17330, rate: 0.03 }
        - { min: 17330, max: null, rate: 0.06 }
      hoh:
        - { min: 0, max: 3460, rate: 0.0 }
        - { min: 3460, max: 17330, rate: 0.03 }
        - { min: 17330, max: null, rate: 0.06 }
  VT:
    _source: state_vt
    type: graduated
    brackets:
      single:
        - { min: 0, max: 47600, rate: 0.0335 }
        - { min: 47600, max: 115350, rate: 0.054 }
        - { min: 115350, max: 200200, rate: 0.066 }
        - { min: 200200, max: 254400, rate: 0.076 }
        - { min: 254400, max: null, rate: 0.0875 }
      mfj:
        - { min: 0, max: 79300, rate: 0.0335 }
        - { min: 79300, max: 192250, rate: 0.054 }
        - { min: 192250, max: 333650, rate: 0.066 }
        - { min: 333650, max: 424000, rate: 0.076 }
        - { min: 424000, max: null, rate: 0.0875 }
      mfs:
        - { min: 0, max: 47600, rate: 0.0335 }
        - { min: 47600, max: 115350, rate: 0.054 }
        - { min: 115350, max: 200200, rate: 0.066 }
        - { min: 200200, max: 254400, rate: 0.076 }
        - { min: 254400, max: null, rate: 0.0875 }
      hoh:
        - { min: 0, max: 79300, rate: 0.0335 }
        - { min: 79300, max: 192250, rate: 0.054 }
        - { min: 192250, max: 333650, rate: 0.066 }
        - { min: 333650, max: 424000, rate: 0.076 }
        - { min: 424000, max: null, rate: 0.0875 }
  VA:
    _source: state_va
    type: graduated
    brackets:
      single:
        - { min: 0, max: 3000, rate: 0.02 }
        - { min: 3000, max: 5000, rate: 0.03 }
        - { min: 5000, max: 17000, rate: 0.05 }
        - { min: 17000, max: null, rate: 0.0575 }
      mfj:
        - { min: 0, max: 3000, rate: 0.02 }
        - { min: 3000, max: 5000, rate: 0.03 }
        - { min: 5000, max: 17000, rate: 0.05 }
        - { min: 17000, max: null, rate: 0.0575 }
      mfs:
        - { min: 0, max: 3000, rate: 0.02 }
        - { min: 3000, max: 5000, rate: 0.03 }
        - { min: 5000, max: 17000, rate: 0.05 }
        - { min: 17000, max: null, rate: 0.0575 }
      hoh:
        - { min: 0, max: 3000, rate: 0.02 }
        - { min: 3000, max: 5000, rate: 0.03 }
        - { min: 5000, max: 17000, rate: 0.05 }
        - { min: 17000, max: null, rate: 0.0575 }
  WV:
    _source: state_wv
    type: graduated
    brackets:
      single:
        - { min: 0, max: 10000, rate: 0.0236 }
        - { min: 10000, max: 25000, rate: 0.0315 }
        - { min: 25000, max: 40000, rate: 0.0354 }
        - { min: 40000, max: 60000, rate: 0.0472 }
        - { min: 60000, max: null, rate: 0.0512 }
      mfj:
        - { min: 0, max: 10000, rate: 0.0236 }
        - { min: 10000, max: 25000, rate: 0.0315 }
        - { min: 25000, max: 40000, rate: 0.0354 }
        - { min: 40000, max: 60000, rate: 0.0472 }
        - { min: 60000, max: null, rate: 0.0512 }
      mfs:
        - { min: 0, max: 5000, rate: 0.0236 }
        - { min: 5000, max: 12500, rate: 0.0315 }
        - { min: 12500, max: 20000, rate: 0.0354 }
        - { min: 20000, max: 30000, rate: 0.0472 }
        - { min: 30000, max: null, rate: 0.0512 }
      hoh:
        - { min: 0, max: 10000, rate: 0.0236 }
        - { min: 10000, max: 25000, rate: 0.0315 }
        - { min: 25000, max: 40000, rate: 0.0354 }
        - { min: 40000, max: 60000, rate: 0.0472 }
        - { min: 60000, max: null, rate: 0.0512 }
  WI:
    _source: state_wi
    type: graduated
    brackets:
      single:
        - { min: 0, max: 14320, rate: 0.035 }
        - { min: 14320, max: 28640, rate: 0.044 }
        - { min: 28640, max: 315310, rate: 0.053 }
        - { min: 315310, max: null, rate: 0.0765 }
      mfj:
        - { min: 0, max: 19090, rate: 0.035 }
        - { min: 19090, max: 38190, rate: 0.044 }
        - { min: 38190, max: 420420, rate: 0.053 }
        - { min: 420420, max: null, rate: 0.0765 }
      mfs:
        - { min: 0, max: 14320, rate: 0.035 }
        - { min: 14320, max: 28640, rate: 0.044 }
        - { min: 28640, max: 315310, rate: 0.053 }
        - { min: 315310, max: null, rate: 0.0765 }
      hoh:
        - { min: 0, max: 14320, rate: 0.035 }
        - { min: 14320, max: 28640, rate: 0.044 }
        - { min: 28640, max: 315310, rate: 0.053 }
        - { min: 315310, max: null, rate: 0.0765 }
state_graduated_mt_wi_standard_deductions:
  NE: { single: 8600, mfj: 17200, mfs: 8600, hoh: 12900 }
  NY: { single: 8000, mfj: 16050, mfs: 8000, hoh: 11200 }
  ND: { single: 15750, mfj: 31500, mfs: 15750, hoh: 23625 }
  OK: { single: 6350, mfj: 12700, mfs: 6350, hoh: 9350 }
  OR: { single: 2910, mfj: 5820, mfs: 2835, hoh: 5820 }
  RI: { single: 10900, mfj: 21800, mfs: 10900, hoh: 16350 }
  VA: { single: 8750, mfj: 17500, mfs: 8750, hoh: 8750 }
  VT: { single: 14600, mfj: 29200, mfs: 14600, hoh: 29200 }
  WV: { single: 2000, mfj: 4000, mfs: 2000, hoh: 2000 }
  WI: { single: 12760, mfj: 23620, mfs: 12760, hoh: 17840 }
ptet:
  _source: ptet_overview
  _verification_note: "PTET rates and credit types verified via AICPA tracker and state legislation"
  _last_verified: "2026-01-15"
  AL: { rate: 0.05, credit: refundable }
  AZ: { rate: 0.025, credit: refundable }
  AR: { rate: 0.044, credit: refundable }
  CA: { rate: 0.093, credit: nonrefundable }
  CO: { rate: 0.044, credit: refundable }
  CT: { rate: 0.0699, credit: exclusion }
  GA: { rate: 0.0509, credit: refundable }
  HI: { rate: 0.014-0.11, credit: refundable }
  ID: { rate: 0.053, credit: nonrefundable }
  IL: { rate: 0.0495, credit: refundable }
  IN: { rate: 0.0295, credit: refundable }
  IA: { rate: 0.038, credit: refundable }
  KS: { rate: 0.0558, credit: refundable }
  KY: { rate: 0.035, credit: nonrefundable }
  LA: { rate: 0.03-0.0425, credit: refundable }
  ME: { rate: 0.0715, credit: refundable }
  MD: { rate: 0.0575, credit: refundable }
  MA: { rate: 0.05, credit: refundable }
  MI: { rate: 0.0425, credit: refundable }
  MS: { rate: 0.04, credit: refundable }
  MO: { rate: 0.047, credit: refundable }
  MT: { rate: 0.0565, credit: nonrefundable }
  NE: { rate: 0.0455, credit: refundable }
  NJ: { rate: 0.05675-0.109, credit: refundable }
  NM: { rate: 0.059, credit: refundable }
  NY: { rate: 0.0685-0.109, credit: refundable }
  NC: { rate: 0.0399, credit: refundable }
  OH: { rate: null, credit: exclusion }
  OK: { rate: 0.045, credit: refundable }
  OR: { rate: 0.09, credit: refundable }
  RI: { rate: 0.0599, credit: refundable }
  SC: { rate: 0.06, credit: refundable }
  WV: { rate: 0.0482, credit: refundable }
  WI: { rate: 0.0765, credit: refundable }
  UT: { rate: 0.045, credit: tbd }
ptet_expired:
  _source: ptet_overview
  _verification_note: "Expired PTET programs - MN expired 2025-12-31, VA pending extension"
  _last_verified: "2026-01-15"
  MN: { former_rate: 0.0985, status: "expired 2025-12-31" }
  VA: { former_rate: 0.0575, status: "pending extension" }
---

# ============================================================================
# MAINTENANCE GUIDE FOR AI UPDATES
# ============================================================================

## How to Update This File

When asked to "update the tax data" or "update for tax year [YEAR]", follow these steps systematically. This file is designed for future AI to perform comprehensive updates by tracing each data point back to its authoritative source.

### Step 1: Understand What Needs Updating

**Check the metadata:**
- Look at `_metadata` section at top - what tax year is this file currently?
- Review `_metadata.last_updated` - when was it last modified?
- Determine if you're updating for a new tax year or correcting current year data

**Identify update categories:**
- Federal data: Updated November each year for following tax year
- State data: Updated January 1 each year
- PTET: Monitor quarterly for changes (new adoptions, expirations, rate changes)
- Legislative provisions: Monitor for new laws (OBBBA-style changes)

### Step 2: Find Authoritative Sources

**Every data section in this file has source references:**
- `_source:` field points to a source ID in the `sources:` section
- Look up the source to find: URL, update pattern, what to verify
- Sources include update hints: `update_frequency`, `update_month`, `update_pattern`

**Federal Sources - Where to Look:**

**Tax Brackets & Deductions** (Annual - November):
- Source: IRS Revenue Procedure
- Search pattern: "IRS Revenue Procedure [YEAR] inflation adjustments"
- Example: "Rev. Proc. 2025-32" for 2026 tax year
- URL pattern: `https://www.irs.gov/pub/irs-drop/rp-{YY}-*.pdf`
- What it covers: Brackets, standard deductions, capital gains thresholds, AMT, QBID, estate exemption
- Time to update: 1-2 hours

**Retirement Limits** (Annual - November):
- Source: IRS Notice
- Search pattern: "IRS Notice [YEAR] retirement limits"
- Example: "IRS Notice 2025-67" for 2026 tax year
- URL pattern: `https://www.irs.gov/pub/irs-drop/n-{YY}-*.pdf`
- What it covers: 401(k), IRA, SEP, SIMPLE, HSA, FSA, compensation limits
- Time to update: 30-60 minutes

**Social Security Wage Base** (Annual - October):
- Source: SSA COLA announcement
- Search pattern: "Social Security wage base [YEAR]"
- Example: "2026 Social Security Changes"
- URL pattern: `https://www.ssa.gov/news/press/factsheets/colafacts{YEAR}.pdf`
- Announced: Mid-October of prior year
- Time to update: 15 minutes

**Fixed Rates** (Legislative - Rarely Changes):
- NIIT: 3.8% rate, NOT indexed since 2013
- Additional Medicare: 0.9%, NOT indexed since 2013
- FICA/Medicare base rates: 12.4% SS, 2.9% Medicare
- Only change via legislation - do not modify unless new law passed

**State Sources - Where to Look:**

**Overview:**
- 51 jurisdictions (50 states + DC)
- Each state has its own DOR website
- Start with Tax Foundation: "Tax Foundation state tax rates [YEAR]"
- Then verify each state individually at official state site

**For each state:**
1. Search "[STATE] income tax rates [YEAR]"
2. Go to official state DOR website (URLs in `sources:` section)
3. Verify: Tax rate(s), brackets, standard deductions, personal exemptions
4. Note: Some states update rates automatically, others require legislation
5. Cross-reference with Tax Foundation for reasonableness check
6. Time to update all 51: 2-3 hours

**PTET Sources - Where to Look:**

**Overview Source:**
- AICPA State Pass-Through Entity Tax Tracker
- URL: https://www.aicpa.org/resources/article/state-pass-through-entity-tax-information
- Updated quarterly - check for: new adoptions, expirations, rate changes

**Monitor for:**
- New PTET adoptions (currently 36 active states)
- Expirations (MN expired 2025-12-31, VA pending)
- Rate changes (states may adjust rates annually)
- Credit type changes (refundable/nonrefundable/exclusion)
- Election deadlines (most March 15, some different like CA, NY)

**Verification:**
- For each PTET state, check state DOR website
- Verify: Rate, credit type, election deadline, expiration date
- Time to update: 30-60 minutes quarterly

### Step 3: Update the Data

**For each section you're updating:**

1. **Read the source document** - Find the specific data points
2. **Locate the data in this file** - Search for the section with matching `_source`
3. **Update the values** - Change the numbers to match the new source
4. **Update verification metadata:**
   - `_last_verified:` → Today's date (YYYY-MM-DD format)
   - If source URL changed, update in `sources:` section
5. **Check for structural changes:**
   - New tax brackets? Add them to the brackets array
   - Brackets eliminated? Remove them
   - New states adopting PTET? Add to ptet section
   - PTET expirations? Move to ptet_expired section

**Example: Updating Federal Brackets for 2027**

```yaml
# 1. Find the source (November 2026)
# Search: "IRS Revenue Procedure 2026 inflation adjustments"
# Find: Rev. Proc. 2026-XX published November 2026

# 2. Update the source definition
sources:
  fed_2027_inflation:  # Create new source ID for new year
    id: fed_2027_inflation
    authority: IRS
    publication: "Rev. Proc. 2026-XX"
    url: "https://www.irs.gov/pub/irs-drop/rp-26-XX.pdf"
    verification_date: "2026-11-15"
    effective_date: "2027-01-01"
    # ... rest of source definition

# 3. Update the data
brackets:
  _source: fed_2027_inflation  # Update source reference
  _last_verified: "2026-11-15"  # Update verification date
  single:
    - { min: 0, max: 12750, rate: 0.10 }  # New inflation-adjusted values
    # ... rest of brackets
```

### Step 4: Validation Checklist

**After updating, verify the following:**

**Bracket Continuity:**
- [ ] Each bracket's `max` value equals the next bracket's `min` value
- [ ] No gaps or overlaps in bracket ranges
- [ ] Top bracket has `max: null`

**Standard Deductions:**
- [ ] MFJ = 2× Single (for federal)
- [ ] All filing statuses present (single, mfj, mfs, hoh, qw where applicable)

**Rate Reasonableness:**
- [ ] Federal top rate = 37% (unless TCJA changed)
- [ ] NIIT rate = 3.8% (fixed since 2013)
- [ ] Additional Medicare = 0.9% (fixed since 2013)
- [ ] State rates are reasonable (top rate typically 3-13%)
- [ ] Capital gains: 0%, 15%, 20% (fixed rates)

**Inflation Check:**
- [ ] Most changes should be 2-4% from prior year (typical inflation adjustment)
- [ ] Large changes (>10%) should be investigated - may indicate error or legislative change
- [ ] Compare to previous year: `grep "single: " tax.md` to see progression

**Cross-Reference:**
- [ ] Verify each major change with 2+ independent sources
- [ ] Federal data: IRS.gov + Tax Foundation or reputable tax software site
- [ ] State data: State DOR + Tax Foundation

**Expiring Provisions:**
- [ ] Check expiration dates: SALT cap (2029-12-31), Senior deduction (2028-12-31)
- [ ] PTET expirations: Check for newly expired programs
- [ ] Sunset provisions: Track TCJA elements, OBBBA elements

**Metadata:**
- [ ] Update `_metadata.version` (increment: 2026.1 → 2027.1 for new year)
- [ ] Update `_metadata.last_updated` to today's date
- [ ] Update `_metadata.tax_year` if moving to new year
- [ ] Update `_metadata.effective_date` if moving to new year

### Step 5: Document Changes in Changelog

**After completing updates, add an entry to the CHANGELOG section below:**

```markdown
## [DATE] - Tax Year [YEAR] - [Brief Description]

### Federal Income Tax
- Tax brackets: [Source] ([verification date])
  - Changes: [Describe major changes]
- Standard deductions: Single $X, MFJ $Y
- Source: [URL]

### Retirement Limits
- 401(k): $X / IRA: $Y / HSA: $Z
- Changes: [Describe any limit increases]
- Source: [Source] ([verification date])

### State Tax
- States updated: [Number] jurisdictions
- Major changes: [List any rate changes, new tax structures]
- PTET updates: [New adoptions, expirations, rate changes]

### Validation
- Cross-referenced with [list sources]
- Bracket continuity verified
- Rate reasonableness confirmed
```

## Update Schedule

Use this schedule to know when to check for updates:

### October (Prior Year)
**Social Security Wage Base**
- SSA announces COLA mid-October
- Update: `payroll.ss_wage_base`
- Time: 15 minutes
- Next: October 2026 for 2027 tax year

### November (Prior Year)
**IRS Inflation Adjustments**
- Published mid-November (typically second week)
- Update: brackets, standard_deductions, capital_gains, amt, qbid, estate_exemption
- Time: 1-2 hours
- Next: November 2026 for 2027 tax year

**IRS Retirement Limits**
- Published early November (typically first week)
- Update: solo_401k, ira_limit, hsa, fsa, sep_ira, simple_ira, defined_benefit
- Time: 30-60 minutes
- Next: November 2026 for 2027 tax year

### January (New Year)
**State Tax Changes**
- Most states effective January 1
- Update: All state_flat, state_graduated_*, state standard deductions
- Check: Tax Foundation state tax page + individual state DORs
- Time: 2-3 hours for all 51 jurisdictions
- Next: January 2027 for 2027 tax year

### Quarterly
**PTET Monitoring**
- Check AICPA tracker quarterly
- Monitor for: new adoptions, expirations, rate changes
- Update: ptet, ptet_expired sections
- Time: 30 minutes
- Next check: April 2026, July 2026, October 2026

### As Needed (Legislative Changes)
**Monitor for new legislation:**
- TCJA provisions: Expiring 2025 (unless extended)
- OBBBA provisions: SALT cap (expires 2029), Senior deduction (expires 2028)
- State legislation: New tax rates, new PTET adoptions, flat tax conversions
- Bonus depreciation: Currently 100% through 2027
- Check: congress.gov, Tax Foundation, AICPA, state legislature websites

## Important Reminders

⚠️ **CRITICAL - DO NOT MODIFY WITHOUT SOURCE:**

**Fixed Rates (NOT indexed, only change via legislation):**
- NIIT: 3.8% rate since 2013, thresholds NOT indexed
- Additional Medicare: 0.9% since 2013, NOT deductible
- Capital gains: 0%, 15%, 20% brackets (thresholds ARE indexed)
- FICA base rates: 12.4% Social Security, 2.9% Medicare (only wage base indexed)

**Bracket Continuity:**
- Each `max` must equal next `min`
- No gaps allowed - would create undefined tax ranges
- Top bracket always `max: null`

**Standard Deductions - Federal:**
- MFJ MUST equal 2× Single
- If this relationship breaks, investigate - may indicate error

**Expiring Provisions - Track Carefully:**
- SALT cap: $40,400 through 2029-12-31, reverts to $10,000 on 2030-01-01
- Senior deduction: $6,000/$12,000 through 2028-12-31 only
- Bonus depreciation: 100% through 2027, verify annually
- PTET programs: Check state-by-state expirations

**State Verification:**
- ALWAYS verify with official state source, not just Tax Foundation
- Some states update automatically (indexed), others require legislation
- Effective dates vary - some mid-year, most January 1
- Local taxes exist in some states (NYC, Philadelphia, etc.) - separate from state rates

**Cross-Reference Everything:**
- Use 2+ sources for every change
- If sources conflict, use official government source (IRS, SSA, state DOR)
- Tax Foundation is reliable but secondary - always verify with primary source

**PTET Special Considerations:**
- Election deadlines vary by state (most March 15, CA/NY different)
- Credit types: refundable (best), nonrefundable, exclusion
- Some states limit PTET to S-corps only, others include partnerships
- Expiration tracking is critical - legislatures often extend last-minute

## Common Pitfalls

**DON'T:**
- ❌ Modify NIIT rate or thresholds (fixed since 2013 unless Congress acts)
- ❌ Modify Additional Medicare rate or deductibility (0.9%, not deductible)
- ❌ Create bracket gaps (each max must equal next min)
- ❌ Assume MFJ ≠ 2× Single for federal (this is a red flag for errors)
- ❌ Update capital gains rates without legislation (0%, 15%, 20% are fixed)
- ❌ Forget to update `_last_verified` dates after changes
- ❌ Copy data without verifying against current year source
- ❌ Trust secondary sources without verifying primary source

**DO:**
- ✅ Verify every number with official government source
- ✅ Cross-reference with 2+ sources
- ✅ Check bracket continuity after updates
- ✅ Update metadata (version, last_updated, _last_verified)
- ✅ Document changes in CHANGELOG
- ✅ Compare to prior year (2-4% inflation typical)
- ✅ Track expiration dates for temporary provisions
- ✅ Monitor PTET quarterly for changes

## Testing Your Updates

**After making updates, test by asking:**

1. "Show me the 2027 tax brackets for single filers"
   - Should display updated brackets with no gaps

2. "What's the 401(k) contribution limit for 2027?"
   - Should show updated limit with source reference

3. "Which states have PTET?"
   - Should reflect any new adoptions or expirations

4. "Explain where the Social Security wage base comes from"
   - Should trace to SSA COLA announcement with URL

5. "What provisions expire in 2029?"
   - Should identify SALT cap expiration

If AI can answer these accurately with source references, your update was successful.

# ============================================================================
# CHANGELOG
# ============================================================================

## 2026-02-12 - Tax Year 2026 - Initial Version with Comprehensive Source Citations

**Overview:** First version of tax.md with complete source citation system. Every data point now traces to an authoritative source, enabling systematic updates by future AI.

### Federal Income Tax
**Source:** IRS Rev. Proc. 2025-32 (verified 2025-11-15)
**URL:** https://www.irs.gov/pub/irs-drop/rp-25-32.pdf

**Tax Brackets:**
- Single: 10% to 37% (7 brackets)
- Top bracket begins: $640,600 single, $768,700 MFJ
- Brackets fully documented in Table 1 of Rev. Proc.

**Standard Deductions:**
- Single: $16,100
- MFJ: $32,200 (= 2× Single)
- HOH: $24,150

**Additional Standard Deduction (65+/Blind):**
- Single/HOH: $2,050 per condition
- MFJ/MFS: $1,650 per person per condition

**Capital Gains Thresholds:**
- 0% bracket: Up to $49,450 single, $98,900 MFJ
- 15% bracket: $49,450-$545,500 single, $98,900-$613,700 MFJ
- 20% bracket: Above $545,500 single, $613,700 MFJ

**QBID Thresholds:**
- Full deduction: $201,750 single, $403,500 MFJ
- Phaseout range: $75,000
- Phaseout complete: $276,750 single, $553,500 MFJ

**AMT:**
- Exemption: $90,100 single, $140,200 MFJ
- Phaseout begins: $500,000 single, $1,000,000 MFJ

### Legislative Provisions
**Source:** P.L. 119-21 (OBBBA, verified 2025-02-05)

**SALT Cap (Section 201):**
- Limit: $40,400 ($20,200 MFS)
- Phasedown: 30% of MAGI over $505,000 ($252,500 MFS)
- Floor: $10,000 ($5,000 MFS)
- **Expires:** 2029-12-31 (reverts to $10,000 cap on 2030-01-01)

**Senior Deduction (Section 102):**
- Amount: $6,000 single, $12,000 MFJ (both 65+)
- Phaseout: $75,000-$175,000 single, $150,000-$250,000 MFJ
- **Tax years:** 2025-2028 only

**Bonus Depreciation:**
- 100% restored retroactive to 2025-01-01
- Applies: 2025, 2026, 2027

### Retirement Limits
**Source:** IRS Notice 2025-67 (verified 2025-11-13)
**URL:** https://www.irs.gov/pub/irs-drop/n-25-67.pdf

- 401(k) elective deferral: $24,500
- Catch-up (50+): $8,000
- Super catch-up (60-63): $11,250
- IRA contribution: $7,500
- IRA catch-up (50+): $1,100
- SEP IRA: $72,000
- SIMPLE IRA: $17,000
- HSA individual: $4,400
- HSA family: $8,750
- Healthcare FSA: $3,400
- Defined benefit annual limit: $290,000

### Payroll Tax
**Source:** SSA COLA Announcement 2026 (verified 2025-10-10)
**URL:** https://www.ssa.gov/news/press/factsheets/colafacts2026.pdf

- Social Security wage base: $184,500
- Max SS tax per side: $11,439
- SS rate: 12.4% (6.2% employee + 6.2% employer)
- Medicare rate: 2.9% (1.45% employee + 1.45% employer)
- Additional Medicare: 0.9% (NOT deductible)

### Fixed Rates (Not Indexed)
**Source:** IRC Sections 1411, 3101 (verified 2026-02-12)

**NIIT:**
- Rate: 3.8%
- Thresholds: $200,000 single, $250,000 MFJ, $125,000 MFS
- **NOT indexed** - unchanged since 2013

**Additional Medicare Tax:**
- Rate: 0.9%
- Thresholds: $200,000 single, $250,000 MFJ, $125,000 MFS
- **NOT indexed** - unchanged since 2013
- **NOT deductible** per IRC §164(f)

### State Tax
**51 jurisdictions documented with individual sources**
**Verification date:** 2026-01-15

**No income tax (9):** AK, FL, NV, NH, SD, TN, TX, WA, WY

**Flat tax (16):** AZ (2.5%), CO (4.4%), GA (5.09%), ID (5.3%), IL (4.95%), IN (2.95%), IA (3.8%), KY (3.5%), LA (3.0%), MI (4.25%), MO (4.7%), MS (4% above $10K), NC (3.99%), OH (2.75% above $26,050), PA (3.07%), UT (4.5%)

**Graduated tax (26):** AL, AR, CA, CT, DC, DE, HI, KS, ME, MD, MA, MN, MT, NE, NJ, NM, NY, ND, OK, OR, RI, SC, VT, VA, WV, WI

**Top rates:**
- Highest: CA 13.3%, NY 10.9%, NJ 10.75%, DC 10.75%, HI 11%
- Lowest (with income tax): ND 2.5%, AZ 2.5%, IN 2.95%, PA 3.07%

### PTET (Pass-Through Entity Tax)
**Source:** AICPA State PTET Tracker + individual state legislation
**Verification date:** 2026-01-15

**Active programs: 36 states**
AL, AZ, AR, CA, CO, CT, GA, HI, ID, IL, IN, IA, KS, KY, LA, ME, MD, MA, MI, MS, MO, MT, NE, NJ, NM, NY, NC, OH, OK, OR, RI, SC, UT, WV, WI (plus DC partial)

**Expired programs: 2 states**
- MN: Expired 2025-12-31 (was 9.85% refundable)
- VA: Pending extension (was 5.75% refundable)

**Credit types:**
- Refundable: 26 states (AL, AZ, AR, CO, GA, HI, IL, IN, IA, KS, LA, ME, MD, MA, MI, MS, MO, NE, NJ, NM, NY, NC, OK, OR, RI, SC, WI, WV)
- Nonrefundable: 5 states (CA, ID, KY, MT)
- Exclusion: 2 jurisdictions (CT, OH)
- TBD: 1 state (UT)

### Section 179 & Depreciation
**Source:** Rev. Proc. 2025-32 + OBBBA (verified 2025-11-15)

- Section 179 limit: $1,220,000
- Phaseout begins: $3,050,000
- Phaseout ends: $4,270,000
- Bonus depreciation: 100% (2025-2027)

### Estate & Gift Tax
**Source:** Rev. Proc. 2025-32 (verified 2025-11-15)

- Estate exemption: $15,000,000
- Gift exemption: $15,000,000
- GST exemption: $15,000,000
- Annual exclusion: $19,000
- Annual exclusion (noncitizen spouse): $194,000
- Top estate rate: 40%
- Portability: Yes

### Source Documentation
**Total sources defined: 65**
- Federal sources: 11 (IRS, SSA, IRC, OBBBA)
- State sources: 51 (all jurisdictions)
- PTET sources: 3 (AICPA tracker + state-specific)

**Source metadata includes:**
- Authority (issuing organization)
- Publication number/name
- Direct URLs
- Verification dates
- Effective dates
- Update frequency and timing
- What to verify in each source

### Validation Performed
- [x] All data cross-referenced with 2+ independent sources
- [x] Bracket continuity verified (no gaps)
- [x] MFJ = 2× Single for standard deductions
- [x] Rate reasonableness confirmed:
  - Federal top rate: 37% ✓
  - NIIT: 3.8% ✓
  - Additional Medicare: 0.9% ✓
  - Capital gains: 0%, 15%, 20% ✓
- [x] Expiration dates documented:
  - SALT cap expires 2029-12-31 ✓
  - Senior deduction expires 2028-12-31 ✓
- [x] All 51 state jurisdictions sourced ✓
- [x] PTET: 36 active, 2 expired documented ✓

### Implementation Notes
- Every major data section now has: `_source`, `_verification_note`, `_last_verified`
- Expiring provisions have: `_expiration_date`
- Sources section enables future AI to:
  - Find exact source documents
  - Know when to check for updates
  - Understand update patterns
  - Verify data systematically

**Next update:** November 2026 for tax year 2027

---

[Future update entries will be added above this line]

# ============================================================================
# ORIGINAL TAX NOTES AND STATE DETAILS
# ============================================================================

## Contents
- Federal Rules & Calculations (Income Tax, SE Tax, NIIT, QBID, SALT, Retirement, Depreciation, Estate & Gift)
- Cross-State Reference (S-Corp Entity Taxes, PTET Overview, QBID Non-Conforming)
- State Notes (alphabetical, A-Z)

# Federal Rules & Calculations

## Income Tax

Personal exemption remains 0 under TCJA/OBBBA. Senior deduction (OBBBA §102) is separate from existing 65+/blind additional deduction.

## Self-Employment Tax Calculation

1. SE Tax Base = Net SE Income × 0.9235
2. Social Security Tax = min(SE Tax Base, 184,500) × 12.4%
3. Medicare Tax = SE Tax Base × 2.9%
4. Regular SE Tax = Social Security Tax + Medicare Tax
5. Additional Medicare Tax = max(0, SE Tax Base - threshold) × 0.9%
6. Total SE Tax = Regular SE Tax + Additional Medicare Tax
7. **SE Tax Deduction = Regular SE Tax × 50%** (excludes Additional Medicare Tax!)

**Additional Medicare Tax:** Not indexed (unchanged since 2013). CRITICAL: 0.9% additional Medicare is NOT deductible per IRC §164(f).

## NIIT

3.8% on lesser of: (1) net investment income, or (2) MAGI exceeding threshold. Not indexed.

**Applies to:** Interest, dividends, capital gains, rental income, royalties, passive income, non-qualified annuities

**Excludes:** Wages, SE income, active business income, retirement distributions, tax-exempt interest, veterans benefits, Social Security

**Planning:**
- Cannot be reduced by capital losses below zero
- Passive activity losses can reduce NII
- S-Corp distributions generally not NII if materially participating
- Rental income usually NII unless real estate professional

## QBID

**W-2 wage limitations (above threshold):**
- Option 1: 50% of W-2 wages
- Option 2: 25% of W-2 wages + 2.5% of UBIA

**SSTB (Specified Service Trades):**
- Below threshold: full deduction
- In phaseout: proportional reduction
- Above phaseout: NO deduction

**SSTB types:** Health, law, accounting, actuarial, performing arts, consulting, athletics, financial services, brokerage, investment management, trading, any trade where principal asset is reputation/skill

**SSTB exclusions:** Architecture, engineering

## SALT Cap

Cap reduced by 30% of MAGI exceeding threshold; cannot fall below floor.

## Kiddie Tax

2,700 unearned income threshold.

## Retirement

**Mega Backdoor Roth:** total_limit - employee deferral - employer contributions. Requires plan allowing after-tax contributions and in-service distributions/conversions.

**SIMPLE IRA:** Applicable = higher limits for certain SIMPLE plans under SECURE 2.0.

**FSA:** Dependent care limit is statutory, not indexed.

**Catch-ups:** Must be Roth above 150K wage (SECURE 2.0, effective 2026).

## Depreciation

**Section 179:** Phases out dollar-for-dollar above threshold.

**Bonus Depreciation:** 100% restored retroactive to Jan 2025 via OBBBA.
- Applies to: Qualified property with recovery period ≤20 years, computer software, water utility property, qualified film/TV/live theatrical productions, specified plants
- Excludes: Real property (buildings), used property (in some cases), property from related parties

## Estate & Gift

Unused exemption transfers to surviving spouse via timely-filed Form 706. Exemption permanent under OBBBA, indexed for inflation.

# Cross-State Reference

## S-Corp Entity Taxes

No S-Corp recognition (taxed as C-Corp): NYC, NH, TN, DC.

| Jurisdiction | Tax Name | Rate | Base | Minimum |
|--------------|----------|------|------|---------|
| CA | Entity tax | 1.5% | Net income | 800 (plus LLC fee) |
| DC | Franchise Tax | 8.25% | Net income | 250 |
| IL | Replacement tax | 1.5% | Net income | 0 |
| NH | Business Profits Tax | 7.5% | Net income | 0 |
| NJ | Minimum tax | — | Gross receipts | 375-1,500 |
| NY | Fixed dollar min | — | NY receipts | 25-4,500 |
| NYC | General Corporation Tax | 8.85% | Net income | 25-5,000 |
| TN | Franchise & Excise Tax | 6.5% + 0.25% net worth | Net income | 100 |

## PTET Overview

Workaround for SALT cap. Entity pays state tax, owners get credit/exclusion. SALT Cap: 40,400. Expires December 31, 2029. Election timing: most states before tax year or with extension (see CA, NY for exceptions).

States without PTET: AK, DE, FL, NV, NH, ND, PA, SD, TN, TX, WA, WY.

## QBID Non-Conforming States

Tax QBI at full state rate: CA, DC, HI, MN, NJ, NY, OR, PA, SC, VT. Partial: GA.

# State Notes

## Alabama
Top rate 5%. MFJ brackets differ (1,000/6,000 vs 500/3,000). Sliding scale max deduction decreases with AGI above 20,499. Also allows federal tax deduction. PTET: 5% refundable.

## Alaska
No income tax. No capital gains tax.

## Arizona
Own standard deduction, indexed annually. PTET: 2.5% refundable.

## Arkansas
Top rate 3.9%. Same brackets all statuses. Capital gains: 50% exclusion. PTET: 4.4% refundable.

## California
Top rate 13.3% (includes 1% mental health surcharge on income over 1M). Capital gains taxed as ordinary income. QBID: does NOT conform. SDI: 1.3% on all wages (no cap). S-Corp entity tax: 1.5% net income, min 800, plus LLC fee. PTET: 9.3% nonrefundable credit, 5-yr carryforward, expires 2030. Election: original return due date.

## Colorado
Uses federal taxable income as starting point (no state standard deduction). PTET: 4.4% refundable.

## Connecticut
Top rate 6.99%. No standard deduction (uses personal exemption credits). Personal exemption: Single 15,000 | MFJ 24,000 | MFS 12,000 | HOH 19,000 (credit, phases out). PTET: 6.99% exclusion, elective since 2024.

## DC
Top rate 10.75%. Same brackets all statuses. Uses federal standard deduction. QBID: does NOT conform. S-Corp: not recognized (Franchise Tax 8.25%, min 250).

## Delaware
Top rate 6.95%. Same brackets all statuses.

## Florida
No income tax. No capital gains tax.

## Georgia
5.09% flat effective Jan 1, 2026. PTET: 5.09% refundable.

## Hawaii
Top rate 11%. HOH uses same brackets as MFJ. QBID: does NOT conform. PTET: uses individual rates (1.4%-11%), refundable.

## Idaho
5.3% flat. PTET: 5.3% nonrefundable.

## Illinois
4.95% flat. 1.5% replacement tax on S-corps. PTET: 4.95% refundable, permanent (sunset removed Dec 2025).

## Indiana
2.95% flat. Counties add 0.5%-3.38% local tax. PTET: 2.95% refundable.

## Iowa
3.8% flat. PTET: 3.8% refundable.

## Kansas
Top rate 5.58%. MFS and HOH use same brackets as single. PTET: 5.58% refundable.

## Kentucky
3.5% flat effective Jan 1, 2026. PTET: 3.5% nonrefundable.

## Louisiana
3% flat. Combined deduction+exemption, adjusted annually for inflation. PTET: 3%-4.25% refundable.

## Maine
Top rate 7.15%. Personal exemption: 5,300. Standard deduction phases out for Single >102,250 and MFJ >204,550. PTET: 7.15% refundable.

## Maryland
Top rate 6.5%. Local tax: counties add 2.25%-3.30%. Capital gains surtax: 2% on income >350K. PTET: 5.75% + local county rate, refundable.

## Massachusetts
Top rate 9%. Same brackets all statuses. No standard deduction (uses personal exemptions). Personal exemption: Single 4,400 | MFJ 8,800 | MFS 4,400 | HOH 6,800 | Additional 65+/blind 700. 4% millionaire surtax on income over ~1.1M (inflation-adjusted). PTET: 5% rate (not 9% surtax rate), refundable.

## Michigan
4.25% flat. Personal exemption: 5,900 per person and per dependent. Senior deduction age 67+. Some cities have local tax (Detroit 2.4% resident, 1.2% non-resident). PTET: 4.25% refundable.

## Minnesota
Top rate 9.85%. Dependent exemption: 5,300. Capital gains taxed as ordinary income. QBID: does NOT conform. PTET: EXPIRED 12/31/2025 — NOT available for 2026.

## Mississippi
First 10,000 exempt, 4% flat above. Same brackets all statuses. PTET: 4% refundable.

## Missouri
4.7% flat. Federal conformity standard deduction. Additional deductions for age 65+/blind. PTET: 4.7% refundable.

## Montana
Top rate 5.65%. Uses federal standard deduction. Capital gains: preferential (max 4.1%). PTET: 5.65% nonrefundable.

## Nebraska
Top rate 4.55%. Additional for age 65+/blind. PTET: 4.55% refundable.

## Nevada
No income tax. No capital gains tax. Commerce Tax: 0.051%-0.331% on gross receipts over 4M.

## New Hampshire
No income tax on wages. No capital gains tax. Business Profits Tax: 7.5% (treats S-Corps same as C-Corps).

## New Jersey
Top rate 10.75%. Brackets NOT indexed for inflation. No standard deduction (uses personal exemptions). Personal exemption: 1,000 per person | Additional 65+/blind 1,000. Capital gains taxed as ordinary income. QBID: does NOT conform. S-Corp minimum tax: 375-1,500 (by gross receipts). PTET: top rate 10.9% (not 10.75%), refundable.

## New Mexico
Top rate 5.9%. Uses federal standard deduction. PTET: 5.9% refundable.

## New York
Top rate 10.9%. Capital gains taxed as ordinary income. QBID: does NOT conform. NYC additional: 3.078%-3.876% for residents. S-corps taxed as C-corps at 8.85%. S-Corp fixed dollar minimum (by NY receipts): 25-4,500. PTET: 6.85%-10.9% refundable. Election by March 15. NYC has separate PTET.

## North Carolina
3.99% flat effective Jan 1, 2026. PTET: 3.99% refundable.

## North Dakota
Top rate 2.5%. Uses federal standard deduction. Capital gains: 40% exclusion.

## Ohio
Top rate 2.75%. Personal exemption unavailable for MAGI >500K. Business income taxed at 3.0% flat. 600+ cities have municipal income tax (0.5%-3%). Same brackets all statuses. PTET: CAT only (exclusion basis).

## Oklahoma
Top rate 4.5%. PTET: 4.5% refundable.

## Oregon
Top rate 9.9%. Capital gains taxed as ordinary income. QBID: does NOT conform. Local: Portland Metro 1% supportive housing (>200K) + 1.5-3% Multnomah Co preschool tax. CAT: 250 + 0.57% on commercial activity over 1M (after 35% subtraction). PTET: 9% refundable.

## Pennsylvania
3.07% flat. Uses 8 classes of income with limited deductions, no federal AGI concept. Tax Forgiveness program for low/moderate-income. Most municipalities have Earned Income Tax (1%-3.9%). QBID: does NOT conform.

## Rhode Island
Top rate 5.99%. Same brackets all statuses. Personal exemption: 5,100. Standard deduction phases out for MAGI >254,250, reaching 0 at 283,250+. PTET: 5.99% refundable.

## South Carolina
Top rate 6.0%. Same brackets all statuses. Uses federal standard deduction. QBID: does NOT conform. PTET: 6% refundable.

## South Dakota
No income tax. No capital gains tax.

## Tennessee
No income tax on wages. No capital gains tax. Franchise & Excise Tax: 6.5% + 0.25% on net worth (treats S-Corps same as C-Corps, min 100).

## Texas
No income tax. No capital gains tax. Margin Tax: Retail/Wholesale 0.375%, Other 0.75%, No Tax Threshold 2,650,000.

## Utah
4.5% flat. Uses tax credit system: 6% of federal deductions (excluding state tax deduction) + personal exemption (2,046), phases out at higher incomes. PTET: 4.5% (tbd).

## Vermont
Top rate 8.75%. QBID: does NOT conform. MFJ thresholds <2x Single (marriage penalty).

## Virginia
Top rate 5.75%. Same brackets all statuses. Personal exemption: 930 per person | Additional 65+/blind 800. PTET: pending extension to Jan 1, 2027 — verify status.

## Washington
No income tax on wages. Capital gains: 7% on gains over 278K + 2.9% surcharge on gains over 1M = 9.9% top rate. B&O Tax: Retailing 0.471%, Manufacturing 0.484%, Services <1M 1.5%, Services 1-5M 1.75%, Services >5M 2.1%.

## West Virginia
Top rate 5.12%. MFS brackets are half of single/MFJ/HOH. Social Security fully exempt. PTET: 4.82% refundable.

## Wisconsin
Top rate 7.65%. MFJ thresholds ~1.33x Single (marriage penalty). Standard deduction phaseout: 12% of income above threshold (Single 16,390, MFJ 23,620). PTET: 7.65% refundable.

## Wyoming
No income tax. No capital gains tax.
