---
title: Adobe Customer Journey Analytics & Adobe Journey Optimizer integration
description: Architecture for analyzing Adobe Journey Optimizer campaign and journey insights in Adobe Customer Journey Analytics and publishing audiences back for journey execution.
solution: Customer Journey Analytics, Journey Optimizer, Experience Platform
product_v2:
  - id: e98b7246-966c-4318-9e95-cad2f7a17dc7
    internal-label: Customer Journey Analytics
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
    internal-label: Journey Optimizer
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
---
# Adobe Customer Journey Analytics & Adobe Journey Optimizer integration

This architecture shows how Adobe Journey Optimizer delivery and interaction data flows through Adobe Experience Platform into Customer Journey Analytics for campaign and journey insights. Audiences created in Customer Journey Analytics can be published through Real-Time CDP for use in Journey Optimizer execution.

## Campaign and journey insights architecture

The architecture connects Journey Optimizer delivery and interaction data with Experience Platform and Customer Journey Analytics for reporting, analysis, and audience creation.

![Adobe Customer Journey Analytics and Adobe Journey Optimizer integration architecture](assets/cja_ajo_integration.png){width="1000" zoomable="yes"}

## Primary data flows and integration points

- Journey Optimizer delivery, interaction, and effectiveness data is shared to Experience Platform data services.
- Experience Platform data is ingested into Customer Journey Analytics through a CJA connection.
- Customer Journey Analytics data views and analysis provide campaign and journey insight.
- Audiences authored in Customer Journey Analytics are published to Real-Time CDP.
- Real-Time CDP audiences are available for Journey Optimizer journey execution and personalization.

## Use case patterns supported

- [Customer analytics and insight generation](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) -- Analyze campaign and journey behavior across channels.
- [Event-triggered messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) -- Use customer and journey signals to support orchestrated messaging.

## Further reading

- [Journey Optimizer reporting](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/reports/sharing-overview)
- [Customer Journey Analytics overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Publish Customer Journey Analytics audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
