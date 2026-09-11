---
hold: true
title: Create other identities
description: Use the schema registry API to create a non-primary email address identity descriptor for the Customer Account schema.
doc-type: article
solution: Experience Platform
exl-id: 22c40299-fb93-4d41-a23b-f8629df3e7b9
---

# Create other identities

1. Click on the `Step 2 - Create Email Address Identity for Customer Account Schema` API call in the `XDM Schema Lab -> Create Identity Descriptors` folder

>[!CAUTION]
>
>Do not execute the request...yet

![Step 2 - Create Email Address Identity for Customer Account Schema Postman request](assets/create-other-identities-step-2-postman-request.jpeg "Step 2 - Create email address identity descriptor")



1. Update the `xdm:sourceSchema` value in the body of the request using the `$id` you saved from the [Create Schema](../build-schema/create-schema.md)  lab step

1. Update the `xdm:isPrimary` value in the body of the request to `false`

EXAMPLE ONLY

```json
{
  "@type": "xdm:descriptorIdentity",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/personalEmail/address",
  "xdm:namespace": "Email",
  "xdm:property": "xdm:code",
  "xdm:isPrimary": false
}
```

>[!NOTE]
>
>Remember to update the tenant name above (\_devbc) with your own



1. Save your request before continuing using the `Save` button

1. Execute the API by clicking the `Send` button. You should now see a `201 Created` response like below

![201 Created response after successfully creating email address identity descriptor](assets/create-other-identities-201-created-response.png "Successful Identity Descriptor for Email Address")
