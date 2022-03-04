# SQL

- Book Name: SQL in 10 minutes
- Article Link to download SQL software: https://cierra-andaur.medium.com/sams-teach-yourself-sql-in-10-minutes-a-day-setting-up-for-success-76dd346e5dd
- Book Link to download content for creting SQL Databaase: https://forta.com/books/0135182794/

## Day 1: Setup (Mar 01, 2022)


1. Download MySQL
    - Go to https://forta.com/books/0135182794/ and download MySQL (and MariaDB) SQL scripts from Supporting Resources (Lesson 1: Understanding SQL)
    - MySQL: https://dev.mysql.com/downloads/mysql/
    - Version: macOS 11 (x86, 64-bit), DMG Archive
    - Once downloaded, open and follow instructions
    - After installing, delete the installer
2. Download SQLWorkbench
    - SQLWorkbench: https://dev.mysql.com/downloads/workbench/
    - Version: macOS (x86, 64-bit), DMG Archive
    - Once downloaded, drag and drop in Applications Folder
    - Open SQLWorkbench and click on the + sign
    - Name it as localhost and click on ‘Test Connection’
    - Press OK
3. Create database 
    - Follow the article, there is a video in there as well. You will create database using data provided by the book that you downloaded from the link: https://forta.com/books/0135182794/
    - Open SQLWokBench, Click on ‘Create New Schema’ button.  
    - Name as tysql (THIS IS THE NEW DATABASE) and Click Apply and then again click Apply.  
    - Now go to Query and open tysql by double clicking on it.  
    - Copy and paste the contents of the “create” file into the SQL editor window and execute the query using the lightning bolt icon. You will see data towards the bottom of screen. Now select everything that you just pasted and delete it. Repeat the process to copy and paste the contents of “populate”  file into the SQL editor window and execute this query as well and then delete the pasted data. Now you have the data in the database called tysql.  
4. Write SELECT * statement to see the data.

## Day 2: Retrieving Data (Mar 02, 2022)

#### Show All Columns

Select * 
FROM tablename;

```sql
SELECT *
FROM Products;
```


#### Show Individual Columns
Select columnname/s 
FROM tablename;
```sql
SELECT prod_id, vend_id, prod_name
FROM Products;
```

#### Distinct
Select DISTINCT columnname 
FROM tablename;

```sql
SELECT DISTINCT vend_id
FROM Products;
```

#### Limit
Select columnname 
FROM tablename
LIMIT 5;

```sql
SELECT *
FROM Products
LIMIT 5;
```

## Day 3: Mar 03, 2022

#### Sort single column ascending (Default sort is ASC)
SELECT columnname
FROM tablename
ORDER BY columnname;
```sql
SELECT prod_name 
FROM Products
ORDER BY prod_name;
```

#### Sort single column descending
SELECT columnname
FROM tablename
ORDER BY columnname DESC;
```sql
SELECT prod_name 
FROM Products
ORDER BY prod_name DESC;
```

#### Sort two columns, first ascending, second descending
SELECT columnname1, columnname2
FROM tablename
ORDER BY columnname1, columnname2 DESC;
```sql
SELECT prod_price, prod_name
FROM Products
ORDER BY prod_price, prod_name DESC;
```


## Day 4: Mar. 03, 2022 USING FILTER (WHERE)

#### Show records matching value
SELECT columnname or *
FROM tablename
WHERE columnname = 'some condition';
```sql
SELECT * 
FROM OrderItems
WHERE order_item = 2;

```

#### Show records not matching value (!= or <>)
SELECT columnname or *
FROM tablename
WHERE columnname != 'some condition';
```sql
SELECT * 
FROM OrderItems
WHERE order_item != 2;

```

#### Show records matching range
SELECT columnname or *
FROM tablename
WHERE columnname BETWEEN 'some condition' AND 'some condition';
```sql
SELECT *
FROM OrderItems
WHERE quantity BETWEEN 5 AND 100 ;

```

#### Show records matching no value
