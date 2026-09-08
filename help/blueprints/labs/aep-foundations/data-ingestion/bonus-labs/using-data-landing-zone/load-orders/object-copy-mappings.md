---
hold: true
title: Object Copy Mappings
description: Object Copy Mappings
doc-type: article

solution: Experience Platform
exl-id: 762d0e19-ed1c-4f4d-91ec-a962bd6277a7
---

In this section, you will add the object copy mappings and create some overrides. 

## Passthrough Mappings

Add the following passthrough mappings with **Products\[\*] **and **Products\[\*].productID **by clicking New field type and add a new field for each row here. Some may already be present due to ML Recommendations. 

| Source Column           | XDM Column                |
| ----------------------- | ------------------------- |
| orderStatus             | eventType                 |
| lastOrderStatusUpdate   | timestamp                 |
| Products\[\*]           | productListItems\[\*]     |
| Products\[\*].productID | productListItems\[\*].SKU |

>[!NOTE]
>
>Note that ***Products\[\*]*** is doing a 1-1 field mapping between the object fields and the explicit field mapping ***Products\[\*].productID***is overriding the default copy.

>[!NOTE]
>
>***Products\[\*].productID ***is also mapped to ***prodictListItems\[\*].SKU ***in addition to ***prodictListItems\[\*].\_id*****. **This is an example of a single input field being mapped to multiple output fields in the XDM schema. Keep the mapping as it is.

2\. Keep the mapping **products\[\*].price** to **productListItems\[\*].priceTotal**

## Add Overrides on Certain Fields 

1. Override the object copy mappings by 
   1. Mapping **products\[\*].make** to **productListItems\[\*].\_devbc.make**
   2. Mapping **products\[\*].model** to **productListItems\[\*].\_devbc.model**

## Delete Overrides on Certain Fields

1. Observe that** productListitems.currencyCode** and **productListItems.quantity** are auto-populated. 
1. Remove the **productListItems\[\*].quantity** and **productListItems\[\*].currencyCode **mappings.
1. The overrides do not happen and the object copy takes over with passthrough fields going through. 


## Summary of Object Copy Mappings, Overrides and Deletes

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

## Verify Mappings

There are 2 sets of mappings that you should verify. In total, you should have 6 mappings after the removal of 2. 



![The resultant mappings for productlistitems should look like this.png "The resultant mappings for ProductListItems\[*] should look like this"](assets/pxtfzDmbEF935LVFdNUgL_the-resultant-mappings-for-productlistitems-should-look-like-this.png "The resultant mappings for ProductListItems\[*] should look like this")

![The resultant mappings for productlistitems should look like this copy](assets/the-resultant-mappings-for-productlistitems-should-look-like-this-copy.png)

