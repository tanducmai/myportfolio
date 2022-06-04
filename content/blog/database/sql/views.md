+++
date = 2022-04-04T17:33:58+09:30
title = "Database - SQL - Views"
slug = "database-sql-views"
aliases = "/database-sql-views"
description = "Database - SQL - Views"
thumbnail = "/images/database/blog/sql/views.png"
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

1. [Database views](#database-views)
1. [VIEW Syntax](#view-syntax)
1. [Examples](#examples)
1. [Complex query](#complex-query)
1. [Aggregate on Aggregate](#aggregate-on-aggregate)
1. [Vertical inheritance](#vertical-inheritance)
1. [Horizontal inheritance](#horizontal-inheritance)
1. [Rename columns](#rename-columns)
1. [Important Notes](#important-notes)
1. [Updatable Views](#updatable-views)
1. [Notes on updatable views](#notes-on-updatable-views)

![Anatomy of a View](/images/database/blog/sql/views.png)

Image Source: *[C#
Corner](https://www.c-sharpcorner.com/UploadFile/f0b2ed/views-in-sql-server/)*

### Database views

Views are very useful for complex queries
Queries with lots of joins
Queries with complex conditions (e.g. aggregates)
Especially if the queries are used frequently

Views are necessary to express certain queries
queries that combine and nest aggregate operators
queries that make sophisticated use on the UNION operator

Views are useful for security/access control:
views can be defined to show parts of a table for specific users
Views can replace table access (depending on how they are defined)

Views are like virtual tables
It is created by a SELECT query
It does not store data
Materialised/updatable views can be created that store data in the original base tables

When the view is accessed, the expression is evaluated in real time and the result is presented
No different to writing and running a query

### `VIEW` Syntax

```sql
CREATE VIEW someName
AS
<SELECT QUERY>;
```

```sql
CREATE VIEW someName
AS
<SELECT QUERY>;
```

### Examples

```sql
CREATE VIEW SimpsonsFamily
AS
SELECT haracterID, characterName, characterRole
FROM Characters
WHERE (characterName LIKE '%Simpson');
```

Views can reference other views,

```sql
CREATE VIEW  AdminEmployee  (firstName, surname, salary) AS
SELECT firstName, surname, salary
FROM Employees
WHERE dept = 'Administration'
```

```sql
CREATE VIEW JuniorEmployee AS
SELECT * FROM AdminEmployee
WHERE salary < 50
```

### Complex query

Given the following [example
database](https://tanducmai.com/blog/database-sql-set-operators/#sample-database).

:memo: Find the department with the highest salary expenditure.

##### Not using a VIEW

```sql
SELECT dept
FROM Employees
GROUP BY dept
HAVING SUM(salary) = (
SELECT MAX(totalSalary) FROM        (   SELECT SUM(salary) AS totalSalary
    FROM Employees
    GROUP BY dept
) AS calc
)
```

##### Using a VIEW
```sql
CREATE VIEW SalaryBudget (dept,totalSalary) AS
SELECT dept, SUM(salary)
FROM Employees
GROUP BY dept
```

```sql
SELECT dept
FROM SalaryBudget
WHERE salaryTotal = (
    SELECT MAX (salaryTotal)
    FROM SalaryBudget
)
```

### Aggregate on Aggregate

:memo: Find the average number of staff per department.

##### Incorrect solution

can’t have cascade of aggregate operators.

```sql
SELECT AVG(COUNT(*))
FROM Employees
GROUP BY dept
```

```text
Cannot perform an aggregate function
on an expression containing an aggregate
or a subquery.
```

##### Correct solution, using a view

```sql
CREATE VIEW NoOfEmployees AS
    SELECT dept, COUNT(*) AS employeeCount
    FROM Employees GROUP BY dept
```

```sql
SELECT AVG(employeeCount) FROM NoOfEmployees
```

### Vertical inheritance

For example:

![Inheritance Example](/images/database-conceptual-design/inheritance-1.png)

When selecting records, use the VIEW (not the table)
When modifying records, use the tables (not the view)

### Horizontal inheritance

### Rename columns

Views can be used to rename columns and provide only specific data.

The below view returns only part (2 columns) from of the Simpsons table
and only members of the Simpsons family.

```sql
CREATE VIEW SimpsonsView

AS

SELECT characterID AS charID,
characterName AS charName
FROM Characters
WHERE characterName LIKE '%Simpson'
```

or

```sql
CREATE VIEW SimpsonsView (charID, charName)

AS

SELECT characterID, characterName
FROM Characters
WHERE characterName LIKE '%Simpson'
```

### Important Notes

Every column in the SELECT query that defines a view must have a name
Especially true of aggregate values, calculations and functions

Views cannot make use of the ORDER BY clause
If you want to re-order the results, you must do it when you call the view

Views in MS-SQL can be deleted even if they are used by other views
Calling a view that uses a view that has been dropped will throw a runtime error
PostgreSQL wins here :’(

Views are defined using the Data Definition Language (DDL)

```sql
CREATE VIEW xx AS <Query>
```

Views can also be modified using the same DDL
```sql
ALTER VIEW xx AS <Query>
DROP VIEW xx
```

### Updatable Views

Updateable Views allow the use of Data Manipulation Language (DML) in
addition to selecting records.
- INSERT, UPDATE and DELETE
- This will depend on the view definition (what tables the view
  contains!)
  - A Complex view may only allow UPDATE/DELETE in addition to SELECT
  - A Simple view that reflects some columns in one table may allow
    UPDATE/DELETE/INSERT
  - This is also dependent on the DBMS

### Notes on updatable views

A view is an Updateable View only if
1. It represents data from one table only (no JOINs)
1. It does not remove duplicates (no DISTINCT)
1. Attributes not present in the view allow NULL or have a DEFAULT value
   specified
1. It does not contain Aggregate or GROUP BY clauses
1. Subqueries in the view must not refer to the same table used by the
   view (but can refer to other tables)

Many of the rules applying to Updatable Views make sense:
- If it contains aggregates, or a DISTINCT or GROUP BY clause.
- It doesn’t make sense to insert/update a value that is calculated across
  multiple rows.
- If the View affects multiple base tables, inserting a record may violate FK
  constraints or create NULL values for attributes not present in the view.
