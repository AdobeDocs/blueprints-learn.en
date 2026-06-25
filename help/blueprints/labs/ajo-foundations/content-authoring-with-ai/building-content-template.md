---
title: Building Content Template
description: Building Content Template
doc-type: article
exl-id: e73f06b1-be8a-4096-949c-900db13db9f8
---

# Content creation with Templates & Fragments

**Purpose:** Learn how to create reusable templates in Adobe Journey Optimizer

## Learning Objectives

By the end of this module, you will be able to:

1. Build a full email template using imported HTML and fragments.

## Why Templates matter

Templates allow you to create consistent, brand‑aligned content that can be reused across emails, campaigns, and journeys.

### Templates

Blueprints that structure:

- Header placement
- Body content area
- Footer area
- Standard layout styling

Templates ensure brand consistency across teams and save significant creation time.

***

# Create a New Template Using Fragments

Templates help users reuse full layouts across campaigns. Content templates in Adobe Journey Optimizer are powerful tools designed to simplify and streamline the way you create reusable content for campaigns and journeys. Whether you’re crafting an email, SMS, or push notification, templates help you save time by providing pre-designed structures that can be easily customized and shared across projects.

For an accelerated and improved design process, create standalone templates to reuse custom content easily across Journey Optimizer campaigns and journeys.

This functionality allows content-oriented users to work on templates outside campaigns or journeys. Marketing users can then reuse and adapt these standalone content templates inside their own journeys or campaigns.

## Create Template

1. Go to **Content Management → Content Templates**.

![](assets/atNZ_8GT_AZjDP0Ab4bIU_image.png)

2. Click **Create Template **and then fill in the following:
   - **Name:** `Promotional Template`
   - **Description:** `Promotional Template for phone products`
   - **Channel:** `Email`

![](assets/v-iJh6PTBmOZRPeNyA8wz_image.png)

3. Click **Create**.

![](assets/HLnaL6U1vD8YC79dC_Gwy_image.png)

***

## Add Subject Line & Open Email Designer

1. Add subject line: `Promotional Template` and click **on the email body **to open it to edit

![](assets/LURFvHgaheokhQz-AMiEO_image.png)

2. You will see three options: 
   1. Desing from scratch
   2. Code your own
   3. Import HTML

We will select third option. Click **Import HTML**



![](assets/mTFvCmtsQNxQc3ggKjPQi_image.png)

## Import Provided HTML Template



1. Upload the template html file from the toolkit folder `promotional-template-final.html`

![](assets/AZoo-_cVvhKbyJUh41nbw_image.png)

2. Click on Import button to **import** the template. 

![](assets/OkPv3NEY69JNRND8Z7naG_image.png)

3. Wait for the layout to render. You will notice issues like broken image links and missing branding. (This is expected behavour as we have placeholder assets)

![](assets/7dk1wjfsvm0YwSgJxVVHR_image.png)

***

## Explore Template Structure

### Left Panel

The "**Structures**" and "**Contents**" components in Adobe Journey Optimizer (AJO) are essential elements used when designing emails, landing pages, and content fragments. Structures define the layout framework, while Contents provide the actual building blocks placed inside those layouts.

The body section in Adobe Journey Optimizer is the main container for your email or page content. It serves as the root of the visual design space, where all structure components (columns, layouts) and content components (text, images, buttons, etc.) are nested.

### Right Panel

The "**Settings**" and "**Style**" options under the body section in Adobe Journey Optimizer allow you to define the foundational look and layout of your email or page. These controls affect the entire design since the body is the parent of all components.

![](assets/zNpHmfgdwjdWrp3WjKqBJ_image.png)

***

On your left hand rail bar you will find sections for: 

- Fragments
- Files
- Body structure 
- Tracked URLs

You should be able to see the header fragement that we created in previous execrise should appear here as shown below. Make sure your header fragment should show they are live with blue dot and not in a draft mode. Spend time checking rest of the sections. 

![](assets/9kueBJier0TTuJua-RRZD_image.png)

>[!WARNING]
>If you do not see your fragment here it means that you did not save it properly and will need to re-upload it.



## Insert Header Fragments

Let us now improve the template. We have already created header and footer. 

1. Drag a **1:1 Column** above the existing content.

![](assets/Xg1_DBVTti7na-JBDJxdD_image.png)

You should see something like this. 

![](assets/xjoYMqCikDiEVclNMqonz_image.png)

2. Your background will use template background color which is black currently. Set its **background colour to white. Click **in the Style tab on the right rail and use white colour from the colour picker. 

![](assets/v2ki1nxHt4wXaD3g8LIu9_image.png)

3. Open **Fragments** and drag in your **Header** fragment.

![](assets/s5T7FMOun7Fts5lv_V8tK_image.png)

4. Notice that the header fragment is neatly alligned to your template as shown below.

![](assets/5xKXFQNZbeBrCba4bQdQL_image.png)

5. Click the **Save **button to save your template and then click **Back**.

![](assets/qqpj1nXStCHYmMrBfMav8_image.png)

>[!NOTE]
>Note that you may see some broken images. We will fix that later. 

***

# Recap

In this module, you successfully:

- Imported HTML to build a full promotional template

You are now ready to move on to next module - ** Email Creation**
