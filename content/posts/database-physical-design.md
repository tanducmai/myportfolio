+++ 
date = 2022-03-08T23:40:53+10:30
title = "Database - Physical Design"
slug = "database-physical-design"
aliases = "/database-physical-design/"
description = "Database - Physical Design"
thumbnail = "images/database-conceptual-design/uml-example.png"
tags = [
    "database",
    "fundamentals",
    "SQL",
    "DBMS",
    "physical design",
]
categories = [
    "database",
]
draft = true
+++

### Table Of Contents

1. [Physical Modelling?](#physical-modelling)

### [Physical](https://www.oxfordlearnersdictionaries.com/definition/english/physical_1?q=physical) Modelling

After the [conceptual
design](https://tanducmai.com/posts/database-conceptual-design) and the
[physical design](https://tanducmai.com/posts/database-physical-design), the
next phase is to take the relational schemas and implement them using a DBMS.
- Structured Query Language (SQL) is a higher-level language (4GL) used to
  create the relational database and manage data within the database.

For example:

```sql
CREATE TABLE Project(
    ProjectName varchar(200),
    Budget decimal(6,2),
    Manager varchar(200),
    CONSTRAINT projectPk PRIMARY KEY (ProjectName),
    CONSTRAINT managerFk FOREIGN KEY (Manager) REFERENCES Manager(Name)
);
```
