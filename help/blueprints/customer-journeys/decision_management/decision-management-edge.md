---
title: Decision Management on the Edge blueprint
description: Deliver personalized offers to consumers across channels including in real-time web and mobile experiences.
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
---
# Journey Optimizer - [!DNL Decision Management] on the Edge blueprint

Adobe [!DNL Decision Management] is a service provided as part of Adobe Journey Optimizer. This blueprint outlines the use cases and technical capabilities of the application and provides a deep dive into the various architectural components and considerations that make up Decision Management.

>[!MORELIKETHIS]
>
>To learn more about Decision Management, see the [blueprint overview](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=en) and the  [product documentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html).

Decision Management can be deployed in one of two ways. The first is via the Adobe Experience Platform Hub, which is a single data center architecture. In the "hub" approach offers are executed, personalized, and delivered in second latency. Thus the hub architecture is best suited for customer experience that do not demand sub-second latency, examples include offer decisions which are provided for kiosks or agent assisted experiences such as in call centers or in person interactions. 

The second approach is via the Experience Edge Network, which is a globally distributed geographically located infrastructure to serve fast sub-second and millisecond experiences. The end consumer experience being executed by the edge infrastructure closest to the consumers geo-location to minimize latency. Decision Management on the Edge is designed to serve real-time consumer experiences. These include experiences such as web or mobile inbound personalization requests. 

This blueprint will cover the specifics of Decision Management on the Edge.

To learn more about Decision Management on the hub refer to the [Decision Management on the hub](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-hub.html?lang=en) blueprint.

## Use cases for Decision Management on the edge

* Streaming use cases where profile context latency is strict below 15 minute latency and decision management execution is sub-second.
* Online personalization via web or mobile inbound experiences.
* Cross channel journey execution - offer consistency across web, mobile, email, and other interaction channels through Adobe Journey Optimizer.

<br>

## Architecture

<img src="../assets/offers_edge.svg" alt="Reference architecture Decision Management on the edge blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Integration patterns

| Integration | Description |
| :-- | :--- |
|[Decision Management with Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html)| Decision Management can be integrated with Adobe Target such that offers can be tested and delivered as Target experiences.|

## Prerequisites

Adobe Experience Platform

* Schemas and datasets must be configured in the system before you can configure Journey Optimizer data sources
* For Experience Event class-based schemas add 'Orchestration eventID field group when you want to have an event triggered that is not a rule-based event
* For Individual Profile class-based schemas add the 'Profile test details' field group to be able to load test profiles for use with Journey Optimizer

<br>

## Guardrails

* For Journey Optimizer guardrails refer to the following [Journey Optimizer Guardrails](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html).

* For Decision Management guardrails refer to the following [Decision Management Product Description](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html).

[Guardrails and End to End Latency Guidance](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)


## Implementation patterns

* Use the Web or Mobile SDK for deployment on websites and mobile applications to implement Decision Management where the SDK deployed.
  * [Web/Mobile SDK Blueprint](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/websdk.html?lang=en)
  * [Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/offer-decisioning/offer-decisioning-overview.html)
  * [MobileSDK](https://aep-sdks.gitbook.io/docs/)

Or

* For an API server to server based implementation use the Edge Network Service API for direct server to server implementation of Decision Management.
  * [Edge Network Server API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/deliver-offers.html)

<br>

## Implementation steps

### Adobe Experience Platform

#### Schema/datasets

1. [Configure individual profile, experience event, and multi-entity schemas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, based on customer-supplied data.
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

1. [Ingest data into Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) using streaming APIs & source connectors.

## Related documentation

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html)
* [Adobe Journey Optimizer Decision Management](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html) 
* [Adobe Journey Optimizer Product Description](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe Decision Management Product Description](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
