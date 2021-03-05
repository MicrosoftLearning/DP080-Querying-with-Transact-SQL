---
lab:
    title: 'Write basic SELECT statements'
    module: 'Module 2: Write SELECT statements in Transact-SQL'
---

# Lab: Write basic SELECT statements
 
In this exercise, you will use Azure Data Studio to connect to the _MyStore_ database and execute some basic SELECT statements.

## Connect to the lab environment

When the VM lab environment opens, select the  **Ctrl+Alt+Delete** button in the **Resources** tab to open the login screen. 
Select the password on the **Resources** tab for the **Administrator** account to populate the password field, and then select the arrow to sign in to Windows.

## Open Azure Data Studio

There is an icon in the toolbar to open Azure Data Studio. 

![Picture 1](../media/Module1-Unit6-picture1.png)

Select the icon for Azure Data Studio. The tool will open to a Welcome screen. If you get a message in the lower right corner asking if you want to enable **Preview features**, you can select either option. 

From the **File** menu, select **New Query**. You should now see a blank query window. 

## Execute simple queries
The queries will use a sample database called _MyStore_. Although there are about a dozen user tables in this database, we’ll only be working with a couple of them in this exercise. We’ll be using the _Customers_ and the _OrderDetails_ tables. 

For the queries we are using, you can try typing them in directly or you can select File/Open File, and navigate to D:\Lab Code\Basic SELECT. Double-click on the file script2.sql and it will be loaded into a new query window.

Remember that you can run an entire script at once, which will be multiple queries in this case. Or you can highlight a single query and select the **Run** button to execute just the highlighted query. 

Run the following query to return the name and city of all the customers. 
```tsql
USE MyStore;
SELECT contactname, city
FROM Sales.Customers;
```
Select the Run button next to the green arrow in the upper left corner.  

![Picture 2](../media/Module1-Unit6-picture2.png)

You will be prompted to connect to your SQL Server. Enter a single dot for the Server, which indicates your default local SQL Server. Because the Authentication type is Windows Authentication, the tool will use your login credentials from Windows and you don't need to enter anything for User name and Password. 

Select **Connect**. 

![Picture 3](../media/Module1-Unit6-picture3.png)

You should get 91 rows back. 

Modify the query to only show the customers in London. You should get six rows back. 

Modify the query further to change column headers in the output so that the _contactname_ column is labelled "Customer Name" and the _cty_ column is labelled "Customer City".

Now modify the original query to only show the customer names, with the _city_ and _country_ for all customers who don't have a value for _region_.  You should get 60 rows back. 

Run the following query to return the order ID, product ID, price and quantity of all sales of items costing more than 250. 

```tsql
SELECT orderid, productid, unitprie, qty
FROM Sales.OrderDetails
WHERE UnitPrice > 250;
```

Now modify this query to add another column that is the product of quantity and price. Name that new column GrossCost.

To finish this exercise select **Done** below.
