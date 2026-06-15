# Financial KPI Handbook
## Firefly III Financial Analytics Platform

---

# KPI Classification

The KPIs are grouped into:

1. Liquidity KPIs
2. Cash Flow KPIs
3. Income KPIs
4. Expense KPIs
5. Budget KPIs
6. Savings KPIs
7. Forecasting KPIs
8. Risk KPIs
9. Behavioral KPIs
10. Financial Health KPIs

---

# 1. Liquidity KPIs

Liquidity KPIs measure the ability to cover future expenses and obligations.

---

## Current Cash Balance

### Purpose

Shows available money at a specific point in time.

### Formula

```sql
Current Cash Balance =
SUM(Account Balances)
```

### Example

| Account | Balance |
|----------|---------:|
| Cash | 10,000 |
| Savings | 50,000 |
| Bank | 40,000 |

```text
Current Cash Balance = 100,000
```

### Status

| Value | Status |
|---------|---------|
| > 6 months expenses | Excellent |
| 3-6 months expenses | Good |
| 1-3 months expenses | Warning |
| < 1 month expenses | Critical |

---

## Liquidity Ratio

### Formula

```sql
Liquidity Ratio =
Available Cash
/
Average Monthly Expenses
```

### Example

```text
Cash = 120,000

Monthly Expenses = 20,000

Liquidity Ratio = 6
```

### Interpretation

| Ratio | Status |
|---------|---------|
| > 12 | Excellent |
| 6-12 | Strong |
| 3-6 | Acceptable |
| < 3 | Risk |

---

# 2. Cash Flow KPIs

---

## Net Cash Flow

### Formula

```sql
Net Cash Flow =
Total Income
-
Total Expenses
```

### Example

```text
Income = 50,000

Expenses = 35,000

Net Cash Flow = 15,000
```

### Status

| Value | Status |
|---------|---------|
| Positive | Healthy |
| Zero | Neutral |
| Negative | Risk |

---

## Cash Flow Growth %

### Formula

```sql
Cash Flow Growth % =
(
Current Period Cash Flow
-
Previous Period Cash Flow
)
/
Previous Period Cash Flow
× 100
```

### Interpretation

Positive growth indicates financial improvement.

---

## Cash Runway

Measures how many months current cash can sustain spending.

### Formula

```sql
Cash Runway =
Current Balance
/
Average Monthly Expenses
```

### Example

```text
Balance = 180,000

Expenses = 30,000

Runway = 6 Months
```

---

# 3. Income KPIs

---

## Total Income

### Formula

```sql
Total Income =
SUM(Income Transactions)
```

---

## Income Growth %

### Formula

```sql
Income Growth =
(
Current Income
-
Previous Income
)
/
Previous Income
×100
```

### Status

| Growth | Status |
|---------|---------|
| > 20% | Excellent |
| 10%-20% | Good |
| 0%-10% | Stable |
| < 0% | Declining |

---

## Income Stability Index

Measures consistency of income.

### Formula

```sql
Income Stability =
1 -
(
Income Standard Deviation
/
Average Income
)
```

### Status

| Score | Meaning |
|---------|---------|
| > 0.9 | Very Stable |
| 0.8-0.9 | Stable |
| 0.6-0.8 | Variable |
| < 0.6 | Unstable |

---

# 4. Expense KPIs

---

## Total Expenses

### Formula

```sql
Total Expenses =
SUM(Expense Transactions)
```

---

## Expense Growth %

### Formula

```sql
Expense Growth =
(
Current Expenses
-
Previous Expenses
)
/
Previous Expenses
×100
```

### Status

| Growth | Meaning |
|---------|---------|
| < 5% | Healthy |
| 5%-15% | Monitor |
| >15% | Risk |

---

## Average Daily Spend

### Formula

```sql
Average Daily Spend =
Total Expenses
/
Number Of Days
```

---

## Average Transaction Value

### Formula

```sql
Average Transaction Value =
SUM(Transaction Amount)
/
COUNT(Transactions)
```

---

## Largest Expense Category %

### Formula

```sql
Largest Category %
=
Largest Category Spend
/
Total Expenses
×100
```

### Status

| Value | Status |
|---------|---------|
| <30% | Diversified |
| 30%-50% | Moderate |
| >50% | Concentrated |

---

# 5. Budget KPIs

---

## Budget Utilization %

### Formula

```sql
Budget Utilization =
Actual Spend
/
Budget Amount
×100
```

### Status

| Value | Status |
|---------|---------|
| <90% | Under Budget |
| 90%-100% | Healthy |
| >100% | Overspent |

---

## Budget Variance

### Formula

```sql
Budget Variance =
Budget Amount
-
Actual Spend
```

### Example

```text
Budget = 10,000

Spend = 8,000

Variance = 2,000
```

---

## Budget Accuracy

### Formula

```sql
Budget Accuracy =
1 -
ABS(
Budget Amount
-
Actual Spend
)
/
Budget Amount
```

---

# 6. Savings KPIs

---

## Savings Rate

### Formula

```sql
Savings Rate =
(
Income
-
Expenses
)
/
Income
×100
```

