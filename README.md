# Beyond Accuracy: Diabetes Classification Using the Pima Indians Diabetes Dataset

This project is part of **ADS-503: Applied Predictive Modeling** in the Applied Data Science Program at the University of San Diego.


## Overview

This project predicts whether a patient has diabetes using clinical measurements from the Pima Indians Diabetes dataset. The main goal was to compare multiple classification models and evaluate the trade-off between predictive performance and interpretability.

Because diabetes prediction is a healthcare-related classification problem, this project looks beyond accuracy alone. Models were evaluated using accuracy, sensitivity, specificity, F1 score, and AUC. Sensitivity was especially important because it measures how well the model identifies actual diabetes cases.

## Project Objective

The objective of this project was to answer the following research question:

**Which classification model provides the best balance between predictive performance and interpretability for diabetes prediction using patient health measurements?**

The project was designed as a complete predictive modeling workflow that includes data exploration, preprocessing, train/test splitting, model building, model evaluation, and final model selection.

## Dataset

The dataset used in this project is the **Pima Indians Diabetes Database** from Kaggle. Link to kaggle below
https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database

- **File used:** `diabetes.csv`
- **Observations:** 768 patient records
- **Predictors:** 8 clinical measurements: 
- **Response variable:** `Outcome`
  - `1` = Diabetes
  - `0` = No Diabetes

### Variables

| Variable | Description |
|---|---|
| `Pregnancies` | Number of pregnancies |
| `Glucose` | Plasma glucose concentration |
| `BloodPressure` | Diastolic blood pressure |
| `SkinThickness` | Triceps skin fold thickness |
| `Insulin` | 2-hour serum insulin |
| `BMI` | Body mass index |
| `DiabetesPedigreeFunction` | Diabetes family history score |
| `Age` | Patient age |
| `Outcome` | Diabetes status |

## Data Preprocessing

Although the dataset did not contain missing values coded as `NA`, several variables contained zero values that were not realistic medical measurements. Zero values in the following variables were treated as missing:

- `Glucose`
- `BloodPressure`
- `SkinThickness`
- `Insulin`
- `BMI`

Zero values in `Pregnancies` were kept because a patient can have zero pregnancies. Zero values in `Outcome` were also kept because they represent the no-diabetes class.

The dataset was split into training and testing sets using an 80/20 split. Median imputation was then performed using training-set medians only to avoid data leakage. KNN and SVM predictors were scaled using training-set statistics.

## Methods Used

- Exploratory Data Analysis
- Data Cleaning
- Data Preprocessing
- Train/Test Splitting
- Median Imputation
- Cross-Validation
- Classification Modeling
- Model Evaluation
- Data Visualization

## Models Compared

Six classification models were trained and compared:

- Logistic Regression
- Decision Tree
- Random Forest
- K-Nearest Neighbors
- Support Vector Machine
- Gradient Boosting

## Technologies

This project was completed using:

- R
- RStudio
- Quarto / R Markdown
- GitHub

## Required R Packages

The project uses the following R packages:

```r
library(tidyverse)
library(caret)
library(pROC)
library(rpart)
library(rpart.plot)
library(randomForest)
library(class)
library(e1071)
library(gbm)
```

## Installation

To run this project on another machine, first clone or download this GitHub repository.

Make sure the dataset file `diabetes.csv` is saved in the same folder as the code file:

`pima_indians_dataexploration_and_preprocessing.qmd`

Install the required R packages if they are not already installed:

```r
install.packages(c(
  "tidyverse",
  "caret",
  "pROC",
  "rpart",
  "rpart.plot",
  "randomForest",
  "class",
  "e1071",
  "gbm"
))
```

## How to Run

1. Open `pima_indians_dataexploration_and_preprocessing.qmd` in RStudio.
2. Make sure `diabetes.csv` is saved in the same project folder. (Make sure in case the file is renamed, moved, or saved in a different folder, the code may not run unless the file path in the code is updated. Edit code if needed: diabetes <- read.csv("diabetes.csv") )
3. Install the required R packages if needed.
4. Run the code chunks from top to bottom, or click **Render** to generate the final report.
5. The file will load the data, perform exploratory data analysis, preprocess the data, train classification models, and compare model performance.

## Results

| Model | Accuracy | Sensitivity | Specificity | F1 | AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 0.8039 | 0.6038 | 0.9100 | 0.6809 | 0.8904 |
| Decision Tree | 0.7582 | 0.5472 | 0.8700 | 0.6105 | 0.8127 |
| Random Forest | 0.8235 | 0.6792 | 0.9000 | 0.7273 | 0.8841 |
| KNN | 0.7778 | 0.6038 | 0.8700 | 0.6531 | 0.8577 |
| SVM | 0.7908 | 0.6226 | 0.8800 | 0.6735 | 0.8832 |
| Gradient Boosting | 0.8170 | 0.6604 | 0.9000 | 0.7143 | 0.9034 |

## Final Model

**Random Forest** was selected as the final model because it had the best overall balance of performance. It achieved the highest accuracy, sensitivity, and F1 score while maintaining strong specificity.

Gradient Boosting had the highest AUC, but Random Forest was selected because it performed better on the main metrics most important to the project goal. Glucose was the strongest predictor of diabetes status across the analysis.

## Contributors

- Christopher Guillen
- Andrew Hashoush
- Christopher Andra

## Acknowledgments

This project was completed for **ADS-503: Applied Predictive Modeling** at the University of San Diego.


## License

This project is for educational purposes as part of a graduate course project. The dataset is publicly available from Kaggle. Please review the original Kaggle dataset page for dataset-specific usage terms.
