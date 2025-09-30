# Sales Trend Analysis Using SQL

## Objective
Analyze monthly revenue, order volume, and product-wise performance using SQL aggregations to extract insights from sales data.

## Tools
- MySQL Workbench 
- SQL queries for aggregation

## Dataset
- Table: `online_sales`  
- Columns:  
  - `order_id` (INT)  
  - `order_date` (DATE)  
  - `amount` (DECIMAL)  
  - `product_id` (INT)  
- Sample data: 30 rows representing orders across the year 2024

## Queries Executed

### 1. Monthly Revenue & Order Volume
SELECT 
    YEAR(order_date) AS order_year,
    MONTH(order_date) AS order_month,
    SUM(amount) AS monthly_revenue,
    COUNT(DISTINCT order_id) AS order_volume
FROM online_sales
GROUP BY YEAR(order_date), MONTH(order_date)
ORDER BY order_year, order_month;
## Insight: Shows revenue trends and number of orders per month.

## 2. Top 3 Months by Sales
SELECT 
    YEAR(order_date) AS order_year,
    MONTH(order_date) AS order_month,
    SUM(amount) AS monthly_revenue
FROM online_sales
GROUP BY YEAR(order_date), MONTH(order_date)
ORDER BY monthly_revenue DESC
LIMIT 3;
## Insight: Highlights the months with the highest revenue.

## 3. Total Revenue per Year
SELECT 
    YEAR(order_date) AS order_year,
    SUM(amount) AS yearly_revenue
FROM online_sales
GROUP BY YEAR(order_date)
ORDER BY order_year;
## Insight: Summarizes revenue at the yearly level.

## 4. Count Orders per Product
SELECT 
    product_id,
    COUNT(order_id) AS total_orders
FROM online_sales
GROUP BY product_id
ORDER BY total_orders DESC;
## Insight: Identifies products with the highest number of orders.

## Key Insights

--Highest Revenue Months: Certain months (e.g.November) show peak sales, indicating seasonal trends.
--Monthly Order Volume: Months with high revenue also tend to have more orders, showing consistency in demand.
--Yearly Revenue: Overall sales increase steadily across the year, reflecting business growth.
--Top Products: Some products contribute disproportionately to total orders, highlighting best-sellers.
--Sales Trends: The data shows clear patterns in revenue and order distribution, useful for inventory and marketing decisions.
