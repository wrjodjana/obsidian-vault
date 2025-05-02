
### Operators

**Arithmetic Operators**
- `+` - perform addition operation on data values
- `-` - perform subtraction operation on data values
- `/` - works with `ALL` keyword and calculates division operations
- `*` - perform multiplication operation on data values
- `%` - modulus is used to get remainder when data is divided by another

Example:

```sql
SELECT emp_salary, emp_salary * 1.05 AS "Revised Salary" FROM employee;
```

Output:

| emp_salary | Revised Salary |
|:----------:|:--------------:|
|   50000    |     52500      |
|   60000    |     63000      |
|   45000    |     47250      |
**Comparison Operators**
- `=` - equal to
- `>` - greater than
- `<` - less than
- `>=` - greater than or equal to
- `<=` - less than or equal to
- `<>` - not equal to

Example:

```sql
SELECT * FROM MATHS WHERE MARKS=50;
```

Output:

| ROLL_NUMBER | S_NAME | MARKS |
|:-----------:| ------ | ----- |
|      5      | MOHAN  | 50    |

**Logical Operators**
- `AND` - compares two booleans as expressions 