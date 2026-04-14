# RDS Project 2025 — Fairness audit of a depression-prediction ADS

This repository holds the **notebooks** and **LaTeX report** for a fairness-focused audit of a high-performing depression prediction pipeline. The work goes beyond leaderboard accuracy: it asks who benefits, who is harmed, and how mitigation trades off against performance.

The analysis is **staged**: broad EDA and attribute-level screening first; student vs. working-professional subgroup work comes **after** other axes show weaker disparity signals.

## Project aim

Grounded in the final report (`Latex/thesis.tex`), the project evaluates:

- predictive performance of ensemble-based models  
- subgroup fairness behavior  
- mitigation trade-offs (fairness vs. accuracy)  
- deployment readiness and risk  

## Work scope

- Culturally embedded disparities and regional representation skew  
- Disparity patterns across gender and employment status  
- Feature correlation and bias hypotheses from EDA  
- Leakage risk from synthetic train/validation construction  
- Null-imputation behavior and identity-field ablations (`Name`, `City`)  
- Subgroup retraining (students vs. professionals)  
- Fairlearn-style metrics and threshold-based mitigation (`ThresholdOptimizer`)  
- Explainability (e.g. LIME) and fairness/accuracy trade-offs summarized in the report  

## Repository layout

| Path | Contents |
|------|----------|
| `notebooks/` | Cleaned, renamed legacy notebooks (section headings, cleared outputs) |
| `Latex/` | Final report source (`thesis.tex` and chapters) |

## Notebook order (recommended)

1. `notebooks/01_eda_overview_and_feature_screening.ipynb`  
2. `notebooks/02_eda_data_distribution_and_regional_skew.ipynb`  
3. `notebooks/03_fairness_audit_experiments.ipynb`  
4. `notebooks/04_subgroup_model_students.ipynb`  
5. `notebooks/05_subgroup_model_working_professionals.ipynb`  

Subgroup ensemble notebooks (`04`–`05`) use numbered sections (e.g. imports through results) for scanning; code cells were not reordered.

## Key findings (high level)

- Strong headline accuracy can coexist with serious subgroup-level unfairness.  
- Employment status often mattered more than gender-only slices for disparity.  
- Thresholding and distribution mismatch drove much of the gap, not only raw feature choice.  
- Fairness mitigation narrowed gaps but cost some overall accuracy.  

## Reproducibility

1. Create a virtual environment and install: `pip install -r requirements.txt`  
2. Add competition/source CSVs under `data/` (see filenames below).  
3. Open Jupyter and run notebooks **top to bottom** in the order above.  
4. Do **not** commit API keys, `kaggle.json`, or large private datasets.  

Expected data paths (adjust if your layout differs):

- `data/train.csv`  
- `data/test.csv`  
- `data/final_depression_dataset_1.csv` (optional, where used in notebooks)  

Notebooks retain Colab/Kaggle cells where relevant; **code outputs are cleared** so diffs stay small on GitHub.
