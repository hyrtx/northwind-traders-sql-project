# Using SQL to Analyze Northwind Traders Data

## Business Understading

![Andy Lee Trader Image Unsplash](assets/andy-li-trader-unsplash.jpg)

### Project Objectives
The main objective of this project is to **carry out an comprehensive analysis of the sales data of the fictitious company Northwind Traders using SQL queries**. The aim is to extract valuable information that can support strategic business decisions.

This analysis will follow the **CRISP-DM methodology** to ensure a structured and effective approach.

### Business Questions
The analysis will address the following specific questions:

1. **Revenue Reports**
    - What was the **total revenue in 1997?**
    - What was the **monthly revenue growth** in 1997, and what was the **YTD (Year-To-Date) calculation**?
    - What was the **top 10 best-selling products** in terms of quantity and sales value?
2. **Customer Segmentation**
    - What is the **total amount each customer has paid** so far?
    - How can we **segment customers into 5 groups** based on the total amount paid?
    - Which customers are in **groups 3, 4 and 5** for targeted marketing campaigns?
    - Which **UK customers** have paid **more than $1000**?

### Expected Benefits
- **Enhanced Market Understanding**: Gain insights into which products perform best and which customers contribute the most to total revenue.
- **Targeted Marketing Strategies**: Identify customer segments for personalized offers and increased retention.
- **Sales Optimization**: Detect growth patterns and seasonality for strategic planning.
- **Support for Decision-Making**: Provide concrete data to support management and operational decisions.

## Data Understanding
This stage involves getting to know the data, such as the tables and column names, primary and foreign keys, relationships between tables and the data types in each table.

### Dataset Description
The **Northwind Traders database** is a sample dataset simulating the operations of a food import and export company. The database covers various operational and commercial aspects of the company, including:

- **Suppliers**: Information about suppliers and vendors.
- **Customers**: Data on customers who make purchases from Northwind.
- **Employees**: Details about the company's employees.
- **Products**: Detailed information on the products sold.
- **Shippers**: Details about the companies responsible for shipping the products.
- **Orders and Order Details**: Records of sales transactions between customers and the company.

The database consists of **14 tables**, which are interrelated to provide a comprehensive view of business operations.

![Northwind Traders Tables Schema](assets/northwind-er-diagram.png)

### Table Structure
Not all the data we have available in the Data Repository is important to the problem. At this stage, we will select the tables with the variables that really matter to answer the business questions.

We already have access to the database schema, but if we needed to, we could list them using the following query:

```sql
SELECT table_name
FROM information_schema.tables
WHERE 
	table_schema NOT IN ('information_schema', 'pg_catalog')
	AND table_type = 'BASE TABLE'
ORDER BY
	table_schema,
	table_name;
```

By inspecting the available schema, we were able to define the tables that we will use in the analysis:

1. **orders**
2. **order_details**
3. **products**
4. **customers**

Let's also check which columns are in each table of interest through the query:

```sql
SELECT 
	table_name,
	column_name,
	data_type,
	is_nullable,
	column_default
FROM information_schema.columns
WHERE 
	table_schema NOT IN ('information_schema', 'pg_catalog')
	AND table_name IN ('orders', 'order_details', 'products', 'customers')
ORDER BY 
	table_name,
	ordinal_position;
```

The `is_nullable` column allows us to check which variables accept `NULL` values. From this, we were able to generate some valuable information about the tables:

- **orders**
    - With the exception of `order_id`, all the other columns are nullable. This is very dangerous, because it means that we can have an order without any information other than the id.
- **order_details**
    - There is no column that accepts `NULL` values in the table. 
- **products**
    - Neither `product_id` nor `product-name` accept `NULL` values.
    - The `unit_price` column can have `NULL` values, which is strange since this type of information it's usually mandatory.
- **customers**
    - All the columns except for `customer_id` and `company_name` accept `NULL` values.
    - Since the `country` column accepts `NULL` values, we have to be cautious because one of the business questions involves a geographical filter.

### Data Quality
Before proceeding with the analysis, an assessment of data quality will be conducted to identify and address potential issues.

#### Identifying and removing duplicate records
#### Checking for for fields with missing or incomplete information.
#### Standardize the data

## Data Preparation
### Data Extraction and Loading
### Data Cleaning
### Data Transformation and Integration
## Modeling
### SQL Query Strategies
### Query Details
## Evaluation
### Result Validation
### Insights Analysis
## Deployment
### Presentation of Results
### Business Recomendations
## Conclusion
## Appendices
# northwind-traders-sql-project
