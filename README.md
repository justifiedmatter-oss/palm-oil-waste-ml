# Palm Oil Waste Prediction Using Machine Learning

## Project Overview

This project investigates the use of machine learning to predict monthly palm oil waste quantities in Nigeria.

The analysis compares Random Forest, XGBoost, Long Short-Term Memory (LSTM), and an Elastic Net stacking ensemble for predicting four major palm oil waste streams:

- Empty Fruit Bunches (EFB)
- Palm Kernel Shells (PKS)
- Palm Oil Mill Effluent (POME)
- Mesocarp Fibre

The project also incorporates temporal validation, sensitivity analysis, conformal prediction for uncertainty quantification, and model explainability using feature importance and SHAP.

The work was developed from my MSc Management and Information Systems research at Cranfield University.

---

## Research Objective

The main objective was to develop and evaluate a machine-learning framework for predicting palm oil waste quantities while accounting for predictive uncertainty.

A key part of the analysis was determining whether complex machine-learning models provided meaningful improvements over a simple domain-informed conversion-factor baseline.

---

## Dataset

The dataset contains 732 monthly observations covering January 1964 to December 2024.

### Predictor Variables

- Year
- Month Number
- Quarter
- Fresh Fruit Bunch production (FFB)
- Average Temperature
- Rainfall
- Humidity
- Wind Speed
- Solar Radiation

### Target Variables

- EFB
- PKS
- POME
- Mesocarp Fibre

The data were divided chronologically into:

- **Development period:** 1964–2021
- **Independent test period:** 2022–2024

The independent test period was excluded from model selection and hyperparameter tuning.

---

## Modelling Approach

Four machine-learning approaches were evaluated:

1. **Random Forest**
2. **XGBoost**
3. **Long Short-Term Memory (LSTM)**
4. **Elastic Net Stacking Ensemble**

The stacking model combined out-of-fold predictions from Random Forest, XGBoost, and LSTM using Elastic Net as the meta-learner.

Rolling-origin validation was used to preserve the temporal structure of the data.

The primary evaluation metric was RMSE, supported by MAE, MAPE, and R².

---

## Independent Test Results

| Waste Stream | Random Forest RMSE | XGBoost RMSE | LSTM RMSE | Stacking RMSE |
|---|---:|---:|---:|---:|
| EFB | 1.4167 | 1.2578 | **0.6399** | 0.6669 |
| PKS | 0.4069 | 0.3332 | 0.1809 | **0.1698** |
| POME | 4.4452 | 3.6904 | **1.8736** | 1.9221 |
| Mesocarp Fibre | 0.8592 | 0.7181 | **0.3866** | 0.3888 |

The stacking ensemble substantially improved upon Random Forest and XGBoost across all four waste streams.

However, stacking did not consistently outperform the strongest individual model. LSTM achieved the lowest RMSE for EFB, POME, and Mesocarp Fibre, while stacking achieved the lowest machine-learning RMSE for PKS.

---

## Conversion-Factor Baseline

An important finding emerged when the machine-learning models were compared with a simple conversion-factor baseline.

The waste targets in the independent test period corresponded to the following FFB conversion relationships:

- EFB = 22% of FFB
- PKS = 6% of FFB
- POME = 65% of FFB
- Mesocarp Fibre = 13% of FFB

The conversion-factor baseline reproduced the 2022–2024 test targets exactly at the stored dataset precision.

This finding demonstrates why complex machine-learning models should always be compared with appropriate domain-informed baselines.

---

## Sensitivity Analysis

To investigate the influence of FFB, Random Forest and XGBoost models were retrained without the FFB predictor.

Removing FFB substantially increased prediction errors.

For example, XGBoost without FFB produced R² values of approximately 0.94 compared with approximately 0.99 when FFB was included.

This showed that the remaining temporal and environmental predictors retained some predictive information, but FFB was the dominant predictor.

---

## Model Explainability

Random Forest feature importance and SHAP analysis were used to investigate the contribution of individual predictors.

Random Forest attributed approximately **99.92% of average feature importance to FFB**.

XGBoost SHAP analysis produced a similar result:

| Waste Stream | FFB SHAP Importance |
|---|---:|
| EFB | 98.03% |
| PKS | 97.77% |
| POME | 98.14% |
| Mesocarp Fibre | 98.17% |

These results reinforce the strong structural relationship between FFB and the derived waste quantities.

Feature importance is interpreted as predictive rather than causal importance.

---

## Uncertainty Quantification

Additive conformal prediction was applied to the stacking ensemble to quantify predictive uncertainty.

For a nominal 95% prediction interval, empirical coverage on the independent 2022–2024 test period was:

| Waste Stream | Empirical Coverage |
|---|---:|
| EFB | 97.22% |
| PKS | 100.00% |
| POME | 97.22% |
| Mesocarp Fibre | 97.22% |

The results indicate high empirical coverage on the 36-month independent test period, although this should not be interpreted as a guarantee of equivalent future coverage.

---

## Key Findings

- All four machine-learning approaches achieved strong predictive performance.
- XGBoost consistently outperformed Random Forest.
- LSTM achieved the lowest RMSE for three of the four waste streams.
- Stacking achieved the lowest machine-learning RMSE for PKS.
- Conformal prediction provided high empirical test coverage.
- FFB overwhelmingly dominated Random Forest and SHAP feature importance.
- Removing FFB substantially reduced predictive performance.
- Most importantly, the simple conversion-factor baseline reproduced the independent-test targets exactly.

The results demonstrate the importance of combining machine learning with domain knowledge, sensitivity analysis, explainability, uncertainty quantification, and appropriate baseline comparisons.

---

## Repository Structure

```text
palm-oil-waste-ml/
│
├── data/
│   └── palm_oil_waste_dataset_1964_2024.csv
│
├── 01_data_exploration.ipynb
├── 02_data_preprocessing.ipynb
├── 03_model_development.ipynb
├── README.md
└── .gitignore
