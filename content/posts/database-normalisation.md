+++
date = 2022-02-25T01:05:26+10:30
title = "Database - Normalisation"
slug = "database-normalisation"
aliases = "/database-normalisation"
description = "Database - Normalisation"
thumbnail = "images/database-normalisation.png"
tags = [
    "database",
    "relational model",
    "normalisation",
    "fundamentals",
]
categories = [
    "database",
]
draft = false
+++

### Table of Contents

1. [Good and Bad Database Designs](#good-and-bad-database-designs)
1. [Rule of Thumb](#rule-of-thumb)
1. [Normalisation](#normalisation)
1. [How to Normalise?](#how-to-normalise)

![Normalisation Illustration](/images/database-normalisation.png)
Image Source: *[Evil
Martians](https://evilmartians.com/chronicles/normalization-consistency-and-clowne)*

### Good and Bad Database Designs

When designing a database, people tend to do one that captures all or
too much of the required information.

It should be noted that more than one design are plausible.

- One design may be better than another.
- A good design in one situation may perform poorly in another.

A good design should take into account how the data will be used:

- Frequent user searches
- Auditing purposes
- Predictions or data mining

In contrast, a bad design can create data quality issues (anomalies):

1. **Redundancy**
- Information is recorded unnecessarily in multiple tuples.
2. **Update Anomaly**
- Information can be changed in one tuple leaving old information in another.
3. **Insertion Anomaly**
- A bad design that forces unrelated information to be recorded as well and this
  information may be wrong.
4. **Deletion Anomaly**
- Deletion of a record results in complete loss of other information.

Taking a poorly designed database as an example:

| Student | Course   | Room  |
| ---     | ---      | ---   |
| Henry   | INFS1025 | C2-04 |
| Mai     | INFS1025 | C2-04 |
| Duc     | INFS1025 | C2-04 |
| ...     | ...      | ...   |

1. If every course is in only one room, contains **redundant** information!
1. If we update the room number for just one tuple (Update anomaly).
1. Suppose everyone drops the course suddenly, we lose information about where
   the course is (Delete Anomaly).
1. We may not be able to create a room reservation without students. We need to
   know every detail (Insert anomaly).

### Rule Of Thumb

Ensure a relation only captures **one type** of information about an **entity**
or **object**.

In order to design a database where each relation only captures one type of
information, we need normalisation.

### Normalisation

**Normalisation** is the process of *decomposing* large relational schemas into
smaller, more efficient ones.

- Smaller schemas that contain only one copy of any given record.
  - Avoids issues that result from having multiple copies of the same record
    (typo erros, etc.)
- Smaller schemas contain only relevant data.
- Smaller schemas are more easily searched.

Normalisation prevents update anomalies and data inconsistencies.

It works well where data is updated frequently, but at the expense of
information retrieval

### How To Normalise

1. **Data Initialisation**:

- Identify the *Unnormalised form* (UNF).
  - The unstructured data / information received from the client.
- Find out the *repeating group*.
  - Any value that has multiple entries.
  - E.g. I take four courses this semester, hence four entries listed under my
    name.

2. **First Normal Form (1NF)**:

- Identify the *Primary Key* (PK).
- Remove the *repeating group*.
- Bring the PK to the *child relation*.
  - We now have a *proper schema*.
- Identify the *partial dependency*
  - Non-key attribute(s) partially depend on the PK.
  - Meaning that the PK should be a Composite Key, and the Non-key attribute(s)
    now depend on part of the PK (not the whole PK).
  - For example:
    - PK - Attribute1, Attribute2
    - Non-key attribute depends on {Attribute1} or {Attribute1} -> Non-key
      attribute.

3. **Second Normal Form (2NF)**:

- Remove the *partial dependency* which will become a new *child relation*.
- Leave the child PK to the parent relation.
- Identify the *transitive dependency*.
  - A non-key attribute depend on another non-key attribute.
  - For example:
    - BOOK(BookName, AuthorName, AuthorAge)
    - {BookName} -> {AuthorName}
    - {AuthorName} -> {AuthorAge}
    - Thus, {BookName} -> {AuthorAge}
  - For this reason, a transitive dependency can only occur in a relation of
    three of more attributes.

4. **Third Normal Form (3NF)**:

- Remove the *transitive dependency*.
- Result in the *full dependency*.
  - We are now left with no partial / transitive dependency.
  - PK now determines the rest of the attributes.
  - For example:
    - Having removed the transitive dependency, we now have our schema:
    - COURSE(CourseNumber, CourseName, CourseDescription, CourseValue)
    - PK - CourseNumber
    - CourseNumber -> CourseName, CourseDescription, CourseValue

5. In the case that we have several reports, we then need to:

- Collect all the 3NF.
- Combine the relations.
