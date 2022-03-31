+++
date = 2022-03-28T17:37:46+10:30
title = "Database Sql Common Functions"
slug = ""
aliases = ""
description = ""
thumbnail = "images/tn.png"
tags = []
categories = []
draft = true
+++

### Table of Contents

1. [What is a Function?](#what-is-a-function)
1. [Common Functions](#common-functions)

1. [Date-related Functions](#common-functions)


### What is a Function

Functions are calculations performed by the Database Management System
(DBMS).

### Common functions

Common functions include:

| Function                   | Example                           | Output    |
| ---                        | ---                               | ---       |
| LEFT(string, length)       | LEFT('Sam', 2)                    | Sam -> Sa |
| RIGHT(string, length)      | RIGHT('Sam', 2)                   | Sam -> am |
| CHARINDEX(str1, str2)      | CHARINDEX('Fun', DBFundamentals') | 3         |
| SUBSTRING(col, start, len) | SUBSTRING(Name, 1, 1) |Returns char(s) at start position|

CHARINDEX starts from 0 and counts to the length.

### Date

Below is a list of common functions related to dates:

| Function                        | Example                  | Output     |
| GETDATE()                       |                          | 28/03/2022 |
| DATEPART(datepart, date)        | DATEPART(d, GetDate())   | 28         |
| DATENAME(datepart, date)        | DATENAME(dw, GetDate())  | Monday     |
|                                 | DATENAME(m, GetDate())   | March      |
| DATEADD(datepart, number, date) | DATEADD(d, 7, GetDate()) | 04/04/2022 |

Datepart can be:

- d | m | yy/yyyy => day | month | year number of the calander date
- y |dy => day of year (note the difference from yy/yyyy!!!)
- dw returns the day of the week number except when used with DATENAME where it returns the name of the day!
- m will return the name of the month when used with DATENAME


