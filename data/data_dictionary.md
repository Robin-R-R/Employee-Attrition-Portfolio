# Data Dictionary: Saudi Private Sector Attrition Dataset

This document describes all variables present in `cleaned_employee_attrition.csv`. 

## 1. Identifier & Target

| Column Name | Description | Data Type | Valid Values / Encoding |
| :--- | :--- | :--- | :--- |
| `id` | Unique respondent ID | Integer | - |
| `attrition_raw` | Raw text for attrition | String | "yes", "no" |
| `attrition` | **Target**: Past attrition experience | Binary | 1 = Yes, 0 = No |

---

## 2. Raw Text Columns (For Traceability)

*These columns retain the exact string inputs from the survey. The analysis-ready mapping is listed below.*

| Column Name | Original Question Topic | Valid Raw Text Values (Examples) | Mapped To |
| :--- | :--- | :--- | :--- |
| `gender_raw` | Gender | "male", "female" | `gender` (1/0) |
| `age_raw` | Age bracket | "21 to 30", "31 to 40", "41 to 50", "51 to 60" | `age` (1-4), `age_mid` |
| `marital_status_raw` | Marital status | "single", "married", "divorced" | `marital_married`, `marital_divorced` |
| `academic_degree_raw` | Highest degree | "ph.d", "master's", "bachelor's", "diploma or secondary" | `academic_degree` (4-1) |
| `years_experience_raw` | Total years of experience | "less than 5 years", "from 5 to 10 years", etc. | `years_experience` (1-7), `_mid` |
| `years_last_org_raw` | Tenure at last org | Same brackets as above. | `years_last_org` (1-7), `_mid` |
| `monthly_salary_raw` | Monthly salary bracket | "less than 5000 sar", "from 5000 to 10000 sar", etc. | `monthly_salary` (1-7), `_mid` |
| `sector_raw` | Industry sector | "medical sector", "education sector", etc. | `sector_group` |
| `department_raw` | Department | "accounting", "teaching", "sales", "hr", etc. | `department_group` |
| `job_title_raw` | Job title | "teacher", "accountant", "manager assistant", etc. | `major_group_isco` |
| `overtime_raw` | Has overtime | "yes", "no" | `overtime` (1/0) |
| `payment_overtime_raw`| Is overtime paid? | "yes", "no", "i don't have overtime" | `unpaid_overtime`, `ot_status` |
| `training_programs_raw`| Training count | "i did not receive any training", "from 1 to 3...", etc.| `training_programs` (0-3) |
| `business_travel_raw` | Travel frequency | "i do not travel for work", "travel rarely", "travel frequently" | `business_travel` (0-2) |
| `job_support_raw` | Org support level | "low", "medium", "high" | `job_support` (1-3) |
| `distance_to_work_raw` | Commute distance | "close", "medium", "far" | `distance_to_work` (1-3) |
| `work_life_balance_raw`| WLB ease | "difficult", "medium", "easy" | `work_life_balance` (1-3) |
| `physical_stress_raw` | Physical stress | "no", "sometimes", "yes" | `physical_stress` (0-2) |
| `psychological_exhaustion_raw`| Mental exhaustion | "no", "sometimes", "yes" | `psychological_exhaustion` (0-2) |
| *Other `_raw` columns* | (Satisfaction, Recognition, etc.) | "yes", "no", "low", "medium", "high" | See ordinal/binary mapping below. |

---

## 3. Clean Analysis Variables (Encoding & Mapping)

### 3.1 Binary Variables (1 = Yes, 0 = No)

| Column Name | Meaning |
| :--- | :--- |
| `gender` | 1 = Male, 0 = Female |
| `medical_insurance` | Has medical insurance |
| `bonus` | Received annual bonus |
| `overtime` | Works overtime |
| `rewards_wages_satisfaction` | Satisfied with pay vs. effort |
| `deserved_promotion` | Received deserved promotion |
| `useful_training` | Training was useful |
| `recognition` | Received moral appreciation |
| `job_stability` | Felt job security |
| `health_issues` | Had health issues forcing turnover |
| `job_opportunities` | Had external job opportunities |
| `unpaid_overtime` | Has OT AND not paid |
| `marital_married` | 1 = Married, 0 = Others |
| `marital_divorced` | 1 = Divorced, 0 = Others |
| `logic_exp_gt_age` | Flag: Experience > (Age - 16) |
| `logic_last_gt_total` | Flag: Last org tenure > Total experience |

