---
title: Customer Journey Analytics blueprints
description: Unify and analyze data and customer behaviors from across the customer journey
solution: Customer Journey Analytics
kt: 
thumbnail:
exl-id: 3bb2dada-f4cd-43f7-a0d0-f276510ad224
---
# Customer Journey Analytics blueprints

Customer Journey Analytics shows how brands can unify customer data and behavior from various interaction channels and sources to create a journey-based view of all customer interactions. Reporting and analysis can be performed in the Customer Journey Analytics application service to evaluate and gain insight into customer interaction and behavior patterns. 

A full list of Customer Journey Analytics use cases can be found in the Customer Journey Analytics documentation found here.

## Customer Journey Analytics use cases

[Common Use Cases](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cja-usecases.html?lang=en) include:

* Create and Publish Audiences to Real-time Customer Data Platform
* Top/bottom converting paths
* Channel engagement and conversion 
* Top viewed content
* Top Categories and products
* What campaigns resulted in conversion and increased engagement
* Tool usage analysis to optimize self-service experiences

## Architecture for Customer Journey Analytics

![Architecture diagram](assets/CJA.svg){zoomable="yes"}

Example primary use cases included the following.

| Blueprint | Description |  Experience Cloud Applications |
|---|---|---|
| **[Cross Channel Journey Analysis](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cross-channel.html)**  | <ul><li>Have a single consolidated view of customer behavior across various channels by unifying data from various web, mobile, and offline properties.</li></ul> | <ul><li>Adobe Experience Platform</li><li>Customer Journey Analytics</li><li>Adobe Analytics (optional)</li></ul>|
| **[Publish Audiences to Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html)** | <ul><li>create and publish audiences identified in Customer Journey Analytics (CJA) to Real-time Customer Profile in Adobe Experience Platform for customer targeting and personalization. Ideal for creating audiences using historical data or more refined audiences from granular filtering and computed fields in Customer Journey Analytics.</li></ul> | <ul><li>Real-time Customer Data Platform</li><li>Customer Journey Analytics</li> |
| **[Call Deflection Journey Analysis](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/call-center.html)** | <ul><li>Determine what behaviors are most indicative in resulting in agent assisted calls by bringing Call Center data together with web, mobile, and other interaction data.</li><li>These insights can then be used to optimize the customer experience and reduce the path to agent assisted interactions through optimized self-service content and tooling.  </li></ul> | <ul><li>Adobe Experience Platform</li><li>Customer Journey Analytics</li> |

## Guardrail diagram for Customer Journey Analytics blueprints

* For detailed guardrails and end to end latencies refer to the [deployment guardrails document](../experience-platform/deployment/guardrails.md)

![Guardrail diagram](../experience-platform/deployment/assets/CJA_guardrails.svg){zoomable="yes"}

## Related blog posts

* [[!DNL Blueprint for Multi-Channel Orchestration in Adobe Experience Platform]](https://medium.com/adobetech/blueprint-for-multi-channel-orchestration-in-adobe-experience-platform-c68317e94184){target="_blank"}
* [[!DNL Leveraging External Data Platforms in Adobe Experience Platform Journey Orchestration]](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17){target="_blank"}
* [[!DNL Event-Based Triggering on Adobe Experience Platform Orchestration Service using Apache Airflow]](https://medium.com/adobetech/event-based-triggering-on-adobe-experience-platform-orchestration-service-using-apache-airflow-8607b28251f1){target="_blank"}
* [[!DNL Adobe Campaign Classic Integration with Journey Orchestration]](https://medium.com/adobetech/adobe-campaign-classic-integration-with-journey-orchestration-ae577653281){target="_blank"}
* [[!DNL Demonstrating the Power of Adobe's New Journey Orchestration Service to Build Personalized Omnichannel Experiences in Real-Time]](https://medium.com/adobetech/demonstrating-the-power-of-adobes-new-journey-orchestration-service-to-build-personalized-aa60d88cd34){target="_blank"}
* [[!DNL Journey Orchestration in an Omnichannel World]](https://medium.com/adobetech/journey-orchestration-in-an-omnichannel-world-3a2d32d556d9){target="_blank"}
