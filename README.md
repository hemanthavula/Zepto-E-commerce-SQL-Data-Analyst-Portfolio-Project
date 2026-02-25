# Zepto-E-commerce-SQL-Data-Analyst-Portfolio-Project
A comprehensive data exploration and analysis project using SQL to uncover business insights from a Zepto product dataset. Includes data cleaning, inventory analysis, and revenue estimation.
Zepto E-Commerce Product Analysis
Project Overview
This project provides a deep-dive analysis of an e-commerce dataset from Zepto, a leading quick-commerce platform in India. The primary goal is to leverage SQL to perform Exploratory Data Analysis (EDA), clean structured data, and derive actionable business insights regarding product performance, pricing strategies, and inventory management.

Business Questions Answered
The analysis focuses on key operational metrics for a quick-commerce business:

Product Availability: Identifying high-value items that are currently out of stock.

Revenue Estimation: Calculating potential revenue per category based on selling price and available inventory.

Pricing Strategy: Analyzing discount distributions across different product categories.

Inventory Profiling: Categorizing products based on weight (Low, Medium, Bulk) to understand logistics needs.

Dataset Description
The dataset (zepto_v2.csv) contains real-world product metadata across various categories like Fruits & Vegetables, Cooking Essentials, and Munchies.

Column,Description:
sku_id:Unique identifier for each product (Primary Key)
category:"Product segment (e.g., Beverages, Packaged Food) "
name:Specific product title 
mrp:Maximum Retail Price 
discountPercent:Percentage discount offered 
discountedSellingPrice:Final price after discount 
availableQuantity:Units currently in stock 
outOfStock:Boolean indicator of availability 


Tech Stack
Language: SQL (PostgreSQL compatible)

Tools: DBeaver / MySQL Workbench / pgAdmin

Skills: Data Cleaning, Aggregations, CTEs, Case Statements, Window Functions

Key Data Analysis Tasks
1. Data Cleaning & Exploration
Handled NULL values across critical columns like mrp and quantity.

Standardized column names for better readability (e.g., renaming dicountedsellingprice).

Conducted initial data profiling to count total records and unique categories.

2. Strategic Inventory Insights
Identified products with an MRP > 300 that are out of stock to highlight potential lost revenue.

Grouped inventory into 'Low', 'Medium', and 'Bulk' based on gram weight for optimized delivery routing.

3. Financial Analysis
Revenue Estimation: Summed discountedSellingPrice * availableQuantity grouped by category to identify top-performing segments.

Discount Optimization: Ranked top 5 categories by average discount percentage to assess promotional aggressiveness.

Sample SQL Queries
-- Calculate estimated revenue per category
SELECT category, 
       SUM(discountedsellingprice * availablequantity) AS total_revenue
FROM zepto
GROUP BY category
ORDER BY total_revenue DESC;

-- Inventory segmenting
SELECT name, weightingms,
CASE WHEN weightingms < 1000 THEN 'low'
     WHEN weightingms < 5000 THEN 'medium'
     ELSE 'bulk' END AS weight_category
FROM zepto;

Insights Summary:

Revenue Drivers: Higher estimated revenue is concentrated in staple categories such as "Cooking Essentials" and "Dairy".


Stock Risk: Several high-value items are frequently out of stock, suggesting a need for tighter supply chain integration for premium SKUs.


Promotion Impact: Categories like "Fruits & Vegetables" show high discount volatility, reflecting their perishable nature.
