# 📉 Customer Churn Analysis – Power BI Project with ETL and ML

This project presents an end-to-end Customer Churn Analysis pipeline that integrates SQL-based ETL, Power BI visualization, and a machine learning model for predicting potential churners.

---

## 🚀 Project Goals

- Build a full ETL process in SQL to clean, transform, and load customer data.
- Analyze customer churn using Power BI dashboards across:
  - Demographic
  - Geographic
  - Payment & Account Info
  - Services Used
- Study churner profiles to identify marketing opportunities.
- Predict potential future churners using a Random Forest classifier in Python.

---

## 🛠 Tools & Technologies

- **SQL Server**: ETL & data modeling
- **Power BI**: Dashboard design & DAX measures
- **Power Query**: Data transformation
- **Python (Jupyter Notebook)**: Churn prediction model (Random Forest)
- **Pandas, scikit-learn, seaborn**: For machine learning and visualization

---

## 🔄 ETL Process (SQL)

### ✅ Data Exploration
- Count distributions (e.g., Gender, Contract, State)
- Revenue analysis by `Customer_Status`
- Missing values audit using `CASE` + `SUM`

 ### ✅ Data Cleaning
- Used `ISNULL()` to replace null values
- Inserted clean records into `prod_Churn`

```sql
SELECT ...
INTO [dbo].[prod_Churn]
FROM [dbo].[stg_Churn]
WHERE ...
# powerbi-churn-analysis
Customer churn analysis using Power BI with full ETL pipeline

CREATE VIEW vw_ChurnData AS 
SELECT * FROM prod_Churn WHERE Customer_Status IN ('Churned', 'Stayed');

CREATE VIEW vw_JoinData AS 
SELECT * FROM prod_Churn WHERE Customer_Status = 'Joined';


Total Customers = COUNT(prod_Churn[Customer_ID])
New Joiners = CALCULATE(COUNT(prod_Churn[Customer_ID]), prod_Churn[Customer_Status] = "Joined")
Total Churn = SUM(prod_Churn[Churn Status])
Churn Rate = [Total Churn] / [Total Customers]


### Project Structure
powerbi-churn-analysis/
│
├── SQL/
│   ├── ETL_Queries.sql
│   └── Views.sql
│
├── PowerBI/
│   ├── CustomerChurn.pbix
│   └── Screenshots/
│        └── churn_summary.png
│
├── Python_Model/
│   ├── Churn_Prediction.ipynb
│   └── Predictions.csv
│
├── Data/
│   └── SampleData.xlsx
│
└── README.md

