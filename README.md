# Healthcare Expenditure Analysis

## Overview

This project analyzes healthcare spending patterns in the United States using the 2024 Medical Expenditure Panel Survey (MEPS) Full Year Consolidated Data File. Using Python, pandas, and scikit-learn, I explored how healthcare expenditures vary across demographic and insurance groups and developed predictive models to evaluate the relationship between individual characteristics and healthcare costs.

## Business Questions

- How does healthcare spending vary across age groups?
- How do expenditures differ across insurance coverage categories?
- How concentrated are healthcare expenditures among high-cost individuals?
- Can demographic, insurance, and self-reported health characteristics help predict healthcare expenditures?

## Data Source

- **Source:** Agency for Healthcare Research and Quality (AHRQ)
- **Dataset:** 2024 Medical Expenditure Panel Survey (MEPS), Full Year Consolidated Data File
- **Target variable:** Total healthcare expenditures (`TOTEXP24`)
- **Survey weight:** `PERWT24F`

Raw MEPS data are not included in this repository. Users should obtain the dataset directly from the AHRQ website.

## Tools and Technologies

- Python
- pandas and NumPy
- Matplotlib
- scikit-learn
- Jupyter Notebook

## Methodology

1. Cleaned and prepared MEPS demographic, insurance, health status, and expenditure variables.
2. Conducted exploratory data analysis to examine weighted healthcare expenditure patterns.
3. Compared spending across age and insurance categories using MEPS person-level survey weights.
4. Examined the concentration of healthcare spending among high-expenditure individuals.
5. Developed a weighted Random Forest regression model and compared its performance against a weighted mean baseline.
6. Evaluated model performance using weighted MAE, weighted RMSE, weighted R-squared, and residual analysis.

## Preliminary Model Results

The initial random forest model, using demographic and insurance characteristics without self-reported health status, produced the following results on a held-out test set:

| Metric | Mean Baseline | Random Forest |
|---|---:|---:|
| Weighted MAE | $10,698.37 | $9,971.63 |
| Weighted RMSE | $25,815.18 | $25,541.62 |
| Weighted R-squared | -0.0004 | 0.0207 |

The random forest reduced weighted MAE by approximately 6.8% relative to the baseline. However, the low R-squared indicates that the model explains only a small portion of expenditure variation.

*These are preliminary baseline-model results. Additional model comparisons and final results should be reported separately.*

## Limitations

- Healthcare expenditures are highly right-skewed, with a relatively small number of individuals accounting for a large share of total spending.
- Predictive performance is limited, particularly for individuals with exceptionally high expenditures.
- Insurance categories combine age and coverage characteristics, so observed differences should not be interpreted as causal effects of insurance.
- MEPS uses a complex survey design. Person-level weights were incorporated into weighted analyses and model evaluation, but the modeling process does not fully account for all aspects of the survey design, such as stratification and clustering.
- Findings are descriptive and predictive, not causal.

## Repository Contents

- `notebooks/01_healthcare_expenditure.ipynb` — Main analysis and modeling notebook.
- `output/expenditure_by_insurance.png` — Healthcare expenditures by insurance category.
- `output/feature_importance.png` — Random forest feature importance.
- `output/high_cost_spending_concentration.png` — Concentration of healthcare expenditures.

## How to Run

1. Clone this repository.
2. Download the 2024 MEPS Full Year Consolidated Data File from AHRQ.
3. Place the required raw data files in the local `data/` directory.
4. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

5. Open `notebooks/01_healthcare_expenditure.ipynb` in Jupyter Notebook or VS Code.
6. Run the notebook cells in order.

## Disclaimer

This project was created for educational and portfolio purposes. It is not intended for clinical, underwriting, or insurance pricing decisions.
