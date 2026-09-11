---
hold: true
title: Creating the email
description: Learn how to apply a branded content template to a campaign email in Adobe Journey Optimizer and replace hero and product images.
doc-type: article
solution: Experience Platform
exl-id: bf823714-7298-48fc-a18b-9bf2462ae52e
---

# Creating the email

## Content creation with templates

**Purpose:** Learn how to create reusable templates in Adobe Journey Optimizer, then apply them inside a real email within a campaign.

## Learning objectives

By the end of this module, you will be able to:

1. Create a new campaign and use your new branded template.
1. Update hero images, product images, buttons, and layout styling.

## Create and update the email in a campaign

### Objective

In this exercise, we will learn how to apply the template you created to an email within a journey. In an ideal scenario, you can use any existing journey or campaign and replace its email content with a standardized template to ensure brand consistency and faster execution.

This step demonstrates how templates can be reused across journeys, allowing teams to update designs without rebuilding emails from scratch.

## Create new email campaign

1. Go back to the main screen and click on **Journeys Management → Campaigns**.
2. Click on **Create Campaign** 

![Create Campaign button in Journeys Management](assets/creating-the-email-click-create-campaign-button.png)

3. Select "**Orchestration - Marketing**" and click **confirm**

![Selecting Orchestration - Marketing and clicking confirm](assets/creating-the-email-select-orchestration-marketing.png)

4. Name your campaign `Flagship Phone Launch Branded`. Press **Save** button. 

![Naming the campaign Flagship Phone Launch Branded and clicking Save](assets/creating-the-email-name-campaign-save.png)

5. Click on the **+ sign** and select **Read Audience** activity 

![Plus sign to select the Read Audience activity](assets/creating-the-email-click-plus-read-audience.png)

6. The next step is to select **"Read Audience"** box and click on **Audience folder icon**

![Read Audience box and Audience folder icon](assets/creating-the-email-read-audience-folder-icon.png)

7. Select the **dep: Interested in iPhone 17** audience and click "**Add Audience**" button

![Selecting the Interested in iPhone 17 audience and clicking Add Audience](assets/creating-the-email-select-audience-add-button.png)

8. Select Entity - **dep-rel: Customer Account - customer\_id** (or any as it does not matter for this part)
9. Add the **Email activity** by clicking **+ sign** and then select **Email** from Channel activities. 

![Adding the Email activity from Channel activities](assets/creating-the-email-add-email-channel-activity.png)

10. Click on **Edit email**. 

![Edit email option for the campaign email activity](assets/creating-the-email-click-edit-email.png)

11. Click on the **Action tab** and select **your** email configuration. Your sandbox may show this as Relational Email. (Select any)

![Action tab with the email configuration selected](assets/creating-the-email-action-tab-email-configuration.png)

12. Click on **Content tab**

![Content tab in the email editor](assets/creating-the-email-click-content-tab.png)

13. Click on **Apply Content Template**

![Apply Content Template option in the email editor](assets/creating-the-email-click-apply-content-template.png)

14. Select the template **"Promotional Template"** you created and click **Confirm**

![Selecting the Promotional Template and clicking Confirm](assets/creating-the-email-select-promotional-template-confirm.png)

15. Click on **Edit email body**

![Edit email body option after applying the template](assets/creating-the-email-click-edit-email-body.png)

16. Confirm the new header, hero, footer, and content blocks appear correctly.

![Header, hero, footer, and content blocks appearing correctly in the email](assets/creating-the-email-header-hero-footer-blocks-confirmed.png)


## Replace hero image & product images

Change the hero and phone images. You need to upload content to assets from the toolkit folder. Currently your product hero banner image is a placeholder.

1. Click the broken hero banner image.

![Clicking the placeholder hero banner image](assets/creating-the-email-click-broken-hero-banner-image.png)

2. Remove the temporary source URL.

![Removing the temporary source URL from the image](assets/creating-the-email-remove-temporary-source-url.png)

3. Click on **Import Media**

![Import Media button for the hero image](assets/creating-the-email-click-import-media.png)

4. Upload `hero.png` from your toolkit. (You can drag the file)

![Uploading hero.png from the toolkit folder](assets/creating-the-email-upload-hero-png-file.png)

5. Click **Next,** Select **your folder for assets** and press **import**

![Selecting the assets folder and clicking import for the hero image](assets/creating-the-email-select-folder-import-hero.png)

6. Your email template is coming up nicely. It appears like the following. Click on **"Save"** to save your work. 

![Updated email template with the new hero image before saving](assets/creating-the-email-save-updated-email-template.png)


## Optional exercise

### Replace product images

Go ahead and update all the product images (images provided in the toolkit folder) and also add rounded border to your liking. Your email looks nicer without any broken links, as shown below. Repeat the process for all product cards.

![Email with all product images updated and no broken links](assets/creating-the-email-product-images-updated-no-broken-links.png)

## Recap

In this module, you successfully:

- Created a new campaign with email using your branded template
- Updated hero and product images
- Enhanced styling 

You are now ready to move on to the next module - **AI assistant and content personalization**, where you will use AI to refine text and generate images automatically.
