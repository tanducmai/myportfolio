+++
date = 2022-03-28T17:37:46+10:30
title = "Database - SQL - Common Functions"
slug = "database-sql-common-functions"
aliases = "/database-sql-common-functions"
description = "Database - SQL - Common Functions"
thumbnail = "/images/database/posts/sql/query-complete-syntax.png"
tags = [
    "database",
    "intermediate",
    "SQL",
]
categories = [
    "database",
]
draft = false
+++

### Table of Contents

1. [What is a Function?](#what-is-a-function)
1. [Working with String](#working-with-string)
1. [SUBSTRING Function](#substring-function)
1. [CHARINDEX Function](#charindex-function)
1. [Example of Working with String](#example-of-working-with-string)
1. [Working with Date](#working-with-date)
1. [CAST Function](#cast-function)
1. [ISNULL Function](#isnull-function)

![SQL Query Syntax](/images/database/posts/sql/query-complete-syntax.png)

### What is a Function

Functions are calculations performed by the Database Management System
(DBMS).

### Working with String

Common functions include:

| Function                   | Example                           | Output                            |
| ---                        | ---                               | ---                               |
| UPPER(col)                 | UPPER('Sam')                      | Sam -> SAM                        |
| LOWER(col)                 | LOWER('Sam')                      | Sam -> sam                        |
| RTRIM(col)                 | RTRIM('Sam   ')                   | [  Sam M  ] -> [  Sam M]          |
| LTRIM(col)                 | LTRIM('   Sam')                   | [  M Sam  ] -> [M Sam  ]          |
| LEN(col)                   | LEN('Sam')                        | 3                                 |
| REVERSE(col)               | REVERSE('Sam')                    | Sam -> maS                        |
| LEFT(string, length)       | LEFT('Sam', 2)                    | Sam -> Sa                         |
| RIGHT(string, length)      | RIGHT('Sam', 2)                   | Sam -> am                         |

##### Example:

```sql
SELECT UPPER ('Eynesbury') AS [School Name]
```

Result:

| School Name |
| :---:       |
| EYNESBURY   |

### `SUBSTRING` function

##### Syntax

```sql
SUBSTRING ( expression, start, length )
```

- Returns part of a character or text in SQL server.

##### Arguments

1. **expression**

- A character or text.

2. **start**

- An integer that specifies where the returned characters start.
- If start is less than 1, the returned expression will begin at the
  first character specified in expression.
- If start is greater than the number of characters in the value
  expression, a zero-length expression is returned.

3. **length**

- A positive integer that specifies how many characters of the
  expression will be returned.
- If the sum of start and length is greater than the number of
  characters in expression, the whole value expression beginning at
  start is returned.
- If length is negative, an error is raised and the statement is
  terminated.

##### Example:

```sql
SELECT SUBSTRING ('Eynesbury', 1, 2) AS [School Name];
```

Result:

| School Name |
| :---:       |
| Ey          |

### `CHARINDEX` function

##### Syntax

```sql
CHARINDEX ( expressionToFind, expressionToSearch [ , start_location ] )
```

- Searches an expression for another expression and returns its starting
  position if found.

##### Arguments

1. **expressionToFind**

- A character expression that contains the sequence to be found.
- expressionToFind is limited to 8000 characters.

2. **expressionToSearch**

- A character expression to be searched.

3. **start_location**

- An integer at which the search starts.
- If start_location is not specified, is a negative number, or is 0, the
  search starts at the beginning of expressionToSearch.

##### Example

```sql
SELECT CHARINDEX ('Fun', 'DatabaseFundamentals') AS counting;
```

Result:

| counting |
| :---:    |
| 9        |

### Example of working with string

```sql
DECLARE @address varchar(100) = '13 Wayville road, Woodville, SA 5000'

SELECT
    LEFT(@address, CHARINDEX(',', @address) - 1) AS streetAddress,
    LEFT(secondPart, LEN(secondPart) - CHARINDEX(' ', REVERSE(secondPart)) -1) AS suburb,
    RIGHT(secondPart, CHARINDEX(' ', REVERSE(secondPart))) AS state,
    REVERSE(SUBSTRING(REVERSE(@address), 1, 4)) AS postcode
    FROM (
    SELECT
        RTRIM(
    REVERSE(
        SUBSTRING(
            REVERSE(@address), 6, LEN(@address) - CHARINDEX(',', @address) – 5
                  )
        )
    ) AS secondPart
) AS t1;
```

Result:

| streetAddress    | suburb    | state | postcode |
| ---              | ---       | ---   | ---      |
| 13 Wayville road | Woodville | SA    | 5000     |

### Working with date

Below is a list of common functions related to dates:

Today is Monday, 28 March, 2022.

| Function                        | Example                  | Output     |
| ---                             | ---                      | ---        |
| GETDATE()                       |                          | 2022-03-28 |
| DATEPART(datePart,inputDate)    | DATEPART(d, GETDATE())   | 28         |
| DATENAME(datePart,inputDate)    | DATENAME(dw, GETDATE())  | Monday     |
|                                 | DATENAME(m, GETDATE())   | March      |
| DATEADD(datePart, number, date) | DATEADD(d, 6, GETDATE()) | 2022-04-03 |

##### Arguments

1. **inputDate**

- A literal date or an expression that can resolve to a TIME, DATE,
  SMALLDATETIME, DATETIME, DATETIME2, or DATETIMEOFFSET value.

2. **datePart**

- A part of the date that you want to return.
- The table below lists all valid date part values.
- Note: either upper-case or lower-case letters are acceptable.

| datePart    | abbreviation |
| :---:       | :---:        |
| year        | yy, yyyy     |
| quarter     | qq, q        |
| month       | mm, m        |
| dayofyear   | dy, y        |
| day         | dd, d        |
| week        | wk, ww       |
| weekday     | dw           |
| hour        | hh           |
| minute      | mi, n        |
| second      | ss, s        |
| millisecond | ms           |
| microsecond | mcs          |
| nanosecond  | ns           |
| TZoffset    | tz           |
| ISO_WEEK    | isowk, isoww |

##### `DATEPART()` vs. `DATENAME()`

DATENAME() is similar to the DATEPART(), except for the return type.

1. DATENAME() returns the date part as a character string.
1. DATEPART() returns the date part as an integer.

##### Example

```sql
SELECT
    DATEPART(year, '2022-03-28') + '1' [datePart],
    DATENAME(year, '2022-03-28') + '1' [dateName] ;
```

Result:

| datePart | dateName |
| :---:    | :---:    |
| 2023     | 20221    |

:link: *[SQL Server
Tutorial](https://www.sqlservertutorial.net/sql-server-date-functions/sql-server-datename-function/)*

### `CAST` function

##### Syntax

```sql
CAST ( expression AS datatype [ ( length ) ] )
```

- Converts an expression (of any type) into a specified data type.

##### Arguments

1. **expression**

- Any valid expression.

2. **datatype**

- The target data type, such as int, varchar, bit, etc.

3. **length**

- An optional integer that specifies the length of the target data type.
- The default value is 30.

##### Examples

:memo: Change a value to text.

```sql
SELECT
  CAST (COUNT (A.actorID) AS varchar (50)) AS example1
FROM Actor as A;
```

:memo: Change a number to text.

```sql
SELECT CAST (5 AS varchar(50)) AS example2
```

:memo: Add dollar sign before money values.

```sql
SELECT
    '$' + CAST (MAX (E.salary) AS varchar(40)) AS example3
FROM Employee AS E;
```

### `ISNULL` function

##### Syntax

```sql
ISNULL (expression_or_attribute, replacement_value)
```

- Returns a specified value if the expression is NULL.
- If the expression is NOT NULL, then returns the expression.

##### Examples

```sql
SELECT ISNULL ('Hello', 'tanducmai.com') AS example1;
```

Result

| example1 |
| :---:    |
| Hello    |

```sql
SELECT ISNULL (NULL, 'tanducmai.com') AS example2;
```

Result

| example2      |
| :---:         |
| tanducmai.com |

:memo: Find ALL Simpsons characters and their first aired episode; otherwise,
display 'TBA'.

```sql
SELECT
    CharacterName,
    ISNULL (EpisodeName, 'TBA') AS FirstEpisode
FROM Character AS C LEFT OUTER JOIN Episode AS E
ON C.EpisodeID = E.EpisodeID
```

Sample result:

![ISNULL function
example](/images/database/posts/sql/control-statements/isnull-function-example.png)
