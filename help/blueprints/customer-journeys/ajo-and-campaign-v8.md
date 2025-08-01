---
title: Journey Optimizer with Adobe Campaign v8 blueprint
description: Demonstrates how Adobe Journey Optimizer can be used with Adobe Campaign to natively send messages by utilizing the real-time messaging server in Campaign
solution: Journey Optimizer, Campaign, Campaign v8, Campaign v8 Client Console
version: Campaign v8, Campaign v8 Client Console
exl-id: 447a1b60-f217-4295-a0df-32292c4742b0
---
# Journey Optimizer with Adobe Campaign v8 blueprint 

Demonstrates how Adobe [!DNL Journey Optimizer] can be used with Adobe [!DNL Campaign] to natively send messages by utilizing the real-time messaging server in [!DNL Campaign].

## Architecture

<img src="assets/ajo-campaign-architecture.svg" alt="Reference architecture Journey Optimizer blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

>[!IMPORTANT]
>Using both Journey Optimizer and Campaign to send messages independently of each other is possible but has some technical considerations that need to be thought through. If you wish to pursue this route please work with your Pre-Sales Enterprise Architect to ensure that you have an understanding of what will be required to support the implementation.

## Prerequisites

Review the following prerequisites for each application.

### Adobe Experience Platform

* Schemas and datasets must be configured in the system before you can configure Journey Optimizer data sources
* For Experience Event class-based schemas add 'Orchestration eventID field group when you want to have an event triggered that is not a rule-based event
* For Individual Profile class-based schemas add the 'Profile test details' field group to be able to load test profiles for use with Journey Optimizer
* Journey Optimizer and Campaign are provisioned in the same IMS Org

### Campaign v8

* Execution instance of the real-time messaging service (i.e Message Center) must be hosted by Adobe Managed Cloud Services
* All message authoring is done within the Campaign instance itself

## Guardrails

* [Journey Optimizer Guardrails product limitations](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

* [Guardrails and end-to-end latency guidance](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html)

## Implementation steps

Follow the implementations for each application described below.

### Adobe Experience Platform

#### Schema/datasets

1. [Configure individual profile, experience event, and multi-entity schemas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, based on customer-supplied data.
1. (Optional) Create Experience Event class-based schemas for Adobe Campaign broadLog, trackingLog and non-deliverable addresses tables.
1. [Create datasets](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) in Experience Platform for data to be ingested.
1. [Add data usage labels](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html) in Experience Platform to the dataset for governance.
1. [Create policies](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html) that enforce governance on destinations.

#### Profile/identity

1. [Create any customer-specific namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Add identities to schemas](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Enable the schemas and datasets for Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Set up merge policies](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) for differing views of [!UICONTROL Real-time Customer Profile] (optional).
1. Create segments for Journey usage.

#### Sources/destinations

1. [Ingest data into [!DNL Experience Platform]](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) using streaming APIs & source connectors.

### Journey Optimizer

1. Configure your [!DNL Experience Platform] datasource and determine what fields should be cached as part of the profileStreaming data used to initiate a customer journey must be configured within Journey Optimizer first to get an orchestration ID. This orchestration ID is then supplied to the developer to use with ingestion.
1. Configure external data sources.
1. Configure custom actions for Campaign instance.

### Campaign v8

* Messaging templates need to be configured with appropriate personalization context.
* For [!DNL Campaign] standard: Export workflows need to configured to export the transactional messaging logs back to the Experience Platform. The recommendation is to run at most every four hours.
* For [!DNL Campaign] v8.4 it is possible to leverage Adobe [!DNL Campaign] Managed Services Source Connector in Experience Platform to sync delivery and tracking events from Campaign into Experience Platform. Refer to the [Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html) documentation for details.

### Mobile push configuration (optional)

1. Implement [!DNL Experience Platform] Mobile SDK to collect push tokens and login information to tie back to known customer profiles.
1. Leverage Adobe Tags and create a mobile property with the following extension:
    * Adobe [!DNL Journey Optimizer] | Adobe [!DNL Campaign Classic] | Adobe [!DNL Campaign Standard]
    * Adobe [!DNL Experience Platform] [!DNL Edge Network]
    * Identity for [!DNL Edge Network]
    * Mobile Core
1. Ensure you have a dedicated datastream for mobile app deployments vs. web deployments.
1. For more information follow the [Adobe Journey Optimizer Mobile Guide](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer/push-notification/).

    >[!IMPORTANT]
    >Mobile tokens may need to be collected in both Journey Optimizer and Campaign if there is desire send real-time communications via Journey Optimizer and batch push notifications via Campaign. Campaign v8 requires the exclusive use of the Campaign SDK for capturing push tokens.

## Related documentation

* [Journey Optimizer documentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=en)
* [Journey Optimizer Product Description](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=en)
