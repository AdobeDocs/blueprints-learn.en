---
hold: true
title: Denormalize
description: Apply the LID methodology's denormalization rules to fold bridge and dependent tables from an ERD back into their parent profile, event, and lookup tables.
doc-type: article
solution: Experience Platform
exl-id: c98c9f58-03bc-4b28-becb-f84f3de04300
---

# Denormalize

## Lecture

In this video you will learn the three denormalization rules for folding lookup and bridge tables back into their parent tables, plus how personalization and streaming segmentation requirements affect those decisions.

>[!VIDEO](https://video.tv.adobe.com/v/3459083/?quality=12&learn=on)



## Lab details

>[!NOTE]
>
>This lab focuses only on the Connection 5G warehouse ERD

## Denormalization rules:

1. Any table in the relational model that is labeled as a “**D**” with a 1\:M cardinality or labeled as “**B**” will be defined as an object array or map on the parent table
1. Triggered by rule #1, before denormalizing “**D**” or “**B**” tables that act as arrays or maps, interrogate them to determine how best to denormalize them back into their parent table
1. Any table in the relational model that is labeled as “**D**” with a cardinality of M:1 will act as either an object or a list of fields on its parent table

## Denormalization for personalization rules:

Always remember to review the customer use cases when building out the data model.  Keep in mind the following:

- Streaming segmentation does not have access to lookup tables at evaluation time
- Only the traits and segment memberships of a profile are accessible for personalizing content

![Connection 5G use cases considered when applying denormalization for personalization](assets/denormalize-connection-5g-use-cases.png "Connection 5G Use Cases")

>[!NOTE]
>
>Remember to reference the Connection 5G Training Scenario.pdf during this lab!



## Step 1 – Fill in the Individual Profile table

1. Write in the fields that need to be denormalized back on the Customer Account table from any related “**B**” or “**D**” schemas
1. Reviewing the use cases above what additional fields are required to support streaming segmentation and/or personalization? Add those fields to the table



## Step 2 – Fill in the Experience Event tables

1. Write in the fields that need to be denormalized back into the Billing and Orders tables from any related “**B**” or “**D**” tables
1. Reviewing the use cases above what additional fields are required to support streaming segmentation and/or personalization? Add those fields to the table



## Step 3 – Fill in the Lookup tables

1. Write in the fields that need to be denormalized back into the Product lookup table from any related “**B**” or “**D**” tables
1. Reviewing the use cases above what additional fields are required to support streaming segmentation and/or personalization? Add those fields to the table




## Review

The below video reviews how the Connection 5G tables were denormalized into arrays and objects, and how the acquisition and upsell use cases required bringing additional fields back onto the primary profile and event tables.

>[!VIDEO](https://video.tv.adobe.com/v/3459086/?quality=12&learn=on)
