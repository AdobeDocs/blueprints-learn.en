---
hold: true
title: Building Content Fragments
description: Building Content Fragments
doc-type: article

solution: Experience Platform
exl-id: 253a9332-dc08-420d-ac11-2bf342f0dc38
---

# Content creation with Templates & Fragments

**Purpose:** Learn how to create reusable fragments in Adobe Journey Optimizer, then apply them inside a real email within a journey.

## Learning Objectives

By the end of this module, you will be able to:

1. Break down an email design into reusable fragments.
1. Create header, footer, banner, body, and CTA fragments.

## Why Fragments matter

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

![Image](assets/building-content-fragments-18.png)

But the design team normally provides you with templates such as this:

![Image](assets/building-content-fragments-14.png)


## Step 1: Create Content Fragments

The below template is a generic design template and our goal is to break this down into repeatable content blocks. In Adobe journey optimizer this is called **Fragments**. 

The first step is to identify how many fragments do we need to create. In this template it makes sense to use 5 fragments as shown below. 



![Image](assets/building-content-fragments-11.png)

We have identified the templates requires 5 fragments as follows. 

- Header
- Banner
- CTA
- Body
- Footer    

>[!NOTE]
>
>For this exercise we will just create one header fragment in order to save time. 



Let us create a header fragment to start with. However, before we start creating fragment we need to setup an asset folder as we are sharing the assets enviroment. To achieve this we will first create your own folder. 

1. From the left-hand navigation, locate the **Content Management **section and click on **Assets**

.

![Image](assets/building-content-fragments-7.png)

1. Click on **Assets** under Assets Management section.

![Image](assets/building-content-fragments-17.png)

1. Create a folder by clicking **"Create Folder"** button. 

![Image](assets/building-content-fragments-15.png)

1. Give a name like your first and last name. eg. Nish\_Pithia\_LabAssets (Something you can remember)

![Image](assets/building-content-fragments-16.png)

1. **Create a new fragment: **Under Content Management click on **Fragments** and create new fragment. 

![Image](assets/building-content-fragments-6.png)

Give a friendly name as shown below. Add all details as follows: 

**Name:** Header

**Description: **Fragment Header for the template

**Type: **Select Visual fragment

![Image](assets/building-content-fragments-3.png)

1. Click on **Create button** on your top right.

![Image](assets/building-content-fragments-19.png)

You will now be presented with a blank fragment creator screen. 

1. Click on 1:1 Columns under Structures and drag on the canvas as shown below. (Please click on the image below to see animated graphic)

![CO8gSyUOmK89AEC](assets/building-content-fragments-1.gif)

1. Next, drag "**image**" on the 1:1 row which we just added

![Image](assets/building-content-fragments-4.png)

1. Upload the logo image that you have been provided. Click on **"Import media button" **

![Image](assets/building-content-fragments-9.png)

1. **Upload the logo: **You will need to upload logo (*C5G-Logo.png*) from the toolkit folder of images and click next.

![Image](assets/building-content-fragments-5.png)

![Image](assets/building-content-fragments-13.png)

1. Select the **asset folder** that you have created, then click **Import**. The file will be saved in your folder.

![Image](assets/building-content-fragments-8.png)

1. The logo is placed correctly, but it is too large and needs to be resized. To resize the logo, update its properties. Click the **Style tab** and set the width to 40% by dragging the slider, as shown below. 

>[!NOTE]
>
>Note that the the toggle button is on means that the 40 number reprents % and not pixel). if you want an absolute pixel perfect value, toggle the button to px. 



![KsAz 8u image](assets/building-content-fragments-20.png)

1. Click **“Save”** and your fragment is saved. You will get a green bar notification on the confirmation. 

![TobdQzQobFP7iDy image](assets/building-content-fragments-10.png)

1. The fragment saved is in a draft mode. Before you use you will need to publish it. Click on the **back** button. 

![Image](assets/building-content-fragments-21.png)

1. Click "**Publish**" button. You will see a message "Publishing fragment, this may take some time. We will notify once done." on confirmation. Your fragment is ready to be used for template creation. 

![Image](assets/building-content-fragments-12.png)

You will see the status will change to **"Live"**. At this point, we have completed building a header fragment which we will be used in our next step. 

![VME0 2x4UKBD image](assets/building-content-fragments-2.png)

>[!NOTE]
>
>Note that in this exercise, we will create only one fragment. In practice, architects may choose to create multiple fragments, such as headers, footers, or other reusable components.

## Recap

In this module, you successfully:

- Broke down an email into reusable header fragment
- Created a header content blocks

You are now ready to move on to next module - ** Content Creation - Template**, where you will use fragment you created to generate new template. 
