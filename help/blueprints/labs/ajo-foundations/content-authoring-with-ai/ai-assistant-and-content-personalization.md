---
title: AI assistant and content personalization
description: Use Adobe Journey Optimizer's AI Assistant to generate on-brand subject lines, refine email copy and tone, and create Firefly-generated images inside the email designer.
doc-type: article
solution: Experience Platform
exl-id: 1f30c920-7b2b-4343-b663-ebbed1ae4709
---

# AI assistant and content personalization

**Purpose:** Learn how to use Adobe Journey Optimizer’s AI Assistant to generate subject lines, refine email text, adjust tone, and create on-brand Firefly images directly inside the email designer.

## Learning objectives

By the end of this module, you will be able to:

1. Use the AI Assistant to generate subject lines and pre-headers.
1. Refine hero text, descriptions, tone, and messaging.
1. Apply AI-driven rephrasing, summarization, and tone adjustments.
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

For this exercise, you improve the email that you created using the AI Assistant. 

> [!NOTE]
>
>The AI Assistant is **non-deterministic**, which means it may generate slightly different content each time it is used. What you see during your practice may not exactly match the screenshots or examples in this guide. That’s okay—focus on learning the process and concepts rather than expecting identical results.

## Create email subject line using AI Assistant

1. Go back to the Campaign by clicking the back button, or edit the email you created in the previous module. From the previous step, you can click the **Settings** tab on the right-hand side.
2. Click on Email Container > Click on Edit Email button. 
3. Click on the content tab, and then click on Email body
4. Select the **Subject Line** field.
5. Click the **AI Assistant icon**. (see below)

   ![AI Assistant icon in the Subject Line field toolbar](assets/ai-assistant-and-content-personalization-ai-assistant-icon.png)

6. You notice that Brand Guideline is selected by default. 
7. Enter the prompt:

   >We are launching iPhone 17 and want a subject line to be catchy

8. Press **Generate**.
9. Review the four variants generated.
10. Choose the variant with the best alignment score and click **Select**.

![Selecting the best-aligned subject line variant from AI Assistant](assets/ai-assistant-and-content-personalization-select-subject-line-variant.png)

> [!NOTE]
>
>Your results may be completely different from the lab guide, so you do not need to worry. Select what you think is a right title and continue with the lab. 




## Improve hero title & description

1. Open email by clicking on "Edit email body" button. 

   ![Edit email body button in Campaign editor](assets/ai-assistant-and-content-personalization-edit-email-body-button.png)

2. Click on the **Product Catchy line** heading.
3. Open AI Assistant by clicking on **Generate and select a text**

   ![Generate and select a text option opening AI Assistant](assets/ai-assistant-and-content-personalization-generate-and-select-text.png)

4. Select **Connection 5G Brand Guidelines** from the dropdown.

   ![Connection 5G Brand Guidelines option selected in AI Assistant dropdown](assets/ai-assistant-and-content-personalization-brand-guidelines-dropdown.png)

5. Prompt:

   >*Write a bold, attention-grabbing headline for the iPhone 17 launch. Keep it under 10 words*

6. Click on Text settings to change the tone and communication strategy. Change Communication strategy to **FOMO (Fear of Missing Out)**, Language to **English** and Tone to **Exciting**. Use shorter version by scaling down the dial. 

   ![Text settings panel with FOMO communication strategy and Exciting tone selected](assets/ai-assistant-and-content-personalization-text-settings-fomo-tone.png)

7. Click the **Generate** button
8. Review and select the best version, 
9. If your text is long, then use the slider to **"shorter text"** and regenerate the text. 



   ![Shorter text slider used to regenerate a shorter headline](assets/ai-assistant-and-content-personalization-shorter-text-slider.png)

10. Once you are happy with the text click on **Select**

![Selecting the generated hero headline text](assets/ai-assistant-and-content-personalization-select-generated-hero-text.png)

## Description prompt

This time, you test how AI can help find issues. 

1. Select the text below which is templated text and has no meaning. 

   ![Templated placeholder text selected for evaluation](assets/ai-assistant-and-content-personalization-select-templated-text.png)

2. Click on evaluate button as shown below. 

   ![Evaluate button in AI Assistant text panel](assets/ai-assistant-and-content-personalization-click-evaluate-button.png)

3. Your original content is automatically selected with your brand, as shown in Steps 1 and 2 below. Click the **Evaluate** button to proceed.

   ![Original content automatically selected with brand guidelines before evaluation](assets/ai-assistant-and-content-personalization-evaluate-brand-alignment.png)

4. As expected, you notice many errors that violate brand guidelines. Although these could be corrected using AI, in this case you don't revise the existing materials. Instead, you leave them as they are and create new content from scratch that fully aligns with brand standards.

   ![AI Assistant evaluation results showing brand guideline violations](assets/ai-assistant-and-content-personalization-brand-guideline-errors.png)

