---
title: Decision Management on the Edge blueprint
description: Deliver personalized offers to consumers across channels including in real-time web and mobile experiences.
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
TQID: https://experienceleague.adobe.com/SwjKOJIL5WidXtVuLCNbBpNz3mhe0EvD93IhMfxI1oY
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
    internal-label: Journey Optimizer
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: d998adac-2f81-400b-a669-d07bb196e4eb
    internal-label: Journeys
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: df64005d-8f9a-422e-ba4d-c6f6dc3454b4
    internal-label: Use cases
  - id: fe338112-e2ce-4876-8989-fc4d497613f1
    internal-label: Email
subfeature_v2:
  - id: e5ae22e3-a3b0-46ed-804f-9abf1bbe3e74
    internal-label: Guardrails
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
  - id: c18d9e03-ac7d-4811-9c92-3e92ddc70ade
    internal-label: Mobile experience
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
---
# Journey Optimizer - [!DNL Decision Management] on the Edge Blueprint

[!DNL Decision Management] is a service provided as part of [!DNL Journey Optimizer]. This blueprint outlines the use cases and technical capabilities of the application and provides a deep dive into the various architectural components and considerations that make up Decision Management.

>[!MORELIKETHIS]
>
>To learn more about [!DNL Decision Management], see the [blueprint overview](decision-management-overview.md) or visit the [product documentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html).

[!DNL Decision Management] can be deployed in one of two ways. The first is via the [!DNL Experience Platform] Hub, which is a single data center architecture. In the "hub" approach offers are executed, personalized, and delivered in second latency. Thus the hub architecture is best suited for customer experience that do not demand sub-second latency, examples include offer decisions which are provided for kiosks or agent assisted experiences such as in call centers or in person interactions. 

The second approach is via the Experience Platform [!DNL Edge Network], which is a globally distributed geographically located infrastructure to serve fast sub-second and millisecond experiences. The end consumer experience being executed by the Edge infrastructure closest to the consumers geo-location to minimize latency. [!DNL Decision Management] on the Edge is designed to serve real-time consumer experiences. These include experiences such as web or mobile inbound personalization requests. 

This blueprint will cover the specifics of Decision Management on the Edge.

To learn more about Decision Management on the hub refer to the [Decision Management on the hub](decision-management-hub.md) blueprint.

## Use cases for Decision Management on the edge

* Streaming use cases where profile context latency is strict below 15 minute latency and decision management execution is sub-second.
* Online personalization via web or mobile inbound experiences.
* Cross channel journey execution - offer consistency across web, mobile, email, and other interaction channels through Adobe Journey Optimizer.

## Architecture

<img src="images/offers_edge.svg" alt="Reference architecture Decision Management on the edge blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Integration patterns

| Integration | Description |
| :-- | :--- |
|[Decision Management with Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html)| Decision Management can be integrated with Adobe Target such that offers can be tested and delivered as Target experiences.|

## Guardrails

* For Journey Optimizer guardrails refer to the following [Journey Optimizer Guardrails](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html).

* For Decision Management guardrails refer to the following [Decision Management Product Description](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html).

[Guardrails and End to End Latency Guidance](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html)

## Related documentation

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html)
* [Adobe Journey Optimizer Decision Management](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html) 
* [Adobe Journey Optimizer Product Description](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe Decision Management Product Description](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
