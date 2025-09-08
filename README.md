# README

## Project Title

**Investigating the Relationship Between Alcohol Content in Wine and Its Physicochemical Properties**

## Authors

* **Anav Vora**
* **Lavanya Kudli**

## Date

December 16, 2024

---

## Overview

This project explores the relationship between **alcohol content in wine** and a set of **physicochemical properties** (such as acidity, sugar, sulphates, etc.). Using statistical and regression-based modeling approaches, the goal was to:

1. Identify which predictors significantly influence alcohol content.
2. Develop the best predictive model for estimating alcohol content.
3. Evaluate the assumptions of linear models and investigate remedial measures.

---

## Dataset

* Wine dataset consisting of **red and white wines**.
* Predictors:

  * fixed.acidity
  * volatile.acidity
  * citric.acid
  * residual.sugar
  * chlorides
  * free.sulfur.dioxide
  * total.sulfur.dioxide
  * density
  * pH
  * sulphates
  * type (red or white)

The dataset shows:

* Normal distribution in some predictors (fixed.acidity, citric.acid, pH, alcohol, free.sulfur.dioxide, density).
* Skewed distributions in others (volatile.acidity, residual.sugar, chlorides, sulphates).
* White wines are more frequent than red wines.

---

## Methodology

### Exploratory Data Analysis (EDA)

* Histograms and scatter plots to explore predictor distributions.
* Boxplots to compare alcohol content across wine types.

### Model Building (Model A – Prediction Focus)

1. **AIC & BIC criteria** – suggested removing total.sulfur.dioxide.
2. **Leaps-and-bounds (adj. R², BIC, Cp)** – supported \~10 predictors.
3. **Principal Component Regression (PCR)** – suggested using all predictors.
4. **Ridge Regression** – penalty effect minimal, retained all predictors.
5. **LASSO Regression** – retained all predictors, optimal t ≈ 0.989.

**Best prediction model:** 10 predictors (excluding total.sulfur.dioxide) with lowest RMSE ≈ **0.4543**.

### Model Diagnostics

* **Issues found:**

  * High leverage and influential points (21 bad leverage points, 12 outliers).
  * Violations of **constant variance** (BP test p < 2.2e-16) and **normality** (KS test p < 2.2e-16).

### Model Building (Model B – Selection Focus)

* **Backward elimination using partial F-tests**:

  * Dropping total.sulfur.dioxide acceptable (p > 0.05).
  * Dropping chlorides rejected (p < 0.05).
* **Final model matches Model A**, excluding total.sulfur.dioxide.

### Remedial Measures

* **Box-Cox Transformation (λ ≈ -0.4)** applied to alcohol.
* Transformation did not fix variance or normality violations.

---

## Results & Key Findings

* **Best predictive model excludes total.sulfur.dioxide.**
* High R² (\~0.82) indicates strong explanatory power.
* Some model assumptions (constant variance, normality) violated.
* Box-Cox transformation unsuccessful in remedying these issues.
* For prediction-focused applications, violations may be tolerable since point estimates remain accurate.

---

## File Contents

* **CS3\_FA24\_Anav\_Lavanya\_v2.pdf** – Full project report with EDA, modeling steps, diagnostics, and results.

---

## How to Use

1. Read the **Introduction** for context.
2. Follow the **Data Description** to understand variables.
3. Explore the **Model A** and **Model B** sections for different approaches to prediction and selection.
4. Review **Diagnostics** to understand assumption checks and remedial measures.
5. Refer to the **Conclusion** for a summary of insights.

---

## Statistical Tests Summary

* **AIC/BIC**: Model selection criteria → drop total.sulfur.dioxide.
* **Leaps-and-bounds (R², Cp, BIC)**: Supported 10-predictor model.
* **Ridge & LASSO regression**: Penalization approaches; both kept most predictors.
* **Breusch-Pagan test**: Rejected homoscedasticity (variance not constant).
* **Kolmogorov-Smirnov test**: Rejected normality assumption.
* **Partial F-tests**: Guided backward elimination for model selection.
* **Box-Cox transformation**: Attempted fix for normality/variance violations.

---
