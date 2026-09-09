---
title: Get Plan Schema ID
description: Query the tenant schema registry API to find and save the $id of the Plan lookup schema for use in a relationship descriptor.
doc-type: article
solution: Experience Platform
exl-id: f66e0483-b5b3-4493-b752-c4e00211a8bd
---

# List All Tenant Schemas

1. Click on the `Step 1 - Get Lookup Schemas`API request in the `XDM Schema Lab -> Create Relationship Descriptors` folder
1. Execute the API by clicking the `Send` button

![Step 1 get lookup schemas.jpeg "Step 1   Get Lookup Schemas"](assets/2WgUimjBRcQiUeBTOFrvq_step-1-get-lookup-schemas.jpeg "Step 1 - Get Lookup Schemas")

>[!NOTE]
>
>This GET call fetches all the schemas that exist within the "tenant" part of the schema registry (i.e. custom created schemas). We only need to search for the **Plan** schema so we can relate it to the Customer Account schema. 



## Identify the Plan Schema

1. Search for the `dep: Plan [Lookup] `schema in the calls response
1. Copy the `$id` of the schema and save it somewhere for future reference

![JkA 0UjRCfQ tCmSus dep lookup plan schema sid.png "dep: Lookup Plan schema $id"](assets/3__JkA-0UjRCfQ-tCmSus_dep-lookup-plan-schema-sid.png "dep: Lookup Plan schema $id")

>[!NOTE]
>
>This schema should be pre-deployed in your sandbox already

>[!WARNING]
>
>Do not continue until you have saved `$id` of the schema somewhere.  It will be required later to create the Relationship Descriptor
