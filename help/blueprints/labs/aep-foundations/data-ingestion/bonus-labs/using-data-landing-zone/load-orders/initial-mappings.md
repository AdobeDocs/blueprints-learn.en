---
title: Initial Mappings
description: Manually map the required _id and timestamp fields for an Experience Event dataset using calculated field expressions.
doc-type: article
solution: Experience Platform
exl-id: 4052d104-bf0c-4b2d-a298-8075279aeaf8
---

# Initial Mappings

As in the previous exercise, you will need to verify the mapping and in some cases, modify it. 

## Verify ML Recommendations

1. In the Mapping step, ML Recommendations will automatically map most attributes. However, you will also see several errors. The initial screen may look similar to below.

![V id times.png " id, timestamp are two fields that the ML Recommender will not generate the mapping for"](assets/7ry70XWYr2bYtJe5zjW_v_id-times.png "_id, timestamp are two fields that the ML Recommender will not generate the mapping for")

>[!NOTE]
>
>Since we are mapping an Experience Event dataset for the first time, note that **\_id** and **timestamp** are never recommended or mapped by default for Experience Events. You have to manually ensure that these are mapped correctly.

## Map *\_id, timestamp *and ***order.\_devbc.acqSource** ***Fields**

1. To map **\_id,** write the following calculated field expression and click preview

```none
concat(orderID, "-", lastOrderStatusUpdate)
```

![Calculat.png "Calculated field for mapping  id will look similar to this. Click Save to save the calculated field"](assets/sV0ke-0RcFdpZvKfxJzNJ_calculat.png "Calculated field for mapping _id will look similar to this. Click Save to save the calculated field")

![Map the calculated field to id.png "Map the calculated field to  id"](assets/gjHr1I9RfX9NIuy-B2czo_map-the-calculated-field-to-id.png "Map the calculated field to _id")

3\. Ensure that **timestamp** field in the target schema is mapped to the following calculated field:

```none
lastOrderStatusUpdate
```

![Expression preview.png "Write the following expression and click Preview. NOTE that this value is case sensitive and must be written exactly this way"](assets/TqYEYOCfML2mnAjde38oT_expression-preview.png "Write the following expression and click Preview. NOTE that this value is case-sensitive and must be written exactly this way")

![Map the calculated field expression 22instore 22 to order devbcacqsource](assets/map-the-calculated-field-expression-22instore-22-to-order-devbcacqsource.png)

4\. Map the calculated field expression **"inStore"** to **order.\_devbc.acqSource**

![Write th.png "Write the following expression and click Preview. NOTE that this value is case sensitive and must be written exactly this way"](assets/r74-rI8dltmScxIdBOR3l_write-th.png "Write the following expression and click Preview. NOTE that this value is case-sensitive and must be written exactly this way")

## Handling Duplicate Mappings

If the mapping screen now complains there is a duplicate mapping such as **orderStatus** mapped to **order.\_devbc.acqSource,** click the "-" icon to remove the mapping.

>[!CAUTION]
>
>Remember that multiple input fields cannot be mapped to the same output field as this makes the mapping ambiguous. But a single input field can be mapped to multiple output fields in the XDM schema. 

![Duplicate mapping for.png "Duplicate mapping for "](assets/VA-Ih-jwYsHps6hnqh-x1_duplicate-mapping-for.png "Duplicate mapping for ")



![Duplicat.png "Duplicate mapping for order. devbc.acqSource since we created a calculated field and have already mapped to it. "](assets/tJE4v0HpQzToD1Hh4Uw6Q_duplicat.png "Duplicate mapping for order._devbc.acqSource since we created a calculated field and have already mapped to it. ")
