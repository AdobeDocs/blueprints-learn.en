---
title: Configure for Profile
description: Configure for Profile
doc-type: article
exl-id: bb85e0aa-554e-4527-bf91-e7fd4f69ce71
---

# Objective

In the next set of steps you will create an Email Channel Configuration with both Journeys and Orchestrated Campaigns using the `personalEmail.address`AEP Profile attribute 

# Create Channel Configuration

1. Navigate to **Channel Configurations** found under the menu **Administration → Channels → General settings**
2. Click the **Create configuration **button

![Create channel configuration](assets/gOlMQhTEv_TkHLsoWJTKn_image.png)

3. In the Create wizard set the following values:
   - **Name:**  `Profile-Email`
   - **Channel:**  `Email`
   - **Marketing action:**  `Email Targeting`

![Channel configuration details](assets/NJlQ6SuJoNSZbJdura7r7-20251217-194516.png)

**Note**: On selecting Email as the channel, a new section** Email settings **shows up. 

## Configure Email Type

Set the **Email Type** to **Marketing**

![Email Type](assets/wTReTT5V3d8r4JJAx6Pvi_image.png)

## Configure **Subdomain**

From the **Subdomain** dropdown, select **email.dep-labs.com**

![](assets/AdZp_6cp-vSlyDtLAXOUO_image.png "Configure Subdomain")

## Configure IP pool details

From the **IP pool** dropdown, select **marketing**

![](assets/1epXqlBD_OBQizW0WK3qX_image.png "IP pool details")

## Configure List unsubscribe

1. Ensure that the toggle is **enabled** for list-unsubscribe
2. Under the List unsubscribe preference area make sure all the checkboxes are **checked**
3. Under Link management make sure **Adobe managed** is selected
4. For the Consent level make sure this is set to **Channel**

![Config List unsubscribe](assets/4ykrp4kvCRbGdKFo6fgCH_image.png)

## Configure Header Parameters

1. Set the the following fields as follows:
   - **From name:**  `DEP Labs`
   - **From email prefix:  **`dep`
   - **Reply to name:  **`DEP Labs Support`
   - **Reply to email:  **`reply@email.dep-labs.com`
   - **Error email prefix:**  `error`

![Header parameters](assets/aFxboSmGAbW0LWsY15tA__image.png)

## Configure Bcc Email

Leave this blank

>[!NOTE]
>You can keep a copy of sent emails by sending them to a BCC inbox. Enter the email address of your choice so that every email sent is blind-copied to this BCC address. Note that the BCC address domain must be different from any subdomain delegated to Adobe. This feature is optional. *How to use BCC for emails*

## Configure Email retry parameters

Leave with the default settings of **Hours **set to **84 **

## Configure URL tracking parameters

Leave with the default settings

## **Execution Details**

1. Complete the **Execution details** section. Under **Journey and Action **tab**-> Execution dimension,** select **Profile** as **Source** and click on the Edit icon for **Delivery address** under the **Execution Address **section

![Execution details](assets/MTF4kjyNtSUsjun9Ods9n_image.png)

2. Click on the folder titled **Personal Email** to open it up

![Delivery address](assets/1P-z1N1agX9X0zQOOhu4I_image.png)

3. Click the **checkbox** on the `Address` field then click the **Select **button

![Personal Email as Delivery address](assets/Rcstf9YUtEkdYB661p2_7_image.png)

4. For **Profile**, the `personalEmail.address` is now configured as the **Delivery address** under **Execution Address **section

![Delivery address configured](assets/G5QetLEOEPIQY-17aijOD_image.png)

5. Click on the Orchestrated campaign tab and **check **the Enabled checkbox.

![Orchestrated campaign configuration](assets/TG_jHc5KWx1011kPc2v01_image.png)

6. Under the Execution dimension heading configure the following:
   - **Deliver one message per:**  `Target Dimension`
   - **Profile Target Dimension:**  `dep-rel: Customer Account - customer_id`

![Target Dimension](assets/AmX8YqAtJniWBNbi2uM3w_image.png)

7. Under Execution Address configure the following:
   - **Source:  **`Profile`
   - **Delivery address: **` click on the Edit icon`

![Execution Address](assets/EuPuL6bwCPimejEHOxKtn_image.png)

8. Search for and click on the `Personal Email` folder to open it

![Personal Email Profile attribute](assets/3KlS_nunXwoildC2VvBhC_image.png)

9. Select the `Address` field within the Personal Email folder and click on **Select**

![Personal Email as Delivery address](assets/FZFAjwJRH_Fon8IPRZaw5_image.png)

10. For **Orchestrated campaign**, the **dep-rel: Customer Account - customer\_id** is configured as **Profile** **Target Dimension **for **Execution Dimension** with **Execution Address** having a **Source** of **Profile** and `personalEmail.address` as **Delivery address**

![Execution dimension configured](assets/jYRaYhtrLcr5TqFJt39TR-20251217-200156.png)

>[!NOTE]
>For Orchestrated Campaigns you will be targeting the customer account with an email so you only need to send *one message per Profile*.  The Execution address you will use will come from the Profile itself (i.e. what is stored in AEP Profile under the **personalEmail.address** attribute)

****

# **Review & Save**

1. Review all details again to ensure they match. 
2. Scroll up and click on **Submit**. 

>[!WARNING]
>The processing of the Email channel configuration has been observed to take up to 2hrs!  Yikes! 
>
>Continue on to the next exercise while you wait for this channel configuration to process.

>[!TIP]
>🚀 Once the Email channel configuration status is **Active**, it is ready and can now be selected directly inside **Email activities** within Orchestrated Campaigns.

# Recap

You have now seen how to create an Email Channel Configuration to use the AEP Profile attribute for both Journeys and Orchestrated Campaigns.

