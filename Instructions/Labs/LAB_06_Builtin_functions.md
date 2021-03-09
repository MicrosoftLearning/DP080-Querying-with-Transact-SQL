---
lab:
    title: 'Use built-in functions in Transact-SQL'
    module: 'Module 6: Use built-in functions in Transact-SQL'
---

# Lab: Use built-in functions in Transact-SQL
 
In this exercise, you will use Azure Data Studio to connect to the _MyStore_ database and execute some queries using built-in functions.

## Connect to the lab environment

When the VM lab environment opens, select the  **Ctrl+Alt+Delete** button in the **Resources** tab to open the login screen. 
Select the password on the **Resources** tab for the **Administrator** account to populate the password field, and then select the arrow to sign in to Windows.

## Open Azure Data Studio

There is an icon in the toolbar to open Azure Data Studio. 

![Picture 1](../media/Module1-Unit6-picture1.png)

Select the icon for Azure Data Studio. The tool will open to a Welcome screen. If you get a message in the lower right corner asking if you want to enable **Preview features**, you can select either option. 

From the **File** menu, select **New Query**. You should now see a blank query window. 

## Scalar functions for replacing NULL values

The queries will use a sample database called _MyStore_. Although there are about a dozen user tables in this database, we’ll only be working with a couple of them in this exercise. We’ll be using the _Orders_, _OrderDetails_ and _Customers_ tables. 

For the queries we are using, you can try typing them in directly or you can select File/Open File, and navigate to D:\Lab Code\Scalar functions. Double-click on the file script6.sql and it will be loaded into a new query window.

Remember that you can run an entire script at once, which will be multiple queries in this case. Or you can highlight a single query and select the **Run** button to execute just the highlighted query. 

Write a SELECT statement to retrieve the _contactname_, _phone_ and _fax_ information from the _Sales.Customers_ table. If there is a missing value in the fax column, return the value “No information”.

Write two solutions, one using the COALESCE function and the other using the ISNULL function.

## Metadata functions

Recall the the db_id() and db_name functinos can be used with or without an argument. Without an argument they give you information about your current database; with an argument, you can specify which database you want information about. 

Write a query to select from _sys.dm_exec_sessions_ system view and return the _login\name_ and _login\_time_ columns from the view, for all sessions that are in the same database as your own session is. 

>NOTE: Some of the rows in _sys.dm_exec_sessions_ have a 0 in the _database\_id_ column, which indicates they are background sessions not attached to a particular database. However, if you use the DB_NAME function with the _database\_id_ column as the argument, the results look like all these background sessions are in your current database. That is because DB_NAME(0) is equivalent to DB_NAME(). 

## System functions

Run the following query to see the current time using four different system functions. 

```tsql
SELECT GETDATE(), CURRENT_TIMESTAMP, sysdatetime(), sysutcdatetime();
```

Which of the functions return the same exact values?  
What is the difference between the value returned by **CURRENT_TIMESTAMP** and the value returned by **sysdatetime()**?  
When would **sysutcdatetime()** return the same value as one of the other columns? 


