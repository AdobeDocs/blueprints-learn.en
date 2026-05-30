---
title: Offer Decisioning
description: Learn how to use centralized decision logic to select the next-best offer or content for a profile across channels.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 8fd511b3-0200-41bf-aff1-e3f2a00a578e
---
# Offer decisioning

This guide describes the offer decisioning use case pattern, which uses [!DNL Adobe Journey Optimizer] (AJO) Decisioning and [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) to implement centralized offer selection logic that determines the next-best offer for each customer profile across channels. It is designed for solution architects, marketing technologists, and implementation engineers who need to understand what this pattern does, the business objectives it supports, the tactical use cases it enables, and the Adobe applications involved.

The pattern decouples the "what to show" decision from the "where to show it" channel logic, enabling consistent, optimized offer selection across email, web, mobile app, and any other touchpoint. AJO Decisioning manages the full offer lifecycle: offer creation and catalog management, eligibility rules (who can see each offer), ranking strategies (how to select among eligible offers), placements (where offers appear), and decision policies (which bind everything together).

## Use case pattern

This section describes the execution plan and pattern definition for offer decisioning.

**Offer decisioning**

Use centralized decision logic to select the next-best offer or content for a profile across channels.

**Execution plan:** Audience Evaluation > Offer Eligibility > Ranking Strategy > Decision Execution > Delivery > Reporting

## Use case overview

Organizations frequently need to present the most relevant offer, promotion, or incentive to each customer at the moment of interaction. Whether the interaction occurs in an email campaign, on a website homepage, within a mobile app, or at a decision point within a multi-step journey, the challenge is the same: select the optimal offer from a catalog of available options based on who the customer is, what they qualify for, and which offer is most likely to drive the desired outcome.

Offer decisioning addresses this by centralizing all offer selection logic in AJO's Decision Management engine. Rather than hardcoding offer assignments into individual campaigns or channels, the decision engine evaluates each profile's attributes, audience membership, and contextual signals to determine the best offer in real time. This centralization ensures that the same customer receives consistent, optimized offers regardless of which channel they engage through.

This pattern differs from known-visitor web/app personalization in scope -- offer decisioning is channel-agnostic and centralized, while known-visitor personalization focuses on digital surface personalization. It differs from behavioral recommendation in catalog model -- use offer decisioning when the eligible item set is governed by business rules, eligibility constraints, or regulatory requirements (promotions, financial products, incentives). Use behavioral recommendation when the item set is large, continuously changing, and selection is driven by behavioral similarity or affinity signals (product catalogs, content libraries).

## Key business objectives

The following business objectives are supported by this use case pattern.

**[Deliver personalized customer experiences](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
Tailor content, offers, and messaging to individual preferences, behaviors, and lifecycle stage.
**KPIs:** Engagement, Conversion Rates, Customer Satisfaction (CSAT)

**[Drive cross-sell & upsell revenue](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
Promote complementary and premium products or services to existing customers based on behavior and purchase history.
**KPIs:** Upsell/Cross Sell %, Incremental Revenue, Customer Lifetime Value

**[Increase customer loyalty & lifetime value](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
Deepen customer relationships and maximize long-term value through loyalty programs, rewards, and personalized engagement.
**KPIs:** Customer Lifetime Value, Retention, Upsell/Cross Sell %

## Example tactical use cases

The following scenarios illustrate how offer decisioning can be applied in practice.

- Next-best-offer in email campaigns -- select the most relevant promotion per recipient at send time
- Real-time promotional banner on website -- decisioning selects the offer at page load based on the visitor's profile
- Personalized in-app card with the best incentive for the user's lifecycle stage
- Cross-channel offer consistency -- same decisioning logic serves email, web, and push so the customer sees a unified offer experience
- Dynamic coupon or discount selection based on customer value tier (e.g., high-value customers receive a premium offer)
- Product upgrade or upsell offer selection based on current subscription level
- Loyalty reward offer personalization based on tier and activity history

## Key performance indicators

The following KPIs help measure the effectiveness of an offer decisioning implementation.

| KPI | Description | Measurement approach |
| --- | --- | --- |
| Offer Acceptance Rate | Percentage of delivered offers that result in a click, redemption, or conversion | Offer clicks or redemptions / Total offers delivered |
| Offer Selection Distribution | Proportion of each offer selected across all decisions | Count per offer / Total decisions rendered |
| Fallback Rate | Percentage of decisions where no personalized offer qualified and the fallback was served | Fallback impressions / Total decisions |
| Conversion Rate | Percentage of offer recipients who completed the desired action (purchase, sign-up, redemption) | Conversions / Offer impressions |
| Incremental Revenue | Revenue attributable to decisioning-selected offers versus a control group or fallback | Revenue from personalized offers - Revenue from fallback/control |
| Cross-Channel Consistency Score | Percentage of profiles receiving the same offer across multiple channels within a defined window | Consistent offers / Total multi-channel impressions |
| Offer Click-Through Rate | Percentage of offer impressions that result in a click | Offer clicks / Offer impressions |

## Applications

The following Adobe applications are used in this use case pattern.

- **[!DNL Adobe Journey Optimizer] (AJO)** -- Decision Management engine for offer creation, eligibility rules, ranking strategies, placements, and decision policies; channel configuration and message authoring for offer delivery; campaign and journey execution
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** -- Audience evaluation for offer eligibility segments; profile data and computed attributes used in eligibility and ranking
- **[!DNL Adobe Experience Platform] (AEP)** -- Unified profile store, identity resolution, and data foundation supporting both AJO and RT-CDP

## Related documentation

The following resources provide additional detail on the components used in this use case pattern.

### Decision Management

- [Decision Management overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Create placements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Create decision rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Create personalized offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Create fallback offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Create collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Create collection qualifiers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Create decisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Ranking strategies](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Offer delivery

- [Deliver offers in messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Deliver offers using the Edge Decisioning API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Deliver offers using the Decisioning API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/decisioning-api)

### Channel configuration

- [Get started with email configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Email surface settings](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delegate subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Configure push notification channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Configure SMS channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### Message authoring and personalization

- [Design email content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Work with content templates](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Preview and test your content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Campaigns and journeys

- [Get started with campaigns](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Create a campaign](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Get started with journeys](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)

### Content experimentation

- [Get started with content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Create a content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### Audiences and segmentation

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Profile and identity

- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Customer AI overview](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Data modeling and collection

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)

### Reporting and analytics

- [Campaign global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Journey global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Work with Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Data governance and lifecycle

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview)
- [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Consent in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Guardrails

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### Tutorials

- [Decision Management API getting started](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/getting-started)
