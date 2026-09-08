---
title: View Schema
description: View Schema
doc-type: article
solution: Experience Platform
exl-id: dae48ef4-f762-4173-8564-c1ad40c0109b
---

# ** View via the UI**

1. Open your browser and navigate back to the `Schema -> Browse` section.
1. Search for the schema `Sample Customer Schema - <your sandbox number>`
1. Notice that the relationship to the `dep: Plan [Lookup]` is defined

![LxxLyKc0x1oi vmcN6zFf9 JDETG 4ABvR 20241023 221048](assets/view-schema-1.png)


## View via the API

1. Select the `Step 4 - Get Customer Account Schema and it's descriptors` API by clicking on it

![LxxLyKc0x1oi xii169YWs00qVMMkpzrUJ 20241023 221315.png "Step 4   Get Customer Account Schema and its descriptors"](assets/n-ADAXZy_lxxLyKc0x1oi-xii169YWs00qVMMkpzrUJ-20241023-221315.png "Step 4 - Get Customer Account Schema and its descriptors")



2\. In the URL of the request replace the `<replace me>` with the `$meta:altId` you saved from the previous section [Create Schema](../build-schema/create-schema.md) as shown below

![XgdstULG2FTY7922R final step 4 request.png "Final Step 4 Request"](assets/t9-_xgdstULG2FTY7922R_final-step-4-request.png "Final Step 4 Request")



3\. Save the request using the `Save` button

4\. Execute the request by clicking the `Send `button

You should now see a `200 OK` response and you should be able to browse to the end of the schema you created to see the Identity through the lens of the XDM JSON structure



![KGWvIzg relationship descriptor.png "Relationship Descriptor"](assets/ngtzk5xPfeslE_KGWvIzg_relationship-descriptor.png "Relationship Descriptor")



![Pt4Ed88GbpjwD dSfX reference identity descriptor.png "Reference Identity Descriptor"](assets/yi_pt4Ed88GbpjwD-dSfX_reference-identity-descriptor.png "Reference Identity Descriptor")



