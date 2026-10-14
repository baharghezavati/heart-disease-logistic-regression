# heart-disease-logistic-regression
Heart Disease Prediction using Logistic Regression and Clinical Features in R
# Heart Disease Risk Prediction using Logistic Regression and Clinical Features

## Overview and Problem Statement
Heart disease is a leading cause of mortality worldwide[cite: 1]. Clinical diagnostic procedures can be complex and invasive[cite: 1]. Accurately predicting the presence of heart disease using patient clinical attributes helps cardiologists improve diagnostic accuracy and enable early intervention[cite: 1].

This project builds an interpretable predictive model using R to identify key risk factors and predict heart disease status based on clinical patient data[cite: 1].

---

## Dataset and Preprocessing
* Source: UCI Machine Learning Repository (Cleveland Clinic Foundation)[cite: 1].
* Data Cleaning: The initial dataset contained 1025 raw records[cite: 1, 3]. To prevent data leakage and overfitting, 723 duplicate rows were removed, resulting in 302 unique patient records[cite: 1, 3].
* Class Distribution: Balanced dataset containing 164 patients with heart disease (54.3%) and 138 healthy individuals (45.7%)[cite: 2].
* Outlier Handling: Clinical outliers such as cholesterol level around 564 mg/dl were intentionally retained because they represent true high-risk clinical profiles in real-world patients[cite: 4, 5].

---

## Methodology and Feature Selection
* Data Preparation: Encoded categorical variables such as sex, chest pain type, and thalassemia into R factor levels[cite: 3].
* Multicollinearity Check: Evaluated correlation across all 13 attributes; all pairwise correlations were below 0.7, indicating no severe multicollinearity[cite: 7].
* Model Baseline: Linear Regression (OLS) was evaluated with R-squared of 0.575, but discarded as OLS is unsuitable for binary classification[cite: 9].
* Feature Selection: Combined clinical domain knowledge with Stepwise selection based on Akaike Information Criterion (AIC)[cite: 10].
  * Retained Features: chest pain type, max heart rate, exercise induced angina, oldpeak, slope, vessels colored, thalassemia, and sex[cite: 10].
  * Excluded Features: age, resting blood pressure, cholesterol, fasting blood sugar, and resting ECG were excluded as direct diagnostic indicators superseded their predictive contribution[cite: 10, 11].

---

## Model Performance and Threshold Analysis

A Logistic Regression model was trained on 241 observations and evaluated on 61 holdout test cases[cite: 11, 12].

### Performance Comparison Table

| Metric | Default Threshold (0.5) | Tuned Threshold (0.3) |
| :--- | :--- | :--- |
| Accuracy | 80.3% | 78.7%[cite: 12, 13] |
| Specificity | 82.1% | 67.9%[cite: 12, 13] |
| Sensitivity (Recall) | 78.8% | 87.9%[cite: 12, 13] |
| False Negatives | 7 patients | 4 patients[cite: 12, 13] |

Key Clinical Insight: In medical diagnostics, missing a sick patient (False Negative) has a severe cost[cite: 13]. Lowering the decision threshold from 0.5 to 0.3 improves Sensitivity from 78.8% to 87.9%, prioritizing patient safety by detecting more high-risk individuals[cite: 12, 13].

---

## Tools Used
* **R / Radiant:** Data cleaning, factor encoding, OLS baseline, Logistic Regression modeling, and AIC Stepwise variable selection[cite: 1, 3, 7, 10].
* **Tableau:** Visualizations for exploratory data analysis (e.g., chest pain vs risk distribution, heart disease distribution by sex)[cite: 1, 6].

---

## Project Documentation
The complete project presentation and detailed methodology, visualizations, and statistical outputs are available in the repository as [`Heart_Disease_Project_Report.pdf`](./Heart_Disease_Project_Report.pdf)[cite: 1].
