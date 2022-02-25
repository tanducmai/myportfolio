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
draft = true
+++

### Table of Contents

1. [Good and Bad Database Designs](#good-and-bad-database-designs)
1. [Rule of Thumb](#rule-of-thumb)
1. [Normalisation](#normalisation)
1. [How to Normalise?](#how-to-normalise)

![Normalisation Illustration](/images/database-normalisation.png)

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
