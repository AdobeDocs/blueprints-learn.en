---
title: Adobe Real-Time CDP activation
description: Architecture reference for activating audiences and profile data from Adobe Real-Time CDP to advertising, social, cloud storage, and enterprise destinations.
solution: Real-Time Customer Data Platform, Experience Platform
product_v2:
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
    internal-label: Real-Time Customer Data Platform
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
---
# Adobe Real-Time CDP activation

This architecture shows how Adobe [!DNL Real-Time Customer Data Platform] ([!DNL Real-Time CDP]) activates audiences and profile data to advertising, social, cloud storage, and enterprise destinations through streaming and batch data flows.

## Audience and profile activation

The architecture illustrates the shared activation path from [!DNL Real-Time CDP] audiences and profiles to destination applications. It includes destination activation for advertising and social platforms, as well as enterprise destinations used for storage, analysis, and downstream application workflows.

![Adobe Real-Time CDP audience and profile activation architecture](assets/real_time_cdp_activation.png){width="1000" zoomable="yes"}

## Use case patterns supported

The architecture above supports the following use case patterns:

- [Audience activation to destinations](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md) -- Activate evaluated audiences to advertising, social, cloud storage, CRM, and other enterprise destinations.
- [Anonymous visitor web personalization](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md) -- Support audience activation and profile-based personalization across digital channels.

## Primary data flows and integration points

- Ingest customer data from multiple sources into [!DNL Real-Time CDP].
- Unify identity and profile attributes in [!DNL Real-Time Customer Profile].
- Evaluate profiles into audiences for activation.
- Stream or batch audience and profile changes to advertising, social, cloud storage, and enterprise destinations.
- Use activated profile and audience data in downstream marketing, sales, support, analytics, and personalization workflows.

## Further reading

- [Adobe Real-Time CDP destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Activate audiences to destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Adobe Real-Time CDP guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/guardrails/overview)
