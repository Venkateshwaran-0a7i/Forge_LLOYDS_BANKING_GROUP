# Customer Churn Analysis Report

## 1. Data Gathering and Rationale
The dataset was integrated from five distinct sheets in `Customer_Churn_Data_Large.xlsx`. The selection criteria focused on features that traditionally impact customer churn in banking:

- **Customer Demographics**: Age, Gender, and Income Level help segment the risk profile.
- **Transaction History**: Total Spend and Number of Transactions (aggregated) represent the customer's financial engagement.
- **Customer Service**: The frequency of support interactions (aggregated) often correlates with dissatisfaction.
- **Online Activity**: Login frequency indicates how much the customer relies on our digital platforms.
- **Churn Status**: The target indicator for future model building.

## 2. Exploratory Data Analysis (EDA)

### Statistical Summary
The aggregated dataset contains 1,000 unique customers.
- **Churn Rate**: Approximately 20.4%.
- **Average Age**: 43.3 years.
- **Average Spend**: $1,267.07.
- **Avg Support Calls**: ~1 per customer.

### Visualizations
Key insights from EDA:
- **Age**: Younger customers appeared to have a slightly higher variance in churn, but it is distributed broadly.
- **Transactions & Spend**: Churned customers often show lower transaction counts and total spend compared to loyal ones.
- **Support Calls**: A higher number of support interactions is a strong indicator of churn risk.

*(Visualizations are available in the project directory as churn_distribution.png, age_dist_churn.png, and spend_vs_trans.png)*

## 3. Data Cleaning and Preprocessing

### Cleaning Steps:
- **Missing Values**:
  - `ServiceUsage` was filled with 'Unknown'.
  - `LoginFrequency` was imputed with the median.
- **Outliers**:
  - Numerical features (Age, Spend, Transactions, Support Calls) were capped at the 99th percentile to prevent extreme values from skewing the model.

### Preprocessing Steps:
- **Categorical Encoding**: One-hot encoding was applied to `Gender`, `MaritalStatus`, `IncomeLevel`, and `ServiceUsage`.
- **Standardization**: Numerical features were scaled using `StandardScaler` to ensure a mean of 0 and standard deviation of 1.
- **Column Dropping**: Non-predictive ID columns and messy date strings were removed for the final model-ready dataset.

## 4. Final Dataset
The cleaned dataset `cleaned_customer_churn_data.csv` is now ready for machine learning model development.
- **Rows**: 1,000
- **Columns**: 17 (after encoding and scaling)
