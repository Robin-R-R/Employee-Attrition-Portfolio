# Drivers of Past Attrition Experience

A diagnostic analysis of 1,191 real employee survey responses (Saudi private sector): which factors are associated with past attrition, and whether those associations hold across industries and occupational groups.


## Why This Project
- **Real survey data** — not the synthetic IBM dataset; includes 17 attitudinal scale variables (pay satisfaction, promotion fairness, commitment, exhaustion, etc.)
- **Diagnostic, not predictive** — cross-sectional, retrospective design; reports adjusted associations, no causal or forecasting claims
- **Group heterogeneity** — tests whether drivers differ by industry and ISCO major occupational group (managers, professionals, technicians, clerical support, services & sales)
- **Cross-validated evidence** — every finding triangulated across four methods (correlation, adjusted logistic OR, RF permutation importance, CART), with honest 5-fold CV performance


## Key Findings
- **Sector has the largest gap**: past-attrition rates range from 27% (Education) to 75% (Communications & IT)
- **Demographics show little association**: gender, age, marital status and education offer no consistent pattern that could serve as an intervention lever
- **Drivers differ by occupation**: external opportunity is the top correlate in 4 of 5 major groups (strongest among managers, r = 0.47); services & sales responds mainly to opportunity and physical stress; clerical support is the exception — promotion fairness is its strongest correlate (r = −0.36)
- **Two moderation effects pass formal interaction tests** (exploratory, pending validation): in medical professionals, high psychological exhaustion reverses the protective association of job stability; among clerical staff, low recognition flips the direction of pay satisfaction vs. attrition

→ [Full findings report with all figures and tables](FINDINGS.md)


## Recommendations
- **Clerical staff (especially in Communications & IT)**: review whether promotions were accompanied by pay adjustments *(exploratory insight from a small-sample analysis, pending validation)*
- **Managers**: when external opportunities are abundant, tenure perks stop working; benchmark total compensation against market instead
- **Medical professionals**: address workload and exhaustion before rolling out retention incentives
- **Services & sales**: pay and promotion interventions have limited effect; focus on workload and physical stress


## Methodology
- **Cleaning & coding**: text standardization, ISCO occupational classification, logic checks
- **Inference**: Spearman correlations with FDR correction; VIF collinearity check; adjusted logistic regression (OR + 95% CI + FDR); formal logit interaction tests within subgroups
- **Modeling & validation**: CART rule tree; 5-fold stratified CV (logistic vs. random forest); cross-validated permutation importance; four-source triangulation matrix (Tier 1–4)


## Project Structure
```
Employee-Attrition-Portfolio/
├── README.md                              ← Project overview (this file)
├── FINDINGS.md                            ← Full findings report: figures, numbers, recommendations
├── data_dictionary.csv                    ← Variable dictionary
├── data/
│   ├── cleaned_employee_attrition.csv     ← analysis-ready dataset (N=1,191)
│   ├── data_audit.csv                     ← quality audit
│   ├── value_report.csv                   ← value distributions
│   ├── mapping.csv                        ← encoding rules
│   └── mapping_job_title.csv              ← ISCO mapping + confidence
├── notebooks/
│   ├── 01Clean_data.ipynb                ← Data cleaning & coding
│   ├── 02Eda.ipynb                       ← Descriptive statistics & group differences
│   └── 03Modeling.ipynb                  ← Regression, CART, interaction tests, model evaluation
└── assets/
    └── *.png                              ← figures embedded in FINDINGS.md
```

## Tech Stack
Python · pandas · statsmodels · scikit-learn · matplotlib · seaborn


## Data Source & Ethics
- **Source**: *Saudi Employee Attrition Dataset* (Mendeley, DOI `10.17632/6z2hty8php.1`) — https://data.mendeley.com/datasets/6z2hty8php/1; cite Alqahtani et al., *Data in Brief* 2025, 63, 112242.
- **License**: CC BY 4.0 — reuse with attribution; this repo's cleaned and recoded CSV is shared under the same terms.
- **Collection**: anonymous online survey, Jun–Nov 2023, Saudi private sector, N = 1,191; per data authors, no ethics approval was required and responses are non-identifiable.


## About me
With hands-on experience in training operations, recruitment execution, and HRBP, I'm passionate about people data and aspire to become a people analytics expert—committed to creating healthier, more sustainable work environments for employees.

