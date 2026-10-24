# Consumer-Electronics-Sales-PowerBI

A 3-page Power BI report that shows which years, employees, products and states drive revenue for a consumer electronics business (2018 to 2022).

## Business questions
- How much revenue did each employee earn, by year and quarter?
- Which states, employees, products and categories are best and worst?
- What is driving revenue up or down?

## Report pages
1. **Key Data Points and Employee Performance:** KPI cards, plus Year, Quarter and Employee slicers.
2. **Top-Bottom Items:** Top 5 and Bottom 5 states, employees, products and categories by year.
3. **AI Visuals:** Key influencers, decomposition tree and smart narrative.

## Data model
Star schema. **Sales Data** is the fact table. It links one-to-many to four lookup tables:
Transaction Data, Product Data, Customer_Profile_Data, Sales_Employee_Data.

- 5 years of data, 96 employees, 84 products, 21 categories, 49 states
- Rows in Sales Data: [add count]

## DAX
```dax
Unit_Price = LOOKUPVALUE('Product Data'[Unit Price],
    'Product Data'[Product ID], 'Sales Data'[Product_ID])

Total_Revenue = [Quantity] * [Unit_Price]
    - ([Quantity] * [Unit_Price] * [Discount] / 100)
```
KPI cards and charts use Power BI aggregations: Sum of Total_Revenue, Sum of Quantity, and counts of employees, states, products and categories.

## Key insights
- Total revenue: 26.9M, steady at about 5.3M to 5.5M a year
- Q4 has the highest average revenue per order line
- PCMaster is the strongest product
- California leads states in 2018 (0.72M); Vermont is lowest (2.6K)

## Tools
Power BI Desktop, DAX

## Author
Umesh Sakpal | umeshsakpal14@gmail.com
