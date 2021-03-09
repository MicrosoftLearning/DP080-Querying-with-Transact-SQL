
---
lab:
    title: 'Organize data'
    module: 'Module 5: Organize data with Transact-SQL'
---

# Lab: Organize data with Transact-SQL
 
In this exercise, you will use Azure Data Studio to connect to the _MyStore_ database and execute some queries that organize data by sorting and grouping.

## Connect to the lab environment

When the VM lab environment opens, select the  **Ctrl+Alt+Delete** button in the **Resources** tab to open the login screen. 
Select the password on the **Resources** tab for the **Administrator** account to populate the password field, and then select the arrow to sign in to Windows.

## Open Azure Data Studio

There is an icon in the toolbar to open Azure Data Studio. 

![Picture 1](../media/Module1-Unit6-picture1.png)

Select the icon for Azure Data Studio. The tool will open to a Welcome screen. If you get a message in the lower right corner asking if you want to enable **Preview features**, you can select either option. 

From the **File** menu, select **New Query**. You should now see a blank query window. 

## Execute simple joins

The queries will use a sample database called _MyStore_. Although there are about a dozen user tables in this database, we’ll only be working with a couple of them in this exercise. We’ll be using the _Orders_, _OrderDetails_ and _Customers_ tables. 

For the queries we are using, you can try typing them in directly or you can select File/Open File, and navigate to D:\Lab Code\Organize data. Double-click on the file script5.sql and it will be loaded into a new query window.

Remember that you can run an entire script at once, which will be multiple queries in this case. Or you can highlight a single query and select the **Run** button to execute just the highlighted query. 

## Use ORDER BY for sorting results

Write a SELECT statement to retrieve the custid and contactname columns from the Sales.Customers table and the orderid and orderdate columns from the Sales.Orders table. Filter the results to include only orders placed on or after '20210401', which is April 1, 2021 (filter the orderdate column), then sort the result by orderdate in descending order and custid in ascending order.

Your query should return 84 rows. 

You decide you want to give aliases to the column names so you write the following query:

```tsql
SELECT c.custid AS CustomerID, contactname AS ContactName, orderid AS OrderID, orderdate AS DateOfOrder
FROM Sales.Customers c JOIN Sales.Orders o
   ON c.custid = o.custid
WHERE DateOfOrder > 20210401'
ORDER BY DateOfOrder DESC, CustomerID;
```

If you execute the query above, you will get an error about an invalid column name. What is the problem? 

## Use the TOP option and OFFSET - FETCH to receive a subset of the rows

The sales department wants to have some additional reports that show the last invoiced orders and the top 15 percent of the least expensive products being sold.

Write a SELECT statement against the _Sales.Orders_ table, and retrieve the orderid and orderdate columns. Retrieve the 20 most recent orders, ordered by _orderdate_.

Use the OFFSET-FETCH clause to implement the same task: return the 20 most recent orders.

Write a SELECT statement to retrieve the _productname_ and _unitprice_ columns from the _Production.Products_ table. Note the number of rows returned. 

Modify the SELECT statement to include only the lowest 15 percent of the products based on the _unitprice_. (That is, the products with the lowest prices.) Again, note the number of rows returned.  

Modify the query to return the lowest 15 percent of the products based on _unitprice_, including all products with the same _unitprice_ value as the last one returned. 

Is it possible implement this task with the OFFSET-FETCH clause?

## Simple GROUP BY

The sales department wants to know which customers are placing the most orders. 

Write a query with GROUP BY to return a list of the _custid_ values and the number of orders each has placed. You should get 89 rows back. 

Enhance the previous query to return the rows in order, with the customer with the most orders being first in the output. 

##GROUP BY with Having

Enhance the previous query to only return the _custid_ values for customers placing more than 25 orders. You should get three rows back. 

To finish this exercise select **Done** below.

**Done**
