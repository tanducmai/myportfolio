+++
date = 2022-02-26T01:05:26+10:30
title = "Normalisation"
slug = "database-normalisation"
aliases = "/database-normalisation"
description = "Database - Normalisation"
thumbnail = "images/database/blog/normalisation.png"
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
1. [Rules of the First Three Normal Forms](#rules-of-the-first-three-normal-forms)

![Normalisation Illustration](/images/database/blog/normalisation.png)
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

| student | course   | room  |
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

**I. Data Initialisation**:

- Identify the *Unnormalised form* (UNF).
  - The unstructured data / information received from the client.
- Find out the *repeating group* or *multi-value attributes*.
  - Refer to this *[section](#rules-of-the-first-three-normal-forms)*.

**II. First Normal Form (1NF)**:

- Identify the *Primary Key* (PK).
- Remove the *repeating group* which will become a new *child relation*.
- Bring the parent relation's PK to the *child relation*.
  - Next, identify the PK of the child relation.
    - The parent PK may or may not be the child's PK, or it can just be part of
      the child's PK.
  - We now have a *proper schema*.
- Identify the *partial dependency*.
  - Non-key attribute(s) partially depends on the PK.
  - Meaning that the PK should be a Composite Key, and the Non-key attribute(s)
    now can depend on part of it.
  - For example:
    - PK - Attribute1, Attribute2
    - Non-key attribute depends on {Attribute1} or {Attribute1} -> Non-key
      attribute.

**III. Second Normal Form (2NF)**:

- Remove the *partial dependency* which will become a new *child relation*.
  - The relation whose elements have just been removed now becomes another
    parent relation.
  - Next, identify the PK of the new child relation.
    - If the partial dependency or part of it is part of the new parent PK, it
      (or part of it) needs to stay in the parent relation and references itself
      in the new child relation.
    - Leave the child PK to the parent relation (resulting in a FK in the parent
      relation).
- Identify the *transitive dependency*.
  - A non-key attribute(s) depends on another non-key attribute(s).
  - Meaning that the relation should have at least two non-key attributes in
    order to check for the transitive dependency.
  - For example:
    - Book(bookName, authorName, authorAge)
    - {bookName} -> {authorName}
    - {authorName} -> {authorAge}
    - Thus, {bookName} -> {authorAge}
  - For this reason, a transitive dependency can only occur in a relation of
    three of more attributes.

**IV. Third Normal Form (3NF)**:

- Remove the *transitive dependency* which will become a new *child relation*.
  - The relation whose elements have just been removed now becomes another
    parent relation.
  - Next, identify the PK of the new child relation.
    - This is as clear as day: just look back at the previously identified
      transitive dependency.
    - Leave the child PK to the parent relation (resulting in a FK in the parent
      relation).
- Identify the *full dependency*.
  - Ensure that there is no partial and transitive dependency.
  - The PK now determines the rest of the attributes.
  - For example:
    - Having removed the partial and transitive dependency, our schema is now:
    - Course(courseNumber, courseName, courseDescription, courseValue)
    - PK - courseNumber
    - courseNumber -> courseName, courseDescription, courseValue

**V. Consolidation**:

- In the case that we have several reports, we then need to collect all their
  3NFs and join them together into one, hence
  *[consolidation](https://www.oxfordlearnersdictionaries.com/definition/english/consolidation)*.
- Rules: `Join all the relations (and their attributes) that have the same
  PK(s).`
- For example, up to this stage, we have eight relations whose PKs are
  italicised:

  1. Unit(*unitNo*, unitName, unitDescrip, unitValue)
  2. Lecturer(*lecturerNo*, lecturerName. lecturerOfficeNo, lecturerPhoneNo)
  3. UnitAdvisor(*lecturerNo, unitNo*)
  4. Unit(*unitNo*, unitName)
  5. Student(*stuNo*, stuName, stuAddr, modeOfStudy, mentorNo)
  6. Mentor(*mentorNo*, mentorName)
  7. AcademicRecord(*stuNo, unitNo, yearSemester*, grade)
  8. Unit(*unitNo*, unitName)

  - The combination should be:
    - 1 & 4 & 8
      - Unit(*unitNo*, unitName, unitDescrip, unitValue)
    - 2 & 6
      - Lecturer(*lecturerNo*, lecturerName. lecturerOfficeNo, lecturerPhoneNo)
    - 3
      - UnitAdvisor(*lecturerNo, unitNo*)
    - 5
      - Student(*stuNo*, stuName, stuAddr, modeOfStudy, mentorNo)
    - 7
      - AcademicRecord(*stuNo, unitNo, yearSemester*, grade)

### Rules Of The First Three Normal Forms

1. **No repeating groups or multi-value attributes.**

- Repeating group: Once a student enrols a course, their name is repeated
  everytime that it comes up.

| student | age   | course |
| :---:   | :---: | :---:  |
| Henry   | 20    | OOP    |
| Henry   | 20    | SRUX   |
| Mai     | 18    | OOP    |
| ...     | ...   | ...    |

- Multi-value attributes: Multiple values presented in a single attribute.

| courses         |
| :---:           |
| DDWT, SRUX, OOP |

- The correct way:

| courses |
| :---:    |
| DDWT     |
| SRUX     |
| OOP      |

2. **Data must be atomic (single values with meaning).**

  - **Atomic data** means there is only one piece of data per column
  - Taking a COURSES relation as an example.
  - Not atomic:

| courseCodeAndCourseName |
| :---:                   |
| INFS 1025 DDWT          |
| INFS1025 SRUX           |
| COMP1046 OOP            |

  - Atomic:

| courseCode | courseName |
| :---:      | :---:      |
| INFS 1025  | DDWT       |
| INFS1025   | SRUX       |
| COMP1046   | OOP        |

3. **Candidate Keys must be found.**

A Candidate Key is the minimum number of attributes in a table required to
uniquely identify each tuple. A given table may have more than one CK, but only
one can be selected as the Primary Key. All other CKs can be
implemented as Unique Keys.

4. **Each table contains relevant data to the candidate keys.**

All data in a table should relate back to the
candidate keys (e.g. a table should contain data about only one type of object).

For example:

| title           | format | author   | genreID | genre | price | publisher |
| :---:           | :---:  | :---:    | :---:   | :---: | :---: | :---:     |
| SQL for Dummies | E-book | Taylor A | 1       | SQL   | 49.99 | Wiley     |

So, in the given example, we can identify many different objects. Thus, we can
separate them into their own relations, and where necessary, create new CKs
(such as a Surrogate Key) to help uniquely identify the records in each new
relation:

*Book*

| title           | authorID | genreID | publisherID |
| :---:           | :---:    | :---:   | :---:       |
| SQL for Dummies | 1        | 1       | 1           |

*Publisher*

| publisherID | publisher |
| :---:       | :---:     |
| 1           | Wiley     |

*Author*

| authorID | author   |
| :---:    | :---:    |
| 1        | Taylor A |

*Format*

| formatID | format    |
| :---:    | :---:     |
| 1        | E-book    |
| 2        | Paperback |

*BookFormat*

| title           | formatID | price |
| :---:           | :---:    | :---: |
| SQL for Dummies | 1        | 32.99 |
| SQL for Dummies | 2        | 49.95 |
