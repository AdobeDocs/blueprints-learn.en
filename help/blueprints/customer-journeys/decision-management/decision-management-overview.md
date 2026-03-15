---
title: Decision Management blueprints
description: Deliver personalized offers across customer journeys.
solution: Experience Platform, Journey Optimizer
exl-id: 1bc9335c-5321-4d0c-939e-4f402e2e8f51
---
# Journey Optimizer - Decision Management blueprints

Please refer to the following documentation for [Decision Management](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)

Please refer to the following documentation for guardrails related to Decision Management. [Decision Management Guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails#decision-management.html)

Adobe Decision Management is a service provided as part of Adobe Journey Optimizer. This blueprint outlines the use cases and technical capabilities of the application and provides a deep dive into the various architectural components and considerations that make up Decision Management.

Journey Optimizer is used to deliver the best offer and experience to your customers across all touch points at the right time. Decision Management makes personalization easy with a central library of marketing offers and a decision engine that applies rules and constraints to real-time profiles created by Adobe Experience Platform. This allows you to easily send your customers the right offer at the right time.

The Decision Management capability consists in two main components:

* The Centralized Offer Library which is the interface where you create and manage the different elements that compose your offers, and define their rules and constraints.
* The Offer Decision Engine which leverages Adobe Experience Platform data and Real-time Customer profiles, along with the Offer Library, in order to select the right time, customers and channels to which offers will be delivered.

<img src="images/offers_overview.png" alt="Decision Management" style="width:100%; border:1px solid #4a4a4a" />

Decision Management can be deployed in one of two ways, on the edge or via the hub. Each of these methods has a specific set of interfaces and protocols for operating the service as outlined in the respective blueprints referenced below. Additional details can also be obtained in the [Decision Management documentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery-api/decisioning-vs-edge-apis.html).

## Decision Management on the hub

The first is via the Adobe Experience Platform hub, which is a central data center architecture. The hub architecture is best suited for customer experiences that do not demand low latency and high throughput, but do require a fuller view of the customer profile, examples include offer decisions which are provided for kiosks or agent assisted experiences such as in call centers or in person interactions. Offers that are inserted into emails, SMS messages, or push notifications and other outbound campaigns are also powered by the hub approach. To learn more about Decision Management on the hub refer to the [Decision Management on the hub](decision-management-hub.md) blueprint.

* Offer eligibility can operate agains the full real-time customer profile, including all attributes and experience events

### Use cases for Decision Management on the hub

* Personalized offers on kiosks and in store experiences.
* Personalized offers via agent assisted experience such as to call centers or sales intereactions.
* Offers included in email, SMS, or other outbound interactions.
* Cross channel journey execution - offer consistency across web, mobile, email, and other interaction channels through Adobe Journey Optimizer.

### Decision Management on the hub technical considerations

* Access to full real-time customer profile including audience memberships, attributes and experience events.

## Decision Management on the edge

The second approach is via the Experience [!DNL Edge Network], which is a globally distributed geographically located infrastructure to serve fast sub-second and millisecond experiences. The end consumer experience being executed by the edge infrastructure closest to the consumers geo-location to minimize latency. Decision Management on the Edge is designed to serve real-time consumer experiences such as web or mobile inbound personalization requests. To learn more about Decision Management on the Edge refer to the [Decision Management on the edge](decision-management-edge.md) blueprint.

### Use cases for Decision Management on the edge

* Online personalization via web or mobile inbound experiences.
* Cross channel journey execution - offer consistency across web, mobile, email, and other interaction channels through Adobe Journey Optimizer.

### Decision Management on the edge technical considerations

* Access to edge real-time profile. Only edge projected audiences and profile attributes will be available in the profile. 

## Related documentation

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html)
* [Adobe Journey Optimizer Decision Management](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html) 
* [Adobe Journey Optimizer Product Description](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe Decision Management Product Description](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
