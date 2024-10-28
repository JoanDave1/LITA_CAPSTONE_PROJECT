# LITA_CAPSTONE_PROJECT
## Introduction
This is the final project for the Ladies in Tech Africa(LITA)- Data Analysis Track. It contains two datasets (Sales Data and Customer Data) of which we are to conduct and visualize our analysis. The Sales data contains 50,000 records of sales transactions, including order ID, customer ID, product, region, order date, quantity ordered, unit price and total sales revenue. The Customer data contains information about 75,000+ customers and their subscription details for TV services, including customer ID, name, region, subscription type, subscription start and end dates, cancellation status and revenue generated. 

-----------
## Project 1
### Objectives
The purposes of this analysis is to: 
1. Calculate metrics such as average sales per product and total revenue by region.  
2. Retrieve the total sales for each product category. 
3. Find the number of sales transactions in each region. 
4. Find the highest-selling product by total sales value. 
5. Calculate total revenue per product. 
6. Calculate monthly sales totals for the current year. 
7. Find the top 5 customers by total purchase amount. 
8. Calculate the percentage of total sales contributed by each region. 
9. Identify products with no sales in the last quarter.  
10. Create a dashboard that visualizes insights generated.
    
Using pivot tables in Excel, SQL queries and Power BI, we aim to gain deeper understanding of the customer-sales dynamics and uncoveer insights that can inform business strategies to optimize revenue and customer satisfaction. 

-----------
### Methodology
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






