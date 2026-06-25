---
title: Content Simulation
description: Content Simulation
doc-type: article
exl-id: 3e2b064f-5680-461c-a49e-2a61514e146f
---

**Purpose:** Validate personalisation, conditional logic, and content variants using Adobe Journey Optimizer’s Simulation and Proof tools.

## Learning Objectives

By the end of this module, you will be able to:

1. Upload and use test profile data for simulation.
2. Validate personalised fields and variant logic.
3. Test fallback behaviour for missing or unmatched data.

## Introduction

In this final module, you will test your email with **two conditional variants** using the Simulation tool in Adobe Journey Optimizer.
This allows you to preview how different customers will experience your personalised message, ensuring accuracy before launching the campaign. 

You will use the sample test profile file **sample.csv** from your toolkit.

![](assets/rn5YPx7TSOXwCcdZcYy2J_image.png)

## Open the Simulation Tool

1. Open your completed email.
2. Click **Simulate Content**.
3. Select **Simulate content variation**.

![](assets/19p3U9X_CHBaM4efsxWxR_image.png)

A simulation panel will open after few seconds.

# Upload the Test Profile Data

1. Open **sample.csv** from your toolkit folder.
   - **Alex** → Above 40 years old 
   - **Jason** → Below 40 years old 
2. Click **Upload Input Data**.

![](assets/Psxhxvriekm8nui4CHtA2_image.png)

3. Choose **sample.csv** and click **Continue**.

![](assets/rgjLqjHNWL_MJz46u7gfk_image.png)

AJO processes the file and prepares previews.

***

# Review Variant Rendering

AJO will show both variants side by side based on the uploaded profiles.

**Expected outcomes:**

- **Alex** → Sees **Variant 1** (Age above 40)

![](assets/hNBkCWhSx-5wd9jqdXKqh_image.png)

If you scroll up you wil also see personalised fields with name now as you can see below. 

![](assets/kGCmiMbc4Xqe6Tka-7aHJ_image.png)

- **Jason** → Sees **Variant 2** (Age below 40)

![](assets/zDAMHrNOlgebAy6bjTP25_image.png)

With Jason's full name as well. How cool is that!

![](assets/3Vj09Dz9NDR6d4E6iUjuH_image.png)

***

***

# Validate Fallback Behaviour

**Fallbacks and Defaults:** Check that your email handles any missing data or no-match scenarios gracefully. For example, simulate a profile with an empty birth year field or one that doesn’t qualify for any targeted offer. The preview should either show a default content block or a sensible placeholder instead of broken or empty content. If your simulation shows an empty section where content should be, that indicates you may need to configure a fallback offer or default text in your design.

***

# Recap

In this module, you successfully:

- Simulated personalised content using sample profiles
- Validated variant switching logic
- Confirmed personalised fields populate correctly

You are now ready for next module - ** Brand Alignment**,
where you will evaluate your email against Connection 5G brand guidelines using AI.
