# Superstore Sales Analysis using SQL

## 1. Project Overview

This project focuses on analyzing the Superstore sales dataset using PostgreSQL to address six business-oriented analytical requirements related to product sales, sales performance, monthly trends, and customer purchasing behavior.

The objective was to translate business requirements into SQL queries, apply appropriate analytical techniques, and generate structured outputs to support data-driven decision-making.

## 2. Business Requirements and Implementation

### Q1. Above-Average Product Sales Analysis

**Business Requirement**

Identify products whose total sales are strictly greater than the average total sales generated per product.

**Implementation**

- Calculated total sales and distinct order counts at the product level.
- Used a nested subquery to calculate the average of product-level total sales.
- Filtered products whose total sales exceeded this average.
- Sorted the results by total sales in descending order.

**Analytical Output**

A list of qualifying products containing product ID, product name, category, total sales, and distinct order count.

**SQL Techniques:** GROUP BY, SUM(), COUNT(DISTINCT), Subqueries, HAVING, ORDER BY.

### Q2. Customer Sales Performance by Segment

**Business Requirement**

Evaluate each customer segment's sales performance against its assigned sales target.

**Implementation**

- Calculated total sales, distinct customers, and distinct orders for each segment.
- Created a supporting temporary table containing sales targets for each segment.
- Joined the aggregated sales data with the target table using the segment column.
- Calculated target achievement percentage.
- Classified each segment as Target Achieved or Target Not Achieved.

**Analytical Output**

A segment-level performance comparison containing total sales, customer count, order count, sales target, achievement percentage, and performance classification.

**SQL Techniques:** GROUP BY, Aggregate Functions, INNER JOIN, CASE WHEN, Mathematical Calculations.

### Q3. Product Sales Ranking Within Each Category

**Business Requirement**

Identify the top three products by total sales within each product category.

**Implementation**

- Aggregated sales at the product level within each category.
- Applied the DENSE_RANK() window function.
- Partitioned the ranking by category and ordered products by total sales in descending order.
- Filtered the results to retain the top three ranks within each category.

**Analytical Output**

A category-wise ranking of products containing product ID, product name, total sales, and sales rank.

**SQL Techniques:** GROUP BY, SUM(), DENSE_RANK(), PARTITION BY, CTEs.

### Q4. Monthly Sales Trend Analysis

**Business Requirement**

Analyze monthly sales performance and identify changes compared with the previous month.

**Implementation**

- Aggregated total sales by year and month.
- Used the LAG() window function to retrieve previous-month sales.
- Calculated month-over-month (MoM) sales change.
- Applied CASE WHEN to classify the sales trend as Growth, Decline, No Change, or First Month.
- Used three chained CTEs to organize the calculations.

**Analytical Output**

A chronological monthly sales summary containing current sales, previous-month sales, MoM sales change, and sales trend classification.

**SQL Techniques:** CTEs, GROUP BY, Date Functions, LAG(), CASE WHEN, Arithmetic Calculations.

### Q5. Customer Order Frequency Analysis

**Business Requirement**

Analyze customer ordering patterns by calculating the number of days between consecutive orders.

**Implementation**

- Retrieved unique customer-order combinations to avoid counting multiple product rows from the same order separately.
- Used the LAG() window function, partitioned by customer, to retrieve the previous order date.
- Calculated the number of days between consecutive orders.
- Extracted the order year and month.
- Classified each order as First Order or Repeat Order.

**Analytical Output**

A customer-order-level analysis containing customer details, order dates, previous order dates, days since the previous order, order year, order month, and order sequence.

**SQL Techniques:** CTEs, GROUP BY, LAG(), PARTITION BY, Date Subtraction, EXTRACT(), CASE WHEN.

### Q6. Customer Purchase Behavior Analysis

**Business Requirement**

Identify customers whose total sales exceed the average customer-level sales within their respective segments and analyze their purchasing activity.

**Implementation**

- Calculated total sales and distinct order counts at the customer level.
- Used a correlated subquery to calculate the average customer-level sales within each segment.
- Filtered customers whose total sales exceeded their segment's average.
- Applied the RANK() window function to rank qualifying customers within each segment.
- Classified customers with 10 or more distinct orders as Frequent Customers and the remaining customers as Occasional Customers.

**Analytical Output**

A segment-wise customer performance analysis containing customer details, total sales, distinct order count, sales rank, and customer type.

**SQL Techniques:** GROUP BY, Aggregate Functions, Correlated Subqueries, RANK(), COUNT(DISTINCT), CASE WHEN.

## 3. Dataset Description

| Attribute | Description |
|---|---|
| Dataset | Superstore Sales Dataset |
| Source | Kaggle |
| Number of Records | 9,994 |
| Number of Columns | 21 |
| File Format | CSV |
| Database | PostgreSQL |

The dataset contains information about orders, customers, products, sales, discounts, quantities, and shipping.

Key fields used in the analysis include order ID, order date, customer ID, customer name, segment, product ID, product name, category, and sales.

## 4. Tools and Technologies

- **Database:** PostgreSQL
- **SQL Environment:** pgAdmin
- **Code Editor:** Visual Studio Code
- **Language:** SQL

## 5. Key SQL Concepts Applied

The project involved the practical application of the following SQL concepts:

- Data aggregation and grouping
- Subqueries and correlated subqueries
- INNER JOIN
- Common Table Expressions (CTEs)
- Window functions: RANK(), DENSE_RANK(), and LAG()
- Conditional logic using CASE WHEN
- Date and time functions
- DISTINCT and COUNT(DISTINCT)
- Mathematical calculations and sorting

## 6. Project Files

| File | Description |
|---|---|
| `project_1_super_store_sales_dataset.sql` | SQL implementations for the six analytical requirements. |
| `P1_SQL_Superstore Dataset.txt` | Documentation of business requirements, expected outputs, and SQL concepts. |
| `README.md` | Project overview, implementation approach, and analytical outputs. |

## 7. Dataset Source

The original dataset is available on Kaggle:

[Superstore Dataset Final – Kaggle](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final)

The raw CSV file is not included in this repository. It can be downloaded directly from the source.

---

**Project Status:** Completed