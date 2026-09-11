---
title: Recap
description: Review the API modeling lab steps, from creating the Customer Account schema through JSON Patching, marking identities, and building the lookup relationship.
doc-type: article
solution: Experience Platform
exl-id: 0279cd68-af7b-43b4-8c6c-d8f8f96f0c0e
---

# Recap

The below video recaps how you built the schema, identities, and relationship descriptors via API calls, and demonstrates how JSON Patch is used to modify a schema.

>[!VIDEO](https://video.tv.adobe.com/v/3459564/?quality=12&learn=on)

> [!TIP]
>
>First off congratulations! Building things via API isn't easy, but understanding how it works will help you understand the system as a whole. Kudos!



## Created the Customer Account schema

You created the schema by `$ref` both the Adobe created field groups and your own custom created field group (i.e. tenant).  You also `$ref` the class the schema is meant to represent (i.e. XDM Individual Profile)

![Customer Account schema referencing field groups and class via $ref](assets/recap-customer-account-schema.png "Customer Account Schema")


## JSON patch'd the Customer Account schema

You used the JSON Patch method to modify the Customer Account schema to add a new field to the plan object. You did this by patching the `$ref` custom field group called `Customer Account Details` you defined in [Create Custom Field Groups](build-schema/create-custom-field-groups.md), rather than patching the schema itself.

![JSON Patch request adding a planDescription field to the Customer Account Details field group](assets/recap-json-patch-plan-description-field.png "JSON Patch of planDescription field")


## Marked identity fields

In this step you performed two of the same `POST` calls to create `Identity Descriptors` for both the `_devbc.customerID` and `personalEmail.address` fields within the Customer Account schema.

1. The `_devbc.customerID` field was set as the **primary** identity
1. The `personalEmail.address` field was **not set** as a primary

![Customer Account schema showing primary and non-primary identity descriptors](assets/recap-marked-identity-fields.png "Customer Account schema identity fields")

## Created lookup relationship

The last step was to create the relationship between the Customer Account and Plan schemas from the XDM ERD on Paper lab.  This required you to create both a relationship descriptor (i.e. how to relate the `Customer Account` schema to the `dep: Plan [Lookup]` schema) and a reference identity descriptor on the Customer Account schema.

![Relationship descriptor and reference identity descriptor linking Customer Account to the Plan lookup schema](assets/recap-relationship-reference-identity-descriptors.png "Relationship & Reference Identity Descriptors")

>[!NOTE]
>
>The `referenceIdentity` descriptor tells the Real-Time Customer Profile what field in the `Customer Account` schema matches to what identity namespace. Remember that when you define a lookup schema you must mark a field as a primary identity and assign it a namespace with a type of `non-person`.
