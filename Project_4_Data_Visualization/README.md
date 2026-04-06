# 📊 Project 4 — Data Visualization & Storytelling

**Intern:** Suchitra S. Patne  
**Project:** Data Visualization — Optional Mastery Phase  
**Tool:** Python, Matplotlib, Seaborn, Jupyter Notebook, Excel

---

## 📌 Problem Statement

After cleaning, analyzing, and querying the dataset in Projects 1–3, this project focuses on **communicating findings visually** — transforming raw numbers into clear, decision-ready charts that a business executive can understand in 30 seconds.



---

## 📂 Dataset

- **File:** `Dataset for Data Analytics.xlsx`
- **Records:** 1,200 e-commerce orders
- **Columns Used:** Product, TotalPrice, UnitPrice, OrderStatus, ReferralSource, PaymentMethod, Date

---

## 🎨 Visualization Principles Applied

| Principle | What It Means |
|-----------|--------------|
| **Chart Selection Matrix** | Bar=compare, Line=trend, Scatter=relationship, Stacked=composition |
| **Action Titles** | Every chart title states the conclusion, not just the topic |
| **Color as Spotlight** | Grey for all bars, one bold accent color only on the key insight |
| **Data-Ink Ratio** | Removed all borders, 3D effects, heavy grids — every pixel serves the data |
| **Eradicate Chartjunk** | No decorative backgrounds, no unnecessary elements |
| **Direct Labeling** | Values labeled on bars directly — no legend required |
| **Axis Honesty** | All bar charts start y-axis at zero |

---

## 📊 9 Visualizations Created

| # | Chart Title (Action) | Chart Type |
|---|----------------------|------------|
| 1 | Chair Generates the Highest Revenue Despite Not Having Most Orders | Horizontal Bar |
| 2 | Monthly Revenue Shows Clear Seasonal Peaks — Q4 Drives Top Performance | Line Chart |
| 3 | ⚠ Cancellations Exceed Deliveries — Urgent Operational Risk | Horizontal Bar |
| 4 | Instagram Drives Highest Revenue — Double Down on Social Investment | Column Bar |
| 5 | Credit Card Customers Spend More Per Order — Prioritize for Upsells | Column Bar |
| 6 | Higher Unit Price Strongly Predicts Larger Orders (r = 0.72) | Scatter Plot |
| 7 | Most Orders Below ₹1,000 — Large Orders Inflate the Average | Histogram |
| 8 | Printer Has Most Orders But Chair Earns More Revenue — Volume ≠ Value | Column Bar |
| 9 | Chair + Laptop Together Account for >40% of Total Revenue | Stacked Bar |

---

## 🔑 Key Business Insights

1. ⚠️ **Cancellations (250) exceed Deliveries (231)** — urgent operational issue
2. 📦 **Chair is the top revenue product** despite not having the most orders
3. 📱 **Instagram drives the highest revenue** across all referral channels
4. 📈 **Strong correlation (r = 0.72)** between unit price and total order value
5. 💳 **Credit Card users have the highest average order value**
6. 📉 **Median order value (₹824) is more accurate** than mean (₹1,054) due to skew
7. 🏆 **Chair + Laptop = 40%+ of total revenue** — protect these SKUs
8. 📊 **Volume ≠ Value** — Printer leads orders but Chair leads revenue

---

## 📤 Deliverables

| File | Description |
|------|-------------|
| `4_Data_Visualization.ipynb` | Jupyter Notebook with all 9 chart codes |
| `DataViz_Suchitra_P4.xlsx` | Excel report with charts, principles, and insights |

---

## ▶️ How to Run

```bash
pip install pandas openpyxl matplotlib seaborn numpy
```

```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

df = pd.read_excel('Dataset_for_Data_Analytics.xlsx')
df['CouponCode'] = df['CouponCode'].fillna('NO_COUPON')
df['Date'] = pd.to_datetime(df['Date'])

# Global clean style — no chartjunk
plt.rcParams.update({
    'axes.spines.top': False,
    'axes.spines.right': False,
    'axes.spines.left': False,
    'axes.grid': True,
    'grid.color': '#f0f0f0',
    'axes.axisbelow': True,
    'figure.facecolor': 'white',
})

GREY = '#CCCCCC'
BLUE = '#1A6FBF'

# Example — Chart 1: Revenue by Product with color spotlight
prod_rev = df.groupby('Product')['TotalPrice'].sum().sort_values()
colors = [BLUE if p == 'Chair' else GREY for p in prod_rev.index]
plt.barh(prod_rev.index, prod_rev.values, color=colors)
plt.title('Chair Generates the Highest Revenue Despite Not Having Most Orders',
          fontweight='bold')
plt.show()
```

Open `4_Data_Visualization.ipynb` in Jupyter Notebook to run all 9 charts.
