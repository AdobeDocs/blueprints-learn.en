---
title: "[!DNL Journey Optimizer] - Campaign Orchestration"
description: Enables marketers to coordinate scheduled, audience-based, multi-step marketing communications across outbound messaging channels.
solution: Journey Optimizer
---
# [!DNL Journey Optimizer] - Campaign Orchestrataion Blueprint

AJO Campaign Orchestration enables marketers to design and execute scheduled, audience-based, multi-step communications across outbound channels like email, sms, push and direct mail. Unlike AJO Journeys, which react to individual customer behaviors using real-time data from the Real-Time Customer Profile, campaigns are coordinated marketing efforts that target audiences at planned intervals. Together, campaigns and journeys offer complementary approaches—campaigns drive brand engagement strategies, while journeys deliver personalized, responsive experiences.

<br>

## Architecture

<img src="images/ajo-campaigns-architecture.svg" alt="Reference architecture Adobe Journey Optimizer Campaign Orchestration Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Architectural Considerations for Journeys

- **Data Architecture**: AJO Campaign Orchestration utilizes a relational database underneath for audience building and orchestration
- **Audience Portal Integration**: natively integrated with the Audience Portal within the Real-Time Customer Profile to both read existing audiences from and save new audiences to when building campaigns
- **On-demand Audience Creation**: build, evaluate and execute an audience immediately for urgent marketing use cases
- **Real-Time Customer Profile Integration:** the Real-Time Customer Profile remains the source of truth for consent and communication history and therefore should always be considered during design to hold a "skinny profile" (i.e. the basic traits of a person needed for personalization)
- **Multi-entity Message Sending:** ability to send multiple messages per profile in a single delivery (e.g. send one message per reservation to the customer email address)
- **Multi-entity Segmentation**: start building an audience from any entity within the relational store (i.e. product, inventory, plan, etc.)

<br>

## Guardrails

[[!DNL Journey Optimizer] Guardrails Product Link](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

[Guardrails and End to End Latency Guidance](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

<br>

## Related documentation

- [[!DNL Experience Platform] documentation](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
- [[!DNL Experience Platform] Tags documentation](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
- [[!DNL Experience Platform Mobile SDK] documentation](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
- [[!DNL Journey Optimizer] documentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=en)
- [[!DNL Journey Optimizer] product description](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)