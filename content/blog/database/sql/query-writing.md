+++
date = 2022-03-14T22:16:08+10:30
title = "Database - SQL - Query Writing"
slug = "database-sql-query-writing"
aliases = "/database-sql-query-writing"
description = "Database - SQL - Query Writing"
thumbnail = "images/database/blog/sql/query-writing/cheatsheet.png"
tags = [
    "database",
    "intermediate",
    "SQL",
    "DBMS",
]
categories = [
    "database",
]
draft = false
+++

### Table of Contents

1. [Why Query?](#why-query)
1. [SELECT Statement](#select-statement)
1. [WHERE Condition](#where-condition)
1. [DISTINCT Keyword](#distinct-keyword)
1. [AS Keyword](#as-keyword)
1. [ORDER BY Keyword](#order-by-keyword)
1. [TOP Keyword](#top-keyword)
1. [Summary](#summary)

![SQL syntax cheat sheet](/images/database/blog/sql/query-writing/cheatsheet.png)

### Why Query

Now that we have got our
[tables](https://tanducmai.com/blog/database-physical-design/) storing
[data](https://tanducmai.com/blog/database-sql-data-manipulation/)
(records), let's start asking questions (queries) about those data.

### `SELECT` statement

This statement is used to retrieve data from the database.

SELECT syntax:

```sql
SELECT <selectList> FROM <tableName> WHERE <conditions>;
```

1. The `SELECT` clause defines the target list of attributes/values to
be returned.
1. The `FROM` keyword defines the tables used by the query to obtain the
attribute values.
1. The `WHERE` clause is included to determine which tuples should be
retrieved.

- It specifies the conditions that each tuple must match in order to be
  included in the final result.

Examples:

| Query                                                   | Purpose                                                                             |
| ---                                                     | ---                                                                                 |
| `SELECT studentID, studentName FROM Student;`           | Select **specific** attributes from **all** tuples from Student                     |
| `SELECT * FROM Student;`                                | Select **all** attributes and **all** tuples from Student (display all records)     |
| `SELECT Student.* FROM Student;`                        | Select **all** attributes and **all** tuples from Student specifically.             |
| `SELECT * FROM Student WHERE StudentName = 'Henry Mai'` | Select **all** attributes and **all** tuples whose studentName value is 'Henry Mai' |

The SQL SELECT statement returns a new relation composed of the
attributes used in the query.

For example:

![SELECT example](/images/database/blog/sql/query-writing/select.png)

### `WHERE` condition

The expression (condition) after this clause evaluates to TRUE, FALSE,
or UNKNOWN for each row of data tested.

It is used in the search condition of WHERE clauses and HAVING clauses,
the JOIN conditions of FROM clauses, and other constructs where a
Boolean value is required.

Logical conditions are used:

- Multiple conditions can be chained using **AND**/**OR**.

| Condition     | Description                                   |
| ---           | ---                                           |
| `=`           | Equal                                         |
| `<>`          | Not equal                                     |
| `<`           | Less than                                     |
| `>`           | Greater than                                  |
| `<=`          | Less than or equal to                         |
| `>=`          | Greater than or equal to                      |
| `LIKE`        | Partial matches (string comparison)           |
| `NOT LIKE`    | Not like the partial matches                  |
| `IS NULL`     | Test an attribute value is empty (e.g. NULL)  |
| `IS NOT NULL` | Test an attribute has a value (e.g. NOT NULL) |

Note: LIKE condition

- E.g. s LIKE 'p'
- p must be surrounded by quotes.
- p may contain two special symbols:
  - _ = a single unknown character
  - % = zero or more unknown characters
    - Find the colours that have 'r' as the second letter and end in 'n':
    - colourName LIKE '_r%n' returns: B**r**ow**n**, G**r**ee**n**.

`BETWEEN` and `AND`

```sql
... WHERE price BETWEEN 100 and 150;
... WHERE price >= 100 AND price <= 150;
```

### `DISTINCT` keyword

This keyword is used to remove duplicate records from a given table.

For example, if DISTINCT is not used, the results may contain duplicate
values:

![Distances example](/images/database/blog/sql/query-writing/distinct.png)

### `AS` keyword

This keyword is used to rename an attribute or a table with an alias.

Such an alias only exists for the duration of the query.

AS syntax:

```sql
SELECT attr1 + attr2 + ... AS aliasName, ...
FROM TableName;
```

For example: The following SQL statement creates an alias named
'address' that combines four attributes (address, postalCode, city, and
country):

```sql
SELECT studentName, address + ', ' + postalCode + ' ' + city AS address
FROM Student;
```

Note: it requires double quotation marks *""* or square brackets *[]* if the alias
name contains spaces:

```sql
SELECT studentName AS student, contactName AS [Student Contact]
FROM Customers;
```

### `ORDER BY` keyword

This keyword is used to re-order (sort) the output of the query set in
ascending or descending order.

The result is set in ascending order by default, unless the `DESC`
keyword is used.

ORDER BY syntax:

```sql
SELECT <selectList>
FROM TableName
ORDER BY attributeName [DESC];
```

For example: list the contents of the Automobile table in descending
order of make and model (resort to the order of model if make is the
same).

![ORDER BY example](/images/database/blog/sql/query-writing/order-by.png)

### `TOP` keyword

This keyword is used to limit the number of matching records to return
based on the sort order.

It is mainly used with ordered records.

TOP syntax:

```sql
SELECT TOP number [PERCENT] attribute(s) | *
FROM TableName
[WHERE <condition>]
[ORDER BY <expression> [DESC]];
```

There are two types of values to specify after the Top keyword.

##### Use with a constant value

Return the top X values from a given table.

![TOP X example](/images/database/blog/sql/query-writing/top.png)

##### Use with a percentage value

Return a percentage of tuples from a given table.

For example, consider returning two per cent of the Student table which
has 214 tuples. Two per cent of 214 tuples is a fraction value (4.28),
SQL Server rounds it up to the next whole number - 5 tuples.

```sql
SELECT TOP 2 PERCENT
    studentID,
    lastName,
    firstName
FROM Student
WHERE lastName = 'Mai'
ORDER BY studentID;
```

### Summary

The SELECT statement is the most often used one to query the database.

It consists of 3 basic clauses: SELECT, FROM, and WHERE clauses.

1. FROM – identifies the relation(s) to query over.
1. WHERE – the conditions used to combine and filter the relations.
1. SELECT – the attributes or data to be returned.

![SQL syntax cheat sheet](/images/database/blog/sql/query-writing/cheatsheet.png)
