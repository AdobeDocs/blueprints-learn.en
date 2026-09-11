---
title: View Schema
description: View the Customer Account schema's lookup relationship to the Plan schema through both the schema UI and the Get Schema API.
doc-type: article
solution: Experience Platform
exl-id: dae48ef4-f762-4173-8564-c1ad40c0109b
---

# View Schema

## View via the UI

1. Open your browser and navigate back to the `Schema -> Browse` section.
1. Search for the schema `Sample Customer Schema - <your sandbox number>`
1. Notice that the relationship to the `dep: Plan [Lookup]` is defined

![Sample Customer Schema in the Experience Platform UI showing the dep: Plan Lookup relationship](assets/view-schema-relationship-to-plan-lookup-schema.png)


## View via the API

1. Select the `Step 4 - Get Customer Account Schema and its descriptors` API by clicking on it

   ![Step 4 - Get Customer Account Schema and its descriptors API call](assets/view-schema-step-4-get-schema-and-descriptors.png "Step 4 - Get Customer Account Schema and its descriptors")



2. In the URL of the request replace the `<replace me>` with the `$meta:altId` you saved from the previous section [Create Schema](../build-schema/create-schema.md) as shown below

   ![Step 4 request with the meta:altId appended to the URL](assets/view-schema-final-step-4-request.png "Final Step 4 Request")



3. Save the request using the `Save` button

4. Execute the request by clicking the `Send` button

You should now see a `200 OK` response and you should be able to browse to the end of the schema you created to see the Identity through the lens of the XDM JSON structure



![Relationship descriptor visible in the Customer Account schema JSON](assets/view-schema-relationship-descriptor.png "Relationship Descriptor")



![Reference identity descriptor visible in the Customer Account schema JSON](assets/view-schema-reference-identity-descriptor.png "Reference Identity Descriptor")
