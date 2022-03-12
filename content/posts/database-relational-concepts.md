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
1. [Types of Attributes](#types-of-attributes)
1. [Domains](#domains)
1. [Table Schemas](#table-schemas)
1. [Tuples](#tuples)
1. [Put It All Together](#put-it-all-together)

### General Terminology

| Relational Name | Common Name | Alternative |
| :---:           | :---:       | :---:       |
| relation        | table       | -           |
| attribute       | column      | field       |
| tuple           | row         | record      |

Within a table, every **column name** must be UNIQUE.

Within a Table every **row** must be UNIQUE (no duplicate data!).

Every Row must have a **unique Primary Key** that can identify that data row
only!

### Relations

A **RELATION** defines a *real world* or *conceptual object* we collect
information about.

When a relation is implemented in a Database Management System (DBMS), it is
often called a *table*.

A relational database (model) consists of a series of relations with distinct
names.

- It is a convention to name relations using the *PascalCase*.

For example, a School relation stores lecturerInfo, studentID, courses.

### Attributes

An **ATTRIBUTE** is a property that describes a relation.

Each attribute must have a unique name in a given relational table.

- It is a convention to name attributes using the *camelCase*.

For example, the School table (relation) has columns (attributes) for collecting
the Lecturer’s information, Student ID, and Courses.

Every attribute has a domain.

### Types of Attributes

There are five types of attribute:

1. **Simple** attributes are atomic values which cannot be divided further.

- They provide a single piece of useful information and not consist of subparts
  or multiple values or repeating information.
- E.g. A person's phone number is an atomic value of 10 digits.

2. **Composite** attributes are made of more than one simple attribute.

- E.g. A person's complete name may have firstName and lastName attributes.

3. **Derived** attributes are those whose values are calculated from the values
   of other attributes.

| PurchaseOrder |
| :---:         |
| quantity      |
| price         |
| /total        |

- total = quantity * price
- Thus, total is a Derived Attribute.

4. **Structured** attributes are those composed of more than one attribute.

| Employee     |
| :---:        |
| name         |
| salutation   |
| firstName    |
| lastName     |
| address:     |
| addressLine1 |
| addressLine2 |

- The name attribute consists of salutation + firstName + lastName.
- Thus name is a Structured Attribute.

5. **Single-valued** attributes are those which simply contain a single value.

- E.g. taxFileNumber, socialSecurityNumber, etc.

6. **Multivalued** attributes are those which contain more than one values.

- E.g. A person can have more than one phoneNumber, emailAddress, etc.
- It violates basic relational theory (single-valued attributes).
- To resolve a multivalued attribute, place it in a separate table and associate
  it with the original table.

For example:

![Multivalued attribute](/images/database-relational-concepts/multivalued.png)

### Domains

A **Domain** dictates (determines) the data type and the range of acceptable
values of an attribute.
- A domain of possible values must be associated with every attribute (e.g.,
  integer types, character types, date/time types).

Declaring an attribute to be of a particular domain acts as a constraint on the
values that it can take. Domain constraints are the most elementary form of
integrity constraint. They are tested easily by the system whenever a new data
item is entered into the database.

For a list of common Database data type, please read:
*[W3Schools](https://www.w3schools.com/sql/sql_datatypes.asp)* or *[Teach
Computer Science](https://teachcomputerscience.com/database-data-types/)*

For example:

| Attribute Name | Domain                         |
| ---            | ---                            |
| studentName    | varchar(100)                   |
| favColour      | varchar(10) {red, green, blue} |

### Table Schemas

A **TABLE SCHEMA** is the overall design of a relational table in a relational
database.

Programming analogy: a database schema corresponds to the variable declarations
(along with associated type definitions) in a program.

Format: **RelationName(attributeNames)**

Example: Customer(customerID, firstName, familyName, address, age)

### Tuples

A **TUPLE** is an instance of a relation or entity and contains the actual raw
data.

To simplify, a Tuple is a row of data.

A relation consists of one or more unordered tuples.

Within a relation, every tuple has a fixed number of values, hence the name
'tuple'.

### Put It All Together

![Terms and 
Notations](/images/database-relational-concepts/terms-and-notations.png)
