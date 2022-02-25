+++
date = 2022-02-21T05:11:42+10:30
title = "Database - Fundamentals"
slug = "database-fundamentals"
aliases = "/database-fundamentals/"
description = "Database Fundamentals"
thumbnail = "images/database-fundamentals/database.png"
tags = [
    "database",
    "fundamentals",
]
categories = [
    "database",
]
draft = false
+++

### Table of Contents

1. [What is a Database?](#what-is-a-database)
1. [Database Management System (DBMS)](#database-management-system)
1. [Example of a Database](#example-of-a-database)
1. [Why Bother Storing Data?](#why-bother-storing-data)
1. [Examples of Facts Analysed from Stored Data](#examples-of-facts-analysed-from-stored-data)
1. [How to Query the Database?](#how-to-query-the-database)
1. [More about the Role of a DBMS](#more-about-the-role-of-a-dbms)
1. [Structure of a DBMS](#structure-of-a-dbms)

![Database Illustration](/images/database-fundamentals/database.png)
Image Source:
*[Toptal](https://www.toptal.com/database/database-design-bad-practices)*

### What Is A Database

A collection of tables containing data that are used to retrieve information.

A collection of potentially useful data that models **real-world** or
**conceptual objects** and their **relationships**.

- Objects/Entities like People, Items, Students, etc.
- Relationships like Henry purchased an apple.
- Conceptual like films and songs (*intangible*).

### Database Management System

A DBMS is software designed to store and manage collections of data across one
or more databases.

- It can handle large amounts of data (more than RAM can hold)
- It can share the data between various applications and users (web interfaces,
  desktop/console applications incl. command line via the DBMS!)

A DBMS ensures:
- Data is persistent (can be retrieved once it is created).
- Data is reliable (can be retrieved after hardware/software failures).
- Data meets specific requirements ("constraints": e.g. the student mark is
  between 0 and 100).
- Privacy is maintained (it controls access and manipulation).

Popular free DBMS include:
- SQLite
- MySQL
- MS-SQL Express
- PostgreSQL
- Commercial: MS-SQL and Oracle, DB2 + the rest

### Example Of A Database

A typical example of a database is a library.

In the case of a library:

- Books = objects containing data
- Catalogue system = DBMS

### Why Bother Storing Data

In fact, 90% of business data is rarely accessed again. So why bother?

There are primarily two reasons for it:

1. Compliance with laws and company regulations
1. Data Mining – maybe the data holds some hidden detail?

When having data stored, we can extract information and use it for decision
making.

1. Analyse the history.
1. Predict the future.

### Examples Of Facts Analysed From Stored Data

- Car airbags kill 1 person for every 22 lives that they save.
- A new baby usually deprives each of it’s parents around 350-400 hours of sleep
  in the first year.
- On average, 100 people choke to death on ballpoint pens every year.

### How To Query The Database

A **Structured Query Language** (SQL) is needed to ask questions (query) the
structured data (database).

A structured language uses keywords in a logical pattern to perform tasks.

- It is a very high-level programming languages - Fourth Generation Languages
  (4GL), along with Focus, Metafont, etc.
- Programming in a 4GL, programmers only define the logic, not the control flow.


### More About The Role Of A DBMS

A DBMS interprets SQL and actions it, which means it determines what needs to be
done, how, and then returns the result.

A DBMS performs all the maintenance and management functions for the data model:

1. Exchanging data from the computer to human users (and vice versa)
1. Managing disk space (shrink/expansion)
1. Managing the creation of tables (and various indexes)
1. Managing the insertion, updating and deletion of data records – including
   performing any necessary checks

A DBMS performs complex query answering (searching and matching) of records.

The DBMS and its users communicate using a mutually understandable language:
**SQL** (Structured Query Language!)

### Structure Of A DBMS

![Structure of a DBMS](/images/database-fundamentals/dbms-structure.png)
Adapted from *[Database Management
Systems](https://www.google.com.au/books/edition/Database_Management_Systems/74JykQEACAAJ?hl=en)*
(2000) by Ramakrishnan and Gehrke.

In the diagram:

The **Transaction Manager** ensures that queries (or actions involving data) are
carried out in the correct order.

- It ensures that if a specific query fails (eg and update or insert) that the
  database will not have data left in an inconsistent state

The **Lock Manager** is provided to control access to records when there are
multiple users involved.

- If both users are updating a record, or one is trying to retrieve a record
  that is being modified the Lock Manager may restrict or reject access to the
  record

The **Recovery Manager** uses system logs created by the transaction manager to
retain data integrity in the event of a system failure

The **System Catalogue** is a data dictionary (metadata) that holds information
about schemas, users, applications etc.

- It stores:
1. Names, types, sizes of data items
1. Names of relationships
1. Names of authorised users
1. Usage statistics etc
