# 📈 Retirement Corpus Survival Simulator

A comprehensive Monte Carlo retirement planning tool that simulates 1,000+ scenarios using historical US market data (1926–2024), real tax law, healthcare costs, and dual-spouse planning.

![Monte Carlo](https://img.shields.io/badge/Monte%20Carlo-1000%20simulations-brightgreen)
![Tax Aware](https://img.shields.io/badge/Tax-2024%20Federal%20Law-purple)
![Healthcare](https://img.shields.io/badge/Healthcare-HealthView%202024-orange)
![License](https://img.shields.io/badge/License-MIT-blue)

---

## 🎯 Features

### 💰 **Portfolio & Income Modeling**
- Current corpus with flexible withdrawal strategies
- Social Security with COLA adjustments (2.5%/yr)
- Pension/annuity income
- Part-time/rental income with configurable end age
- Multiple withdrawal strategies:
  - Fixed (inflation-adjusted)
  - Guardrail method (dynamic spending cuts/increases)
  - Constant 4% of portfolio
  - RMD-based withdrawals (IRS Uniform Lifetime Table)

### 🟠 **Healthcare & Medicine Costs**
Based on **HealthView 2024** and **Fidelity Retiree Health Cost Estimates**:
- **Medicare coverage** (Part B, Medigap/Medicare Advantage, Part D)
- **Pre-65 coverage** (ACA/COBRA premiums)
- **Out-of-pocket costs**: copays, labs, vision, dental
- **Prescription drugs** with age-based escalation
- **Fitness & wellness** expenses
- **Long-term care (LTC)** insurance and out-of-pocket costs
- **Medical inflation** defaults to 5.5%/yr (vs 3% general inflation)
- Age-based cost increases (25% at 75, 50% at 80)

**Default healthcare cost for health-conscious couple:**
- Age 62–64: ~$17,000/yr (ACA + OOP)
- Age 65–74: ~$22,000/yr (Medicare premiums + OOP + LTC insurance)
- Age 80+: ~$35,000/yr (Medicare + increased OOP + LTC costs)
- **Lifetime estimate**: ~$413,000–$662,000 per couple

### 🔵 **Complete Expense Tracking**
- **Housing**: property tax, home insurance, maintenance (1% rule)
- **Insurance**: life, auto, umbrella policies
- **Lifestyle**: travel, hobbies, entertainment
- **Family**: gifts to children/grandkids, charitable giving
- **Tax deductions**: 
  - Medical expense deduction (>7.5% AGI)
  - Qualified Charitable Distributions (QCD) from IRA
  - SALT and itemized deductions
  - Age-65+ standard deduction add-on ($1,550/person in 2024)

### 👥 **Dual-Spouse Planning**
- Independent ages and planning horizons
- Dual Social Security income streams
- **Survivor benefits**: configurable percentage of higher SS benefit
- **Spending reduction** after first death (default 75%)
- Portfolio horizon automatically extends to longer-lived spouse

### 💜 **Comprehensive Tax Modeling** (2024 Federal Law)
- **Filing status**: Single, Married Filing Jointly, Head of Household
- **Account types**:
  - Traditional IRA/401(k) (fully taxable)
  - Roth (tax-free)
  - Taxable brokerage (long-term capital gains rates)
  - Mixed (60% Traditional / 40% Roth)
- **Social Security taxation**: up to 85% taxable based on combined income
- **State income tax**: 0–13% configurable
- **Tax-aware gross-up**: automatically calculates how much to withdraw to cover both spending AND taxes
- **Age-65 deductions**: automatic additional standard deduction
- **QCDs**: reduce taxable RMDs dollar-for-dollar (age 70½+, max $105k)

### 📊 **Monte Carlo Simulation Engine**
- **1,000–5,000 simulations** per run
- Historical returns: US stocks (~10.5% nominal), bonds (~4.5% nominal)
- Random sampling from 98 years of market data (1926–2024)
- **Percentile visualization**: 10th, 25th, 50th, 75th, 90th paths
- **Success rate**: probability of portfolio surviving to target age
- **Failure analysis**: depletion age distribution and sequence-of-returns risk detection

---

## 🚀 Quick Start

### Installation

```bash
# Clone or download the project
git clone <your-repo-url>
cd retirement-simulator

# Install dependencies
pip install streamlit plotly numpy pandas

# Run the Streamlit app
streamlit run retirement_simulator_v3.py
```

The app will open in your browser at `http://localhost:8501`

### HTML Version (Standalone)

Open `retirement-simulator-v3.html` directly in any modern browser. No installation required.

---

## 📋 Usage Guide

### 1️⃣ Configure Your Portfolio
- Set your current corpus (investable assets)
- Enter base annual living expenses (excludes healthcare)
- Configure Social Security start age and annual benefit
- Add pension, annuity, or part-time income if applicable

### 2️⃣ Enable Healthcare Modeling (Optional)
Toggle **"Include Healthcare & Medicines"** and configure:
- Medicare premiums (defaults = 2024 standard rates)
- Pre-65 coverage (ACA/COBRA)
- Out-of-pocket medical costs
- Prescription drug costs
- Long-term care insurance and OOP costs
- Medical inflation rate (default 5.5%)

### 3️⃣ Add Other Expenses (Optional)
Toggle **"Include Other Expenses & Deductions"** to track:
- Property tax, home insurance, maintenance
- Life, auto, and umbrella insurance
- Travel and entertainment budgets
- Family gifts and charitable giving
- Tax deductions (medical, QCD, SALT)

### 4️⃣ Add Spouse (Optional)
Toggle **"Include Spouse / Partner"** to model:
- Dual Social Security benefits
- Survivor benefit percentage
- Household spending reduction after first death
- Extended planning horizon to longer-lived spouse

### 5️⃣ Enable Tax Modeling (Optional)
Toggle **"Include Tax Modeling"** to:
- Select filing status and account type
- Set state income tax rate
- Model SS taxation, LTCG rates, and deductions
- See gross withdrawal amounts after tax gross-up

### 6️⃣ Run Simulation
Click **"▶ Run Simulation"** and view:
- **Success rate** (% of simulations where portfolio survives)
- **Median end balance** and 10th percentile outcome
- **Net withdrawal rate** from portfolio
- **Lifetime healthcare cost estimate**
- **Average tax drag** on withdrawals

---

## 📊 Understanding the Results

### Key Metrics
- **Success Rate**: Percentage of 1,000 simulations where portfolio lasted to target age
  - ≥90% = Very safe
  - 80–89% = Acceptable
  - 70–79% = Borderline
  - <70% = High risk
- **Median End Balance**: Middle outcome across all simulations
- **Net Withdrawal Rate**: Your spending as % of corpus (4% rule benchmark)
- **10th Percentile End**: Worst 10% outcome (stress test)

### Tabs Explained

#### 📈 Projection
Fan chart showing 10th/25th/50th/75th/90th percentile portfolio paths over time. Shaded bands show range of outcomes.

#### 💰 Spending Budget
Itemized year-1 breakdown:
- Living expenses
- Healthcare costs (if enabled)
- Other expenses (if enabled)
- Income offsets (SS, pension, part-time)
- **Net portfolio draw** (what you actually withdraw)

Includes waterfall chart visualizing cash flows.

#### 📋 Scenarios
End balance outcomes at different percentiles:
- Best case (90th)
- Good case (75th)
- Median (50th)
- Stress case (25th)
- Worst case (10th)

Plus histogram of end balance distribution.

#### 💜 Tax Detail
Year-1 tax breakdown showing:
- Federal and state income tax
- Social Security taxable portion
- Total tax burden
- Gross withdrawal required (net spending + taxes)
- Effective tax rate

Includes pie chart of tax vs net spending.

#### 🟠 Healthcare
Projected healthcare costs at 5-year intervals, with:
- Premiums (Medicare or ACA)
- Out-of-pocket medical
- LTC costs
- Line chart showing cost growth over retirement

Compares your estimate to Fidelity benchmark ($413k/couple).

#### ⚠️ Depletion
For simulations where portfolio depleted:
- Failure rate (% of runs)
- Average and median depletion age
- Early failures (<50% of horizon) — indicates sequence risk
- Histogram of depletion ages

---

## 🧮 Methodology

### Return Sampling
- **98 years of data**: 1926–2024 US market annual returns
- **Stocks**: S&P 500 large-cap index (~10.5% nominal avg)
- **Bonds**: US aggregate bonds (~4.5% nominal avg)
- Each simulation year randomly samples one historical year
- Returns are **independent draws** (not sequential)

### Tax Calculations
- **2024 federal brackets**: Applied to taxable ordinary income
- **LTCG rates**: 0%, 15%, 20% based on income
- **SS taxation**: 0%, 50%, or 85% taxable based on combined income thresholds
- **State tax**: Flat rate applied to taxable income (minus 50% of federal deductions)
- **Gross-up iteration**: 2-pass calculation to ensure withdrawal covers both spending and taxes

### Healthcare Escalation
- **General inflation**: Applies to living expenses, housing, insurance, travel
- **Medical inflation**: Separate rate (default 5.5%) for all healthcare costs
- **Age-based increases**: OOP multiplied by 1.25 at age 75, 1.5 at age 80
- **LTC transition**: Insurance premium until configured age, then OOP costs phase in at 80

### Spouse Modeling
- **Dual income**: Both SS streams active until death
- **Survivor benefit**: Survivor receives higher SS × survivor benefit % (default 100%)
- **Spending reduction**: Household expenses drop to configured % after first death
- **Horizon**: Simulation runs until longer-lived spouse's target age

---

## 💡 Tips for Better Results

### Improve Your Success Rate
1. **Lower withdrawal rate**: Target 3.5–4% of initial corpus
2. **Increase stock allocation**: 60–70% stocks for long retirements (30+ years)
3. **Delay Social Security**: Every year from 62→70 increases benefit ~8%
4. **Use Guardrail strategy**: Cuts spending 10% when WR > 5.5%
5. **Hold cash buffer**: 2–3 years expenses in bonds/cash to avoid forced stock sales in downturns

### Reduce Tax Burden
1. **Roth conversions** in low-income years (before SS starts)
2. **QCDs from IRA** (age 70½+): Donate directly, not counted as income
3. **Tax-loss harvesting** in taxable accounts
4. **Relocate to no-income-tax state**: FL, TX, NV, WA, WY, SD, AK
5. **IRMAA planning**: Keep MAGI below Medicare surcharge thresholds ($103k single / $206k MFJ in 2024)

### Manage Healthcare Costs
1. **Medicare Part D**: Shop plans annually — premiums vary $0–$200/mo
2. **Medigap vs Medicare Advantage**: Medigap = higher premiums, lower OOP; MA = opposite
3. **HSA contributions**: Triple tax-advantaged if still working
4. **LTC insurance**: Buy at 50–60 for lower premiums; or self-insure if net worth > $2M
5. **Healthy lifestyle**: Exercise, diet, preventive care reduce long-term costs 25–40%

---

## 🔧 Customization

### Modify Default Healthcare Costs
Edit these lines in the code:
```python
part_b  = st.slider("Part B Premium ($/mo per person)", 100, 600, 174, 5)
medigap = st.slider("Medigap / Medicare Advantage ($/mo per person)", 0, 500, 185, 10)
oop_r   = st.slider("Routine OOP: copays, labs, vision, dental", 0, 15_000, 4_200, 200)
```

### Add Custom Withdrawal Strategy
In `run_simulation()` function, add to the strategy logic:
```python
elif p["strategy"] == "custom":
    # Your custom logic here
    gross_withdrawal = ...
```

### Change Number of Simulations
```python
n_sims = st.select_slider("Simulations", [500, 1000, 2000, 5000, 10000], 1000)
```

---

## 📚 Data Sources

- **Historical returns**: S&P 500 (1926–2024), US Aggregate Bonds (1926–2024)
- **Tax law**: IRS 2024 federal tax brackets, standard deductions, LTCG rates
- **Healthcare costs**: HealthView 2024 Retirement Healthcare Costs Data Report
- **LTC costs**: Genworth 2024 Cost of Care Survey
- **Medicare premiums**: CMS 2024 standard Part B premium ($174.70/mo)
- **Fidelity benchmark**: Fidelity Retiree Health Care Cost Estimate (2024)

---

## ⚠️ Disclaimers

### Not Financial Advice
This tool is for **educational purposes only**. It is not financial, tax, or legal advice. Consult with qualified professionals before making retirement decisions.

### Limitations
- **Past performance ≠ future results**: Historical returns do not guarantee future market behavior
- **Simplified tax model**: Does not account for AMT, NIIT, state-specific rules, or tax law changes
- **Healthcare estimates**: Based on averages; actual costs vary widely by health status, location, coverage choices
- **No guarantees**: Simulations are probabilistic — even 95% success rate means 5% chance of failure
- **Inflation assumptions**: Fixed inflation rates; actual inflation varies year-to-year
- **No longevity modeling**: Uses fixed target ages; does not model probability of reaching various ages

### Assumptions
- Returns are **independent** annual draws (not sequentially correlated)
- Social Security continues with 2.5% COLA
- Tax law remains similar to 2024 rules
- Medicare continues in current form
- No major life changes (divorce, large inheritances, disability, etc.)
- Investment fees are constant over time

---

## 🤝 Contributing

Contributions welcome! Please:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Ideas for Enhancement
- [ ] Longevity tables (SSA actuarial data)
- [ ] Variable inflation scenarios
- [ ] Required Minimum Distribution (RMD) enforcement
- [ ] Estate planning / legacy goals
- [ ] Part-time work income ramps
- [ ] One-time expenses (home purchase, college, weddings)
- [ ] Roth conversion optimizer
- [ ] IRMAA bracket calculator
- [ ] Export results to PDF/Excel
- [ ] Save/load configurations

---

## 📄 License

MIT License - see LICENSE file for details

---

## 🙏 Acknowledgments

- Historical market data: Ibbotson Associates / Morningstar
- Healthcare data: HealthView Services, Fidelity Investments, Genworth
- Tax calculations: IRS Publication 590-B, Publication 915
- Inspiration: Bogleheads community, /r/financialindependence

---

## 📞 Support

For bugs, feature requests, or questions:
- Open an issue on GitHub
- Email: [your-email@example.com]

---

**Built with:** Python, Streamlit, Plotly, NumPy, Pandas

**Version:** 3.0.0 (2024)

---

## 🎓 Further Reading

### Retirement Planning
- [The 4% Rule Revisited](https://www.kitces.com/blog/understanding-sequence-of-return-risk-safe-withdrawal-rates-bear-market-crashes-and-bad-decades/)
- [Guardrail Withdrawal Strategy](https://www.bogleheads.org/wiki/Variable_percentage_withdrawal)
- [Social Security Claiming Strategies](https://www.ssa.gov/benefits/retirement/planner/agereduction.html)

### Healthcare in Retirement
- [Fidelity Retiree Health Care Cost Estimate](https://www.fidelity.com/viewpoints/personal-finance/plan-for-rising-health-care-costs)
- [Medicare Coverage Explained](https://www.medicare.gov/what-medicare-covers)
- [Long-Term Care Planning](https://longtermcare.acl.gov/)

### Tax Planning
- [Roth Conversion Strategies](https://www.bogleheads.org/wiki/Roth_IRA_conversion)
- [Qualified Charitable Distributions](https://www.irs.gov/retirement-plans/charitable-donation-options-for-ira-owners-70-or-older)
- [Managing Tax Brackets in Retirement](https://www.kitces.com/blog/managing-tax-brackets-in-retirement-roth-conversions-aca-subsidies-irmaa/)

---

**Happy Planning! 🎯📊🚀**
