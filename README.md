# LITA_CAPSTONE_PROJECT
## Introduction
This is the final project for the Ladies in Tech Africa(LITA)- Data Analysis Track. It contains two datasets (Sales Data and Customer Data) of which we are to conduct and visualize our analysis. The Sales data contains 50,000 records of sales transactions, including order ID, customer ID, product, region, order date, quantity ordered, unit price and total sales revenue. The Customer data contains information about 75,000+ customers and their subscription details for TV services, including customer ID, name, region, subscription type, subscription start and end dates, cancellation status and revenue generated. 

-----------
## Project 1
### 1.1 Objectives
The purposes of this analysis is to: 
1. Calculate metrics such as average sales per product and total revenue by region.  
2. Retrieve the total sales for each product category. 
3. Find the number of sales transactions in each region. 
4. Find the highest-selling product by total sales value. 
5. Calculate total revenue per product. 
6. Calculate monthly sales totals for the current year. 
7. Calculate the percentage of total sales contributed by each region. 
8. Identify products with no sales in the last quarter.  
9. Create a dashboard that visualizes insights generated.
    
Using pivot tables in Excel, SQL queries and Power BI, we aim to gain deeper understanding of the customer-sales dynamics and uncoveer insights that can inform business strategies to optimize revenue and customer satisfaction. 

-----------
### 1.2 Methodology
#### Microsoft Excel: 
- *Data Source*: This dataset was provided by the facilitators of Ladies in Tech Africa(LITA) for Data Analysis track.
- *Data Cleaning*: I imported the dataset into Microsoft Excel. Afterwards, I proceeded to claen my dataset using the "Remove Duplicates" feature available on the "Data" tab to remove values occurring more than once. My dataset of about 50,000 records was reduced to 9,922 records of sales. There were no other errors present in this dataset. I noticed, however, that the dataset was missing a revenue column to show the revenue generated from each transaction at various dates. I proceeded to add a revenue column by using the "Product" function to multiply the Quantity(Units) column by the UnitPrice to get our Total Sale Revenue.
- *Relevant Computations*: I calculated the average sales for each product as well as total revenue generated from each region. According to our analysis, the product "gloves" has the highest number of quantity sold on the average.

#### SQL(Structure Query Language):
Using SQL queries, I made relevant computations in order to understand product sales performance. 

- Total sales per product: I computed this using the following SQL query
  
      SELECT Product, SUM(Quantity_Units) AS Quantity_Per_Product
  
      FROM SalesData
  
      GROUP BY Product
  
      ORDER BY Quantity_Per_Product desc
  
- Number of sales transactions in each region
  
      SELECT Region, COUNT(Quantity_Units) AS Quantity_Per_Region
  
      FROM SalesData
  
      GROUP BY Region
  
      ORDER BY Quantity_Per_Region
  
- Highest selling product by total sales revenue
  
      SELECT TOP 1 Product, SUM(Total_Sales_USD) AS Top_Performing_Product
  
      FROM SalesData
  
      GROUP BY Product
  
      ORDER BY Top_Performing_Product

- Total revenue per product

      SELECT Product, SUM(Total_Sales_USD) AS Total_Sales_Per_Product

      FROM SalesData

      GROUP BY Product

      ORDER BY Total_Sales_Per_Product

- Monthly Sales Total for the current year

      SELECT DATEPART(month,OrderDate) AS month,
  
      SUM(Total_Sales_USD) AS Monthly_Sales
  
      FROM SalesData
  
      WHERE DATEPART (year, OrderDate) = '2023'
  
      GROUP BY DATEPART(month, OrderDate)
  
      ORDER BY month
     
- Percentage of total sales by each region

      SELECT Region,

      SUM(Total_Sales_USD) AS regional_sales,

      SUM(Total_Sales_USD) * 100.0/

      SUM(SUM(Total_Sales_USD)) OVER () AS Percentage_of_Total_Sales

      FROM SalesData

      GROUP BY Region

      ORDER BY regional_sales desc

- Products with no sales in the last quarter

      SELECT DISTINCT PRODUCT

      FROM SalesData

      WHERE Product NOT IN (SELECT Product FROM SalesData

      WHERE OrderDate >= DATEADD(month, -3, GETDATE())

      )
  
#### Power BI: 
---------  

### 1.3 Results 
---------

## Project 2
### 2.1 Objectives 

The purpose of this analysis is to:

1. Calculate the average subscription duration and identify the most popular subscription types.   
2. retrieve the total number of customers from each region. 
3. find the most popular subscription type by the number of customers. 
4. find customers who canceled their subscription within 6 months. 
5. calculate the average subscription duration for all customers. 
6. find customers with subscriptions longer than 12 months. 
7. calculate total revenue by subscription type. 
8. find the top 3 regions by subscription cancellations. 
9. find the total number of active and canceled subscriptions.

### 2.2 Methodology
#### Microsoft Excel: 
- *Data Source*: This dataset was provided by the facilitators of Ladies in Tech Africa(LITA) for Data Analysis track.
- *Data Cleaning*: I imported the dataset into Microsoft Excel. Afterwards, I proceeded to claen my dataset using the "Remove Duplicates" feature available on the "Data" tab to remove values occurring more than once. My dataset of about 75,000+ records was reduced to 33,788 records of sales. There were no other errors present in this dataset. 
- *Relevant Computations*: Using pivot tables, I was able to identify the popular subscriptions based on the number of customers ans revenue generated as well as the cancellation of each subscription type based on total number of customers.

#### SQL











