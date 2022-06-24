+++
date = 2022-03-09T23:40:53+10:30
title = "Physical Design"
slug = "database-physical-design"
aliases = "/database-physical-design/"
description = "Database - Physical Design"
thumbnail = "images/database/blog/physical-design/create-table.png"
tags = [
    "database",
    "fundamentals",
    "SQL",
    "DBMS",
    "physical design",
]
categories = [
    "database",
]
draft = false
+++

### Table Of Contents

1. [Physical Modelling?](#physical-modelling)
1. [SQL Overview](#sql-overview)
1. [Table Creation and Manipulation](#table-creation-and-manipulation)
1. [Table Definition](#table-definition)
1. [Table Modification](#table-modification)

### [Physical](https://www.oxfordlearnersdictionaries.com/definition/english/physical_1?q=physical) Modelling

After the [conceptual
design](https://tanducmai.com/blog/database-conceptual-design) and the
[physical design](https://tanducmai.com/blog/database-physical-design), the
next phase is to take the relational schemas and implement them using a DBMS.
- Structured Query Language (SQL) is a higher-level language (4GL) used to
  create the relational database and manage data within the database.

For example:

```sql
CREATE TABLE Project (
    projectName varchar(200),
    budget decimal(6,2),
    manager varchar(200),
    CONSTRAINT PK_Project PRIMARY KEY (projectName),
    CONSTRAINT FK_Project_Manager FOREIGN KEY (manager) REFERENCES Manager (name)
);
```

### SQL Overview

##### Categorisation

SQL commands can be categorised into:

1. **Data Definition Language** (DDL – add, modify, and delete relations and
   attributes in a relational database)

```sql
CREATE TABLE Employee (
    name varchar(200),
    birthDate date,
    CONSTRAINT PK_Employee PRIMARY KEY (name)
);
```

2. **Data Manipulation Language** (DML – add, modify, delete, and retrieve
   data in a relational database)

```sql
SELECT * FROM Employee
WHERE DatePart(y, birthDate) >= 1990
ORDER BY name;
```

##### Features

SQL commands have several important aspects:

1. SQL contains Keywords that act on the table and attributes:
- Commands are case insensitive
- SELECT = select = SeLECt
- Upper case is often used to highlight keywords that evoke actions.

2. A single semi-colon separates individual SQL statements by indicating
   where a statement ends:

```sql
SELECT
         S.Businessentityid, E.Jobtitle
  FROM
         Sales.Salesperson
        AS S
         INNER JOIN
         Humanresources.Employee
                       AS E
              ON E.Businessentityid = S.Businessentityid;
```

3. SQL Commands and Statements ignore excess white space:

- They can be written in one long sentence or broken into separate lines of
  text.
- Breaking up statements onto individual lines helps with readability.

##### Syntax

The following rules are used in this blog post:

- *Italic*/normal font indicates a user input value (number or name).
- **Bold**/CAPITALISED font indicates keywords,
- Elements in square brackets **(** and **)** can appear 0 or 1 times.
- Elements in braces **{** and **}** can appear 0, 1 or more times.
- The *|* symbol delimits alternative choices .
- Angle brackets **<** and **>** are used with **|** to group choices and
  indicate that something must appear exactly once.
- None of the above: ,,{,},<,>, and | are part of SQL. They are symbols used to
  help describe possible SQL statements.

### Table Creation and Manipulation

Key Table Manipulation SQL commands:

1. **CREATE** - Creates a new table in the relational database.
1. **ALTER** - Modifies an existing table in a relational database.
1. **DROP** - Permanently removes a table in a relational database.

### Table Definition

![CREATE TABLE command](/images/database/blog/physical-design/create-table.png)

An SQL table (relation) consists of:
- An ordered set of attributes.
- The order is the order in which they were listed in the CREATE TABLE
  statement.

When creating a table using SQL, each attribute of the relation must be
assigned a data type (called an **attribute domain**).

This dictates the type and length of future data to be stored.

For a list of common Database data types, please refer to
[here](https://tanducmai.com/blog/database-relational-concepts/#domains).

Note: It is important to choose data types cautiously:
- Only use *int*/*decimal* where calculations are concerned.
- Ensure enough number of digits/characters is assigned. Think about:
  - Can you store the total value - allow for price increase, especially sum.
  - can you store someone's complete hyphenated name?
- Be careful when using *char*, especially if you are using it to populate a
  drop down list - it can cause issues by padding text with white space.
  - Use *varchar* instead.

1. **decimal(m, n)** data type:

- For example: decimal(5, 2)
- Stores a number containing 5 digits, 2 of which are decimal places.
- 5 = precision, 2 = scale
- Acceptable numeric value from -999.99 to 999.99.
- Note: Choose size (precision) carefully:
  - Decimal(3,2) will only store values of items up to $9.99.
  - Choose carefully when storing increasing/growing totals.

2. **int** data type

- Integer value, range of values implementation dependent.
- Note: Do NOT store general information in numeric fields:
  - No House numbers (e.g. Unit 1A)
  - No Phone numbers (e.g., 1800 CALL-ME, (08), +61, 0434 xxx xxx)
  - No Account numbers (e.g. 0041 xxx xxx)
  - Only values you need to add/subtract/multiply or `ORDER BY`.

3. **Default** domain values

- Define the value of the attribute when it is not specified during row
  insertion.
- For example:

```sql
DEFAULT <defaultValue | NULL >
```

- defaultValue represents a value compatible with the domain, in the form of a constant or an expression.
- E.g specify ‘True’ as the default for a BIT field:

```sql
smartStudent BIT DEFAULT 'True'
enjoyLearning BIT DEFAULT 'False'
dateOfBirth DATETIME GetDate()
```

4. **NULL**

- If no default value is given, then NULL is used.
- In Relational Database, `NULL` is a value entered to indicate:
  - A value that does not yet exist (to be entered later or was never
    collected).
  - An optional value (not relevant to the current record).
  - A missing value (the data was never captured for the given record or some
    other unknown reasons).
- If you don’t know the value of an attribute, put NULL.
- NULL can have painful consequences in queries.
- NULL in operation:
  - 'Henry' + NULL = NULL
  - If `x = NULL`, then `4*x` is still `NULL`.
- For example:
  - Student(studentID, studentName, gpa)
  - In SQL, attributes like studentName can be specified as `NOT NULL`.

![NULL example](/images/database/blog/physical-design/null.png)

5. Constraints

- Please head to this
  *[post](https://tanducmai.com/blog/database-sql-table-constraints)* for a
  comprehensive explanation of constraints.

### Table Modification

Two SQL key words are defined to update table schemas: ALTER and DROP

- ALTER TABLE TableName ...
- ALTER DOMAIN domainName ...
- DROP TABLE TableName CASCADE
- DROP DOMAIN domainName CASCADE

```sql
ALTER TABLE Student Add address varchar(100);
ALTER TABLE Courses ADD maxClassSize int DEFAULT 30;
DROP TABLE Courses CASCADE;
```

For full example, please refer to
*[here](http://msdn.microsoft.com/en-au/library/ms190273.aspx)*.

1. **Add a new attribute**

```sql
ALTER TABLE TableName ADD newAttribute dataType;
ALTER TABLE Student ADD dateOfBirth date;
```

2. **Remove a existing attribute**

```sql
ALTER TABLE TableName DROP oldAttribute;
ALTER TABLE Student DROP dateOfBirth;
```

3. **Completely remove a table from an existing database**

```sql
DROP TABLE TableName
DROP TABLE Student
DROP TABLE Course
```

- Note: where FK(s) are involved, the order in which tables are dropped is
  important.
- Course and Student tables are referred to by the Enrolment table.
- Thus, they cannot be dropped before Enrolment as this would violate the FK
  constraints (contracts).
