---
title: Initial mappings
description: Manually map the required _id and timestamp fields for an Experience Event dataset using calculated field expressions.
doc-type: article
solution: Experience Platform
exl-id: 4052d104-bf0c-4b2d-a298-8075279aeaf8
---

# Initial mappings

As in the previous exercise, you will need to verify the mapping and in some cases, modify it. 

## Verify ML recommendations

1. In the Mapping step, ML Recommendations automatically map most attributes. However, you also see several errors. The initial screen may look similar to below.

![Mapping screen showing _id and timestamp as unmapped fields not recommended by ML](assets/initial-mappings-id-timestamp-unmapped-fields.png "_id, timestamp are two fields that the ML Recommender will not generate the mapping for")

>[!NOTE]
>
>Since we are mapping an Experience Event dataset for the first time, note that **\_id** and **timestamp** are never recommended or mapped by default for Experience Events. You have to manually ensure that these are mapped correctly.

## Map \_id, timestamp and order.\_devbc.acqSource fields

1. To map **\_id,** write the following calculated field expression and click preview

```none
concat(orderID, "-", lastOrderStatusUpdate)
```

![Calculated field for mapping _id, ready to save](assets/initial-mappings-calculated-field-for-id-mapping.png "Calculated field for mapping _id will look similar to this. Click Save to save the calculated field")

![Mapping the calculated field to the _id attribute](assets/initial-mappings-map-calculated-field-to-id.png "Map the calculated field to _id")

1. Ensure that **timestamp** field in the target schema is mapped to the following calculated field:

```none
lastOrderStatusUpdate
```

![Calculated field expression preview for the timestamp mapping](assets/initial-mappings-expression-preview.png "Write the following expression and click Preview. NOTE that this value is case-sensitive and must be written exactly this way")

![Mapping the calculated field expression "inStore" to order._devbc.acqSource](assets/initial-mappings-map-instore-expression-to-acqsource.png)

1. Map the calculated field expression **"inStore"** to **order.\_devbc.acqSource**

![Writing the "inStore" calculated field expression and clicking Preview](assets/initial-mappings-write-instore-expression-preview.png "Write the following expression and click Preview. NOTE that this value is case-sensitive and must be written exactly this way")

## Handling duplicate mappings

If the mapping screen now complains there is a duplicate mapping such as **orderStatus** mapped to **order.\_devbc.acqSource,** click the "-" icon to remove the mapping.

> [!NOTE]
>
>Remember that multiple input fields cannot be mapped to the same output field as this makes the mapping ambiguous. But a single input field can be mapped to multiple output fields in the XDM schema. 

![Duplicate mapping warning for orderStatus mapped to order._devbc.acqSource](assets/initial-mappings-duplicate-mapping-warning.png "Duplicate mapping for orderStatus mapped to order._devbc.acqSource")



![Duplicate mapping warning for order._devbc.acqSource after creating the calculated field](assets/initial-mappings-duplicate-mapping-for-acqsource.png "Duplicate mapping for order._devbc.acqSource since we created a calculated field and have already mapped to it. ")
