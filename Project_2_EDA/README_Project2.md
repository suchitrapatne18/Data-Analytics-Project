# 📊 Project 2 — Exploratory Data Analysis (EDA)

## 📌 Overview
Numbers don't speak for themselves — analysts do. This project interrogates the cleaned sales dataset to uncover hidden patterns, trends, outliers, and relationships using descriptive statistics and data visualisation.

---

## 🎯 Goal
Analyze the dataset to understand patterns, trends, and distributions — transforming raw numbers into actionable business intelligence.

---

## 🔍 4-Phase EDA Framework

### Phase 1 — Descriptive Statistics
- Computed mean, median, std dev, min, max for all numeric columns
- **Key finding:** TotalPrice is right-skewed (Mean ₹1,054 > Median ₹824)

### Phase 2 — Trend Analysis
- Monthly revenue trend across 2023–2025
- Revenue and order count breakdown by Product and Referral Source

### Phase 3 — Outlier Detection
- **IQR Method:** `Outlier < Q1 − 1.5×IQR` or `Outlier > Q3 + 1.5×IQR`
- **Z-Score Method:** Flag if `|Z| > 3`
- Found **8 TotalPrice outliers** — classified as VIP/bulk orders, not errors

### Phase 4 — Correlation Analysis
- Pearson correlation matrix across all numeric columns
- **Key finding:** UnitPrice vs TotalPrice → r = 0.72 (strong positive)

---

## 💡 Key Business Insights

| # | Finding | Insight |
|---|---------|---------|
| 1 | Right-skewed revenue | Use Median (₹824) not Mean (₹1,054) as KPI |
| 2 | Chair = top revenue product | Bundle Chair + Desk for upsell |
| 3 | Cancellations > Deliveries | 250 cancelled vs 231 delivered — urgent alert |
| 4 | Instagram #1 channel | 259 orders, ₹275K revenue |
| 5 | Strong price correlation | r = 0.72, premium products drive revenue |
| 6 | 8 high-value outliers | Potential VIP customers — create loyalty tier |

---

## 📁 Files

| File | Description |
|------|-------------|
| `2_EDA_Analysis.ipynb` | Jupyter Notebook with all EDA code |
| `EDA_Report_Suchitra_P2.xlsx` | Full EDA report with charts (5 sheets) |

---

## 🛠️ How to Run

```python
# Install dependencies
pip install pandas openpyxl matplotlib seaborn scipy

# Run in Jupyter Notebook
# Open 2_EDA_Analysis.ipynb and run all cells
```

---

## 🔧 Key Python Functions Used

| Function | Purpose |
|----------|---------|
| `df.describe()` | Full statistical summary |
| `df.groupby().sum()` | Revenue by group |
| `df.quantile()` | IQR outlier detection |
| `scipy.stats.zscore()` | Z-score outlier detection |
| `df.corr()` | Pearson correlation matrix |
| `plt.hist()` | Distribution histogram |
| `sns.heatmap()` | Correlation heatmap |
