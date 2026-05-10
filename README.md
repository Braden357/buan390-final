# BUAN 390 Final Project — AI Adoption & Revenue Growth

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Braden357/buan390-final/blob/main/notebooks/analysis.ipynb)

**Course:** BUAN/ECON 390 — Business Analytics  
**Option:** A — Prediction-Based Analysis  
**Group members:** *(add names here)*

---

## Business Question

What company characteristics and AI investment factors best predict revenue growth? We use linear regression and a tuned random forest to identify the strongest predictors across 150,000 companies globally.

---

## How to Run (Colab)

1. Click the **Open in Colab** badge above
2. In Colab: **Runtime → Run all**
3. The notebook auto-detects its environment and downloads the data if needed
4. Tuning cell takes ~5 minutes on Colab free tier

---

## Deliverables

| File | Description |
|---|---|
| `notebooks/analysis.ipynb` | Main analysis notebook |
| `dataset/ai_company_adoption.csv` | Source dataset (150k rows, Kaggle) |
| `report/report.docx` | Written business report |
| Tableau Public | *(add link here after publishing)* |

---

## Dataset

- **Source:** [Kaggle — mohankrishnathalla/global-ai-adoption-and-workforce-impact-dataset](https://www.kaggle.com/datasets/mohankrishnathalla/global-ai-adoption-and-workforce-impact-dataset)
- **Size:** 150,000 rows × 43 columns, zero nulls
- Only `ai_company_adoption.csv` is used for modeling

---

## Methods

- **Parametric:** Linear Regression (sklearn)
- **Nonparametric:** Random Forest Regressor, tuned via `RandomizedSearchCV` (3-fold CV)
- **Split:** 80/20 train/test, `random_state=42`
- **Metrics:** RMSE, MAE, R² on test set

---

## Requirements

All packages ship with Colab by default:

```
pandas, numpy, matplotlib, seaborn, scikit-learn
```
