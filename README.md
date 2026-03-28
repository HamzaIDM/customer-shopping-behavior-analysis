# Customer Shopping Behavior Analysis

A data analysis project examining consumer trends to inform business decisions.

---

## Overview

A retail company needed a clearer picture of how its customers shop — what they buy, when, and why — to improve sales and retention. This project works through a dataset of **3,900 customer records** across **18 variables**, from raw CSV to interactive dashboard.

**The core question:**
> *"What does the shopping data actually tell us, and what should the company do about it?"*

---

## Repository Structure

[... unchanged ...]

---

## Tools & Technologies

[... table unchanged ...]

---

## Data Preparation (Python)

**File:** `python/Customer_Shopping_Behavior_Analysis.ipynb`

Steps:

1. **Data Loading** — Imported dataset with `pandas`
2. **Initial Exploration** — `df.info()`, `df.describe()` to understand structure and distributions
3. **Missing Values** — 37 missing values in `Review Rating` (0.95%). Filled using the median rating per product category via `groupby().transform()`
4. **Column Standardization** — Renamed columns to `snake_case`; renamed `purchase_amount_(usd)` → `purchase_amount`
5. **Feature Engineering:**
   - `age_group` — Four quartile-based segments using `pd.qcut()`: `Young Adult`, `Adult`, `Middle-aged`, `Senior`
   - `purchase_frequency_days` — Converted text labels to numbers (e.g. `Weekly` → 7, `Monthly` → 30)
6. **Column Removal** — `promo_code_used` was 100% identical to `discount_applied`. Dropped to cut features from 18 → 17
7. **Database Export** — Loaded the cleaned dataframe into MySQL via `SQLAlchemy`

---

## SQL Analysis

**File:** `sql/analysis_queries.sql`

10 queries run against the MySQL `customer_behavior` database:

[... table unchanged ...]

---

## Key Findings

| # | Finding | Detail |
|---|---------|--------|
| 1 | **Gender Revenue Gap** | Male customers make up **67.7%** of total revenue |
| 2 | **Loyalty Dominance** | **79.9%** of customers have made more than 10 purchases |
| 3 | **Low Subscription Rate** | Only **27%** subscribed — yet they spend about the same per transaction as non-subscribers |
| 4 | **Discount–Spend Correlation** | **839 customers** used discounts and still spent above the $59.76 average |
| 5 | **Seasonal Peaks** | **Fall** brings the highest revenue at $60,018 |
| 6 | **Young Adults Lead** | The 18–31 age group contributes the most: **$62,143** |
| 7 | **Clothing Dominates** | Clothing is **44.7%** of total revenue |

---

## Dashboard (Power BI)

**File:** `powerbi/customer_behavior_dashboard.pbix`

**KPIs:**
- **3,900** Customers
- **$59.76** Average Purchase Amount
- **3.75 / 5** Average Review Rating

**Visuals:**
- Subscription donut chart (27% Yes / 73% No)
- Revenue by Category (bar chart)
- Sales by Category (bar chart)
- Revenue & Sales by Age Group (horizontal bar charts)
- Slicers: Subscription Status, Gender, Category, Shipping Type

---

## Business Recommendations

1. **Grow the Subscriber Base** — 73% of customers aren't subscribed. Perks like early access or free shipping could convert a portion of them
2. **Target Female Customers** — Women bring in 32.3% of revenue. A dedicated campaign or product line could close that gap
3. **Reward High-Value Discount Users** — 839 customers use discounts *and* spend above average. Worth creating a loyalty tier for them
4. **Plan Around Fall** — Revenue peaks August–October. Inventory and campaigns should be ready before that window
5. **Bring in New Customers** — With 79.9% already loyal, referral programs and intro offers are the growth lever
6. **Expand Accessories & Footwear** — Accessories ($74,200) and Footwear ($36,093) have room to grow

---

## Dataset

[... table unchanged ...]

---

## Author

**Hamza Idrissi Meliani**
Mathematics and Systems Engineering Student
March 2026

---

## License

Academic and educational use only.
