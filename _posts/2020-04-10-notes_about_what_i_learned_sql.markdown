---
layout: post
title:      "Notes about what I learned SQL"
date:       2020-04-11 01:41:40 +0000
permalink:  notes_about_what_i_learned_sql
---


### What is SQL?
* SQL stands for "**Structured Query Language**".  
* It is for managing/interacting with data in a database.
* This language servers one thing only, talk to database. So it is referred as a "**spcial purpose**" or "**domain specific**" programming language. 


**Database**  
It is a collection of data stored in a format that can easily be accessed.  

**DBMS**  
* It stands for Database Management System.  
* It is a software. 
* It is used to manage database.  
* It interacts with the user, applciations and the database itself to capture and analyse data.

**There are two types of DBMS:**
* Relational Databases, SQL is the language used to talk to this Relational Databases.
* NoSQL Database.  This kind of DBMS does not understand SQL language.  


**RDBMS**  
* It stands for Reational Database Management System.      
* MySQL(open source), SQL Server (Microsoft), Oracle, etc.. are RDBMS. 
* SQL should work with all the database that is RDMBS.  

### SQL Commands. 
SQL commands can be categorized into the following categories / subset:  
* DDL - Data Definition Language  used to define database schema.
* DQL - Data Query Language  
* DML - Data Manipulation Language used to manipulate data presented in database.
* DCL - Data Control Language used to deal with the rights, permissins and other controls of database system
* TCL - Transaction Control Language used to deal with the transaction of database.


**DDL - Data Defination Language** contains the following commands:  
* CREATE
* ALTER
* DROP  
   Remove a table and it cannot be rolled back from the database.  
	 Remove a database.  
	 Syntax 
	 
```
DROP object object_name;
```  
if the object is DATABASE, the object name is the database_name
if hte ojbect is TABLE, the object name is table_name
	 
* REMANE
* TRUNCATE 
   * It is used to delete all the rows from a table.
   * The truncated rows can not be rolled back.
   * It is faster  than drop table.
   * The table is an empty table.  
   Syntax  
```
TRUNCATE TABLE table_name
```
	 
* COMMENT

**DQL - Data Query Language** contains the following commands:  
* SELECT
   is used to retrived data from a database.  

**DML - Data Manipulation Language** contains the following commands:  
* INSERT
* UPDATE
* DELETE
  *  It is used to delete a row in a table.
  *  The deleted data can be rollback.
  *  This performace is slower than TRUNCATE commands


**DCL - Data Control Language** contains the following commands:  
* GRANT
* REVOKE

**TCL - Transaction Control Language** contains the following commands:  
* COMMIT
* ROLLBACK
* SAVEPOINT
* SET TRANSATION


### SQL  
* Table: A table refers to a collection of data in an organized structure in form of rows and columns.  
* Field: A field refers to the number of colums in a table.  
* join : It is used to merge two tables or retrive data from there.   
  There are 4 joins in SQL:  
  * 	**INNER JOIN** - selects records that have mathcing values in both tables.  
       Syntax
			 SELECT column_name(s)
			 FROM table1
			 INNTER JOIN table2
			 ON table1.column_name = table2.column_name;  
  * 	**FULL JOIN ** - retuns all records when there is a match table1 or table2 records.  
       Syntax
			 SELECT column_name(s)
			 FROM table1
			 FULL OUTER JOIN table2
			 ON table1.column_name = tables.column_name
			 WHERE condition  
  * 	LEFT JOIN - returns all records from the table1, and matched records from the tables2.  The result is NULL from the table2, if there is no match.  
       Syntax
			 SELECT column_name(s)
			 FROM table1
			 LEFT JOIN table2
			 ON table1.column_name = tables_column_name;  
  * 	RIGHT JOIN - returns all records from the table2, and the matched records from the table1. Ther result is NULL from the table1, when there is no match.  
       Syntax  
			 SELECT column_name(s)
			 FROM table1
			 RIGHT JOIN table2
			 ON table1.column_name = table2.column_name;  
			 
