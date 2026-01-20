# Extreme Heat and Poor Mental Health in the United States (2024)

![Status](https://img.shields.io/badge/Status-Completed-success)
![R](https://img.shields.io/badge/Language-R-blue)
![Python](https://img.shields.io/badge/Language-Python-blue)
![Methods](https://img.shields.io/badge/Methods-Random%20Forest%20%7C%20Spatial%20Lag-orange)

## 📌 Project Overview
This repository documents a **two-phase multi-modal analysis** examining the relationship between extreme heat and mental health outcomes across the US (2024). The analysis is conducted at the **Zip Code Tabulation Area (ZCTA)** level and evolves from standard epidemiological modeling to advanced geospatial analysis:

* **Phase 1 (Risk Modeling):** Initial investigation using Logistic Regression and Random Forest to rank risk factors (R).
* **Phase 2 (Spatial Correction):** Addressed the limitations of Phase 1 by incorporating **Absolute Heat metrics** and accounting for **spatial dependence** (Python).

## 📂 Data Sources & Variables
All data correspond to the year 2024 and are aggregated to the ZCTA level.

### 🧠 Outcome Variable
* **Poor Mental Health:** Crude prevalence of adults (18+) reporting ≥14 days of “not good” mental health.
* **Source:** CDC Heat & Health Tracker.

### 🌡️ Exposure Variables (Heat Metrics)
* **Relative Heat (Phase 1):** Number of extreme heat days (days above the 95th percentile of historical temperature).
* **Absolute Heat (Phase 2):** Annual maximum temperature (°C), derived from PRISM gridded climate data.
* **Sources:** PRISM Climate Group; CDC Heat & Health Tracker.

### 📊 Covariates (Risk Factors)
Covariate selection was informed by a Directed Acyclic Graph (DAG) to control for confounding:
* **Sociodemographics:** Composite sociodemographic score (Poverty, Education), Percent white population, Households without vehicle access.
* **Built Environment:** Impervious surface coverage (%), Mobile home percentage.
* **Natural Environment:** Tree canopy coverage (%), Days above PM2.5 regulatory threshold.
* **Source:** U.S. Census Bureau (ACS 5-Year Estimates) and CDC.

## 🔍 Key Findings

### Phase 1: Risk Modeling (The Baseline)
* **Socioeconomics Dominates:** Random Forest analysis identified **Poverty Status** and **Education Level** as the top predictors of poor mental health prevalence.
* **The Limitation:** Standard logistic regression suggested heat was a secondary factor. However, diagnostic testing revealed high spatial autocorrelation, indicating that standard models were potentially underestimating environmental risks by treating regions as independent.

### Phase 2: Spatial Analysis (The Correction)
* **Accounting for Space:** By switching to a **Spatial Lag Model** (Python), we corrected for the geographic clustering of disease.
* **The Hidden Signal:** Once spatial dependence was accounted for, **Absolute Heat Intensity** (Max Temp) emerged as a significant driver of poor mental health ($p < 0.05$), proving that the "where" matters just as much as the "what."

## 🛠️ Methodology

### Phase 1: Machine Learning & Risk (R)
* **Goal:** Establish baseline risk factors and rank variable importance.
* **Techniques:** Random Forest Regressors, Logistic Regression (GLM), Diagnostic Testing (VIF, Heteroscedasticity).
* **Libraries:** `randomForest`, `caret`, `lmtest`, `tidyverse`.

### Phase 2: Spatial Statistics (Python)
* **Goal:** Correct for spatial autocorrelation ($I \approx 0.71$) and test absolute heat metrics.
* **Techniques:** LISA (Local Indicators of Spatial Association), Spatial Lag Models (Maximum Likelihood), Global Moran's I.
* **Libraries:** `geopandas`, `pysal`, `statsmodels`.

## 📄 Reports & Code

### 📈 Phase 1: Risk Modeling (R)
* **Full Report:** [Read Phase 1 Findings (PDF)](Reports/Phase1_Risk_Modeling.pdf)
* **Source Code:**
    * [Logistic Regression: Odds Ratios](Predictive-Modeling/logistic_regression_risk_model.Rmd)
    * [Random Forest: Variable Importance](Predictive-Modeling/random_forest_risk_model.Rmd)

### 🌍 Phase 2: Spatial Analysis (Python)
* **Full Report:** [Read Phase 2 Findings (PDF)](Reports/Phase2_Spatial_Analysis.pdf)
* **Source Code:** [Geospatial Workflow (Notebook)](Geospatial-Analysis/spatial_econometric_modeling.ipynb)
