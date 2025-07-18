# KMS-Sales-Analysis
Analysis of Kultra Mega Stores' order data (2009-2012) for strategic insights.").

Introduction/Overview

This project involves a comprehensive business intelligence analysis of Kultra Mega Stores' (KMS) order data from 2009 to 2012. As a Business Intelligence Analyst supporting the Abuja division, the goal is to extract key insights and findings to inform strategic decisions related to product categories, regional performance, customer segmentation, and shipping efficiency.
Problem Statement/Business Objective

**Business Context:** Kultra Mega Stores (KMS), headquartered in Lagos, specializes in office supplies and furniture, serving individual consumers, small businesses (retail), and large corporate clients (wholesale) across Lagos, Nigeria. The Abuja Business Manager requires data-driven insights from historical order data to optimize operations and revenue.

**Objective:** Analyze historical order data (2009-2012) to identify sales trends, customer behavior patterns, shipping cost efficiencies, and provide actionable recommendations for revenue growth and operational improvement in the Abuja division.
Dataset Description

**Dataset:** `kms_order_data.xlsx`
*Source:** The data for this project is gotten from Digital SkillUp African (DSA) Learning Management System as part of our final Project..
**Period:** 2009 - 2012.
**Content:** Contains information on orders, products (e.g., category), customers (e.g., segment), regions, sales figures, shipping costs, and order priority.
Analysis Tasks Performed (Case Scenarios)

Etl Process

Data Extraction
As stated above, the data for this analysis is gotten from Digital SkillUp African Learning Management System.

Data Transformation/Loading
The Data was transformed using SQL Server, changing inappropriate data types (converting Date from Strings back to Date and changing Order ID from Smallint to Int) due to the large volume of data and also replacing missing Values in Profit_Base_Margin Colum, Proft Column and Unit_Price Colum using queries.

Checking for null values in "PROFIT, PRODUCT BASE MARGIN and UNIT PRICE COLUMNS"

              select * from [KMS Sql Case Study]
              Where Product_Base_Margin Is NULL Or Profit is NULL Or
              Unit_Price is NULL

  After checking for Null Values in the above Columns, 153 Null Values were discovered in total. 72 from Profit Column, 63 from Profit Base Margin Column and 12 from Unit Price Column.



<img width="940" height="402" alt="Image1" src="https://github.com/user-attachments/assets/b5286832-be24-4275-bd0b-d3fe6bf7e846" />

Replacing the Null Values with Mean

              update [KMS Sql Case Study]
              Set Profit = 181.18
              where Profit is NULL
              
              update [KMS Sql Case Study]
              Set Unit_Price = 89.35
              where Unit_Price is NULL
              
              update [KMS Sql Case Study]
              Set Product_Base_Margin = 0.51
              where Product_Base_Margin is NULL

 Analysis Tasks Performed (Case Scenarios)

 **Analysis Tasks & Business Questions Addressed (Applying SQL Skills from DSA Data Analysis class):**

 Key Performance Indicators (KPIs)
Total Sales ₦ 14,915,600.83

Total Shippimg Cost ₦ 107,831.04

Total Profit ₦ 1,537,521.02

Total Discount ₦ 417.19

Total Unit Price ₦ 751442.43

Total Orders 8399

Total Product Base Margin ₦ 4,304.44

The following Queries wrere used in Extracting the above KPIs

              Select Sum(Sales) As Total_Sales,
              Count(Order_ID) As Total_Orders,
              Sum(Profit) As Total_Profit,
              Sum(Shipping_Cost) As Total_Shipping_Cost,
              Sum(Discount) As Total_Discount,
              Sum(Unit_Price) As Total_Unit_Price,
              Sum(Product_Base_Margin) As Toatl_Product_Base_Margin
              From [KMS Sql Case Study]






 
<img width="955" height="408" alt="Image2" src="https://github.com/user-attachments/assets/77413fd1-b0cc-4b90-9b96-12aa7ff8495c" />


 **Case Scenario I:**

Which product category had the highest sales?

              Select top 1 Product_Category, Sum(Sales) As TotalSales
              From [KMS Sql Case Study]
              Group By Product_Category
              Order By TotalSales Desc

The product category with the highest sales is Technology







              


<img width="938" height="404" alt="Image3" src="https://github.com/user-attachments/assets/b347703c-4dea-448d-9330-4f1943e728b8" />


What are the Top 3 and Bottom 3 regions in terms of sales?

 Top 3 Highest Sales Products

                 Select top 3 Product_Category, Sum(Sales) As TotalSales
                From [KMS Sql Case Study]
                Group By Product_Category
                Order By TotalSales Desc

 The Top 3 Highest Sales Products are; Technology, Furniture and Office Supplies





 





![Uploading Image4.png…]()

Bottom 3 Region by Sales

            Select top 3 Region, Sum(Sales) As TotalSales
            From [KMS Sql Case Study]
            Group By Region
            Order By TotalSales Asc

 The bottom 3 Region by sales are; Nunavut, Northwest Territories and Yukon, with Nunavut having the lowest.




 
<img width="938" height="399" alt="Image5" src="https://github.com/user-attachments/assets/dde3f01e-1a93-44ad-b309-4a828f9813bd" />


Determining the Total sales of appliances in Ontario

          Select Sum(Sales) As TotalSales
          From [KMS Sql Case Study]
          where Product_Category = 'Appliances'
          And Region = 'Ontario'

 They were no Sales of Appliances made in Ontario



 






        





        





<img width="950" height="406" alt="Image6i" src="https://github.com/user-attachments/assets/41cdd127-a1a4-4444-993e-99179bbba586" />


Determining the bottom 10 customers by Sales

        SELECT Top 10 customer_name, SUM(sales) AS total_sales
        FROM [KMS Sql Case Study]
        GROUP BY customer_name
        ORDER BY total_sales ASC




<img width="945" height="404" alt="Image7" src="https://github.com/user-attachments/assets/093beffb-ec85-4506-bac2-1eeb20009915" />






    

