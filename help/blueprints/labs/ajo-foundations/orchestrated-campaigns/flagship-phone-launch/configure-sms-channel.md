---
title: Configure SMS channel
description: Learn how to configure a Twilio-based SMS channel and its execution dimensions for use in Orchestrated Campaigns.
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
1. Enter the following API credential details, using your own [Twilio trial account](https://www.twilio.com/try-twilio):
   - **Name:**  `DEP SMS`
   - **Account SID:**  Found on your Twilio Console dashboard
   - **Auth Token:**  Found on your Twilio Console dashboard (click **View** to reveal it)
1. Click **Submit** to register the API credential 

>[!NOTE]
>
>You'll need a free Twilio trial account with a verified phone number before starting this step. Sign up at [twilio.com/try-twilio](https://www.twilio.com/try-twilio), then find your Account SID and Auth Token on the Twilio Console dashboard.

![Enter SMS API credentials](assets/configure-sms-channel-8.png)



## Create **SMS Channel Configuration**

Now you will map this API credential to a channel configuration that journeys and campaigns can use.

1. Navigate to **Channels** → **General Settings** → **Channel configurations**. 

![Navigate to channel configurations](assets/configure-sms-channel-9.png)



2. Click **Create channel configuration**. 

![Create a new channel configuration](assets/configure-sms-channel-5.png)



3. Fill in SMS Channel Configuration Settings with the following values:
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

![Enter SMS sender number](assets/configure-sms-channel-2.png)



## Execution details

1. Under Execution details**,** click the tab **Orchestrated campaign**

![3fXXt mHG8 image](assets/configure-sms-channel-6.png)



2. Ensure the **Enabled** checkbox is checked

![Enabled orchestrated campaigns](assets/configure-sms-channel-4.png)



3. Next under the sub-section **Execution dimension** ensure the following are setup as such:
   - **Deliver on message per:** `Target + Secondary Dimension`
   - **Profile Target Dimension:**  `del-rel: Customer Account - customer_id`
   - **Secondary Dimension:**  `Customer Line`

![Setup the execution dimension](assets/configure-sms-channel-7.png)

![VhWKVxWWS5 image.png "Secondary Dimension"](assets/4Y1rO6942x_vhWKVxWWS5_image.png "Secondary Dimension")

>[!NOTE]
>
>This is telling Orchestrated Campaigns that when it sends messages if should deliver one message per record that that matches to the Profile Target Dimension.



4. Under Execution Address heading ensure you select the radio button for **Secondary Dimension** and then click the edit button on the **SMS Execution Field**

![Choose execution address](assets/configure-sms-channel-11.png)



5. On the pop-up, click into the schema **dep-rel: Customer Line** and select **Mobile Phone**.

![Image](assets/configure-sms-channel-10.png)

![Image.png "Mobile Phone field"](assets/co6cW9s4IZwdgbKow7jGj_image.png "Mobile Phone field")



6. Confirm the final Execution details section matches below

![Final execution details config](assets/flagship-phone-launch-1.png)



## Submit & Review

1. You can click the **Submit** button to complete the configuration and should see a success message appear

![Success message](assets/configure-sms-channel-1.png)



2. On the channel configurations inventory page ensure the status shows as **Active** before moving on

![Active SMS Channel configuration](assets/configure-sms-channel-3.png)

>[!CAUTION]
>
>Wait until the status turns **Active** otherwise future lab steps will fail miserabily for you



3. When the status turns Active you are complete!

>[!TIP]
>
>🚀 Booyah! Your SMS channel is now live and ready for action!



## Recap

You have now seen how to successfully configure a SMS channel.  Note this is an API-based SMS so depending on your provider they may use alternative methods for authentication.

You can read more [here ](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)if you are interested.
