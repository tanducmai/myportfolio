+++
date = 2022-02-23T07:58:02+10:30
title = "Database - Relational Concepts"
slug = "database-relational-concepts"
aliases = "/database-relational-concepts/"
description = "Database - Relational Concepts"
thumbnail = "images/database-relational-concepts/terms-and-notations.png"
tags = [
    "database",
    "relational model",
    "relational concepts",
    "fundamentals",
]
categories = [
    "database",
]
draft = false
+++

### Table of Contents

1. [General Terminology](#terminology)
1. [Relations](#relations)
1. [Attributes](#attributes)
1. [Domains](#domains)
1. [Table Schemas](#table-schemas)
1. [Tuples](#tuples)
1. [Put It All Together](#put-it-all-together)

### General Terminology

| Relational Name | Common Name | Alternative |
| :---:           | :---:       | :---:       |
| relation        | table       | -           |
| attribute       | colum       | field       |
| tuple           | row         | record      |

Within a table, every **column name** must be UNIQUE.

Within a Table every **row** must be UNIQUE (no duplicate data!).

Every Row must have a **unique Primary Key** that can identify that data row
only!

### Relations

A **RELATION** defines a *real world* or *conceptual* object we collect
information about.

When a relation is implemented in a Database Management System (DBMS), it is
often called a Table.

A relational database (model) consists of a serries of relations with distinct
names.

For example, the SCHOOL table stores LecturerInfo, StudentID, Courses.

### Attributes

An **ATTRIBUTE** is a name assigned to column in a relational table.

Each Attribute must have a unique name in a given relational table.

For example, the SCHOOL table has columns (attributes) for collecting the
Lecturer’s information, Student ID, and Courses.

Every attribute has a **domain**.

### Domains

A **Domain** dictates - determines the acceptable values of an attribute.

To simplify, a domain is often referred to as a data type - as in Programming.

For a list of common Database data type, please read:
*[W3Schools](https://www.w3schools.com/sql/sql_datatypes.asp)* or
*[Teach Computer Science](https://teachcomputerscience.com/database-data-types/)*

For example:

| Attribute Name | Domain (Data Type) |
| ---            | ---                |
| FirstName      | varchar            |
| LastName       | varchar            |
| Email          | varchar            |
| ContactNo      | char               |
| Username       | varchar            |
| AddressLine1   | varchar            |
| AddressLine2   | varchar            |

### Table Schemas

A **TABLE SCHEMA** defines the structure of a relational table in a relational
database.

Format: RELATION_NAME(attributeNames)

Example: CUSTOMER(CustomerID, FirstName, FamilyName, Address, Age)

### Tuples

A **TUPLE** is an instance of a relation or entity and contains the actual raw
data.

To simplify, a Tuple is a row of data.

A relation consists of one or more unordered tuples

Within a relation, every tuple has a fixed number of values, hence the name
'tuple'.

### Put It All Together

![Terms and 
Notations](/images/database-relational-concepts/terms-and-notations.png)
