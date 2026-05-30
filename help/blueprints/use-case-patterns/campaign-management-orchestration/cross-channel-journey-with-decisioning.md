---
title: Cross-Channel Journey with Decisioning
description: Learn how to orchestrate a multi-step journey incorporating real-time decisioning to select optimal channel, content, or offer.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: eabdd91f-bb7d-4de3-adb5-5940d3ca4a78
---
# Cross-channel journey with decisioning

This guide describes the cross-channel journey with decisioning use case pattern, which uses [!DNL Adobe Journey Optimizer] and [!DNL Adobe Real-Time Customer Data Platform] to orchestrate multi-step, multi-channel journeys that incorporate real-time decisioning at one or more journey nodes. It is designed for solution architects, marketing technologists, and implementation engineers who need to understand what this pattern does, the business objectives it supports, the tactical use cases it enables, and the Adobe applications involved.

Cross-channel journey with decisioning is the most sophisticated campaign orchestration pattern in the [!DNL Adobe Experience Platform] ecosystem. It extends multi-step orchestrated journeys by incorporating real-time decisioning — using [!DNL AJO] Decisioning to evaluate a profile's current context and dynamically select the optimal channel, content, or offer at one or more decision points within the journey canvas.

## Use case pattern

**Cross-channel journey with decisioning**

Orchestrate a multi-step, multi-channel journey that incorporates real-time decisioning at one or more nodes to select the optimal channel, content, or offer.

**Execution plan:** Audience Evaluation > Journey Execution > Decision Node > Channel Selection > Message Delivery > Reporting

## Use case overview

Organizations increasingly need to deliver adaptive, personalized customer journeys that respond dynamically to each individual's real-time context rather than following a fixed, predetermined sequence. A customer's preferred channel, their engagement history, their loyalty tier, their predicted lifetime value, and their current product interests all factor into what the next-best action should be at each touchpoint.

Cross-channel journey with decisioning addresses this need by combining two powerful [!DNL AJO] capabilities: journey orchestration (which manages the multi-step flow, timing, conditions, and channel delivery) and decisioning (which evaluates eligibility rules, applies ranking strategies, and selects the optimal offer or content variant at each decision point).

This pattern is appropriate when:

- The journey must adapt dynamically to each profile's real-time state rather than following a fixed channel or content sequence
- Multiple offers, content variants, or channels are candidates at one or more journey nodes, and the best option should be selected based on profile context
- AI-assisted or formula-based ranking is needed to optimize offer selection across the journey
- The organization wants to consolidate channel selection logic and offer management into a centralized decision framework rather than maintaining complex branching logic

The target audience includes marketers managing lifecycle programs, loyalty journeys, win-back sequences, and onboarding flows where personalization at scale requires automated decision-making at each touchpoint.

>[!NOTE]
>If your journey does not require dynamic decisioning at individual nodes — for example, a fixed-sequence nurture or onboarding program — see [Multi-step orchestrated journey](multi-step-orchestrated-journey.md). That pattern is simpler to configure and does not require AJO Decisioning.

## Key business objectives

The following business objectives are supported by this use case pattern.

