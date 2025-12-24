# 📊 Supermarket Sales Analysis Dashboard | Power BI

## 📝 Project Overview
This project analyzes supermarket sales transaction data and transforms it into actionable business insights using **Power BI**.  
The dashboard focuses on **revenue, profit, gross profit margin, customer behavior, and product line performance**, supported by well-structured **DAX measures** and interactive visualizations.

This project is built as part of a **data analytics portfolio** to demonstrate skills in:
- Data modeling
- DAX calculations
- Quantitative business analysis
- Dashboard storytelling

---

## 🎯 Business Objectives
- Measure overall business performance using quantitative KPIs
- Analyze profitability and gross profit margin (GPM %)
- Identify top-performing product lines based on revenue and profit
- Analyze sales trends over time at multiple granularities
- Understand customer behavior and payment preferences

---

## 📁 Dataset Overview
 **Dataset Name:** Supermarket Sales Dataset
 **Time Period:** January – March 2019
 **Number of Transactions:** ~1,000
 **Granularity:** Transaction-level
 **Format:** CSV
 
### 📌 Dataset Schema
| Column | Description |
|------|-------------|
| invoice_id | Unique transaction identifier |
| branch | Store branch |
| city | Store location |
| customer_type | Member / Normal |
| gender | Customer gender |
| product_line | Product category |
| quantity | Number of units sold |
| unit_cost | Price per unit |
| cogs | Cost of Goods Sold |
| revenue | Sales amount |
| tax | Tax amount |
| payment | Payment method |
| rating | Customer satisfaction score |
| date | Transaction date |

---

##  Data Preparation & Cleaning
* The following steps were performed in Power BI:
* Standardized column naming conventions
* Converted date fields to proper Date format
* Validated numeric columns (quantity, unit cost, COGS)
* Checked missing and duplicate records
* Ensured data consistency for financial calculations

---

## Data Modeling & DAX Measures
All business metrics are calculated using **DAX measures** to ensure accuracy under slicers and filters.
---
### Dashboard Metrics (Quantitative KPIs)
KPI	Value
Total Revenue	~307,000
Net Revenue	~323,000
Total Profit	~15,000
Quantity Sold	~6,000 units
Gross Profit Margin	~4.8%
Number of Transactions	~1,000
---
### Sales & Profit Analysis

The supermarket generated approximately 307K in revenue with a total profit of 15K, resulting in a gross profit margin of 4.8%.

Profit trends show high daily volatility, with peak profit days exceeding 300, indicating potential effects from promotions or high-traffic periods.

Revenue and profit remain relatively consistent across product lines, suggesting a uniform pricing strategy.
---
### Product Line Performance

Food and Beverages is the highest-performing product line, contributing the largest share of revenue and profit.

Other product lines such as Fashion Accessories, Sports & Travel, and Electronic Accessories show balanced performance.

Average customer ratings range between 6.8 – 7.1, indicating overall positive customer satisfaction.
---
---
### 📐 Key DAX Measures
```DAX
Revenue =
SUMX(
    supermarket_sales,
    supermarket_sales[quantity] * supermarket_sales[unit_cost]
)

Tax =
[Revenue] * 0.05

Net Revenue =
[Revenue] + [Tax]

Profit =
[Net Revenue] - SUM(supermarket_sales[cogs])

Gross Profit Margin % =
DIVIDE([Profit], [Net Revenue], 0)



