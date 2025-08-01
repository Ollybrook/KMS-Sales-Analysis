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



To increase revenue from its ten least active customers, KMS should focus on personalized engagement strategies. Sending tailored email offers featuring special discounts or product bundles could help revive customer interest. Introducing loyalty programs or time-sensitive deals may also drive repeat business. By reviewing past purchase histories, KMS can suggest relevant products and identify reasons for low engagement through brief customer surveys. Offering more flexible payment and delivery options might further support customer retention. Through consistent, customized outreach and well-planned incentives, KMS can steadily grow these customers' value and strengthen loyalty across its entire customer base.


Determining the Highest shipping cost by shipping method

      Select Ship_Mode, Shipping_Cost
      From [KMS Sql Case Study]
      Order by Shipping_Cost Desc

      The Highest Cost Shipping Methoed is Delivery Truck.


      




<img width="953" height="403" alt="Image8" src="https://github.com/user-attachments/assets/bf5acff3-d093-4fc0-b86f-357dda846b8e" 


  Top 1


        Select Top 1 Ship_Mode, Shipping_Cost
      From [KMS Sql Case Study]
      Order by Shipping_Cost Desc


      

  


<img width="952" height="397" alt="Image9" src="https://github.com/user-attachments/assets/65b27408-a833-4cc4-8102-53d0a0f9eaf3" 


  The Most valuable Customers and the product or Services there purchase

  Top 10 most valuable Customer

              Select * from [KMS Sql Case Study]
            Select Top 10 Customer_Name, Product_Name, Sum(Sales) As Total_Spent
            From [KMS Sql Case Study]
            Group By Customer_Name, Product_Name
            Order By Total_Spent Desc




            

    

<img width="946" height="410" alt="Image10" src="https://github.com/user-attachments/assets/71d8574c-c3fa-42fb-b1b2-bca6e486e4d9" />


Small Business Customer with the highest Sales

Small Business Customer


          SELECT Top 1 Customer_Name, SUM(Sales) AS Total_sales
          FROM [KMS Sql Case Study]
          WHERE Customer_Segment = 'Small Business'
          GROUP BY Customer_Name
          ORDER BY Total_sales DESC





          
<img width="960" height="407" alt="Image12" src="https://github.com/user-attachments/assets/81788506-3ec9-4a9d-80ee-1381311e0ba7" />


Top 10 Small Business Customer


          SELECT Top 10 Customer_Name, SUM(Sales) AS Total_sales
          FROM [KMS Sql Case Study]
          WHERE Customer_Segment = 'Small Business'
          GROUP BY Customer_Name
          ORDER BY Total_sales DESC





          
<img width="948" height="403" alt="Image13" src="https://github.com/user-attachments/assets/037e4310-fda9-4b66-9fe5-50f7795ea235" />


Corporate customer with the most placed number of orders in 2009 - 2012

Top 1


         Select Top 1 Customer_Name, Count(Order_ID) As Total_Orders
          From [KMS Sql Case Study]
          WHERE Customer_Segment = 'Corporate'
          And Order_Date Between '2009-01-01' and '2012-12-31'
          Group By Customer_Name
          Order By Total_Orders Desc



          Top 1 Corporate Customer with the Highest Order is Adam Hart with 27 Orders.



          




          
<img width="958" height="406" alt="Image 14i" src="https://github.com/user-attachments/assets/2d1b3197-97e0-40dd-aa85-f493f316be9b" />



 Top 5 Corperate customer that placed the most number of orders in 2009 - 2012



           Select Top 5 Customer_Name, Count(Order_ID) As Total_Orders
          From [KMS Sql Case Study]
          WHERE Customer_Segment = 'Corporate'
          And Order_Date Between '2009-01-01' and '2012-12-31'
          Group By Customer_Name
          Order By Total_Orders Desc


           




          


          

<img width="958" height="404" alt="Image 15" src="https://github.com/user-attachments/assets/fdb69e84-b6fb-438c-9e75-9da5408bf126" />


 Most Profitable Consumer Customer


            SELECT Top 1 Customer_Name, SUM(Profit) AS total_profit
            FROM [KMS Sql Case Study]
            WHERE Customer_Segment = 'Consumer'
            GROUP BY Customer_Name
            ORDER BY total_profit DESC





            


         



<img width="960" height="419" alt="Image 16" src="https://github.com/user-attachments/assets/5abed65c-4b78-4299-ab02-2904e2883f15" />





5 Most Profitable Consumer Customer


            SELECT Top 5 Customer_Name, SUM(Profit) AS total_profit
            FROM [KMS Sql Case Study]
            WHERE Customer_Segment = 'Consumer'
            GROUP BY Customer_Name
            ORDER BY total_profit DESC




            
<img width="958" height="425" alt="Image 17" src="https://github.com/user-attachments/assets/1de7acac-4c4b-4c10-975f-689ee01a102b" />




Customer that returned items, and the segment they belong to


Joining the two tables (KMS Sql Case Study and Order_Status) to determine which customer returned items and from which Segment.


From the analysis, 419 Customers Actually returned their Goods.


            SELECT DISTINCT [KMS Sql Case Study].customer_name, [KMS Sql Case Study].customer_segment
            FROM [KMS Sql Case Study]
            JOIN Order_Status 
            ON [KMS Sql Case Study].Order_ID = Order_Status.Order_ID
            WHERE [Status] = 'Returned'





            
<img width="949" height="427" alt="Image 18" src="https://github.com/user-attachments/assets/3653d706-021a-4b1a-9e5f-f6ff65daaf87" />





If the delivery truck is the most economical but the slowest shipping method and Express Air is the fastest but the most expensive one, do you think the company appropriately spent shipping costs based on the Order Priority? Explain your answer




            SELECT 
                Order_Priority,
                Ship_Mode,
                SUM(Shipping_Cost) AS Total_Shipping_Cost
            FROM [KMS Sql Case Study]
            GROUP BY Order_Priority, Ship_Mode
            ORDER BY Order_Priority, Ship_Mode





            
<img width="947" height="423" alt="Image 19" src="https://github.com/user-attachments/assets/c85319fd-ea08-4322-8ce7-2147a4825792" />





An analysis of KMS’s shipping costs in relation to order priority reveals a lack of alignment between the company’s shipping methods and the urgency of its orders. Express Air—the fastest and most expensive option—was used not only for Critical and High priority orders but also for Low and unspecified ones, leading to unnecessary costs. Conversely, Delivery Truck, the slowest and most economical method, was sometimes chosen for Critical orders, risking delays in urgent deliveries. Although Regular Air was more evenly distributed across priorities, the overall pattern indicates the absence of a structured shipping policy based on order urgency. To enhance efficiency, Express Air should be reserved strictly for high-priority shipments, while Delivery Truck should be designated for low-priority deliveries. By aligning shipping methods with order urgency, KMS can cut costs significantly without affecting service quality. Implementing a rules-based shipping strategy would streamline logistics operations and boost overall profitability.







Conclusion





The analysis offered an in-depth overview of KMS’s sales trends, shipping effectiveness, and customer activity between 2009 and 2012. It highlighted key opportunities to improve logistics, strengthen relationships with high-value customers, and boost engagement among underperforming clients. By acting on the recommendations provided, KMS stands to greatly improve operational efficiency, elevate customer satisfaction, and drive profitability within the Abuja division and across other regions.





  **Contact:**


  https://github.com/Ollybrook

https://www.linkedin.com/in/olayiwola-agboola-483254333/




