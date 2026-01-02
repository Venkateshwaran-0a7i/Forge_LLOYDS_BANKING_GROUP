📊 Forge_LLOYDS_BANKING_GROUP

Customer Churn Analysis & Prediction (Banking Use Case)

Overview

This project analyses and predicts customer churn for Lloyds Banking Group using structured customer data spanning demographics, transactional behaviour, service interactions, and digital engagement.

The objective is not just model accuracy, but to:

Identify actionable churn signals

Prepare regulation-safe, explainable features

Build a dataset ready for production-grade ML pipelines

This work aligns with retail banking risk and retention analytics, where explainability, robustness, and business cost awareness are critical.

🔍 Project Structure
Forge_LLOYDS_BANKING_GROUP/
│
├── data/
│   ├── Customer_Churn_Data_Large.xlsx
│   ├── cleaned_customer_churn_data.csv
│   └── cleaned_customer_churn_data.xlsx
│
├── reports/
│   ├── Data_Cleaning_and_Preprocessing_Report.docx
│   ├── Data_Cleaning_and_Preprocessing_Report_Extended.docx
│   └── Customer_Churn_Analysis_Report.docx
│
├── visuals/
│   ├── churn_distribution.png
│   ├── age_dist_churn.png
│   └── spend_vs_trans.png
│
├── notebooks/
│   └── churn_model_dev.ipynb
│
└── README.md

📈 Key Insights

Churn Rate: ~20.4%
Indicates a material retention risk typical of large retail banking portfolios.

Behavioral Drivers:

Declining transaction count

Reduced monthly spend

Increased support call frequency

These signals consistently precede churn events.

Demographic Trends:
Age shows moderate variability; younger customers exhibit higher volatility, likely due to lower switching costs.

Digital Engagement:
Login frequency and online usage show strong negative correlation with churn, reinforcing the value of digital stickiness.

🧹 Data Cleaning & Preprocessing Summary
Step	Operation	Columns Affected	Rationale
Missing Values	Median Imputation	MonthlySpend, NumTransactions	Robust against skewed banking data
Categorical Encoding	One-Hot Encoding	AccountType, ServiceTier	Preserve non-ordinal semantics
Outlier Treatment	IQR Capping	MonthlySpend, NumTransactions	Prevent model dominance by extreme values
Feature Scaling	StandardScaler	All numeric features	Required for distance-based models
Target Encoding	Binary Mapping	Churn	Model compatibility
Train-Test Split	Stratified 80/20	All features	Maintain churn distribution

Data Leakage Control:
All preprocessing steps were fit only on the training set and applied to the test set via a scikit-learn Pipeline, ensuring zero leakage.

🧠 Feature Groups

Demographic: Age, Tenure, Region

Behavioral: NumTransactions, MonthlySpend

Service Interaction: SupportCalls, Complaints

Digital Engagement: LoginFrequency, OnlineUsageScore

This grouping supports both model interpretability and business storytelling.

🧠 Model Readiness

Fully numerical, standardized dataset

Compatible with:

Logistic Regression (baseline, explainable)

Random Forest (non-linear interactions)

XGBoost (performance-focused)

Class imbalance addressed via:

Class weights (primary)

SMOTE (evaluated, not default)

Designed for SHAP-based explainability, essential in regulated banking environments

📊 Evaluation Strategy (Banking-Aligned)

Metrics are selected based on business cost, not vanity accuracy:

Primary: Recall (minimise false negatives → missed churners)

Secondary: Precision (avoid unnecessary retention spend)

Overall: F1-score, ROC-AUC

In retail banking, failing to identify a churner has a higher financial impact than contacting a non-churner.

🚀 Next Steps

Feature importance analysis (SHAP)

Model comparison and selection

Threshold optimisation based on retention cost

Optional deployment pipeline using FastAPI + MLflow

📎 References

Lloyds Banking Group retail banking context

Industry churn modelling best practices

Python stack: Pandas, Scikit-learn, Matplotlib, Seaborn
