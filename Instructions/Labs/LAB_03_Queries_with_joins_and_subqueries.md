-
lab:
    title: 'Write queries with joins and subqueries'
    module: 'Module 3: Query multiple tables in Transact-SQL'
---

# Lab: Write queries with joins and subqueries
 
In this exercise, you will use Azure Data Studio to connect to the _MyStore_ database and execute some queries that combine multiple tables.

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

For the queries we are using, you can try typing them in directly or you can select File/Open File, and navigate to D:\Lab Code\Multiple Tables. Double-click on the file script3.sql and it will be loaded into a new query window.

Remember that you can run an entire script at once, which will be multiple queries in this case. Or you can highlight a single query and select the **Run** button to execute just the highlighted query. 

Run the following query to return information about all the orders and the details of those orders. 

```tsql
USE MyStore;MySTore
SELECT o.orderid, o.orderdate,
 od.productid,od.unitprice,
 od.qty
FROM Sales.Orders o JOIN Sales.OrderDetails od
    ON o.orderid = od.orderid;
```

Select the Run button next to the green arrow in the upper left corner.  

![Picture 2](../media/Module1-Unit6-picture2.png)

You will be prompted to connect to your SQL Server. Enter a single dot for the Server, which indicates your default local SQL Server. Because the Authentication type is Windows Authentication, the tool will use your login credentials from Windows and you don't need to enter anything for User name and Password. 

Select **Connect**. 

![Picture 3](../media/Module1-Unit6-picture3.png)

You should get 2155 rows back.

Run the following query to return information about all the customers and the dates of their orders. 

```tsql
SELECT c.companyname, c.custid, o.orderdate
FROM Sales.Customers AS c JOIN Sales.Orders AS o
    ON c.custid = o.custid;
```
You should get 830 rows returned. 

If you have reason to suspect that not all your customers have placed order, you might want to run this query with an OUTER JOIN. Rewrite the query to all the company name values, whether or not that customer has placed any orders.

You should get 832 rows returned, which means there are two customers who did not place any orders. The value that shows up in the _orderdate_ column is NULL. 

Modify this query to return ONLY the rows for the customers that did not place any order. You should get two rows back. 

Run the following query that performs a self-join of the _Customers_ table to find all the customers who are based in the same city and country. 

```tsql
SELECT c1.custid, c1.contactname, c2.custid, c2.contactname, c1.city, c1.country
FROM Sales.Customers AS c1 JOIN Sales.Customers AS C2
   ON c1.city = c2.city AND c2.country = c2.country;
WHERE c1.custid > c2.custid;
```
You should get 44 rows back.

Now run the query again, leaving off the WHERE clause. Make sure you understand why you get so many more rows back. 


In this next query, you will return details about the most recent orders using a subquery to find the date of the most recent order:

```tsql
SELECT orderid, orderdate, shipcountry, custid 
FROM Sales.Orders
WHERE orderdate = 
    (SELECT MAX(orderdate) FROM Sales.Orders);
```

You should get four rows back, all with the same orderdate. 

Modify the query to return information about the oldest orders. That query should only return one row.

Modify the query again to return information about the order with the highest freight charge. 

To finish this exercise select **Done** below.Mul

