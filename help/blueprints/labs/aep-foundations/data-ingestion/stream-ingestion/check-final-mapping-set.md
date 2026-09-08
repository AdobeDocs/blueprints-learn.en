---
title: Check Final Mapping Set
description: Check Final Mapping Set
doc-type: article
solution: Experience Platform
exl-id: 8802aaca-f566-4972-8bd6-41aca9fae9bf
---

# Passthrough Mappings

>[!CAUTION]
>
>Ensure your final mapping matches what is shown below before continuing.

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



## Calculated Mappings

>[!NOTE]
>
>Be aware that the mappings for `birth_birth` are different from the batch ingestion lab mappings due to how the date is formatted.  Batch is using backslashes `/` whereas streaming is using dashes `-`

| Calculated fields                                                                                                                   | XDM Field                  |
| ----------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| iif(sms\_optIn == null or sms\_optIn == "", 'n', sms\_optIn)                                                                        | consents.marketing.sms.val |
| concat(date\_part("mm", date(birth\_Date, "yyyy-M-d")).toString(), "-", date\_part("dd", date(birth\_Date, "yyyy-M-d")).toString()) | person.birthDayAndMonth    |
| date\_part("yyyy",date(birth\_Date,"yyyy-M-d"))                                                                                     | person.birthYear           |

>[!CAUTION]
>
>Ensure your final mapping matches to what is shown below before continuing



## Finalize Dataflow

When you are done click the **Next** button and then click the Finish button to update the dataflow with the new mapping logic.

![Review the details and click finish to save the dataflow](assets/review-the-details-and-click-finish-to-save-the-dataflow.png)



You should now see the a screen that displays the HTTP API account you created with all the associated dataflows using that account. The dataflow you created should be shown as well.
