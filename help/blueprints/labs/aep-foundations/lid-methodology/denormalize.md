---
title: Denormalize
description: Apply the LID methodology's denormalization rules to fold bridge and dependent tables from an ERD back into their parent profile, event, and lookup tables.
doc-type: article
solution: Experience Platform
exl-id: c98c9f58-03bc-4b28-becb-f84f3de04300
---

# Lecture

>[!VIDEO](https://video.tv.adobe.com/v/3459083/?quality=12&learn=on)



## Lab Details

>[!NOTE]
>
>Note for this lab we will only focus on the Connection 5G warehouse ERD only

## Denormalization Rules:

1. Any table in the relational model that is labeled as a “**D**” with a 1\:M cardinality or labeled as “**B**” will be defined as as an object array or map on the parent table
1. Triggered by rule #1, before denormalizing “**D**” or “**B**” tables that act as arrays or maps, interrogate them to determine how best to denormalize them back into their parent table
1. Any table in the relational model that is labeled as “**D**” with a cardinality of M:1 will act as either an object or a list of fields on its parent table

## Denormalization for Personalization Rules:

Always remember to review the customer use cases when building out the data model.  Keep in the mind the following:

- Streaming segmentation does not have access to lookup tables at evaluation time
- Only the traits and segment memberships of a profile are accessible for personalizing content

![Screenshot 2024 08 02 at 22035 pm.png "Connection 5G Use Cases"](assets/cfPXzjwC2RtwoTT31e5fr_screenshot-2024-08-02-at-22035-pm.png "Connection 5G Use Cases")

>[!NOTE]
>
>Remeber to reference the Connection 5G Training Scenario.pdf during this lab!



## Step 1 – Fill in the Individual Profile Table

1. Write in the fields that need to be de-normalized back on the Customer Account table from any related “**B**” or “**D**” schemas
1. Reviewing the use cases above what additional fields are required to support streaming segmentation and/or personalization? Add those fields to the table



## **Step 2 – Fill in the Experience Event Tables**

1. Write in the fields that need to be denormalized back into the Billing and Order’s table from any related “**B**” or “**D**” tables
1. Reviewing the use cases above what additional fields are required to support streaming segmentation and/or personalization? Add those fields to the table



## **Step 3 – Fill in the Lookup Tables**

1. Write in the fields that need to be de-normalized back into the Product lookup table from any related “**B**” or “**D**” tables
1. Reviewing the use cases above what additional fields are required to support streaming segmentation and/or personalization? Add those fields to the table




## Review

>[!VIDEO](https://video.tv.adobe.com/v/3459086/?quality=12&learn=on)
