+++
date = 2022-02-21T11:23:37+10:30
title = "Database - Why?"
slug = "database-why"
aliases = "/database-why/"
description = "Why Databases?"
thumbnail = "images/database-fundamentals.png"
tags = [
    "database",
]
categories = [
    "database",
]
draft = false
+++

### Table of Contents

1. [Traditional & Physical Data
   Storage](#problems-with-traditional-and-physical-data-storage)
1. [Modern & Digital Data Storage](#modern-and-digital-data-storage)

### Problems With Traditional And Physical Data Storage

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
Source:
*[Britannica](https://www.britannica.com/story/a-brief-history-of-libraries)*

### Modern And Digital Data Storage

Data can now be stored in files, such as text files, Excel sheets, Word
documents.

![Modern Data Storage](/images/database-why/modern.jpg)
Source: *[Orange
Matter](https://orangematter.solarwinds.com/2018/09/06/databases-101-factors-to-consider-when-choosing-a-database/)*

##### Advantages

1. Low cost
1. No extra software / hardware is needed

##### Disadvantages

1. Size - the larger the volume of data, the slower the retrieval of them (yet
   still better than physical data).
1. Update / Synchronisation - files are hard to share. Updates from multiple
   users often end up with multiple versions of the same file or even
   overwriting someone's changes!
1. Accuracy - duplication is wasteful and can cause confusion (inconsistent
   data).
1. Security - restriction to some fields is more difficult to manage (e.g., Tax
   File Numbers, IDs + usernames).
