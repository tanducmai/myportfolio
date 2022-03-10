+++
date = 2022-03-07T23:19:58+10:30
title = "Database - Logical Design"
slug = "database-logical-design"
aliases = "/database-logical-design/"
description = "Database - Logical Design"
thumbnail = "images/database-conceptual-design/uml-example.png"
tags = [
    "database",
    "fundamentals",
    "uml diagram",
    "relational schema",
    "logical design",
]
categories = [
    "database",
]
draft = true
+++

### Table Of Contents

1. [Logical Modelling?](#logical-modelling)
1. [Logical Design](#logical-design)
1. [Classes](#classes)
1. [Associations - Multiplicities](#associations---multiplicities)
1. [Recursive Relationships / Self
   Associations](#recursive-relationship-or-self-association)

### [Logical](https://www.oxfordlearnersdictionaries.com/definition/english/logical_1?q=logical) Modelling

After the [conceptual
design](https://tanducmai.com/posts/database-conceptual-design), the next phase
is to create functional relational schemas based on the conceptual design.
- A written description of how the relational database will be implemented.
- This includes deciding which CK(s) will become the
  [PK](https://tanducmai.com/posts/database-identify-the-primary-key).

### Logical Design

The logical design of the database is the UML translation process.

UML can often be translated automatically into relational schemas, using:
- MS-SQL Diagrams feature
- Lucid chart
- DBDesigner Fork
- ArgoUML

In this post, we will explore how to translate UML into relational schemas
manually following some basic rules.

### Classes

Every UML Class becomes its own relation of the same name.

The Primary Key (PK) becomes the relations PK.

For example:

![Example](/images/database-conceptual-design/association.png)

Relational Schema 1:

```text
Student(studentID, emailID, studentName)
PK(studentID)
CK(emailID)
```

Relational Schema 2:

```text
Course(courseID, courseName)
PK(courseID)
CK(courseName)
```

### Associations - Multiplicities

There are three different types of associations (One-to-One, One-to-Many,
Many-to-Many) which follow the rules as disscussed in
[here](https://tanducmai.com/posts/database-conceptual-design/#multiplicity).

1. **One-to-One** (`1:1`)

For example:

![One-to-One](/images/database-conceptual-design/one-to-one-2.png)

Relational Schema 1:

```text
Person(personID, personName, dateOfBirth)
PK(personID)
```

Relational Schema 2:

```text
AustralianPassport(passportNo, dateIssued, dateExpired, personID)
PK(passportNo)
FK(personID) ~> Person(personID)
```

2. **One-to-Many** (`1:*`) and Many-to-One (`*:1`)

For example:

![One-to-Many](/images/database-conceptual-design/one-to-many-2.png)

Relational Schema 1:

```text
Course(courseID, courseName)
PK(courseID)
```

Relational Schema 2:

```text
Tutorial(classNo, location, courseID)
PK(classNo)
FK(courseID) ~> Course(courseID)
```

3. **Many-to-Many** (`*:*`) or (`0:*`) or (`m:n`)

For example:

![Many-to-Many](/images/database-conceptual-design/association-class-after.png)

Relational Schema 1:

```text
Student(studentID, emailID, studentName)
PK(studentID)
CK(emailID)
```

Relational Schema 2:

```text
Course(courseID, courseName)
PK(courseID)
```

Relational Schema 3:

```text
Enrolment(StudentID, CourseID, dateCommenced, mark)
PK(StudentID, CourseID)
FK(StudentID) ~> Student(StudentID)
FK(CourseID) ~> Course(CourseID)
```

### Recursive Relationship / Self Association

For example:

![Recursive Relationship](/images/database-conceptual-design/recursive-1.png)

Relational Schema 1:

```text
Employee(ID, name)
PK(ID)
```

Relational Schema 2:

```text
Supervision(supervisorID, superviseeID)
PK(supervisorID, superviseeID)
FK(supervisorID) ~> Employee(ID)
FK(superviseeID) ~> Employee(ID)
```
