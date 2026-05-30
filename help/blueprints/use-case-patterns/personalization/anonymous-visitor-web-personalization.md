---
title: Anonymous Visitor Web Personalization
description: Learn how to deliver personalized web content to unidentified visitors based on in-session behavioral signals.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: e2446801-ffce-40e6-bfe9-abec623c9201
---
# Anonymous visitor web personalization

This guide describes the anonymous visitor web personalization use case pattern, which uses [!DNL Adobe Journey Optimizer] (AJO), [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP), and [!DNL Adobe Experience Platform] (AEP) to deliver personalized web content to anonymous (unidentified) visitors based on in-session behavioral signals. It is designed for solution architects, marketing technologists, and implementation engineers who need to understand what this pattern does, the business objectives it supports, the tactical use cases it enables, and the Adobe applications involved.

The pattern operates with limited data -- only what can be observed in the current session and any anonymous edge profile accumulated from prior visits with the same device or cookie. This makes it suitable for top-of-funnel personalization where the visitor has no account or has not authenticated.

## Use case pattern

The following describes the core pattern and execution plan for this use case.

**Anonymous Visitor Web Personalization**

Deliver personalized content based on in-session behavioral signals for unidentified visitors via AJO web channel.

**Execution plan:** Web Surface Configuration > Behavioral Rule Evaluation > Content Delivery > Impression Tracking > Reporting

## Use case overview

Anonymous Visitor Web Personalization addresses the business need to deliver relevant, personalized content to website visitors who have not yet been identified -- they have not logged in, have no known identity, and cannot be resolved to a unified customer profile. Despite this limitation, meaningful personalization is achievable using in-session behavioral signals: pages viewed, time on site, scroll depth, referral source, geographic location, device type, and UTM campaign parameters.

This pattern uses AJO's web channel surfaces and code-based experiences to modify page content in real time. Edge segmentation is the primary evaluation method since decisions must be made with sub-second latency as the visitor navigates the site. The [!DNL Web SDK] collects behavioral signals and sends them to the [!DNL AEP Edge Network], where edge-evaluated audience rules determine which content variant to deliver.

Unlike known-visitor web/app personalization, which leverages the full unified profile and segment membership, this pattern is constrained to data observable in the current session and any anonymous edge profile associated with the visitor's ECID ([!DNL Experience Cloud ID]). This distinction is critical for implementation planning: the behavioral signals available for personalization are limited to what the [!DNL Web SDK] captures and what persists in the edge profile store across sessions via the cookie-based ECID.

## Key business objectives

The following business objectives are supported by this use case pattern.

**[Increase website engagement](../../business-objectives/acquisition-growth/increase-website-engagement.md)**

Improve time on site, pages per session, and interaction with web content through relevant experiences tailored to anonymous visitor signals.

| KPIs |
| --- |
| Time On (web) Page |
| Engagement |
| Conversion Rates |

**[Deliver personalized customer experiences](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

Tailor content, offers, and messaging to individual preferences, behaviors, and lifecycle stage -- even for visitors who have not yet identified themselves.

| KPIs |
| --- |
| Engagement |
| Conversion Rates |
| Customer Satisfaction (CSAT) |

**[Increase conversion rates](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

Improve the percentage of visitors and prospects who complete desired actions such as purchases, sign-ups, or form submissions by presenting the most relevant content based on behavioral context.

| KPIs |
| --- |
| Conversion Rates |
| Lead Conversion |
| Cost Per Lead |

## Example tactical use cases

The following examples illustrate specific scenarios where this pattern can be applied.

- **Landing page headline A/B test based on referral source** -- Test different headlines for visitors arriving from Google, social media, or direct traffic to optimize engagement by acquisition channel
- **Category affinity recommendations based on browse behavior** -- Display product or content recommendations based on pages viewed in the current session to increase discovery and conversion
- **Exit-intent offer for visitors about to leave** -- Present a promotional offer or lead capture form when behavioral signals indicate the visitor is about to abandon the site
- **Geo-targeted promotional banner** -- Show location-specific promotions, store locator content, or regional offers based on the visitor's geographic location
- **Device-specific content layout optimization** -- Adapt content layout, image sizes, and CTA placement based on whether the visitor is on desktop, tablet, or mobile
- **New vs. returning visitor welcome messaging** -- Differentiate the experience for first-time visitors versus returning anonymous visitors using ECID persistence across sessions
- **Content recommendations based on viewed pages in current session** -- Dynamically surface related articles, products, or resources based on the pages the visitor has already viewed
- **Dynamic hero banner based on UTM campaign parameters** -- Personalize the hero banner to match the messaging or creative from the referring campaign

## Key performance indicators

Use the following KPIs to measure the effectiveness of this use case pattern.

| KPI | Description | Measurement approach |
| --- | --- | --- |
| Personalization Impression Rate | Percentage of eligible page views where personalized content was delivered | AJO campaign report: impressions / total page views |
| Click-Through Rate (CTR) | Percentage of personalized content impressions that result in a click | AJO campaign report: clicks / impressions |
| Engagement Lift | Increase in time on page, pages per session, or scroll depth for personalized vs. default content | CJA workspace comparison: personalized cohort vs. control |
| Conversion Rate | Percentage of visitors exposed to personalized content who complete a desired action | CJA funnel analysis: impression > interaction > conversion |
| Bounce Rate Reduction | Decrease in single-page sessions for visitors who receive personalized content | CJA session analysis: bounce rate delta for personalized vs. default |
| Experiment Win Rate | Percentage of A/B tests that produce a statistically significant winner | AJO experiment report: experiments reaching confidence threshold |

## Applications

The following applications are used in this use case pattern.

- **[!DNL Adobe Journey Optimizer] (AJO)** -- Web channel surface configuration, content authoring (web and code-based experiences), campaign execution, content experimentation (A/B testing), decisioning (dynamic content selection), and reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** -- Edge segmentation for real-time audience evaluation based on in-session behavioral signals; anonymous edge profile management
- **[!DNL Adobe Experience Platform] (AEP)** -- [!DNL Web SDK] for behavioral signal collection, [!DNL Edge Network] for real-time data routing and personalization delivery, datastream configuration

## Architecture

The following reference architecture illustrates how anonymous visitor signals are collected at the edge, evaluated against audience rules, and used to deliver personalized content.

![Reference architecture for anonymous audience activation and personalization](/help/blueprints/audience-activation/assets/anonymous_activation.png)

## Related documentation

The following Experience League resources provide additional detail on the capabilities used in this use case pattern.

**Web channel and code-based experiences**

- [Get started with web channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Create web experiences](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Code-based experience channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Code-based experience configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

**Audiences and segmentation**

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language reference](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

**Personalization and content**

- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Work with content templates](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Work with content fragments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

**Content experimentation**

- [Get started with content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Create a content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Content experiment report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Statistical calculations](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

**Decision Management**

- [Decision Management overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Create placements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Create decision rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Create personalized offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Create fallback offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Create collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Create decisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Ranking strategies](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Deliver offers in messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

**Campaigns**

- [Get started with campaigns](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Create a campaign](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

**[!DNL Web SDK] and data collection**

- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Install Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Tags overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)

**Identity and profile**

- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Identity namespaces overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Real-Time Customer Profile overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

**Data modeling**

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

**Reporting and analytics**

- [Campaign live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Campaign global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Work with Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

**Data governance and privacy**

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Consent and preferences field group](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

**Guardrails**

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identity Service guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
