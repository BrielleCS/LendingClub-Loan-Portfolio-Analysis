# LendingClub Loan Portfolio Analysis: Realized Risk, Return, and Portfolio Concentration

![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat&logo=jupyter&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=flat&logo=python&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![Tableau Public](https://img.shields.io/badge/Tableau_Public-E97627?style=flat&logo=tableau&logoColor=white)

## Overview
This analysis evaluates credit risk, loan performance, and portfolio concentration using over 2.2 million loans from the LendingClub dataset (2007–2018). The focus is on ~1.3 million finalized loans with `Fully Paid` or `Charged Off` status to measure realized portfolio outcomes.

The analysis uses SQL for aggregation, Python for preprocessing and analysis, and Tableau for dashboard development to identify high-risk segments, evaluate risk-adjusted returns, and assess portfolio concentration.

### Key Objectives:
- Analyze portfolio default trends across origination cohorts
- Identify borrower segments contributing most to realized defaults
- Evaluate risk-adjusted returns across credit grades
- Measure portfolio concentration across loan purposes and geographic regions
- Develop interactive Tableau dashboards for portfolio monitoring

---

## Business Questions

#### 1. Portfolio Health & Default Trends
How does loan performance vary across loan origination cohorts from 2007–2018, and what patterns emerge in portfolio credit risk over time?

#### 2. Default Contribution & Risk Distribution
Which grades contribute most to loan defaults, and how is risk distributed across subgrades and borrower segments?

#### 3. Risk vs. Return Optimization
How does net return performance vary across grades relative to default risk?

#### 4. Portfolio Concentration & Diversification Risk
Is the portfolio heavily concentrated across specific borrower segments or geographic regions?

---

## Tableau Dashboards

| Dashboard | Description | CSV Files | Preview |
|---|---|---|---|
| **Executive Portfolio Health Overview** | Funded volume distribution, default rate, and cohort default trends | [**exposure_and_default.csv**](data/exposure_and_default.csv)<br>[**default_rate_pct_time.csv**](data/default_rate_pct_time.csv) | ![Plot](images/Executive_Portfolio_Health_Overview.png) |
| **Default Contribution & Risk Distribution** | Pareto analysis of defaults and borrower risk segmentation | [**default_contribution_pareto.csv**](data/default_contribution_pareto.csv)<br>[**segment_exposure.csv**](data/segment_exposure.csv) | ![Plot](images/Default_Contribution_&_Risk_Distribution.png) |
| **Credit Risk & Return Analysis** | Net return, yield efficiency, average interest rate, and risk-return tradeoff analysis | [**return_risk_int.csv**](data/return_risk_int.csv) | ![Plot](images/Profitability_&_Yield_Metrics.png) |
| **Strategic Exposure & Diversification** | Geographic exposure, portfolio concentration, Lorenz curve, and Gini coefficient | [**segment_exposure.csv**](data/segment_exposure.csv)<br>[**lorenz_curve.csv**](data/lorenz_curve.csv)<br>[**gini_coefficient.csv**](data/gini_coefficient.csv) | ![Plot](images/Strategic_Exposure_&_Diversification.png) |

> **Technical Note:** The Lorenz curve and Gini coefficient are computed in Python due to the large dataset size (~1.3M borrowers) and the need for borrower-level cumulative calculations. The resulting visualization is embedded in a Tableau dashboard.

---

## Executive Summary

### Portfolio Metrics

- **Total Funded Volume**: \$19.4B
- **Realized Losses**: \$4.2B
- **Weighted Average Default Rate**: 21.55%
- **Peak Cohort Default Rate**: 26.61% (July 2016 cohort)
- **Default Concentration**: 18 of 35 subgrades accounted for 80% of realized defaults
- **Highest Risk Borrower Segment**: Renters with Grade G loans — 54.87% default rate
- **Realized Net Return**: \$543.4M
- **Average Interest Rate**: 13.65%
- **Net Return Efficiency**: 2.80%
- **Top Loan Purpose Share**: Debt Consolidation — 61.27% share, \$11.9B exposure
- **Top State Exposure**: California — $2.9B exposure, 19.6% default rate
- **Portfolio Inequality Index**: 0.336 Gini Coefficient

### Key Insights

- **Cohort Default Trends**: Default rates peaked at 26.6% in the July 2016 origination cohort, indicating a period of elevated credit risk and weaker underwriting performance.
- **Default Distribution**: Defaults were broadly distributed across the portfolio, with 18 of 35 subgrades contributing to 80% of total defaults.
- **Highest Risk Segment**: Renters with Grade G loans exhibited the highest observed default rate at 54.9%.
- **Risk vs. Return**: Grades A and B generated the strongest risk-adjusted returns (~5%) while lower grades experienced deteriorating profitability and materially higher default exposure.
- **Portfolio Concentration**: Debt consolidation loans accounted for 61.27% of funded volume, while California represented the largest geographic exposure.
- **Portfolio Inequality**: The Gini coefficient of 0.336 indicates moderate concentration risk across borrower exposure.

### Business Recommendations

- Implement automated monitoring and back-testing of underwriting models to detect deteriorating loan quality earlier and reduce future default exposure.
- Apply targeted lending restrictions and risk-based pricing for high-risk borrower combinations rather than relying solely on broad credit grade limits.
- Focus origination on Grades A–C, where risk-adjusted returns remain strongest, and tighten underwriting or pricing in lower grades where default risk outweighs yield.
- Diversify lending across loan purposes and geographic regions to reduce concentration risk and improve portfolio resilience.

---

## Analysis Workflow (Dashboard Architecture)

### Data Preparation
- Data Exploration, Filtering, and Cleaning

### Dashboard 1: Executive Portfolio Health Overview
- Funded Volume Distribution
- Default Rate
- Cohort Default Rate by Origination Month (2007–2018)

### Dashboard 2: Default Contribution & Risk Distribution
- Default Contribution by Grade (Pareto)
- Default Contribution by Subgrade (Pareto)
- Risk Matrix: Homeownership vs. Grade

### Dashboard 3: Credit Risk & Return Analysis
- Net Return
- Net Return Efficiency
- Risk vs. Return
- Average Interest Rate

### Dashboard 4: Strategic Exposure & Diversification
- Geographic Risk Exposure
- Portfolio Concentration & Inequality (Lorenz Curve & Gini Coefficient)
- Portfolio Concentration by Loan Purpose

---

## Technologies Used
- Python (Pandas, NumPy, Matplotlib, SQLAlchemy)
- PostgreSQL
- Tableau Public
- Jupyter Notebook
- Git / GitHub

---

## Data Preparation

- Processed the dataset in 100k-row chunks to manage memory usage efficiently
- Filtered finalized loans (`Fully Paid`, `Charged Off`)
- Selected 20 relevant analytical columns
- Standardized datetime fields
- Handled missing values
- Loaded cleaned data into PostgreSQL for querying and aggregation
- Generated a reproducible 1,000-row sample (`accepted_loans_sample.csv`) for GitHub portability, ensuring notebook runs instantly for reviewers

---

## Technical Skills Demonstrated

### Python
- Data preprocessing
- Memory-efficient chunking
- Missing value handling
- Datetime conversion
- Lorenz curve construction and visualization
- Gini coefficient calculation

### SQL
- CTEs
- Window functions
- Aggregations

### Tableau
- Dashboard development
- KPI visualization

### Analytics Concepts
- Credit risk analysis
- Cohort analysis
- Pareto analysis
- Risk-return optimization
- Portfolio concentration analysis
- Loan distribution inequality (Lorenz curve & Gini coefficient)

---

## Repository Structure

```
LendingClub_Loan_Portfolio_Analysis/
|
|-- data/ (CSV outputs used in analysis)
| |-- accepted_loans_sample.csv
| |-- exposure_and_default.csv
| |-- default_rate_pct_time.csv
| |-- default_contribution_pareto.csv
| |-- segment_exposure.csv
| |-- return_risk_int.csv
| |-- lorenz_curve.csv
| |-- gini_coefficient.csv
|
|-- images/ (Saved dashboards)
| |-- Executive_Portfolio_Health_Overview.png
| |-- Default_Contribution_&_Risk_Distribution.png
| |-- Profitability_&_Yield_Metrics.png
| |-- Strategic_Exposure_&_Diversification.png
| 
|-- notebook/
| |-- LendingClub_Loan_Portfolio_Analysis.ipynb
|
|-- README.md
```