* Primary Key  vs Foreign Key:  
   Primary Key:  
	 A Primary Key is a column or columns that uniquely identifies each row in the table.  
	 When multiple columns are used as a primeary key, it is known as **composite primary key**.  
	 Each table can only have Primary Key constraint.
   Foreign Key:
   A Foreign Key is a field or a column that is used to establish a link between two tables.  
	 A Foreign key in the child table references the primary key in the parent table.  
	 The foreign key constraint prevents actions that would destroy links between the child and parent tables.
	 
* data type char() and varchar2()
* SQL Costraints:  
   Constrains can be specified when the table is created with the CREATE TABLE statement, or after the table is created with the ALTER TABLE statement.  
	 Syntax:  
	```
 CREATE TABLE table_name (
	      column1 datatype constraint,
				column2 datatype constraint,
				column3 datatype constraint,
				.....
	);  
```  

 **There are 5 commonly used constraints in SQL:  **

   * 	**NOT NULL** - ensure that a NULL value can not be stored in a column.  
      Example:  
	
   ```
    CREATE TABLE Users (
       ID int NOT NULL,  
		   UserName varchar(255),
		   password varchar(255)
   );
  ```  

  ```
   ALTER TABLE Users 
   MODIFY UserName varchar(255) NOT NULL;
 ```  

					 
   * 	**UNIQUE** - ensure that all the values in a column are different.  
      Example:  
			
	```
CREATE TABLE Users (
    ID int NOT NULL  UNIQUE,
		UserName varchar(255),
		password varchar(255)
);
```   

```
ALTER TABLE Users 
ADD UNIQUE (ID);
```    


If there are more than one columns need to set UNIQUE constraint, the syntax:

```
CREATE TABLE Users (
    ID int NOT NULL,  
		UserName varchar(255),
		password varchar(255),
		CONSTRAINT UC_User UNIQUE (ID, password)
		
);
```  

```
ALTER TABLE Users 
ADD CONSTRAINT UC_User UNIQUE (ID, password);
```    
		
			
   * 	**CHECK** - is used to limit the value range that can be placed in a column.   
     
   	```
    CREATE TABLE Users (
       ID int NOT NULL  UNIQUE,
		   UserName varchar(255),
		   password varchar(255),
			 Age int NOT NULL,
			 CHECK (Age >= 16)
   );
```   

  ```
   ALTER TABLE Users 
   ADD CHECK (Age >= 18);
   ```    

   Drop a CHECK Constraint:

   ```
   ALTER TABLE Users 
   DROP CONSTRAINT CHK_UserAge;
	 
  ```  
 
   * 	**DEFAULT** - set a default value for a column when no value is specified.  
  ```
   CREATE TABLE Orders (
      ID int NOT NULL,
	    OrderNumber int NOT NULL UNIQUE,
	    OrderDate date DEFAULT GETDATE()
  );
```  

  ```
   ALTER TABLE Orders 
	 ALTER OrderDate SET DEFAULT GETDATE();
```  
   * 	**INDEX** - used to create and retrieve data from the database very quickly.   

*  Group Function:
    Group functions work on the set of rows and returns one result per group.
		The commonly used group functions:
    * 	AVG
    * 	COUNT
    * 	MAX
    * 	MIN
    * 	SUM
    * 	VARIANCE	

* What is the relationship in the RDB, and what are the different type of relationship?
   Relationships are defined as connection between the tables in a database.
	 There are about 4 type of relationships:
   * One to One replationship
   * One to Many relationship
   * Many to One Replationship
   * Self-Referencing Relationship  
 
* "BETWEEN" and "IN"
   * "BETWEEN" operator select values within a given range. This operator is inclusive.   
       Syntax:  
```
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```
			 
   * "IN" operator allows you to spcidfy multiple values in a WHERE clause.  
      Syntax:  
```
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2,....);
```   
Or  

```
SELECT column_name(s)
FROM table_name
WHERE column_name IN (SELECT statement);
```  

* Why are SQL functions used?
   SQL functions are used for the following purpose:  
   * 	 perform calculations on the data
   * 	 convert the data types
   * 	 fromat dates and numbers
   * 	 modify individual data items
   * 	 manipulate the output

