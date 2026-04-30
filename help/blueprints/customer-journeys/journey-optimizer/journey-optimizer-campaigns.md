---
title: "[!DNL Journey Optimizer] - Campaign Orchestration"
description: Enables marketers to coordinate scheduled, audience-based, multi-step marketing communications across outbound messaging channels.
solution: Journey Optimizer
exl-id: a8ff16f8-146d-4e1f-9bd0-9eda6af0c69b
TQID: https://experienceleague.adobe.com/aPDagEC1zZdi-Bz29fFf6g5Uy8v4qMPhDA47Cdwl-Sw
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
    internal-label: Journey Optimizer
feature_v2:
  - id: a653cc2e-bc85-4353-a306-399e5b247978
    internal-label: Journey Optimizer campaigns
  - id: d998adac-2f81-400b-a669-d07bb196e4eb
    internal-label: Journeys
  - id: df64005d-8f9a-422e-ba4d-c6f6dc3454b4
    internal-label: Use cases
  - id: fe338112-e2ce-4876-8989-fc4d497613f1
    internal-label: Email
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
---
# [!DNL Journey Optimizer] - Campaign Orchestration Blueprint

>[!TIP]
>This blueprint is also available as a [use case pattern](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) under Campaign Management & Orchestration.

AJO Campaign Orchestration enables marketers to design and execute scheduled, audience-based, multi-step communications across outbound channels like email, SMS, push and direct mail. Unlike AJO Journeys, which react to individual customer behaviors using real-time data from the Real-Time Customer Profile, campaigns are coordinated marketing efforts that target audiences at planned intervals. Together, campaigns and journeys offer complementary approaches—campaigns drive brand engagement strategies, while journeys deliver personalized, responsive experiences.

<br>

## Architecture

<img src="images/ajo-campaigns-architecture.svg" alt="Reference architecture Adobe Journey Optimizer Campaign Orchestration Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

### Message Execution Architecture

<img src="images/ajo-campaigns-message-sending-architecture.png" alt="Reference architecture Adobe Journey Optimizer Campaign Orchestration Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

### Relational Store - Data Ingestion Latency

<img src="images/ajo-campaigns-data-ingestion-architecture.png" alt="Reference architecture Adobe Journey Optimizer Campaign Orchestration Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Architectural Considerations for Journeys

- **Data Architecture**: AJO Campaign Orchestration utilizes a relational database underneath for audience building and orchestration
- **Audience Portal Integration**: natively integrated with the Audience Portal within the Real-Time Customer Profile to both read from existing audiences and save new audiences to when building campaigns
- **On-demand Audience Creation**: build, evaluate and execute an audience immediately for urgent marketing use cases
- **Real-Time Customer Profile Integration:** source of truth for consent and communication history; supports 'skinny profile' design for personalization
- **Multi-entity Message Sending:** ability to send multiple messages per profile in a single delivery (e.g. send one message per reservation to the customer email address)
- **Multi-entity Segmentation**: start building an audience from any entity within the relational store (i.e. product, inventory, plan, etc.)

<br>

## Guardrails

[Orchestrated Campaigns Product Link](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/guardrails)

[Guardrails and End to End Latency Guidance](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails)

<br>

## Related documentation

- [[!DNL Journey Optimizer] Orchestrated Campaigns](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/orchestrated-campaigns-landing-page.html)
- [[!DNL Experience Platform] documentation](https://experienceleague.adobe.com/docs/experience-platform.html)
- [[!DNL Experience Platform] Tags documentation](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)
- [[!DNL Experience Platform Mobile SDK] documentation](https://experienceleague.adobe.com/docs/mobile.html)
- [[!DNL Journey Optimizer] documentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html)
- [[!DNL Journey Optimizer] product description](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
