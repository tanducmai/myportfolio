+++
date = 2022-02-24T21:29:52+10:30
title = "Database - Key Concepts"
slug = "database-key-concepts"
aliases = "/database-key-concepts/"
description = "Database - Key Concepts"
thumbnail = "images/database-key-concepts/thumbnail.png"
tags = [
    "database",
    "relational model",
    "key concepts",
    "fundamentals",
]
categories = [
    "database",
]
draft = false
+++

### Table Of Contents

1. [What is a Key?](#what-is-a-key)
1. [Super Key](#super-key)
1. [Candidate Key](#candidate-key)
1. [Primary Key](#primary-key)
1. [Unique Key](#unique-key)
1. [Surrogate Key](#surrogate-key)
1. [Natural Key](#natural-key)
1. [Foreign Key](#foreign-key)
1. [Non-key Attributes](#non-key-attributes)

![Keys in DBMS](/images/database-key-concepts/thumbnail.png)
Image Source:
*[Arvindzeclass](https://www.arvindzeclass.in/2021/06/What-is-primary-key.html)*

### What Is A Key

A **KEY** in the DBMS is a set of one or more attributes whose values can
*uniquely identify* a given tuple within a relation.

There are generally eight types of keys:

1. Super Key
1. Candidate Key (CK) (name given to all keys)
1. Primary Key (PK) is a value that identifies a particular tuple.
1. Unique Key
1. Composite Key
1. Surrogate Key
1. Natural Key
1. Foreign Key

### Super Key

The **SUPER KEY** is the set of *all* the keys that, taken collectively, help to
*uniquely identify* a tuple within a relation.

- Due to this feature, even a key that contains every attribute in a tuple is
still considered a Super Key.

From this huge collection of keys, extract those containing the minimum number of
attributes to be used as Candidate Keys.

### Candidate Key

The **CANDIDATE KEY(S)** is a minimum combination of attributes, extracted from
the Super Key, that could become the Primary Key of a relation.

- If there is only one Candidate Key (CK), it is generally selected as the
  Primary Key.
- Otherwise, the developer must choose which CK will be used as the Primary Key.

### Primary Key

The **PRIMARY KEY** is a set of one or more attributes chosen to *uniquely
identify* each tuple within a relation.

It serves to distinguish one tuple from every other.

The value(s) must be unique for each tuple.

All relations require one and only one Primary Key (PK).

Given a PK, we can locate the specific data within any tuple.

Sometimes, it is an automatically generated number (e.g. the current row number
in Excel).

### Unique Key

A **UNIQUE KEY** is, obviously, a set of attribute(s) whose values are always
*unique*.

Taking the below relation as an example:

- Student(firstName, lastName, email, username, contactNo, address)
- email & username are two Unique Keys.

Further, any CK that is not selected as the PK can be implemented as a Unique
Key constraint in the DBMS.

- The data is checked to ensure that each entry is a unique value and does not
  exists in other tuples within a relation.

### Composite Key

The **COMPOSITE KEY(S)** is a set of *two or more* attributes whose values can
*uniquely identify* a given tuple within a relation.

### Surrogate Key

A **SURROGATE KEY** is an ultimate lazy approach to implementing a PK.

It is simply an incremental number stored as an ID column in a table.

- E.g. row numbers (1, 2, 3) that is automatically assigned to each row in an
  Excel spread sheet.

It is a randomly generated alpha-numeric value and has nothing to do with the
table data.

### Natural Key

A **NATURAL KEY** is a minimum set of one or more attributes that can be used or
combined with others to *uniquely identify* each tuple within a relation.

- E.g., bankAccount + telephoneNo, name + dateOfBirth.

A Natural Key exists if and only if a Surrogate Key does.

- Why is it called 'natural'? Given that a Surrogate Key is one that is made up
  (not related to the relation); thus, the name 'Natural Key' could be natural
  to the relation and to differentiate itself from the Surrogate Key.

### Foreign Key

A **FOREIGN KEY** is a set of one or more attributes whose values are the PK of
another relation (Primary or Unique!)

To be more specific, the PK values are copied and stored in another relation as
a Foreign Key (FK) value.

The main purpose of Foreign Keys is to establish a relationship between two
relations, hence the term "Relational Database"

The relation containing the FK is called the *child* table, and the relation
containing the PK is called the *referenced* or *parent* table.

To modify (insert or delete) a FK value, the process must take place in the
parent table, not the child one.

Example: A course mark is of no use if it does not relate back to a student and
a course:

- Enrolment(studentID) is a FK referencing Student(studentID)
- Enrolment(courseID) is a FK referencing Course(courseID)

![Foreign Keys Example](/images/database-key-concepts/foreign-keys.png)

### Non-key Attributes

The **NON-KEY ATTRIBUTE(S)** does not have any relationship with any other keys
(PK, CK, FK).

It is simply not categorised as any key listed above.

A non-key attribute is also referred to as a **NON-PRIME ATTRIBUTE**.
