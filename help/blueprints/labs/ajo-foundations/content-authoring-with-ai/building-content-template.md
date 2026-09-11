---
hold: true
title: Building content template
description: Learn how to build a reusable email template in Adobe Journey Optimizer by importing HTML and inserting a previously created header fragment.
doc-type: article
solution: Experience Platform
exl-id: e73f06b1-be8a-4096-949c-900db13db9f8
---

# Building content template

## Content creation with templates & fragments

**Purpose:** Learn how to create reusable templates in Adobe Journey Optimizer

## Learning objectives

By the end of this module, you will be able to:

1. Build a full email template using imported HTML and fragments.

## Why templates matter

Templates allow you to create consistent, brand‑aligned content that can be reused across emails, campaigns, and journeys.

### Templates

Blueprints that structure:

- Header placement
- Body content area
- Footer area
- Standard layout styling

Templates ensure brand consistency across teams and save significant creation time.


## Create a new template using fragments

Templates help users reuse full layouts across campaigns. Content templates in Adobe Journey Optimizer are powerful tools designed to simplify and streamline the way you create reusable content for campaigns and journeys. Whether you’re crafting an email, SMS, or push notification, templates help you save time by providing pre-designed structures that can be easily customized and shared across projects.

For an accelerated and improved design process, create standalone templates to reuse custom content easily across Journey Optimizer campaigns and journeys.

This functionality allows content-oriented users to work on templates outside campaigns or journeys. Marketing users can then reuse and adapt these standalone content templates inside their own journeys or campaigns.

## Create template

1. Go to **Content Management → Content Templates**.

![Navigating to Content Management then Content Templates](assets/building-content-template-navigate-content-templates.png)

2. Click **Create Template** and then fill in the following:
   - **Name:** `Promotional Template`
   - **Description:** `Promotional Template for phone products`
   - **Channel:** `Email`

![Create Template form with name, description, and Email channel](assets/building-content-template-create-template-form-fields.png)

3. Click **Create**.

![Create button to finish creating the Promotional Template](assets/building-content-template-click-create-button.png)


## Add subject line & open email designer

1. Add subject line: `Promotional Template` and click **on the email body** to open it to edit

![Adding the subject line and opening the email body to edit](assets/building-content-template-add-subject-line-open-editor.png)

2. You see three options: 
   1. Design from scratch
   2. Code your own
   3. Import HTML

Select the third option. Click **Import HTML**



![Selecting the Import HTML option among the three design choices](assets/building-content-template-select-import-html-option.png)

## Import provided HTML template



1. Upload the template html file from the toolkit folder `promotional-template-final.html`

![Uploading promotional-template-final.html from the toolkit folder](assets/building-content-template-upload-html-template-file.png)

2. Click on Import button to **import** the template. 

![Import button to import the uploaded HTML template](assets/building-content-template-click-import-button.png)

3. Wait for the layout to render. You notice issues like broken image links and missing branding. (This is expected behaviour as we have placeholder assets)

![Rendered template showing broken image links and missing branding placeholders](assets/building-content-template-rendered-template-broken-images.png)


## Explore template structure

### Left panel

The "**Structures**" and "**Contents**" components in Adobe Journey Optimizer (AJO) are essential elements used when designing emails, landing pages, and content fragments. Structures define the layout framework, while Contents provide the actual building blocks placed inside those layouts.

The body section in Adobe Journey Optimizer is the main container for your email or page content. It serves as the root of the visual design space, where all structure components (columns, layouts) and content components (text, images, buttons, etc.) are nested.

### Right panel

The "**Settings**" and "**Style**" options under the body section in Adobe Journey Optimizer allow you to define the foundational look and layout of your email or page. These controls affect the entire design since the body is the parent of all components.

![Settings and Style options in the right panel for the body section](assets/building-content-template-body-settings-style-panel.png)


On your left hand rail bar you find sections for: 

- Fragments
- Files
- Body structure 
- Tracked URLs

You see the header fragment that you created in the previous exercise appear here as shown below. Make sure your header fragment shows as live with a blue dot and not in draft mode. Spend time checking the rest of the sections. 

![Header fragment shown live with a blue dot in the left sidebar](assets/building-content-template-header-fragment-live-sidebar.png)

> [!NOTE]
>
>If you do not see your fragment here it means that you did not save it properly and need to re-upload it.



## Insert header fragments

Now improve the template. You have already created the header and footer. 

1. Drag a **1:1 Column** above the existing content.

![Dragging a 1:1 Column above the existing template content](assets/building-content-template-drag-1-1-column-above-content.png)

You see something like this. 

![Template layout after adding the new column above the content](assets/building-content-template-column-added-above-content.png)

2. Your background uses the template background color, which is currently black. Set its **background colour to white. Click** in the Style tab on the right rail and use white colour from the colour picker. 

![Setting the column background colour to white using the colour picker](assets/building-content-template-set-background-color-white.png)

3. Open **Fragments** and drag in your **Header** fragment.

![Dragging the Header fragment into the template from the Fragments panel](assets/building-content-template-drag-header-fragment-into-template.png)

4. Notice that the header fragment is neatly aligned to your template as shown below.

![Header fragment neatly aligned within the template](assets/building-content-template-header-fragment-aligned-template.png)

5. Click the **Save** button to save your template and then click **Back**.

![Save button to save the template before clicking Back](assets/building-content-template-click-save-button-template.png)

>[!NOTE]
>
>Note that you may see some broken images. We will fix that later. 


## Recap

In this module, you successfully:

- Imported HTML to build a full promotional template

You are now ready to move on to the next module - **Creating the email**
