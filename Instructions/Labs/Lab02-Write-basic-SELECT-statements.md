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

Select the icon for Azure Data Studio. The tool will open to a blank query window. If you get a message in the lower right corner asking ifyou want to enable **Preview features**, you can select either option. 

## Execute simple queries
The queries will use a sample database called _MyStore_. Although there are about a dozen user tables in this database, we’ll only be working with a couple of them in this exercise. As with the examples in the Module, we’ll be using the _Customers_ and the _Products_ table. 

For the queries we are using, you can try typing them in directly or you can select File/Open File, and navigate to D:\Lab Code\Basic SELECT. Double-click on the file script1.sql and it will be loaded into a new query window.

Remember that you can run an entire script at once, which will be multiple queries in this case. Or you can highlight a single query and select the **Run** button to execute just the highlighted query. 

Run the following query to return the first and last names of all the customers. 
Show query
Now modify it to only show the customers with the last name of Khan. 
Now modify to change column headers
Now modify it to only show the customers with the last name of Khan and no known middle name. 

Run the following query to return the name, listing price and company cost of all products with a list price less than 50. 
SELECT Name, ListPrice, StandardCost
FROM SalesLT.product
WHERE ListPrice < 50;
Now modify to add another column that is the percentage that our cost is of the listing price. Name that new column Percentage. 
SELECT Name, ListPrice, StandardCost, StandardCost/ListPrice * 100 as Percentage
FROM SalesLT.product
WHERE ListPrice < 50;
Write a query to list all the distinct last names in the Customer table. 


To finish this exercise select **Done** below.
