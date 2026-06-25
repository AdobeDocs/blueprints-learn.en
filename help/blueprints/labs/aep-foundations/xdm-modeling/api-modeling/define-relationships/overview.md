---
hold: true
title: Define Relationships
description: Define Relationships
doc-type: overview-page
solution: Experience Platform
exl-id: be672c84-09ac-4941-b40e-da7bd3fd6704
---

# **Relationship Descriptors**

In order to create a relationship from one schema to another, you need to create a Relationship Descriptor in the schema registry. A sample schema descriptor body looks like the following:

One-to-one Descriptor

```json
{
  "@type": "xdm:descriptorOneToOne",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:destinationSchema": "https://ns.adobe.com/devbc/schemas/6470f71181cf87aa39c2c2c43824eaa15f523652f7f88ff7",
  "xdm:destinationVersion": 1
}
```

Reference Identity Descriptor

```json
{
  "@type": "xdm:descriptorReferenceIdentity",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/6470f71181cf87aa39c2c2c43824eaa15f523652f7f88ff7",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:identityNamespace": "planID"
}
```

## **Your Objective**

Create Relationship identities for the Customer Account Schema. After performing the steps in the next section, your schema should look like below.

![LxxLyKc0x1oi dNRps1V ngEdac6AdbbpB 20241024 001844](assets/n-ADAXZy_lxxLyKc0x1oi-dNRps1V-ngEdac6AdbbpB-20241024-001844.png)

