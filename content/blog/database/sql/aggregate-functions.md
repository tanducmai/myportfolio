+++
date = 2022-03-22T17:34:33+10:30
title = "Database - SQL - Aggregate Functions"
slug = "database-sql-aggregate-functions"
aliases = "/database-sql-aggregate-functions"
description = "Database - SQL - Aggregate Functions"
thumbnail = "/images/database/blog/sql/query-complete-syntax.png"
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

1. [Aggregate Queries?](#aggregate-queries)
1. [COUNT()](#count-function)
1. [SUM()](#sum-function)
1. [AVG()](#avg-function)
1. [MAX() & MIN()](#max-and-min-functions)
1. [Maths in SELECT Clause](#maths-in-select-clause)
1. [Multiple Aggregate Queries](#multiple-aggregate-queries)
1. [GROUP BY Clause](#group-by-clause)
1. [Aggregate queries with JOINS](#aggregate-queries-with-joins)
1. [HAVING Clause](#having-clause)
1. [HAVING and WHERE Clauses](#having-and-where-clauses)

![SQL Query Syntax](/images/database/blog/sql/query-complete-syntax.png)

### Aggregate Queries

Aggregate queries or aggregation is a method of performing computations over
sets of numerical values in multiple tuples of a relation and returning a single
value.

SQL provides users with many aggregate functions for aggregate queries,
including AVG, COUNT, SUM, MIN, MAX, etc.

Aggregate functions can be used within three clauses, namely SELECT, HAVING, and
ORDER BY.

- Group BY allows us to partition our relations into groups and then we
  can compute our aggregate values over each group independently.
- The HAVING condition allows us to filter our results based on
  aggregate values.

With the exception of COUNT, all aggregate functions:

- Apply to a single attribute.
- Ignore NULL values when performing the calculation.

### `COUNT` function

This function returns the number of tuples (an integer) that matches a
specified criterion.

##### COUNT() syntax

```sql
COUNT ( [DISTINCT] expression | * )
```

| Argument   | Semantic                                                        |
| ---        | ---                                                             |
| DISTINCT   | COUNT will operate only on one unique instance of every value   |
| expression | An expression of any type; no aggregate functions or subqueries |
| *          | Specify that all tuples should be counted; not support DISTINCT |

##### Examples

Given the following [example
database](https://tanducmai.com/blog/database-sql-set-operators/#sample-database).

:memo: Find the number of employees.

```sql
SELECT COUNT (E.*) AS employeeCount
FROM Employee AS E;
```

:memo: Find the number of tuples having a nonnull value for salary.

```sql
SELECT COUNT (E.salary) AS employeeCount
FROM Employee AS E;
```

:memo: Find the number of different values of salary.

```sql
SELECT COUNT (DISTINCT E.salary) AS employeeCount
FROM Employee AS E;
```

Note: DISTINCT will only return the first of duplicate values.

- If two people earn 40k, it will only be counted once, not twice.

### `SUM` function

This function returns the sum of all the numerical values of an attribute
(specified by the expression).

##### SUM() syntax

```sql
SUM ( [DISTINCT] expression )
```

| Argument   | Semantic                                                    |
| ---        | ---                                                         |
| DISTINCT   | SUM will operate only on one unique instance of every value |
| expression | A constant, column, function, or any combination of arithmetic, bitwise, and string operators; no aggregate functions or subqueries |

##### Return Types

Return the summation of all expression values in the most precise
expression data type.

| Expression result             | Return type    |
| ---                           | ---            |
| tinyint                       | int            |
| smallint                      | int            |
| int                           | int            |
| bigint                        | bigint         |
| decimal category (p, s)       | decimal(38, s) |
| money and smallmoney category | money          |
| float and real category       | float          |

:link:
*[Microsoft](https://docs.microsoft.com/en-us/sql/t-sql/functions/sum-transact-sql?view=sql-server-ver15)*

##### Example

Given the following [example
database](https://tanducmai.com/blog/database-sql-set-operators/#sample-database).

:memo: Find the sum of the salaries of the Administration department.

```sql
SELECT SUM (E.salary) AS salarySum
FROM Employee AS E
WHERE E.dept = 'Administration';
```

### `AVG` function

This function returns the average of all the numerical values of an attribute
(specified by the expression).

##### AVG() syntax

```sql
AVG ( [DISTINCT] expression )
```

| Argument   | Semantic                                                    |
| ---        | ---                                                         |
| DISTINCT   | AVG will operate only on one unique instance of every value |
| expression | An expression of the exact numeric or approximate numeric data type category (-bit); no aggregate functions or subqueries |

##### Return Types

The evaluated result of expression determines the return type.

| Expression result             | Return type           |
| ---                           | ---                   |
| tinyint                       | int                   |
| smallint                      | int                   |
| int                           | int                   |
| bigint                        | bigint                |
| decimal category (p, s)       | decimal(38, max(s,6)) |
| money and smallmoney category | money                 |
| float and real category       | float                 |

:link:
*[Microsoft](https://docs.microsoft.com/en-us/sql/t-sql/functions/avg-transact-sql?view=sql-server-ver15)*

##### Example

Given the following [example
database](https://tanducmai.com/blog/database-sql-set-operators/#sample-database).

:memo: Find the average of the salaries of the Production department.

```sql
SELECT AVG (E.salary) AS salaryAverage
FROM Employee AS E
WHERE E.dept = 'Production';
```

### `MAX` and `MIN` functions

These functions return maximum or minimum value in the expression.

- The return type is the same as the expression).
- MAX returns NULL when there is no row to select.

##### MAX() | MIN() syntax

```sql
MAX | MIN ( [DISTINCT] expression )
```

| Argument   | Semantic                                 |
| ---        | ---                                      |
| DISTINCT   | MAX and MIN will ignore duplicate values |
| expression | An expression of the exact numeric or approximate numeric data type category (-bit); no aggregate functions or subqueries |

##### Examples

Given the following [example
database](https://tanducmai.com/blog/database-sql-set-operators/#sample-database).

:memo: For expressions that are 'strings' (city, firstName), the alphabetical
order goes from the smallest letter (a) to the largest letter (w).

:memo: For expressions that are 'date' (dateOfBirth, orderDate), such as
a list of dates between 2002-07-03 and 2022-03-22).

```sql
SELECT MIN (C.date) FROM Customer AS C;
-- will return 2002-07-03
SELECT MAX (C.date) FROM Customer AS C;
-- will return 2022-03-22
```

### Maths in `SELECT` clause

### Multiple aggregate queries

Multiple aggregate queries can be combined into a singe query within
the SELECT clause.

However, it is only acceptable when each aggregate queries in the
combination only returns a single value.

```sql
SELECT (
    MAX (E.Salary) AS [Max Salary],
    MIN (E.Salary) AS [Min Salary]
FROM Employee AS E
```

Result:

| Max Salary | Min Salary |
| :---:      | :---:      |
| 80         | 40         |

### `GROUP BY` clause

Given the following [example
database](https://tanducmai.com/blog/database-sql-set-operators/#sample-database).

:memo: Find the highest salary paid in each department.

When conducting aggregate queries, there is an error that is often
encountered.

```sql
SELECT E.dept, MAX (E.salary) AS [Highest Salary in this Department]
FROM Employee AS E;
```

Our query completed with an error, displaying:

```text
Msg 8120, Level 16, State 1, Line 1
Column 'Employee.firstName' is invalid in the select list because it is
not contained in either an aggregate function or the GROUP BY clause.
```

Rationale: in the SELECT clause, especially <selectList>, we have an
aggregate function (MAX), together with a regular, non-aggregate
attribute.

- All non-aggregate attributes in the SELECT clause must appear in the
  GROUP BY clause.
- The GROUP BY clause collects data across multiple records and then
  groups the results by one or more attributes.
- The GROUP BY clause may have more attributes than those non-aggregate
  attributes in the SELECT clause.

Solution: use a GROUP BY clause followed by the non-aggregate
attribute(s), as instructed in the error message.

```sql
SELECT E.dept, MAX (E.salary) AS [Highest Salary in this Department]
FROM Employee AS E
GROUP BY E.delp;
```

Result:

| dept           | Highest Salary in this Department |
| ---            | ---                               |
| Administration | 45                                |
| Distribution   | 80                                |
| Planning       | 80                                |
| Production     | 50                                |

##### Use with other Keywords

The GROUP BY clause can be implemented with many other clauses, such as
AS, TOP, ORDER BY, DISTINCT, etc.

For example:

- This will display the same result as above but with Department names
  being placed in the reversed order.

```sql
SELECT E.dept, MAX (E.salary) AS [Highest Salary in this Department]
FROM Employee AS E
GROUP BY E.dept
ORDER BY E.dept DESC;
```

- This will display only the first result.

```sql
SELECT TOP 1 E.dept, MAX (E.salary) AS [Highest Salary in this Department]
FROM Employee AS E
GROUP BY E.dept
```

##### Multiple non-aggregate attributes

When there are multiple regular, non-aggregate attributes in the
<selectList>, we need to indicate all of them within the GROUP BY
clause.

###### Two non-aggregate attributes

:memo: Find the highest salary paid in each office in each department.

There are two ways of listing them. The result will be sorted based on
the second column in the GROUP BY clause.

1. Listing in the original order.

- The result will `ORDER BY` E.office

```sql
SELECT E.dept, E.office, MAX (E.salary)
FROM Employee AS E
GROUP BY E.firstName, E.office;
```

2. Listing in the reversed order.

- The result will `ORDER BY` E.firstName

```sql
SELECT E.dept, E.office, MAX (E.salary)
FROM Employee AS E
GROUP BY E.office, E.firstName;
```

###### More than two non-aggregate columns

:memo: Find the highest salary paid in each office in each department in
each city.

There are many ways of listing them. The result will be sorted based on
the first column in the GROUP BY clause.

In the below example, the result will `ORDER BY` E.city

```sql
SELECT E.dept, E.office, E.city, MAX (E.salary)
FROM Employee AS E
GROUP BY E.city, E.office, E.dept;
```

### Aggregate queries with `JOINS`

Given the following [example
database](https://tanducmai.com/blog/database-sql-set-operators/#sample-database).

:memo: Find the maximum salary among the employees who work in a
department based in London.

1. Join Employee with Department to take into account what city they
work in (not live in!) – filter on London.
- This returns many tuples.
2. Find the maximum salary from the filtered result – MAX(Salary).
- This returns the single value.

```sql
SELECT MAX (E. salary) AS MaxLondonSal
FROM Employee AS E INNER JOIN Department AS D
ON E.dept = D.deptName
WHERE d.city = 'London';
```

### `HAVING` clause

The HAVING clause is used to place conditions on the result of an
aggregate operator.

This clause is only used in the presence of aggregation.

For example, given the following [example
database](https://tanducmai.com/blog/database-sql-set-operators/#sample-database).

:memo: Find which departments spend more than 150 on salaries.

Correct query:

```sql
SELECT E.dept, SUM (E.salary) AS theSalary
FROM Employee AS E
GROUP BY E.dept
HAVING SUM (E.salary) > 150;
```

Incorrect query:

```sql
SELECT E.dept, SUM (E.salary) AS theSalary
FROM Employee AS E
GROUP BY E.dept
HAVING theSalary > 150;
```

Result:

| dept     | theSalary |
| :---:    | :---:     |
| Planning | 153       |

### HAVING and WHERE clauses

The `HAVING` clause allows us to apply conditions to the whole result of
aggregate functions and to check conditions that apply to the
whole group.

- Conditions involving **aggregate** operators must appear in a HAVING
  clause.

Whereas the `WHERE` clause applies conditions to 1 tuple at a time.

- Conditions involving **non-aggregate** operators must appear in the
  WHERE clause.

For example, given the following [example
database](https://tanducmai.com/blog/database-sql-set-operators/#sample-database).

:memo: Find the departments in which the average salary of employees
working in office 20 is higher than 25.

This will require a combination of a normal condition (WHERE clause) and
a aggregate condition (HAVING clause).

```sql
SELECT E.dept, AVG (E.salary)
FROM Employee AS E
WHERE E.office = '20'
GROUP BY E.dept
HAVING AVG (E.salary) > 25;
```

### Complete syntax of an SQL query

```sql
SELECT <selectList>
FROM <tableList>
WHERE <condition>
GROUP BY <groupingAttributeList>
HAVING <aggregateCondition>
ORDER BY <orderingAttributeList>
```

![SQL Query Syntax](/images/database/blog/sql/query-complete-syntax.png)
