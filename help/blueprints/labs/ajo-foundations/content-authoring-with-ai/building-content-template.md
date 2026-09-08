---
title: Building Content Template
description: Learn how to build a reusable email template in Adobe Journey Optimizer by importing HTML and inserting a previously created header fragment.
doc-type: article
solution: Experience Platform
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


## Create a New Template Using Fragments

Templates help users reuse full layouts across campaigns. Content templates in Adobe Journey Optimizer are powerful tools designed to simplify and streamline the way you create reusable content for campaigns and journeys. Whether you’re crafting an email, SMS, or push notification, templates help you save time by providing pre-designed structures that can be easily customized and shared across projects.

For an accelerated and improved design process, create standalone templates to reuse custom content easily across Journey Optimizer campaigns and journeys.

This functionality allows content-oriented users to work on templates outside campaigns or journeys. Marketing users can then reuse and adapt these standalone content templates inside their own journeys or campaigns.

## Create Template

1. Go to **Content Management → Content Templates**.

![8GT AZjDP0Ab4bIU image](assets/building-content-template-9.png)

1. Click **Create Template **and then fill in the following:
   - **Name:** `Promotional Template`
   - **Description:** `Promotional Template for phone products`
   - **Channel:** `Email`

![Image](assets/building-content-template-13.png)

1. Click **Create**.

![Gwy image](assets/building-content-template-5.png)


## Add Subject Line & Open Email Designer

1. Add subject line: `Promotional Template` and click **on the email body **to open it to edit

![Image](assets/building-content-template-6.png)

1. You will see three options: 
   1. Desing from scratch
   2. Code your own
   3. Import HTML

We will select third option. Click **Import HTML**



![Image](assets/building-content-template-10.png)

## Import Provided HTML Template



1. Upload the template html file from the toolkit folder `promotional-template-final.html`

![CVvhKbyJUh41nbw image](assets/building-content-template-4.png)

1. Click on Import button to **import** the template. 

![Image](assets/building-content-template-7.png)

1. Wait for the layout to render. You will notice issues like broken image links and missing branding. (This is expected behavour as we have placeholder assets)

![Image](assets/building-content-template-2.png)


## Explore Template Structure

### Left Panel

The "**Structures**" and "**Contents**" components in Adobe Journey Optimizer (AJO) are essential elements used when designing emails, landing pages, and content fragments. Structures define the layout framework, while Contents provide the actual building blocks placed inside those layouts.

The body section in Adobe Journey Optimizer is the main container for your email or page content. It serves as the root of the visual design space, where all structure components (columns, layouts) and content components (text, images, buttons, etc.) are nested.

### Right Panel

The "**Settings**" and "**Style**" options under the body section in Adobe Journey Optimizer allow you to define the foundational look and layout of your email or page. These controls affect the entire design since the body is the parent of all components.

![Image](assets/building-content-template-16.png)


On your left hand rail bar you will find sections for: 

- Fragments
- Files
- Body structure 
- Tracked URLs

You should be able to see the header fragement that we created in previous execrise should appear here as shown below. Make sure your header fragment should show they are live with blue dot and not in a draft mode. Spend time checking rest of the sections. 

![Image](assets/building-content-template-3.png)

>[!WARNING]
>
>If you do not see your fragment here it means that you did not save it properly and will need to re-upload it.



## Insert Header Fragments

Let us now improve the template. We have already created header and footer. 

1. Drag a **1:1 Column** above the existing content.

![DBVTti7na JBDJxdD image](assets/building-content-template-8.png)

You should see something like this. 

![Image](assets/building-content-template-15.png)

1. Your background will use template background color which is black currently. Set its **background colour to white. Click **in the Style tab on the right rail and use white colour from the colour picker. 

![Image](assets/building-content-template-14.png)

1. Open **Fragments** and drag in your **Header** fragment.

![V8tK image](assets/building-content-template-12.png)

1. Notice that the header fragment is neatly alligned to your template as shown below.

![Image](assets/building-content-template-1.png)

1. Click the **Save **button to save your template and then click **Back**.

![Image](assets/building-content-template-11.png)

>[!NOTE]
>
>Note that you may see some broken images. We will fix that later. 


## Recap

In this module, you successfully:

- Imported HTML to build a full promotional template

You are now ready to move on to next module - ** Email Creation**
