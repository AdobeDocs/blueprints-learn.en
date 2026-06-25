---
title: Part 2 - Key Fields
description: Part 2 - Key Fields
doc-type: article
solution: Experience Platform
exl-id: 24b6fdbd-0d59-4fe7-828e-c4bc7036db90
---

# Lecture

>[!VIDEO](https://video.tv.adobe.com/v/3459085/?quality=12&learn=on)



## Lab Details

## Identity Fields

- **Person identity **– Used to uniquely identify a person. They are only used in Primary Entity tables. There must be at least one of these but there can be more than one.
- **Relationship identity (i.e. non-person) **– Used to describe relationships from the Primary Entity tables of the Real-Time Customer Profile to an associated supporting entity class (i.e. Lookups). 
- **Primary identity **– Can be either a person identity or relationship (non-person) identity that is being used as a storage key and required for any schema being used by the Real-Time Customer Profile. For Primary Entity tables the identity also uniquely identifies a person. When specified for XDM Profile schemas and lookup schemas this field will determine whether a new record is created or an existing record is updated. There must be exactly one of these.

## Required Fields (XDM Experience Event Only)

- **\_id **- used by the Real-Time Customer Profile in conjunction with the Primary Identity to create a unique storage key for the event. Required to prevent accidental duplication of event data within Profile Service
- **Timestamp **– all events happen at a specific time and therefore every event requires a timestamp

Not required but highly encouraged:

- **Event Type **– describes the high-level behavior of the event data (i.e. purchase, reservation booked, etc.)

## General Rules

1. Bridge Table Rule #2 - in situations where a bridge table exists between a “**P**” or “**E**” parent (i.e. parent table) and a “**L**” table treat the bridge table as part of the parent table
1. Always validate that identities are unique to a **single** person at this stage to avoid rework during data ingestion
1. For Experience Event schemas, the Primary Identity is what uniquely identifies that behavior to a single person.
1. For lookup tables, the primary key (PK) from the relational model will always be the non-person Primary Identity

For each table from the Connection 5G Warehouse ERD and streaming ERD that you have labeled as either a **“P”, “E” or “L”,  **you will now perform the steps below to identify the primary identities, person identities, relationship identities and any required fields for the given schema classes.

>[!NOTE]
>
>Refer to the diagram below during the labs as you label identities on schemas
>
>![Image](assets/xuugRlx0ZrPbHIqjSrPeF_image.png)



## **Step 1 – Label Key Fields in the XDM Individual Profile Tables**

Perform the below steps to identify the key fields within the Customer Account table:

- Identify the field that will be used as the Primary Identity and label it with a `PI`
- Identify all other Person Identities and label them with an `I`
- Identify any Relationship Identities and label them with a `R`



## **Step 2 – Label Key Fields in the XDM Experience Event Tables**

Perform the same set of tasks you did in Step #1  but now for the XDM Experience Event tables:

- Identify the field in each table that will be the Primary Identity and label it with a `PI`
- Identify all other Person Identities in each table and label them with an `I`
- Identify all Relationship Identities and label them with a `R`

In addition to the labels above also label the following:

- Identify or create the unique event id for each XDM Experience Event table and label it with a `_id`
- Identify the event's timestamp for each table and label it with an `T`
- Identify or create the Event Type for each table and label it with an `ET`



## **Step 3 – Label Key Fields in the Lookup Tables**

Identify in each lookup table the field that will be Primary Identity and label it with a `PI` 



## Review

>[!VIDEO](https://video.tv.adobe.com/v/3459088/?quality=12&learn=on)

