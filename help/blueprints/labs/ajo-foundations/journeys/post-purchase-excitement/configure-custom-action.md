---
title: Configure Custom Action
description: Configure a reusable custom action in Adobe Journey Optimizer that calls a third-party endpoint to retrieve shipping ETA and tracking details.
doc-type: article
solution: Experience Platform
exl-id: f81cc8be-bc2a-43cb-a2d4-89834aa94dcb
---

# Learning Objective

Create a custom action that defines how the journey will communicate with an external endpoint or service to get an ETA for when the package will arrive.

## Navigate to Actions

In the left rail under the  Adminstration menu click to **Configurations **and then on the Actions tile click the **Manage** button

![LmhfabYwizD64PUMaDDRX 20251117 221425](assets/configure-custom-action-8.png)



## Configure the Action

## Action Name & Details

1. In the upper right click on the **Create Action** button

![Create a new action](assets/configure-custom-action-3.png)

1. In the configuration panel that appears update the following basic values as shown below:
   - **Name**: `GetShippingDetails`
   - **Description**: `Call third party to get Shipping ETA and Tracking Number`
   - **Action Type**: `Custom`
   - **Channel**: `Email`
   - **Required marketing Action**: `Email Targeting`

![Ad8 20260121 222336](assets/configure-custom-action-10.png)


## Endpoint Details

In the Endpoint configuration area provide the following details:

- **Endpoint URL**: `https://api.mockaroo.com/api/67077bb0?count=1&key=a0dbce20`
- **Method**: `GET`
- **Headers: ***leave as-is*
- **Query parameters:**
  - **Name**: `orderid`
  - **Type**: `variable`

>[!NOTE]
>
>A variable allows for us to pass in a value during a journey vs having a static value for all journeys

- **Authentication Type**: `No Authentication`

![RZ MD9gDP54DaU3wV2Ffv 20260121 224857](assets/configure-custom-action-11.png)

![X7b2R7jGuU2KoXlb84DVY 20260121 224916](assets/configure-custom-action-7.png)



## Response Payload Details

Now you need to provide a sample payload so the action knows what the response payload should look like.

1. In the Payloads area click on the **Pencil icon** to open the Field configuration screen

![JNPWtISmH68 rVbooJAGN 20251112 191547](assets/configure-custom-action-5.png)

![P9syM UXJbkAx4aRXPgj  20251112 191647](assets/configure-custom-action-9.png)



1. **Copy and paste** the below payload into the Payload box

JSON

```json
{
    "eta": "11/19/2025",
    "tracking_number": "072000326"
}
```

>[!NOTE]
>
>This is the same JSON structure the mockaroo endpoint we use above should return:


1. The response payload will display. Click the **Save **button.

![FSWM 20251112 191815](assets/configure-custom-action-1.png)

>[!NOTE]
>
>You can leave everything as a string but in real-life you would probably want to update this to match the data type



## Test the Action

1. Click the **Send test request **button in the bottom right rail to validate you didn't mess anything up 😀

![Z3Zn defewlUqo O 20251112 192923](assets/configure-custom-action-2.png)



1. Click on the **Query parameters** tab and update the value for `orderId`to **123**

![9HtNxkbpHpG2CVRs6H7xu 20251112 193020](assets/configure-custom-action-4.png)



1. Click the **Send button **and if all works out well you should see a response code of 200 and a Preview of the payload as shown below\...

![WYsxnbwpkIVug1YHoEWBP 20260121 230625](assets/configure-custom-action-6.png)

Preview

```json
{
  "eta": string "12/26/2025",
  "tracking_number": string "063112249"
}
```

>[!WARNING]
>
>If you are not seeing a 200 response or a Preview do not continue. Raise your ✋to get some help.



1. Click the **Cancel **button to go back to the Action screen and then scroll back up in top right rail and click the **Save **button

>[!TIP]
>
>Congrats! Your Custom Action is live, thanks to your expert-level Ctrl+C, Ctrl+V skills.

## Recap

A reusable custom action configured in Adobe Journey Optimizer that takes an Order Id and returns the ETA and Tracking Number
