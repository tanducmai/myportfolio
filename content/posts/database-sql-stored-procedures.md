+++
date = 2022-04-05T17:34:07+09:30
title = "Database - SQL - Stored Procedures"
slug = "database-sql-stored-procedures"
aliases = "/database-sql-stored-procedures"
description = "Database - SQL - Stored Procedures"
thumbnail = "images/tn.png"
tags = [
    "database",
    "intermediate",
    "SQL",
    "DBMS",
]
categories = [
    "database",
]
draft = true
+++

### Table of Contents

1. [Stored procedures](#stored-procedures)
1. [Syntax](#syntax)
1. [VIEWS](#views)
1. [@varName](#varname)

### Stored procedures

Stored Procedures (SPs) are pre-written SQL queries stored by the DBMS They are
similar to Views in that they are called when required

Unlike views they may contain INSERT, UPDATE, DELETE, SELECT queries or any
combination of these! Often SPs are used to perform basic CRUD tasks (create,
read, update, delete) Other SPs are used to perform complex calculations needed
for generating reports or transforming data

### Syntax

##### Create
```sql
CREATE PROCEDURE GetSimpsons
AS

SELECT * FROM Characters
WHERE characterName LIKE '%Simpson'
```

##### Execute

```sql
EXECUTE GetSimpsons

-- OR

EXEC GetSimpsons
```

##### Modify

```sql
ALTER PROCEDURE GetSimpsons
AS

SELECT characterID, characterName FROM Characters
WHERE characterName LIKE '%Simpson'
```

### VIEWS

##### Similarity
Stored Procedures can be used like VIEWs

```sql
CREATE PROCEDURE GetStaff
AS

SELECT personID, personName, position
FROM Person AS P JOIN Staff AS S
ON P.personID = S.personID
```

Is akin to

```sql
CREATE VIEW StaffView
AS
SELECT personID, personName, position
FROM Person AS P JOIN Staff AS S
ON P.personID = S.personID
```

```sql
EXECUTE GetStaff

-- VS

SELECT * FROM StaffView
```

##### Difference

A View can readily be used in other queries
A Stored Procedure cannot – it requires more work

JOIN Query using SP

```sql
DECLARE @tablevar TABLE (
charID int,
charName varchar(100)
);

INSERT INTO @tablevar(charID, charName) EXEC GetSimpsons

SELECT * FROM @tablevar AS t1 JOIN @tablevar AS t2
ON t1.charName = t2.charName
```

Same JOIN Query using View

```sql
SELECT V1.charID, V1.charName
FROM SimpsonsView AS V1
JOIN SimpsonsView AS V2
ON V1.charName = V2.charName
```

Stored Procedures are more powerful than Views
They are not the same thing…

Unlike a View, a stored procedure can
Contain flow control statements (IF, ELSE, IF ELSE)
Contain many separate statements that work collectively or separately on data
Make use of variables
@someVariableName

Views cannot!

### @varName

Variables (@someName) are placeholders for unknown values
The value of a variable is provided by the user when it is needed
It must be declared
Like any other attribute it must have a known data type
It can have a default value

1. Single declaration

```sql
DECLARE @someInt INT
```

2. Multiple declaration

```sql
DECLARE 	@someString VARCHAR(50),
				@someDate DATETIME
```

3. Multiple Declaration with Default values

```sql
DECLARE	@someString VARCHAR(50) = 'DefaultValue',
			 	@someDate DATETIME = GetDate()
```

Variables (@someName) can be used to return values

```sql
DECLARE
	@someString VARCHAR(50) = 'DefaultValue',
 	@someDate DATETIME = GetDate()


SELECT 	@someString AS someText,
			@someDate AS currentDate
```
