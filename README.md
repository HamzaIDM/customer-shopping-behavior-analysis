# 🛍️ Customer Shopping Behavior Analysis

> *End-to-end data analysis project uncovering consumer trends to drive smarter business decisions.*

---

## 📌 Overview

A leading retail company wanted to better understand its customers' shopping behavior in order to improve sales, customer satisfaction, and long-term loyalty. This project analyzes a dataset of **3,900 customer records** across **18 variables** using a full data pipeline — from raw data cleaning to interactive visualization.

**Central Business Question:**
> *"How can the company leverage consumer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategies?"*

---

## 🗂️ Repository Structure

```
customer-shopping-behavior-analysis/
│
│── customer_shopping_behavior.csv       # Raw dataset
│
│── Customer_Shopping_Behavior_Analysis.ipynb  # Data preparation notebook
│
│── analysis_queries.sql                # All 10 SQL analytical queries
│
│── customer_behavior_dashboard.pbix    # Power BI dashboard file
│
│── consumer_behavior_report.pdf        # Full project report
│
│── Customer_Shopping_Behavior_Analysis.pdf  # Final presentation
│
└── README.md
```

---

## 🛠️ Tools & Technologies

| Phase | Tool | Purpose |
|-------|------|---------|
| Data Preparation | Python (Pandas) | Cleaning, imputation, feature engineering |
| Database & Analysis | MySQL + SQLAlchemy | Structured storage and 10 analytical queries |
| Visualization | Microsoft Power BI | Interactive dashboard with slicers and KPIs |
| Reporting | PDF | Professional formatted project report |

---

## 🔄 Data Preparation (Python)

**File:** `python/Customer_Shopping_Behavior_Analysis.ipynb`

Steps performed:

1. **Data Loading** — Imported dataset using `pandas`
2. **Initial Exploration** — `df.info()`, `df.describe()` for structure and statistics
3. **Missing Value Treatment** — 37 missing values found in `Review Rating` (0.95%). Imputed using the **median rating per product category** via `groupby().transform()`
4. **Column Standardization** — Renamed all columns to `snake_case`; renamed `purchase_amount_(usd)` → `purchase_amount`
5. **Feature Engineering:**
   - `age_group` — Created 4 quartile-based segments using `pd.qcut()`: `Young Adult`, `Adult`, `Middle-aged`, `Senior`
   - `purchase_frequency_days` — Mapped text labels to numeric days (e.g. `Weekly` → 7, `Monthly` → 30)
6. **Column Removal** — `promo_code_used` was **100% identical** to `discount_applied` (confirmed by Boolean check → `np.True_`). Dropped to reduce features from 18 → 17
7. **Database Export** — Loaded cleaned DataFrame into MySQL via `SQLAlchemy`

---

## 🗄️ SQL Analysis

**File:** `sql/analysis_queries.sql`

10 analytical queries were written and executed on the MySQL `customer_behavior` database:

| # | Question |
|---|----------|
| Q1 | Total revenue by gender |
| Q2 | Customers who used a discount but spent above average |
| Q3 | Top 5 products by average review rating |
| Q4 | Average purchase amount by shipping type (Standard vs Express) |
| Q5 | Subscriber vs non-subscriber spend comparison |
| Q6 | Top 5 products with highest discount usage rate |
| Q7 | Customer segmentation: New / Returning / Loyal |
| Q8 | Top 3 most purchased products per category (Window Function) |
| Q9 | Repeat buyers vs subscription likelihood |
| Q10 | Revenue contribution by age group |

---

## 📊 Key Findings

| # | Finding | Detail |
|---|---------|--------|
| 1 | **Gender Revenue Gap** | Male customers account for **67.7%** of total revenue |
| 2 | **Loyalty Dominance** | **79.9%** of customers are Loyal (>10 purchases) |
| 3 | **Low Subscription Rate** | Only **27%** subscribed, yet subscribers show similar spend per transaction |
| 4 | **Discount–Spend Correlation** | **839 customers** used discounts and still spent above the $59.76 average |
| 5 | **Seasonal Peaks** | **Fall** is the top revenue season ($60,018) |
| 6 | **Young Adults Lead** | Young Adults (18–31) contribute the most revenue: **$62,143** |
| 7 | **Clothing Dominates** | Clothing accounts for **44.7%** of total revenue |

---

## 📈 Dashboard (Power BI)

**File:** `powerbi/customer_behavior_dashboard.pbix`

**KPIs displayed:**
- 🧑‍🤝‍🧑 **3,900** Customers
- 💰 **$59.76** Average Purchase Amount
- ⭐ **3.75 / 5** Average Review Rating

**Visuals included:**
- Subscription donut chart (27% Yes / 73% No)
- Revenue by Category (bar chart)
- Sales by Category (bar chart)
- Revenue & Sales by Age Group (horizontal bar charts)
- Interactive slicers: Subscription Status, Gender, Category, Shipping Type

---

## 💡 Business Recommendations

1. **Grow the Subscriber Base** — Introduce tiered subscription plans targeting the 73% non-subscribers with perks like early access and free shipping
2. **Target Female Customers** — Dedicated female-focused collections could unlock an under-served segment (currently 32.3% of revenue)
3. **Leverage High-Value Discount Users** — Create a premium loyalty tier for the 839 deal-conscious high-spenders
4. **Capitalize on Fall Seasonality** — Pre-plan campaigns and inventory build-up for August–October
5. **Invest in New Customer Acquisition** — With 79.9% loyal customers, referral programs and introductory offers are needed
6. **Expand Accessories & Footwear** — Accessories ($74,200) and Footwear ($36,093) show strong growth potential

---

## 📦 Dataset

| Property | Value |
|----------|-------|
| File | `customer_shopping_behavior.csv` |
| Records | 3,900 |
| Columns | 18 (original) → 17 (after cleaning) |
| Missing values | 37 (in `Review Rating` only) |
| Source | Retail customer transaction records |

---

## 👤 Author

**Hamza Idrissi Meliani**
Mathematics and Systems Engineering Student
📅 March 2026

---

## 📄 License

This project is for academic and educational purposes.
