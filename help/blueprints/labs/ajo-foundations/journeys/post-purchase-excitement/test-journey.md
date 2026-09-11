---
title: Test journey
description: Use the journey Test Mode simulator to trigger an Order Shipped event and confirm the trigger and action logic run correctly before publishing.
doc-type: article
solution: Experience Platform
exl-id: fc3dbfb9-b44b-4866-acc9-398a8b52f2b9
---

# Test journey

## Learning objective

Use the journey testing tools to verify that the event trigger and journey logic are configured correctly.

## Test the journey

1. Click on **Journeys** on the left rail and the **Browse tab** if you don't see a list of Journeys
2. Click on your **Journey** to open it
3. Click on **Alerts** & ensure no errors (warnings are ok)

   ![Alerts panel showing no errors after opening the journey](assets/test-journey-alerts-no-errors.png)

   >[!NOTE]
   >
   >**What is CJMMAS - 2001-200**
   >
   >Indicates the opt-out link is missing in an email variant

4. Click on the **Simulate** and on the left side, select **Test Mode**

   ![Test Mode selected under Simulate on the left side](assets/test-journey-select-test-mode.png)



   >[!NOTE]
   >
   >It might take a minute to get ready. During that time the Trigger an Event button will not be available.



5. Click **Trigger an Event** and fill out these properties:
   - **Event Type**: `orders.shipped`
   - **Personal Email**: `henry.creel@emailsim.io`
   - **Order ID**: `123`
6. Click **Send** (note, it takes a few seconds to respond after clicking send)

   ![Trigger an Event form filled out and Send clicked](assets/test-journey-trigger-event-send.png)

   >[!WARNING]
   >
   >Some students get errors and need to send this a few times. You may have to do this **multiple** times.
   >
   >**Sometimes** the first Send gives an error of:
   >
   >**Inlet does not exist (Reference id: 3216a850-c40d-11f0-8fa5-73d1522cc9a2)**
   >
   >If you get an error, Click **Trigger an Event**, then **send** again.  You may have to do this **multiple times**.



7. Under **Results** -> Click **Show Log** on left side

![Show Log option under Results after triggering the test event](assets/test-journey-show-log-results.png)

>[!NOTE]
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



8. **Close** the Browser **tab**
9. **Close Test Mode** in the top right

   ![Close Test Mode button in the top right](assets/test-journey-close-test-mode.png)

10. Click on **Publish** the Journey in the top right

   ![Publish button for the Journey in the top right](assets/test-journey-publish-journey.png)

11. **Close** the **Journey** by clicking \<- arrow in the top left

![Back arrow in the top left to close the Journey](assets/test-journey-close-journey-back-arrow.png)

Next we will send a real Order Shipped Event into AEP

## Recap

The journey has passed configuration validation and is ready to receive events
