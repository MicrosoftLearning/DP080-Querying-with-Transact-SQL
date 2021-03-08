---
lab:
    title: 'Modify data in Transact-SQL'
    module: 'Module 2: Modify data in Transact-SQL'
---

# Lab: Modify data in Transact-SQL
 
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
The queries will use a sample database called _MyStore_. Although there are about a dozen user tables in this database, we’ll only be working with a couple of them in this exercise. We’ll be using the _Customers_ and the _Employees_ tables. 

For the queries we are using, you can try typing them in directly or you can select File/Open File, and navigate to D:\Lab Code\Modify data. Double-click on the file script4.sql and it will be loaded into a new query window.

Remember that you can run an entire script at once, which will be multiple queries in this case. Or you can highlight a single query and select the **Run** button to execute just the highlighted query. 

## Add rows to a table

Run the following query to create a copy of the _HR.Employees_ table called _HR.EmployeesTemp_. We will not be modifying the base tables so that you can continue to use them for other exercises. The **WHERE** clause contains an expression that will never be true, so no rows will actually be copied. We will have an empty table with the same columns as the original table.

```tsql
USE MyStore
SELECT * INTO HR.EmployeesTemp
FROM HR.Employees
WHERE 1 = 0;
```

Select the Run button next to the green arrow in the upper left corner.  

![Picture 2](../media/Module1-Unit6-picture2.png)

You will be prompted to connect to your SQL Server. Enter a single dot for the Server, which indicates your default local SQL Server. Because the Authentication type is Windows Authentication, the tool will use your login credentials from Windows and you don't need to enter anything for User name and Password. 

Select **Connect**. 

![Picture 3](../media/Module1-Unit6-picture3.png)

You should see a message that zero rows have been affected, which means no rows were copied into the new table. 

Write an INSERT statement to add a row to the _HR.EmployeesTemp_ table, with the following values:
o	title: Sales Representative
o	titleofcourtesy: Mr
o	firstname: Laurence
o	lastname: Grider
o	hiredate: 20130404
o	birthdate: 19751025
o	address: 1234 1st Ave. S.E.
o	city: Seattle
o	country: USA
o	phone: 206-555-0105

Note that we are not supplying values for all the columns.  The column _empid_ has the **identity** property and will be automatically populated. The columns _region_,  _postalcode_ and _mgrid_ are nullable, so NULL will be used for those values. 

Examine the row that you just inserted:

```tsql
SELECT * FROM HR.EmployeesTemp;
```
Write an INSERT statement that uses another table as the source of the data. Insert all rows from the _HR.Employees_ table into the new _HR.EmployeesTemp_ table. 


## Update and Delete rows 

Run the following query to create a copy of the _Sales.Customers_ table called _Sales.CustomersTemp_. This time we will actually copy all the rows.

```tsql
SELECT * INTO Sales.CustomersTemp
FROM Sales.Customers
```

Write an UPDATE statement to update all the records in the _CustomerTemp_ table that have a city of ‘Berlin’ and a contacttitle of ‘Sales Representative’ to have a contacttitle of ‘Sales Consultant’.

Write a DELETE statement to delete all the records in the _CustomerTemp_ table which have the contactname of ‘Taylor, Maurice’, ‘Smith, Denise’, or ‘Misiec, Anna’, as these contacts no longer work for the company. 


## Clean up
Drop the table you created in this exercise:

```tsql
DROP TABLE HR.EmployeesTemp;
DROP TABLE Sales.CustomersTemp;
```

To finish this exercise select **Done** below.
