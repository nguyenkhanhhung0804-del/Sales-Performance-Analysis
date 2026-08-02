# Plant Sales Analytics (SQL & Power BI Data Modeling)

This repository contains a comprehensive data analysis project focused on regional plant sales, product performance, and financial reporting. It utilizes a multi-table database (`Plant_DTS.xls`) to extract key business insights using custom **SQLite** queries and structured data relationship models.

# 📊 Database Relationship

The project uses a **star schema**, where `Plant_FACT` is the central fact table connected to two dimension tables.

```text
                    Accounts
             (Customer Dimension)
                  Account_id
                      │
                      │
                      │
Plant_Hierarchy ───── Plant_FACT
(Product Dimension)    (Fact Table)
    Product_id          Product_id
                        Account_id
```

## Table Relationships

| Table | Primary Key | Relationship |
|-------|-------------|--------------|
| **Accounts** | `Account_id` | One customer can have multiple sales transactions. |
| **Plant_FACT** | `Account_id`, `Product_id` | Stores transactional sales data and links customers to products. |
| **Plant_Hierarchy** | `Product_id` | One product can appear in multiple sales transactions. |

---

# 🛠️ SQLite Queries & Analytical Tasks

The repository includes curated **SQLite scripts** designed to answer critical business performance questions, structured into the following analytical themes:

### 1. Financial Trends & Growth Analysis
* **Pareto Analysis (80/20 Rule):** Computes cumulative revenue percentages to identify which top products generate $80\%$ of total company revenue.

### 2. Product & Category Optimization
* **Top 10 Most Profitable Products:** Pinpoints high-volume drivers by calculating gross profits:
  $$\text{Profit} = (\text{Sales USD} - \text{COGS USD}) \times \text{Quantity}$$
* **High-Revenue, Low-Profit Products:** Highlights products with higher-than-average revenue but below-average margins, pointing to high production costs or pricing issues.
* **Profit Margin by Product:** Breaks down individual product margin efficiency percentages.

### 3. Geographical Segmentation
* **Top 5 Product Family contribution to Revenue:** Measures revenue amount contributed for each product family
* **Top 5 Country contribution to Revenue:** Measures percent share contributions for each geographical market.
* **Revenue & Profit by Country:** Summarizes overall financial performance per country code.
* **Top 3 Products by Country:** Uses partitioning and row ranking (`ROW_NUMBER()`) to extract top selling items tailored to local market preferences.

---

# 🎨 Power BI Dashboard & Data Modeling Skills

In addition to SQL extraction, this project features an interactive **sales_performance_dashboard.pbix** built to turn raw data into executive-level insights. This component highlights key business intelligence capabilities:

* **Star-Schema Data Modeling:** Designed a highly efficient relational data model in Power BI, establishing robust relationships (1-to-many) between the centralized fact table (`Plant_FACT`) and the geographical (`Accounts`) and product (`Plant_Hierarchy`) dimensions.
* **DAX Formulas (Data Analysis Expressions):** Wrote custom DAX measures to compute key performance indicators (KPIs) dynamically, such as total revenues, profit margins, geographic distribution percentages, and time-intelligence metrics (MoM and YoY performance).
* **Interactive Data Visualization:** Developed an intuitive user interface utilizing slicers, map-based regional breakdowns, and product category trends to allow stakeholders to drill down from global trends directly into specific product families.

## Author

**Hung Khanh Nguyen**
