# Cleaning Sales data for E-Commerce Insight

## Table of Content 

- [Overview](#overview)
- [Dataset Information](#dataset-information)
- [Technologies Used](#technologies-used)
- [Objectives](#objectives)
- [Process](#process)

## Overview
 This project demonstrates the process of cleaning and preparing raw sales data using SQL. The primary goal was to ensure the dataset was accurate, consistent, and ready for further analysis or visualization.

## Dataset Information
## Dataset Name: 
 [Sales_data_2] I used a mock sales dataset generated from Mockaroo to simulate real-world challenges.
## Dataset Description: 
 The dataset contains sales records, including product names, customer name, sales amounts, sale dates, transaction id and customer email.
## Dataset Size: 
 1000 rows, 7 columns.
## Initial Condition: 
 Messy data with missing values, duplicate entries, inconsistent formats, and unstandardized categories.

## Technologies Used
- SQL: For data cleaning and manipulation.
- DBMS: MySQL.


## Objectives
- Identify and handle missing or null values.
- Remove duplicates to ensure data integrity.
- Standardize and format product categories, dates, and regions.
- Clean and organize the data for seamless analysis.

## Process
- Step 1: Inspecting the Data
Performed an initial exploration to identify missing values, inconsistencies, and duplicates.
Used SQL queries like SELECT, COUNT, and GROUP BY to assess data quality.
- Step 2: Handling Missing Values
Replaced null values in key columns using appropriate methods .
- Step 3: Removing Duplicates
Used DISTINCT and DELETE queries to remove duplicate rows.
- Step 4: Standardizing Data
Ensured consistent formatting of product categories and regions (e.g., lowercase or title case).
Reformatted dates into a standard format (e.g., YYYY-MM-DD).
- Step 5: Verifying Cleaned Data
Ran queries to confirm all cleaning tasks were completed successfully.

```SQL
WITH RankedProducts AS(
	SELECT
		transaction_ID TD,
		product_name,
        ROW_NUMBER() OVER(PARTITION BY product_name ORDER BY TD) AS row_num
	)
    SELECT TD, product_name
	FROM RankedProducts
    WHERE row_num = 1
	ORDER BY TD;
```
## Results
- All missing values were addressed appropriately.
- Duplicates were removed, reducing dataset size by 10%.
- Product categories, dates, and regions were standardized for consistency.
- The cleaned dataset is ready for further analysis or visualization.

![sql clean data](https://github.com/user-attachments/assets/eb052f73-cbf3-4b19-9418-be2815b651d3)

## Challenges Encountered
- Handling a high number of null values in the customer_name column and customer_email.
- Standardizing categories with slight spelling variations (e.g., "MILK" vs. "Milk").

## Future Work
1. Perform Exploratory Data Analysis (EDA) on the cleaned dataset.
2. Visualize sales trends using Power BI or Tableau.
3. Use the dataset for predictive modeling (e.g., forecasting sales).






