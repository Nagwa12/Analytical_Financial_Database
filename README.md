# Firefly III Financial Analytics
## Technical Architecture Document

**Version:** 1.0  
**Status:** Draft  
**Author:** Data Analytics Team

---

# 1. Executive Summary

## Purpose

The purpose of this analytical platform is to transform operational financial data from Firefly III into a scalable analytical database that supports:

- Financial Reporting
- KPI Monitoring
- Budget Analysis
- Cash Flow Forecasting
- Spending Behavior Prediction
- Anomaly Detection
- Executive Dashboards
- Data-Driven Decision Making

---

## Business Goals

### Financial Visibility

Provide a complete financial overview across:

- Accounts
- Categories
- Budgets
- Tags
- Time Periods

### Predictive Analytics

Enable prediction of:

- Future Balances
- Cash Shortages
- Spending Trends
- Financial Anomalies

### Self-Service Reporting

Allow users to create reports using:

- Power BI
- Metabase
- SQL

---

# 2. High-Level Architecture

```text
                    ┌─────────────────┐
                    │  Firefly III    │
                    │ Operational DB  │
                    └────────┬────────┘
                             │
                             ▼

                    ┌─────────────────┐
                    │   Staging Area  │
                    │ Raw Data Layer  │
                    └────────┬────────┘
                             │
                             ▼

                    ┌─────────────────┐
                    │ Transformation  │
                    │      DBT        │
                    └────────┬────────┘
                             │
                             ▼

          ┌─────────────────────────────────┐
          │      Analytical Database        │
          │                                 │
          │  Dimensions                     │
          │  Facts                          │
          │  Predictions                    │
          │  Feature Store                  │
          └──────────────┬──────────────────┘
                         │
           ┌─────────────┴──────────────┐
           ▼                            ▼

     Power BI                     Metabase
```

---

# 3. Data Warehouse Design

## Schema Type

Hybrid Star Schema

Contains:

- Fact Tables
- Dimension Tables
- Bridge Tables
- Prediction Tables

---

# 4. Fact Tables

Fact tables contain measurable business events.

---

## fact_transaction

### Grain

One row per financial transaction.

### Purpose

Central financial activity table.

### Key Metrics

- Amount
- Foreign Amount
- Exchange Rate

### Relationships

```text
fact_transaction
    │
    ├── dim_date
    ├── dim_account
    ├── dim_category
    ├── dim_budget
    └── dim_user
```

### Example Transactions

| Transaction |
|------------|
| Salary |
| Grocery |
| Rent |
| Utility Bill |

---

## fact_daily_balance

### Grain

One row per account per day.

### Purpose

Tracks account balance evolution.

### Formula

```sql
closing_balance =
opening_balance
+ total_credit
- total_debit
```

### Business Value

Supports:

- Balance Trends
- Cash Flow Analysis
- Liquidity Monitoring

---

# 5. Dimension Tables

## dim_date

### Purpose

Time-based analysis.

### Hierarchy

```text
Year
 └─ Quarter
     └─ Month
         └─ Week
             └─ Day
```

### Example KPIs

- Monthly Expenses
- Quarterly Savings
- Year-over-Year Growth

---

## dim_account

### Purpose

Account analysis.

### Examples

- Cash
- Bank
- Savings
- Credit Card

### Hierarchy

```text
Account Type
     └─ Account
```

---

## dim_category

### Purpose

Expense and income categorization.

### Example

```text
Housing
   ├─ Rent
   ├─ Mortgage

Transportation
   ├─ Fuel
   ├─ Maintenance
```

---

## dim_budget

Stores budget definitions.

Supports:

- Budget Tracking
- Variance Analysis

---

## dim_user

Stores:

- User Ownership
- User Reporting

---

## dim_currency

Supports:

- Multi-Currency Analysis
- Currency Conversion

---

## dim_tag

### Purpose

Advanced categorization.

### Hierarchical Structure

```text
Expenses
 └─ Housing
      └─ Rent

Expenses
 └─ Transportation
      └─ Fuel
```

---

# 6. Bridge Tables

## bridge_transaction_tag

### Purpose

Many-to-many relationship.

One transaction can have:

- Multiple Tags

One tag can belong to:

- Multiple Transactions

### Example

| Transaction | Tag |
|------------|------|
| Rent | Housing |
| Rent | Essential |

---

# 7. Prediction Layer

Prediction tables store machine learning outputs.

---

## pred_time_series_forecast

### Purpose

Forecast future spending.

### Example Outputs

- Next Month Expenses
- Future Balances
- Seasonal Trends

