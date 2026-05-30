---
title: Behavioral Recommendation
description: Learn how to generate item and content recommendations using selection strategies and ranking models.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: db16e773-e0da-46c4-9fa5-d16f04feb46b
---
# Behavioral recommendation

This guide describes the behavioral recommendation use case pattern, which uses [!DNL Adobe Journey Optimizer] (AJO) Decisioning, [!DNL Real-Time Customer Data Platform] (RT-CDP), and [!DNL Adobe Experience Platform] (AEP) to deliver personalized recommendation experiences across web, mobile app, and email channels. It is designed for solution architects, marketing technologists, and implementation engineers who need to understand what this pattern does, the business objectives it supports, the tactical use cases it enables, and the Adobe applications involved.

Behavioral Recommendation generates item-level or content-level recommendations using behavioral signals -- product views, purchases, content interactions, search queries -- combined with AJO Decisioning selection strategies and ranking models. Unlike offer decisioning — which governs a bounded set of offers, promotions, or incentives using eligibility rules and business constraints — this pattern operates on large, continuously changing item catalogs (products, articles, videos) where selection is driven by behavioral affinity signals rather than governed eligibility.

## Use case pattern

**Behavioral Recommendation**

Generate item-level or content-level recommendations based on behavioral signals, using AJO Decisioning selection strategies and ranking models to serve contextual content.

**Execution plan:** Behavioral Signal Ingestion > Decisioning Strategy Evaluation > Recommendation Delivery > Reporting

## Use case overview

Organizations with product catalogs, content libraries, or media libraries need to surface the most relevant items to each visitor based on their behavioral history and in-session activity. Whether it is a "recommended for you" carousel on a homepage, a cross-sell widget on a product detail page, or product recommendations embedded in an email campaign, the underlying challenge is the same: match each visitor's behavioral profile to the most relevant items from a catalog, then deliver those recommendations in the right channel at the right moment.

This pattern addresses that challenge by ingesting behavioral signals in real time via [!DNL Web SDK] or [!DNL Mobile SDK], processing them through AJO Decisioning selection strategies that combine item attributes with behavioral context, and delivering the recommended items through web, in-app, or email channels. Ranking models can be formula-based (e.g., sort by category affinity score) or AI-ranked (e.g., personalized recommendation model). The pattern also handles cold-start scenarios for new visitors with no behavioral history by configuring fallback recommendations.

The target audience for this pattern includes ecommerce merchandising teams, content personalization teams, and digital experience teams seeking to improve engagement, conversion, and average order value through personalized recommendations driven by real user behavior.

## Key business objectives

The following business objectives are supported by this use case pattern.

### [Drive cross-sell and upsell revenue](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)

Promote complementary and premium products or services to existing customers based on behavior and purchase history.

**KPIs:** Upsell/Cross Sell %, Incremental Revenue, Customer Lifetime Value

### [Increase conversion rates](../../business-objectives/revenue-monetization/increase-conversion-rates.md)

Improve the percentage of visitors and prospects who complete desired actions such as purchases, sign-ups, or form submissions.

**KPIs:** Conversion Rates, Lead Conversion, Cost Per Lead

### [Deliver personalized customer experiences](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

Tailor content, offers, and messaging to individual preferences, behaviors, and lifecycle stage.

**KPIs:** Engagement, Conversion Rates, Customer Satisfaction (CSAT)

## Example tactical use cases

The following are common tactical implementations of this pattern:

- Product cross-sell widget on product detail page ("customers also bought")
- "Recommended for you" carousel on homepage based on browse history
- Content recommendations on media site based on reading behavior
- "Recently viewed" combined with similar items widget
- Post-purchase complementary product recommendations
- Email product recommendations based on behavioral affinity
- Category-specific recommendations based on in-session browse behavior
- Search result re-ranking based on behavioral signals

## Key performance indicators

The following KPIs help measure the effectiveness of behavioral recommendation implementations.

| KPI | Measurement approach |
| --- | --- |
| Recommendation Click-Through Rate (CTR) | Clicks on recommended items divided by recommendation impressions |
| Recommendation Conversion Rate | Purchases or desired actions from recommendation clicks divided by total recommendation clicks |
| Revenue Influenced by Recommendations | Total revenue from orders that included at least one recommendation-driven product |
| Average Order Value (AOV) Lift | Increase in AOV for sessions that engaged with recommendations vs. sessions without |
| Items Per Order | Number of items per order for recommendation-engaged sessions |
| Recommendation Coverage | Percentage of eligible page views or sessions that received personalized (non-fallback) recommendations |
| Cold-Start Fallback Rate | Percentage of recommendation requests served by fallback logic due to insufficient behavioral history |

## Applications

The following applications are used in this use case pattern.

- **[!DNL Adobe Journey Optimizer] (AJO) Decisioning** -- Selection strategies, ranking models, item catalogs, and decision policies that evaluate behavioral signals and return the most relevant items for each visitor
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** -- Behavioral profile data accumulation, audience evaluation for recommendation scoping, and computed attributes for behavioral affinity scoring
- **[!DNL Adobe Experience Platform] (AEP)** -- Behavioral event ingestion via [!DNL Web SDK] and [!DNL Mobile SDK], [!DNL Edge Network] processing, XDM schema management for event and catalog data

## Related documentation

The following resources provide additional detail on the technologies and capabilities used in this pattern.

### Decision management

- [Decision Management overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Create placements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Create decision rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Create personalized offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Create fallback offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Create collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Create collection qualifiers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Create decisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Ranking strategies](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Deliver offers in messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Deliver offers using the Edge Decisioning API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)

### Data collection and Web/Mobile SDK

- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Install Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Mobile SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Edge Network Server API overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### XDM and data modeling

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Create a dataset](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/create)
- [Define a relationship between two schemas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-api)

### Identity and profile

- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Identity namespaces overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Real-Time Customer Profile overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Audiences and segmentation

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Computed attributes and profile enrichment

- [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Computed attributes UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Customer AI overview](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Channel configuration

- [Get started with email configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Set up channel surfaces](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delegate subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)

### Message authoring and personalization

- [Design email content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Work with content templates](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### Reporting and analytics

- [Campaign global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Journey global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Work with Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Calculated metrics overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

### Data governance and lifecycle

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview)
- [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Dataset expirations](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration)

### Monitoring and observability

- [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
- [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

### Guardrails

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Ingestion guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Identity Service guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)

### Tutorials and guides

- [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Tags overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
- [Consent and preferences field group](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