### Status

| Rate | Status |
|---------|---------|
| >30% | Excellent |
| 20%-30% | Strong |
| 10%-20% | Good |
| <10% | Weak |

---

## Monthly Savings Amount

### Formula

```sql
Monthly Savings =
Income
-
Expenses
```

---

## Emergency Fund Coverage

### Formula

```sql
Emergency Fund Coverage =
Emergency Fund
/
Average Monthly Expenses
```

### Status

| Months | Status |
|---------|---------|
| >12 | Excellent |
| 6-12 | Strong |
| 3-6 | Acceptable |
| <3 | Risk |

---

# 7. Forecasting KPIs

---

## Forecast Accuracy %

### Formula

```sql
Forecast Accuracy =
(
1 -
ABS(
Actual
-
Forecast
)
/
Actual
)
×100
```

### Status

| Accuracy | Status |
|---------|---------|
| >95% | Excellent |
| 90%-95% | Good |
| 80%-90% | Acceptable |
| <80% | Poor |

---

## Forecast Error %

### Formula

```sql
Forecast Error =
ABS(
Actual
-
Forecast
)
/
Actual
×100
```

---

## Predicted Cash Shortfall Risk

Generated by ML models.

### Range

```text
0% = No Risk

100% = Certain Shortfall
```

### Status

| Probability | Status |
|---------|---------|
| <20% | Safe |
| 20%-50% | Monitor |
| >50% | Risk |

---

# 8. Risk KPIs

---

## Anomaly Rate

### Formula

```sql
Anomaly Rate =
Anomaly Transactions
/
Total Transactions
×100
```

### Status

| Rate | Status |
|---------|---------|
| <1% | Excellent |
| 1%-3% | Monitor |
| >3% | Risk |

---

## Fraud Probability

Output from anomaly model.

### Range

```text
0.00 → 1.00
```

### Status

| Score | Status |
|---------|---------|
| <0.2 | Low |
| 0.2-0.5 | Medium |
| >0.5 | High |

---

# 9. Behavioral KPIs

---

## Spending Trend Score

### Formula

```sql
Spending Trend =
Current Month Spend
/
Average Historical Spend
```

### Status

| Score | Meaning |
|---------|---------|
| <1 | Improving |
| =1 | Stable |
| >1 | Increasing Spend |

---

## Category Volatility

Measures spending fluctuation.

### Formula

```sql
Category Volatility =
STDDEV(Category Spend)
/
AVG(Category Spend)
```

---

## Transaction Frequency

### Formula

```sql
Transaction Frequency =
Total Transactions
/
Number Of Days
```

---

# 10. Advanced Financial Health KPIs

---

## Expense-to-Income Ratio

### Formula

```sql
Expense-to-Income Ratio =
Expenses
/
Income
×100
```

### Status

| Ratio | Status |
|---------|---------|
| <60% | Excellent |
| 60%-80% | Healthy |
| 80%-100% | Warning |
| >100% | Critical |

---

## Financial Independence Ratio

### Formula

```sql
Financial Independence Ratio =
Passive Income
/
Total Expenses
×100
```

### Status

| Ratio | Status |
|---------|---------|
| >100% | Financially Independent |
| 50%-100% | Approaching |
| <50% | Dependent |

---

## Debt Coverage Ratio

### Formula

```sql
Debt Coverage Ratio =
Income
/
Debt Payments
```

### Status

| Ratio | Status |
|---------|---------|
| >3 | Excellent |
| 2-3 | Good |
| 1-2 | Risk |
| <1 | Critical |

---

## Net Worth

### Formula

```sql
Net Worth =
Total Assets
-
Total Liabilities
```

### Example

```text
Assets = 500,000

Liabilities = 150,000

Net Worth = 350,000
```

---

## Net Worth Growth %

### Formula

```sql
Net Worth Growth =
(
Current Net Worth
-
Previous Net Worth
)
/
Previous Net Worth
×100
```

---

# Executive KPI Scorecard

| KPI | Excellent | Good | Warning | Critical |
|------|------|------|------|------|
| Savings Rate | >30% | 20%-30% | 10%-20% | <10% |
| Budget Utilization | 90%-100% | 80%-90% | 100%-110% | >110% |
| Liquidity Ratio | >12 | 6-12 | 3-6 | <3 |
| Expense-to-Income | <60% | 60%-80% | 80%-100% | >100% |
| Forecast Accuracy | >95% | 90%-95% | 80%-90% | <80% |
| Anomaly Rate | <1% | 1%-2% | 2%-3% | >3% |
| Cash Runway | >12M | 6-12M | 3-6M | <3M |
| Debt Coverage | >3 | 2-3 | 1-2 | <1 |

---

# Recommended Dashboard Sections

1. Executive Summary
2. Cash Position
3. Income Analysis
4. Expense Analysis
5. Budget Performance
6. Savings Performance
7. Forecasting & Predictions
8. Financial Health Score
9. Risk & Anomalies
10. Trend Analysis
11. Tag-Based Analytics
12. Account Performance
13. Category Performance
14. Net Worth Tracking
15. Financial Recommendations
