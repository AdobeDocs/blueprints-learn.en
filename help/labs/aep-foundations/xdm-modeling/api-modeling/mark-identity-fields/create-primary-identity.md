---
title: Create Primary Identity
description: Create Primary Identity
doc-type: article
exl-id: db690081-e857-4875-8bb9-7ac197d73cab
---

1. Click on the `Step 1 - Create Primary Identity for Customer Account Schema` API request in the `XDM Schema Lab -> Create Identity Descriptors` folder

![](assets/0gqRD5pD7afT23gI40IFm_step-1-create-primary-identity-for-customer-account-schema.jpeg "Step 1 - Create Primary Identity for Customer Account Schema")

>[!CAUTION]
>Do not execute the request yet



2\. Update the `xdm:sourceSchema` value in the body of the request using the `$id` you saved from the [Create Schema](<././Build Schema/Create Schema.md>)  lab step

3\. Update the `xdm:isPrimary` value in the body of the request to `true`

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
>Remember to update the tenant name above (\_devbc) with the your own



4\. Save your request before continuing using the `Save` button

5\. Execute the API by clicking the `Send` button. You should now see a `201 Created` response like below

![](assets/6_lkbiD41A1JCXPl-iexl_successfully-created-primary-identity-descriptor.png "Successfully created primary identity descriptor")

>[!NOTE]
>Congratulations!  You just created a primary identity descriptor in your schema

