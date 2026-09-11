---
hold: true
title: Object copy mappings
description: Configure object copy mappings for a products array, then add and remove field-level overrides on top of the default copy.
doc-type: article
solution: Experience Platform
exl-id: 762d0e19-ed1c-4f4d-91ec-a962bd6277a7
---

# Object copy mappings

In this section, you will add the object copy mappings and create some overrides. 

## Passthrough mappings

Add the following passthrough mappings with **products\[\*]** and **products\[\*].productID** by clicking New field type and add a new field for each row here. Some may already be present due to ML Recommendations. 

| Source Column           | XDM Column                |
| ----------------------- | ------------------------- |
| orderStatus             | eventType                 |
| lastOrderStatusUpdate   | timestamp                 |
| products\[\*]           | productListItems\[\*]     |
| products\[\*].productID | productListItems\[\*].SKU |

>[!NOTE]
>
>Note that **products\[\*]** is doing a 1-1 field mapping between the object fields and the explicit field mapping **products\[\*].productID** is overriding the default copy.

>[!NOTE]
>
>**products\[\*].productID** is also mapped to **productListItems\[\*].SKU** in addition to **productListItems\[\*].\_id**. This is an example of a single input field being mapped to multiple output fields in the XDM schema. Keep the mapping as it is.

1. Keep the mapping **products\[\*].price** to **productListItems\[\*].priceTotal**

## Add overrides on certain fields 

1. Override the object copy mappings by 
   1. Mapping **products\[\*].make** to **productListItems\[\*].\_devbc.make**
   2. Mapping **products\[\*].model** to **productListItems\[\*].\_devbc.model**

## Delete overrides on certain fields

1. Observe that **productListItems.currencyCode** and **productListItems.quantity** are auto-populated. 
1. Remove the **productListItems\[\*].quantity** and **productListItems\[\*].currencyCode** mappings.
1. The overrides do not happen and the object copy takes over with passthrough fields going through. 


## Summary of object copy mappings, overrides and deletes

| Source Column              | XDM Column                          | Action                                 |
| -------------------------- | ----------------------------------- | -------------------------------------- |
| products\[\*]              | productListItems\[\*]               | `Add`       |
| products\[\*].productID    | productListItems\[\*].SKU           | `Add`       |
| products\[\*].productID    | productListItems\[\*].\_id          | `No change` |
| products\[\*].make         | productListItems\[\*].\_devbc.make  | `Change`    |
| products\[\*].model        | productListItems\[\*].\_devbc.model | `Change`    |
| products\[\*].price        | productListItems\[\*].priceTotal    | `No change` |
| products\[\*].quantity     | productListItems\[\*].quantity      | `Remove`    |
| products\[\*].currencyCode | productListItems\[\*].currencyCode  | `Remove`    |

## Verify mappings

There are 2 sets of mappings that you should verify. In total, you should have 6 mappings after the removal of 2. 



![Resultant mappings for productListItems after adding object copy overrides](assets/object-copy-mappings-resultant-mappings-for-productlistitems.png "The resultant mappings for ProductListItems\[*] should look like this")

![Second view of the resultant mappings for productListItems after object copy overrides](assets/object-copy-mappings-resultant-mappings-for-productlistitems--2.png)
