+++
date = 2022-03-10T23:40:53+10:30
title = "Database - SQL - Table Constraints"
slug = "database-sql-table-constraints"
aliases = "/database-sql-table-constraints"
description = "Database - SQL - Table Constraints"
thumbnail = "images/database/posts/physical-design/foreign-key.png"
tags = [
    "database",
    "fundamentals",
    "SQL",
    "DBMS",
    "physical design",
    "constraints",
]
categories = [
    "database",
]
draft = false
+++

### Table Of Contents

1. [Definition](#definition)
1. [Hypotheses](#hypotheses)
1. [Syntax](#syntax)
1. [Categorisation](#categorisation)
1. [Intra-relational Constraints](#intra-relational-constraints)
1. [Inter-relational Constraints](#inter-relational-constraints)

### Definition

Constraints are clauses that need to be satisfied by data in the database.

Constraints are like contracts to guard against bad data.

Data that does not meet the rules of a given constraint will not be
saved to the database.

- The whole tuple (new record) gets rejected and the DBMS throws an SQL Error.
- For example:
  - PRIMARY KEY Violation
  - FOREIGN KEY Violation
  - CHECK CONSTRAINT Violation

### Hypotheses

Consider this example:

```sql
Students(studentID, studentName, gpa)
Enrolment(studentID, courseID, mark)
```

If there is no constraint:
1. What if we insert a tuple into Enrolment, but there is no
   corresponding student?
1. What is we delete a student?

### Syntax

```sql
CREATE TABLE Enrolment (
    student int,
    course int,
    mark decimal(3, 2),
    CONSTRAINT PK_Enrolment PRIMARY KEY (course, student),
    CONSTRAINT FK_Enrolment_Student FOREIGN KEY (student) REFERENCES Student (studentID),
    CONSTRAINT FK_Enrolment_Student FOREIGN KEY (course) REFERENCES Course (courseID),
    CONSTRAINT checkMark CHECK (mark >= 0 AND mark <= 100)
);
```

### Categorisation

There are two major constraint types:

1. [INTRA](https://www.oxfordlearnersdictionaries.com/definition/english/intra?q=intra) - Relational
1. [INTER](https://www.oxfordlearnersdictionaries.com/definition/english/inter_2) - Relational

### Intra-Relational Constraints

Those that affect attributes *within a table*.

Attribute constraints – checked each time the attribute's value is modified.

- Domain
  - The data type (varchar(n), int, decimal(m, n), etc.)
  - Ensures data is of the correct type.
- PRIMARY KEY
  - `PRIMARY KEY (studentID)`
  - Ensures a record does not get entered more than twice.
- UNIQUE KEY
  - `UNIQUE (emailID)`
  - Forces each emailID to be unique (a Candidate/alternate Primary
    Key).
- NOT NULL
  - `studentName NOT NULL`
  - Forces a value to be entered.
- CHECK
  - `CHECK (mark >=0 AND mark <= 100)`
  - Ensures a value is in a given range (dates, decimals, etc.)
- IDENTITY
  - Not a constraint, but a *property*.
  - `PRIMARY KEY (studentID) IDENTITY`
  - Makes the studentID an auto-incrementing number (thus always
    unique).
  - Only works for the int data type.

1. **An OK Approach**

```sql
CREATE TABLE ColumnLevelConstraints (
    id int PRIMARY KEY,
    startDate date NOT NULL,
    endDate date NOT NULL,
    dateChecked date CHECK (dateChecked > '01/Aug/2015') NOT NULL
);
```
2. **A recommended Approach**

```sql
CREATE TABLE ColumnLevelConstraints (
    id int,
    startDate date NOT NULL,
    endDate date NOT NULL,
    dateChecked date NOT NULL,
    CONSTRAINT PK_TableName PRIMARY KEY (id),
    CONSTRAINT dateCheck CHECK (dateChecked > '01/Aug/2015')
);
```

### Inter-Relational Constraints
Those that affect attributes and values *across tables*.

Foreign Key (referential) constraints:

- Is a contract between tables to ensure a related record exists (e.g.
  no orphan records).
- Syntax:
  - For single or multiple attribute FK(s).
  - `FOREIGN KEY (Attribute {, Attribute}) REFERENCES TableName
    (Attribute {, Attribute})`
- For example:
  - FOREIGN KEY (student) REFERENCES Student(studentID)

A good approach:

```sql
CREATE TABLE Enrolment (
    student int,
    course int,
    mark int,
    CONSTRAINT PK_Enrolment PRIMARY KEY (student, course),
    CONSTRAINT FK_Enrolment_Student FOREIGN KEY (student) REFERENCES Student (studentID),
    CONSTRAINT FK_Enrolment_Course FOREIGN KEY (course) REFERENCES Course (courseID)
);
```

FK constraints can have reaction policies in response to violations of
referential integrity.

- These operate on the secondary/child table, after changes made to the
  primary/parent table.
- Violations may be introduced by updates on the referenced attribute or
  by row deletions.

Consider the Enrolment table referencing the Student table when a
student is deleted.

![FK Constraint](/images/database/posts/physical-design/foreign-key.png)

- `ON UPDATE | DELETE NO ACTION` - no action is performed with the child
  data when the parent data is deleted or updated.
  - Do not permit the change – default behaviour.
- `ON UPDATE | DELETE CASCADE` - the child data is either deleted or
  updated when the parent data is deleted or updated.
  - Are you going to lose anything important?
- `ON UPDATE | DELETE SET NULL` - the child data is set to NULL when the
  parent data is deleted or updated.
  - Does the FK column allow NULL values? (is it part of a PK/NOT NULL?)
    – orphan records.
- `ON UPDATE | DELETE SET DEFAULT` - the child data is set to their
  default values when the parent data is deleted or updated.

```sql
CREATE TABLE Enrolment (
    student char(5) REFERENCES Student (studentID)
        ON UPDATE CASCADE
        ON DELETE CASCADE,
    course char(5) REFERENCES Course (courseID)
        ON UPDATE CASCADE
        ON DELETE CASCADE,
    mark int,
    CONSTRAINT PK_Enrolment PRIMARY KEY (student, course)
    CONSTRAINT validMark CHECK (mark >= 0 AND mark <= 100),
);
```

Same Enrolment table but with constraint names.
- Naming a constraint allows you to drop it from the table when needed.
  - Otherwise, the whole table has to be dropped and re-created: data
    lost.
  - It can also help with debugging a query when reading error messages.

```sql
CREATE TABLE Enrolment (
    student int,
    course int,
    mark int,
    CONSTRAINT PK_Enrolment PRIMARY KEY (student,course),
    CONSTRAINT validMark CHECK (mark >= 0 AND mark <= 100),
    CONSTRAINT FK_Enrolment_Student FOREIGN KEY (student) REFERENCES Student (studentID)
        ON UPDATE CASCADE
        ON DELETE CASCADE,
    CONSTRAINT FK_Enrolment_Course FOREIGN KEY (course) REFERENCES Course (courseID)
        ON UPDATE CASCADE
        ON DELETE CASCADE
);
```
