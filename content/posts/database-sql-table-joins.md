+++
date = 2022-03-15T15:38:40+10:30
title = "Database - SQL - Table Joins"
slug = "database-sql-table-joins"
aliases = "/database-sql-table-joins"
description = "Database - SQL - Table Joins"
thumbnail = "images/database-physical-design/foreign-key.png"
tags = [
    "database",
    "fundamentals",
    "SQL",
    "DBMS",
    "physical design",
    "table joins",
]
categories = [
    "database",
]
draft = true
+++

### Table Of Contents

1. [JOIN Keyword](#join-keyword)
1. [Table Aliases](#table-aliases)
1. [INNER JOIN Keyword](#inner-join-keyword)
1. [Duplicate Column Names](#duplicate-column-names)
1. [Multiple Attributes in a Join
Condition](#multiple-attributes-in-a-join-condition)
1. [OUTER JOIN Keyword](#outer-join-keyword)

### `JOIN` keyword

Tables (relations) can be combined to form a new relation using the JOIN keyword.

This relation can have a combination of the attributes from the tables
used in the query.

Syntax:

```sql
SELECT <selectList> FROM TableA JOIN TableB
ON TableA.key = TableB.key;
```

For example:

**TableA**

| studentID | name  | addID |
| ---       | ---   | ---   |
| 001       | Henry | a1    |
| 002       | Duc   | a2    |

**TableB**

| addID | postcode |
| ---   | ---      |
| a1    | 5000     |
| a2    | 5010     |

Combine TableA and TableB produces TableC.

```sql
SELECT * FROM TableA JOIN TableB ON TableA.addID = TableB.addID
```

**TableC** (result)

| studentID | name  | addID | addID | postcode |
| ---       | ---   | ---   | ---   | ---      |
| 001       | Henry | a1    | a1    | 5000     |
| 001       | Duc   | a2    | a2    | 5010     |

##### Joined attributes

To re-create the information captured in the data, relations must be
merged together based on conditions that specify which attributes in one
relation match the same data in the attributes of the other relation.

This ordinarily follows the rule: TableB(FK) ~> TableA(PK) attributes.

In the above database design:

```sql
TableA.addID = TableB.addID
```

The addID attribute of TableA and the addID attribute of TableB are
called the **joined attributes**.

### Table Aliases

When querying, you may want to improve the readability of the JOIN
queries by renaming your relations with an alias.

It is useful where the relation is used more than once to distinguish
between different instances of the relation.

For example: given the following relational database:

```text
Department(deptName, address, city)
PK(deptName)

Employee(firstName, lastName, dept, office, salary, city)
PK(firstName, lastName)
FK(dept) -> Department(deptName)
```

Bad design:

```sql
SELECT Employee.firstName, Department.city
FROM Department JOIN Employee
ON Department.deptName = Employee.dept
WHERE lastName = 'Brown';
```

Better design:

```sql
SELECT E.firstName, D.city
FROM Department AS D JOIN Employee AS E
ON D.deptName = E.dept
WHERE lastName = 'Brown';
```

### INNER JOIN keyword

The type of joining two relations we have been discussing so far is the
same as using the INNER JOIN keyword.

For an explanation of why it is called an INNER JOIN, refer to the
following algorithm:

```sql
for each employee x in Employee
    for each department y in Department
        if x.dept == y.deptname then
            output x + y tuple
        end if
    end for y
end for x
```

If an employee's tuple does not match any department's tuple in a join,
the employee's tuple is said to be *dangling* and thus dropped from the
output.

The following sql statements have the same meaning:

```sql
SELECT * FROM Department, Employee WHERE Employee.dept = Department.deptName
SELECT * FROM Department JOIN Employee ON Employee.dept = Department.deptName
SELECT * FROM Department INNER JOIN Employee ON Employee.dept = Department.deptName
```

### Duplicate column names

Using the same relational database as above, for each employee with
lastName Brown, list their firstName, the city where they live and the
city in which they work.

- Use the table's name to distinguish duplicate column names.

Incorrect query (ambiguous column name):

```sql
SELECT firstName, city, city
FROM Department AS D JOIN Employee AS E ON deptName = dept
WHERE lastName = 'Brown';
```

Correct query:

```sql
SELECT firstName, E.city, D.city
FROM Department AS D JOIN Employee AS E ON deptName = dept
WHERE lastName = 'Brown';
```

Note that "firstName" is unambiguous hence it does not need to be
qualified with the table from which it comes from.

### Multiple attributes in a join condition

![Multiple attributes](/images/database-sql-table-joins.png)

### `OUTER JOIN` keyword

This keyword is a variant of the JOIN keyword that keeps the *dangling*
tuples in the result.

It is achieved by
[padding](https://www.oxfordlearnersdictionaries.com/definition/english/pad_2) missing values with NULL where the tuples do
not match in both relations.

