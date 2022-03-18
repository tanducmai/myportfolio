+++
date = 2022-03-11T11:53:55+10:30
title = "Database - SQL Data Manipulation"
slug = "database-sql-data-manipulation"
aliases = "/database-sql-data-manipulation"
description = "Database - SQL Data Manipulation"
thumbnail = "images/sql-meme.png"
tags = [
    "database",
    "fundamentals",
    "SQL",
    "DBMS",
    "physical design",
    "data manipulation",
]
categories = [
    "database",
]
draft = false
+++

### Table of Contents

1. [Data Manipulation](#data-manipulation)
1. [INSERT INTO Statement](#insert-into-statement)
1. [DELETE FROM Statement](#delete-from-statement)
1. [DELETE FROM and DROP TABLE
Statements](#delete-from-and-drop-table-statements)
1. [UPDATE Statement](#update-statement)

![SQL Meme](/images/sql-meme.png)

### Data Manipulation

So we have created a set of tables. However:
- How do we actually put data in our database?
- How do we modify data that is already in our database?
- How do we answer questions (queries) using our database data?

Key Data Manipulation SQL commands:

1. **INSERT INTO** - Creates new tuple(s) in a table.
1. **DELETE FROM** - Permanently removes tuple(s) from a table.
1. **UPDATE** - Modifies existing tuple(s) in a table.
1. **SELECT** - Retrieves tuple(s) of data from table (a Query).

### `INSERT INTO` Statement

This statement is used to populate with data - your newly created database.
- String data (text) must be wrapped in single 'quotations'.
- Same applies to date strings: '01/03/2014'

##### Insert a single tuple

There are two ways of creating new tuple(s) in a table: default positions
and keywords.

For example: Student(studentName, studentID)

1. Insert new values in the default order of the attributes when the table was created.

```sql
INSERT INTO TableName VALUES (x, y, z);
INSERT INTO Student VALUES ('50011', 'Barry');
```

2. Insert the values in a different order to the default order of the attributes when the table was created.

```sql
INSERT INTO TableName (att3, att2, att1) VALUES (z, y, x);
INSERT INTO Student (studentName, studentID) VALUES ('Stacy', '50022');
```

Note the different order of studentName and studentID. If the order is
not specified, you must insert the values in the order of the table
attribute when they are defined (left -> right).

##### Use a sub-query (insert from another table)

Insert values from another table into the given table as a new tuple.

Syntax:

```sql
INSERT INTO GivenTable
    SELECT att1, att2, att3
    FROM AnotherTable
    WHERE <condition>;
```

Example:

```sql
INSERT INTO Student (StudentID, StudentName)
    SELECT id, name
    FROM AnotherTable
    WHERE name IS NOT NULL;
```

### `DELETE FROM` statement

This statement is used to remove ALL the tuple(s) that satisfy the condition from a
given table.
- The removal may result in deletions from other tables if a FK
  constraint with `CASCADE ON DELETE` has been used.

1. If the WHERE clause is omitted, DELETE FROM empties (removes all
tuples from) the table:

For example, remove all students from the table:

```sql
DELETE FROM TableName;
DELETE FROM Student;
```

2. If the WHERE clause presents, each tuple is compared to it and if
TRUE is returned, that tuple is deleted.

For example, remove all students from the table whose name is 'Henry':

```sql
DELETE FROM TableName WHERE <condition>;
DELETE FROM Student WHERE studentName = 'Henry';
```

### `DELETE FROM` and `DROP TABLE` statements

| DELETE FROM                      | DROP TABLE                             |
| ---                              | ---                                    |
| Delete all tuples from the table | Delete all tuples from the table       |
| Do NOT delete the table / schema | Delete the table / schema              |
| `DELETE FROM Employee`           | `DROP TABLE Employee`                  |
| The table is empty               | The table is removed from the database |

### `UPDATE` statement

This statement is used to modify the existing records in a table that
satisfy the condition from a given table.

Syntax:

```sql
UPDATE TableName
  SET attribute=<Expression|SelectSQL|NULL|DEFAULT>
  {, attribute=<Expression|SelectSQL|NULL|DEFAULT>}
  {, attribute=<Expression|SelectSQL|NULL|DEFAULT>}
  [WHERE <condition>]
```

Akin to the DELETE FROM statement, the presence of the WHERE clause is
vital.

1. If the WHERE clause is omitted, all records in the table will be
updated.

For example, all employees will get a double raise:

```sql
UPDATE Employee
SET Salary = Salary * 2;
```

2. If the WHERE clause presents, each tuple is compared to it and if TRUE
is returned, that tuple is updated.

For example, only *senior* employees will get a double raise:

```sql
UPDATE Employee
SET Salary = Salary * 2.0
WHERE rank = senior;
```
