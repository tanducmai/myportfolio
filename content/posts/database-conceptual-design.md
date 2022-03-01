+++ 
date = 2022-02-28T19:30:29+10:30
title = "Database - Conceptual Design"
slug = "database-conceptual-design"
aliases = "/database-conceptual-design/"
description = "Database Conceptual Design"
thumbnail = "images/database-fundamentals/database.png"
tags = [
    "database",
    "fundamentals",
]
categories = [
    "database",
]
draft = true
+++

### Table of Contents

1. [What is a Conceptual Design?](#what-is-a-conceptual-design)
1. [Entity Relationship (ER) Model](#entity-relationship-(er)-model)

### What Is A [Conceptual](https://www.oxfordlearnersdictionaries.com/definition/english/conceptual?q=conceptual) Design

When designing a database, we should:

1. Create a list of *all* the **real-world** AND **conceptual objects** that we
   need to store data about.
1. To each of those items, list *all* the **attributes** required to capture the
   desired data.
1. Check that each of our objects only captures the **relevant information** to
   that object.
1. Check to see if there are any Candidate Keys:

- Do they apply to *all records in all cases*?
- If so, pick the best one (usually the smallest one) as the *Primary Key*.
- If not, add an artificial PK - *Surrogate Key*.

### Entity Relationship (ER) Model

**Entities**

- Reflect *real-world* and *theoretical/conceptual objects*.
  - A real-world object is one that can be easily identifiable and
    distinguishable.
  - Real-world: Book, Car, etc.
  - Conceptual: Class, COurse, etc.
- Represent what the database keeps track of.
- Translated into *relations/tables* in the final database.
- Some entities may be the result of relationships between other entities.
  - E.g., StudentClasses, StudentCourses, CourseBooks
- To simplify, entities correspond to classes in Object-Oriented Programming (OOP).
  - Tuples within a relation correspond to an instance of a class (an entity).

**Relationships & Multiplicity**

- Depict how many *objects* of one type *interact* with another.

**Attributes**

- Describe details of an entity.
- Can also be used to help record entity interactions.
- Can include the *domain*(data type, range of values).
  - Every attribute requires a data type (int, varchar, etc.)
  - Depending on the situtation, it is not necessary to include the range of
    values.
