---
title: Known-Visitor Web/App Personalization
description: Learn how to deliver personalized content, offers, or promotions to identified visitors based on real-time profile and segment membership.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 585adc0e-f528-4a09-b931-ef6b45fa8ec8
---
# Known-visitor web/app personalization

This guide describes the known-visitor web/app personalization use case pattern, which uses [!DNL Adobe Journey Optimizer] (AJO) and [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) to deliver personalized content to identified visitors across digital surfaces. It is designed for solution architects, marketing technologists, and implementation engineers who need to understand what this pattern does, the business objectives it supports, the tactical use cases it enables, and the Adobe applications involved.

Known-visitor web/app personalization is the primary personalization pattern for authenticated digital experiences. Unlike anonymous visitor personalization, which relies solely on in-session behavioral signals, this pattern leverages the full unified profile: historical behavioral data, segment membership, loyalty tier, purchase history, lifecycle stage, computed attributes, and propensity scores. It supports personalization across web pages (via AJO web channel), mobile in-app messages, and content cards.

## Use case pattern

This section describes the core pattern and its execution plan.

**Known-visitor web/app personalization**

Deliver personalized content, offers, or promotions to an identified visitor based on real-time profile and segment membership across web, mobile in-app, and content card surfaces.

**Execution plan:** Audience Evaluation > Personalization Decisioning > Surface/Channel Configuration > Content Delivery > Impression Tracking > Reporting

## Use case overview

Organizations with authenticated digital properties -- e-commerce sites, banking portals, subscription services, loyalty programs, mobile apps -- need to deliver personalized experiences that reflect each customer's relationship with the brand. When a visitor logs in or is recognized through identity resolution, the platform can access their full unified profile and deliver content tailored to their specific attributes, behaviors, and preferences.

This pattern addresses the scenario where an identified visitor arrives on a web property or opens a mobile app, and the system must determine the optimal content, offer, or promotion to display based on real-time profile data and audience membership. The personalization decision happens at the edge in milliseconds, enabling sub-second content delivery without perceptible latency.

The pattern supports both deterministic personalization (where specific content maps to specific audience segments) and dynamic decisioning (where AJO Decisioning evaluates eligibility rules and ranking strategies to select the optimal content per profile). It spans multiple digital surfaces -- web pages, mobile in-app messages, and content cards -- enabling consistent personalization across the customer's digital journey.

## Key business objectives

The following business objectives are supported by this use case pattern.

### Deliver personalized customer experiences

Tailor content, offers, and messaging to individual preferences, behaviors, and lifecycle stage. For more information, see [Deliver personalized customer experiences](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md).

**KPIs:** Engagement, Conversion Rates, Customer Satisfaction (CSAT)

### Increase website engagement

Improve time on site, pages per session, and interaction with web content through relevant experiences. For more information, see [Increase website engagement](../../business-objectives/acquisition-growth/increase-website-engagement.md).

**KPIs:** Time On (web) Page, Engagement, Conversion Rates

### Increase mobile app engagement

Drive daily active usage, feature adoption, and in-app conversions through personalized in-app experiences.

**KPIs:** Engagement, Retention, Conversion Rates

## Example tactical use cases

The following are common tactical implementations of this pattern:

- Homepage hero personalization by loyalty tier or lifecycle stage -- display different hero banners based on whether the customer is new, active, at-risk, or VIP
- Product recommendation carousel based on purchase history -- surface relevant product suggestions using past purchase data and product affinity scores
- Personalized promotional banner by customer segment -- show different promotions to high-value, at-risk, and new customer segments
- In-app message for mobile users based on feature adoption -- guide users to underutilized features based on their usage patterns
- Content card with personalized offer on account dashboard -- persistent, dismissible offers tailored to the customer's profile
- Personalized pricing or discount display based on customer tier -- show tier-specific pricing or exclusive discounts to loyalty program members
- Cross-sell recommendation widget based on owned products -- suggest complementary products or services based on current portfolio
- Personalized navigation or content ordering based on interests -- reorder content modules or navigation elements based on demonstrated preferences

## Key performance indicators

The following KPIs help measure the effectiveness of this use case pattern.

| KPI | Measurement approach | Benchmark guidance |
| --- | --- | --- |
| Personalization Engagement Rate | Clicks and interactions with personalized content elements divided by impressions | Personalized content should outperform default content by 20-50% |
| Conversion Rate Lift | Conversion rate for personalized experiences versus control/default experiences | Target 10-30% lift over non-personalized experiences |
| Click-Through Rate (CTR) | Clicks on personalized CTAs, offers, and recommendations divided by impressions | Monitor per surface (web, in-app, content card) and per segment |
| Revenue per Visit | Revenue attributed to sessions with personalized experiences | Compare personalized versus non-personalized visitor cohorts |
| Content Card Interaction Rate | Content card clicks and dismissals relative to impressions | Track per card type and audience segment |
| In-App Message Engagement | In-app message interactions (CTA clicks, dismissals) relative to impressions | Compare across audience segments and message types |
| Time on Page | Average time spent on pages with personalized content versus default | Personalized pages should show increased dwell time |
| Offer Acceptance Rate | Percentage of decisioning-selected offers that result in a conversion event | Track per offer, per placement, and per ranking strategy |

## Applications

The following applications are used in this use case pattern.

- **[!DNL Adobe Journey Optimizer] (AJO)** -- Web channel configuration, in-app channel configuration, content card channel configuration, decisioning (offer selection and ranking), message authoring (personalized content creation), campaign execution, content experimentation, and reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** -- Audience evaluation (edge, streaming, and batch), real-time profile lookup via Edge Network, profile enrichment with computed attributes and propensity scores
- **[!DNL Adobe Experience Platform] (AEP)** -- Profile store, identity service, Web SDK, Mobile SDK, datastream configuration, edge network delivery

## Related documentation

The following resources provide additional detail on the technologies and configurations referenced in this guide.

### Web channel personalization

- [Get started with web channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Create web experiences](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Web channel configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)

### In-app and content card channels

- [In-app channel overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [In-app channel prerequisites](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [Create in-app messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [Content card channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Content card configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)
- [Create content cards](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/create-content-card)

### Decision management

- [Decision Management overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Create placements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Create decision rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Create personalized offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Create fallback offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Create collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Create decisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Ranking strategies](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Deliver offers in messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Personalization and content

- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Helper functions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Work with content templates](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Work with content fragments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

### Audiences and segmentation

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language reference](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Identity and profile

- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Identity namespaces overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Identity graph linking rules](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Profile overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Data collection and SDK

- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Install Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Mobile SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Edge Network Server API overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### Campaigns and experimentation

- [Get started with campaigns](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Create a campaign](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Get started with content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Create a content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Content experiment report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### Computed attributes and enrichment

- [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Computed attributes UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Customer AI overview](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Reporting and analytics

- [Campaign live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Campaign global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Governance and privacy

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Consent in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### Guardrails

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identity Service guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
