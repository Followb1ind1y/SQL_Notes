# **SQL Notes and Examples**

## **SQL SELECT Statement**

The `SELECT` statement is used to select data from a database.

The data returned is stored in a result table, called the result-set.

### **SELECT Syntax**

```
SELECT column1, column2, ... 
FROM table_name;
```
```
SELECT * FROM table_name;
```

### **SELECT Example**

* Selects the "CustomerName" and "City" columns from the "Customers" table:

    ```
    SELECT CustomerName, City
    FROM Customers;
    ```
* Selects **all the columns** from the "Customers" table:
    ```
    SELECT * FROM Customers;
    ```

## **SQL SELECT DISTINCT Statement**

The `SELECT DISTINCT` statement is used to return only distinct (different) values.

### **SELECT DISTINCT Syntax**

```
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

### **SELECT DISTINCT Example**

* Selects only the DISTINCT values from the "Country" column in the "Customers" table:

    ```
    SELECT DISTINCT Country 
    FROM Customers;
    ```