---
title: Audience and Profile Activation to File and Enterprise Streaming Destinations blueprint
description: Audience and Profile Activation to Enterprise Destinations
solution: Real-Time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5
---
# Audience and Profile Activation to File and Enterprise Streaming Destinations blueprint

Share profile and audience changes and events in streaming or batch from [!UICONTROL Real-time Customer Data Platform] to enterprise data stores and applications. These profile and audience events can be used to initiate a sales or support action to the customer such as following up on an abandoned application process or webinar registration or to update enterprise applications with the latest customer attributes and intelligence from [!UICONTROL Real-time Customer Data Platform].

## Use cases

* Profile and audience activation to cloud storage destinations, or streaming destinations for enterprise tracking, storage, analysis, and activation of customer data and insights. 

## Applications

* Adobe Experience Platform Activation

## Architecture

<img src="assets/known_activation.svg" alt="Reference architecture for the Enterprise Activation Scenario" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />


## Guardrails

[Refer to the guardrails as outlined on the guardrails page.](../experience-platform/deployment/guardrails.md)  

## Implementation steps

1. [Create schemas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) for data to be ingested.
1. [Create datasets](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) for data to be ingested.
1. [Configure the correct identities and identity namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html) on the schema to be sure that ingested data can stitch into a unified profile.
1. [Enable the schemas and datasets for profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html). 
1. [Ingest data](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) into Experience Platform.
1. [Provision [!UICONTROL Real-time Customer Data Platform] segment sharing](https://www.adobe.com/go/audiences) between Experience Platform and Audience Manager for audiences defined in Experience Platform to be shared to Audience Manager.
1. [Create segments](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html) in Experience Platform. The system automatically determines whether the segment is evaluated as batch or streaming.
1. [Configure destinations](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html) for sharing of profile attributes and audience memberships to desired destinations.

## Related documentation

* [Destinations documentation](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)
* [Cloud storage destinations overview](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [HTTP Destination](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [[!UICONTROL Real-time Customer Data Platform] Product Description](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Profile and segmentation guidelines](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Segmentation documentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)

## Related videos & tutorials

* [[!UICONTROL Real-time Customer Data Platform] overview](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo of [!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Create segments](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