### 3.2 Ordinal Variables (Ordered Categories)

| Column Name | Mapping Rule (High to Low) |
| :--- | :--- |
| `emotional_commitment` | 3 = High, 2 = Medium, 1 = Low |
| `job_support` | 3 = High, 2 = Medium, 1 = Low |
| `environment_satisfaction` | 3 = High, 2 = Medium, 1 = Low |
| `work_life_balance` | 3 = Easy, 2 = Medium, 1 = Difficult |
| `job_engagement` | 3 = Easy, 2 = Medium, 1 = Difficult |
| `job_satisfaction` | 3 = Very Satisfied, 2 = Satisfied, 1 = Not Satisfied |
| `physical_stress` | 2 = Yes, 1 = Sometimes, 0 = No |
| `psychological_exhaustion` | 2 = Yes, 1 = Sometimes, 0 = No |
| `business_travel` | 2 = Frequently, 1 = Rarely, 0 = Never |
| `training_programs` | 3 = 7+, 2 = 4 to 6, 1 = 1 to 3, 0 = None |
| `academic_degree` | 4 = Ph.D, 3 = Master, 2 = Bachelor, 1 = Diploma/Secondary |
| `distance_to_work` | 3 = Far, 2 = Medium, 1 = Close |
| `age` | 4 = 51-60, 3 = 41-50, 2 = 31-40, 1 = 21-30 |
| `years_experience` | 7 = 31-35 yrs, ..., 2 = 5-10 yrs, 1 = <5 yrs |
| `years_last_org` | 7 = 31-35 yrs, ..., 2 = 5-10 yrs, 1 = <5 yrs |
| `monthly_salary` | 7 = 31k+ SAR, ..., 2 = 5k-10k SAR, 1 = <5k SAR |

### 3.3 Continuous Variables (Midpoints)
*Calculated to preserve sample size for correlations.*

| Column Name | Calculated Midpoints |
| :--- | :--- |
| `age_mid` | 25.5, 35.5, 45.5, 55.5 |
| `years_experience_mid` | 2.5, 7.5, 13, 18, 23, 28, 33 |
| `years_last_org_mid` | 2.5, 7.5, 13, 18, 23, 28, 33 |
| `monthly_salary_mid` | 2500, 7500, 13000, 18000, 23000, 28000, 35000 |

---

## 4. Derived & Auxiliary Variables

| Column Name | Description | Notes |
| :--- | :--- | :--- |
| `allowances` | Count of allowance types received | Integer (0-4). Derived from Q12 (multi-select). Represents how many types (Housing, Transport, Living, Travel) were selected. 0 = No allowances. |
| `flag_overtime_payment_inconsistent` | Logic flag for OT | 1 = Has OT but payment status is unknown. |
| `ot_status_label` | Text label for OT status | "no_overtime", "paid_overtime", "unpaid_overtime", "unknown_payment". |
| `ot_2` | Dummy: Paid overtime | 1 = Yes, 0 = No (Base = no overtime) |
| `ot_3` | Dummy: Unpaid overtime | 1 = Yes, 0 = No (Base = no overtime) |
| `ot_4` | Dummy: Unknown payment | 1 = Yes, 0 = No (Base = no overtime) |
| `sector_group` | Industry sector | Rare categories (<25 samples) grouped into "other". |
| `department_group` | Department | Rare categories (<25 samples) grouped into "other". |
| `isco_2digit` | ISCO-08 2-digit code | Mapped from `job_title_raw`. |
| `isco_major` | ISCO-08 Major Group number | 1-digit extraction from `isco_2digit`. |
| `major_group_isco` | ISCO-08 Major Group name | "managers", "professionals", etc. |
| `training_status` | Combined training label | "No Training", "Trained but Not Useful", "Trained and Useful". |
| `training_status_ord` | Ordinal training status | 2 = Useful, 1 = Not Useful, 0 = No Training. |
