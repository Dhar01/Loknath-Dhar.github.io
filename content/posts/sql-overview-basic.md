---
title: "SQL Overview - 01"
date: 2022-02-22
tags: ["SQL"]
draft: false
author: Me
---

This is a *note* type post for personal reference.  I am learning SQL right now and for the learning purpose, I chose two websites:
1. [SQL Course](https://www.sqlcourse.com/);
2. [SQLBolt](https://sqlbolt.com/);

For awesome learning experience, my advice is to follow one of them according to your preference. This post is just a summary of those content.

Also, if anyone wants to practice SQL, see [Hackerrank's SQL problem-set](https://www.hackerrank.com/domains/sql).

> This is still in the early stage. Any suggestions will be appreciated.

- - -
(update 31 Mar, 2022): I got an awesome website: check [Animate SQL](https://animatesql.com/)!

- - -

A **relational database** system contains one or more objects called **tables**. Tables are identified by their names and are comprised of *columns* and *rows*.

### SELECT

The **SELECT** statement is used to query the database and retrieve selected data that match the criteria we specify.

> All statements end with an `;`.

```SQL
SELECT column FROM table_name;
```

> Use `*` to select all columns.

### WHERE

The **WHERE** clause specifies which data or rows will be returned or displayed based on the criteria described after the keyword `WHERE`.

Conditional selections used in the `WHERE` clause:
| Sign | Meaning |
|------|---------|
| `=` | Equal |
| `>` | Greater than |
| `<` | Less than |
| `>=` | Greater than or equal |
| `<=` | Less than or equal |
| `< >` | Not equal to |
| `LIKE` | see details below |

The **LIKE** <ins>pattern matching operator</ins> can also be used in the conditional selection of the where clause.

It is a very powerful operator that allows selecting only rows that are *like* what is specified. The **percent** sign (`%`) can be used as a wild card to match any possible character that might appear before or after the characters specified.

```SQL
SELECT first, last, city
    FROM employee_info
    WHERE first LIKE 'Er%';
```

### CREATE TABLE

The **CREATE TABLE** statement is used to create a new table.

```sql
CREATE TABLE table_name
    (
        column1 data_type,
        column2 data_type,
        column3 data_type
    );
```

Example:

```sql
CREATE TABLE employees (
                        name varchar(30),
                        position varchar(30),
                        age number(3),
                        salary(8,2)
                       );
```

Common data types:

| type | description |
|------|-------------|
| `char` (size) | Fixed-length character string, size is specified in parenthesis. Max 255 bytes. |
| `varchar` (size) | Variable-length character string. Max size is specified in parenthesis. |
| `number` (size) | Number value with a max number of column digits specified in parenthesis. |
| `date` | Date value |
| `number` (size, d) | Number value with a maximum number of digits of *size* total, with a maximum number of `d` digits to the right of the decimal. |

A **constraint** is a rule associated with a column that the data entered into that column must follow the rules. 

### INSERT INTO a table

The **INSERT INTO** statement is used to insert or add a row of data into the table.

```sql
INSERT INTO table_name
    (first_column, .... last_column)
    VALUES (first_value, .... last_value);
```

> All strings should be enclosed between single quotes `'string'`.

Example:

```SQL
INSERT INTO employees (name, position, age, salary)
    VALUES ('Dirk Smith', 'Programmer', 32, 45300.00),
        ('Lokanth Dhar', 'Admin', 26, 35000.00),
        ('Muidul Islam', 'Doctor', 26, 40000.00);
```

### UPDATE records

The **UPDATE** statement is used to update or change records that match specified criteria.

```SQL
UPDATE table_name
    SET column_name = new_value, next_column = new_value2
    WHERE column_name
    OPERATOR value and|or column OPERATOR value;
```

Example:

```sql
UPDATE phone_book
    SET area_code = 623
    WHERE prefix = 979;
    
UPDATE phone_book
    SET last_name = 'Smith', prefix = 555, suffix = 9292
    WHERE last_name = 'Jones';
```

### DELETE records

The **DELETE** statement is used to delete records or rows from the table.

```SQL
DELETE FROM table_name
    WHERE column_name
    OPERATOR value;
```

example:

```SQL
DELETE FROM employee; -- all records will be deleted

DELETE FROM employee
    WHERE first_name = 'Mike' or first_name = 'Eric';
```

> To insert comment, use `--`

# DROP a table

The **DROP TABLE** command is used to delete a table and all rows in the table.

To delete an entire table including all of its rows:

```SQL
DROP TABLE table_name
```
