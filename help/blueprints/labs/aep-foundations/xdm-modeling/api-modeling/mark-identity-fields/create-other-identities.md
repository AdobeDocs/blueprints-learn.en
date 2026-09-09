---
title: Create Other Identities
description: Use the schema registry API to create a non-primary email address identity descriptor for the Customer Account schema.
doc-type: article
solution: Experience Platform
exl-id: 22c40299-fb93-4d41-a23b-f8629df3e7b9
---

# Create Other Identities

1. Click on the `Step 2 - Create Email Address Identity for Customer Account Schema` API call in the `XDM Schema Lab -> Create Identity Descriptors` folder

>[!CAUTION]
>
>Do not execute the request...yet

![BHmf step 2 create email address identity descriptor.jpeg "Step 2   Create email address identity descriptor"](assets/Nm-VdS97-5zSXpZm_BHmf_step-2-create-email-address-identity-descriptor.jpeg "Step 2 - Create email address identity descriptor")



2\. Update the `xdm:sourceSchema` value in the body of the request using the `$id` you saved from the [Create Schema](../build-schema/create-schema.md)  lab step

3\. Update the `xdm:isPrimary` value in the body of the request to `false`

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
>Remember to update the tenant name above (\_devbc) with the your own



4\. Save your request before continuing using the `Save` button

5\. Execute the API by clicking the `Send` button. You should now see a `201 Created` response like below

![Successful identity descriptor for email address.png "Successful Identity Descriptor for Email Address"](assets/WdV4wU2sci4CT-L4SHAM8_successful-identity-descriptor-for-email-address.png "Successful Identity Descriptor for Email Address")
