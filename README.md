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

**Analysis Tasks & Business Questions Addressed (Applying SQL Skills from DSA Data Analysis class):**
**Case Scenario I:**

Which product category had the highest sales?






    

