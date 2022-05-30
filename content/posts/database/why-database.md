+++
date = 2022-02-22T06:23:37+10:30
title = "Database - Why?"
slug = "database-why"
aliases = "/database-why/"
description = "Why Databases?"
thumbnail = "images/database-why/modern.jpg"
tags = [
    "database",
]
categories = [
    "database",
]
draft = false
+++

### Table of Contents

1. [Traditional - Physical Data Storage](#traditional-and-physical-data-storage)
1. [Modern - Digital Data Storage](#modern-and-digital-data-storage)
1. [Database-System Applications](#database-system-applications)

### Traditional And Physical Data Storage

1. Limited by physical size
1. Limited multi-access - a borrowed book can only be viewed by one person at a
   time.
1. Limited search methods (title, author, subject)
1. Slow turn-around
1. Multiple indexes that must be rigorously maintained.
1. Complex Query Limitations - vast amounts of time wasted counting the number
   of books on a subject or by an author.
1. Anomalies: - What IFs:
- A card is misplaced?
- A catalogue card is misplaced?
- An item is entered into / deleted in one index but not the others?

![Traditional Data Storage](/images/database-why/traditional.webp)
Image Source:
*[Britannica](https://www.britannica.com/story/a-brief-history-of-libraries)*

### Modern And Digital Data Storage

Data can now be stored in files, such as text files, Excel sheets, Word
documents.

![Modern Data Storage](/images/database-why/modern.jpg)
Image Source: *[Orange
Matter](https://orangematter.solarwinds.com/2018/09/06/databases-101-factors-to-consider-when-choosing-a-database/)*

##### Advantages

1. Low cost.
1. No extra software / hardware is needed.

##### Disadvantages

1. Size - the larger the volume of data, the slower the retrieval of them (yet
   still better than physical data).
1. Update / Synchronisation - files are hard to share. Updates from multiple
   users often end up with multiple versions of the same file or even
   overwriting someone's changes!
1. Accuracy - duplication is wasteful and can cause confusion (inconsistent
   data).
1. Security - restriction to some fields is more difficult to manage (e.g.,
   taxFileNumbers, IDs + usernames).

### Database-System Applications

Database systems are used to manage collections of data that:
- are highly valuable,
- are relatively large, and
- are accessed by multiple users and applications, often at the same time.

Here are some representative applications:
- **Enterprise Information**
  - Sales: For customer, product, and purchase information.
  - Accounting: For payments, receipts, account balances, assets, and other
    accounting information.
  - Human resources: For information about employees, salaries, payroll taxes,
    and benefits, and for generation of paychecks.
- **Manufacturing**: For management of the supply chain and for tracking
  production of items in factories, inventories of items in warehouses and
  stores, and orders for items.
- **Banking and Finance**
  - Banking: For customer information, accounts, loans, and banking
    transactions.
  - Credit card transactions: For purchases on credit cards and generation of
    monthly statements.
  - Finance: For storing information about holdings, sales, and purchases of
    financial instruments such as stocks and bonds; also for storing real-time
    market data to enable online trading by customers and automated trading by
    the firm.
- **Universities**: For student information, course registrations, and grades
  (in addition to standard enterprise information such as human resources and
  accounting).
- **Airlines**: For reservations and schedule information. Airlines were among
  the first to use databases in a geographically distributed manner.
- Telecommunication: For keeping records of calls, texts, and data usage,
  generating monthly bills, maintaining balances on prepaid calling cards, and
  storing information about the communication networks.
- **Web-based services**
  - Social-media: For keeping records of users, connections between users (such
    as friend/follows information), posts made by users, rating/like information
    about posts, etc.
  - Online retailers: For keeping records of sales data and orders as for any
    retailer, but also for tracking a user’s product views, search terms, etc.,
    for the purpose of identifying the best items to recommend to that user.
  - Online advertisements: For keeping records of click history to enable
    targeted advertisements, product suggestions, news articles, etc. People
    access such databases every time they do a web search, make an online
    purchase, or access a social-networking site.
- **Document databases**: For maintaining collections of new articles, patents,
  published research papers, etc.
- **Navigation systems**: For maintaining the locations of varies places of
  interest along with the exact routes of roads, train systems, buses, etc.

Adapted from *[Database System
Concepts](https://www.google.com.au/books/edition/Database_System_Concepts/dc5HswEACAAJ?hl=en)*
(2019) by Silberschatz, Korth, and Sudarshan.

-> [PDF
Version](https://raw.githubusercontent.com/Sorosliu1029/Database-Systems/master/Database-System-Concepts-7th-Edition.pdf)
