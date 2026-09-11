---
hold: true
title: Verify and schedule dataflow
description: Verify the complete Orders mapping set, preview the output, and schedule the dataflow to run every 15 minutes.
doc-type: article
solution: Experience Platform
exl-id: b7f0c43b-092c-45ba-b95b-27cb4a49d110
---

# Verify and schedule dataflow

## Double check mapping set

| #  | Source Column                               | XDM Column                                               |
| -- | ------------------------------------------- | -------------------------------------------------------- |
| 1  | orderStatus                                 | eventType                                                |
| 2  | lastOrderStatusUpdate                       | timestamp                                                |
| 3  | orderID                                     | order.orderID                                            |
| 4  | orderDate                                   | order.orderDate                                          |
| 5  | orderTotal                                  | order.priceTotal                                         |
| 6  | paymentType                                 | order.payment.paymentType                                |
| 7  | paymentAmount                               | order.payment.paymentAmount                              |
| 8  | paymentCurrencyCode                         | order.payment.currencyCode                               |
| 9  | paymentTransactionID                        | order.payment.transactionID                              |
| 10 | plan.ID                                     | order.\_devbc.plan.planID                                |
| 11 | customerID                                  | \_devbc.customerID                                       |
| 12 | personalEmail                               | \_devbc.personalEmail                                    |
| 13 | storeID                                     | store.storeID                                            |
| 14 | shippingStreetAddress                       | shipping.address.street1                                 |
| 15 | shippingCity                                | shipping.address.city                                    |
| 16 | shippingState                               | shipping.address.state                                   |
| 17 | shippingZip                                 | shipping.address.postalCode                              |
| 18 | shippingMethod                              | shipping.shippingMethod                                  |
| 19 | shippingAmount                              | shipping.shippingAmount                                  |
| 20 | shippingDestination                         | shipping.shippingDestination                             |
| 21 | billingStreetAddress                        | billing.address.street1                                  |
| 22 | billingCity                                 | billing.address.city                                     |
| 23 | billingState                                | billing.address.state                                    |
| 24 | billingZip                                  | billing.address.postalCode                               |
| 25 | products\[\*]                               | productListItems\[\*]                                    |
| 26 | products\[\*].productID                     | - productListItems\[\*].\_id - productListItems\[\*].SKU |
| 27 | products\[\*].make                          | productListItems\[\*].\_devbc.make                       |
| 28 | products\[\*].model                         | productListItems\[\*].\_devbc.model                      |
| 29 | products\[\*].price                         | productListItems\[\*].priceTotal                         |
| 30 | concat(orderID, "-", lastOrderStatusUpdate) | \_id                                                     |
| 31 | "inStore"                                   | order.\_devbc.acqSource                                  |



## Preview the mapping output

1. Preview the mapping output. Scroll through all the attributes to ensure there is no red exclamation next to any of the attributes on the right-hand side. 

![Preview mapping screen with no errors on any mapped attributes](assets/verify-and-schedule-dataflow-preview-mapping-screen.png "Preview mapping screen will look like this")

1. On the left-hand side navigation of the Preview, select the **productListItems** object array. The right-hand side updates to show only the attributes in that object array. 

>[!NOTE]
>
>Notice that **productListItems.currencyCode** and **productListItems.quantity** are automatically populated (even after removing the mappings). This happens because **productListItems** as a parent object are mapped.

![Completed mapping screen for productListItems after removing duplicate overrides](assets/verify-and-schedule-dataflow-completed-mapping-screenshot.png "Completed mapping will look similar to the following screenshot")

## Schedule the run

1. Set the schedule to run **every 15 minutes** by setting the Frequency as Minute and Interval as 15. Review the flow and click Finish. 

>[!CAUTION]
>
>Ensure that your schedule is set to 15 minutes. If you schedule the run as **Run Once**, you cannot run it again even if you make changes to the mapping later.

1. Dataflow execution does not start immediately and takes a few minutes. So, the last Dataflow Run Status is set to “*No runs*”.

1. After a few minutes, the Dataflow succeeds. Notice the **Last Dataflow Run Status** and **Last Dataflow Run Date**. 

1. Click on the Dataflow name to get a list of Dataflow Runs. 10 Records should be ingested.

1. Click on the Dataflow Run Start time to see error diagnostic details.

1. In the Left Nav bar, Go to Datasets in Platform and click on **Orders - YourNameHere**

1. Click on the **Preview Dataset.**
