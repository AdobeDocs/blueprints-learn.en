---
title: Label
description: Label
doc-type: article
solution: Experience Platform
exl-id: 332ead7a-ca6e-4e30-bb35-8419c060c596
---

# Lecture

>[!VIDEO](https://video.tv.adobe.com/v/3459087/?quality=12&learn=on)



## Lab Details

Label the tables from the Connection 5G data warehouse ERD and Streaming ERD with the appropriate XDM class label for Individual Profile, Experience Event, and Lookup tables.

Keep in mind the following when performing the lab:

- **Individual Profile (traits) – **uniquely describes the traits of a person (e.g. name, email, address, preferences, etc.)
- **Experience Event (behaviors) – **describe interactions and touchpoints a person has with a brand/company (e.g. web page visit, purchase, call center interactions, application submit, etc.)
- **Lookups (supporting) – **provide additional contextual information in support of the Individual Profile or Experience Event



## Step 1.  Label XDM Individual Profile Tables

1. Identify all the source tables which represent an individual person in both the customer data warehouse ERD and the customer streaming ERD. 
1. Mark each table with a “**P**” signifying it is part of the XDM Individual Profile class

>[!NOTE]
>
>Only mark the tables which uniquely represent an individual person's traits



## Step 2.  Label XDM Experience Event Tables

1. Identify all the source tables which represent the behavior of an individual person in both the Connection 5G data warehouse ERD and Streaming ERD.
1. Mark each table with an “**E**” signifying it is part of the XDM Experience Event class.

>[!NOTE]
>
>Only mark the tables which uniquely represent an individual person’s behavior

 

## **Step 3.  Label XDM Supporting Tables**

1. Identify all the source tables which represent lookup data and are directly related to either a **“P” **or **“E” **table you have marked in either the Connection 5G data warehouse ERD and Streaming ERD.
1. Mark each table with a **“L” **signifying it is part of a non-person custom XDM class.

>[!NOTE]
>
>Lookup tables can only be 1 join level or "hop" away from either a “P” or “E” labeled table



## Review

>[!VIDEO](https://video.tv.adobe.com/v/3459081/?quality=12&learn=on)

