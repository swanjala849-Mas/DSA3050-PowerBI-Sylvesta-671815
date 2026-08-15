# DSA3050-PowerBI-Sylvesta-671815
## Global Superstore Business Intelligence & Data Visualization
- Student Name: Sylvesta Wanjala
- Registration Number: 671815
- Course: DSA 3050A – Business Intelligence & Data Visualization
- Software: Microsoft Power BI Desktop
- Dataset: Global Superstore Dataset
- Dataset Source: Kaggle – Global Superstore Dataset
## Project Overview
The project follows the complete Business Intelligence development process from raw data acquisition and preparation to data modelling, DAX calculations, dashboard development, business insights and recommendations. The objective is to transform transactional Superstore data into an analytical solution that enables users to understand sales performance, profitability, customer behaviour, product performance, regional performance and trends over time.
###  Dataset Source
The dataset was obtained from Kaggle: https://www.kaggle.com/datasets/apoorvaappz/global-super-store-dataset

Global Superstore Dataset contains transactional information relating to orders, customers, products, sales, profit, discounts, shipping and geographical locations.
## Business Problem
Management needs to determine which products, customer segments and geographical regions contribute most to business performance, while also identifying areas where profitability is weak. The analysis also investigates sales trends over time and relationships between important business variables such as sales, quantity, profit and discounts. The Power BI solution is therefore designed to transform raw transactional data into actionable information that can support better business decision-making.
## Power Query – Data Cleaning & Transformation
- Correct data types 
- Removing unnecessary columns – Three redundant or uninformative columns—Postal Code (entirely empty), State (captured by City),—were removed to streamline the dataset. 
- Handle missing values - Missing values were identified and handled where appropriate. Missing values can affect calculations and produce incomplete or misleading analysis.
- Clean text fields 
- Date extraction - These fields will allow us to analyse, yearly sale, quartely performance, monthly trends and seasonal patterns 
- Custom column 
- Dimension preparations Reference queries were used to create dimension tables including: DimCustomer, DimProduct, DimLocation
and DimDate. Dimension tables separate descriptive information from transactional information and support a Star Schema.
- Group by A reference query called Region Summary was created and records were grouped by Region. The grouped query calculated: Total Sales and Total Profit. Grouping allows regional performance to be summarized and compared.
- Remove duplicates 
- Column profiling to check the quality of data

## Data Model
A Star Schema was developed for the Power BI solution.
### Fact Table
It contains transactional information including measures and attributes such as:
- Order ID
- Order Date
- Customer ID
- Product ID
- Sales
- Profit
- Quantity
- Discount
- Shipping Cost

### Dimension Tables
#### DimDate
DimDate provides the time dimension for analysing transactions by:
- Date
- Year
- Quarter
- Month
- Month Name

### DimCustomer
DimCustomer provides customer-related descriptive information including:
- Customer ID
- Customer Name
- Segment

### DimProduct
DimProduct provides product-related descriptive information including:
- Product ID
- Product Name
- Category
- Sub-Category

### DimLocation
DimLocation provides geographical information including:
- Country
- Region
- State
- City

### Model
<img width="1366" height="768" alt="Modelling" src="https://github.com/user-attachments/assets/f433fdb8-31d7-41d6-8f3d-90cd94005cbe" />

## DAX Measures
- Total Sales = SUM(FactSales[Sales])
- Total Profit = SUM(FactSales[Profit])
- Total Quantity = SUM(FactSales[Quantity])
- Total Orders = DISTINCTCOUNT(FactSales[Order ID])
- Total Customers = DISTINCTCOUNT(FactSales[Customer ID])
- Average Order Value = DIVIDE( [Total Sales], [Total Orders], 0 )
- Profit Margin % = DIVIDE( [Total Profit], [Total Sales], 0 )
- Average Discount = AVERAGE(FactSales[Discount])
- Previous Year Sales = CALCULATE( [Total Sales], SAMEPERIODLASTYEAR(DimDate[Date]) )
- YoY Sales Growth % = DIVIDE( [Total Sales] - [Previous Year Sales], [Previous Year Sales], 0 )
- Region Sales Rank = RANKX( ALL(DimLocation[Region]), [Total Sales], , DESC, DENSE )
- Profitability Status = SWITCH( TRUE(), [Profit Margin %] >= 0.20, "Highly Profitable", [Profit Margin %] >= 0.10, "Profitable", [Profit Margin %] > 0, "Low Profit", "Loss" )

<img width="1366" height="768" alt="DAX measures" src="https://github.com/user-attachments/assets/9d74692d-3c56-4290-9781-61e220f9501c" />

## Dashboard Design
### Page 1 — Executive Performance Overview
<img width="1366" height="686" alt="Executive Overview" src="https://github.com/user-attachments/assets/966a5565-2511-41b6-8a4f-8c0bfc42da54" />

### Page 2 — Product & Customer Analysis
<img width="1366" height="683" alt="Product and Customer Analysis" src="https://github.com/user-attachments/assets/f35827e0-297e-4471-ac92-aabc22d5f2c4" />

### Page 3 — Profitability & Discount Analysis
<img width="1366" height="690" alt="Profitability and Discount Analysis" src="https://github.com/user-attachments/assets/95b6c119-5c55-4eba-8d49-36bb29cec08b" />

## Key Business Insights
Insight 1 — Sales and Profit Performance
- Sales provide an indication of revenue generation, but profit provides a stronger indication of the financial value generated by different business areas. Comparing Sales and Profit helps identify areas where high sales do not necessarily translate into high profitability.

Insight 2 — Regional Performance
- Regional analysis allows management to identify which geographical markets contribute strongly to sales and profit and which regions may require additional attention.

Insight 3 — Product Profitability
- Product and sub-category analysis helps identify products that generate strong sales as well as products that contribute relatively low or negative profit.

Insight 4 — Customer Performance
- Customer analysis identifies the customers and customer segments that contribute significantly to sales, orders and profitability.

Insight 5 — Sales and Profit Relationship
- The scatter plot comparing Sales and Profit helps identify whether high-performing product areas in terms of sales are also financially profitable.

Insight 6 — Discount and Profitability
- Discount analysis provides a basis for investigating whether aggressive discounting may be associated with weaker profitability in particular product areas.

## Business Recommendations
1. Focus on profitable products

Management should identify products and sub-categories that generate strong profit and consider strategies for increasing their contribution to overall performance.

2. Review low-profit areas

Products or regions with high sales but weak profitability should be investigated to determine whether discounts, costs or pricing strategies are reducing profit.

3. Improve discount management

Discount strategies should be reviewed to ensure that increased sales volume does not result in disproportionately lower profit margins.

4. Strengthen high-performing customer segments

The business should maintain strong relationships with customer segments that generate significant sales, orders and profit.

5. Monitor regional performance

Regional performance should be monitored regularly so that resources can be directed toward markets with strong potential while weaker areas are investigated.

6. Use time-based monitoring

Management should monitor sales growth and year-over-year performance to identify positive trends and potential periods of declining performance.


## Conclusion
The Global Superstore Business Intelligence project demonstrates the transformation of raw transactional data into an interactive analytical solution using Microsoft Power BI. Power Query was used to clean and transform the dataset, while dimension tables and a fact table were developed to create an analytical model. DAX measures were then created to calculate important business KPIs and advanced analytical metrics. The three dashboard pages provide management with a progression from overall performance to detailed product and customer analysis and finally to advanced profitability analysis. The solution demonstrates how Business Intelligence can transform transactional data into meaningful information that supports business performance evaluation and decision-making.
