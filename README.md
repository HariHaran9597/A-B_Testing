# A/B Testing & Decision Science — Pricing Experiment

A complete statistical analysis of a pricing strategy A/B test for a B2C SaaS company, demonstrating experiment design, rigorous hypothesis testing, and data-driven decision making. **Result: +1.76 pp conversion lift (p = 0.002), +22.3% revenue uplift.**

## Problem Statement
A SaaS company is evaluating whether introducing a discounted annual subscription plan can increase paid conversions without negatively impacting revenue quality.

**Goal:** Make a clear ship/no-ship decision using controlled experimentation, statistical rigor, and business reasoning.

---

## Key Results at a Glance

| Metric | Control | Treatment | Lift | p-value |
|--------|---------|-----------|------|---------|
| Conversion Rate | 9.58% | 11.34% | +1.76 pp | 0.002 |
| Revenue per Visitor | $3.28 | $4.01 | +$0.73 (+22.3%) | <0.001 |
| Sample Size | 3,991 | 3,988 | — | — |

**Decision:** ✅ **SHIP with staged rollout**

---

## Business Context
- Product type: B2C SaaS
- Current pricing: Monthly subscription only
- Proposed change: Discounted annual subscription option

This decision has high business impact because pricing changes affect both
customer acquisition and long-term revenue.

---

## Experiment Design

### Groups
- **Control:** Existing monthly pricing
- **Treatment:** Monthly pricing + discounted annual plan

### Primary Metric
- **Conversion rate (trial → paid)**
  - Why: Pricing changes directly influence purchase likelihood
  - Statistical test: Two-proportion z-test
  - Powered to detect ≥2% absolute lift with 90% power

### Secondary Metrics (Guardrails)
- **Average revenue per user (ARPU)**
  - Why: Ensures higher conversions don't sacrifice revenue quality
  - Statistical test: Mann–Whitney U test (non-parametric, robust to skew)
- **Refund rate**
  - Why: Guards against poor quality conversions or customer dissatisfaction

### Methodology Notes
- **Sample size:** 7,979 users (3,991 control, 3,988 treatment)
- **Duration:** 2 weeks
- **Randomization:** Balanced assignment at user level
- **Significance level (α):** 0.05

---

## Hypotheses

**Null Hypothesis (H₀):**  
The introduction of a discounted annual plan has no effect on conversion rate.

**Alternative Hypothesis (H₁):**  
The introduction of a discounted annual plan increases conversion rate.

---

## Analysis Plan
1. Validate experiment setup and group balance
2. Evaluate conversion impact using proportion tests
3. Evaluate revenue impact using appropriate statistical tests
4. Compute confidence intervals for observed effects
5. Assess statistical power
6. Make a business recommendation based on results and uncertainty

---

## What You'll Learn

This project demonstrates:
- **Statistical rigor:** Two-proportion z-tests, Mann–Whitney U tests, bootstrap CI estimation
- **Experimental design:** Power analysis, randomization validation, guardrail metrics
- **Business sense:** Translating statistics into decisions with risk assessment and implementation planning
- **Data visualization:** Professional figures for stakeholder communication

---

## Quick Start

1. **View the results:**
   - Start with [insights.md](insights.md) for the executive summary
   - See [README.md](README.md) for methodology and findings

2. **Explore the analysis:**
   - [01_experiment_design.ipynb](notebooks/01_experiment_design.ipynb) — Data setup and validation
   - [02_statistical_testing.ipynb](notebooks/02_statistical_testing.ipynb) — Hypothesis testing & visualizations
   - [03_decision_analysis.ipynb](notebooks/03_decision_analysis.ipynb) — Business decision & monitoring plan

3. **Reproduce the analysis:**
   ```bash
   pip install pandas numpy scipy statsmodels matplotlib
   jupyter notebook notebooks/
   ```

---

## Technical Details

### Experiment Design
- **Sample size:** 7,979 users (balanced randomization)
- **Duration:** 2 weeks
- **Statistical power:** 89% for detecting 2% conversion lift
- **Significance level (α):** 0.05 (one-sided test)

### Methods
- **Conversion test:** Two-proportion z-test (large samples, binary outcome)
- **Revenue test:** Mann–Whitney U test (non-parametric, handles skewed distributions)
- **Confidence intervals:** Bootstrap and normal approximation methods
- **Power analysis:** statsmodels NormalIndPower analysis

---

## Experiment Design (Detailed)

### Groups
- **Control:** Existing monthly pricing
- **Treatment:** Monthly pricing + discounted annual plan

### Primary Metric
- **Conversion rate (trial → paid)**
  - Why: Pricing changes directly influence purchase likelihood
  - Statistical test: Two-proportion z-test
  - Powered to detect ≥2% absolute lift with 90% power

### Secondary Metrics (Guardrails)
- **Average revenue per user (ARPU)**
  - Why: Ensures higher conversions don't sacrifice revenue quality
  - Statistical test: Mann–Whitney U test (non-parametric, robust to skew)
- **Refund rate**
  - Why: Guards against poor quality conversions or customer dissatisfaction

### Methodology Notes
- **Sample size:** 7,979 users (3,991 control, 3,988 treatment)
- **Duration:** 2 weeks
- **Randomization:** Balanced assignment at user level
- **Significance level (α):** 0.05

---

## Hypotheses

**Null Hypothesis (H₀):**  
The introduction of a discounted annual plan has no effect on conversion rate.

**Alternative Hypothesis (H₁):**  
The introduction of a discounted annual plan increases conversion rate.

---

## Findings Summary

### Conversion Impact
- Absolute lift: **+1.76 percentage points** (9.58% → 11.34%)
- Relative lift: **+18.4%**
- 95% CI: [0.56%, 2.96%] ✅ *excludes zero*
- Test statistic: z = 3.08, p = 0.002

### Revenue Impact
- Lift: **+$0.73 per visitor (+22.3%)**
- Driven by increased annual plan adoption
- Mann–Whitney U test: p < 0.001 ✅ *highly significant*

### Statistical Robustness
- ✅ Large sample size (n=7,979)
- ✅ High statistical power (89%)
- ✅ Balanced randomization (<0.1% imbalance)
- ✅ Confidence intervals exclude zero
- ✅ Multiple metrics show consistent lift

---

## Recommendation & Implementation

### Decision
**✓ SHIP the discounted annual plan** with monitored staged rollout

### Rationale
1. Conversion lift is **statistically significant** (p = 0.002) and **economically material** (+1.76 pp)
2. Revenue per visitor increased **substantially** (+22.3%)
3. **High statistical power** (89%) reduces false positive risk
4. Results are **robust** across multiple metrics and methods

### Risk Assessment
- Revenue gains depend on **sustained annual plan uptake** (renewal rates not yet measured)
- Support costs may increase with higher conversion
- Customer perception of pricing change unknown

### Implementation Plan
1. **Staged rollout:** 25% of users initially
2. **Monitor:** Daily conversion rate, annual plan renewals, refund rate, support volume
3. **Follow-up:** A/B test discount levels after 3 months
4. **Full rollout:** Only after validating 30/60/90-day renewal rates

---

## Technologies Used

- **Python 3.11** — Data analysis and visualization
- **Pandas, NumPy** — Data manipulation
- **SciPy, Statsmodels** — Statistical testing and power analysis
- **Matplotlib** — Publication-quality visualizations
- **Jupyter** — Interactive analysis notebooks

---

## Files Generated

- `results_conversion_analysis.png` — Conversion rate comparison with CI
- `results_statistical_summary.png` — Three-panel statistical overview