**[Deliver personalized customer experiences](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
Tailor content, offers, and messaging to individual preferences, behaviors, and lifecycle stage.
**KPIs:** Engagement, Conversion Rates, Customer Satisfaction (CSAT)

**[Increase customer loyalty & lifetime value](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
Deepen customer relationships and maximize long-term value through loyalty programs, rewards, and personalized engagement.
**KPIs:** Customer Lifetime Value, Retention, Upsell/Cross Sell %

**[Improve customer retention](../../business-objectives/customer-experience/improve-customer-retention.md)**
Keep existing customers engaged and renewing through value-driven experiences and ongoing relationship nurturing.
**KPIs:** Retention, Customer Lifetime Value, Engagement

**[Drive cross-sell & upsell revenue](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
Promote complementary and premium products or services to existing customers based on behavior and purchase history.
**KPIs:** Upsell/Cross Sell %, Incremental Revenue, Customer Lifetime Value

## Example tactical use cases

The following scenarios illustrate how cross-channel journey with decisioning can be applied in practice.

- **Adaptive win-back journey** — A multi-step journey where decisioning selects the channel (email, push, or SMS) based on each profile's engagement history, and dynamically selects the best incentive offer based on predicted lifetime value
- **Next-best-action lifecycle journey** — Decisioning determines what to communicate at each stage of the customer lifecycle, selecting from onboarding content, cross-sell offers, loyalty rewards, or retention incentives
- **Personalized onboarding with dynamic content selection** — New customer onboarding journey where each touchpoint uses decisioning to select the most relevant product education content, tips, or activation offers
- **Cross-channel loyalty program journey with personalized rewards** — Loyalty members progress through a journey where decisioning selects personalized reward offers based on tier, purchase history, and category affinity
- **Dynamic re-engagement with channel and incentive optimization** — Dormant customer re-engagement where both the outreach channel and the incentive are dynamically selected to maximize response probability
- **Customer lifecycle nurture with AI-ranked content recommendations** — Ongoing nurture journey where AI-ranked decisioning selects the most relevant content or product recommendations at each touchpoint

## Key performance indicators

Use the following KPIs to measure the effectiveness of this use case pattern.

| KPI | Description | Measurement approach |
| --- | --- | --- |
| Journey Completion Rate | Percentage of profiles that complete the full journey | Journey report: completed / entered |
| Offer Acceptance Rate | Percentage of decisioning-selected offers that are engaged with (clicked, redeemed) | Decisioning report: offer clicks / offer impressions |
| Channel Engagement Rate | Open and click rates across each channel used in the journey | Per-channel delivery metrics in journey report |
| Conversion Rate | Percentage of journey participants who complete the target conversion action | Journey exit event tracking or CJA funnel analysis |
| Fallback Offer Rate | Percentage of decision requests returning the fallback offer instead of a personalized offer | Decisioning report: fallback selections / total selections |
| Customer Lifetime Value Impact | Change in CLV for journey participants vs. control group | CJA cohort analysis with holdout comparison |
| Cross-Sell / Upsell Revenue | Incremental revenue attributed to decisioning-selected offers | CJA attribution analysis on offer-driven conversions |
| Decisioning Ranking Effectiveness | Performance difference between AI-ranked offers and random/priority-based selection | A/B experiment comparing ranking strategies |

## Applications

The following applications are used to implement this use case pattern.

- **[!DNL Adobe Journey Optimizer] ([!DNL AJO])** — Journey orchestration (multi-step canvas design, entry conditions, waits, conditions, exit criteria), message authoring across channels, channel surface configuration, conflict and priority management
- **[!DNL Adobe Journey Optimizer] Decisioning** — Offer and content item management, eligibility rules, ranking strategies (priority, formula, AI), decision policies, placements, fallback offers
- **[!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP])** — Audience evaluation for journey entry and offer eligibility segments, profile enrichment with computed attributes and propensity scores, consent and governance enforcement
- **[!DNL Adobe Experience Platform] ([!DNL AEP])** — Real-Time Customer Profile store, Identity Service for cross-channel resolution, data modeling and ingestion infrastructure

## Related documentation

The following resources provide additional detail on the capabilities used in this use case pattern.

### Journey orchestration

- [Get started with journeys](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Create a journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journey properties](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Read audience activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [General events](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Audience qualification events](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Condition activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Wait activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Add a message in a journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Exit criteria](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Journey entry management](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Test your journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Publish the journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

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

### Channel configuration

- [Get started with email configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delegate subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Create IP pools](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP warmup plans](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Email surface settings](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configure SMS channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configure push notification channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Message authoring and personalization

- [Create an email](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Design email content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Work with content templates](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Work with content fragments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Preview and test your content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Conflict, priority, and frequency management

- [Conflict and priority management overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Priority scores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identify potential conflicts](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Journey capping and arbitration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Frequency rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### Audiences and segmentation

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Audience Composition](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language reference](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Reporting and analytics

- [Journey live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Journey global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Work with Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Profile and identity

- [Real-Time Customer Profile overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Customer AI overview](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Data governance and consent

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Consent in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Manage suppression list](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Guardrails

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identity Service guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
