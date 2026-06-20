# Diabetes Risk Prediction: Pima Indians Diabetes Dataset

Final team project for ADS-503: Applied Predictive Modeling

## Overview

This project predicts whether a patient has diabetes using clinical measurements from the Pima Indians Diabetes dataset. Six classification models were trained and compared to evaluate the trade-off between predictive performance and interpretability, with a focus on metrics beyond accuracy alone (sensitivity, specificity, F1, and AUC).

## Dataset

- **Source:** [Pima Indians Diabetes Database (Kaggle)](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database)
- **Observations:** 768 patients
- **Predictors (8):** Pregnancies, Glucose, BloodPressure, SkinThickness, Insulin, BMI, DiabetesPedigreeFunction, Age
- **Response:** Outcome (1 = Diabetes, 0 = No Diabetes)

Unrealistic zero values in Glucose, BloodPressure, SkinThickness, Insulin, and BMI were treated as missing and imputed using training-set medians after the train/test split, to avoid data leakage.

## Methods

Models trained and compared on an 80/20 train/test split:

- Logistic Regression (baseline)
- Decision Tree
- Random Forest
- K-Nearest Neighbors (k tuned via 5-fold cross-validation)
- Support Vector Machine (radial kernel)
- Gradient Boosting

KNN and SVM features were scaled using training-set statistics applied to both sets. All models were evaluated on accuracy, sensitivity, specificity, F1 score, and AUC.

## Results

| Model | Accuracy | Sensitivity | Specificity | F1 | AUC |
|---|---|---|---|---|---|
| Logistic Regression | 0.8039 | 0.6038 | 0.91 | 0.6809 | 0.8904 |
| Decision Tree | 0.7582 | 0.5472 | 0.87 | 0.6105 | 0.8127 |
| Random Forest | 0.8235 | 0.6792 | 0.90 | 0.7273 | 0.8841 |
| KNN | 0.7778 | 0.6038 | 0.87 | 0.6531 | 0.8577 |
| SVM | 0.7908 | 0.6226 | 0.88 | 0.6735 | 0.8832 |
| Gradient Boosting | 0.8170 | 0.6604 | 0.90 | 0.7143 | 0.9034 |

**Random Forest** was selected as the final model, providing the best overall balance of accuracy, sensitivity, and F1 while maintaining strong specificity. Gradient Boosting had the highest AUC. Glucose was the strongest predictor of diabetes status across models.

## Team

Christopher Guillen, Andrew Hashoush, Christopher Andra
