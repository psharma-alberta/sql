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


## Day 3: Mar. 03, 2022 USING FILTER (WHERE)

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
SELECT columnname or *
FROM tablename
WHERE columnname IS NULL;
```sql
SELECT * 
FROM Customers
WHERE cust_email IS NULL;

```

## Day 4: Mar 04, 2022 
## Advanced filtering using wildcards

#### Return Records that begins with, ends with and contains a specific string.
SELECT columnname
FROM tablename
WHERE columnname LIKE 'a%';
```sql
SELECT prod_name
FROM PRODUCTS 
WHERE prod_name LIKE 'b%';
```
SELECT columnname
FROM tablename
WHERE columnname LIKE '%y';
```sql
SELECT prod_name
FROM PRODUCTS 
WHERE prod_name LIKE '%y';
```

SELECT columnname
FROM tablename
WHERE columnname LIKE '%inch%';
```sql
SELECT prod_name
FROM PRODUCTS 
WHERE prod_name LIKE '%inch%';
```

#### Return Records that begins with, or ends with any (single) character where the rest of the string is given.
SELECT columnname
FROM tablename
WHERE columnname LIKE '_restofthestring';
```sql
SELECT prod_name
FROM PRODUCTS 
WHERE prod_name LIKE '_ inch teddy bear';
```
SELECT columnname
FROM tablename
WHERE columnname LIKE 'restofthestring_';
```sql
SELECT vend_id
FROM PRODUCTS 
WHERE vend_id LIKE 'DLL0_';
```

#### Return Records that begins with, or ends with one of two given special characters, where the rest of the string is also given.
SELECT columname
FROM tablename
WHERE columnname LIKE '[ab]%';
```sql
SELECT cust_contact
FROM Customers
WHERE cust_contact LIKE '[JM]%'
ORDER BY cust_contact;
```
#### !!! THIS SYNTAX DOES NOT WORK WITH ALL DATABASE MANAGEMENT SYSTEMS !!!
#### !!! HERE IS AN ALTERNATE TO BE USED WITH MYSQL DBM !!!

```sql
SELECT cust_contact
FROM Customers
WHERE cust_contact LIKE 'J%' OR cust_contact LIKE 'M%'
ORDER BY cust_contact;
```
## Day 5: Mar 05, 2022 
## Using Data Manipulation Functions

#### Remove extra spaces from the left(LTRIM), right(RTRIM) & both sides(TRIM) of a column
SELECT columname
LTRIM(columnname) 
FROM tablename;

#### Display a new column by concatenating 2 columns, with a space between them, and an alias
SELECT columnname1, columname2
CONCAT(columname1, ' ', columname2) AS newcolumn
FROM tablename;
```sql
SELECT cust_id, cust_name,
CONCAT(cust_contact, '  ','(', (cust_country), ')') AS cust_detail
FROM Customers;
```
#### !!! MYSQL doesn't use + sign to join two column values, it does so by using CONCAT function !!!


#### Display a new column with the product of 2 columns, and an alias
SELECT columnname1, columname2, columname1 * columname2 AS newcolumn
FROM tablename;
```sql
SELECT quantity, item_price,
quantity * item_price AS total_price
FROM OrderItems;
```


## Day 6: Mar 06, 2022 
## Summarizing Data (Aggregate Functions)

#### Show the number of rows in a table
SELECT COUNT(*)
FROM tablename;
```sql
SELECT count(*) AS totalrows
FROM PRODUCTS;
```

#### Show the the lowest & highest value in a specified column, in the same query
SELECT MAX(columnname1) AS maxvalue,
MIN(columnname1) AS minvalue
FROM tablename;
```sql
SELECT MAX(prod_price) AS max_price,
MIN(prod_price) AS min_price
FROM Products;
```

#### Show the average value of a specific column
SELECT AVG(columnname) AS avrgvalue
FROM tablename;
```sql
SELECT AVG(prod_price) AS avrgvalue
FROM Products;
```

#### Show the sum (total) of the values in a specific column.
SELECT SUM(columnname) AS sum_value
FROM tablename;
```sql
SELECT SUM(prod_price) AS sum_value
FROM Products;
```

## 7. Grouping Data 

#### Show the count of rows for every distinct value of a (foreign key) column
SELECT columnname, COUNT(*) AS somename
FROM tablename
GROUP BY columnname;
```sql
SELECT prod_id, COUNT(*) as distinc_prodid
FROM OrderItems
GROUP BY prod_id;
```
#### Show the count of rows for every distinct value of a (foreign key) column, filtered by condition
SELECT columnname, COUNT(*) AS somename
FROM tablename
GROUP BY columnname
HAVING columnname = some condition;
```sql
SELECT prod_id, SUM(quantity) AS totalquant
FROM OrderItems
WHERE order_item >= 3
GROUP BY prod_id;
```

```sql
SELECT prod_id, SUM(quantity) AS totalquant
FROM OrderItems
GROUP BY prod_id
HAVING SUM(quantity)>= 165;
```

#### Show the count of rows for every distinct value of a (foreign key) column, filtered by condition, and sorted
SELECT columnname, COUNT(*) AS somename
FROM tablename
GROUP BY columnname
HAVING columnname = some condition
ORDER BY columnname;

```sql
SELECT prod_id, SUM(quantity) AS totalquant
FROM OrderItems
GROUP BY prod_id
HAVING SUM(quantity)>= 165
ORDER BY SUM(quantity);
```


## 8. Joining Tables 

#### Given two tables (T1 & T2), show records that have matching values in both tables (assumin column_id is common column between T1 & T2)
SELECT T1.columnname, T2.columnname
FROM T1
INNER JOIN T2 ON T1.column_id = T2.column_id;
```sql
SELECT OrderItems.quantity, Products.prod_name
FROM OrderItems
INNER JOIN Products ON OrderItems.prod_id = Products.prod_id;
```

#### Given two tables (T1 & T2), show all records from T1, and only matching records from T2
SELECT T1.columnname, T2.columnname
FROM T1
LEFT JOIN T2 ON T1.column_id = T2.column_id;
```sql
SELECT OrderItems.quantity, Products.prod_name
FROM OrderItems
LEFT JOIN Products ON OrderItems.prod_id = Products.prod_id;
```


#### Given two tables (T1 & T2), show all records from T2, and only matching records from T1
SELECT T1.columnname, T2.columnname
FROM T1
RIGHT JOIN T2 ON T1.column_id = T2.column_id;
```sql
SELECT OrderItems.quantity, Products.prod_name
FROM OrderItems
RIGHT JOIN Products ON OrderItems.prod_id = Products.prod_id;
```

#### Given two tables (T1 & T2), show all matching & non-matching records
SELECT T1.columnname, T2.columnname
FROM T1
CROSS JOIN T2 ON T1.column_id = T2.column_id; 
```sql
SELECT OrderItems.quantity, Products.prod_name
FROM OrderItems
CROSS JOIN Products ON OrderItems.prod_id = Products.prod_id;
```


## 9. Inserting, Updating & Deleting Records
INSERT INTO tablename (columnname1, columnname2, columnname3)
Values(1, 'abc', 2020-10-23);

#### Insert a new record into a table (explicitly stating the column names)

#### Update all records in a table (by specifying the column names)

#### Update specific records in a table (by specifying the column names) that match a condition

#### Delete all records in a table

#### Delete specific records in a table that match a condition
