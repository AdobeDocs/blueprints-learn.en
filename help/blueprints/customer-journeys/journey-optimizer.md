---
title: "[!DNL Journey Optimizer] - Triggered Messaging and Adobe Experience Platform Blueprint"
description: Execute triggered messages and experiences using Adobe Experience Platform as a central hub of streaming data, customer profiles, and segmentation.
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
---
# [!DNL Journey Optimizer] blueprints

Adobe [!DNL Journey Optimizer] is a purpose built system for marketing teams to react in real-time to customer behaviors and meet them where they are at. Data management capabilities have been moved to the Adobe [!DNL Experience Platform] allowing marketing teams to focus on what they do best: which is creating world class customer journey's and personalized conversations.

This blueprint outlines the technical capabilities of the application and provides a deep dive into the various architectural components that make up [!DNL Journey Optimizer]. 

## Use cases

* Triggered messages
* Welcome and registration confirmations
* Shopping cart and application form abandons
* Location triggered messages
* In-stadium experiences
* Travel and hospitality pre-arrival and stay experiences

## Architecture

<img src="assets/ajo-architecture.svg" alt="Reference architecture Journey Optimizer blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Blueprint scenarios

| Scenario | Description | Capabilities |
| :-- | :--- | :--- |
| [3rd-party Messaging](3rd-party-messaging.md) | Demonstrates how Adobe [!DNL Journey Optimizer] can be utilized with 3rd party messaging systems to orchestrate and send personalized communications | Deliver 1:1 in the moment personalized communications to customers as they interact with your brand or company<br><br>Considerations:<br><ul><li>3rd party system has to support bearer tokens for authentication</li><li>No support for static IPs due to multi-tenant architecture</li><li>Be aware of architectural constraints on 3rd party system when it comes to API calls per second.  May be a need for the customer to buy additional volume from the 3rd party vendor to support volume coming from [!DNL Journey Optimizer]</li><li>Does not support Decision Management in messages or payloads</li></ul> |

<br>

## Integration patterns

| Integration | Description | Capabilities |
| :-- | :--- | :--- |
| [[!DNL Journey Optimizer] with Adobe Campaign](ajo-and-campaign.md) | Shows how you can use Adobe [!DNL Journey Optimizer] to orchestrate 1:1 experiences utilizing the Real-Time Customer Profile and leverage the native Adobe Campaign transactional messaging system to send the message | Leverage the Real-Time Customer Profile and power of [!DNL Journey Optimizer] to orchestrate in the moment experiences while utilizing the native real-time messaging capabilities of Adobe Campaign to do the last mile communication<br><br>Considerations:<br><ul><li>Campaign application must be on either v7 build >21.1 or v8</li><li>Messaging throughput</li><ul><li>Campaign v7 - up to 50k per hour</li><li>Campaign v8 - up to 1M per hour</li><li>Campaign Standard - up to 50k per hour</li></ul><li>No throttling is performed so use cases need technical vetting by an Enterprise Architect</li><li>No support for utilizing Decision Management in message sent by Campaign</li></ul> |

<br>

## Prerequisites

Adobe [!DNL Experience Platform]:

* Schemas and datasets must be configured in the system before you can configure [!DNL Journey Optimizer] data sources
* For Experience Event class-based schemas add 'Orchestration eventID field group when you want to have an event triggered that is not a rule-based event
* For Individual Profile class-based schemas add the 'Profile test details' field group to be able to load test profiles for use with [!DNL Journey Optimizer]

Email:

* Must have a subdomain ready to be used for message sending
* Subdomain can either be fully delegated to Adobe (recommended) or CNAMEs can be used to point to Adobe-specific DNS servers (custom)
* Google TXT record is needed for each subdomain to ensure good deliverability

Mobile Push:

* Customer must have a mobile developer available to build the app 
* Adobe Experience Platform Mobile SDK

## Guardrails

[[!DNL Journey Optimizer] Guardrails Product Link](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

[Guardrails and End to End Latency Guidance](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## Related documentation

* [[!DNL Experience Platform] documentation](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [[!DNL Experience Platform] Tags documentation](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [[!DNL Experience Platform Mobile SDK] documentation](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
* [[!DNL Journey Optimizer] documentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=en)
* [[!DNL Journey Optimizer] product description](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
