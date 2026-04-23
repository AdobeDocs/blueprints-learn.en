---
title: "[!DNL Journey Optimizer] - Triggered Messaging and Adobe Experience Platform Blueprint"
description: Execute triggered messages and experiences using Adobe Experience Platform as a central hub of streaming data, customer profiles, and segmentation.
solution: Journey Optimizer
exl-id: 70573eb9-cd69-4fe6-b2ae-dae81665a308
TQID: https://experienceleague.adobe.com/MuodOvJ52G9lmUAmsuj06q1aTXkRg7W0Bj6nxLp96N8
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
    internal-label: Journey Optimizer
feature_v2:
  - id: a653cc2e-bc85-4353-a306-399e5b247978
    internal-label: Journey Optimizer campaigns
  - id: d998adac-2f81-400b-a669-d07bb196e4eb
    internal-label: Journeys
  - id: fe338112-e2ce-4876-8989-fc4d497613f1
    internal-label: Email
  - id: fe96aceb-8194-4a8a-a6b0-75302d02804d
    internal-label: Integrations
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
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
    internal-label: Customer profiles
---
# [!DNL Journey Optimizer] - Journeys Blueprint

Adobe Journey Optimizer Journeys are real-time, event-driven workflows that deliver personalized, multi-step experiences based on individual customer behaviors. They support a wide range of channels—including email, SMS, push notifications, in-app messaging, code-based experiences and custom API-based integrations allowing brands to engage customers contextually across their preferred touchpoints.

<br>

## Architecture

<img src="images/ajo-journeys-architecture.svg" alt="Reference architecture Adobe Journey Optimizer - Journeys Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Architectural Considerations for Journeys

- **Profile Freshness**: AJO Journeys rely on real-time updates to the customer profile. Ensure that data sources feeding into Adobe Experience Platform (AEP) are configured for low-latency ingestion to maintain profile accuracy.
- **Scalable Event Processing:** Ensure that infrastructure can handle high volumes of journey triggers and message delivery.
- **Modular Integration:** Design APIs and custom actions to connect AJO with external systems for dynamic personalization.
- **Identity Resolution**: Accurate stitching of customer identities across devices and channels is critical. Misaligned identities can lead to broken or misdirected journeys.
- **Segment Qualification Timing**: Audience-based journeys depend on segment membership. Understand how often segments are evaluated and how that timing affects journey entry and personalization.
- **Journey Entry Conditions**: Profiles must meet specific conditions to enter a journey. These conditions should be carefully designed to avoid unintended exclusions or overlaps.
- **Audience Evaluation & Latency**: Read Audience steps depend on segment evaluations within Adobe Experience Platform, which may not occur in real time. Architect journeys with awareness of evaluation frequency and latency to avoid delays in audience qualification and ensure timely personalization.

<br>

## Guardrails

[[!DNL Journey Optimizer] Guardrails Product Link](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[Guardrails and End to End Latency Guidance](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

<br>

## Related documentation

- [[!DNL Experience Platform] documentation](https://experienceleague.adobe.com/docs/experience-platform.html)
- [[!DNL Experience Platform] Tags documentation](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)
- [[!DNL Experience Platform Mobile SDK] documentation](https://experienceleague.adobe.com/docs/mobile.html)
- [[!DNL Journey Optimizer] documentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html)
- [[!DNL Journey Optimizer] product description](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
