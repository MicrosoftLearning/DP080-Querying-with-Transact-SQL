
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

Write a SELECT statement to retrieve the custid and contactname columns from the Sales.Customers table and the orderid and orderdate columns from the Sales.Orders table. Filter the results to include only orders placed on or after '20210401', which is April 1, 2021 (filter the orderdate column), then sort the result by orderdate in descending order and custid in ascending order.

You decide you want to give aliases to the column names so you write the following query:


Need group by examples! 
3.	Execute the written statement and compare the results that you achieved with the desired results shown in the file D:\Labfiles\Lab05\Solution\62 - Lab Exercise 2 - Task 1 Result.txt.
  Task 2: Apply the Needed Changes and Execute the T-SQL Statement
1.	Someone took your T-SQL statement from lab 4 and added the following WHERE clause:
SELECT
e.empid, e.lastname, e.firstname, e.title, e.mgrid,
m.lastname AS mgrlastname, m.firstname AS mgrfirstname
FROM HR.Employees AS e
INNER JOIN HR.Employees AS m ON e.mgrid = m.empid
WHERE mgrlastname = 'Buck';

2.	Execute the query exactly as written inside a query window and observe the result.
3.	There is an error. What is the error message? Why do you think this happened? (Tip: Remember the logical processing order of the query.)
4.	Apply the needed changes to the SELECT statement so that it will run without an error. Test the changes by executing the T-SQL statement.
5.	Observe and compare the results that you achieved with the recommended results shown in the D:\Labfiles\Lab05\Solution\63 - Lab Exercise 2 - Task 2 Result.txt. 
  Task 3: Order the Result by the firstname Column
1.	Copy the existing T-SQL statement from task 2 and modify it so that the result will return all employees and be ordered by the manager’s first name. First, try to use the source column name, and then the alias column name.
2.	Execute the written statement and compare the results that you achieved with the recommended results shown in the file D:\Labfiles\Lab05\Solution\64 - Lab Exercise 2 - Task 3a and 3b Result.txt.
3.	Why were you able to use a source column or alias column name? 

Results: After this exercise, you should know how to use an ORDER BY clause.
Exercise 3: Write Queries that Filter Data Using the TOP Option
Scenario
The sales department wants to have some additional reports that show the last invoiced orders and the top 10 percent of the most expensive products being sold.
The main tasks for this exercise are as follows:
1. Writing Queries That Filter Data Using the TOP Clause
2. Use the OFFSET-FETCH Clause to Implement the Same Task
3. Write a SELECT Statement to Retrieve the Most Expensive Products
  Task 1: Writing Queries That Filter Data Using the TOP Clause
1.	Open the T-SQL script 71 - Lab Exercise 3.sql. Ensure that you are connected to the TSQL database.
2.	Write a SELECT statement against the Sales.Orders table, and retrieve the orderid and orderdate columns. Retrieve the 20 most recent orders, ordered by orderdate.
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
