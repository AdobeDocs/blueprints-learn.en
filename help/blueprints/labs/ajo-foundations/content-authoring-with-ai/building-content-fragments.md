---
title: Building content fragments
description: Learn how to break an email design into reusable fragments, such as a header block, that stay consistent across templates in Adobe Journey Optimizer.
doc-type: article
solution: Experience Platform
exl-id: 253a9332-dc08-420d-ac11-2bf342f0dc38
---

# Building content fragments

## Content creation with templates & fragments

**Purpose:** Learn how to create reusable fragments in Adobe Journey Optimizer, then apply them inside a real email within a journey.

## Learning objectives

By the end of this module, you will be able to:

1. Break down an email design into reusable fragments.
1. Create header, footer, banner, body, and CTA fragments.

## Why fragments matter

Fragments allow you to create consistent, brand‑aligned content that can be reused across emails, campaigns, and journeys.

### Fragments

Reusable building blocks such as:

- Headers
- Footers
- CTAs
- Banners
- Legal disclaimers

Whenever a fragment is updated, all emails using it update automatically.

## How this fits into email creation

- **Create fragments** for elements that rarely change.
- **Build a template** that uses those fragments.
- **Use the template** in your campaign email and customise its content.

Below is the final email you will create from this lab.

![Final email design you build in this lab](assets/building-content-fragments-final-email-preview.png)

But the design team normally provides you with templates such as this:

![Generic design template provided by the design team](assets/building-content-fragments-generic-design-template.png)


## Step 1: Create content fragments

The below template is a generic design template and our goal is to break this down into repeatable content blocks. In Adobe journey optimizer this is called **Fragments**. 

The first step is to identify how many fragments do we need to create. In this template it makes sense to use 5 fragments as shown below. 



![Template broken down into five identified fragments](assets/building-content-fragments-five-fragments-identified.png)

We have identified the templates requires 5 fragments as follows. 

- Header
- Banner
- CTA
- Body
- Footer    

>[!NOTE]
>
>For this exercise, you create only one header fragment to save time. 



Create a header fragment to start with. However, before creating the fragment, set up an asset folder since the assets environment is shared. To do this, first create your own folder. 

1. From the left-hand navigation, locate the **Content Management** section and click on **Assets**.

   ![Content Management section with Assets option in left navigation](assets/building-content-fragments-content-management-assets-nav.png)

2. Click on **Assets** under Assets Management section.

   ![Assets option under the Assets Management section](assets/building-content-fragments-assets-under-assets-management.png)

3. Create a folder by clicking **"Create Folder"** button. 

   ![Create Folder button in the Assets area](assets/building-content-fragments-click-create-folder-button.png)

4. Give a name like your first and last name. eg. Nish\_Pithia\_LabAssets (Something you can remember)

   ![Naming the new asset folder with your first and last name](assets/building-content-fragments-name-asset-folder.png)

5. **Create a new fragment:** Under Content Management click on **Fragments** and create new fragment.

   ![Fragments option under Content Management to create a new fragment](assets/building-content-fragments-click-fragments-create-new.png)

   Give a friendly name as shown below. Add all details as follows:

   **Name:** Header

   **Description:** Fragment Header for the template

   **Type:** Select Visual fragment

   ![Header fragment name, description, and Visual fragment type fields](assets/building-content-fragments-fragment-name-type-details.png)

6. Click on **Create button** on your top right.

   ![Create button in the top right of the new fragment dialog](assets/building-content-fragments-click-create-button-top-right.png)

   This opens a blank fragment creator screen. 

7. Click on 1:1 Columns under Structures and drag on the canvas as shown below. (Please click on the image below to see animated graphic)

   ![Animated demo of dragging a 1:1 Columns structure onto the fragment canvas](assets/building-content-fragments-drag-1-1-columns-structure.gif)

8. Next, drag "**image**" on the 1:1 row which we just added

   ![Dragging an image component onto the 1:1 row](assets/building-content-fragments-drag-image-onto-row.png)

9. Upload the logo image that you have been provided. Click on **"Import media button"**

   ![Import media button to upload the logo image](assets/building-content-fragments-click-import-media-button.png)

10. **Upload the logo:** Upload the logo (*C5G-Logo.png*) from the toolkit folder of images and click next.

   ![Selecting C5G-Logo.png from the toolkit folder to upload](assets/building-content-fragments-upload-logo-select-file.png)

   ![Clicking Next after selecting the logo upload](assets/building-content-fragments-upload-logo-click-next.png)

11. Select the **asset folder** that you have created, then click **Import**. The file is saved in your folder.

   ![Selecting the created asset folder and clicking Import](assets/building-content-fragments-select-asset-folder-import.png)

12. The logo is placed correctly, but it is too large and needs to be resized. To resize the logo, update its properties. Click the **Style tab** and set the width to 40% by dragging the slider, as shown below. 

   >[!NOTE]
   >
   >Note that when the toggle button is on, the 40 number represents % and not pixels. If you want an absolute pixel-perfect value, toggle the button to px. 



   ![Style tab width slider set to 40 percent to resize the logo](assets/building-content-fragments-resize-logo-width-slider.png)

13. Click **“Save”** and your fragment is saved. You get a green bar notification on the confirmation. 

   ![Green confirmation bar after saving the fragment](assets/building-content-fragments-save-fragment-confirmation.png)

14. The fragment saved is in a draft mode. Before you use it, you need to publish it. Click on the **back** button. 

   ![Back button to leave the draft fragment before publishing](assets/building-content-fragments-click-back-button-draft.png)

15. Click "**Publish**" button. You see a message "Publishing fragment, this may take some time. We will notify once done." on confirmation. Your fragment is ready to be used for template creation. 

![Publish button and publishing fragment confirmation message](assets/building-content-fragments-click-publish-fragment-button.png)

You see the status change to **"Live"**. At this point, you have completed building a header fragment, which is used in the next step. 

![Header fragment status changed to Live](assets/building-content-fragments-fragment-status-live.png)

>[!NOTE]
>
>Note that in this exercise, you created only one fragment. In practice, architects may choose to create multiple fragments, such as headers, footers, or other reusable components.

## Recap

In this module, you successfully:

- Broke down an email into reusable header fragment
- Created a header content blocks

You are now ready to move on to the next module - **Building content template**, where you will use fragment you created to generate new template.
