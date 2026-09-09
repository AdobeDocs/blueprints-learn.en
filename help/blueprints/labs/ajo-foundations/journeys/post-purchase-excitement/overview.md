---
title: Post-Purchase Excitement
description: Learn how to build an event-driven post-purchase journey that triggers a shipping notification email with dynamic tracking details from a third-party API.
doc-type: overview-page
solution: Experience Platform
exl-id: 570dc378-e7a3-4895-8f14-89d420b6b340
---

# Post-Purchase Excitement

## Pre-Requisites

>[!WARNING]
>
>The below labs must have been completed before starting this lab

These labs must have been completed before starting this lab:

- **Data Stores -- Relational Store in Action** **-->** [Profile Target Dimension](../../data-stores/relational-store-in-action/profile-target-dimension.md)****
- **Data Stores -- Configure Email Channels -->** [Configure for Profile](../../data-stores/configure-email-channels/configure-for-profile.md) 
  *(this can take up to 3hrs to complete)*

If you have not done so please complete these now

## Lab Overview

>[!VIDEO](https://video.tv.adobe.com/v/3491146/)

## Learning Objectives

- Build a Journey that starts with a unitary event
- Setup and configure a custom action to call to 3rd party system to return information used in a Journey
- Execute a journey by streaming in a event payload
- Test and debug profiles and Journeys
- Validate the intended experience through reporting and logs
- Setup personalization in a simple email and see it in action



## Use Case Description

When a customer places an order, you want to send a confirmation message with order details.  Once the order is shipped, you want to trigger a second message with tracking information retrieved dynamically from a 3rd-party API.

**Key callouts:**

- The initial order placed would typically be implemented as transactional message as people don't want to wait around for a confirmation they just order something.
- The order shipped notification could also be implemented using transactional messaging but could be built in a journey allowing for a custom action to retreieve shipping information and enhancing the customer communication

>[!NOTE]
>
>In this lab you will only build out the Order Shipped message and skip the Order Confirmation message.
