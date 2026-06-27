# Employee Attrition Classification System

## Overview
This repository contains a predictive Machine Learning pipeline designed to classify and identify high-risk factors leading to employee turnover. By analyzing HR metrics such as job satisfaction, salary, work-life balance, and performance ratings, this system provides actionable insights for HR departments to preemptively address employee attrition.

# 📊 Employee Attrition Prediction & HR Analytics

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Scikit--Learn-orange)
![Data Visualization](https://img.shields.io/badge/Data%20Viz-Seaborn%20%7C%20Matplotlib-green)

## 🚀 Project Overview
Employee attrition is a massive cost for businesses. This project applies Machine Learning to an HR dataset to predict **which employees are at the highest risk of leaving** and uncovers the **root causes of turnover**. 

Unlike generic predictive models that focus solely on overall accuracy, this project prioritizes **Recall** to ensure the business doesn't miss actual flight-risk employees, providing actionable recommendations for HR teams.

---

## 🔍 The Business Problem
HR departments often rely on exit interviews to understand why people leave—by then, it's too late. The objective of this analysis is to:
1. Identify the hidden patterns driving attrition.
2. Build a predictive model to flag at-risk employees early.
3. Deliver concrete, data-backed retention strategies to HR leadership.

---

## 🛠️ Data Science Approach & Methodology

### 1. Exploratory Data Analysis (EDA)
- Analyzed attrition rates across 1470 employees.
- Uncovered severe leakage in specific job roles (e.g., Sales Representatives at ~40% attrition).
- Mapped attrition against Work-Life Balance, Tenure, and Monthly Income.

### 2. Data Preprocessing
- Handled categorical variables using **One-Hot Encoding** (e.g., Business Travel, Department, Gender).
- Applied **StandardScaler** to normalize numerical features (Age, Income, Years at Company) to prepare data for distance-based and linear models.

### 3. Machine Learning Modeling
Trained and compared three classification models, explicitly handling class imbalance (84% Stayed / 16% Left) using the `class_weight='balanced'` parameter:
- **Logistic Regression** (Baseline & Explainability)
- **Random Forest Classifier**
- **Gradient Boosting Classifier**

---

## 📈 Model Evaluation: The "Accuracy Trap"
A major finding in this project is that in imbalanced HR data, **Accuracy is a misleading metric**. 

- **Random Forest** achieved the highest overall accuracy (**87.4%**), but it did so by simply predicting "No Attrition" for almost everyone. Its Recall was extremely poor (caught only 9 out of 39 actual leavers).
- **Logistic Regression** (The Winner): Selected as the best model despite a lower overall accuracy (71.4%). It achieved the **highest Recall (61.5%)**, successfully identifying 24 out of 39 true flight risks. 

**Business Logic:** Missing an employee who is about to quit (False Negative) is far more costly than falsely flagging someone who stays (False Positive). Therefore, Logistic Regression is the most actionable model for HR intervention.

---

## 💡 Key Business Insights (Feature Importance)
By extracting the coefficients from the Logistic Regression model, the data proved that **salary alone does not explain employee turnover**. The top 3 drivers of attrition are:

1. **🚨 Severe Burnout (Overtime):** Forced overtime is the absolute #1 reason employees quit.
2. **✈️ Role Exhaustion (Business Travel):** Frequent travel drastically accelerates burnout.
3. **👤 Demographic Risk (Marital Status):** Single employees show a significantly higher flight risk, likely due to a higher career risk tolerance.

**High-Risk Zones:** The models highlighted **Sales Representatives** and **Laboratory Technicians** as immediate retention priorities.

---

## 🎯 Strategic HR Recommendations
Based on the predictive model and EDA, the following actions are recommended to the HR Director:
1. **Implement Overtime Caps:** Enforce strict limits on mandatory overtime or introduce mandatory 'comp-off' policies to directly tackle the #1 cause of burnout.
2. **Targeted Stay-Interviews:** Proactively engage single employees in high-travel roles within their critical first two years at the company.
3. **Model Operational Guidance:** HR should use this model as an "early warning radar" to guide supportive check-ins, knowing the model is aggressively tuned to catch risks (and may produce some false alarms).

---

## 💻 How to Run This Project

### Prerequisites
- Python 3.x
- Jupyter Notebook

### Installation
1. Clone this repository:
   ```bash
   git clone [https://github.com/yourusername/hr-attrition-analytics.git](https://github.com/yourusername/hr-attrition-analytics.git)
