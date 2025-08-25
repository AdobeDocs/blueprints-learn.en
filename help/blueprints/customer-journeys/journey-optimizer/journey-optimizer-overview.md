---
title: "[!DNL Journey Optimizer] - Triggered Messaging and Adobe Experience Platform Blueprint"
description: Execute triggered messages and experiences using Adobe Experience Platform as a central hub of streaming data, customer profiles, and segmentation.
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
---
# [!DNL Journey Optimizer] blueprints

Adobe [!DNL Journey Optimizer] is a cloud-native application built on Adobe Experience Platform that enables real-time and scheduled orchestration of customer journeys across multiple channels. It supports event-driven triggers, audience segmentation, and decisioning services to deliver personalized experiences through email, SMS, push, web, and in-app messaging. It integrates with inbound and outbound systems, allowing for unified audience state management and contextual engagement across the customer lifecycle.

This blueprint outlines the technical capabilities of the application and provides a deep dive into the various architectural components that make up [!DNL Journey Optimizer].

<br>

## Use cases

>[!BEGINTABS]

>[!TAB Journey Use Cases (Event-Driven, Real-Time)]
- **Abandonment Recovery**  
  Trigger personalized messages when a user abandons a cart, form, or session—via email, push, or in-app.

- **Onboarding & Activation Flows**  
  Guide new users through multi-step onboarding journeys based on behavior and milestones.

- **Transactional Messaging**  
  Send real-time confirmations, alerts, or updates (e.g., order shipped, password reset) using event triggers.

- **Behavioral Retargeting**  
  Re-engage users based on browsing history, product views, or app usage patterns.

- **Contextual Upsell/Cross-Sell**  
  Deliver personalized offers based on real-time profile attributes and recent interactions.

>[!TAB Campaign Orchestration Use Cases (Scheduled, Brand-Initiated)]

- **Promotional Campaigns**  
  Launch multi-step, multi-channel campaigns for product launches, seasonal offers, or sales events.

- **Lifecycle Marketing**  
  Automate recurring campaigns like birthday messages, renewal reminders, or loyalty milestones.

- **Audience-Based Funnel Pushes**  
  Segment and push audiences into structured journeys based on business logic or CRM attributes.

- **Newsletter & Content Distribution**  
  Schedule and deliver personalized content to targeted segments across email and mobile.

- **Re-engagement Campaigns**  
  Identify dormant users and reintroduce them into engagement flows based on inactivity thresholds.

>[!ENDTABS]

<br>

## Architecture

<img src="images/ajo-architecture.svg" alt="Reference architecture Journey Optimizer blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Blueprint Scenarios

| Scenario | Description | Technical Considerations |
| :-- | :--- | :--- |
| [3rd-party Messaging](3rd-party-messaging.md) | Demonstrates how Adobe [!DNL Journey Optimizer] can integrate with third-party messaging platforms to orchestrate and deliver personalized customer communications. | <ul><li>The third-party system must support **bearer token authentication**</li><li>**Static IPs are not supported** due to the multi-tenant architecture.</li><li>Be aware of **API rate limits** on third-party systems; customers may need to purchase additional capacity to handle traffic originating from **Adobe Journey Optimizer**.</li><li>**Decision Management** is not supported within message payloads or delivery logic.</li></ul> |

<br>

## Integration Patterns

| Integration | Description | Technical Considerations |
| :-- | :--- | :--- |
| [[!DNL Journey Optimizer] with Adobe Campaign v8](../campaign-v8/ajo-and-campaign-v8.md) | Demonstrates how Adobe [!DNL Journey Optimizer] can orchestrate 1:1, in-the-moment experiences using Real-Time Customer Profile data, while leveraging Adobe Campaign v8's native transactional messaging capabilities to execute final message delivery. | <ul><li>Messaging throughput up to 1,000,000 messages per hour</li><li>No throttling is applied, so use cases must be technically vetted by an Enterprise Architect</li><li>Decision Management is not supported in messages sent by Campaign</li></ul> |

<br>

## Prerequisites

Adobe [!DNL Experience Platform]:

*Schemas and datasets must be configured in the system before you can configure [!DNL Journey Optimizer] data sources
*For XDM Experience Event class-based schemas add 'Orchestration eventID field group when you want to have an event triggered that is not a rule-based event
*For XDM Individual Profile class-based schemas add the 'Profile test details' field group to be able to load test profiles for use with [!DNL Journey Optimizer]

<br>

Email:

*Must have a subdomain ready to be used for message sending
*Subdomain can either be fully delegated to Adobe (recommended) or CNAMEs can be used to point to Adobe-specific DNS servers (custom)
*Google TXT record is needed for each subdomain to ensure good deliverability

<br>

Mobile Push:

*Customer must have a mobile developer available to build the app 
*Adobe Experience Platform Mobile SDK

<br>

## Guardrails

[[!DNL Journey Optimizer] Guardrails Product Link](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

[Guardrails and End to End Latency Guidance](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## Related documentation

*[[!DNL Experience Platform] documentation](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
*[[!DNL Experience Platform] Tags documentation](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
*[[!DNL Experience Platform Mobile SDK] documentation](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
*[[!DNL Journey Optimizer] documentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=en)
*[[!DNL Journey Optimizer] product description](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)