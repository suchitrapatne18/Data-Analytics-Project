# 🧹 Project 1 — Data Cleaning & Preparation

## 📌 Overview
Raw data is never perfect. This project takes a messy e-commerce dataset and transforms it into a clean, analysis-ready file using Python and pandas — following a professional 3-phase cleaning framework.

---

## 🎯 Goal
Clean the raw dataset by handling missing values, removing duplicates, and standardising formats.

---

## 📋 3-Phase Cleaning Process

### Phase 1 — Strategic Imputation (Missing Values)
- Identified **309 null values** in the `CouponCode` column
- Filled using `fillna('NO_COUPON')` — preserving all 309 rows instead of deleting them
- No other columns had missing values

### Phase 2 — Integrity Audit (Duplicates)
- Checked for duplicate rows → **0 found**
- Checked for duplicate OrderIDs → **0 found**
- All 1,200 OrderIDs confirmed unique

### Phase 3 — Format Standardisation
- Converted all dates to **ISO 8601 format** (YYYY-MM-DD)
- Rounded `UnitPrice` and `TotalPrice` to **2 decimal places**
- Stripped whitespace from all text columns using `.str.strip()`

---

## ✅ Verification Gate Results

| Check | Target | Result |
|-------|--------|--------|
| Duplicate OrderID Error Rate | 0% | ✅ 0% |
| Date Format Error Rate | 0% | ✅ 0% |
| Missing Value Coverage | 100% | ✅ 100% |

---

## 📁 Files

| File | Description |
|------|-------------|
| `1_Data_Cleaning.ipynb` | Jupyter Notebook with all cleaning code |
| `Dataset for Data Analytics.xlsx` | Original raw dataset |
| `Cleaned_Dataset.xlsx` | Final cleaned output |
| `ChangeLog_P1.pdf` | Documentation of every change made |

---

## 🛠️ How to Run

```python
# Install dependencies
pip install pandas openpyxl

# Run in Jupyter Notebook
# Open 1_Data_Cleaning.ipynb and run all cells
```

---

## 🔧 Key Python Functions Used

| Function | Purpose |
|----------|---------|
| `df.isnull().sum()` | Count missing values |
| `df.fillna('NO_COUPON')` | Fill null values |
| `df.drop_duplicates()` | Remove duplicate rows |
| `pd.to_datetime().dt.strftime()` | Standardise date format |
| `df.round(2)` | Round to 2 decimal places |
| `df.str.strip()` | Remove whitespace |