### Possible Models

```text
ARIMA
Prophet
XGBoost
LSTM
```

---

## pred_cash_flow_prediction

### Purpose

Predict future liquidity.

### Example

```text
Cash Shortfall Risk = 85%
```

Outputs:

- Predicted Cash Flow
- Shortfall Probability
- Future Balance Trend

---

## pred_behavioral_prediction

### Purpose

Predict user financial behavior.

Outputs:

- Predicted Monthly Spend
- Spending Trend
- Churn Probability

---

## pred_anomaly_prediction

### Purpose

Detect unusual transactions.

Outputs:

- Fraud Probability
- Alert Priority
- Anomaly Score

---

## pred_model_registry

Stores:

- Model Versions
- Accuracy Scores
- Deployment Status

---

## pred_feature_store

Stores reusable ML features.

Example:

```text
avg_daily_spend
avg_monthly_income
expense_growth_rate
transaction_frequency
```

---

# 8. Data Flow Architecture

```text
Firefly III
    │
    ▼

Raw Transactions
    │
    ▼

Staging Layer
    │
    ▼

Transformation Layer
(DBT Models)
    │
    ▼

Dimension Tables
    │
    ▼

Fact Tables
    │
    ▼

Prediction Models
    │
    ▼

Dashboards
```

---

# 9. ETL / ELT Architecture

## Extract

Source:

```text
Firefly III PostgreSQL
```

Frequency:

```text
Daily
```

---

## Load

Raw data is loaded into staging tables.

Examples:

```sql
stg_transactions
stg_accounts
stg_budgets
stg_categories
```

---

## Transform

DBT builds:

```text
dim_*
fact_*
pred_*
```

---

# 10. Data Quality Rules

## Transaction Validation

```sql
amount IS NOT NULL
```

```sql
transaction_date IS NOT NULL
```

```sql
account EXISTS
```

---

## Balance Validation

```sql
opening_balance
+ total_credit
- total_debit
=
closing_balance
```

---

## Currency Validation

```sql
exchange_rate > 0
```

---

# 11. Security Architecture

## Row-Level Security

Filter all user-facing reports by:

```sql
user_id
```

---

## Access Levels

| Role | Access |
|--------|----------|
| Admin | Full |
| Analyst | Read |
| Viewer | Dashboard Only |

---

# 12. Performance Architecture

## Partitioning Strategy

Recommended:

```sql
fact_transaction
PARTITION BY YEAR
```

---

## Indexes

### fact_transaction

```sql
transaction_date_key
account_key
category_key
user_key
```

### fact_daily_balance

```sql
date_key
account_key
```

---

# 13. Power BI Semantic Model

```text
dim_date
      │
      ▼
fact_transaction
      ▲
      │
dim_account

dim_category

dim_budget
```

## Core Measures

```DAX
Total Expense =
SUM(fact_transaction[amount])
```

```DAX
Total Income =
SUM(fact_transaction[income_amount])
```

```DAX
Net Cash Flow =
[Total Income] - [Total Expense]
```

---

# 14. Recommended Project Structure

```text
analytics_project/

├── staging/
│   ├── stg_accounts.sql
│   ├── stg_transactions.sql
│
├── dimensions/
│   ├── dim_account.sql
│   ├── dim_date.sql
│   ├── dim_category.sql
│
├── facts/
│   ├── fact_transaction.sql
│   ├── fact_daily_balance.sql
│
├── predictions/
│   ├── pred_cashflow.sql
│   ├── pred_anomaly.sql
│
├── tests/
│
├── docs/
│
└── dashboards/
```

---

# 15. Future Roadmap

## Phase 1

- Core Dimensions
- Core Facts
- Financial KPIs

## Phase 2

- Budget Analytics
- Cash Flow Analytics
- Forecasting

## Phase 3

- Behavioral Prediction
- Anomaly Detection

## Phase 4

- AI-Powered Recommendations
- Automated Financial Insights
- Scenario Simulations

---

# Architecture Principles

1. Single Source of Truth
2. Reusable Dimensions
3. Scalable Fact Tables
4. Machine Learning Ready
5. BI Tool Agnostic
6. Auditability
7. Data Quality First
8. Financial Accuracy

---

# Conclusion

This architecture provides a scalable foundation for a modern financial analytics platform capable of supporting:

- Operational Reporting
- Financial KPIs
- Budget Management
- Forecasting
- Machine Learning
- Executive Dashboards
- Strategic Decision-Making

while maintaining data quality, performance, scalability, and governance.
