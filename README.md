# Palm Oil Waste Prediction Using Stacking Ensemble Machine Learning

## Project Overview

This project investigates the use of machine learning to predict quantities of major palm oil waste streams in Nigeria.

The study compares three machine learning models — Random Forest, XGBoost, and Long Short-Term Memory (LSTM) — and combines their predictions using an Elastic Net stacking ensemble.

The project also incorporates time-series validation and conformal prediction to evaluate predictive uncertainty.

This work was developed as part of my MSc Management and Information Systems research at Cranfield University.

## Objectives

The project aims to:

- Develop machine learning models for predicting palm oil waste quantities.
- Compare the predictive performance of Random Forest, XGBoost, and LSTM.
- Develop a stacking ensemble using Elastic Net as the meta-learner.
- Evaluate model performance using time-series validation and an independent test dataset.
- Quantify predictive uncertainty using conformal prediction.

## Predicted Waste Streams

The models predict four major palm oil waste streams:

- Empty Fruit Bunches (EFB)
- Palm Kernel Shells (PKS)
- Palm Oil Mill Effluent (POME)
- Mesocarp Fibre (MF)

## Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- TensorFlow / Keras
- Matplotlib
- Jupyter Notebook

## Machine Learning Models

- Random Forest
- XGBoost
- Long Short-Term Memory (LSTM)
- Elastic Net Stacking Ensemble

## Model Evaluation

Model performance was evaluated using:

- Root Mean Squared Error (RMSE)
- Mean Absolute Error (MAE)
- Mean Absolute Percentage Error (MAPE)
- R²

A rolling-origin validation strategy was used to preserve the temporal structure of the data.

## Repository Structure

```text
palm-oil-waste-ml/
│
├── data/        # Dataset information
├── notebooks/   # Data analysis and machine learning notebooks
├── figures/     # Visualisations and model evaluation figures
├── .gitignore
└── README.md

## Project Status

This repository is being developed from my completed MSc research project. Code, visualisations and documentation are being reorganised into a portfolio-friendly format.
