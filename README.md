# BUAN 390 Final Project — AI Adoption & Revenue Growth

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Braden357/buan390-final/blob/main/notebooks/analysis.ipynb)

**Course:** BUAN/ECON 390 — Business Analytics  
**Option:** A — Prediction-Based Analysis  
**Group members:** Braden Flynn · Mariano Del Castillo · Josh Mora

---

## Project Status

| Deliverable | Owner | Status |
|---|---|---|
| `notebooks/analysis.ipynb` | Braden | ✅ Complete — executed, all outputs saved |
| `report/report.docx` | Braden | ✅ Complete — 8 figures embedded, ready to submit |
| `dataset/ai_company_adoption.csv` | — | ✅ In repo |
| Tableau Public dashboard | **Mariano / Josh** | ✅ Complete — [view dashboard](https://public.tableau.com/app/profile/joshua.mora4180/viz/BUAN390-AI-Revenue-Growth/Dashboard1) |
| Peer evaluation | Everyone | Due same day — instructor provides form |

**Submit:** notebook + report + CSV + Tableau link

---

## Business Question

What company characteristics and AI investment factors best predict revenue growth? Linear regression and tuned random forest applied to 150,000 company observations.

**Key result:** `productivity_change_percent` is the strongest predictor (r=0.476 with target). Linear Regression RMSE = 4.69%, R² = 0.239.

---

## ⭐ Tableau Instructions (Mariano / Josh — do this part)

### What you're building
Single dashboard, 4 charts. Takes ~30–45 min.

### Step 1 — Get Tableau Public Desktop
Download free at: https://public.tableau.com/en-us/s/download  
(Must use Desktop to publish — web authoring is too limited)

### Step 2 — Sign in
Create a free account at https://public.tableau.com if you don't have one.

### Step 3 — Connect the data
1. Open Tableau Public Desktop
2. On the start screen, click **Text File** under Connect
3. Navigate to the `dataset/` folder in this repo and open `tableau_scatter.csv`
4. Click **Sheet 1** tab at the bottom to start building
5. To add the second data source: **Data menu → New Data Source → Text File → `dataset/tableau_region_summary.csv`**

### Step 4 — Build 4 sheets

#### Sheet 1: "AI Budget vs Revenue Growth" (scatter)
- Data source: `tableau_scatter.csv`
- Drag `Ai Budget Percentage` → Columns
- Drag `Revenue Growth Percent` → Rows
- Drag `Industry` → Color (Marks card)
- Analytics pane (left sidebar) → drag **Trend Line** onto chart → select **Linear**
- Right-click chart title → Edit → type: `AI Budget vs Revenue Growth`

#### Sheet 2: "Revenue Growth by Industry" (bar)
- Data source: `tableau_scatter.csv`
- Drag `Industry` → Rows
- Drag `Revenue Growth Percent` → Columns → change aggregation to **AVG**
- Click **Sort Descending** on the axis
- Drag `Revenue Growth Percent` (AVG) → Color
- Title: `Average Revenue Growth by Industry`

#### Sheet 3: "Revenue Growth by Region" (bar — easier than map)
- Data source: `tableau_region_summary.csv`
- Drag `Region` → Rows
- Drag `Mean Revenue Growth` → Columns
- Drag `Mean Ai Maturity` → Color
- Sort descending
- Title: `Revenue Growth and AI Maturity by Region`

#### Sheet 4: "Revenue Growth by Adoption Stage" (bar)
- Data source: `tableau_scatter.csv`
- Drag `Ai Adoption Stage` → Rows
- Drag `Revenue Growth Percent` → Columns → **AVG**
- Color by `Ai Adoption Stage`
- Title: `Revenue Growth by AI Adoption Stage`

### Step 5 — Build the dashboard
1. Bottom tab → **New Dashboard**
2. Set size: **Automatic**
3. Drag all 4 sheets into the dashboard (2×2 grid)
4. Drag a **Text** object (left panel) to top → type title: `AI Adoption & Revenue Growth — BUAN 390 Final`
5. Add subtitle text: `150,000 company observations · Kaggle dataset · May 2026`

### Step 6 — Publish
1. **Server menu → Tableau Public → Save to Tableau Public As…**
2. Sign in with your account
3. Name it: `BUAN390-AI-Revenue-Growth`
4. After saving, browser opens with the public URL
5. **Copy that URL**

### Step 7 — Add link to report
1. Open `report/report.docx`
2. Find the line near the end: `[Tableau Public dashboard: INSERT LINK HERE]`
3. Replace it with: `Interactive Tableau dashboard: <paste your URL>`
4. Save the file and commit + push

---

## How to Run the Notebook (already done — for reference)

The notebook is fully executed with saved outputs. You don't need to re-run it.

If you want to re-run locally:
```bash
python3 -m nbconvert --to notebook --execute --ExecutePreprocessor.timeout=3600 --inplace notebooks/analysis.ipynb
```

Or click the **Open in Colab** badge above. Runtime → Run all. (~20 min due to RF tuning.)

---

## Deliverables

| File | Description |
|---|---|
| `notebooks/analysis.ipynb` | Main analysis — executed with all outputs |
| `dataset/ai_company_adoption.csv` | Source dataset (150k rows, Kaggle) |
| `report/report.docx` | Written business report with 8 embedded figures |
| [Tableau Public Dashboard](https://public.tableau.com/app/profile/joshua.mora4180/viz/BUAN390-AI-Revenue-Growth/Dashboard1) | Interactive dashboard by Joshua Mora |

---

## Dataset

- **Source:** [Kaggle — mohankrishnathalla/global-ai-adoption-and-workforce-impact-dataset](https://www.kaggle.com/datasets/mohankrishnathalla/global-ai-adoption-and-workforce-impact-dataset)
- **Tableau data:** `dataset/tableau_scatter.csv` (5,000 rows) and `dataset/tableau_region_summary.csv`
- Only `ai_company_adoption.csv` used for modeling

---

## Methods

- **Parametric:** Linear Regression — RMSE 4.69%, R² 0.239
- **Nonparametric:** Random Forest (tuned via `RandomizedSearchCV`, 3-fold CV) — RMSE 4.71%, R² 0.232
- **Split:** 80/20 train/test, `random_state=42`
- **Top predictor:** `productivity_change_percent` (r=0.476, LR coef +0.349)
