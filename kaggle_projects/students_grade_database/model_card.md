# Model Card: Student Academic Performance & Risk Prediction

## Model Overview
- **Model Architecture:** Random Forest Regressor & K-Means Clustering (K=4)
- **Primary Objective:** Predict student final grade percentages (`final_grade_pct`), identify dominant socioeconomic and behavioral performance drivers, and segment student cohorts to prioritize intervention.
- **Repository Location:** `kaggle_projects/students_grade_database/`
- **Notebook Reference:** `student_grade_prediction copy.ipynb`
- **Owner / Author:** Data Science MBA Portfolio

---

## Intended Use
- **Primary Use Case:** Exploratory data analysis, academic risk screening, and evidence-based education policy recommendations.
- **Out-of-Scope:** Automated high-stakes decisions (e.g., student expulsion or automatic grade penalties) without human counselor review.

---

## Factors & Feature Pipeline
- **Input Variables:** Socioeconomic status (income, parental education, occupation), behavioral metrics (attendance rate, study hours, tutoring), institutional factors (school type, distance to school).
- **Target Variable:** `final_grade_pct` (Continuous: 0–100%) and secondary classification `grade_class` / `at_risk_flag`.
- **Pre-filtering:** Statistical significance tests (ANOVA and two-sample Student's t-test with $\alpha = 0.05$) to exclude non-informative variables before model training.

---

## Performance & Metrics
- **Feature Importance Top Drivers:**
  1. `attendance_rate_pct` (High correlation with overall academic retention)
  2. `previous_year_grade_pct` (Baseline academic foundation)
  3. `study_hours_per_week`
  4. Socioeconomic support indices (Parental involvement, scholarship status)
- **Segmentation Strategy (K-Means, K=4):**
  - **Cluster 0 (High Risk / Vulnerable):** Low attendance, low SES score, elevated at-risk flag.
  - **Cluster 1 (Average Stable):** Standard attendance and performance across median income brackets.
  - **Cluster 2 (High Potential / Resource Constrained):** High study hours and engagement despite SES constraints.
  - **Cluster 3 (High Achievers):** Superior baseline grades, stable attendance, high parental involvement.

---

## Ethical Considerations & Governance
- **Fairness & Bias:** Socioeconomic attributes (income brackets, parental education) are strong statistical predictors but must be used for educational support rather than institutional discrimination.
- **Data Privacy:** Synthetic or anonymized student IDs (`student_id`) must ensure no personally identifiable information (PII) is exposed.

