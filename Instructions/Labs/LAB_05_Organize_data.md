
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

You get a error about an invalid column name. What is the problem? 

## Use the TOP option in the SELECT list

The sales department wants to have some additional reports that show the last invoiced orders and the top 10 percent of the most expensive products being sold.

Write a SELECT statement against the Sales.Orders table, and retrieve the orderid and orderdate columns. Retrieve the 20 most recent orders, ordered by orderdate.
3.	Execute the written statement and compare the results that you achieved with the recommended result shown in the file 72 - Lab Exercise 3 - Task 1 Result.txt.
  Task 2: Use the OFFSET-FETCH Clause to Implement the Same Task
1.	Write a SELECT statement to retrieve the same result as in task 1, but use the OFFSET-FETCH clause.
2.	Execute the written statement and compare the results that you achieved with the results from task 1.
3.	Compare the results that you achieved with the recommended result shown in the file 73 - Lab Exercise 3 - Task 2 Result.txt.
  Task 3: Write a SELECT Statement to Retrieve the Most Expensive Products
1.	Write a SELECT statement to retrieve the productname and unitprice columns from the Production.Products table.
2.	Execute the T-SQL statement and notice the number of the rows returned.
3.	Modify the SELECT statement to include only the top 10 percent of products based on unitprice ordering.
4.	Execute the written statement and compare the results that you achieved with the recommended result shown in the file 74 - Lab Exercise 3 - Task 3 Result.txt. Notice the number of rows returned.
5.	Is it possible to implement this task with the OFFSET-FETCH clause?

Simple group by

GROUP BY with Having



**Done**
