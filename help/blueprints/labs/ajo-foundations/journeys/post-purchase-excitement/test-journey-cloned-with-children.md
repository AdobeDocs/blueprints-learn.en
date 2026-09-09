---
title: Test Journey (cloned with children)
description: Use Test Mode to trigger a simulated Order Shipped event and review the execution log before publishing the journey.
doc-type: article
solution: Experience Platform
exl-id: 7545158e-015d-4015-a7b9-8e0121eca591
---

# Learning Objective

Use the journey testing tools to verify that the event trigger and journey logic are configured correctly.

## Test the Journey

1. Click on **Journeys **on the left rail and the **Browse tab** if you don't see a list of Journeys
1. Click on your **Journey **to open it
1. Click on **Alerts **& ensure no errors (warnings are ok)

![ZYn2cnZa6 L1 20251113 200640](assets/post-purchase-excitement-3.png)

>[!NOTE]
>
>**What is CJMMAS - 2001-200**
>
>Indicates the opt-out link is missing in an email variant

1. Click on the **Simulate **and on the left side, select **Test Mode**

![WnyV5WyS3iyKIvOILMzRU 20260615 104621](assets/post-purchase-excitement-6.png)



>[!NOTE]
>
>It might take a minute to get ready. During that time the Trigger an Event button will not be available.



1. Click **Trigger an Event **and fill out these properties:
   - **Event Type**: `orders.shipped`
   - **Personal Email**: `henry.creel@emailsim.io`
   - **Order ID**: `123`
1. Click **Send **(note, it takes a few seconds to respond after clicking send)

![SvyzYc4SMYffxKat90AuF 20251113 201239](assets/post-purchase-excitement-1.png)

>[!CAUTION]
>
>Some students get errors and need to send this a few times. You may have to do this **multiple **times.
>
>**Sometimes **the first Send gives an error of:
>
>**Inlet does not exist (Reference id: 3216a850-c40d-11f0-8fa5-73d1522cc9a2)**
>
>If you get an error, Click** Trigger an Event**, then **send **again.  You may have to do this **multiple times**.



1. Under **Results **-> Click **Show Log **on left side

![T83sahcgABemDM7PnACDD 20251113 201517](assets/post-purchase-excitement-2.png)

>[!WARNING]
>
>Some students who received errors sometimes receive different logs showing an empty instances array `{"instances": []}`. This is not a blocker, go ahead and move on to the next step.

You should see something like this in the log:

>[!NOTE]
>
>We are looking for the key fields used: **actionsHistory**, **transitionsHistory**, **eta**, **tracking_number**, **eventType**, **personalEmail**, and **orderID**.

```json
{
  "actionsHistory": {
    "8919055f-1b00-4a43-8bd6-c8af894474b2": {
      "eta": "11/27/2025",
      "tracking_number": "091204404",
      "jo_status_code": "http_200"
    }
  },
  "transitionsHistory": {
    "orderShipped (1158856989)": {
      "eventType": "orders.shipped",
      "_id": "joTestModeEvent_5abbfdcd-561d-45a7-ba42-d0640539831a",
      "_dep": {
        "personalEmail": "henry.creel@emailsim.io"
      },
      "order": {
        "orderID": "123"
      },
      "timestamp": "2025-11-17T23:30:49.576289372Z"
    }
  }
}
```



1. **Close **the Browser **tab**
1. **Close Test Mode** in the top right

![NiqxGZjRWMi7MDiQul5hw 20251117 235338](assets/post-purchase-excitement-4.png)

1. Click on **Publish **the Journey in the top right

![RqfeWFQA4yR0J8CvPxu5o 20251118 001155](assets/post-purchase-excitement-5.png)

1. **Close **the **Journey **by clicking \<- arrow in the top left

![ZxaTyocb4irBpx9COCJRk 20251117 235355](assets/post-purchase-excitement-7.png)

Next we will send a real Order Shipped Event into AEP

## Recap

The journey has passed configuration validation and is ready to receive events
