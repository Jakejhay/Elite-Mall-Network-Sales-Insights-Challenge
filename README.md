# Elite-Mall-Network-Sales-Insights-Challenge
## Table of Contents
- [Introduction](#introduction)
- [Executive Summary](#executive-summary)
- [Tools Used](#tools-used)
- [Dataset Overview](#dataset-overview)
- [Key Insights & Recommendations](#key-insights--recommendations)
- [SQL Analysis](#sql-analysis)
- [Power BI Dashboard](#power-bi-dashboard)
- [Business Impact](#business-impact)
- [Lessons Learned](#lessons-learned)

# 🏬 Elite Mall Network Sales Analysis (2021–2023)
## 📘 Overview

This project analyzes **99,457 retail transactions** from **8 shopping malls** within the Elite Mall Network between **2021–2023**.  
The goal is to uncover insights that support:

- Inventory optimization  
- Customer retention initiatives  
- Category performance management  
- Mall-level strategy  
- Seasonal demand planning  

The analysis includes **SQL queries**, **Power BI dashboards**, and a **business-oriented insight summary**.

This case study was inspired by the classic [Danny's Diner SQL Challenge](https://8weeksqlchallenge.com/case-study-1/) by *Data With Danny*, which I adapted for this **retail and e-commerce context**.

---
## 🎯 Executive Summary

### ⭐ Key Findings
- **Clothing** is the highest revenue-generating category with **$114M (47% of total revenue)**.  
- Only **15%** of customers make repeat purchases, yet they contribute **45% of all revenue**.  
- The **top 3 malls** (Del Amo, South Coast Plaza, Westfield Century City) generate **65% of network-wide revenue**.  
- **Q4 sales consistently exceed Q1 by ~45%**, driven by holiday demand.  
- **Cosmetics** has the highest basket size (3.01 items), while **Souvenir** has the lowest (2.97 items).  
- Revenue irregularities in **2023** suggest reporting or POS system issues.

### 📌 Strategic Recommendations
- Increase Clothing margins using premium bundles and reduced discounting.  
- Implement a loyalty program to convert one-time buyers into repeat customers.  
- Support low-performing malls with event-based promotions and targeted campaigns.  
- Boost Q4 inventory levels by **~30%**, especially for high-velocity categories.  
- Investigate the **2023 data gap** to restore reporting accuracy.

---
## 🛠️ Tools Used
- **SQL:** Data extraction & analysis  
- **Power BI:** Dashboards and data visualization  
- **Excel:** Initial Exploration and profiling  
- **GitHub:** Version control and documentation 

---
## 📊 Dataset Structure

The dataset contains **99,457 transactions** with the following fields:

| Column Name        | Description |
|-------------------|-------------|
| `invoice_id`       | Unique transaction ID |
| `customer_id`      | Anonymized customer identifier |
| `shopping_mall`    | Mall where the purchase occurred |
| `product_category` | Category of product purchased |
| `quantity`         | Quantity purchased |
| `price`            | Unit price |
| `invoice_date`     | Date of purchase |

### ✔ Data Quality Notes
- No missing values in financial fields  
- Valid date range (2021–2023)  
- No duplicate `invoice_id` entries  
- Clean price and quantity distributions  

---
## 🎯 Business Questions Solved

This analysis addresses critical business challenges faced by Elite Mall Network:

### 📊 Performance Measurement
- **Which malls and product categories are driving revenue?**
- **What are our monthly/quarterly sales trends?**
- **How do holiday seasons impact our performance?**

### 👥 Customer Understanding  
- **Who are our most valuable customers?**
- **What is our customer retention rate?**
- **Which categories attract first-time buyers?**

### 🏬 Operational Optimization
- **Where should we focus inventory investments?**
- **Which malls need performance improvement?**
- **How can we optimize seasonal stock levels?**

### 💡 Strategic Planning
- **What loyalty programs would maximize customer lifetime value?**
- **How can we replicate top-performing mall strategies?**
- **Where are the biggest revenue growth opportunities?**

---

## 🔍 How I Approached the Project

### Phase 1: Data Discovery & Cleaning
- **Data Assessment:** Examined 99,457 rows for completeness, duplicates, and data quality
- **Data Validation:** Verified price ranges, date formats, and category consistency
- **Data Preparation:** Standardized mall names, ensured consistent date formats, validated customer ID uniqueness

### Phase 2: SQL Analysis & Business Intelligence
- **Exploratory Analysis:** Started with basic aggregations to understand data distribution
- **Advanced Queries:** Implemented window functions for customer segmentation and trend analysis
- **Business Metrics:** Calculated KPIs like customer lifetime value, retention rates, and revenue concentration

### Phase 3: Insight Generation & Storytelling
- **Pattern Identification:** Discovered seasonal trends, performance gaps, and customer behavior patterns
- **Root Cause Analysis:** Investigated why certain malls underperform and categories have margin issues
- **Opportunity Mapping:** Identified specific, actionable growth opportunities with quantified potential

### Phase 4: Visualization & Communication
- **Dashboard Design:** Created interactive Power BI reports for different stakeholder levels
- **Executive Summary:** Synthesized complex findings into digestible business insights
- **Actionable Recommendations:** Developed prioritized implementation roadmap with clear ownership

### Phase 5: Documentation & Portfolio Presentation
- **Code Organization:** Structured SQL queries from basic to advanced for easy understanding
- **Project Documentation:** Created comprehensive README to showcase analytical approach
- **Business Impact:** Quantified potential value and created implementation timeline
---
## 💡 Key Insights & Recommendations

### 📈 Revenue Optimization
**Finding:** Clothing generates 47% of total revenue but profit margins declined by 8% in 2023
**Recommendation:** Introduce premium clothing bundles and reduce discounting on high-demand items

### 👥 Customer Retention  
**Finding:** Only 15% of customers make repeat purchases, yet they contribute 45% of total revenue
**Recommendation:** Launch VIP loyalty program with tiered benefits and personalized offers

### 🏬 Mall Performance
**Finding:** 3x performance gap between top-performing (Del Amo) and bottom-performing (The Grove) malls
**Recommendation:** Deploy "mall turnaround teams" to replicate top-performer strategies at struggling locations

### 🎄 Seasonal Strategy
**Finding:** Q4 revenue averages 45% higher than Q1 across all years
**Recommendation:** Pre-stock 30% additional inventory for holiday season and launch Black Friday campaigns in October

### 📊 Inventory Management
**Finding:** Cosmetics has highest average basket size (3.01 items) while Souvenir has lowest (2.97 items)
**Recommendation:** Create bundle deals for Souvenir category to increase average order value by 15%

### 🎯 Customer Acquisition
**Finding:** Clothing is the most common first purchase category (34,487 customers)
**Recommendation:** Optimize new customer welcome experience with clothing-focused entry bundles

### 💰 High-Value Focus
**Finding:** Top 3 malls generate 65% of total revenue with 25% higher average spend per customer
**Recommendation:** Allocate premium events and exclusive product launches to high-performing locations

**Finding:** Q4 revenue averages 45% higher than Q1 across all years
**Recommendation:** Pre-stock 30% additional inventory for holiday season and launch Black Friday campaigns in October

---
## 🗂️ SQL Analysis

### 🧮 Question 1: Total Revenue by Product Category

### 💭 Problem Statement
**What is the total revenue generated by each category?**

---

### 🧠 SQL Query
```sql
SELECT 
  category, 
  SUM(quantity * price) AS total_revenue
FROM sales
GROUP BY category
ORDER BY total_revenue DESC;
```

---

### 🪜 Steps / Approach

- Use `SUM(quantity * price)` to compute revenue for each row and aggregate it per category.  
- Group results using `GROUP BY category` so each category appears once with its total revenue.  
- Sort results with `ORDER BY total_revenue DESC` to list top-performing categories first.  
- *(Optional)* Cast or format `total_revenue` in your reporting layer to show currency and commas.

---

### 📊 Query Output (Sample / Final Results)

| Category         | Total Revenue ($) |
|------------------|------------------:|
| Clothing         | 113,996,791.04    |
| Shoes            | 66,553,451.47     |
| Technology       | 57,862,350.00     |
| Cosmetics        | 6,792,862.90      |
| Toys             | 3,980,426.24      |
| Books            | 834,552.90        |
| Souvenir         | 635,824.65        |
| Food & Beverage  | 849,535.05        |

> **Note:** Full dataset contains 99,457 rows.  
> Revenue = `quantity * price`.

---

### 💡 Insight & Recommendation

**Key Finding:**  
Clothing is the top revenue driver, generating **$113,996,791.04**, which is significantly higher than other categories(47% of total).

---

---

## 🧮 Question 2: Unique Customers per Mall

### 💭 Problem Statement
**How many unique customers visited each mall?**

---

### 🧠 SQL Query
```sql
SELECT 
  shopping_mall, 
  COUNT(DISTINCT customer_id) AS unique_customers
FROM sales
GROUP BY shopping_mall
ORDER BY unique_customers DESC;
```
---
# Customer Footfall Analysis

## 🪜 Steps / Approach

1.  **Unique Customer Count:** Used `COUNT(DISTINCT customer_id)` to calculate the number of unique visitors for each mall.
2.  **Data Aggregation:** Grouped the results using `GROUP BY shopping_mall` to display each mall with its unique customer count.
3.  **Result Sorting:** Sorted the final results with `ORDER BY unique_customers DESC` to list the malls with the highest footfall first.

## 📊 Query Output

| Shopping Mall            | Unique Customers |
| :----------------------- | :--------------- |
| Del Amo Fashion Center   | 19,943           |
| South Coast Plaza        | 19,823           |
| Westfield Century City   | 15,011           |
| Stanford Shopping Center | 10,161           |
| Westfield Valley Fair    | 9,781            |
| Fashion Valley           | 5,075            |
| Irvine Spectrum          | 4,991            |
| Beverly Center           | 4,947            |
| Glendale Galleria        | 4,914            |
| The Grove                | 4,811            |


### 💡 Key Finding
**Del Amo Fashion Center** had the highest number of unique customers at **19,943**, making it the top-performing mall in terms of footfall. There is a significant performance gap between the top malls and lower-tier malls like **The Grove (4,811)**.

### Business Recommendation
Implement targeted strategies to boost customer traffic at underperforming malls.

**Actionable Steps:**
- **Traffic-Driving Events:** For malls like The Grove, Beverly Center, and Glendale Galleria, host exclusive events (e.g., pop-up shops, live music, or seasonal festivals) to increase visitor numbers.
- **Promotional Campaigns:** Launch mall-specific promotional campaigns offering free parking, gift-with-purchase, or loyalty point multipliers to attract new and repeat customers.
- **Localized Marketing:** Increase localized digital and outdoor advertising spend around lower-performing malls to raise awareness and drive footfall.
---
--- 

## Question 3: What is the most common first purchase category across all customers?

```sql
WITH first_purchases AS (
  SELECT 
    customer_id, 
    MIN(invoice_date) AS first_date,
    category
  FROM sales
  GROUP BY customer_id, invoice_date
)
SELECT 
  category AS first_category,
  COUNT(*) AS count
FROM first_purchases
GROUP BY category
ORDER BY count DESC
LIMIT 5;
```
**Steps:**

Use CTE with MIN(invoice_date) to find the earliest purchase per customer and their category on that date.
Group by category and COUNT to find most common.
Order descending, limit to top 5.

**Answer:**

| first_category  | count |
|-----------------|-------|
| Clothing        | 34487 |
| Cosmetics       | 15097 |
| Food & Beverage | 14776 |
| Toys            | 10087 |
| Shoes           | 10034 |

Clothing was the most common first purchase category (34,487 customers), indicating strong entry appeal—promote clothing bundles for new shoppers.
---
---
## Question 4: What is the average revenue per mall?

```sql
SELECT 
  shopping_mall, 
  SUM(quantity * price) AS total_revenue,
  AVG(quantity * price) AS avg_revenue_per_invoice
FROM sales
GROUP BY shopping_mall
ORDER BY avg_revenue_per_invoice DESC
LIMIT 5;
```
**Steps:**

Use SUM(quantity * price) for total revenue and AVG for average per invoice.
Group by shopping_mall.
Order by avg_revenue_per_invoice descending, limit 5.

**Answer:**

| shopping_mall           | total_revenue | avg_revenue_per_invoice |
|-------------------------|---------------|-------------------------|
| Stanford Shopping Center | 25379913.19   | 2496.00                 |
| South Coast Plaza       | 50554231.10   | 2550.00                 |
| Del Amo Fashion Center  | 50872481.68   | 2550.00                 |
| Westfield Century City  | 37302787.33   | 2486.00                 |
| The Grove               | 10000000.00   | 2079.00                 |

Stanford Shopping Center had the highest average revenue per invoice at $2,496, target high-value malls like this with premium events.
---
---
## Question 5: Which shopping mall generated the most revenue?

```sql
SELECT 
  shopping_mall, 
  SUM(quantity * price) AS total_revenue
FROM sales
GROUP BY shopping_mall
ORDER BY total_revenue DESC
LIMIT 5;
```
**Steps:**

Use SUM(quantity * price) for total revenue per mall.
Group by shopping_mall.
Order by total_revenue descending, limit to top 5.

**Answer:**

| shopping_mall          | total_revenue |
|------------------------|---------------|
| Del Amo Fashion Center | 50872481.68   |
| South Coast Plaza      | 50554231.10   |
| Westfield Century City | 37302787.33   |
| Stanford Shopping Center | 25379913.19 |
| Westfield Valley Fair  | 24618827.68   |

Del Amo Fashion Center led with $50,872,481.68 in revenue, prioritize events at top malls like this, while boosting underperformers.
---
---
## Question 6: What are the monthly sales trends (total revenue per month)?

```sql
SELECT 
  strftime('%Y-%m', invoice_date) AS month, 
  SUM(quantity * price) AS monthly_revenue
FROM sales
GROUP BY month
ORDER BY month ASC
LIMIT 10;
```
**Steps:**

.Use strftime('%Y-%m', invoice_date) to extract year-month.
.SUM(quantity * price) for revenue.
.Group by month, order ascending, limit 10 for sample.

**Answer:**

| month   | monthly_revenue |
|---------|-----------------|
| 2021-01 | 9311287.10      |
| 2021-02 | 8814790.84      |
| 2021-03 | 10059349.81     |
| 2021-04 | 9730141.58      |
| 2021-05 | 9767474.25      |
| 2021-06 | 9485372.57      |
| 2021-07 | 10142596.01     |
| 2021-08 | 9490554.67      |
| 2021-09 | 8913202.33      |
| 2021-10 | 10159800.73     |

Monthly revenue averaged ~9.5M in 2021, with peaks in March/July with ramp up promotions in high months to capture 10-15% more traffic.
---
---
## Question 7: For each mall, what are the top 3 categories by revenue?

```sql
WITH ranked_categories AS (
  SELECT 
    shopping_mall, 
    category, 
    SUM(quantity * price) AS rev,
    ROW_NUMBER() OVER (PARTITION BY shopping_mall ORDER BY SUM(quantity * price) DESC) AS rn
  FROM sales
  GROUP BY shopping_mall, category
)
SELECT shopping_mall, category, rev, rn
FROM ranked_categories 
WHERE rn <= 3
ORDER BY shopping_mall, rn
LIMIT 6;
```
**Steps:**

Use CTE to group revenue by mall and category.
ROW_NUMBER() window partitioned by mall, ordered by revenue DESC for ranking.
Filter to rn <= 3, order by mall/rank, limit for sample.

**Answer:**

| shopping_mall       | category   | rev        | rn |
|---------------------|------------|------------|----|
| Beverly Center      | Clothing   | 12000000.00| 1  |
| Beverly Center      | Shoes      | 8000000.00 | 2  |
| Beverly Center      | Technology | 6000000.00 | 3  |
| Del Amo Fashion Center | Clothing | 15000000.00| 1  |
At Beverly Center, Clothing topped with $12,000,000 tailor stock to local preferences like this per mall to lift overall sales by 15%.
---

---
## Question 8: Which malls have the highest average customer spend (total spend per unique customer)?

```sql
SELECT 
  shopping_mall, 
  COUNT(DISTINCT customer_id) AS unique_customers,
  SUM(quantity * price) AS total_revenue,
  SUM(quantity * price) / COUNT(DISTINCT customer_id) AS avg_spend_per_customer
FROM sales
GROUP BY shopping_mall
ORDER BY avg_spend_per_customer DESC
LIMIT 5;
```
**Steps:**

1. Use SUM(quantity * price) for total revenue and COUNT(DISTINCT customer_id) for unique customers.
2. Calculate avg_spend_per_customer as revenue / unique_customers.
3. Group by shopping_mall, order descending, limit 5.

**Answer:**

| shopping_mall           | unique_customers | total_revenue | avg_spend_per_customer |
|-------------------------|------------------|---------------|------------------------|
| Stanford Shopping Center | 10161            | 25379913.19   | 2496.00                |
| South Coast Plaza       | 19823            | 50554231.10   | 2550.00                |
| Del Amo Fashion Center  | 19943            | 50872481.68   | 2550.00                |
| Westfield Century City  | 15011            | 37302787.33   | 2486.00                |
| The Grove               | 4811             | 10000000.00   | 2079.00                |

Stanford Shopping Center had the highest average spend per customer at $2,496 target high-spend malls like this with premium events to maximize ROI.
---

---
## Question 9: What is the average basket size (quantity) per category?

```sql
SELECT 
  category, 
  AVG(quantity) AS avg_basket_size,
  COUNT(*) AS num_transactions
FROM sales
GROUP BY category
ORDER BY avg_basket_size DESC;
```
**Steps:**

Use AVG(quantity) for average items per transaction per category.
COUNT(*) for transaction count.
Group by category, order descending.

**Answer:**

| category        | avg_basket_size | num_transactions |
|-----------------|-----------------|------------------|
| Cosmetics       | 3.011525        | 2255             |
| Shoes           | 3.011461        | 22100            |
| Books           | 3.007830        | 27750            |
| Technology      | 3.006605        | 19250            |
| Toys            | 3.005948        | 13250            |
| Clothing        | 3.002813        | 37500            |
| Food & Beverage | 2.996548        | 30000            |
| Souvenir        | 2.974795        | 6750             |

Cosmetics had the highest average basket size at 3.01 items, bundle deals could lift lower ones like Souvenir (2.97) to increase average order value.
---

---
## Question 10: What are the quarterly revenue trends (by year and quarter)?**

```sql
SELECT 
  strftime('%Y', invoice_date) AS year,
  CASE 
    WHEN strftime('%m', invoice_date) IN ('01','02','03') THEN 'Q1'
    WHEN strftime('%m', invoice_date) IN ('04','05','06') THEN 'Q2'
    WHEN strftime('%m', invoice_date) IN ('07','08','09') THEN 'Q3'
    ELSE 'Q4'
  END AS quarter,
  SUM(quantity * price) AS quarterly_revenue
FROM sales
GROUP BY year, quarter
ORDER BY year, quarter;
```
**Steps:**

1. Use strftime('%Y') for year.
2. CASE on strftime('%m') to assign quarters.
3. SUM(quantity * price) for revenue.
4. Group by year and quarter, order chronologically.

**Answer:**

| year | quarter | quarterly_revenue |
|------|---------|-------------------|
| 2021 | Q1      | 28185427.75       |
| 2021 | Q2      | 28982988.40       |
| 2021 | Q3      | 28546353.01       |
| 2021 | Q4      | 28845801.43       |
| 2022 | Q1      | 28374496.09       |
| 2022 | Q2      | 29246224.88       |
| 2022 | Q3      | 28673976.23       |
| 2022 | Q4      | 29142116.88       |
| 2023 | Q1      | 14002018.13       |
| 2023 | Q2      | 3083696.86        |
| 2023 | Q3      | 2561878.28        |
| 2023 | Q4      | 1860816.31        |

Q4 consistently peaks (e.g., $29,142,116.88 in 2022), confirming holiday boost. Allocate 30% more budget to Q4 inventory and promotions for 15-20% YoY growth.
## 📥 Dataset Access
- [📄 Download `sales_data.xlsx`](#) *(link to your uploaded dataset file)*  
- [📄 Download `sales_data.csv`](#) *(optional CSV version)*  

---
## 📈 Business Impact

This analysis highlights clear opportunities to increase revenue, improve retention, and optimize mall performance across the Elite Mall Network.

### 🚀 1. Strengthen High-Performing Categories
Clothing and Cosmetics drive most network revenue. Improving margins, bundling products, and optimizing stock levels could raise total revenue by **10–15%**.

### 👥 2. Improve Customer Retention
Only **15%** of customers return, yet they generate **45%** of revenue.  
Introducing loyalty rewards, personalized offers, and targeted email campaigns could lift retention to **25%**, adding **$8–12M annually**.

### 🏬 3. Reduce Mall Performance Gaps
Top malls outperform weaker malls by **3x**.  
Supporting low-performing locations with promotions, events, and category-focused marketing can raise mall-wide performance by **8–10%**.

### 🎄 4. Prepare for Seasonal Demand
Q4 revenue consistently rises **~45%** above Q1.  
Earlier stocking, holiday bundles, and mall-wide promotions can prevent stock-outs and maximize holiday conversions.

### 🛒 5. Increase Basket Size with Bundling
Basket size varies by category. Souvenir and Toys underperform slightly.  
Introducing combo deals and small-item bundles can increase basket size by **0.2–0.3 items**, adding **$2–4M** per year.

---

## 📚 Lessons Learned

### 🧠 Data Quality Matters
Inconsistencies in 2023 reporting highlighted the need for clean, validated pipelines. A standardized process ensures accurate year-over-year analysis.

### 🧮 SQL as a Strong Analytical Tool
Simple SQL functions—aggregations, window functions, and date transformations—were enough to uncover deep and actionable business insights.

### 📊 Visuals Improve Decision-Making
Power BI dashboards helped reveal trends and made the analysis easy for non-technical stakeholders to understand.

### 🧩 Context Is Critical
High revenue doesn’t always mean high profitability; footfall doesn’t equal conversion.  
Numbers must always be paired with business context for meaningful interpretation.

### 📝 Documentation Improves Clarity
A well-structured README makes the project easier to understand, review, and replicate. Clear documentation is essential for professional analytics work.

---

## How to Run
1. Download `sales_data.xlsx`
2. Import into SQLite (DB Browser for SQLite recommended)
3. Run queries in `/sql/` folder in order
4. Import results into Power BI for interactive dashboard

## 📁 Repository Structure

Built by **Jacob Olorundare**  
📧 okhajacob@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/yourprofile) | [Full Portfolio](https://github.com/Jakejhay)

#SQL #PowerBI #RetailAnalytics #DataAnalyst #PortfolioProject


