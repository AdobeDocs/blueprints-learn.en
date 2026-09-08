---
title: AI Assistant & Content Personalization
description: AI Assistant & Content Personalization
doc-type: article
solution: Experience Platform
exl-id: 1f30c920-7b2b-4343-b663-ebbed1ae4709
---

**Purpose:** Learn how to use Adobe Journey Optimizer’s AI Assistant to generate subject lines, refine email text, adjust tone, and create on-brand Firefly images directly inside the email designer.

## Learning Objectives

By the end of this module, you will be able to:

1. Use the AI Assistant to generate subject lines and pre-headers.
1. Refine hero text, descriptions, tone, and messaging.
1. Apply AI-driven rephrasing, summarisation, and tone adjustments.
1. Generate images using Adobe Firefly with reference style and brand settings.
1. Replace placeholders with generated images inside your email design.

## Introduction

The AI Assistant in AJO helps you build smarter, on-brand content.
It can:

- Generate subject lines
- Improve existing text
- Adjust tone and clarity
- Create branded images using Firefly
- Ensure everything aligns with Connection 5G guidelines

For this exercise, we will improve the email that we have created using the AI Assistant. 

>[!WARNING]
>
>**Note: **The AI Assistant is **non-deterministic**, which means it may generate slightly different content each time it is used. What you see during your practice may not exactly match the screenshots or examples in this guide. That’s okay—focus on learning the process and concepts rather than expecting identical results.

## Create Email Subject Line Using AI Assistant

1. Go back to the Campaign by clicking the back button or edit the email you created in the previous module. (from previous step, you can click on settings tab on right hand side)
1. Click on Email Container > Click on Edit Email button. 
1. Click on the content tab, and then click on Email body
1. Select the **Subject Line** field.
1. Click the **AI Assistant icon**. (see below)

![Image](assets/ai-assistant-and-content-personalization-1.png)

1. You will notice that Brand Guideline is selected by default. 
1. Enter the prompt:

>We are launching iPhone 17 and want a subject line to be catchy

1. Press **Generate**.
1. Review the four variants generated.
1. Choose the variant with the best alignment score and click **Select**.

![Image](assets/ai-assistant-and-content-personalization-16.png)

>[!WARNING]
>
>Note: Your results may be completely different from the lab guide, so do not need to worry. Select what you think is a right title and continue with the lab. 




# Improve Hero Title & Description

1. Open email by clicking on "Edit email body" button. 

![Image](assets/ai-assistant-and-content-personalization-20.png)

1. Click on the **Product ****Catchy ****line** heading.
1. Open AI Assistant by clicking on **Generate and select a text**

![Sbl image](assets/ai-assistant-and-content-personalization-13.png)

1. Select **Connection 5G Brand Guidelines** from the dropdown.

![Image](assets/ai-assistant-and-content-personalization-19.png)

1. Prompt:

>*Write a bold, attention-grabbing headline for the iPhone 17 launch. Keep it under 10 words*

1. Click on Text settings to change the tone and communication strategy. Change Communication strategy to **FOMO (Fear of Missing Out)**, Language to **English **and Tone to **Exciting**. Use shorter version by scalling down the dial. 

![F image](assets/ai-assistant-and-content-personalization-6.png)

1. Click the **Generate** button
1. Review and select the best version, 
1. If your text is long then use the slier to **"shorter text" **and regenerate the text. 



![Image](assets/ai-assistant-and-content-personalization-25.png)

1. Once you are happy with the text click on **Select**

![Image](assets/ai-assistant-and-content-personalization-15.png)

## Description prompt

This time we want to test how AI can help to find issues. 

1. Select the text below which is templaed text and has no meaning. 

![Image](assets/ai-assistant-and-content-personalization-5.png)

1. Click on evaluate button as shown below. 

![Image](assets/ai-assistant-and-content-personalization-11.png)

1. Your original content will be automatically selected with your brand, as shown in Steps 1 and 2 below. Click the **Evaluate **button to proceed.

![Image](assets/ai-assistant-and-content-personalization-17.png)

1. As expected, you will notice many errors that violate brand guidelines. Although these could be corrected using AI, in this case we will not revise the existing materials. Instead, we will leave them as they are and create new content from scratch that fully aligns with brand standards.

