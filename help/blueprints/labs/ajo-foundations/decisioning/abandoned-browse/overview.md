---
title: Abandoned Browse
description: Learn how to build an end-to-end abandoned-browse decisioning workflow that delivers personalized, eligibility-aware phone offers across channels.
doc-type: overview-page
solution: Experience Platform
exl-id: 37b8a0b3-2820-4303-81d2-19890a3c5782
---

# Abandoned Browse

## Pre-Requisites

>[!WARNING]
>
>The below labs must have been completed before starting this lab

- **Data Stores -- Profile in Action** **-->** [Create Datastream](../../data-stores/profile-in-action/create-datastream.md)****

If you have not completed these labs please do so now before continuing.

## Lab Overview

>[!VIDEO](https://video.tv.adobe.com/v/3491316/)

## Business Objectives

The business use case for this lab is that Connection 5G wants to increase sales of the new Apple flagship phone, the iPhone 17, by targeting customers who have browsed the iPhone 17 overview page but haven't purchased. The key objectives of the campaign are as follows:

- **Identify high-intent customers** by detecting when a user views a flagship phone page multiple times without completing a purchase. 
- **Trigger a real-time personalized experience** across all Connection 5G-owned digital surfaces when this behavior occurs. 
- **Deliver contextual offers** based on key customer attributes such as the **account holder’s age** and their **current mobile plan**. 
- **Ensure offer eligibility is enforced** so that customers only see phone offers that are compatible with their plan. 
- **Dynamically adjust the phone tier offered** (e.g., base, pro, ultra) based on the customer’s engagement or response to previous offers. 
- **Provide consistent personalization across channels** by using centralized decisioning logic to determine the best offer in real time. 
- **Increase conversion likelihood** by presenting the most relevant flagship phone offer to each customer at the right moment.

## Lab Learning Objectives

To meet the above business objectives in this lab, you will learn how to:

- **Extend the offer data model** by adding custom attributes to the offer schema so they can be used in decisioning logic. 
- **Create eligibility rules** that determine which profiles qualify for specific offers based on profile attributes. 
- **Build and configure offer items**, including setting priorities, defining eligibility conditions, and applying frequency capping. 
- **Organize offers into a collection** so they can be easily referenced and evaluated during the Decisioning activity. 
- **Create a ranking formula** that dynamically adjusts offer priority based on profile characteristics. 
- **Configure a selection strategy** that combines offer collections, eligibility rules, and ranking logic to determine which offers are considered and how they are ordered. 
- **Set up a Code-Based Experience (CBE) channel** to allow external systems to request decision results and receive offers in JSON format. 
- **Test the end-to-end decisioning workflow** by sending experience events and decision requests to validate eligibility logic, ranking behavior, and frequency capping. 

By completing this lab, you will gain hands-on experience designing and validating a **complete offer decisioning workflow in Adobe Journey Optimizer** to meet the business use case.
