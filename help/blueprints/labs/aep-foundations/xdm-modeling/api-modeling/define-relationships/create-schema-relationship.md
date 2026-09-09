---
title: Create Schema Relationship
description: Use the schema registry API to create a one-to-one relationship descriptor linking the Customer Account schema to a lookup Plan schema.
doc-type: article
solution: Experience Platform
exl-id: c9079585-fff1-4ee1-8992-93825fcde759
---

# Create Schema Relationship

1. Click on the` Step 2 - Relationship Descriptor Customer Account To Plan` API request in the `XDM Schema Lab -> Create Relationship Descriptors` folder

>[!CAUTION]
>
>Do not execute the request...yet

![Step 2 relationship descriptor customre acount to plan.png "Step 2   Relationship Descriptor Customre Acount to Plan"](assets/oCG9DCH3isLOcSg5GbDQB_step-2-relationship-descriptor-customre-acount-to-plan.png "Step 2 - Relationship Descriptor Customre Acount to Plan")



2\. Update the following properties in the body of the API call. 

- Set the value of the `xdm:sourceSchema` property to the `$id` of the Customer Account schema you saved from the [Create Schema](../build-schema/create-schema.md) lab step
- Set the value of the `xdm:sourceProperty` to the path of the `planID` field from the Customer Account Schema. 
- Set the value of the `xdm:destinationSchema` property to the `$id` of `dep: Lookup Plan` schema you saved in 1st step

>[!NOTE]
>
>Use the dot notation value of the planId field from the Customer Account Schema and replace the`.` with`/`
>
>
>Don't forget the leading `/` either 😄

EXAMPLE ONLY

```json
{
  "@type": "xdm:descriptorOnetoOne",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:destinationSchema": "https://ns.adobe.com/devbc/schemas/6470f71181cf87aa39c2c2c43824eaa15f523652f7f88ff7"
,
  "xdm:destinationVersion": 1
}
```

>[!NOTE]
>
>Remember to update the tenant name above (\_devbc) with the your own



3\. Save your request before continuing using the `Save` button

4\. Execute the API by clicking the `Send` button

You should now see a `201 Created` response like below

![Customer account plan relationship descriptor.png "Customer Account   Plan Relationship Descriptor"](assets/zt937YGQr28qtVyrsoTXw_customer-account-plan-relationship-descriptor.png "Customer Account - Plan Relationship Descriptor")

>[!NOTE]
>
>Remember the Real-Time Customer Profile (and all of Experience Platform) only supports what we call a **one (1) hop join** from either the XDM Individual Profile or XDM Experience Event schemas (i.e. you can only create one (1) level lookup relationships)

>[!NOTE]
>
>Did you notice the relationship descriptor `@type` is set to a value of `OneToOne`? Isn't the relationship between the Customer Account and Plan table in the XDM ERD on Paper a 1\:N?  What is going on?
>
>
>The Real-Time Customer Profile is built to describe the traits and behaviors of an individual person.  Therefore from a individual person lens a lookup table is **only** **ever** defined as a 1:1 relationship during segmentation.
>
>Its okay if your brain hurts...
