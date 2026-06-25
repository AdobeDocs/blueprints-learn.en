---
hold: true
title: Configure SMS channel
description: Configure SMS channel
doc-type: article

solution: Experience Platform
exl-id: 63c994f2-4b6b-42e9-aa82-cb6697390a08
---

# Objective

In the next step of steps you will configuration the SMS channel.  This is required so that you can send messages to individual line holders later on when you are building your campaign.



## Navigate to Channels

1. In Adobe Journey Optimizer, go to the **Administration** -> **Channels** menu. 
1. Select **SMS Settings** → **API credentials**. 
1. Click **Create API credential**. 

![Image.png "Navigate to SMS Settings"](assets/fwB-OLRsjVgOqJqyXVljM_image.png "Navigate to SMS Settings")



## Define the SMS API Credentials

You will start by creating the API connector that AJO will use to send outbound SMS requests.

1. Under SMS Vendor choose **Twilio**. 
1. Enter the following API credential details from the **Sandbox Assignment.pdf** file that was emailed to you:
   - **Name:**  `DEP SMS`
   - **Account SID: ** `value from the PDF`
   - **Auth Token: ** `value from the PDF`
1. Click **Submit **to register the API credential 

![Enter SMS API credentials](assets/ljA1OrBg5ZaI9RmREw9xL-20260617-131608.png)



## Create **SMS Channel Configuration**

Now you will map this API credential to a channel configuration that journeys and campaigns can use.

1. Navigate to **Channels** → **General Settings** → **Channel configurations**. 

![Navigate to channel configurations](assets/mSyw6M-kEJCaLCtT-UXcQ_image.png)



1. Click **Create channel configuration**. 

![Create a new channel configuration](assets/VnfDtv74S34zxgKaMuyia_image.png)



1. Fill in SMS Channel Configuration Settings with the following values:
   - **Name:**  `Relational-SMS-Multi-Entity`
   - **Channel:**  `Mobile Message`

>[!WARNING]
>
>If you get an error of user does not have permissions ignore it and continue on with your day

**Marketing Action:**  `SMS Targeting`

﻿

## SMS Settings

On selecting Channel as Mobile Message**,** a new section SMS settings shows up. Fill it in with the following details:

- **Mobile message type:**  `Marketing`
- **Mobile message configuration:**  `DEP SMS`
- **Sender number:**  `01234567890`
- **Subdomain:**  `leave blank`
- **Opt-out number:** `leave blank`

![Enter SMS sender number](assets/J07m-KrN2zZb2RrHZho5Y-20260615-121008.png)



## Execution details

1. Under Execution details**, **click the tab** Orchestrated campaign**

![3fXXt mHG8 image](assets/XILfciHQry_3fXXt-mHG8_image.png)



1. Ensure the **Enabled **checkbox is checked

![Enabled orchestrated campaigns](assets/TG_jHc5KWx1011kPc2v01_image.png)



1. Next under the sub-section **Execution dimension** ensure the following are setup as such:
   - **Deliver on message per: ** `Target + Secondary Dimension`
   - **Profile Target Dimension:**  `del-rel: Customer Account - customer_id`
   - **Secondary Dimension:**  `Customer Line`

![Setup the execution dimension](assets/YEvABUpQZTUoJ81l3-rqp_image.png)

![VhWKVxWWS5 image.png "Secondary Dimension"](assets/4Y1rO6942x_vhWKVxWWS5_image.png "Secondary Dimension")

>[!NOTE]
>
>This is telling Orchestrated Campaigns that when it sends messages if should deliver one message per record that that matches to the Profile Target Dimension.



1. Under Execution Address heading ensure you select the radio button for **Secondary Dimension **and then click the edit button on the **SMS Execution Field**

![Choose execution address](assets/qp4NuhR2TC5D3_GpmLsmc_image.png)



1. On the pop-up, click into the schema **dep-rel: Customer Line** and select **Mobile Phone**.

![Image](assets/p0HWpDLI7AADX-fRFV3F1_image.png)

![Image.png "Mobile Phone field"](assets/co6cW9s4IZwdgbKow7jGj_image.png "Mobile Phone field")



1. Confirm the final Execution details section matches below

![Final execution details config](assets/TOxeA4jF7GHha_UMCuyvc-20260115-220814.png)



## Submit & Review

1. You can click the **Submit **button to complete the configuration and should see a success message appear

![Success message](assets/2Rf6ftaYEqVKbv3j2GZAF_image.png)



1. On the channel configurations inventory page ensure the status shows as **Active **before moving on

![Active SMS Channel configuration](assets/NfQ4ePvTsQPyE2mTe0gvc_image.png)

>[!CAUTION]
>
>Wait until the status turns **Active **otherwise future lab steps will fail miserabily for you



1. When the status turns Active you are complete!

>[!TIP]
>
>🚀 Booyah! Your SMS channel is now live and ready for action!



## Recap

You have now seen how to successfully configure a SMS channel.  Note this is an API-based SMS so depending on your provider they may use alternative methods for authentication.

You can read more [here ](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)if you are interested.

