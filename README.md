# MeriSKILL-Sales-Data-Report

## Table of Contents
- [Project Overview](#project-overview)
- [Data Visualization](#data-visualization)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning/Preparation](#data-cleaningpreparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results/Findings](#resultsfindings)
- [Recommendations](#recommendations)
- [Limitations](#limitations)

### Project Overview

---
This project aims to analyze sales data to gain insights into the performance of the sales team and identify areas for improvement.  The report will be used to inform strategic decision-making and drive future sales growth.

### Data Visualization
---
![](MeriSKILL-Sales-Data-Report_Page-0001)
![](MeriSKILL-Sales-Data-Report_Page-0002)

### Data Sources
---
The primary source of data is Sales Data.csv, this is an open source data that can be freely downloaded from an open source.

### Tools
  - Microsoft Excel ***[Download here](https://www.microsoft.com/en-us/microsoft-365/excel)*** - Univariate Analysis
  - Power Query - Data Cleaning and Data Preparation
  - Microsoft PowerBI ***[Download here](https://powerbi.microsoft.com/en-us/downloads/)*** - Data Visualization
 
### Data Cleaning/Preparation
---
In the data preparation phase, we performed the following tasks:
1. Data loading and inspection
2. Handling missing values
3. Data cleaning and formatting

### Exploratory Data Analysis
---
EDA involved exploring the datasets to answer key questions such as:

- Total Orders
- Sum of Quantity Ordered
- Sum of Sales
- Total Products
- Total Cities
- Top 5 Prodcuts by Sales
- Bottom 5 Products by Sales
- Order and Sales by Month
- Sales by City
- Order and Sales by Day
- Top 5 Products by Quantity Ordered
- Bottom 5 Products by Quantity Ordered

### Data Analysis
---
Included below is some of the code I worked in order to acheive accurate results in my analyis

To derive the date columns for the analysis I used;

```F#
let
   #"Renamed Columns" = Table.RenameColumns(#"Changed Type",{{"Month", "MonthNumber"}}),
    #"Inserted Month Name" = Table.AddColumn(#"Renamed Columns", "Month Name", each Date.MonthName([Order Date]), type text),
    #"Inserted Day Name" = Table.AddColumn(#"Inserted Month Name", "Day Name", each Date.DayOfWeekName([Order Date]), type text),
    #"Inserted Day of Week" = Table.AddColumn(#"Inserted Day Name", "Day of Week", each Date.DayOfWeek([Order Date]), Int64.Type),
    #"Inserted Year" = Table.AddColumn(#"Inserted Day of Week", "Year", each Date.Year([Order Date]), Int64.Type),
    #"Inserted Hour" = Table.AddColumn(#"Inserted Year", "Hour.1", each Time.Hour([Order Date]), Int64.Type),
    #"Removed Columns" = Table.RemoveColumns(#"Inserted Hour",{"Hour.1"})
in
    #"Removed Columns"
```

### Results/Findings
---
The analysis results are summarized as follows;
1. The total number of orders identified is 178,437.
2. A total of 209,097 items were ordered.
3. Sales revenue totaled $34,492,035.97.
4. A total of 19 products were identified.
5. Our analysis identified a total of 9 distinct cities.
6. The Macbook Pro reigned supreme as the best-selling product, driving in a whopping $8,037,600 in sales. The iPhone followed closely behind at $4,794,300, showcasing Apple's dominance in the consumer electronics market. ThinkPad Laptops secured the third spot with $4,129,958.70 in sales.
7. AAA Batteries (4-pack) came in last place for sales, generating only $92,740.83. AA Batteries (4-pack) followed closely behind at $106,118.40. Wired Headphones, while exceeding sales of AAA batteries, still fell short with $246,478.43, suggesting a potential area for improvement.
8. Orders and sales reached their highest point in December, with 24,004 orders and $4,613,443.34 in sales revenue.
9. San Francisco emerged as the sales leader, generating a staggering $8,262,203.91. Los Angeles followed at a distant second with $5,452,570.80, and New York City came in third at $4,664,317.43.
10. Tuesdays emerged as the busiest day for sales, with both orders (26,063) and total revenue ($5,087,956.78) reaching their peak.
11. AAA Batteries (4-pack) reigned supreme in order volume, racking up a massive 31,017 orders. AA Batteries (4-pack) followed closely behind at 27,653 orders, while USB-C Charging Cables secured the third spot with 23,975 orders.
12. LG Dryer emerged as the slowest mover in terms of quantity ordered, with only 646 units sold. LG Washing Machine followed closely behind at 666 units, and Vareebadd Phone rounded out the bottom three with 2,068 units sold.

### Recommendations
---
- Focus on top performers: Recommend prioritizing resources for marketing, promotion, and ensuring sufficient stock for top-selling products.
- Analyze bottom performers: Investigate reasons behind low sales/quantity for bottom performers. Consider product improvements, targeted marketing campaigns, or potential removal from the product line.
- Identify sales trends: Based on trends in sales and orders, suggest strategies to manage inventory levels and avoid stockouts during peak demand periods.
- Target specific products/cities: Leverage insights from top-selling products and city-specific sales to develop targeted marketing campaigns in high-performing regions or for high-demand products.
- Analyze customer behavior: If possible, explore the possibility of including customer data in future analyses to understand demographics and buying patterns for more targeted marketing efforts.
- Promotional strategies: Analyze the impact of past promotions (if applicable) and suggest future promotional strategies based on sales trends and top-performing products.

### Limitations
---
- External Factors: The report may not account for external factors impacting sales, such as economic conditions, industry trends, or competitor activity.
- Customer Sentiment: Sales data doesn't capture customer sentiment or satisfaction, which can influence future buying decisions.