* MERGE Statement
  As MERGE statement in SQL, is the combination of three INSERT, DELETE, and UPDATE statement.   
	Example:
	
```
/* Selecting the Target and the Source */ 
MERGE PRODUCT_LIST AS TARGET 
	USING UPDATE_LIST AS SOURCE 

	/* 1. Performing the UPDATE operation */ 

	/* If the P_ID is same, 
	check for change in P_NAME or P_PRICE */ 
	ON (TARGET.P_ID = SOURCE.P_ID) 
	WHEN MATCHED 
		AND TARGET.P_NAME <> SOURCE.P_NAME 
		OR TARGET.P_PRICE <> SOURCE.P_PRICE 

	/* Update the records in TARGET */ 
	THEN UPDATE
		SET TARGET.P_NAME = SOURCE.P_NAME, 
		TARGET.P_PRICE = SOURCE.P_PRICE 
	
	/* 2. Performing the INSERT operation */ 

	/* When no records are matched with TARGET table
	Then insert the records in the target table */ 
	WHEN NOT MATCHED BY TARGET 
	THEN INSERT (P_ID, P_NAME, P_PRICE)		 
		VALUES (SOURCE.P_ID, SOURCE.P_NAME, SOURCE.P_PRICE) 

	/* 3. Performing the DELETE operation */ 

	/* When no records are matched with SOURCE table
	Then delete the records from the target table */ 
	WHEN NOT MATCHED BY SOURCE 
	THEN DELETE

/* END OF MERGE */ 

```  

* WHERE clause and HAVING clause  
   SQL clause helps to limit/filter the result set by providing a condition to the query.  
   *  WHERE clause:  
       Syntax :  
			 
			 SELECT column1, column2,....
			 FROM table_name
			 WHERE condition  
   *  HAVING clause  
       Syntax:
			 
			 SELECT column_name(s)
			 FROM table_name
			 WHERE condtion
			 GROUP BY column_name(s)
			 HAVING condition
			 ORDER BY column_name(s)
   * 	What is the difference between a "HAVING" clause and a "WHERE" clause?
   	   HAVING clause => can be used only with SELECT statement. It is usually used in a GROUP BY clause.  
			 WHERE clause => is applied to each row before they are a part of the GROUP BY clause in a query.  
			 Example:  Lists if the employees "Davolio" or "Fuller" have registered more thatn 25 orders.
```
SELECT Employees.LastName, COUNT(Orders.OrderID) AS NumberOfOrders
FROM Orders
INNER JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID
WHERE LastName = 'Davolio' OR LastName = 'Fuller'
GROUP BY LastName
HAVING COUNT(Orders.OrderID) > 25;
```  

* How to fect common records from two tables?
   INTERSECT. 
	 
	 Syntax:  
	 
	```
 SELECT column1, column2, ...
	 FROM table_1
	 WHERE condition
	 
	 INTERSECT
	 
	 SELECT column1, column2, ...
	 FROM table_2
	 WHERE condition
```
 
  NOTE: what is differences between INSTERSECT and INNER JOIN?  
  *  INNER JOIN will return duplicate records. INTERSECT removes duplicates.
  *  INNER JOIN will never return NULL records, but INTERSECT will return NULL record.  

* SELECT DISTINCT  
   It is used to retrun only distinct values.  
	 Syntax:  
	 
	 SELECT DISTINCT column1, column2, ...
	 FROM table_name

### SQL example
* Get the counts of records in a table.  
```
SELECT * FROM table_name;  
```  

```
SELECT COUNT (*) FROM table_name;
```  

* Find the values of one field that beginning with 'A':  

```
SELECT * FROM table_name WHERE field_name like 'A%';  
```    

   Find the values of one field that end with 'A':  

```
SELECT * FROM table_name WHERE field_name like '%A';  
```   
	 
   Find the values of one field that contains 'A':  

```
SELECT * FROM table_name WHERE field_name like '%A%';  
```   

Note: LIKE is used to search for the pattern.

*  Get the third highest prices of product from Products table:  

```
SELECT * FROM (SELECT * FROM Products ORDER BY Price DESC LIMIT 3) ORDER BY Price ASC LIMIT 1;
```


	 




 

