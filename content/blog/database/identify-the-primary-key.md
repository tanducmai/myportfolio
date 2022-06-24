+++
date = 2022-02-25T17:54:53+10:30
title = "Identify the Primary Key"
slug = "database-identify-the-primary-key"
aliases = "/database-identify-the-primary-key/"
description = "Database - Identify the Primary Key"
thumbnail = "images/database/blog/key-concepts/thumbnail.png"
tags = [
    "database",
    "fundamentals",
    "primary key",
]
categories = [
    "database",
]
draft = false
+++

![Keys in DBMS](/images/database/blog/key-concepts/thumbnail.png)
Image Source:
*[Arvindzeclass](https://www.arvindzeclass.in/2021/06/What-is-primary-key.html)*

Picking a good Primary Key from a list of available Candidate Keys might be an
unappealing process, but try to stick to these rules to make your life easier.

### Keep The Primary Key As Small As Possible

Imagine that the PK will be distributed among other relations.

- 1000s of copies of that PK value will appear in the database, which will
  overload the system.

That is, the smaller they are, the fewer bytes the DBMS has to load into RAM to
find related records.

E.g. Picking *studentName + birthDate + address* is bad as it is large! Try to
keep it below 3 attributes.

### Pick Primary Keys From Attributes That Are Stable

You will definitely not want the DBMS to constantly update Foreign Key values
that reference changing PK values!

Thus, pick a column that has no inherent meaning for the entity or does not
change.

E.g. studentID and productID are good choices.

Picking studentName + address or mobilePhone is bad since these can change over
time.

### Where Possible, Small Natural Keys May Improve Data Readability

Abbreviated names can be excellent: *st* for street, *rd* for road, *ave* for
avenue.

Surrogate Keys have no meaning (e.g., streetTypeID = 1, streetType = ‘Road’).

### Still Have Not Got Any Good Primary Keys? - Use A Surrogate Key

Nonetheless, keep in mind that this is more data to manage which has no meaning
or relationship to the business data.
