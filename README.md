# 📊 Customer Shopping Behavior Analysis

### An End-to-End Data Analytics & Business Intelligence Project

An end-to-end data analytics project exploring customer purchasing patterns, demographic segments, product performance, discount strategies, and subscription behavior across **3,900 retail transactions**.

The project demonstrates a complete analytics workflow, from raw data extraction and transformation using Python to relational database management with MySQL, business analysis using advanced SQL, and interactive dashboard development in Power BI.

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Business Objectives](#-business-objectives)
- [Technology Stack](#-technology-stack)
- [Project Architecture](#-project-architecture)
- [Repository Structure](#-repository-structure)
- [Data Cleaning & Transformation](#-data-cleaning--transformation)
- [SQL Business Analysis](#-sql-business-analysis)
- [Power BI Dashboard](#-power-bi-dashboard)
- [Key Business Insights](#-key-business-insights)
- [Strategic Recommendations](#-strategic-recommendations)
- [Installation & Setup](#-installation--setup)
- [License](#-license)

---

## 🎯 Project Overview

Understanding customer purchasing behavior is essential for improving sales performance, customer retention, and profitability.

This project analyzes a retail customer shopping dataset containing **3,900 records and 18 attributes** to identify purchasing trends, evaluate product performance, investigate discount dependency, and uncover opportunities for subscription growth.

The project follows a structured data analytics pipeline:

1. **Data Preparation:** Cleaned and transformed raw transactional data using Python.
2. **Database Management:** Loaded processed data into MySQL using SQLAlchemy.
3. **Data Analysis:** Executed advanced SQL queries to answer business questions.
4. **Data Visualization:** Developed an interactive Power BI dashboard.
5. **Business Intelligence:** Converted analytical findings into actionable business recommendations.

---

## 🎯 Business Objectives

The primary objectives of this analysis are:

- Analyze purchasing patterns across different customer demographics.
- Identify top-performing products and product categories.
- Evaluate the impact of discounts on customer purchasing decisions.
- Compare spending behavior between subscribers and non-subscribers.
- Understand customer loyalty and repeat purchasing patterns.
- Identify opportunities to improve subscription conversion.
- Develop data-driven recommendations to support business decisions.

---

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Python | Data cleaning, transformation, and ETL |
| Pandas | Data manipulation and analysis |
| NumPy | Numerical operations |
| MySQL | Relational database management |
| SQLAlchemy | Python-to-MySQL connectivity |
| PyMySQL | MySQL database driver |
| SQL | Business analysis and querying |
| Power BI | Interactive dashboards and visualization |
| Visual Studio Code | Development environment |
| Git & GitHub | Version control and project management |

---

## 🏗️ Project Architecture

The project follows a structured ETL and business intelligence workflow.

**Raw Dataset → Python ETL → MySQL Database → SQL Analysis → Power BI Dashboard**

### 1. Data Extraction & Preparation
- Imported the raw CSV dataset using Pandas.
- Audited 3,900 records and 18 attributes.
- Identified missing values, inconsistent column names, and redundant features.

### 2. Data Cleaning & Transformation
- Handled missing review ratings using category-specific median imputation.
- Standardized column names using lowercase snake_case.
- Created age-based demographic segments using `pd.qcut()`.
- Converted purchase frequency categories into numerical day intervals.
- Identified and removed redundant columns.

### 3. Database Integration
- Established a connection between Python and MySQL using SQLAlchemy.
- Created the `customer_analysis` database.
- Loaded the cleaned dataset into the `customer` table.

### 4. SQL Business Analysis
- Developed 10 analytical SQL queries.
- Used aggregations, subqueries, CTEs, window functions, and conditional logic.
- Extracted insights related to revenue, customer loyalty, product performance, and subscription behavior.

### 5. Dashboard Development
- Connected Power BI to the processed dataset.
- Created KPI cards, charts, and interactive slicers.
- Designed an executive dashboard for business performance monitoring.

---

## 📁 Repository Structure

```text
Customer-Shopping-Behavior-Analysis/
│
├── data/
│   └── customer_shopping_behavior.csv
│
├── scripts/
│   └── etl.py
│
├── sql/
│   └── queries.sql
│
├── reports/
│   ├── Customer_Behavior_Dashboard.pbix
│   └── Presentation.pptx
│
├── README.md
└── LICENSE
```

---

## 🧹 Data Cleaning & Transformation

The raw dataset underwent several preprocessing operations to improve data quality and analytical reliability.

| Operation | Description |
|---|---|
| Missing Value Treatment | Imputed 37 missing review ratings using category-specific median values. |
| Column Standardization | Converted column names into lowercase snake_case. |
| Feature Engineering | Created age groups using demographic quartiles. |
| Frequency Mapping | Converted textual purchase frequencies into numerical day intervals. |
| Redundancy Removal | Dropped `promo_code_used` after identifying 100% redundancy with `discount_applied`. |
| Database Loading | Imported cleaned records into MySQL. |

**New Feature Created:**

`age_group` categorizes customers into four demographic segments:

- Young Adult
- Adult
- Middle-Aged
- Senior

---

## 🔍 SQL Business Analysis

Developed 10 SQL queries to investigate important business questions using MySQL.

| # | Business Question | SQL Concepts Used |
|---|---|---|
| 1 | Revenue distribution by gender | GROUP BY, SUM(), Aggregation |
| 2 | High-spending customers using discounts | Subqueries, AVG() |
| 3 | Top 5 highest-rated products | AVG(), ROUND(), ORDER BY, LIMIT |
| 4 | Shipping speed vs. average purchase amount | GROUP BY, HAVING |
| 5 | Subscription vs. non-subscription spending | Conditional Aggregation |
| 6 | Products dependent on discounts | CASE WHEN, Aggregation |
| 7 | Customer loyalty segmentation | CTE, CASE WHEN |
| 8 | Top-performing products within each category | Window Functions, ROW_NUMBER() |
| 9 | Repeat buyers and subscription conversion gap | Filtering, Segmentation |
| 10 | Revenue contribution by age group | GROUP BY, SUM() |

---

## 📈 Key Business Insights

### 1. Revenue by Gender

- Male customers generated **$157,890 (67.7%)** in revenue.
- Female customers generated **$75,191 (32.3%)**.
- Average order value remained nearly identical at approximately $59.70.

**Insight:** The revenue difference is primarily driven by transaction volume rather than spending per transaction.

### 2. High-Spending Discount Users

- Identified **839 high-spending transactions** above the average purchase amount that still received discounts.

**Insight:** Applying discounts to high-value purchases may result in unnecessary margin concessions.

### 3. Top 5 Highest-Rated Products

| Product | Average Rating |
|---|---:|
| Gloves | 3.86 |
| Sandals | 3.84 |
| Boots | 3.82 |
| Hats | 3.80 |
| Skirts | 3.78 |

**Insight:** These products demonstrate relatively strong customer satisfaction and could be prioritized in promotional campaigns.

### 4. Shipping Speed vs. Basket Size

| Shipping Method | Average Purchase Amount |
|---|---:|
| Express | $60.48 |
| Standard | $58.46 |

**Insight:** Express shipping customers spend approximately $2.02 more per transaction.

### 5. Subscription Financial Comparison

| Customer Type | Average Purchase Amount |
|---|---:|
| Subscribers | $59.49 |
| Non-Subscribers | $59.87 |

**Insight:** Subscription membership does not significantly increase average transaction value. Its potential business value lies more in retention and purchase frequency.

### 6. Discount-Dependent Products

Products with the highest discount usage:

| Product | Discount Usage |
|---|---:|
| Hats | 50.0% |
| Sneakers | 49.7% |
| Coats | 49.1% |
| Sweaters | 48.2% |
| Pants | 47.4% |

**Insight:** Several popular apparel products show substantial discount dependency, indicating an opportunity to optimize promotional strategies.

### 7. Customer Loyalty Segmentation

| Customer Segment | Customers | Percentage |
|---|---:|---:|
| Loyal (>10 purchases) | 3,116 | 79.9% |
| Returning (2–10 purchases) | 701 | 18.0% |
| New (1 purchase) | 83 | 2.1% |

**Insight:** The dataset contains a strong proportion of repeat purchasers but a relatively small new-customer segment.

### 8. Top Products by Category

| Category | Top-Performing Products |
|---|---|
| Clothing | Blouse (171), Pants (171), Shirt (169) |
| Accessories | Jewelry (171), Sunglasses (161), Belt (161) |
| Footwear | Sandals (160), Shoes (150), Sneakers (145) |
| Outerwear | Jacket (163), Coat (161) |

**Insight:** Product performance varies across categories, providing opportunities for category-specific inventory and marketing strategies.

### 9. Repeat Buyers & Subscription Conversion Gap

Among customers with more than five previous purchases:

- **2,518** were not subscribed.
- **958** were subscribed.

**Insight:** Frequent repeat buyers represent a potential target audience for subscription conversion campaigns.

### 10. Revenue Contribution by Age Group

| Age Group | Revenue |
|---|---:|
| Young Adults | $62,143 |
| Middle-Aged | $59,197 |
| Adults | $55,978 |
| Seniors | $55,763 |

**Insight:** Revenue contribution is relatively balanced across demographic segments, suggesting opportunities for targeted marketing across different age groups.

---

## 📊 Power BI Dashboard

An interactive executive dashboard was developed in Power BI to visualize customer behavior and key business performance indicators.

### Dashboard Features

**Key Performance Indicators (KPIs)**

- Total Customers: 3.9K
- Average Order Value: $59.76
- Average Review Rating: 3.75

**Subscription Analysis**

- 27% Subscribed
- 73% Non-Subscribed

**Category Performance**

- Clothing generated the highest revenue, exceeding $104K.
- Clothing also recorded the highest sales volume, with 1,737 units.

**Interactive Slicers**

Users can dynamically filter the dashboard using:

- Gender
- Subscription Status
- Product Category
- Shipping Method

The dashboard enables users to explore customer segments, compare purchasing behavior, and identify trends through interactive filtering.

---

## 💡 Strategic Business Recommendations

Based on the SQL analysis and dashboard findings, the following business recommendations were identified.

### 1. Accelerate Subscription Conversion

Target the 2,518 frequent repeat buyers who are not currently subscribed.

Introduce subscription benefits such as:
- Free express shipping.
- Exclusive member rewards.
- Early access to new collections.
- Personalized loyalty benefits.

### 2. Optimize Discount Strategies

Reduce unnecessary discounts on high-demand products such as Sneakers, Pants, and Hats.

Consider introducing minimum purchase thresholds for promotional offers to protect profit margins.

### 3. Promote High-Performing Products

Prioritize highly rated products such as Sandals, Boots, and Gloves in marketing campaigns.

Explore product bundling and cross-selling opportunities to increase average basket value.

### 4. Expand Customer Acquisition

Develop targeted marketing campaigns to attract new customers and improve acquisition across underrepresented customer segments.

Focus on personalized campaigns rather than relying exclusively on discounts.

---

## ⚙️ Installation & Setup

Follow these steps to run the project locally.

### Prerequisites

Make sure you have installed:

- Python 3.10+
- MySQL Server
- Visual Studio Code
- Power BI Desktop

### Step 1: Clone the Repository

```bash
git clone https://github.com/your-username/customer-shopping-behavior-analysis.git

cd customer-shopping-behavior-analysis
```

### Step 2: Install Dependencies

```bash
pip install pandas numpy sqlalchemy pymysql
``
