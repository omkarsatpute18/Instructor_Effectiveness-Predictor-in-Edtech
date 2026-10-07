# Instructor Effectiveness Predictor in EdTech

## 📌 Project Overview

This project focuses on predicting **instructor effectiveness in an EdTech environment** using machine learning.

The objective is to analyze instructor-level learning and engagement metrics and classify instructors into different **effectiveness tiers**. This can help EdTech platforms understand instructor performance and identify areas where additional support or improvement may be required.

> **Note:** The assessment description provided the dataset schema but did not include the actual CSV dataset. Therefore, a reproducible synthetic dataset was created based on the specified schema.

---

## 🎯 Project Objective

The main objectives of this project are:

- Analyze instructor and batch-level performance data.
- Aggregate important learning and engagement metrics at the instructor level.
- Create an instructor effectiveness score/tier.
- Train machine learning classification models.
- Compare different models.
- Evaluate model performance using appropriate classification metrics.
- Use cross-validation to check the reliability of the model.

---

## 📊 Dataset

The project uses a synthetic dataset designed according to the assessment's specified schema.

The original batch-level dataset contains variables such as:

- `batch_id`
- `instructor_id`
- `course_id`
- `completion_rate`
- `dropout_rate`
- `avg_score_improvement`
- `avg_quiz_score`
- `avg_watch_time`
- `assignment_submission_rate`
- `forum_activity_rate`
- `avg_feedback_score`
- `feedback_response_rate`

The data is then aggregated at the instructor level to create instructor performance features.

---

## 🔍 Feature Engineering

Instructor-level metrics are created by aggregating batch-level information.

Important effectiveness features include:

- Completion rate
- Retention rate
- Score improvement
- Quiz performance
- Watch time
- Assignment submission
- Forum activity
- Feedback score
- Feedback response rate

These features are used to represent different aspects of instructor effectiveness.

---

## 🏷️ Target Variable

The target variable is:

```text
effectiveness_tier
```

It represents the instructor's effectiveness category and is used as the target for the classification models.

The feature matrix is represented by `X`, while the target is represented by `y`.

---

## ⚙️ Data Preprocessing

The project includes preprocessing steps such as:

- Handling missing values using `SimpleImputer`
- Feature scaling using `MinMaxScaler`
- Preparing the feature matrix and target variable
- Splitting the data into training and testing sets

`MinMaxScaler` is used in the Logistic Regression pipeline to scale numerical features.

---

## 🤖 Machine Learning Models

Two classification approaches are used:

### 1. Logistic Regression

Logistic Regression is used as a baseline classification model.

The model pipeline includes:

```text
Missing Value Imputation
        ↓
MinMaxScaler
        ↓
Logistic Regression
```

The model uses balanced class weights to handle potential class imbalance.

### 2. Random Forest

A Random Forest classifier is used as the main tree-based model.

The Random Forest configuration includes:

```text
n_estimators = 1000
random_state = 42
class_weight = "balanced"
```

The Random Forest pipeline includes missing-value imputation followed by the classifier.

---

## 📈 Model Evaluation

The models are evaluated using classification performance metrics.

The project also uses **5-fold Stratified Cross-Validation**.

```text
5-Fold Cross Validation

Fold 1 → Train / Validation
Fold 2 → Train / Validation
Fold 3 → Train / Validation
Fold 4 → Train / Validation
Fold 5 → Train / Validation
```

The primary cross-validation scoring metric used is:

```text
F1 Macro
```

Macro F1 is useful when evaluating classification performance across multiple classes because it calculates the F1 score for each class and gives equal importance to each class.

---

## 🔄 Cross-Validation

The project uses:

```python
StratifiedKFold(
    n_splits=5,
    shuffle=True,
    random_state=42
)
```

and evaluates the Random Forest model using:

```python
cross_val_score(
    rf_model,
    X,
    y,
    cv=cv,
    scoring="f1_macro"
)
```

This provides multiple performance scores and helps determine how consistently the model performs across different subsets of the data.

---

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook / Google Colab

---

## 📁 Project Structure

```text
Instructor_Effectiveness-Predictor-in-Edtech/
│
├── main.ipynb
├── instructor_sample_dataset.csv
└── README.md
```

---

## 🚀 Project Workflow

The overall workflow of the project is:

```text
Dataset
   ↓
Data Loading
   ↓
Data Exploration
   ↓
Data Cleaning
   ↓
Feature Engineering
   ↓
Instructor-Level Aggregation
   ↓
Effectiveness Tier Creation
   ↓
Train-Test Split
   ↓
Model Training
   ↓
Logistic Regression
   ↓
Random Forest
   ↓
Model Evaluation
   ↓
5-Fold Cross Validation
   ↓
Final Model Analysis
```

---

## 💡 Key Idea

The core idea of this project is to convert different instructor performance indicators into meaningful machine learning features and use them to predict an instructor's effectiveness tier.

Instead of evaluating instructors using only one metric, the project considers multiple dimensions such as learner completion, retention, score improvement, engagement, feedback, and responsiveness.

This provides a more comprehensive approach to understanding instructor effectiveness in an EdTech platform.

---

## 👨‍💻 Author

**Omkar Satpute**

Data Science / Machine Learning Project

GitHub:  
https://github.com/omkarsatpute18
