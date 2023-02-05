# **SQL Notes and Examples**

## **SQL `SELECT` Statement**

<details><summary>CLICK HERE</summary>

The `SELECT` statement is used to select data from a database.

The data returned is stored in a result table, called the result-set.

### **`SELECT` Syntax**

```sql
SELECT column1, column2, ... 
FROM table_name;
```
```sql
SELECT * FROM table_name;
```

### **`SELECT` Example**

Select the "CustomerName" and "City" columns from the "Customers" table:

```sql
SELECT CustomerName, City
FROM Customers;
```

Select **all the columns** from the "Customers" table:

```sql
SELECT * FROM Customers;
```
</details>

## **SQL `SELECT` `DISTINCT` Statement**

<details><summary>CLICK HERE</summary>

The `SELECT DISTINCT` statement is used to return only distinct (different) values.

### **`SELECT` `DISTINCT` Syntax**

```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

### **`SELECT` `DISTINCT` Example**

Select only the DISTINCT values from the "Country" column in the "Customers" table:

```sql
SELECT DISTINCT Country 
FROM Customers;
```
</details>

## **SQL `WHERE` Clause**

<details><summary>CLICK HERE</summary>

The `WHERE` clause is used to filter records.

It is used to extract only those records that fulfill a specified condition.

### **`WHERE` Syntax**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

### **`WHERE` Clause Example**

Select all the customers from the country "Mexico", in the "Customers" table:

```sql
SELECT * FROM Customers
WHERE Country='Mexico';
```

### **Operators in The `WHERE` Clause**

| Operator | Meaning |
| --- | --- |
| `=` | Equal |
| `>` |	Greater than |
| `<` |	Less than |
| `>=` |	Greater than or equal |
| `<=` |	Less than or equal |
| `<>` |	Not equal. Note: In some versions of SQL this operator may be written as `!=` |
| `BETWEEN` |	Between a certain range|
| `LIKE` |	Search for a pattern |
| `IN`	| To specify multiple possible values for a column|

</details>

## **SQL `AND`, `OR` and `NOT` Operators**

<details><summary>CLICK HERE</summary>

The `WHERE` clause can be combined with `AND`, `OR`, and `NOT` operators.

The `AND` and `OR` operators are used to filter records based on more than one condition:

* The `AND` operator displays a record if all the conditions separated by `AND` are `TRUE`.
* The `OR` operator displays a record if any of the conditions separated by `OR`is `TRUE`.

The `NOT` operator displays a record if the condition(s) is `NOT` `TRUE`.

### **`AND` Syntax**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```

### **`AND` Example**

Select all fields from "Customers" where country is "Germany" AND city is "Berlin":

```sql
SELECT * FROM Customers
WHERE Country='Germany' AND City='Berlin';
```

### **`OR` Syntax**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
```

### **`OR` Example**

Select all fields from "Customers" where city is "Berlin" OR "München":

```sql
SELECT * FROM Customers
WHERE City='Berlin' OR City='München';
```

### **`NOT` Syntax**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;
```

### **`NOT` Example**

Select all fields from "Customers" where country is NOT "Germany":

```sql
SELECT * FROM Customers
WHERE NOT Country='Germany';
```

### **Combining `AND`, `OR` and `NOT`**

Select all fields from "Customers" where country is "Germany" AND city must be "Berlin" OR "München" (use parenthesis to form complex expressions):

```sql
SELECT * FROM Customers
WHERE Country='Germany' AND (City='Berlin' OR City='München');
```

</details>

## **SQL `ORDER BY` Keyword**

<details><summary>CLICK HERE</summary>

The `ORDER BY` keyword is used to sort the result-set in ascending or descending order.

