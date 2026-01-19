# Predictive Modeling & Model Selection with Random Forests

## Overview

This project compares multiple predictive models to estimate a continuous response variable using approximately 19 numeric predictors and 20,000 observations. The goal was to identify a model with strong generalization performance through systematic experimentation and evaluation. Models were evaluated using 10-fold cross-validated RMSE and validation RMSE. After model selection, the best-performing model was retrained on the full dataset and used for final prediction.

## Models Evaluated

The following approaches were tested, ranging from linear to advanced ensemble methods:

- Linear Regression (baseline)
- LASSO Regression
- Principal Component Regression (PCR)
- Generalized Additive Model (GAM)
- Random Forest
- Gradient Boosting Machine (GBM)

## Model Selection & Results

- Tree-based ensemble models substantially outperformed linear methods, indicating strong nonlinear structure in the data.
- Random Forest achieved the lowest validation RMSE (~4.05)
- GBM performed competitively but did not surpass Random Forest
- Linear models (LM, LASSO, PCR) produced higher RMSE values (~5.18–5.19)
- Random Forest also showed excellent consistency between cross-validated, validation, and out-of-bag error, indicating strong generalization and no evidence of overfitting.

## Final Model

The final model was a tuned Random Forest trained on all 20,000 observations:

- mtry = 9
- ntree = 200
- OOB RMSE ≈ 4.01
- ~57% variance explained

## Feature Importance

Variable importance was assessed using %IncMSE, revealing a small subset of highly influential predictors (notably X11, X13, and X1), while many variables contributed little or no predictive signal. This aligns with findings from LASSO and supports the presence of nonlinear interactions.

## Reproducibility

All data preprocessing, model training, hyperparameter tuning, and evaluation were reproduced in a Quarto (.qmd) file using a fixed random seed.

## Tech Stack

- R/RStudio
- caret, randomForest, glmnet, mgcv, xgboost
- Quarto (.qmd) for reproducible reporting