5. Use the new paragraph that's generated for you using AI with the prompt below. You can use the same approach for the description text using the prompt below.

Prompt:

>*Write a compelling product description for the new iPhone 17. Highlight its most impressive features, such as advanced camera, battery life, and performance. The tone should be premium, exciting, and easy to understand for a wide audience. Keep it under 3 sentences.*

To save time, the text has already been created for you. Copy and paste below to get your text.

>Discover the iPhone 17™ - featuring an advanced camera for stunning photos, all-day battery life to keep you going, and lightning-fast performance that keeps you ahead. Don’t miss out on this innovative experience.



Your email looks like the example shown below.  

![Email preview after adding the new AI-generated description text](assets/ai-assistant-and-content-personalization-email-with-description-text.png)


## Add a Firefly-generated image

Until now, we have tested AI Assistant on Subject line and Text. What about images? 

Before diving into AI image generation, look at what types of experiences you can build. 

We understand that we have the year of birth of the profile. One of the experiences we can do is to create a block with different variants. With Adobe Journey Optimizer, this is possible and one of the biggest advantages of having Adobe Experience Platform as your base. We will cover experimentation in our next module, but first, prepare the block below.

1. Drag an **Image** component to the left-hand side column below iphone 17 Family block.

   ![Dragging an Image component below the iPhone 17 Family block](assets/ai-assistant-and-content-personalization-drag-image-component.png)

2. Click outside then select the image placeholder. (Make sure you click on the image, otherwise you won't see the Firefly option.)

   ![Selecting the image placeholder to access Firefly options](assets/ai-assistant-and-content-personalization-select-image-placeholder.png)

3. Under **Firefly**, click **Generate and select image**.

![Generate and select image option under Firefly](assets/ai-assistant-and-content-personalization-firefly-generate-select-image.png)

## Upload reference image

1. Turn on **Reference Style**.
2. Select **Connection 5G Brand Guideline** on brand selection

   ![Connection 5G Brand Guideline selected for image reference style](assets/ai-assistant-and-content-personalization-select-brand-guideline-reference.png)

3. Click on Upload Image

   ![Upload Image button in Firefly reference style panel](assets/ai-assistant-and-content-personalization-click-upload-image.png)

4. Select reference.jpg from the toolkit folder

   ![Selecting reference.jpg from the toolkit folder](assets/ai-assistant-and-content-personalization-select-reference-jpg.png)

5. Add Image Prompt
   `Portrait-oriented image of a confident man in his early to mid-40s, standing alone at night in a neon-lit urban street, focused on his smartphone. Cinematic cyberpunk-inspired city atmosphere with colorful LED signs, cool blue and warm orange lighting, shallow depth of field, soft bokeh lights in the background. Modern lifestyle, tech-savvy mood, realistic skin tones, high contrast, photorealistic, professional lighting, ultra-detailed`.

![Firefly image prompt field with portrait description entered](assets/ai-assistant-and-content-personalization-firefly-image-prompt.png)

## Choose image settings

Choose your **Image settings**:

1. Choose the following settings:
   - **Ratio:** Landscape (4:3)
   - **Content type:** Photo
   - **Color & tone:** Cool tone
   - **Lighting:** Dramatic Lighting
1. Press **Generate** button 

![Firefly image settings including ratio, content type, and lighting before generating](assets/ai-assistant-and-content-personalization-firefly-image-settings.png)


## Select & insert the generated image

1. Review Firefly results by checking all images generated.

   ![Reviewing Firefly-generated image results](assets/ai-assistant-and-content-personalization-review-firefly-results.png)

2. Click **Select** for your desired chosen image.

   ![Selecting the desired generated Firefly image](assets/ai-assistant-and-content-personalization-select-firefly-image.png)

3. If prompted with an upload modal, click **Next**.

   ![Upload modal prompting to click Next](assets/ai-assistant-and-content-personalization-upload-modal-next.png)

4. Then click **Import**.

![Import button to insert the selected image](assets/ai-assistant-and-content-personalization-click-import-button.png)

## Finalize block design

Apply a rounded border radius of 10 just to make it look modern, if you have time. 

After a few iterations and variations, you have the final design. Your final layout resembles the example.

![Final email block design with rounded image corners](assets/ai-assistant-and-content-personalization-final-block-design.png)

At this point, you should feel confident using AI to accelerate and elevate content creation.

## Recap

You successfully used the AI Assistant to:

- Generate subject lines
- Refine hero text
- Rephrase paragraphs
- Change tone of messaging
- Create branded Firefly images using reference style
- Insert generated images into your email

You are now ready for the next module - **Personalization and content experimentation**, where you will build profile-driven variants and tests.
