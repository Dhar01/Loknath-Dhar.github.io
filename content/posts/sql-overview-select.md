---
title: "SQL Overview - 02"
date: 2022-02-23
tags: ["sql"]
draft: false
---

The **SELECT** statement is used to query the database and retrieve data that match the criteria.

The `SELECT` statement has five main clauses to choose from.

Format of the `SELECT` statement:

```sql
SELECT [ALL | DISTINCT] column1[,column2]
FROM [table1, table2]
[WHERE "conditions"]
[GROUP BY "column-list"] [HAVING "conditions]
[ORDER BY "column-list" [ASC | DESC] ]
```

Example:

```sql
SELECT name, age, salary
FROM employee
WHERE age > 40;
```

**ALL** and **DISTINCT** are keywords used to select either all (*default*) or the *distinct* or unique records in query results.

### DISTINCT

`DISTINCT` will discard the duplicate records for the columns specified after the **SELECT** statement.

```sql
SELECT DISTINCT age FROM employee_info;
```

### Aggregate functions

| Function | Description |
|----------|-------------|
| `MIN` | returns the smallest value in a given column |
| `MAX` | returns the largest value in a given column |
| `SUM` | returns the sum of the numeric values in a given column |
| `AVG` | returns the average value of a given column |
| `COUNT` | returns the total number of values in a given column |
| `COUNT(*)` | returns the number of rows in a table |

**Aggregate functions** are used to compute against a *returned column of numeric data* from `SELECT` statement. They summarize the results of a particular column of selected data.

Example:

```sql
SELECT AVG(salary) FROM employee WHERE title = 'Programmer';
```

This statement will return the number of rows in the employees table:

```sql
SELECT Count(*) FROM employee;
```

### GROUP BY

The **GROUP BY** clause will gather all of the rows together that contain data in the specified columns and will allow aggregate to be performed on the one or more columns.

```sql
SELECT column1, SUM (column2)
FROM "list-of-tables"
GROUP BY "column-list";
```

Multiple grouping columns example:

```sql
SELECT last_name, MAX(salary), dept
FROM employee
GROUP BY dept, last_name;
```

### HAVING

The **HAVING** clause allows to specify conditions on the rows for each group. Which rows should be selected will be based on the conditions.

> The `HAVING` clause should follow the `GROUP BY` clause.

```sql
SELECT column1, SUM(column2)
FROM 'list-of-tables'
GROUP BY "column-list"
HAVING "condition";
```

Example:

```sql
SELECT dept, AVG(salary)
FROM employee
GROUP BY dept
HAVING AVG(salary) > 20000;
```

### ORDER BY

**ORDER BY** is an optional clause which will allow to display the results of query in a sorted order based on the columns.

Syntax:

```sql
SELECT column1, SUM(column2)
FROM "list-of-tables"
ORDER BY "column-list" [ASC | DESC];
```

Example:

```sql
SELECT employee_id, dept, name, age, salary
FROM employee_info
WHERE dept = 'Sales'
ORDER BY salary, age DESC;
```

#### combining conditions & boolean operators

The **AND** operator can be used to join two or more conditions in the `WHERE` clause.

```sql
SELECT column1, SUM(column2) FROM "list-of-tables"
WHERE "condition1" AND "condition2";
```

The **OR** operator can be used to join two or more conditions in the `WHERE` clause.

```sql
SELECT employeeid, firstname, lastname, title, salary
FROM employee_info
WHERE (salary >= 45000.00) OR (title = 'Programmer');
```

### IN & BETWEEN

The **IN** conditional operator is a set membership test operator. It is used to test whether or not a value is *in* the list of values provided after the keyword **IN**.

```sql
SELECT employeeid, lastname, salary
FROM employee_info
WHERE lastname IN ('Hernandez', 'Jones', 'Roberts', 'Ruiz');
```

> One can also use **NOT IN** to exclude the rows in the list.

The **BETWEEN** conditional operator is used to test to see whether or not a value is *between* the two values stated after the keyword `BETWEEN`.

```sql
SELECT employeeid, age, lastname, salary
FROM employee_info
WHERE age BETWEEN 30 AND 40;
```

### Mathematical Functions

Standard ANSI SQL-92 supports the following first basic arithmetic operators:

- `+` : addition
- `-` : subtraction
- `*` : multiplication
- `/` : division

I am adding some functions which are not standard but they were available on several major database systems:

| name | description |
|------|-------------|
| `ABS[x]` | returns the absolute value of x |
| `SIGN[x]` | returns the sign of input x as -1, 0 or 1 |
| `MOD[x, y]` | modulo operator (*same as x%y*) |
| `FLOOR[x]` | returns the largest integer value that is less than or equal to x |
| `CEIL[x]` or<br> `CEILING[x]` | returns the smallest integer value that is greater than or equal to x |
| `POWER[x, y]` | returns the value of `x ** y` |
| `ROUND[x]` | returns the value of x rounded to the nearest whole integer |
| `ROUND[x, d]` | returns the value of x rounded to the number of decimal places specified by the value d |
| `SQRT[x]` | returns the square-root value of x |

Example:

```sql
SELECT ROUND(salary), firstname
FROM employee_info
```

### JOIN

The **JOIN** makes relational database systems *relational*.

`Join` allows to link data from two or more tables together into a single query result from one single `SELECT` statement.

```sql
SELECT "list-of-columns" FROM table1, table2
WHERE "search-condition";
```

> Single table database is sometimes referred to as *flat table*.

```sql
SELECT customer_info.firstname, customer_info.lastname, purchases.item
FROM customer_info, purchases
WHERE customer_info.customer_number = purchases.customer_number;
```

This *join* is known as an **Inner Join** or **Equijoin**.

Although the above will probably work, here is the ANSI SQL-92 syntax specification for an Inner Join using the preceding statement:

```sql
SELECT customer_info.firstname, customer_info.lastname, purchases.item
FROM customer_info INNER JOIN purchases
ON customer_info.customer_number = purchases.customer_number;
```
