# Extreme Heat and Poor Mental Health in the United States (2024)  

## Overview

This repository documents a geospatial workflow examining heat exposure and mental health outcomes across the US (2024), implementing Global Moran’s I and LISA for hotspot identification, followed by global linear regression and spatial lag modeling. The project emphasizes the importance of spatial dependence and compares **absolute** versus **relative** measures of extreme heat in explaining mental health disparities.

The analysis is conducted at the Zip Code Tabulation Area (ZCTA) level.

---

## Research Motivation

Anthropogenic climate change is increasing the frequency and intensity of extreme heat events in the United States. At the same time, poor mental health affects a substantial share of the adult population. Prior research suggests a link between heat exposure and adverse mental health outcomes, but results vary depending on modeling choices and heat metrics.

This project addresses two key gaps:
1. The failure of conventional regression approaches to account for spatial autocorrelation.
2. The reliance on relative heat indicators that may obscure the effects of absolute heat intensity.

---

## Research Questions

- How are poor mental health outcomes spatially distributed across the United States?
- Is there evidence of spatial clustering and spatial dependence in poor mental health prevalence?
- How do **absolute heat measures** (maximum temperature) compare with **relative heat measures** (extreme heat days) in predicting poor mental health outcomes?
- Do results change when spatial dependence is explicitly modeled?

---

## Data Sources

All data correspond to the year 2024 and are aggregated to the ZCTA level.

### Mental Health Outcomes
- Crude prevalence of adults (18+) reporting ≥14 days of “not good” mental health  
- Source: CDC Heat & Health Tracker

### Extreme Heat Measures
- **Absolute:** Annual maximum temperature (°C), derived from PRISM gridded climate data  
- **Relative:** Number of extreme heat days (days above the 95th percentile of historical temperature)  
- Sources: PRISM Climate Group; CDC Heat & Health Tracker

### Covariates
- Sociodemographic score (composite index)
- Impervious surface coverage (%)
- Tree canopy coverage (%)
- Mobile homes (%)
- Households without vehicle access (%)
- Days above PM2.5 regulatory threshold
- Percent white population  
- Sources: CDC; U.S. Census Bureau (ACS 5-Year Estimates)

---

## Methods

### Study Design
- Cross-sectional ecological analysis at the ZCTA level  
- Covariate selection informed by a Directed Acyclic Graph (DAG)  
- Poor physical health treated as a mediator and excluded from regression models  

### Analytical Approach

1. **Exploratory Spatial Analysis**
   - Choropleth maps of poor mental health prevalence and key predictors  
   - Global Moran’s I to assess spatial autocorrelation  
   - Local Indicators of Spatial Association (LISA) to identify clustering patterns  

  <img width="644" height="557" alt="image" src="https://github.com/user-attachments/assets/f634904c-0792-4770-bf33-b44a5f8f08d9" />
  <img width="717" height="346" alt="image" src="https://github.com/user-attachments/assets/3ca1cb4b-412c-4fe1-b13f-87a28d7d9af7" />

2. **Regression Modeling**
   - Global linear regression models  
   - Spatial lag models to account for spatial dependence  
   - Separate model sets for:
     - Maximum temperature (absolute heat indicator)
     - Extreme heat days (relative heat indicator)

3. **Software**
   - All analyses conducted in Python using spatial and statistical libraries  

---

## Key Results

### Spatial Patterns
- Poor mental health prevalence exhibits strong geographic clustering.
- High-prevalence clusters are concentrated in:
  - The Southeastern United States
  - Areas overlapping with Native American reservations
- Global Moran’s I indicates strong positive spatial autocorrelation (I ≈ 0.71).

### Regression Findings

#### Maximum Temperature (Absolute Measure)
- Strong, positive, and statistically significant association with poor mental health.
- Remains significant after controlling for covariates and spatial dependence.
- Effect size larger than most sociodemographic and environmental predictors.

#### Extreme Heat Days (Relative Measure)
- Not significantly associated with poor mental health once controls and spatial dependence are included.
- Effect sizes near zero in both global and spatial models.

#### Spatial Dependence
- Spatial lag terms are large and statistically significant.
- Mental health outcomes in one area are strongly influenced by neighboring areas.

---

## Interpretation

Results indicate that **absolute heat intensity**, rather than deviations from historical temperature norms, is a more meaningful predictor of poor mental health outcomes. Accounting for spatial dependence substantially alters effect estimates and improves model validity.

Strong spatial clustering underscores the role of shared environmental, social, and structural conditions, particularly in historically marginalized regions.

---

## Limitations

- Model assumptions (e.g., multicollinearity) were not exhaustively tested.
- Maximum temperature does not fully capture perceived heat stress; metrics such as heat index or wet-bulb temperature may be more appropriate.
- Missing data for some ZCTAs due to Census reporting limitations.

---

## Implications and Future Work

- Spatial methods should be standard practice in population mental health analyses.
- Policymakers should consider absolute heat exposure when assessing climate-related mental health risks.
- Future research should:
  - Incorporate humidity-based heat metrics
  - Explore longitudinal designs
  - Investigate mechanisms linking heat exposure to mental health outcomes
