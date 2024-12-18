# Sales Performance Analysis with Power BI

## Table of Contents
- Project Overview
- Project Objectives
- Dataset Overview
- [Key Research Problems](#key-research-problems)
- Steps Used to Achieve the Analysis
- [DAX Measures Created](#dax-measures-created)
- [Visualizations and Insights](#visualizations-and-insights)
- [Recommendations](#recommendations)
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
### Project Objectives
1. Evaluate sales performance across different product categories.
2. Analyze revenue contributions to identify high-performing and low-performing categories.
3. Calculate metrics like Average Order Value (AOV) to better understand customer behavior.
4. Provide actionable insights through interactive and dynamic dashboards.

### Dataset Overview
Source: Kaggle data, 'online sales data.csv'.
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

### Key Research Problems
- What is the revenue contribution of each product category?
- Which product categories drive the most revenue?
- What is the total revenue from each region?
- What is the Average Order Value (AOV) across all orders?
- How does each product category contribute to total sales performance?
- What is the revenue growth rate by month?
- What is the payment method distribution?
- How can this data inform business decisions for resource allocation?

### Steps Used to Achieve the Analysis
1. Data Preparation
- Imported the dataset into Power BI.
- Cleaned and transformed data using Power Query:
Removed duplicates.
- Checked for missing or erroneous data.
- Ensured data types were consistent (e.g., numerical, text, date).
2. Data Modeling
- Established relationship between the table and date table created.
3. DAX Measures Creation
- Created measures to perform calculations like total revenue, average order value, and category contributions. See DAX Measures Created for detailed formulas.
4. Dashboard Design
Built an interactive dashboard showcasing:
Total revenue by product category and product.
Average Order Value (AOV).
Category contribution as a percentage of total revenue.
Revenue growth by month.
Total units sold by Region
Top 5 performing products.
  
### DAX Measures Created
1. Total Revenue
`Total Revenue = SUM('Online Sales Data'[Total Revenue])`
3. Average Order Value (AOV)
`AOV = DIVIDE(SUM('Online Sales Data'[Total Revenue]), DISTINCTCOUNT('Online Sales Data'[Transaction ID]))`
4. product Category Contribution
`Category Contribution = DIVIDE([Revenue by Product Category], [Total Revenue], 0)`
5. Total Units Sold = `SUM('Online Sales Data'[Units Sold])`
6. Units Sold by Category = `CALCULATE(SUM('Online Sales Data'[Units Sold]), ALLEXCEPT('Online Sales Data', 'Online Sales Data'[Product Category]))`
7. Monthly Revenue = `CALCULATE([Total Revenue], DATESMTD('DateTable'[Date]))`
8. Quarterly Units Sold = `CALCULATE([Total Units Sold], DATESQTD('DateTable'[Date]))`
9. Revenue Growth Rate = `DIVIDE(([Total Revenue] - CALCULATE([Total Revenue], PREVIOUSMONTH('DateTable'[Date]))), CALCULATE([Total Revenue], PREVIOUSMONTH('DateTable'[Date])))`
10. Payment Method Percentage = `DIVIDE([Total Revenue], CALCULATE([Total Revenue], ALL('Online Sales Data'[Payment Method])), 0)`
11. Revenue by Region = `CALCULATE([Total Revenue], ALLEXCEPT('Online Sales Data', 'Online Sales Data'[Region]))`
12. Total Transactions = `DISTINCTCOUNT('Online Sales Data'[Transaction ID])`

### Visualizations and Insights
1. Revenue Contribution by Product Category
A bar chart was used to highlight the revenue contribution of each product category.
Insight: Electronics contributes the highest revenue, followed by Home appliances. This indicates a strong demand in these categories.
2. Average Order Value (AOV)
A card visualization showed the overall AOV.
Insight: The AOV suggests customers typically spend around $335.70 per order.
3. A horizontal bar chart displayed the Total Units sold by product category.
Insight: Clothing followed by books and sports accounts for the highest Total units sold.
4. Top 5 Products by units sold
A horizontal bar chart displayed the top-performing products.
Insight: Product Nike Air force accounts for the highest units sold.
5. Category Contribution
A donut chart was used to show the percentage share of each Area in total revenue.
Insight: North America dominate with 45.73% of total revenue which is $36,800, indicating a strong demand from this Area.
6. Revenue Growth Rate by Month.
A line chart dispalyed the revenue growth by month.
Insight: Sales experienced a sharp decline from March and continued to May.
7. A donut chart was used to show the distribution of payment method.
Insight: Credit card accounts for 63.5% 0f the total payment method. This indicates that customers pay mostly with credit card.
8. Total units sold by region
A horizontal bar chart was used to display the total units sold by area
Insight: Asia accounts for 233 Total units sold followed by North America which is 180 units.
This indicates that customers from Asia buy more of clothing and Sports product category's

![Online Sales Dashboard](https://github.com/user-attachments/assets/92943b98-e69e-44ac-b17e-ff85eaeaec82)


### Recommendations
1. Focus on High-Performing Product Categories
- Inventory Management: Ensure adequate stock levels of high-performing categories such as Electronics and Home appliances to avoid stockouts.
- Marketing: Allocate a larger portion of the marketing budget to promote these categories.
- Pricing Strategies: Experiment with pricing strategies for high-performing categories to maximize revenue while retaining competitiveness.
2. Address Low-Performing Product Categories
- Customer Research: Conduct surveys or analyze customer feedback to understand why these categories underperform.
- Cross-Promotions: Bundle low-performing categories with high-performing ones to boost sales.
- Seasonality Analysis: Check if sales for these categories are seasonal and adjust inventory and promotions accordingly.
3. Optimize for Average Order Value (AOV)
- Upselling and Cross-Selling: Use recommendation engines to suggest complementary products during checkout to increase AOV.
- Free Shipping Thresholds: Introduce free shipping for orders above a certain value to encourage larger purchases.
- Loyalty Programs: Offer rewards or discounts for customers who reach higher spending thresholds.

### Conclusions
This analysis provides a comprehensive understanding of online sales performance, highlighting areas of strength and opportunities for improvement. 
It equips stakeholders with the insights needed to optimize product strategies and allocate resources effectively.