![DCObYpgpMgLJM WX image](assets/ai-assistant-and-content-personalization-7.png)

1. Lets use new paragraph that is generated for you using AI using the prompt below. You can use same approach for decription text using the prompt below.

Prompt:

>*Write a compelling product description for the new iPhone 17. Highlight its most impressive features, such as advanced camera, battery life, and performance. The tone should be premium, exciting, and easy to understand for a wide audience. Keep it under 3 sentences.*

In order to save time I have already created the text for you. Copy and paste below to get your text.

>Discover the iPhone 17™ - featuring an advanced camera for stunning photos, all-day battery life to keep you going, and lightning-fast performance that keeps you ahead. Don’t miss out on this innovative experience.



Your email should look like as shown below.  

![Image](assets/ai-assistant-and-content-personalization-4.png)


## Add a Firefly-Generated Image

Until now, we have tested AI Assistant on Subject line and Text. What about images? 

Before we dive into AI image generation, let us see what types of experiences we can build. 

We understand that we have the year of birth of the profile. One of the experiences we can do is to create a block with different variants. With Adobe Journey Optimizer, this is possible and one of the biggest advantages of having Adobe Experience Platform as your base. We will cover experimentation in our next module, but first, let us prepare the block

1. Drag an **Image** component to the left-hand side column below iphone 17 Family block.

![Image](assets/ai-assistant-and-content-personalization-18.png)

1. Click outside then select the image placeholder. (Make sure you click on the image otherwise you wont see Firefly option)

![CuUzs4Go  image](assets/ai-assistant-and-content-personalization-26.png)

1. Under **Firefly**, click **Generate and select image**.

![Image](assets/ai-assistant-and-content-personalization-22.png)

## Upload Reference Image

1. Turn on **Reference Style**.
1. Select **Connection 5G Brand Guideline **on brand selection

![Image](assets/ai-assistant-and-content-personalization-8.png)

1. Click on Upload Image

![Image](assets/ai-assistant-and-content-personalization-14.png)

1. Select reference.jpg frmo the toolkit folder

![Image](assets/ai-assistant-and-content-personalization-12.png)

1. Add Image Prompt
   `Portrait-oriented image of a confident man in his early to mid-40s, standing alone at night in a neon-lit urban street, focused on his smartphone. Cinematic cyberpunk-inspired city atmosphere with colorful LED signs, cool blue and warm orange lighting, shallow depth of field, soft bokeh lights in the background. Modern lifestyle, tech-savvy mood, realistic skin tones, high contrast, photorealistic, professional lighting, ultra-detailed`.

![Xp4IVBEKWnbcw image](assets/ai-assistant-and-content-personalization-23.png)

## Choose Image Settings

Choose your **Image settings**:

1. Choose the following settings:
   - **Ratio:** Landscape (4:3)
   - **Content type:** Photo
   - **Colour & tone:** Cool tone
   - **Lighting: **Dramatic Lighting
1. Press **Generate** button 

![TByDX1ZBhU0Qpjd image](assets/ai-assistant-and-content-personalization-3.png)


## Select & Insert the Generated Image

1. Review Firefly results by check all images generated.

![Image](assets/ai-assistant-and-content-personalization-10.png)

1. Click **Select** for your desired chosen image.

![Image](assets/ai-assistant-and-content-personalization-9.png)

1. If prompted with an upload modal, click **Next**.

![Image](assets/ai-assistant-and-content-personalization-24.png)

1. Then click **Import**.

![Image](assets/ai-assistant-and-content-personalization-21.png)

## Finalise Block Design

I have applied rounded border radius by 10 just to make it look modern. If you have time you can do that. 

After few iterations and variation we have final design. Your final layout should resemble the example.

![Image](assets/ai-assistant-and-content-personalization-2.png)

At this point, you should feel confident using AI to accelerate and elevate content creation.

## Recap

You successfully used the AI Assistant to:

- Generate subject lines
- Refine hero text
- Rephrase paragraphs
- Change tone of messaging
- Create branded Firefly images using reference style
- Insert generated images into your email

You are now ready for next module **-  Personalisation & Experimentation**, where you will build profile-driven variants and tests.
