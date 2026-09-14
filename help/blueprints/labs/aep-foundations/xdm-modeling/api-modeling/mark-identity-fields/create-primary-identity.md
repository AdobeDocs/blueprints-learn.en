---
title: Create primary identity
description: Use the schema registry API to create a primary customerID identity descriptor for the Customer Account schema.
doc-type: article
solution: Experience Platform
exl-id: db690081-e857-4875-8bb9-7ac197d73cab
---

# Create primary identity

1. Click on the `Step 1 - Create Primary Identity for Customer Account Schema` API request in the `XDM Schema Lab -> Create Identity Descriptors` folder

   ![Step 1 - Create Primary Identity for Customer Account Schema Postman request](assets/create-primary-identity-step-1-postman-request.jpeg "Step 1 - Create Primary Identity for Customer Account Schema")

   >[!CAUTION]
   >
   >Do not execute the request yet



1. Update the `xdm:sourceSchema` value in the body of the request using the `$id` you saved from the [Create Schema](../build-schema/create-schema.md)  lab step

1. Update the `xdm:isPrimary` value in the body of the request to `true`

   EXAMPLE ONLY

   ```json
   {
     "@type": "xdm:descriptorIdentity",
     "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
     "xdm:sourceVersion": 1,
     "xdm:sourceProperty": "/_devbc/customerID",
     "xdm:namespace": "customerID",
     "xdm:property": "xdm:code",
     "xdm:isPrimary": true
   }
   ```

   >[!NOTE]
   >
   >Remember to update the tenant name above (\_devbc) with your own



1. Save your request before continuing using the `Save` button

1. Execute the API by clicking the `Send` button. You should now see a `201 Created` response like below

![201 Created response after successfully creating primary identity descriptor](assets/create-primary-identity-201-created-response.png "Successfully created primary identity descriptor")

>[!SUCCESS]
>
>Congratulations!  You just created a primary identity descriptor in your schema
