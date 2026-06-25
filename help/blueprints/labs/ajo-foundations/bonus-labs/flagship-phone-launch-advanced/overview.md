---
hold: true
title: Flagship Phone Launch (Advanced)
description: Flagship Phone Launch (Advanced)
doc-type: overview-page

solution: Experience Platform
exl-id: ca43035d-4324-4936-836e-3bc007146b7c
---

>[!CAUTION]
>
>Before you start this lab you must have completed the following two labs:
>
>- [Profile Target Dimension](../../data-stores/relational-store-in-action/profile-target-dimension.md)
>- [Configure Email Channel for Relational](../../data-stores/configure-email-channels/configure-for-relational.md)
>
>If you have not please do so now.



# Overview

For the Flagship Phone Launch use case you want to target a distinct group of customers and any of their associated lines on their account with an upgrade message.  The account holder should get an email informing them they have lines to upgrade to the latest flaghship phone while their individual lines should receive a SMS message letting them know they are eligible for an upgrade.

At the end of this campaign you will have created the following:

- Two distinct audiences that you will converge into a single targetable audience based on non-profile targeting dimension
- A reusable audience that you will publish to the Real-Time Customer Profile's audience portal
- Two distinct communiations
  - A single email to the account holder
  - Multiple SMS messages to each line holders qualified lines

## Learning Objectives

- Understand how to build audiences in orchestrated campaigns
- Understand how to combine audience results
- Understand how to save audiences to the Audience Portal
- Understand how to setup channel configurations for both profile targeting and multi-entity sending
- Understand how to test & publish an Orchestrated Campaign
