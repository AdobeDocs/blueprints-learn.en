---
title: "[!DNL Journey Optimizer] - Journeys Blueprint"
description: Execute triggered messages and experiences using Adobe Experience Platform as a central hub of streaming data, customer profiles, and segmentation.
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
TQID: https://experienceleague.adobe.com/Rfi-0QD8bQpD-Zp2CDpzqxrge0yVs2CFt5mDKibNogI
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
subfeature_v2:
  - id: fa683eda-48de-4558-af32-2673edcd44fe
    internal-label: Events
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: addf009e-030a-4310-8534-776a3e62ed48
    internal-label: Customer lifecycle
  - id: b5520579-b31f-4df7-9281-f0d9f91e2edc
    internal-label: Customer engagement
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
  - id: d00e9f03-e50b-4162-b143-0c0817c937c2
    internal-label: Customer journeys
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
    internal-label: Customer profiles
  - id: ff2b9b37-92e0-45fc-b853-379d44c08c89
    internal-label: Audience segmentation
---
# [!DNL Journey Optimizer] blueprints

Adobe [!DNL Journey Optimizer] is a cloud-native application built on Adobe Experience Platform that enables real-time and scheduled orchestration of customer journeys across multiple channels. It supports event-driven triggers, audience segmentation, and decisioning services to deliver personalized experiences through email, SMS, push, web, and in-app messaging. It integrates with inbound and outbound systems, allowing for unified audience state management and contextual engagement across the customer lifecycle.

This blueprint outlines the technical capabilities of the application and provides a deep dive into the various architectural components that make up [!DNL Journey Optimizer].

<br>

## Use cases

>[!BEGINTABS]
>[!TAB Journey (Event-Driven, Real-Time)]

- **Abandonment Recovery:** Trigger personalized messages when a user abandons a cart, form, or session—via email, push, or in-app.
- **New User Sign-up:** Engage new users immediately after they register with new account preferences, relevant promotions or benefits
- **Transactional Messaging:** Send real-time confirmations, alerts, or updates (e.g., order shipped, password reset) using event triggers.
- **Contextual Targeting:** Communicate with users in-the-moment based on their signals and location to help guide and direct their experience
- **Contextual Upsell/Cross-Sell:** Deliver personalized offers based on real-time profile attributes and recent interactions.

>[!TAB Campaign Orchestration (Scheduled, Brand-Initiated)]

- **Promotional Campaigns**: Launch multi-step, multi-channel campaigns for product launches, seasonal offers, or sales events.
- **Lifecycle Marketing**: Automate recurring campaigns like birthday messages, renewal reminders, or loyalty milestones.
- **Audience-Based Funnel Pushes**: Segment and push audiences into structured campaigns based on business logic or CRM attributes.
- **Newsletter & Content Distribution**: Schedule and deliver personalized content to targeted audiences across email and mobile.
- **Re-engagement Campaigns**: Identify dormant users and reintroduce them into engagement flows based on inactivity thresholds.

>[!ENDTABS]

<br>

## Architecture

<img src="images/ajo-architecture.svg" alt="Reference architecture Adobe Journey Optimizer Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Blueprint Scenarios

| Scenario | Description |
| :-- | :-- |
| [Journeys](journey-optimizer-journeys.md) | AJO Journeys in Adobe Journey Optimizer are automated, personalized customer experiences triggered by real-time events or audience segments, allowing marketers to deliver relevant messages across channels like email, SMS, and push notifications. |
| [Campaign Orchestration](journey-optimizer-campaigns.md) | AJO Campaign Orchestration enables marketers to design and execute personalized, cross-channel campaigns using real-time data and audience insights. It supports dynamic targeting, message delivery, and journey logic to optimize customer engagement across email, SMS, push, and custom channels. |

<br>

## Integration Patterns

| Integration | Description | Technical Considerations |
| :-- | :-- | :-- |
| [3rd-party Messaging](3rd-party-messaging.md) | Demonstrates how Adobe [!DNL Journey Optimizer] can integrate with third-party messaging platforms to orchestrate and deliver personalized customer communications. | <ul><li>The third-party system must support **bearer token authentication**</li><li>**Static IPs are not supported** due to the multi-tenant architecture.</li><li>Be aware of **API rate limits** on third-party systems; customers may need to purchase additional capacity to handle traffic originating from **Adobe Journey Optimizer**.</li><li>**Decision Management** is not supported within message payloads or delivery logic.</li></ul> |
| [[!DNL Journey Optimizer] with Adobe Campaign v8](../campaign-v8/ajo-and-campaign-v8.md) | Demonstrates how Adobe [!DNL Journey Optimizer] can integrate with Adobe Campaign v8's transactional messaging capabilities to execute final message delivery. | <ul><li>There is no throttling of messages. Cap of 4,000 messages per 5 minutes.</li><li>Only supports event-initiated journey's</li><li>Decision Management is not supported in messages sent by Campaign</li></ul> |

<br>

## Prerequisites

Adobe [!DNL Experience Platform]:

- Schemas and datasets must be configured in the system before you can configure [!DNL Journey Optimizer] data sources
- For XDM Experience Event class-based schemas, add 'Orchestration eventID field group when you want to have an event triggered that is not a rule-based event
- For XDM Individual Profile class-based schemas, add the 'Profile test details' field group to be able to load test profiles for use with [!DNL Journey Optimizer]

<br>

Email:

- Must have a subdomain ready to be used for message sending
- Subdomain can either be fully delegated to Adobe (recommended) or CNAMEs can be used to point to Adobe-specific DNS servers (custom)
- Google TXT record is needed for each subdomain to ensure good deliverability

<br>

Mobile Push:

- Customer must have a mobile developer available to build the app 
- Adobe Experience Platform Mobile SDK

<br>

## Guardrails

[[!DNL Journey Optimizer] Guardrails Product Link](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[Guardrails and End to End Latency Guidance](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## Related documentation

- [[!DNL Experience Platform] documentation](https://experienceleague.adobe.com/docs/experience-platform.html)
- [[!DNL Experience Platform] Tags documentation](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)
- [[!DNL Experience Platform Mobile SDK] documentation](https://experienceleague.adobe.com/docs/mobile.html)
- [[!DNL Journey Optimizer] documentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html)
- [[!DNL Journey Optimizer] product description](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
