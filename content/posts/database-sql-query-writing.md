+++
date = 2022-03-18T22:16:08+10:30
title = "Database - SQL - Query Writing"
slug = "database-sql-query-writing"
aliases = "/database-sql-query-writing"
description = "Database - SQL - Query Writing"
thumbnail = "images/sql-meme.png"
tags = [
    "database",
    "fundamentals",
    "SQL",
    "DBMS",
    "physical design",
    "query writing",
]
categories = [
    "database",
]
draft = true
+++

### Table of Contents

1. [Why Query?](#why-query)
1. [SELECT Statement](#select-statement)
1. [WHERE Condition?](#where-condition)
1. [DISTINCT](#distinct)

### Why Query

Now that we have got our
[tables](https://tanducmai.com/posts/database-physical-design/) storing
[data](https://tanducmai.com/posts/database-sql-data-manipulation/)
(records), let's start asking questions (queries) about those data.

### `SELECT` statement

This statement is used to retrieve data from the database.

Syntax:

```sql
SELECT <attributes> FROM <tableName> WHERE <conditions>;
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

![SELECT example](/images/database-sql-query-writing/select.png)

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
| `LIKE`        | Partial matches (string comparison).          |
| `NOT LIKE`    | Not like the partial matches                  |
| `IS NULL`     | Test an attribute value is empty (e.g. NULL)  |
| `IS NOT NULL` | Test an attribute has a value (e.g. NOT NULL) |

With the LIKE condition, use a ‘_’ for a single unknown character.
- Use ‘%’ for zero or more unknown characters: LIKE ‘%a%’ returns all
  words containing ‘a’.

BETWEEN and AND

```sql
... WHERE price BETWEEN 100 and 150;
... WHERE price >= 100 AND price <= 150;
```

### `SELECT DISTINCT` statement
