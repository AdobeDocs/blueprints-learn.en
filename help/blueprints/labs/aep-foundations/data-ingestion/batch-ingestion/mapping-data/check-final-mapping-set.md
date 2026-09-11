---
hold: true
title: Check final mapping set
description: Compare your simple and calculated field mappings for the Customer Account schema against the expected final mapping set.
doc-type: article
solution: Experience Platform
exl-id: d1521d08-1ccb-405f-b728-a2777598cb9f
---

# Check final mapping set

> [!NOTE]
>
>If you are coming from the Streaming Ingestion Lab please click the below link to proceed to the next step in that lab:
>
>[Streaming Ingestion Lab - Check Final Mapping Set](../../stream-ingestion/check-final-mapping-set.md) 



## Simple mappings

>[!NOTE]
>
>Replace the \<tenant-name> with the value from your sandbox

| Source Field              | Target Field                      |
| ------------------------- | --------------------------------- |
| account\_create\_date     | \<tenant-name>.account.createDate |
| account\_end\_date        | \<tenant-name>.account.endDate    |
| customer\_id              | \<tenant-name>.customerID         |
| plan\_name                | \<tenant-name>.plan.name          |
| plan\_id                  | \<tenant-name>.plan.planID        |
| billing\_city             | billingAddress.city               |
| billing\_zip\_code        | billingAddress.postalCode         |
| billing\_state            | billingAddress.state              |
| billing\_street\_address  | billingAddress.street1            |
| email\_optIn              | consents.marketing.email.val      |
| mobile\_phone             | mobilePhone.number                |
| firstName                 | person.name.firstName             |
| lastName                  | person.name.lastName              |
| email                     | personalEmail.address             |
| createDate                | repo.createDate                   |
| modifyDate                | repo.modifyDate                   |
| shipping\_city            | shippingAddress.city              |
| shipping\_zip\_code       | shippingAddress.postalCode        |
| shipping\_state           | shippingAddress.state             |
| shipping\_street\_address | shippingAddress.street1           |

> [!NOTE]
>
>Ensure your final mapping matches what is shown below before continuing.



## Calculated mappings

| Calculated fields                                                                                                                     | XDM Field                  |
| ------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| iif(sms\_optIn == null or sms\_optIn == "", 'n', sms\_optIn)                                                                          | consents.marketing.sms.val |
| concat(date\_part("month", date(birth\_Date,"M/d/yyyy")).toString(), "-", date\_part("day", date(birth\_Date,"M/d/yyyy")).toString()) | person.birthDayAndMonth    |
| date\_part("yyyy",date(birth\_Date,"M/d/yyyy"))                                                                                       | person.birthYear           |

> [!NOTE]
>
>Ensure your final mapping matches what is shown below before continuing
