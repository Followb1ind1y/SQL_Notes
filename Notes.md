## **SQL `SELECT` Statement**

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

Selects the "CustomerName" and "City" columns from the "Customers" table:

```sql
SELECT CustomerName, City
FROM Customers;
```

Selects **all the columns** from the "Customers" table:

```sql
SELECT * FROM Customers;
```

## **SQL `SELECT` `DISTINCT` Statement**

The `SELECT DISTINCT` statement is used to return only distinct (different) values.

### **`SELECT` `DISTINCT` Syntax**

```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

### **`SELECT` `DISTINCT` Example**

Selects only the DISTINCT values from the "Country" column in the "Customers" table:

```sql
SELECT DISTINCT Country 
FROM Customers;
```

## **SQL `WHERE` Clause**

The `WHERE` clause is used to filter records.

It is used to extract only those records that fulfill a specified condition.

### **`WHERE` Syntax**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

### **`WHERE` Clause Example**

Selects all the customers from the country "Mexico", in the "Customers" table:

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

## **SQL `AND`, `OR` and `NOT` Operators**

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

Selects all fields from "Customers" where country is "Germany" AND city is "Berlin":

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

Selects all fields from "Customers" where city is "Berlin" OR "München":

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

Selects all fields from "Customers" where country is NOT "Germany":

```sql
SELECT * FROM Customers
WHERE NOT Country='Germany';
```

### **Combining `AND`, `OR` and `NOT`**

Selects all fields from "Customers" where country is "Germany" AND city must be "Berlin" OR "München" (use parenthesis to form complex expressions):

```sql
SELECT * FROM Customers
WHERE Country='Germany' AND (City='Berlin' OR City='München');
```

## **SQL `ORDER BY` Keyword**

The `ORDER BY` keyword is used to sort the result-set in ascending or descending order.

### **`ORDER BY` Syntax**

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```

### **`ORDER BY` Example**

Selects all customers from the "Customers" table, sorted DESCENDING by the "Country" column:

```sql
SELECT * FROM Customers
ORDER BY Country DESC;
```

Selects all customers from the "Customers" table, sorted by the "Country" and the "CustomerName" column. This means that it orders by Country, but **if some rows have the same Country, it orders them by CustomerName**:

```sql
SELECT * FROM Customers
ORDER BY Country, CustomerName;
```

Selects all customers from the "Customers" table, sorted ascending by the "Country" and descending by the "CustomerName" column:

```sql
SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;
```

## **SQL `INSERT INTO` Statement**

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

## **SQL `NULL` Values**

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