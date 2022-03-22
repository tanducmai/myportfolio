+++
date = 2022-03-21T10:34:07+10:30
title = "Database - SQL - Set Operators"
slug = "database-sql-set-operators"
aliases = "/database-sql-set-operators"
description = "Database - SQL - Set Operators"
thumbnail = "images/sql-meme-2.png"
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

1. [Sample Database](#sample-database)
1. [SET Operators](#set-operators)
1. [UNION Operator](#union-operator)
1. [UNION ALL Operator](#union-all-operator)
1. [INTERSECT Operator](#intersect-operator)
1. [INTERSECT ALL Operator](#intersect-all-operator)
1. [INTERSECT and INNER JOIN](#intersect-and-inner-join)
1. [EXCEPT Operator](#except-operator)

### Sample Database

The below two relations will be used as examples for this post.

![Sample Database -
Employee](/images/database-sql-set-operators/sample-employee.png)

![Sample Database -
Department](/images/database-sql-set-operators/sample-department.png)

### SET Operators

Set operators are used to combine tuples of query results.

Standard SQL syntax with set operators:

- Inside a SelectSQL statement, a WHERE clause and some keywords (e.g.
  ORDER BY) can be included.

```sql
SelectSQL
< UNION|INTERSECT|EXCEPT [ALL] >
SelectSQL
```

A set is a result relation (e.g. results returned by a SELECT query
{SelectSQL}).

A set operator has two sets (returned from the two SELECT
queries) surrounding that set operator.

- Both sets must have the same number of attributes (columns).
- Both sets must have compatible attributes (same data types).
  - Note: NULL values can be of any data type.
- The attributes in both sets must be in the same order.

### `UNION` operator

The UNION set operator is used to combine query results, returning a
combination of the tuples from both sets, hence the word
[union](https://www.merriam-webster.com/dictionary/union).

- Duplicates are removed.

UNION syntax:

```sql
SelectSQL
UNION
SelectSQL
```

For example, given the above [sample database](#sample-database):

Task - list the first names and last names of employees.

```sql
SELECT E1.firstName AS name
FROM Employee AS E1
UNION
SELECT E2.lastName
FROM Employee AS E2
```

Result - a new relation having only one attribute (name).

- Each tuple contains one value that may either be a first name or a
  last name of an employee.
- No duplicate values.

### `UNION ALL` operator

The UNION ALL set operator serves a similar purpose to the UNION
keyword. The only discrepancy is that duplicate values are retained.

UNION ALL syntax:

```sql
SelectSQL
UNION ALL
SelectSQL
```

### `INTERSECT` operator

The INTERSECT set operator is also used to combine query results,
returning only the tuples that appear in both sets, hence the word
[intersection](https://www.ldoceonline.com/dictionary/intersection).

INTERSECT syntax:

```sql
SelectSQL
INTERSECT
SelectSQL
```

For example, given the above [sample database](#sample-database):

Task - find the first names of employees that are also last names.

```sql
SELECT E1.firstName AS name
FROM Employee AS E1
INTERSECT
SELECT E2.lastName AS name
FROM Employee AS E2;
```

Is equivalent to:

```sql
SELECT DISTINCT E1.firstName
FROM Employee AS E1 INNER JOIN Employee AS E2
ON E1.FirstName = E2.lastName;
```

Is also equivalent to:

```sql
SELECT DISTINCT E1.firstName AS name
FROM Employee AS E1
WHERE E1.firstName IN (
    SELECT E2.lastName AS name
    FROM Employee AS E2
);
```

Is also equivalent to:

```sql
SELECT DISTINCT E1.firstName AS name
FROM Employee AS E1
WHERE EXISTS (
    SELECT E2.* FROM Employee AS E2
    WHERE E1.firstName = E2.lastName
);
```

Result - a new relation having only one attribute (name).

- The number of tuples represents the number of first names that are
  also last names.

### `INTERSECT ALL` operator

Akin to the UNION ALL operator, appending ALL to the INTERSECT operator
will retain duplicate values.

INTERSECT ALL syntax:

```sql
SelectSQL
INTERSECT ALL
SelectSQL
```

### `INTERSECT` and `INNER JOIN`

|            | INTERSECT operator | INNER JOIN keyword |
| ---        | :---:              | :---:              |
| Duplicates | :x:                | :white_check_mark: |
| Nulls      | :white_check_mark: | :x:                |

The two are very different:

1. The former is a set operator that compares every tuple between two
   sets and can never return more tuples than in the smaller relation.
1. The latter is a keyword that generally matches on a limited number of
   attributes and can return zero or more tuples in either relation.

:link: *[stackoverflow](https://stackoverflow.com/a/51775740/16999206u)*

### EXCEPT operator

Unlike INTERSECT, the EXCEPT set operator only returns the tuples from
the left set (they must not be included in the right set), hence the
word
[exception](https://www.oxfordlearnersdictionaries.com/definition/english/exception?q=exception).

EXCEPT syntax:

```sql
SelectSQL
EXCEPT
SelectSQL
```

For example, given the above [sample database](#sample-database):

Task - find the first names of employees that are not last names.

```sql
SELECT E1.firstName AS name
FROM Employee AS E1
EXCEPT
SELECT E2.lastName AS name
FROM Employee AS E2;
```

Is equivalent to:

```sql
SELECT DISTINCT E1.firstName AS name
FROM Employee AS E1
WHERE E1.firstName NOT IN (
    SELECT E2.lastName AS name
    FROM Employee AS E2
);
```

Is also equivalent to:

```sql
SELECT DISTINCT E1.firstName AS name
FROM Employee AS E1
WHERE NOT EXISTS (
    SELECT E2.* FROM Employee AS E2
    WHERE E1.firstName = E2.lastName
);
```

Result - a new relation having only one attribute (name).

- The number of tuples represents the number of first names that are not
  last names.
