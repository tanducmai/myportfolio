+++
date = 2022-03-16T16:15:06+10:30
title = "Database - SQL - Nested Queries"
slug = "database-sql-nested-queries"
aliases = "/database-sql-nested-queries"
description = "Database - SQL - Nested Queries"
thumbnail = "images/database/posts/sql/meme/meme-2.png"
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

1. [Aliases](#aliases)
1. [Nested Queries?](#nested-queries)
1. [Nested Query Rules](#rules)
1. [Qualifying Attribute Names](#qualifying-attribute-names)
1. [Operators](#operators)
1. [Compare with the JOIN Keyword](#compare-with-the-join-keyword)
1. [Nested Queries using Negation NOT
IN Operator](#nested-queries-using-negation-not-in-operator)
1. [Nested Queries using ALL
Operator](#nested-queries-using-all-operator)
1. [EXISTS and IN Operators](#exists-and-in-operators)
1. [Nested Queries using EXISTS
Operator](#nested-queries-using-exists-operator)
1. [Nested Queries using NOT EXISTS
Operator](#nested-queries-using-not-exists-operator)
1. [Nested Queries in SELECT Clause](#nested-queries-in-select-clause)
1. [Nested Queries in FROM Clause](#nested-queries-in-from-clause)
1. [Comments on Nested Queries](#comments-on-nested-queries)

![SQL Meme](/images/database/posts/sql/meme/meme-2.png)

### Aliases

A Nested query is also called a Subquery or an Inner query.

### Nested Queries

A Nested query is a query within another SQL query and embedded within
the `WHERE` clause.

A Nested query is used to return a list of values that can be tested or
used in the main query as a condition to further restrict the data to be
retrieved.

### Nested query Rules

There are a few rules that every nested query must follow −

- Nested queries must be enclosed within parentheses.
- A nested query can have only one column in the SELECT clause, unless
  multiple columns are in the main query for the nested query to compare its
  selected columns.
- An ORDER BY command cannot be used in a nested query, although the main
  query can use an ORDER BY. The GROUP BY command can be used to perform
  the same function as the ORDER BY in a nested query.
- Nested queries that return more than one row can only be used with
  multiple value operators such as the IN operator.
- The SELECT list cannot include any references to values that evaluate
  to a BLOB, ARRAY, CLOB, or NCLOB.
- A nested query cannot be immediately enclosed in a set function.
- The BETWEEN operator cannot be used with a nested query. However, the
  BETWEEN operator can be used within the nested query.

Adapted from:
*[TutorialsPoint](https://www.tutorialspoint.com/sql/sql-sub-queries.htm)*.

A nested query is subject to the following restrictions -

- The select list of a nested query introduced with a comparison
  operator can include only one expression or column name (except that
  `EXISTS` and `IN` operate on `SELECT *` or a list, respectively).
- If the `WHERE` clause of an outer query includes a column name, it
  must be join-compatible with the column in the nested query select
  list.
- The *ntext*, *text*, and *image* data types cannot be used in the
  select list of nested queries.
- Because they must return a single value, nested queries introduced by
  an unmodified comparison operator (one not followed by the keyword
  `ANY` or `ALL`) cannot include `GROUP BY` and `HAVING` clauses.
- The `DISTINCT` keyword cannot be used with nested queries that include
  `GROUP BY`.
- The `COMPUTE` and `INTO` clauses cannot be specified.
- `ORDER BY` can only be specified when TOP is also specified.
- A view created by using a nested query cannot be updated.
- The select list of a nested query introduced with `EXISTS`, by
  convention, has an asterisk `*` instead of a single column name. The
  rules for a nested query introduced with `EXISTS` are the same as
  those for a standard select list, because a nested query introduced
  with `EXISTS` creates an existence test and returns TRUE or FALSE,
  instead of data.

Adapted from:
*[Microsoft](https://docs.microsoft.com/en-us/sql/relational-databases/performance/subqueries?view=sql-server-ver15)*.

### Qualifying Attribute Names

When it comes to nested queries, we usually prefix every attribute's
name with its relation's name (and a **.**) in order that there is no
confusion in case of duplicate attributes' names among different
relations.

### Operators

Nested queries can be used with the SELECT, INSERT, UPDATE, and DELETE
statements along with the operators like =, <, >, >=, <=, IN, BETWEEN,
etc. within the WHERE clause.

Thus, WHERE clause conditions can:

1. Compare an attribute expression with the result of another SQL query.

- **IN** - True if the attribute value exists in the results returned by
  the sub query.
- **NOT IN** - True if the attribute value being compared does NOT exist
  in the results returned by the sub query.

2. ScalarValue Operator < ANY | ALL > SelectSQL.

- **ANY** - True if at least one row returned by SelectSQL satisfies the
  comparison.
  - This is set by default if not specified.
- **ALL** - True if all rows returned by SelectSQL satisfy the
  comparison.

3. Use the existential quantifier on an SQL query.

- **EXISTS** - True if sub query returns a result.
- **NOT EXISTS**

### Compare with the `JOIN` keyword

For information on this keyword, refer to this
*[page](https://tanducmai.com/posts/database-sql-table-joins/)*.

Given the following relational schemas:

```text
Department(deptName, address, city)
PK(deptName)

Employee(firstName, lastName, dept, office, salary, city)
PK(firstName, lastName)
FK(dept) -> Department(deptName)
```

##### Example 1

Task - find all employees (and their information) who do not work in
departments in London.

```sql
SELECT E.*
FROM Employee AS E
WHERE E.dept IN (
    SELECT D.deptName
    FROM Department AS D
    WHERE city <> 'London'
);
```

Is equivalent to:

```sql
SELECT E.*
FROM Employee AS E JOIN Department AS D
ON E.dept = D.deptName
WHERE D.city <> 'London';
```

##### Example 2

Task - find the name of employees who work in departments that are
located in London city.

```sql
SELECT E.firstName + ' ' + E.lastName AS employeeName
FROM Employee AS E
WHERE E.dept IN (
    SELECT D.deptName
    FROM Department AS D
    WHERE D.city = 'London’
);
```

Is equivalent to:

```sql
SELECT E.firstName + ' ' + E.lastName AS employeeName
FROM Employee AS E INNER JOIN Department AS D
ON E.dept = D.deptName
WHERE D.city = 'London';
```

##### Example 3

Task - find the employees in the Planning department who have the same
first name as someone in the Production department.

```sql
SELECT firstName, lastName
FROM Employee
WHERE dept = 'Planning'
AND firstName IN (
    SELECT firstName
    FROM Employee
    WHERE dept = 'Production'
);
```

Is equivalent to:

```sql
SELECT E1.firstName, E1.lastName
FROM Employee AS E1 INNER JOIN Employee AS E2
ON E1.firstName = E2.firstName
WHERE E1.dept = 'Planning'
AND E2.dept = 'Production’;
```

### Nested queries using negation `NOT IN` Operator

Given the above relational schemas.

Task - find the departments in which there is no one named Brown.

```sql
SELECT D.deptName
FROM Department AS D
WHERE D.deptName NOT IN (
    SELECT E.dept
    FROM Employee AS E
    WHERE E.firstName = 'Brown'
);
```

### Nested queries using `ALL` Operator

Given the above relational schemas.

Task - find the department of the employee who earns the highest salary.

##### Using ALL

```sql
SELECT E1.dept
FROM Employee AS E1
WHERE E1.salary >= ALL (
    SELECT E2.salary
    FROM Employee AS E2
);
```

##### Not using ALL, but MAX / MIN (aggregate operators)

```sql
SELECT E1.dept
FROM Employee AS E1
WHERE E1.salary IN (
    SELECT MAX(E2.salary)
    FROM Employee AS E2
);
```

### Nested queries using `EXISTS` Operator

The EXISTS operator is used to test for the existence of any record in a
nested query.

The nested query is evaluated for each tuple of the main
(external/outer) query.

- Akin to the concept of nested loops in programming.

If the EXISTS operator is used, then for every tuple of the main query:

- The nested query is evaluated.
- TRUE is returned if the nested query returns one or more records.
  - If TRUE is returned, then the current tuple of the main query is executed.
  - Otherwise, then it is the turn of the next tuple of the main query.

For example, given the following relational schema:

```text
Student(studentID, firstName, lastName, email, phoneNumber)
PK(studentID)
```

Task - find students with the same name as another student.

```sql
SELECT S1.firstName + ' ' + S2.lastName AS [Student Name]
FROM Student AS S1
WHERE EXISTS (
    SELECT S2.*
    FROM Student AS S2
    WHERE S1.lastName = S2.lastName
    AND S1.studentID <> S2.studentID
);
```

Explanation:

- First, we evaluate the first tuple of the main query, and when we see
  the EXISTS operator within the WHERE clause, we know that we
  need to evaluate the nested query for a Boolean value.
  - The main query's current tuple is only executed when the nested
  query returns True.
- Inside the nested query, it does not matter what the SELECT clause
selects (so we simply puts a `*`).
- We then looks at the condition after the WHERE clause, evaluate it to
see if there is at least one tuple returned, then we can determine that
the True is returned.

### `EXISTS` and `IN` operators

The main difference between EXISTS and IN is that IN does a direct match
between the attribute(s) specified before the IN keyword and the values
returned by the nested query. This means that if a nested query returns
NULL, the entire IN query becomes NULL – which requires "IS NULL | IS
NOT NULL" operators in order for it to work efficiently.

By contrast, EXISTS does not check for an attribute by attribute match
between tuples, it just tests if a tuple was returned from the nested
query. This means EXISTS will return either True or False, resulting in
a more efficient comparison (no NULL values are returned).

### Nested queries using `NOT EXISTS` Operator

The EXISTS operators tests if results are returned by a nested query
rather than if a particular value exists in the nested query.

1. EXISTS = the nested query is not empty
1. NOT EXISTS = the nested query is empty

For example, find the names of all courses with no students enrolled:

```sql
SELECT C.courseName
FROM Course AS C
WHERE NOT EXISTS (
    SELECT E.*
    FROM Enrolment AS E
    WHERE C.courseID = E.courseID
);
```

### Nested queries in `SELECT` clause

A Nested SELECT query returns a value to be used as a result in the
main query.

- This is different from the previous examples where the nested query is
  used to help generate/condition the results of the main query.

Note: because the SELECT query is part of another SELECT clause, it must
only return ONE result – because it is being used to fill in a single
result.

For example, the following SQL statements raises an error since the
nested SELECT query returns a list of tuples.

```sql
SELECT
    E1.*,
    CONVERT(Decimal(6,2),
    E1.Salary * 100 / (
        SELECT E2.salary
        FROM Employee E2
        WHERE E2.dept = E1.dept
    ) AS percentMax
FROM Employee E1;
```

### Nested queries in `FROM` clause

A Nested FROM query returns a relation that can be used to help generate
the results in the main query.

For example, given the relational schema from
*[here](#compare-with-the-join-keyword)*.

Task - find all employees that live in the same capital city:

```sql
SELECT E1.*
FROM Employee AS E1
JOIN (SELECT E2.* FROM Employee AS E2) AS MySubQuery
ON E1.dept = MySubQuery.dept
WHERE E1.firstName <> MySubQuery.firstName
    AND E1.lastName <> MySubQuery.lastName
    AND E1.city = MySubQuery.city;
```

Is equivalent to:

```sql
SELECT MySubQuery.* FROM (
    SELECT E1.*
    FROM Employee AS E1 JOIN Employee AS E2
    ON E1.dept = E2.dept
    WHERE E1.firstName <> E2. firstName
        AND E1.lastName <> E2. lastName
        AND E1.city = E2.city
) AS MySubQuery;
```

Sample result:

|     | firstName | lastName | dept       | office | salary | city     |
| --- | ---       | ---      | ---        | ---    | ---    | ---      |
| 1   | Henry     | Mai      | Production | 69     | 50     | Adelaide |
| 2   | Katherine | Phan     | Production | 35     | 46     | Adelaide |

### Comments on nested queries

The use of nested queries may produce 'less declarative' queries, but
they can be more readable.

Complex queries can become very difficult to understand.

The use of variables must respect visibility rules.

- A variable can only be used within the query where it is defined, or
  within a query that is nested in the query where it is defined.
