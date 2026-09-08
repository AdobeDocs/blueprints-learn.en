---
hold: true
title: Creating the Email
description: Creating the Email
doc-type: article

solution: Experience Platform
exl-id: bf823714-7298-48fc-a18b-9bf2462ae52e
---

## Content creation with Templates

**Purpose:** Learn how to create reusable templates in Adobe Journey Optimizer, then apply them inside a real email within a campaign.

## Learning Objectives

By the end of this module, you will be able to:

1. Create a new campaign and use your new branded template.
1. Update hero images, product images, buttons, and layout styling.

## Create and Update the Email in a Campaign

### Objective

In this exercise, we will learn how to apply the template you created to an email within a journey. In an ideal scenario, you can use any existing journey or campaign and replace its email content with a standardized template to ensure brand consistency and faster execution.

This step demonstrates how templates can be reused across journeys, allowing teams to update designs without rebuilding emails from scratch.

## Create new email campaign

1. Go back to the main screen and click on **Journeys Management → Campaigns**.
1. Click on **Create Campaign** 

![Image](assets/creating-the-email-17.png)

1. Select "**Orchestration - Marketing**" and click **confirm**

![Image](assets/creating-the-email-9.png)

1.  Name your campaign `Flagship Phone Launch Branded`. Press **Save **button. 

![Image](assets/creating-the-email-13.png)

1. Click on the **+ sign** and select **Read Audience** activity 

![Image](assets/creating-the-email-5.png)

1. The next step is to select **"Read Audience"** box and click on **Audience folder icon **

![Image](assets/creating-the-email-4.png)

1. Select the **dep: Interested in iPhone 17** audience and click "**Add Audience**" button

![Image](assets/creating-the-email-19.png)

1. Select Entity - **dep-rel: Customer Account - customer\_id **(or any as it does not matter for this part)
1. Add the **Email activity** by clicking **+ sign** and then select **Email **from Channel activities. 

![Image](assets/creating-the-email-1.png)

1. Click on **Edit email**. 

![Image](assets/creating-the-email-21.png)

1. Click on the **Action tab** and and select the **your** email configuration. In my sandbox it is Relational Email. (Select Any)

![Image](assets/creating-the-email-3.png)

1. Click on **Content tab**

![DlVWDsaNj6hrqydpH image](assets/creating-the-email-12.png)

1. Click on **Apply Content Template**

![Image](assets/creating-the-email-15.png)

1. Select the template **"Promotional Template" **you created and click **Confirm**

![Image](assets/creating-the-email-16.png)

1. Click on **Edit email body**

![Image](assets/creating-the-email-14.png)

1. Confirm the new header, hero, footer, and content blocks appear correctly.

![SWGIHO image](assets/creating-the-email-20.png)


## Replace Hero Image & Product Images

Let us change hero and phone images. You will need to upload content to assets from the toolkit folder. Currently your product hero banner image is a placeholder.

1. Click the broken hero banner image.

![Image](assets/creating-the-email-8.png)

1. Remove the temporary source URL.

![Image](assets/creating-the-email-7.png)

1. Click on **Import Media **

![Image](assets/creating-the-email-18.png)

1. Upload `hero.png` from your toolkit. (You can drag the file)

![LHDJECCXMpCBrEl70f image](assets/creating-the-email-10.png)

5 Click **Next, **Select **your folder for assets** and press **import**

![Image](assets/creating-the-email-11.png)

1. Your email template is coming up nicely. It should appear like below. Click on **"Save"** to save your work. 

![Image](assets/creating-the-email-2.png)


## Optional Exercise

### Replace Product Images

Go ahead and update all the product images (images provided in the toolkit folder) and also add rounded border to your liking. Your email should look nicer without any broken links as shown below. Repeat the process for all product cards.

![PjNjeRIGKkQTkSSYso image](assets/creating-the-email-6.png)

# Recap

In this module, you successfully:

- Created a new campaign with email using your branded template
- Updated hero and product images
- Enhanced styling 

You are now ready to move on to next module - ** AI Assistant & Content Personalisation**, where you will use AI to refine text and generate images automatically.
