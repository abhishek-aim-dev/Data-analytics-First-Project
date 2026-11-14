📊 Customer Shopping Behavior Analysis

An end-to-end data analytics and business intelligence project exploring consumer purchasing patterns, demographic segments, product performance, and subscription dynamics across 3,900 retail transactions.

📌 Project Overview

This project simulates a real-world enterprise analytics workflow. The objective is to extract raw transactional customer data, engineer features, store cleaned records in a relational database, and perform advanced SQL querying to answer critical commercial questions—concluding with an interactive executive dashboard in Power BI.

🛠️ Tech Stack
Development Environment: Visual Studio Code (VS Code) (modular Python scripts & SQL workspace)
Data Engineering & ETL: Python 3 (Pandas, NumPy, SQLAlchemy, PyMySQL)
Data Warehouse / Storage: MySQL Server (customer_analysis database)
Business Intelligence & Reporting: Power BI Desktop
🏗️ System Architecture & Workflow
Environment Setup (VS Code): Replaced monolithic exploratory notebooks with modular Python scripts (etl.py) and standard .sql script files for clean version control and terminal execution.
ETL & Data Hygiene (Python):
Audited 3,900 rows and 18 attributes.
Handled missing values (37 null values in Review Rating) by imputing category-specific median ratings.
Standardized column headers to lowercase snake_case.
Engineered demographic quartile tiers (age_group: Young Adult, Adult, Middle-Aged, Senior) via pd.qcut.
Mapped textual frequencies to exact numeric days (purchase_frequency_days).
Audited collinearity: confirmed discount_applied and promo_code_used were 100% redundant; dropped redundant column.
Database Ingestion (MySQL): Connected via SQLAlchemy and loaded cleaned records directly into customer_analysis.customer.
SQL Analytics (MySQL): Formulated 10 targeted analytical queries utilizing Common Table Expressions (CTEs), Window Functions (ROW_NUMBER() OVER PARTITION BY), and conditional aggregation.
Reporting (Power BI): Developed an interactive dashboard with multi-dimensional slicers (Gender, Subscription, Category, Shipping Speed).
📁 Repository Structure
text
├── data/
│   └── customer_shopping_behavior.csv    # Raw transactional dataset
├── scripts/
│   └── etl.py                            # Data cleaning & MySQL ingestion script
├── sql/
│   └── queries.sql                       # 10 core business analysis SQL queries
├── reports/
│   └── Customer_Behavior_Dashboard.pbix  # Power BI interactive report
│   └── Presentation.pptx                 # Executive slide deck (13 slides)
└── README.md                             # Project documentation
🔍 Key Business Questions & SQL Insights
1. Revenue by Gender
SQL Technique: SUM() aggregate with GROUP BY
Finding: Male customers generated $157,890 (67.7%) vs $75,191 (32.3%) for female shoppers. Average order value (AOV) is identical across genders (~$59.70), proving that transaction frequency (2,652 vs 1,248 orders) drives the gap.
2. High-Spending Discount Users (Margin Leakage)
SQL Technique: Subquery filtering above average purchase amount
Finding: 839 customers spent above the average basket size ($59.76) while still receiving discounts, highlighting unnecessary margin concession on high-intent buyers.
3. Top 5 Highest-Rated Products
SQL Technique: AVG(), ROUND(), ORDER BY DESC LIMIT 5
Finding: Gloves (3.86), Sandals (3.84), Boots (3.82), Hats (3.80), and Skirts (3.78) earned top customer satisfaction scores.
4. Shipping Speed vs. Basket Size
SQL Technique: HAVING clause filtering
Finding: Express Shipping orders average $60.48 compared to $58.46 for Standard (+$2.02 difference), demonstrating higher order intent from express shoppers.
5. Subscription Financial Comparison
SQL Technique: Multi-metric aggregation across subscription status
Finding: Subscribers spend virtually the same per transaction ($59.49) as non-subscribers ($59.87). Subscriptions drive retention and lifetime frequency rather than larger cart sizes.
6. Discount-Dependent Products
SQL Technique: Conditional aggregation with CASE WHEN
Finding: Top apparel items are heavily discount-reliant: Hats (50.0%), Sneakers (49.7%), Coats (49.1%), Sweaters (48.2%), and Pants (47.4%).
7. Customer Loyalty Segmentation
SQL Technique: Common Table Expression (CTE) with CASE logic
Finding:
Loyal (>10 purchases): 3,116 customers (79.9%)
Returning (2–10 purchases): 701 customers (18.0%)
New (1 purchase): 83 customers (2.1%)
8. Category Volume Leaders
SQL Technique: Window Function ROW_NUMBER() OVER (PARTITION BY category ORDER BY count DESC)
Finding:
Clothing: Blouse (171), Pants (171), Shirt (169)
Accessories: Jewelry (171), Sunglasses (161), Belt (161)
Footwear: Sandals (160), Shoes (150), Sneakers (145)
Outerwear: Jacket (163), Coat (161)
9. Repeat Buyers & Subscription Conversion Gap
SQL Technique: Segmenting customers with previous_purchases > 5
Finding: 2,518 frequent repeat buyers are NOT subscribed (compared to 958 who are). This represents an immediate, high-propensity conversion audience.
10. Revenue Contribution by Age Bracket
SQL Technique: Aggregation over binned demographic tiers
Finding: Spending is remarkably balanced across all generations: Young Adults lead ($62,143), followed by Middle-Aged ($59,197), Adults ($55,978), and Seniors ($55,763).
📈 Power BI Executive Dashboard

The interactive Power BI report provides:

Core KPI Cards: Total Customers (3.9K), Average Order Value ($59.76), Overall Review Rating (3.75).
Subscription Breakdown: 27% Subscribed vs. 73% Non-Subscribed.
Category Performance: Clothing generated the highest revenue ($104K+) and sales volume (1,737 units).
Multi-Filter Slicers: Instant drill-down by Subscription Status, Gender, Category, and Shipping Method.
💡 Strategic Business Recommendations
Accelerate Subscription Conversion: Launch an automated re-engagement campaign targeting the 2,518 unmonetized repeat buyers (>5 orders), offering exclusive perks like free express shipping rather than raw discounts.
Revise Discount Strategy: Eliminate universal item markdowns on high-demand staples (Sneakers, Pants, Hats). Protect margins from the 839 high-spenders by introducing a minimum spend threshold ($75+) to unlock promotions.
Elevate Hero Products: Promote Sandals (dual-winner: #1 in footwear volume and #2 in overall rating) in marketing campaigns and bundle accessories at checkout.
Bridge the Gender Gap: Launch targeted marketing campaigns and merchandise collections to capture female shoppers and expand top-of-funnel acquisition beyond the modest 83 new customers.
🚀 Setup & Execution Guide
Prerequisites
Python 3.10+
MySQL Server (Running locally or hosted)
Power BI Desktop
Visual Studio Code
1. Clone the Repository
bash
git clone https://github.com/your-username/customer-shopping-behavior-analysis.git
cd customer-shopping-behavior-analysis
2. Install Python Dependencies
bash
pip install pandas numpy sqlalchemy pymysql
3. Run ETL & Database Ingestion

Configure your MySQL database credentials in scripts/etl.py and run:

bash
python scripts/etl.py
4. Execute SQL Analysis

Open sql/queries.sql in VS Code or MySQL Workbench to execute the 10 business queries.

5. Open Dashboard

Launch Power BI Desktop and open reports/Customer_Behavior_Dashboard.pbix to view and interact with the visuals.

📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
