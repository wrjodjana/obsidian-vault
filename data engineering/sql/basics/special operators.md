 
### `ALL` keyword

1. Used in a `SELECT` clause, to explicitly specify that all rows should be returned including duplicates
```sql
SELECT ALL [column_name] FROM [table_name];
```
2. Used in comparison operators, in `WHERE` or `HAVING` clauses to compare a value against every value returned in subquery
```sql
SELECT [column_name] 
FROM [table_name] 
WHERE value > ALL (SELECT [column_name] FROM [table_name_2])
```

**Example:**

Products Table:

| ProductID | ProductName | SupplierID | CategoryID | Price |
| --------- | ----------- | ---------- | ---------- | ----- |
| 1         | Chais       | 1          | 1          | 18    |
| 2         | Chang       | 1          | 1          | 19    |
| 3         | Aniseed     | 1          | 2          | 20    |
| 4         | Anton       | 2          | 2          | 22    |
| 5         | Gumbo       | 2          | 2          | 21    |

OrderDetails Table:

| OrderDetailsID | OrderID | ProductID | Quantity |
| -------------- | ------- | --------- | -------- |
| 1              | 10248   | 1         | 12       |
| 2              | 10248   | 2         | 10       |
| 3              | 10248   | 3         | 15       |
| 4              | 10249   | 4         | 4        |
| 5              | 10249   | 1         | 8        |

Query:  Find all product names in the Products table
```sql
SELECT ALL ProductName
FROM Products
WHERE TRUE;
```

Output:

| ProductName |
| ----------- |
| Chais       |
| Chang       |
| Aniseed     |
| Anton       |
| Gumbo       |

Query: Find product names if all records in the OrderDetails have a quantity of 8 or 12
```sql
SELECT ProductName
FROM Products
WHERE ProductID = ALL (SELECT ProductID
					   FROM OrderDetails
					   WHERE Quantity=8 or Quantity=12)
```

Output:

| ProductName |
| ----------- |
| Chais       |

Query: Finding the maximum quantity in the order exceeds the average quantity of all orders
```sql
SELECT OrderID
FROM OrderDetails
GROUP BY OrderID
HAVING MAX(Quantity) > ALL(SELECT AVG(Quantity)
						   FROM OrderDetails
						   GROUP BY OrderID);
```

Output:

| OrderID |
| ------- |
| 10248   |

### `ANY` keyword

1. Used with comparison operators in `WHERE` or `HAVING` and condition is true if the comparison is satisfied for at least one value returned in the category
```sql
SELECT [column_name]
FROM [table_name]
WHERE value > ANY(SELECT [column_name] FROM [table_name_2])
```

**Example:**

Query: Find distinct category IDs of products that appear in the OrderDetails table
```sql
SELECT DISTINCT CategoryID
FROM Products
WHERE ProductID = any(SELECT ProductID
					  FROM OrderDetails)
```

Output:

| CategoryID |
| ---------- |
| 1          |
| 2          |

### `BETWEEN` keyword

**Definition:** used to filter data within a specified inclusive range

1. Used in `WHERE` or `HAVING` clauses to select values within a given range (inclusive of boundary values). Requires the `AND` keyword to connect lower and upper bounds.
```sql
SELECT [column_name]
FROM [table_name]
WHERE [column_name] BETWEEN value1 AND value2;
```
- equivalent to `WHERE [column_name] >= value1 AND column_name <= value2`

### `IN` keyword

**Definition:** used to filter data based on multiple possible values

1. Used in `WHERE` or `HAVING` clauses to check if  a value matches any value in a specified list or subquery.
```sql
SELECT [column_name]
FROM [table_name]
WHERE [column_name] IN (value1, value2, value3);

SELECT [column_name]
FROM [table_name]
WHERE [column_name] IN (SELECT column_name FROM table_name);
```