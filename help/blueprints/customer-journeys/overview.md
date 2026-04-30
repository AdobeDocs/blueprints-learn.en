---
title: Customer Journey blueprints
description: Deliver individual, just-in-time and orchestrated customer experiences across screens.
solution: Journey Optimizer, Campaign, Experience Platform
exl-id: 273d024f-a220-4336-89f2-e3bffafcdc37
TQID: https://experienceleague.adobe.com/vJUJiLr7je-Pp2daoYoNYipfVBRyaEYNv-XCx9PrjzM
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
    internal-label: Journey Optimizer
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: a37e4ecd-c740-426a-addf-cb1b483c5c5a
    internal-label: Segmentation
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
  - id: d1823595-9241-4128-8a33-e4ac3bf08773
    internal-label: Audiences
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5520579-b31f-4df7-9281-f0d9f91e2edc
    internal-label: Customer engagement
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
    internal-label: Data integration
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
---
# Customer Journey blueprints

Modern marketing teams require platforms that can support both reactive engagement—responding to individual customer behaviors—and proactive outreach—initiating campaigns that guide audiences into conversion funnels. These use cases span channels like email, SMS, push, and increasingly, web and in-app experiences.

Adobe Journey Optimizer and Adobe Campaign v8 both support two foundational models for customer engagement:

- Customer-triggered journeys: Event-driven, real-time orchestration based on individual behaviors and signals.
- Brand-initiated campaigns: Strategically timed pushes that introduce audiences into engagement funnels based on segmentation or business logic.

Both solutions enable outbound communication across traditional and digital channels. AJO additionally supports integration with inbound channels (e.g. web and mobile apps) through audience state sharing and decisioning services, allowing for unified cross-channel personalization.

The selection between these tools depends on architectural considerations such as latency tolerance, channel requirements, data integration strategy, and scalability.

<br>

| Blueprint | Description | Architecture |
|---|---|:---:|
| **[Adobe Journey Optimizer](journey-optimizer/journey-optimizer-overview.md)** | Combines event-driven, 1:1 profile orchestration, with audience-based brand communications across multiple channels like email, sms, web, push, in-app messaging, desktop, etc. | <img src="journey-optimizer/images/ajo-architecture.svg" alt="Reference architecture for Journey Optimizer Blueprint" style="width:75%; border:1px solid #4a4a4a" class="modal-image" /> |
| **[Adobe [!DNL Campaign] v8](campaign-v8/campaign-v8-overview.md)** | Focused on batch-based, multi-channel campaign management, ideal for traditional marketing channels like email, SMS, and direct mail. | <img src="campaign-v8/images/campaign-v8-architecture.svg" alt="Reference architecture for Campaign v8 Blueprint" style="width:75%; border:1px solid #4a4a4a" class="modal-image" /> |

<br>

## Deprecated blueprints

| Blueprint | Architecture |
|---|:---:|
| **[Adobe [!DNL Campaign] v7](campaign-v7/campaign-v7-overview.md)** | <img src="campaign-v7/images/campaign-v7-architecture.svg" alt="Reference architecture for Campaign v7 Blueprint" style="width:50%; border:1px solid #4a4a4a" class="modal-image" /> |