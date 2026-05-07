# BUAN381 Final Project — Agent Instructions

## What This Is

BUAN381 (Business Analytics) final project. Option A: Prediction-Based Analysis.

**Business Question:** What company characteristics and AI investment factors best predict revenue growth?

**Target variable:** `revenue_growth_percent`

---

## Deliverables (ALL required)

| # | Deliverable | Status |
|---|---|---|
| 1 | Python Notebook (`notebooks/analysis.ipynb`) | [ ] |
| 2 | Written report PDF/Word (10 pages max) | [ ] |
| 3 | Tableau Public link | [ ] |
| 4 | Data file (`dataset/ai_company_adoption.csv`) | [ ] |
| 5 | Peer evaluation (instructor provides form) | [ ] |

**Due:** This week (group project)

---

## Dataset

- File: `dataset/ai_company_adoption.csv`
- Rows: 150,000 | Cols: 43 | Nulls: 0
- Source: Kaggle — `mohankrishnathalla/global-ai-adoption-and-workforce-impact-dataset`
- **Use only `ai_company_adoption.csv`** — other files not needed

**Key columns:**
- Target: `revenue_growth_percent`
- Numerical features: `ai_adoption_rate`, `ai_maturity_score`, `ai_budget_percentage`, `ai_training_hours`, `num_ai_tools_used`, `ai_projects_active`, `task_automation_rate`, `time_saved_per_week`, `ai_investment_per_employee`, `num_employees`, `annual_revenue_usd_millions`, `company_age`
- Categorical features: `industry`, `company_size`, `region`, `ai_adoption_stage`, `ai_primary_tool`, `ai_use_case`, `ai_ethics_committee`
- Drop: `response_id`, `company_id`, `survey_source`, `data_collection_method`, `country` (use `region` instead)

---

## Stack

| Tool | Purpose |
|---|---|
| Python 3.9 | Analysis |
| pandas, numpy | Data wrangling |
| scikit-learn | Modeling |
| matplotlib, seaborn | Plotting |
| Tableau Public | Dashboards |

---

## Models Required (Option A Rubric)

1. **Parametric:** Linear Regression — interpret coefficients in business terms
2. **Nonparametric:** Random Forest Regressor — tune with cross-validation
3. **Metrics:** RMSE, R², MAE on test set
4. **Split:** 80/20 train/test, random_state=42
5. **Tuning:** RandomizedSearchCV on Random Forest

---

## Report Structure (10 pages max)

1. Executive Summary (1 page)
2. Business Question & Context
3. Data Description
4. Methodology
5. Visualizations & Results
6. Managerial Implications
7. Limitations & Risks
8. Conclusion

---

## File Structure

```
CLAUDE.md                          — this file
dataset/
  ai_company_adoption.csv          — main dataset
notebooks/
  analysis.ipynb                   — Python notebook (primary deliverable)
report/
  report.docx                      — written report
docs/superpowers/plans/
  2026-05-07-buan381-final.md      — implementation plan
```

---

## Hard Rules

- Never use the other two CSV files — only `ai_company_adoption.csv`
- Keep notebook clean and commented for grading — cells in logical order
- Report must be business-oriented, not technical dump
- All figures must have labels/titles (rubric penalizes unlabeled plots)
- No AI-generated boilerplate in the report (rubric explicitly flags this)
- random_state=42 everywhere for reproducibility

---

## Current Phase

**Phase 1 — Setup & EDA** (start here)

| Phase | Description |
|---|---|
| 1 | Setup, EDA, feature engineering |
| 2 | Modeling (linear regression + random forest) |
| 3 | Tableau dashboard |
| 4 | Report writing |
