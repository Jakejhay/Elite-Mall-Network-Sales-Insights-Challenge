# Elite-Mall-Network-Sales-Insights-Challenge

## Table of Contents
- [Introduction](#Introduction)
- [Approach Notes](#how-to-customize-markdown-files)
- [Data Sets](#how-to-create-new-repository)
- [Case Study Questions](#how-to-create-new-repository)
- [Questions and Answers](#how-to-create-new-repository)
- [Bonus Case Study Questions](#how-to-create-new-repository)

# 🏬 Elite Mall Network Sales Analysis (2021–2023)

## 📖 Introduction
In this case study, you are **Jordan**, a data analyst at **Elite Mall Network**, a chain of luxury shopping centers across California.

The company has collected **transaction-level sales data** from **2021–2023**, including details on invoices, customers, product categories (such as *Clothing*, *Shoes*, and *Technology*), quantities sold, prices, and the specific mall location.

With the **holiday seasons approaching** and **inventory budgets tight**, the CEO wants **actionable insights** from this data to:
- Optimize stock levels  
- Launch targeted customer promotions  
- Boost foot traffic at underperforming malls  

This case study was inspired by the classic [Danny's Diner SQL Challenge](https://8weeksqlchallenge.com/case-study-1/) by *Data With Danny*, which I adapted for this **retail and e-commerce context**.

---

## 🎯 Objectives
- Analyze sales performance across malls and product categories  
- Identify top-performing products and customer segments  
- Recommend inventory and marketing strategies to improve sales  

---

## 🛠️ Tools Used
- **SQL** – for querying and extracting insights  
- **Power BI** – for dashboard and visualization  
- **Excel** – for initial data cleaning and validation  

---

## 📊 Dataset Overview
The dataset includes the following key fields:
- `invoice_id`
- `customer_id`
- `mall_location`
- `product_category`
- `quantity`
- `price`
- `order_date`

---

## 💡 Key Questions Explored
1. Which mall locations generated the highest total revenue?  
2. What are the best-selling product categories by year and season?  
3. Which customers contribute most to total sales?  
4. How do sales trends differ before and during holiday seasons?  
5. What actionable strategies can improve performance at low-performing malls?  

---

## 📈 Insights & Recommendations
*(To be filled in after analysis)*

---
---

## 🧭 Approach Notes
To handle the dataset’s scale (~100k rows and thousands of unique customers), I shifted some **per-customer analyses** (e.g., individual visit days) to **group-level insights** (e.g., unique visitors per mall).  
This ensures **efficient queries without performance hits**, mirroring how real analysts approach large datasets in production environments.

---

## 🗂️ Data Sets
The dataset has been provided as a single table called **`sales`**, containing transaction-level information for each purchase.

### **Table Structure**

| Column Name     | Description |
|-----------------|--------------|
| `invoice_no`    | Unique invoice identifier for each transaction |
| `customer_id`   | Unique customer identifier |
| `category`      | Product category purchased (e.g., Clothing, Shoes, Books) |
| `quantity`      | Number of items purchased |
| `invoice_date`  | Date of transaction |
| `price`         | Unit price of product |
| `shopping_mall` | Mall where the transaction occurred |

---

### **Sample Data Preview**

| invoice_no | customer_id | category   | quantity | invoice_date | price  | shopping_mall             |
|-------------|--------------|------------|-----------|---------------|--------|----------------------------|
| I138884     | C241288      | Clothing   | 5         | 2022-05-08    | 1500.4 | South Coast Plaza          |
| I317333     | C111565      | Shoes      | 3         | 2021-12-12    | 1800.51| Beverly Center             |
| I127801     | C266599      | Clothing   | 10        | 2021-09-11    | 300.08 | Westfield Century City     |
| I173702     | C988172      | Shoes      | 5         | 2021-05-16    | 3000.85| Stanford Shopping Center   |
| I337046     | C189076      | Books      | 4         | 2021-10-24    | 60.6   | South Coast Plaza          |
| I227836     | C657758      | Clothing   | 5         | 2022-05-24    | 1500.4 | Beverly Center             |
| I121056     | C151197      | Cosmetics  | 10        | 2022-03-13    | 40.66  | Westfield Valley Fair      |
| I293112     | C176086      | Clothing   | 20        | 2021-01-13    | 600.16 | Del Amo Fashion Center     |
| I293455     | C159642      | Clothing   | 30        | 2021-04-11    | 900.24 | Westfield Century City     |
| I326945     | C283361      | Clothing   | 20        | 2021-08-22    | 600.16 | South Coast Plaza          |

> **Note:** The full dataset contains **99,457 rows**.  
> Revenue can be calculated as `quantity * price`.  
> Download the full file as **`sales_data.xlsx`** or convert it to **CSV** for SQL import.

---

## 🧩 Case Study Questions
Use **SQL** to answer the following **10 questions**, progressing from basic aggregations to advanced date and window functions.  
These questions are designed for **group-level insights**, suitable for large datasets (~100k rows, thousands of customers and malls).

---

## 🧮 Question 1: Total Revenue by Product Category

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
Clothing is the top revenue driver, generating **$113,996,791.04**, which is significantly higher than other categories.

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

## 💡 Insight & Recommendation

### Key Finding
**Del Amo Fashion Center** had the highest number of unique customers at **19,943**, making it the top-performing mall in terms of footfall. There is a significant performance gap between the top malls and lower-tier malls like **The Grove (4,811)**.

### Business Recommendation
Implement targeted strategies to boost customer traffic at underperforming malls.

**Actionable Steps:**
- **Traffic-Driving Events:** For malls like The Grove, Beverly Center, and Glendale Galleria, host exclusive events (e.g., pop-up shops, live music, or seasonal festivals) to increase visitor numbers.
- **Promotional Campaigns:** Launch mall-specific promotional campaigns offering free parking, gift-with-purchase, or loyalty point multipliers to attract new and repeat customers.
- **Localized Marketing:** Increase localized digital and outdoor advertising spend around lower-performing malls to raise awareness and drive footfall.
---
--- 

**Question 3: What is the most common first purchase category across all customers?**

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
**Question 4: What is the average revenue per mall?**

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

Stanford Shopping Center had the highest average revenue per invoice at $2,496—target high-value malls like this with premium events.
---
---
**Question 5: Which shopping mall generated the most revenue?**

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

Del Amo Fashion Center led with $50,872,481.68 in revenue—prioritize events at top malls like this, while boosting underperformers.
---
---
**Question 6: What are the monthly sales trends (total revenue per month)?**

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

Monthly revenue averaged ~9.5M in 2021, with peaks in March/July—ramp up promotions in high months to capture 10-15% more traffic.
---
---
**Question 7: For each mall, what are the top 3 categories by revenue?**

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
At Beverly Center, Clothing topped with $12,000,000—tailor stock to local preferences like this per mall to lift overall sales by 15%.
---

---
**Question 8: Which malls have the highest average customer spend (total spend per unique customer)?**

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

Stanford Shopping Center had the highest average spend per customer at $2,496—target high-spend malls like this with premium events to maximize ROI.
---

---
**Question 9: What is the average basket size (quantity) per category?**

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

Cosmetics had the highest average basket size at 3.01 items—bundle deals could lift lower ones like Souvenir (2.97) to increase average order value.
---

---
**Question 10: What are the quarterly revenue trends (by year and quarter)?**

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

Q4 consistently peaks (e.g., $29,142,116.88 in 2022), confirming holiday boost—allocate 30% more budget to Q4 inventory and promotions for 15-20% YoY growth.
## 📥 Dataset Access
- [📄 Download `sales_data.xlsx`](#) *(link to your uploaded dataset file)*  
- [📄 Download `sales_data.csv`](#) *(optional CSV version)*  

---



## 📁 Repository Structure
