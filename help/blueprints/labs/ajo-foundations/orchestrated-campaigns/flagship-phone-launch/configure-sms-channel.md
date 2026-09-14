---
title: Configure SMS channel
description: Learn how to configure a Twilio-based SMS channel and its execution dimensions for use in Orchestrated Campaigns.
doc-type: article
solution: Experience Platform
exl-id: 63c994f2-4b6b-42e9-aa82-cb6697390a08
---

# Configure SMS channel

## Objective

In the next set of steps you will configure the SMS channel. This is required so that you can send messages to individual line holders later on when you are building your campaign.



## Navigate to channels

1. In Adobe Journey Optimizer, go to the **Administration** -> **Channels** menu. 
1. Select **SMS Settings** → **API credentials**. 
1. Click **Create API credential**. 

![Navigate to SMS Settings and API credentials in the Administration Channels menu "Navigate to SMS Settings"](assets/configure-sms-channel-navigate-to-sms-settings.png "Navigate to SMS Settings")



## Define the SMS API credentials

You will start by creating the API connector that AJO will use to send outbound SMS requests.

1. Under SMS Vendor choose **Twilio**. 
1. Enter the following API credential details, using your own [Twilio trial account](https://www.twilio.com/try-twilio):
   - **Name:**  `DEP SMS`
   - **Account SID:**  Found on your Twilio Console dashboard
   - **Auth Token:**  Found on your Twilio Console dashboard (click **View** to reveal it)
1. Click **Submit** to register the API credential 

>[!NOTE]
>
>You'll need a free Twilio trial account with a verified phone number before starting this step. Sign up at [twilio.com/try-twilio](https://www.twilio.com/try-twilio), then find your Account SID and Auth Token on the Twilio Console dashboard. See Twilio's [getting started guide](https://www.twilio.com/docs/usage/tutorials/how-to-use-your-free-trial-account) for a full walkthrough.

![SMS API credential fields for the Twilio vendor](assets/configure-sms-channel-enter-api-credentials.png)



## Create SMS channel configuration

Now you will map this API credential to a channel configuration that journeys and campaigns can use.

1. Navigate to **Channels** → **General Settings** → **Channel configurations**. 

   ![Navigate to Channel configurations under General Settings](assets/configure-sms-channel-navigate-channel-configurations.png)



2. Click **Create channel configuration**. 

   ![Create channel configuration button](assets/configure-sms-channel-click-create-configuration.png)



3. Fill in SMS Channel Configuration Settings with the following values:
   - **Name:**  `Relational-SMS-Multi-Entity`
   - **Channel:**  `Mobile Message`
   - **Marketing Action:**  `SMS Targeting`

>[!NOTE]
>
>If you get an error stating the user does not have permission, ignore it and continue.

## SMS settings

On selecting Channel as Mobile Message, a new section called SMS settings shows up. Fill it in with the following details:

- **Mobile message type:**  `Marketing`
- **Mobile message configuration:**  `DEP SMS`
- **Sender number:**  `01234567890`
- **Subdomain:**  `leave blank`
- **Opt-out number:** `leave blank`

![SMS settings with sender number and mobile message type](assets/configure-sms-channel-sms-settings-fields.png)



## Execution details

1. Under Execution details, click the tab **Orchestrated campaign**

   ![Orchestrated campaign tab under Execution details](assets/configure-sms-channel-execution-details-tab.png)



2. Ensure the **Enabled** checkbox is checked

   ![Enabled checkbox checked for orchestrated campaigns](assets/configure-sms-channel-enabled-checkbox.png)



3. Next under the sub-section **Execution dimension** ensure the following are set up as follows:
   - **Deliver on message per:** `Target + Secondary Dimension`
   - **Profile Target Dimension:**  `dep-rel: Customer Account - customer_id`
   - **Secondary Dimension:**  `Customer Line`

   ![Execution dimension settings with target and secondary dimension](assets/configure-sms-channel-execution-dimension-setup.png)

   ![Secondary Dimension set to Customer Line in execution dimension settings "Secondary Dimension"](assets/configure-sms-channel-secondary-dimension-detail.png "Secondary Dimension")

   >[!NOTE]
   >
   >This is telling Orchestrated Campaigns that when it sends messages, it should deliver one message per record that matches to the Profile Target Dimension.



4. Under Execution Address heading ensure you select the radio button for **Secondary Dimension** and then click the edit button on the **SMS Execution Field**

   ![Execution address set to Secondary Dimension with edit field](assets/configure-sms-channel-execution-address-selection.png)



5. On the pop-up, click into the schema **dep-rel: Customer Line** and select **Mobile Phone**.

   ![Schema pop-up for the dep-rel: Customer Line schema](assets/configure-sms-channel-customer-line-schema-popup.png)

   ![Mobile Phone field selected from the dep-rel: Customer Line schema "Mobile Phone field"](assets/configure-sms-channel-mobile-phone-field-selected.png "Mobile Phone field")



6. Confirm the final Execution details section matches below

![Final execution details configuration matching required settings](assets/configure-sms-channel-final-execution-details.png)



## Submit and review

1. You can click the **Submit** button to complete the configuration and see a success message appear

   ![Success message after submitting the channel configuration](assets/configure-sms-channel-submit-success-message.png)



2. On the channel configurations inventory page ensure the status shows as **Active** before moving on

   ![Channel configuration status shown as Active](assets/configure-sms-channel-active-status.png)

   >[!CAUTION]
   >
   >Wait until the status turns **Active** otherwise future lab steps will fail miserably for you



3. When the status turns Active you are complete!

>[!TIP]
>
>🚀 Booyah! Your SMS channel is now live and ready for action!



## Recap

You have now seen how to successfully configure an SMS channel.  Note this is an API-based SMS so depending on your provider they may use alternative methods for authentication.

You can read more [here ](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration) if you are interested.
