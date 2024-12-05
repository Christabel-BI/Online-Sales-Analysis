# Sales Performance Analysis with Power BI

## Table of Contents
- project overview
- Project Objectives
- Dataset Overview
- Key Research Problems
- Steps Used to Achieve the Analysis
- DAX Measures Created
- Visualizations and Insights
- How to Run the Project
- Conclusions

### Project overview
This project analyzes an online sales performance using Power BI, focusing on revenue generation, product category contributions, and average order value. It aims to uncover actionable insights that can drive strategic decision-making for businesses. The project leverages Power BI's powerful visualization and data modeling capabilities, along with DAX formulas for advanced calculations.


#### Link to the online Sales Performance dashboard (https://app.powerbi.com/links/KVqFPjguyA?ctid=ede29655-d097-42e4-bbb5-f38d427fbfb8&pbi_source=linkShare)

Key insights include:

- Identification of top-performing product categories.
- Analysis of revenue contribution by product categories and specific products.
- Calculation of Average Order Value (AOV) to understand customer purchasing behavior.
- Contribution analysis to highlight each category's impact on total revenue.
- Revenue growth rate by month.
#### Project Objectives
1. Evaluate sales performance across different product categories.
2. Analyze revenue contributions to identify high-performing and low-performing categories.
3. Calculate metrics like Average Order Value (AOV) to better understand customer behavior.
4. Provide actionable insights through interactive and dynamic dashboards.

#### Dataset Overview
Source: Kaggle data, 'online sales.csv'.
Data Fields:
- Transaction ID
- Product Name
- Product Category
- Total Revenue
- Date
- Units Sold
- Unit price
- Region
- Payment method

#### Key Research Problems
- What is the revenue contribution of each product category?
- Which product categories drive the most revenue?
- What is the total revenue from each region?
- What is the Average Order Value (AOV) across all orders?
- How does each product category contribute to total sales performance?
- What is the revenue growth rate by month?
- What is the payment method distribution?
- How can this data inform business decisions for resource allocation?

#### Steps Used to Achieve the Analysis
1. Data Preparation
- Imported the dataset into Power BI.
- Cleaned and transformed data using Power Query:
Removed duplicates.
Checked for missing or erroneous data.
Ensured data types were consistent (e.g., numerical, text, date).
2. Data Modeling
Established relationship between the table and date table created.
3. DAX Measures Creation
Created measures to perform calculations like total revenue, average order value, and category contributions. See DAX Measures Created for detailed formulas.
4. Dashboard Design
Built an interactive dashboard showcasing:
Total revenue by product category and product.
Average Order Value (AOV).
Category contribution as a percentage of total revenue.
Revenue growth by month.
Total units sold by Region
Top 5 performing products.
  
##### DAX Measures Created
1. Total Revenue
`Total Revenue = SUM('Online Sales Data'[Total Revenue])`
3. Average Order Value (AOV)
`AOV = DIVIDE(SUM('Online Sales Data'[Total Revenue]), DISTINCTCOUNT('Online Sales Data'[Transaction ID]))`
4. product Category Contribution
`Category Contribution = DIVIDE([Revenue by Product Category], [Total Revenue], 0)`
5. `Total Units Sold = SUM('Online Sales Data'[Units Sold])`
6. `Units Sold by Category = CALCULATE(SUM('Online Sales Data'[Units Sold]), ALLEXCEPT('Online Sales Data', 'Online Sales Data'[Product Category]))`
7. `Monthly Revenue = CALCULATE([Total Revenue], DATESMTD('DateTable'[Date]))`
8. `Quarterly Units Sold = CALCULATE([Total Units Sold], DATESQTD('DateTable'[Date]))`
9. `Revenue Growth Rate = DIVIDE(([Total Revenue] - CALCULATE([Total Revenue], PREVIOUSMONTH('DateTable'[Date]))), CALCULATE([Total Revenue], PREVIOUSMONTH('DateTable'[Date])))`
10. `Payment Method Percentage = DIVIDE([Total Revenue], CALCULATE([Total Revenue], ALL('Online Sales Data'[Payment Method])), 0)`
11. `Revenue by Region = CALCULATE([Total Revenue], ALLEXCEPT('Online Sales Data', 'Online Sales Data'[Region]))`
12. `Total Transactions = DISTINCTCOUNT('Online Sales Data'[Transaction ID])`


Visualizations and Insights
1. Revenue Contribution by Product Category
A bar chart was used to highlight the revenue contribution of each product category.
Insight: Electronics contributes the highest revenue, followed by Furniture.
2. Average Order Value (AOV)
A card visualization showed the overall AOV.
Insight: The AOV suggests customers typically spend around $X per order.
3. Top 5 Products by Revenue
A horizontal bar chart displayed the top-performing products.
Insight: Product A and Product B account for 40% of total sales.
4. Category Contribution
A donut chart was used to show the percentage share of each category in total revenue.
Insight: Electronics dominate with 45% of total revenue, indicating a strong demand in this category.


