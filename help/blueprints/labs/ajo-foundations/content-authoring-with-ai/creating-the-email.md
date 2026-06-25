---
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

![Image](assets/kk2TuBzGuFAS3lwKh4-Un_image.png)

1. Select "**Orchestration - Marketing**" and click **confirm**

![Image](assets/Mcg71pvrOBXUjL4YENwm4_image.png)

1.  Name your campaign `Flagship Phone Launch Branded`. Press **Save **button. 

![Image](assets/ZXSgkflj4pKWLUv1DMgFp_image.png)

1. Click on the **+ sign** and select **Read Audience** activity 

![Image](assets/BhsQnkqcipdu83MLhrlOv_image.png)

1. The next step is to select **"Read Audience"** box and click on **Audience folder icon **

![Image](assets/AE-xvn4jiBHSJsXZ3Pi-h_image.png)

1. Select the **dep: Interested in iPhone 17** audience and click "**Add Audience**" button

![Image](assets/qHvhjsncSg5V3KgmdmBdr_image.png)

1. Select Entity - **dep-rel: Customer Account - customer\_id **(or any as it does not matter for this part)
1. Add the **Email activity** by clicking **+ sign** and then select **Email **from Channel activities. 

![Image](assets/-J734-OW9Lir4r4qkNoKH_image.png)

1. Click on **Edit email**. 

![Image](assets/tMOX6OvutNQ--fWeCAUL2_image.png)

1. Click on the **Action tab** and and select the **your** email configuration. In my sandbox it is Relational Email. (Select Any)

![Image](assets/7xYmI03Li-V94VGqi5e5D_image.png)

1. Click on **Content tab**

![DlVWDsaNj6hrqydpH image](assets/UUB_DlVWDsaNj6hrqydpH_image.png)

1. Click on **Apply Content Template**

![Image](assets/iAlo2gfVFl6lTyipTJ4Nk_image.png)

1. Select the template **"Promotional Template" **you created and click **Confirm**

![Image](assets/kFmT75dlj3EaxYvr4k4h9_image.png)

1. Click on **Edit email body**

![Image](assets/denRDGgrcxwflb3Se3gOw_image.png)

1. Confirm the new header, hero, footer, and content blocks appear correctly.

![SWGIHO image](assets/qKEH7zQGVztL7a_SWGIHO_image.png)


## Replace Hero Image & Product Images

Let us change hero and phone images. You will need to upload content to assets from the toolkit folder. Currently your product hero banner image is a placeholder.

1. Click the broken hero banner image.

![Image](assets/LjvBA7pqgk18-aiQ9feJR_image.png)

1. Remove the temporary source URL.

![Image](assets/LOaT2TvvinvQpKFdcomCW_image.png)

1. Click on **Import Media **

![Image](assets/l5yajXzUbJhS5gVqG3qQC_image.png)

1. Upload `hero.png` from your toolkit. (You can drag the file)

![LHDJECCXMpCBrEl70f image](assets/P3_LHDJECCXMpCBrEl70f_image.png)

5 Click **Next, **Select **your folder for assets** and press **import**

![Image](assets/S5D6K4KijF8FcXQZ89ppT_image.png)

1. Your email template is coming up nicely. It should appear like below. Click on **"Save"** to save your work. 

![Image](assets/4A-HEsJ4z1Ca3cSnvSACl_image.png)


## Optional Exercise

### Replace Product Images

Go ahead and update all the product images (images provided in the toolkit folder) and also add rounded border to your liking. Your email should look nicer without any broken links as shown below. Repeat the process for all product cards.

![PjNjeRIGKkQTkSSYso image](assets/Gu_PjNjeRIGKkQTkSSYso_image.png)

# Recap

In this module, you successfully:

- Created a new campaign with email using your branded template
- Updated hero and product images
- Enhanced styling 

You are now ready to move on to next module - ** AI Assistant & Content Personalisation**, where you will use AI to refine text and generate images automatically.
