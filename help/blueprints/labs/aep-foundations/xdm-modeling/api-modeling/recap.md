---
title: Recap
description: Review the API modeling lab steps, from creating the Customer Account schema through JSON Patching, marking identities, and building the lookup relationship.
doc-type: article
solution: Experience Platform
exl-id: 0279cd68-af7b-43b4-8c6c-d8f8f96f0c0e
---

# Recap

>[!VIDEO](https://video.tv.adobe.com/v/3459564/?quality=12&learn=on)

>[!NOTE]
>
>First off congratulations!  Building things via API is not easy but if you understand how it works you will better understand how the system works.  Kudos!



## **Created the Customer Account Schema**

You created the schema by `$ref` both the Adobe created field groups and your own custom created field group (i.e. tenant).  You also `$ref` the class the schema is meant to represent (i.e. XDM Individual Profile)

![LxxLyKc0x1oi Ol6EkZF7zEpODWNLm3AEK 20241023 222046.png "Customer Account Schema"](assets/n-ADAXZy_lxxLyKc0x1oi-Ol6EkZF7zEpODWNLm3AEK-20241023-222046.png "Customer Account Schema")


## **JSON Patch'd the Customer Account Schema**

You used the JSON Patch method to modify the Customer Account schema to add a new field to the plan object.  You did this by patching not the schema but the `$ref` custom field group you defined in the 1st step called `Customer Account Details`

![LxxLyKc0x1oi  880fF92TbOADaEKgpMcw 20241023 235922.png "JSON Patch of planDescription field"](assets/n-ADAXZy_lxxLyKc0x1oi--880fF92TbOADaEKgpMcw-20241023-235922.png "JSON Patch of planDescription field")


## **Marked Identity Fields**

In this step you performed two (2) of the same `POST` calls to create `Identity Descriptors` for both the `_devbc.customerID` and `personalEmail.address` fields within the the Customer Account schema.

1. The `_devbc.customerID` field was set as the **primary** identity
1. The `personalEmail.address` field was **not set** as a primary

![LxxLyKc0x1oi jEL3jslviLmNs4IVEtej4 20241024 000121.png "Customer Account schema identity fields"](assets/n-ADAXZy_lxxLyKc0x1oi-jEL3jslviLmNs4IVEtej4-20241024-000121.png "Customer Account schema identity fields")

## **Created Lookup Relationship**

The last step was to create the relationship between the Customer Account and Plan schemas from the XDM ERD on Paper lab.  This required you to create both a relationship descriptor (i.e. how to relate the `Customer Account` schema to the `dep: Plan [Lookup ]` schema) and a reference identity descriptor on the Customer Account schema.

![LxxLyKc0x1oi KTMOL8mKRzcN cEZ6W26E 20241024 000424.png "Relationship & Reference Identity Descriptors"](assets/n-ADAXZy_lxxLyKc0x1oi-KTMOL8mKRzcN-cEZ6W26E-20241024-000424.png "Relationship & Reference Identity Descriptors")

>[!NOTE]
>
>The `referenceIdentity` descriptor tells the Real-Time Customer Profile what field in the `Customer Account` schema matches to what identity namespace. Remember that when you define a lookup schema you must mark a field as a primary identity and assign it a namespace with a type of `non-person`.
