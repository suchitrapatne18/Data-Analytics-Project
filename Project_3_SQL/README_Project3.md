# 🗄️ Project 3 — SQL Data Analysis

## 📌 Overview
Spreadsheets have limits. SQL doesn't. This project loads the cleaned sales dataset into a real SQLite database and extracts business intelligence using structured queries — the same way professional analysts do it every day.

---

## 🎯 Goal
Use SQL queries to extract insights from the dataset using SELECT, WHERE, GROUP BY, ORDER BY, and aggregation functions (COUNT, SUM, AVG).

---

## 🔑 SQL Concepts Covered

| Concept | Used In |
|---------|---------|
| `SELECT` + `FROM` | All queries |
| `WHERE` | Filtering by value, category, multiple conditions |
| `GROUP BY` | Grouping by Product, Status, Payment, Referral |
| `ORDER BY` | Sorting results ascending/descending |
| `LIMIT` | Top N results |
| `COUNT(*)` | Counting orders |
| `SUM()` | Total revenue |
| `AVG()` | Average order value |
| `MIN()` / `MAX()` | Smallest / largest order |
| `ROUND()` | Rounding decimals |
| `AS` | Column aliases |
| `AND` | Multiple WHERE filters |

---

## 📋 12 Queries Written

| Query | Description | Clauses |
|-------|-------------|---------|
| Q1 | View first 10 orders | SELECT, LIMIT |
| Q2 | High-value orders > ₹2,000 | WHERE, ORDER BY |
| Q3 | Delivered orders only | WHERE |
| Q4 | Total order count | COUNT |
| Q5 | Orders per product | COUNT, GROUP BY |
| Q6 | Revenue per product | SUM, GROUP BY |
| Q7 | Avg order by payment method | AVG, GROUP BY |
| Q8 | Orders by status | COUNT, AVG, GROUP BY |
| Q9 | Revenue by referral source | SUM, AVG, GROUP BY |
| Q10 | Top 5 highest value orders | ORDER BY, LIMIT |
| Q11 | Laptop + Instagram orders | WHERE with AND |
| Q12 | Full business summary | COUNT, SUM, AVG, MIN, MAX |

---

## 💡 Key SQL Findings

| Finding | Query | Result |
|---------|-------|--------|
| Total revenue | Q12 | ₹1,264,761.96 |
| Top product by revenue | Q6 | Chair (₹195,620) |
| Most orders | Q5 | Printer (181 orders) |
| Highest avg payment | Q7 | Credit Card (₹1,127.55) |
| Top referral channel | Q9 | Instagram (₹275,285) |
| Cancellations vs Deliveries | Q8 | 250 vs 231 — alert! |

---

## 📁 Files

| File | Description |
|------|-------------|
| `3_SQL_Analysis.ipynb` | Jupyter Notebook with all 12 SQL queries |
| `SQL_Analysis_Suchitra_P3.xlsx` | Query results exported to Excel |

---

## 🛠️ How to Run

```python
# sqlite3 is built into Python — no installation needed!
import sqlite3
import pandas as pd

# Load dataset
df = pd.read_excel('Dataset_for_Data_Analytics.xlsx')
df['CouponCode'] = df['CouponCode'].fillna('NO_COUPON')

# Create SQL database
conn = sqlite3.connect(':memory:')
df.to_sql('orders', conn, index=False, if_exists='replace')

# Run any query
result = pd.read_sql_query("""
    SELECT Product, COUNT(*) AS Orders
    FROM orders
    GROUP BY Product
    ORDER BY Orders DESC
""", conn)

print(result)
conn.close()
```

---

## ⚠️ Important: SQL Execution Order

SQL is **not** read top-to-bottom. The database executes in this order:

```
FROM → WHERE → GROUP BY → SELECT → ORDER BY
```

This means you **cannot use a SELECT alias in WHERE** — the alias doesn't exist yet when WHERE runs!
