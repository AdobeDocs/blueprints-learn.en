---
title: Real-Time CDP with [!DNL Campaign] v7 and Campaign Standard integration pattern
description: Showcases how the Adobe Experience Platform and its Real-Time Customer Profile and centralized segmentation tool can be utilized with Adobe [!DNL Campaign] to deliver personalized conversations.
solution: Real-Time Customer Data Platform, [!DNL Campaign]
exl-id: a15e8304-2763-42fc-9978-11f2482ea8b8
---
# [!DNL Real-Time Customer Data Platform] with [!DNL Campaign] integration pattern

Showcases how the Adobe [!DNL Experience Platform] and its Real-Time Customer Profile and centralized segmentation tool can be utilized with Adobe [!DNL Campaign] to deliver personalized conversations.

## Applications

* Adobe [!DNL Experience Platform Real-Time Customer Data Platform]
* Adobe [!DNL Campaign] v7 or [!DNL Campaign Standard]

## Architecture

<img src="assets/rtcdp-campaign-architecture.svg" alt="Reference architecture for the Batch Messaging and Adobe Experience Platform integration pattern" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Prerequisites

* Experience Platform and [!DNL Campaign] are recommended to be provisioned in the same IMS Org and be utilizing Adobe Admin Console for user access. This also ensures that customers can utilize the solution switcher from within the marketing UI

## Guardrails

The following sections describe the guardrails for this integration.

### Adobe [!DNL Campaign]

* Only supports Adobe [!DNL Campaign] single organizational unit deployments
* Adobe [!DNL Campaign] is source of truth for all active profiles meaning profiles must exist in Adobe [!DNL Campaign] and new profiles should not be created based on Experience Platform segments.
* [!DNL Campaign] export workflows to run at most every 4hrs
* XDM schema and datasets for Adobe [!DNL Campaign] broadLog, trackingLogs and non-deliverable addresses are not out of the box and must be designed and built

### Real-Time Customer Data Platform segment sharing

* Refer to the RTCDP [!DNL Campaign] Destination connector - [RTCDP Campaign Connection](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html)

* See [Default guardrails for [!DNL Real-Time Customer Profile Data] and segmentation](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

## Implementation steps

The following sections describe implementations steps for each application.

### Adobe Experience Platform

#### Schema/datasets

1. [Configure individual profile, experience event, and multi-entity schemas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, based on customer-supplied data.
1. Create Adobe [!DNL Campaign] schemas for broadLog, trackingLog, non-deliverable addresses, and profile preferences (optional).
1. [Create datasets](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) in Experience Platform for data to be ingested.
1. [Add data usage labels](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html) in Experience Platform to the dataset for governance.
1. [Create policies](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html) that enforce governance on destinations.

#### Profile/identity

1. [Create any customer-specific namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Add identities to schemas](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Enable the schemas and datasets for Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Set up merge policies](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) for differing views of [!UICONTROL Real-time Customer Profile] (optional).
1. Create segments for Adobe [!DNL Campaign] usage.

#### Sources/destinations

1. [Experience Platform and [!DNL Campaign] Standard Sources and Desintations](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html)
1. [Experience Platform and [!DNL Campaign] v7 Sources and Desintations](https://experienceleague.adobe.com/docs/campaign-classic/using/integrating-with-adobe-experience-cloud/aep-sources-destinations/get-started-sources-destinations.html)
1. [Ingest data into Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) using streaming APIs & source connectors.
1. Configure [!DNL Azure] blob storage destination for use with Adobe [!DNL Campaign].

#### Adobe [!DNL Campaign]

1. Configure schemas for profile, lookup data, and relevant delivery personalization data.
    
>[!IMPORTANT]
>
>It's critical to understand at this point what the data model is within Experience Platform for profile and event data so you know what data will be required in Adobe [!DNL Campaign].
    
#### Import workflows

1. Load and ingest simplified profile data onto Adobe [!DNL Campaign] sFTP.
1. Load and ingest orchestration and messaging personalization data onto Adobe [!DNL Campaign] sFTP.
1. Ingest Experience Platform segments from [!DNL Azure] blob via workflows.

#### Export workflows

1.  Send Adobe [!DNL Campaign] logs back to Experience Platform via workflows every four hours (broadLog, trackingLog, non-deliverable addresses).
1.  Send profile preferences back to Experience Platform via consulting-built workflows every four hours (optional).

### Mobile push configuration

* Two supported approaches for integrating with mobile devices for push notifications:
  * Experience Platform Mobile SDK
  * [!DNL Campaign] Mobile SDK
* Experience Platform Mobile SDK route:
  * Leverage Adobe Tags and the [!DNL Campaign Classic] extension for setting up your integration with the Experience Platform Mobile SDK
  * Need a working knowledge of Adobe Tags and data collection
  * Need mobile development experience with push notifications in both Android and iOS to deploy the SDK, integrate with FCM (Android) and APNS (iOS) to get push token, configure your app to receive push notifications and handle push interactions
* [!DNL Campaign] Mobile SDK
  * See the [Campaign Classic SDK documentation](https://developer.adobe.com/client-sdks/solution/adobe-campaign-classic/)

>[!IMPORTANT]
>
>If you deploy the [!DNL Campaign] SDK and are working with other Experience Cloud applications they will require the use of the Experience Platform Mobile SDK for data collection. This will create duplicate client side calls on the device.

## Related documentation

* [Adobe [!DNL Experience Platform] documentation](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [[!DNL Campaign Classic] documentation](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [[!DNL Campaign Standard] documentation](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [[!DNL Experience Platform] Launch documentation](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [[!DNL Experience Platform] Mobile SDK documentation](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
