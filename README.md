# Customer Shopping Behavior Analysis

An end-to-end data analytics project covering **data cleaning (Python/Pandas)**, **database storage (MySQL)**, **exploratory & business SQL analysis**, and **dashboarding (Power BI)** on a retail customer shopping dataset of ~3,900 transactions.

##  Tools & Tech Stack
- **Python (Pandas)** – data cleaning & feature engineering (Jupyter Notebook)
- **MySQL** – relational storage, queried via SQLAlchemy from Python
- **SQL** – business analysis queries (aggregations, CASE WHEN, window functions)
- **Power BI** – interactive dashboard for visual reporting

##  Project Workflow
1. **Data Cleaning (`notebook/customer_Analysis.ipynb`)**
   - Loaded raw CSV (3,900 rows × 18 columns)
   - Filled missing `Review Rating` values using category-wise median
   - Standardized column names (lowercase, snake_case)
   - Engineered `Age_Group` (Young Adult / Adult / Middle-aged / Senior) using quartile-based binning
   - Engineered `purchase_frequency_days` by mapping purchase frequency labels to numeric day values
   - Verified and dropped the redundant `promo_code_used` column (found to be identical to `discount_applied`)
   - Loaded the cleaned dataset into MySQL using SQLAlchemy

2. **SQL Analysis (`sql/Data_Analyst_Projects.sql`)**
   - Revenue breakdowns by gender and age group
   - Discount vs. non-discount spending behavior
   - Top-rated and most-discounted products
   - Standard vs. express shipping comparison
   - Subscriber vs. non-subscriber spend comparison
   - Customer segmentation (New / Returning / Loyal) using CASE WHEN
   - Top 3 products per category using window functions (ROW_NUMBER + PARTITION BY)
   - Repeat buyer subscription behavior

3. **Dashboard (`dashboard/customer_Analysis.pbix`)**
   - Interactive Power BI report built on the same cleaned dataset for visual exploration

##  Key Insights
- **Revenue split by gender:** Male customers generated ~$157.9K vs. ~$75.2K from female customers.
- **Discount-driven high spenders:** 839 customers used a discount yet still spent above the average purchase amount (~$59.76).
- **Top-rated products:** Gloves, Sandals, Boots, Hat, and Handbag lead in average review rating (all ~3.8+).
- **Shipping type impact:** Express shipping customers spend slightly more on average ($60.48) than standard shipping customers ($58.46).
- **Subscription doesn't necessarily mean higher spend:** Non-subscribers actually spend marginally more per transaction ($59.87 vs $59.49), though subscribers still contribute meaningfully to total revenue.
- **Most-discounted products:** Hats (50%), Sneakers (49.7%), and Coats (49.1%) have the highest share of discounted purchases.
- **Customer segments:** The vast majority of customers (3,563) fall into the "Loyal" segment (5+ previous purchases), with far fewer New (83) or Returning (254) customers.
- **Repeat buyers & subscriptions:** Among customers with more than 5 previous purchases, most (2,518) are *not* subscribed — suggesting subscription status alone doesn't drive repeat purchase behavior.
- **Age group revenue:** Young Adults contribute the highest revenue (~$62.1K), fairly evenly spread across all age groups.

##  Repository Structure
```
customer-shopping-behavior-analysis/
├── README.md
├── data/
│   └── customer_shopping_behavior.csv
├── notebook/
│   └── customer_Analysis.ipynb
├── sql/
│   └── Data_Analyst_Projects.sql
├── dashboard/
│   └── customer_Analysis.pbix
└── screenshots/
    └── dashboard_overview.png
```

##  How to Reproduce
1. Clone the repo
2. Run `notebook/customer_Analysis.ipynb` to clean the raw data and load it into a local MySQL instance (update the DB connection string with your own credentials)
3. Run the queries in `sql/Data_Analyst_Projects.sql` against the `customer_shopping` table
4. Open `dashboard/customer_Analysis.pbix` in Power BI Desktop to explore the interactive dashboard

##  Dataset
Customer shopping transactions dataset with attributes including demographics, purchase details, product category, discounts, shipping type, subscription status, and purchase history.
