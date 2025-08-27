---
title: Real-Time CDP with Adobe Campaign v8 integration pattern
description: Showcases how the Adobe Experience Platform and its Real-Time Customer Profile and centralized segmentation tool can be utilized with Adobe Campaign v8 to deliver personalized conversations.
solution: Real-Time Customer Data Platform, Campaign
exl-id: d0291088-02ed-4e7e-b538-018ea40e38c6
---
# [!DNL Real-Time CDP] with Adobe [!DNL Campaign] v8 Integration Pattern

Showcases how the Adobe [!DNL Experience Platform] and its Real-Time Customer Profile and centralized segmentation tool can be utilized with Adobe Campaign to deliver personalized conversations.

## Applications

* Adobe [!DNL Experience Platform Real-Time CDP]
* Adobe [!DNL Campaign] v8

## Architecture

<img src="images/rtcdp-campaign-v8-architecture.svg" alt="Reference architecture for the Batch Messaging and Adobe Experience Platform integration pattern" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br> 

## Prerequisites

* Customer must be provisioned for Experience Cloud with a valid IMS Org 
* Adobe Experience Platform and [!DNL Campaign] are recommended to be provisioned in the same IMS Org for single login URL
* Customer must be provisioned V8 instance of [!DNL Campaign]
* Customer must be eligible and have access for RTCDP, Sources, Destinations.
* Adobe [!DNL Campaign] product context must exist

<br>

## Implementation steps

Refer to the following documentation on configuring the Campaign v8 source connector to Adobe Experience Platform and the Real-time Customer Data Platform destination connector to Campaign v8.
[Campaign and AEP Connectors](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/ac-aep.html?lang=en)

## Guardrails

### Adobe Campaign

* Refer to the Campaign source connector documentation - [Campaign Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/adobe-applications/campaign.html?lang=en)
* Only supports Adobe Campaign single organizational unit deployments


### Experience Platform Real-time Customer Data Platform segment sharing

* Refer to the RTCDP Campaign Destination connector - [RTCDP Campaign Connection](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html)

* See profile and data ingestion guardrails for AEP - [Link](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
