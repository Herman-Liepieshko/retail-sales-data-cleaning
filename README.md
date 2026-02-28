# Retail Store Sales — Data Cleaning & EDA

> **12,575 transactions · 11 columns · 3 years of data · 6 data quality issues resolved**

A production-quality data cleaning and exploratory analysis pipeline applied to a deliberately
messy retail sales dataset. This project demonstrates the full workflow a data analyst follows
when receiving raw, uncleaned data: assess, plan, clean, validate, analyse, and deliver.

---

## Skills Demonstrated

| Skill | Details |
|-------|---------|
| **Data Cleaning** | Multi-step cleaning pipeline with documented rationale for each decision |
| **Missing Value Handling** | Column-specific strategies: imputation, fill with mode/constant, drop |
| **Outlier Detection** | IQR method with investigation before removal — context-aware decision |
| **Data Type Correction** | `datetime64` conversion, boolean casting, string normalisation |
| **Data Validation** | `assert`-based post-cleaning verification for all critical columns |
| **Feature Engineering** | Temporal features, price tiers, revenue-per-unit derived metrics |
| **EDA & Visualisation** | 6 business-focused charts with written insights |
| **pandas** | GroupBy, merge, fillna, astype, dt accessor, vectorised operations |
| **numpy** | Array ops, IQR calculation, correlation |
| **matplotlib / seaborn** | Consistent style, annotated charts, subplots |

---

## Project Structure

```
retail-sales-data-cleaning/
├── data/
│   ├── raw/
│   │   └── retail_store_sales.csv      # Original dirty dataset
│   └── cleaned/
│       └── retail_store_sales_cleaned.csv  # Output of cleaning pipeline
├── notebooks/
│   └── data_cleaning_eda.ipynb         # Main analysis notebook
├── requirements.txt
└── README.md
```

---

## Key Findings

1. **Balanced revenue across all 8 categories** — no single product category drives more than
   ~13% of total revenue, indicating a diversified and resilient product portfolio.

2. **Omnichannel parity** — Online and In-store channels split revenue almost 50/50 across
   every category, reflecting a mature dual-channel retail strategy.

3. **Price-insensitive purchasing behaviour** — low correlation between unit price and quantity
   suggests customers buy based on need, not price, making volume-based discounting less effective.

4. **Evenly distributed payment methods** — Cash, Digital Wallet, and Credit Card each account
   for roughly one-third of revenue, indicating broad payment adoption across the customer base.

---

## Data Quality Issues Found & Resolved

| Issue | Count | Resolution |
|-------|-------|-----------|
| `Transaction Date` stored as string | 12,575 rows | `pd.to_datetime()` conversion |
| `Discount Applied` missing + wrong dtype | 4,199 nulls | Filled `False`; cast to `bool` |
| `Item` missing values | 1,213 nulls | Filled `"Unknown"` — rows retained |
| `Price Per Unit` partially missing | 609 nulls | Back-calculated from `Total Spent / Quantity` |
| `Quantity` + `Total Spent` both missing | 604 rows | Dropped — unrecoverable transaction records |
| `Total Spent` IQR outliers | 60 rows | Investigated and **retained** — all mathematically valid |

---

## How to Run

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/retail-sales-data-cleaning.git
cd retail-sales-data-cleaning

# 2. Install dependencies
pip install -r requirements.txt

# 3. Launch Jupyter
jupyter notebook notebooks/data_cleaning_eda.ipynb
```

Run all cells top-to-bottom. The cleaned dataset will be written to `data/cleaned/` automatically.

---

## Dataset

**Retail Store Sales (Dirty)** — available on Kaggle:
https://www.kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning

The dataset is intentionally dirty and designed for data cleaning practice, containing
missing values, incorrect data types, and inconsistent entries across multiple columns.
