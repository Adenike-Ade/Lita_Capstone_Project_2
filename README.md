# Lita_Capstone_Project_2

### Project title: Customer data analysis

### Project Overview
---
This project aims to analyze customers'subscription data to extract valuable insights, identify trends, and optimize business decisions. The project utilizes Excel, SQL and Power BI data visualization techniques to provide a comprehensive understanding of sales performance such as total revenue, average subscription duration, Highest Subscription type according to region, Customer_ID, and more.

### Data Source
---
The data source is a Customer subscription data obtained from the Lita data class instructors/facilitator.

### Tools Used
---
- Microsoft Excel for Data Cleaning, Analysis and visualization.
- SQL (Structured Query Language) for Querying of Data
- Power Business Intelligence (Power BI) for Data cleaning, Analysis and Creation of Visuals
- GitHub for portfolio building.

### Data cleaning and preparation
---
The initial phase of this project cleaning, the following actions were taken
1. Data loading and inspection on each tool.
2. Removal of Duplicates, Handling missing variables, and changing Data types.
3. Data Transformation, Cleaning and Formatting.

### Exploring Data Analysis
---
In EDA, the Data was explored to  answer some questions such as 
1. Excel:
-  Analyze customer data using pivot tables to find subscription patterns.
-  Calculate the average subscription duration and identify the most popular 
subscription types.
-  Create any other interesting reports.
2. SQL:
Write queries to extract key insights based on the following questions. 
-  retrieve the total number of customers from each region.
- find the most popular subscription type by the number of customers.
- find customers who canceled their subscription within 6 months.
- calculate the average subscription duration for all customers.
- find customers with subscriptions longer than 12 months.
- calculate total revenue by subscription type.
- find the top 3 regions by subscription cancellations.
- find the total number of active and canceled subscriptions.
3. Power BI:
- Build a Power BI dashboard that visualizes key customer segments, cancellations, and subscription trends. Include slicers for interactive analysis.

### Data Analysis 
---
This is where excel functions, SQL queries and as well as lines of Codes used during the salesdata analysis are displayed.

``` SQL
SELECT * FROM [dbo].[LITA CAPSTONE CUSTOMERSDATA 1]

TOTAL NUMBER OF CUSTOMERS FROM EACH REGION

SELECT REGION,
COUNT(CustomerID) AS TOTALCUSTOMERS
FROM[dbo].[LITA CAPSTONE CUSTOMERSDATA 1]
GROUP BY Region

MOST POPULAR SUBSCRIPTION TYPE BY NUMBER OF CUSTOMERS

SELECT TOP 1 SUBSCRIPTIONTYPE,
COUNT(CustomerID) AS TOTALCUSTOMERS
FROM [dbo].[LITA CAPSTONE CUSTOMERSDATA 1]
GROUP BY SUBSCRIPTIONTYPE
Order BY TOTALCUSTOMERS DESC;

CUSTOMERS WHO CANCELLED SUBSCRIPTION BEFORE 6 MONTH

SELECT 
CustomerID, 
SUBSCRIPTIONTYPE,
SubscriptionEnd
from [dbo].[LITA CAPSTONE CUSTOMERSDATA 1]
where SubscriptionEnd<=DATEADD(month,6,subscriptionstart);

AVERAGE SUBSCRIPTION DURATION FOR ALL CUSTOMERS

SELECT
AVG(DATEDIFF(DAY,SubscriptionStart,SubscriptionEnd)) AS AVERAGE_DURATION_BY_DAYS
FROM [dbo].[LITA CAPSTONE CUSTOMERSDATA 1]

SELECT
AVG(DATEDIFF(MONTH,SubscriptionStart,SubscriptionEnd)) AS AVERAGE_DURATION_BY_NUMBER_OF_MONTHS
FROM [dbo].[LITA CAPSTONE CUSTOMERSDATA 1]

CUSTOMERS WITH SUBSCRIPTION LONGER THAN 12 MONTHS

SELECT 
customerID,
SUBSCRIPTIONTYPE,
SubscriptionStart,
SubscriptionEnd
from [dbo].[LITA CAPSTONE CUSTOMERSDATA 1]
where DATEDIFF(month,SubscriptionStart,SubscriptionEnd)>12;

TOTAL REVENUE BY SUBSCRIPTION TYPE

SELECT 
SUBSCRIPTIONTYPE,
SUM(REVENUE) AS TOTALREVENUE
FROM
[dbo].[LITA CAPSTONE CUSTOMERSDATA 1]
GROUP BY
SubscriptionType;

select 
sum(revenue) as total_revenue
from [dbo].[LITA CAPSTONE CUSTOMERSDATA 1];

TOP 3 REGIONS BY SUBSCRIPTION CANCELLATIOON

SELECT TOP 3 Region,
COUNT(canceled) as cancellation 
from [dbo].[LITA CAPSTONE CUSTOMERSDATA 1]
where canceled = 'true'
group by Region
order by cancellation DESC;

TOTAL ACTIVE AND CANCELED SUBSCRIPTION

SELECT 
SUM(CASE WHEN CANCELED = 'FALSE' THEN 1 ELSE 0 END) AS TOTALACTIVESUB,
SUM(CASE WHEN CANCELED = 'TRUE' THEN 0 ELSE 1 END) AS TOTALCANCELEDSUB
FROM [dbo].[LITA CAPSTONE CUSTOMERSDATA 1];
```

