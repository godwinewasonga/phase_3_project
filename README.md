# Live Tap Consultancies #

# Income Prediction Study


## Overview

This repository contains the code and analysis for a machine learning study focused on predicting an individual's annual income based on various demographic and work-related features. The primary objective is to build predictive models to classify income into two categories: `>50K` (higher income) and `<=50K` (lower income).
ncies
## Objectives

This study addresses the following key objectives:

1.  **Predictive Modeling:** Utilize demographic and work-related features (e.g., age, education, occupation, hours-per-week, capital gain/loss) to predict an individual’s annual income.
2.  **Feature Importance:** Quantify which attributes—such as education level, occupation, or hours worked—most strongly drive the `>50K` outcome using various model interpretability methods (e.g., Logistic Regression coefficients, Decision Tree, and Random Forest feature importances).
3.  **Subgroup Analysis:** Examine how income varies across various subgroups (e.g., gender, race, marital status, native country) within the dataset, exploring potential correlations with income for different demographic slices.

## Data

The dataset used for this study includes a range of demographic and work-related features. (Optional: Briefly mention the source of the data if it's publicly available, e.g., "Derived from the Adult Census Income dataset.")

**Key Features:**
* `age`: Age of the individual.
* `education_num`: Numerical representation of education level.
* `capital_gain`: Capital gains.
* `capital_loss`: Capital losses.
* `hours_per_week`: Number of hours worked per week.
* `marital_status`: Marital status (e.g., `Married-civ-spouse`, `Never-married`).
* `occupation`: Type of occupation (e.g., `Exec-managerial`, `Handlers-cleaners`).
* `relationship`: Relationship status (e.g., `Wife`, `Husband`).
* `gender`: Gender (Male/Female).
* `native_country`: Country of origin.
* *(Add any other significant features from your dataset)*

**Target Variable:**
* `income`: Binary classification (`>50K` or `<=50K`).

## Methodology

The study followed a standard machine learning workflow:

1.  **Data Loading & Initial Exploration:** Understanding the dataset structure and initial distributions.
2.  **Data Preprocessing:**
    * Handling categorical features (e.g., One-Hot Encoding).
    * Scaling numerical features using `StandardScaler`.
    * Splitting data into training and testing sets, ensuring stratification of the target variable.
3.  **Model Training & Evaluation:**
    * **Logistic Regression:** Trained as a baseline linear model.
    * **Decision Tree:** Explored for non-linear relationships and direct interpretability.
    * **Random Forest:** Utilized as an ensemble method for improved performance and robust feature importance.
4.  **Addressing Class Imbalance:** Applied `SMOTE` (Synthetic Minority Over-sampling Technique) to the training data for Logistic Regression to improve performance on the minority (`>50K`) class.
5.  **Model Interpretation:**
    * Analyzed Logistic Regression coefficients to understand linear feature impact.
    * Examined feature importance from Decision Tree and Random Forest models to understand predictive power.
    * Utilized classification reports and confusion matrices to evaluate precision, recall, and F1-score for each class.

## Results & Key Insights

### Predictive Performance
* All models achieved an **overall accuracy of approximately 76%**.
* **Logistic Regression:** Showed good precision for the majority class (`<=50K`) but struggled with precision for the minority class (`>50K`). SMOTE provided minimal improvements in this context.
* **Decision Tree:** Demonstrated significantly higher **recall for the `>50K` class (87%)** compared to Logistic Regression (72%), indicating its ability to identify more high-income individuals. This came with a trade-off of increased false positives for the majority class.
* **Random Forest:** (While full performance metrics are not detailed here, its ensemble nature suggests it would offer robust predictive power and generalization).

### Drivers of Higher Income (`>50K`)
* **`capital_gain`** is consistently the most significant positive driver across all models, having the largest coefficient in Logistic Regression.
* **`marital_status_Married-civ-spouse`** is a consistently strong positive predictor, especially dominant in the single Decision Tree model.
* **`education_num`**, **`age`**, and **`hours_per_week`** are also highly influential features, particularly highlighted by the Random Forest model.
* **`education_Preschool`** is a very strong negative driver, significantly decreasing the likelihood of `>50K` income.

### Income Variation Across Subgroups
* **Marital Status:** Being married (especially `Married-civ-spouse` or `Married-AF-spouse`) strongly correlates with higher income. Conversely, `Never-married` or `Separated` statuses correlate with lower income.
* **Education Level:** Higher `education_num` directly correlates with higher income.
* **Occupation:** Specific occupations (e.g., `Exec-managerial`) correlate positively with higher income, while others (e.g., `Handlers-cleaners`, `Farming-fishing`, `Other-service`) correlate negatively.
* **Gender & Native Country:** While these factors were included, their direct predictive importance in the models was comparatively low. Further, dedicated subgroup analysis (e.g., comparing income distributions directly for gender and racial groups, or using advanced interpretability methods like SHAP values) would be necessary to fully quantify income disparities in these areas.
## Repository structure
├── data/
│   └── (adult.data, adult.test)
├── notebooks/
│   └── income_prediction_analysis.ipynb  
├── other scripts/
│   └── (index, adult.names, )
├── README.md
├── icome_study.ppt
└── (generated plots: decision_tree.pdf, decision_tree_feature_importance, decision_tree_income_prediction_model, )