### **`ORDER BY` Syntax**

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```

### **`ORDER BY` Example**

Select all customers from the "Customers" table, sorted DESCENDING by the "Country" column:

```sql
SELECT * FROM Customers
ORDER BY Country DESC;
```

Select all customers from the "Customers" table, sorted by the "Country" and the "CustomerName" column. This means that it orders by Country, but **if some rows have the same Country, it orders them by CustomerName**:

```sql
SELECT * FROM Customers
ORDER BY Country, CustomerName;
```

Select all customers from the "Customers" table, sorted ascending by the "Country" and descending by the "CustomerName" column:

```sql
SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;
```
</details>

## **SQL `INSERT INTO` Statement**

<details><summary>CLICK HERE</summary>

The `INSERT INTO` statement is used to insert new records in a table.

### **`INSERT INTO` Syntax**

1. Specify both the column names and the values to be inserted:

```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```

2. If you are adding values for all the columns of the table, you do not need to specify the column names in the SQL query:

```sql
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```

### **`INSERT INTO` Example**

Inserts a new record in the "Customers" table:

```sql
INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country)
VALUES ('Cardinal', 'Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway');
```

Insert a new record, but only insert data in the "CustomerName", "City", and "Country" columns (CustomerID will be updated automatically, **other columns will be null**):

```sql
INSERT INTO Customers (CustomerName, City, Country)
VALUES ('Cardinal', 'Stavanger', 'Norway');
```

</details>

## **SQL `NULL` Values**

<details><summary>CLICK HERE</summary>

A field with a `NULL` value is a field with no value.

It is not possible to test for NULL values with comparison operators, such as =, <, or <>.

### **`IS NULL` Syntax**

```sql
SELECT column_names
FROM table_name
WHERE column_name IS NULL;
```

### **`IS NOT NULL` Syntax**

```sql
SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;
```

### **`IS NULL` Example**

Lists all customers with a NULL value in the "Address" field:

```sql
SELECT CustomerName, ContactName, Address
FROM Customers
WHERE Address IS NULL;
```

### **`IS NOT NULL` Example**

Lists all customers with a value in the "Address" field:

```sql
SELECT CustomerName, ContactName, Address
FROM Customers
WHERE Address IS NOT NULL;
```
</details>

## **SQL `UPDATE` Statement**

<details><summary>CLICK HERE</summary>

The `UPDATE` statement is used to modify the existing records in a table.

### **`UPDATE` Syntax**

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

### **`UPDATE` Example**

Updates the first customer (CustomerID = 1) with a new contact person and a new city.

```sql
UPDATE Customers
SET ContactName = 'Alfred Schmidt', City= 'Frankfurt'
WHERE CustomerID = 1;
```
</details>

## **SQL `DELETE` Statement**

<details><summary>CLICK HERE</summary>

The `DELETE` statement is used to delete existing records in a table.

### **`DELETE` Syntax**

```sql
DELETE FROM table_name WHERE condition;
```

### **`DELETE` Example**

Deletes the customer "Alfreds Futterkiste" from the "Customers" table:

```sql
DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste';
```
</details>

## **SQL `TOP`, `LIMIT` Clause**

<details><summary>CLICK HERE</summary>

The `SELECT TOP` clause is used to specify the number of records to return.

The `SELECT TOP` clause is useful on large tables with thousands of records. Returning a large number of records can impact performance.

### **SQL Server / MS Access `SELECT TOP` Syntax:**

```sql
SELECT TOP number|percent column_name(s)
FROM table_name
WHERE condition;
```

### **MySQL `LIMIT` Syntax:**

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;
```

### **`SELECT TOP` Example**

Select the first three records from the "Customers" table:

```sql
SELECT TOP 3 * FROM Customers;
```

Select the first 50% of the records from the "Customers" table:

```sql
SELECT TOP 50 PERCENT * FROM Customers;
```

### **`LIMIT` Example**

Select the first three records from the "Customers" table:

```sql
SELECT * FROM Customers
LIMIT 3;
```

Select the first three records from the "Customers" table, where the country is "Germany":

```sql
SELECT * FROM Customers
WHERE Country='Germany'
LIMIT 3;
```

</details>

## **SQL `MIN()` and `MAX()` Functions**

<details><summary>CLICK HERE</summary>

The `MIN()` function returns the smallest value of the selected column.

The `MAX()` function returns the largest value of the selected column.

### **`MIN()` Syntax**

```sql
SELECT MIN(column_name)
FROM table_name
WHERE condition;
```

### **`MAX()` Syntax**

```sql
SELECT MAX(column_name)
FROM table_name
WHERE condition;
```

### **`MIN()` Example**

Finds the price of the cheapest product:

```sql
SELECT MIN(Price) AS SmallestPrice
FROM Products;
```

### **`MAX()` Example**

Finds the price of the most expensive product:

```sql
SELECT MAX(Price) AS LargestPrice
FROM Products;
```
</details>

## **SQL `COUNT()`, `AVG()` and `SUM()` Functions**

<details><summary>CLICK HERE</summary>

The `COUNT()` function returns the number of rows that matches a specified criterion.

### **`COUNT()` Syntax**

```sql
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```

The `AVG()` function returns the average value of a numeric column. 

### **`AVG()` Syntax**

```sql
SELECT AVG(column_name)
FROM table_name
WHERE condition;
```

The SUM() function returns the total sum of a numeric column. 

### **`SUM()` Syntax**

```sql
SELECT SUM(column_name)
FROM table_name
WHERE condition;
```

