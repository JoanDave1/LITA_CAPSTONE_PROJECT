# LITA_CAPSTONE_PROJECT 1
## Introduction
This is the first half of the final project for the Ladies in Tech Africa(LITA)- Data Analysis Track. We have a dataset containing Sales Data and Customer Data for TV subscription of which we are to conduct and visualize our analysis. For project 1, we will be working on the Sales data which contains 50,000 records of sales transactions, including order ID, customer ID, product, region, order date, quantity ordered, unit price and total sales revenue.

-----------
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
- *Data Cleaning*: I imported the dataset into Microsoft Excel. Afterwards, I proceeded to claen my dataset using the "Remove Duplicates" feature available on the "Data" tab to remove values occurring more than once. My dataset of about 50,000 records was reduced to 9,922 records of sales. There were no other errors present in this dataset. I noticed, however, that the dataset was missing a revenue column to show the revenue generated from each transaction at various dates. I proceeded to add a revenue column by using the "Product" function to multiply the Quantity(Units) column by the UnitPrice to get our Total Sales Revenue. The image below is a visualization of the columns I multiplied and the additional column added for the result.

![image](https://github.com/user-attachments/assets/c1421759-a714-4639-a890-912c8899c499)

- *Relevant Computations*: I calculated the average sales for each product as well as total revenue generated from each region. According to our analysis and from image 1 below, the product "gloves" has the highest number of quantity sold on the average. I also calculated the total revenue by region and from image 2 below, South region generates the highest number of revenue.

![image](https://github.com/user-attachments/assets/80d47b6f-3c15-4e4f-8b44-3dd9ed51b1eb)

![image](https://github.com/user-attachments/assets/61fb0bf2-37f4-40db-823d-3e4b7d949a89)



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
Power BI (BI meaning Business Intelligence) is a data visualization tool that allows users to connect to various data sources, create interactive visualizations and business intelligence dashboards. I made use of power bi to viaualize my data and extract meaningful insights. 

---------  

### 1.3 Results 
---------
