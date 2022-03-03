# SQL

## DAY 1: March 01, 2022

### 1. Setup
**Book Name**: SQL in 10 minutes
**Article Link** to download SQL software: https://cierra-andaur.medium.com/sams-teach-yourself-sql-in-10-minutes-a-day-setting-up-for-success-76dd346e5dd
**Book Link** to downloaad content for creting SQL Databaase: https://forta.com/books/0135182794/ 

###### Step 1 - Download MySQL, SQLWorkBench and data to create database
A)	Go to https://forta.com/books/0135182794/ and download MySQL (and MariaDB) SQL scripts from Supporting Resources (Lesson 1: Understanding SQL)

B)	MySQL: https://dev.mysql.com/downloads/mysql/

    (Version: macOS 11 (x86, 64-bit), DMG Archive)

    Once downloaded, open and follow instructions (PW: Sharm@85, might need it later to connect SQLWorkbench to MySQL)

    (After installing, delete the installer)


3)	My SQLWorkbench: https://dev.mysql.com/downloads/workbench/

(Version: macOS (x86, 64-bit), DMG Archive)

Once downloaded, drag and drop in Applications Folder.

Open SQLWorkbench and click on the + sign

Name it as localhost and click on ‘Test Connection’

Press OK


###### Step 2 - Creating database (Follow the article, there is a video in there as well)
(You will create database using data provided by the book that you downloaded from the link: https://forta.com/books/0135182794/ )

A) Open SQLWokBench, Click on ‘Create New Schema’ button.  
B) Name as tysql (THIS IS THE NEW DATABASE) and Click Apply and then again click Apply.  
C) Now go to Query and open tysql by double clicking on it.  
D) Copy and paste the contents of the “create” file into the SQL editor window and execute the query using the lightning bolt icon. You will see data towards the bottom of screen. Now select everything that you just pasted and delete it. Repeat the process to copy and paste the contents of “populate”  file into the SQL editor window and execute this query as well and then delete the pasted data. Now you have the data in the database called tysql.  



###### Step 3 - Write SELECT * statement to see the data.

## DAY 2: March 02, 2022

### 2. Retrieving Data

###### Retrieving All Columns

Select * 
FROM tablename;

```sql
SELECT *
FROM Products;
```


###### Retrieving Individual Columns
Select columnname/s 
FROM tablename;
```sql
SELECT prod_id, vend_id, prod_name
FROM Products;
```

###### Retrieving Distinct Rows
Select DISTINCT columnname 
FROM tablename;

```sql
SELECT DISTINCT vend_id
FROM Products;
```

###### Limiting Results (will provide first 5 records of the table)
Select columnname 
FROM tablename
LIMIT 5;

```sql
SELECT *
FROM Products
LIMIT 5;
```
