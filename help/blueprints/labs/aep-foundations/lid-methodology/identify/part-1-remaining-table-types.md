---
title: Part 1 - Remaining Table Types
description: Identify and label bridge tables and tables requiring denormalization across the Individual Profile, Experience Event, and Lookup ERDs.
doc-type: article
solution: Experience Platform
exl-id: 742b58fa-3feb-4275-ab45-eb8d3aade22c
---

# Part 1 - Remaining Table Types

## Lecture

>[!VIDEO](https://video.tv.adobe.com/v/3459082/?quality=12&learn=on)



## Lab Details

Identify and label tables in the Connection 5G warehouse and streaming ERDs that fit into one of the categories below

- Bridge table (labeled as “**B**”)
- New lookup tables that exist due to bridge tables
- Tables that will require denormalization (labeled as “**D**”)

>[!CAUTION]
>
>Order is very important here! Make sure you are following the steps in order as each step is dependent on the previous



## Step 1:  Identify & Label XDM Individual Profile Tables

1. Identify all tables directly related to (one hop away from) the XDM Individual Profile  tables that do not yet have a label. Mark them with a star "**\***"
   .
1. Looking at only the schema’s you just labeled with a star perform the following tasks:
   1. **Add a label “B” for bridge table** – a table is considered a bridge table when two or more tables are related to it with the many side of the relationship from both tables pointing to the bridge table
   2. **Add a label “D” for tables to denormalize** – any entity that has a 1\:M or M:1 cardinality with the XDM Individual Profile labeled table and is not already marked

>[!NOTE]
>
>Remember Bridge Table Rule #1.
>
>When encountering a bridge table directly related to either a “P” or “E” the M:1 relationship acts like a lookup. Otherwise follow the standard denormalization rules.



## Step 2:  Identify & Label XDM Experience Event Tables

1. Identify all tables directly related to (one hop away from) the Experience Event labeled tables that do not yet have a label. Mark them with a star.
1. Looking at only the tables you just labeled with a star perform the following tasks:
   1. **Add a label “B” for bridge tables** – a table is considered a bridge table when two or more tables are related to it with the many side of the relationship pointing to the bridge table
   2. **Add a label “D” for tables to denormalize** – any table that has a 1\:M or M:1 cardinality with the XDM Experience Event labeled table and is not already marked

>[!NOTE]
>
>Remember Bridge Table Rule #1.
>
>When encountering a bridge table directly related to either a “P” or “E” the M:1 relationship acts like a lookup. Otherwise follow the standard de-normalization rules.



## Step 3: Identify & Label Lookup Tables

1. Identify all tables related to (does not matter how many hops you make) any of the Lookup labeled tables that do not yet have a label. Mark them with a star "**\***".
1. Looking at only the tables you just labeled with a star perform the following tasks:
   1. Add a label “**B**” for bridge tables – a table is considered a bridge table when two or more tables are related to it with the many side of the relationship pointing to the bridge table
   2. Add a label “**D**” for tables to de-normalize – any table that has a 1\:M or M:1 cardinality with a Lookup table or bridge table related to a lookup

>[!NOTE]
>
>Remember Bridge Table Rule #1.
>
>When encountering a bridge table directly related to either a “P” or “E” the M:1 relationship acts like a lookup. Otherwise follow the standard denormalization rules **(hint, hint)**



## Review

>[!VIDEO](https://video.tv.adobe.com/v/3459064/?quality=12&learn=on)
