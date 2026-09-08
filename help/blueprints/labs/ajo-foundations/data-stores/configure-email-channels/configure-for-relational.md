---
title: Configure for Relational
description: Learn how to configure an email channel using the email attribute from a Relational schema for Orchestrated Campaigns only.
doc-type: article
solution: Experience Platform
exl-id: 6f299942-79a6-42c2-8a5b-dd4bccd6aad4
---

# Objective

In the next set of steps you will create an Email Channel Configuration with **only** the Orchestrated Campaigns using the `email` attribute from the  Relational schema `dep-rel: Customer Account` 

## Create Channel Configuration

1. Navigate to **Channel Configurations** found under the menu **Administration → Channels → General settings**
1. Click the **Create configuration **button

![Create Channel configuration](assets/configure-email-channels-4.png)

1. In the Create wizard set the following values:
   - **Name:**  `Relational-Email`
   - **Channel:**  `Email`
   - **Marketing action:**  `Email Targeting`

![Channel configuration details](assets/configure-for-relational-3.png)

>[!NOTE]
>
>On selecting Email as the channel, a new section Email settings shows up.





## Configure Email Type

Set the **Email Type** to **Marketing**

![Email settings](assets/configure-email-channels-5.png)

## **Configure Subdomain**

From the **Subdomain** dropdown, select **email.dep-labs.com**

![6cp vSlyDtLAXOUO image.png "Configure Subdomain"](assets/AdZp_6cp-vSlyDtLAXOUO_image.png "Configure Subdomain")

## Configure IP pool details

From the **IP pool** dropdown, select **marketing**

![OBQizW0WK3qX image.png "Configure IP pool details"](assets/1epXqlBD_OBQizW0WK3qX_image.png "Configure IP pool details")

## Configure List unsubscribe

1. Ensure that the toggle is **enabled** for list-unsubscribe
1. Under the List unsubscribe preference area make sure all the checkboxes are **checked**
1. Under Link management make sure **Adobe managed** is selected
1. For the Consent level make sure this is set to **Channel**

![Configure List unsubscribe](assets/configure-email-channels-1.png)

## Configure Header Parameters

1. Set the the following fields as follows:
   - **From name:**  `DEP Labs`
   - **From email prefix:  **`dep`
   - **Reply to name:  **`DEP Labs Support`
   - **Reply to email:  **`reply@email.dep-labs.com`
   - **Error email prefix:**  `error`

![Header parameters](assets/configure-email-channels-3.png)

## Configure Bcc Email

Leave this blank

>[!NOTE]
>
>You can keep a copy of sent emails by sending them to a BCC inbox. Enter the email address of your choice so that every email sent is blind-copied to this BCC address. Note that the BCC address domain must be different from any subdomain delegated to Adobe. This feature is optional. *How to use BCC for emails*

## Configure Email retry parameters

Leave with the default settings of **Hours **set to **84 **

## Configure URL tracking parameters

Leave with the default settings

## **Execution Details**

1. In the Orchestrated campaign tab and **check **the Enabled checkbox.

![Configure Orchestrated campaign](assets/configure-email-channels-2.png)

1. Under Execution dimension configure the following:
   - **Deliver one message per:**  `Target Dimension `
   - **Profile Target Dimension:  **`dep-rel: Customer Account - customer_id`

![Execution dimension](assets/configure-for-relational-1.png)

1. Under Execution Address configure the following:
   - **Source:** `Target Dimention`
   - **Delivery Address:**  `click on the Edit button`

![Target Dimension](assets/configure-for-relational-6.png)

1. In the pop-up, click into the folder **dep-rel: Customer Account**

![Configure Delivery address](assets/configure-for-relational-5.png)

1. Select **Email** and click on the **Select **button

![Email as Delivery address](assets/configure-for-relational-2.png)

1. When done your final Exectuion details should look like the below screenshot

![Execution dimension configured](assets/configure-for-relational-4.png)

>[!NOTE]
>
>For Orchestrated Campaigns you will be targeting the customer account with an email so you only need to send one message per Target Dimension.  The Execution address you will use will come from the Target Dimension itself (i.e. what is stored in the **dep-rel: Customer Account **table for **email** address)


## **Review & Save**

1. Review all details again to ensure they match. 
1. Scroll up and click **Submit**.
1. When you are done you should see two email channel configurations, both likely in a "processing" state.

>[!WARNING]
>
>The processing of the Email channel configuration has been observed to take up to 2hrs! 

## Recap

You have now seen how to create an Email Channel Configuration to use the Relational schema attribute for Orchestrated Campaigns.