### **`COUNT()` Example**

Finds the number of products:

```sql
SELECT COUNT(ProductID)
FROM Products;
```

### **`AVG()` Example**

Finds the average price of all products:

```sql
SELECT AVG(Price)
FROM Products;
```

### **`SUM()` Example**

Finds the sum of the "Quantity" fields in the "OrderDetails" table:

```sql
SELECT SUM(Quantity)
FROM OrderDetails;
```
</details>

## **SQL `LIKE` Operator**

<details><summary>CLICK HERE</summary>

The `LIKE` operator is used in a `WHERE` clause to search for a specified pattern in a column.

### **`LIKE` Syntax**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE columnN LIKE pattern;
```

### **Wildcard Characters in MySQL**

| Symbol | Description | Example |
| --- | --- | --- |
| `%` | Represents zero or more characters |  	bl% finds bl, black, blue, and blob |
| `_` |	Represents a single character| h_t finds hot, hat, and hit|

### **`LIKE` Example**

Select all customers with a CustomerName starting with "a":

```sql
SELECT * FROM Customers
WHERE CustomerName LIKE 'a%';
```
### **Examples of different `LIKE` operators with `'%'` and `'_'` wildcards:**

| `LIKE` Operator | Description |
| --- | --- |
| `WHERE CustomerName LIKE 'a%'` | Finds any values that start with "a" |
| `WHERE CustomerName LIKE '%a'` |	Finds any values that end with "a" |
| `WHERE CustomerName LIKE '%or%'` | Finds any values that have "or" in any position |
| `WHERE CustomerName LIKE '_r%'` |	Finds any values that have "r" in the second position |
| `WHERE CustomerName LIKE 'a_%'` |	Finds any values that start with "a" and are at least 2 characters in length |
| `WHERE CustomerName LIKE 'a__%'` | Finds any values that start with "a" and are at least 3 characters in length |
| `WHERE ContactName LIKE 'a%o'` | 	Finds any values that start with "a" and ends with "o" |

</details>

## **SQL `IN` Operator**

<details><summary>CLICK HERE</summary>

The `IN` operator allows you to specify multiple values in a `WHERE` clause.

The `IN` operator is a shorthand for multiple `OR` conditions.

### **`IN` Syntax**

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);
```

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name IN (SELECT STATEMENT);
```

### **`IN` Example**

Select all customers that are located in "Germany", "France" or "UK":

```sql
SELECT * FROM Customers
WHERE Country IN ('Germany', 'France', 'UK');
```

Select all customers that are from the same countries as the suppliers:

```sql
SELECT * FROM Customers
WHERE Country IN (SELECT Country FROM Suppliers);
```

</details>

## **SQL `BETWEEN` Operator**

<details><summary>CLICK HERE</summary>

The `BETWEEN` operator Select values within a given range. The values can be numbers, text, or dates.

The `BETWEEN` operator is inclusive: begin and end values are included.

### **`BETWEEN` Syntax**

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

### **`BETWEEN` Example**

Select all products with a price between 10 and 20:

```sql
SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20;
```

Select all products with a ProductName between "Carnarvon Tigers" and "Mozzarella di Giovanni":

```sql
SELECT * FROM Products
WHERE ProductName BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
ORDER BY ProductName;
```

Select all orders with an OrderDate between '01-July-1996' and '31-July-1996':

```sql
SELECT * FROM Orders
WHERE OrderDate BETWEEN '1996-07-01' AND '1996-07-31';
```

</details>

## **SQL `AS` Aliases**

<details><summary>CLICK HERE</summary>

Aliases are used to give a table, or a column in a table, a temporary name.

Aliases are often used to make column names more readable.

An alias only exists for the duration of that query.

An alias is created with the `AS` keyword.

### **`AS` Column Syntax**

```sql
SELECT column_name AS alias_name
FROM table_name;
```

### **`AS` Table Syntax**

```sql
SELECT column_name(s)
FROM table_name AS alias_name;
```

### **`AS` Example**

Create two aliases, one for the CustomerID column and one for the CustomerName column:

```sql
SELECT CustomerID AS ID, CustomerName AS Customer
FROM Customers;
```

Select all the orders from the customer with CustomerID=4 (Around the Horn). We use the "Customers" and "Orders" tables, and give them the table aliases of "c" and "o" respectively (Here we use aliases to make the SQL shorter):

```sql
SELECT o.OrderID, o.OrderDate, c.CustomerName
FROM Customers AS c, Orders AS o
WHERE c.CustomerName='Around the Horn' AND c.CustomerID=o.CustomerID;
```
</details>