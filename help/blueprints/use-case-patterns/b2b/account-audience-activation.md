---
title: B2B Audience Activation
description: Learn how to activate account-based B2B audiences across web, email, and advertising channels.
solution: Real-Time Customer Data Platform
exl-id: 2b979159-37aa-41d4-a6b4-1105538f6546
---
# B2B audience activation

This guide describes the B2B audience activation use case pattern, which uses [!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B Edition to build, evaluate, and activate account-level audiences across web, email, advertising, and CRM channels. It is designed for solution architects, marketing technologists, and implementation engineers who need to understand what this pattern does, the business objectives it supports, the tactical use cases it enables, and the Adobe applications involved.

This pattern covers the full lifecycle from account profile unification through audience evaluation and activation to B2B-specific destinations such as [!DNL Marketo Engage], [!DNL LinkedIn], and CRM systems.

## Use case pattern

**B2B audience activation**

Activate account-based B2B audiences across web, email, and advertising channels.

**Execution plan:** Account Profile Enrichment > Account Audience Evaluation > Destination Configuration > Audience Activation > Monitoring

## Use case overview

B2B marketing teams need to target and activate audiences at the account level rather than the individual person level. Unlike B2C audience activation where the unit of targeting is a single consumer profile, B2B audience activation requires understanding the relationship between people and the accounts they belong to, evaluating audience membership based on account-level attributes combined with person-level engagement signals, and delivering those audiences to destinations that support account-based targeting.

[!DNL RT-CDP] B2B Edition extends the standard [!DNL Real-Time Customer Data Platform] with specialized XDM classes for accounts, opportunities, and campaigns, along with B2B identity resolution that maps person-to-account relationships. This enables marketers to build account audiences that combine firmographic data (industry, revenue, employee count), technographic data (technology stack, product usage), and behavioral data (web visits, email engagement, event attendance) from the people associated with those accounts.

The activated account audiences power use cases across the demand generation funnel: top-of-funnel awareness campaigns on [!DNL LinkedIn] and display advertising, mid-funnel nurture programs in [!DNL Marketo Engage], and bottom-funnel sales enablement through CRM integration. Account suppression audiences prevent wasted spend by excluding existing customers, closed-lost accounts, or accounts already in active sales cycles.

>[!NOTE]
>If your use case involves activating audiences at the person level (B2C) rather than the account level, see [Audience activation to destinations](../audience-building-activation/audience-activation-to-destinations.md). That pattern uses the standard RT-CDP data model and does not require B2B Edition.

## Key business objectives

The following business objectives are supported by this use case pattern.

### Increase lead generation

Generate more qualified leads for the sales pipeline through forms, events, content, and multi-channel engagement.

**KPIs:** Prospects, Cost Per Lead, Lead Conversion

[Learn more about increasing lead generation](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### Improve lead qualification & conversion

Increase lead quality and accelerate pipeline progression through scoring, nurturing, and personalized follow-up.

**KPIs:** Lead Conversion, Prospect/Lead Conversion, Efficiency

[Learn more about improving lead qualification & conversion](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### Acquire new customers

Expand the customer base through targeted acquisition campaigns, lookalike audiences, and paid media optimization.

**KPIs:** New Customers, Customer Acquisition Cost, Prospect/Lead Conversion

[Learn more about acquiring new customers](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Optimize marketing spend & ROI

Improve return on marketing investment through better targeting, attribution, audience suppression, and budget allocation.

**KPIs:** Cost Savings, Customer Acquisition Cost, Incremental Revenue

[Learn more about optimizing marketing spend & ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Example tactical use cases

The following scenarios illustrate how this pattern can be applied in practice.

- **Account-based advertising on [!DNL LinkedIn]** -- Target accounts matching your ideal customer profile (ICP) with sponsored content and InMail campaigns on [!DNL LinkedIn], using account lists activated from [!DNL RT-CDP] B2B Edition
- **[!DNL Marketo Engage] nurture program targeting** -- Activate account audiences to [!DNL Marketo Engage] to enroll associated leads and contacts into targeted nurture streams based on account-level qualification criteria
- **CRM account list synchronization** -- Push qualified account lists to [!DNL Salesforce] or [!DNL Microsoft Dynamics] for sales team visibility, territory assignment, and outbound prospecting workflows
- **Account suppression for paid media** -- Suppress existing customers, closed-won accounts, or accounts in active sales cycles from paid acquisition campaigns to reduce wasted spend
- **Intent-based account targeting** -- Combine third-party intent signals with first-party engagement data at the account level to identify and activate audiences of in-market accounts
- **Product cross-sell to existing accounts** -- Build audiences of accounts using one product line but not another, then activate to email and advertising channels for cross-sell campaigns
- **Event and webinar targeting** -- Activate account audiences to advertising and email channels to drive event registration from target accounts
- **Competitive displacement campaigns** -- Target accounts using competitor products with tailored messaging activated through advertising and email channels
- **Tiered account engagement** -- Segment accounts into engagement tiers (high, medium, low) based on aggregated person-level activity and activate differentiated campaigns for each tier
- **Partner co-marketing audiences** -- Share account audience segments with channel partners or co-marketing programs through cloud storage destinations

## Key performance indicators

The following KPIs help measure the success of this use case pattern.

| KPI | Description | Measurement approach |
| --- | --- | --- |
| Account Reach | Number of target accounts reached across activation channels | Track unique accounts activated per destination |
| Account Engagement Rate | Percentage of activated accounts showing engagement signals | Measure person-level engagement aggregated to account |
| Pipeline Influence | Revenue pipeline attributed to account-based activation campaigns | Track opportunities created from activated account audiences |
| Cost Per Engaged Account | Marketing spend divided by the number of accounts showing engagement | Calculate across advertising and email channel costs |
| Lead Conversion Rate | Percentage of leads from activated accounts that convert to opportunities | Track lead-to-opportunity conversion for activated audiences |
| Audience Suppression Savings | Cost avoided by suppressing ineligible accounts from paid campaigns | Measure spend reduction from suppression audiences |
| Account Coverage | Percentage of total addressable market (TAM) covered by activated audiences | Compare activated accounts against total ICP universe |

## Applications

The following applications are used to implement this use case pattern.

- **[!DNL Real-Time CDP] B2B Edition** -- Core platform for account profile unification, B2B identity resolution, account audience evaluation, B2B-specific destination configuration, and account audience activation
- **[!DNL Adobe Experience Platform] (AEP)** -- Foundational infrastructure for B2B XDM data modeling, data ingestion from CRM and marketing automation sources, identity service, and governance
- **[!DNL Marketo Engage]** -- Primary B2B marketing automation destination for lead nurture programs, scoring, and campaign execution fed by activated account audiences

## Related documentation

The following resources provide additional context and detailed guidance for the capabilities used in this use case pattern.

**[!DNL RT-CDP] B2B Edition**

- [Real-Time CDP B2B Edition overview](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [B2B schemas in Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [RT-CDP B2B Edition product description](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

**Audience evaluation & segmentation**

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Audience Composition](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

**Destinations & activation**

- [Destinations overview](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Destinations catalog](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Marketo Engage destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [LinkedIn Matched Audiences destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Salesforce CRM destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Microsoft Dynamics 365 destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)
- [Amazon S3 destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [Activate audiences to streaming destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Activate audiences to batch destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Activation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

**Data sources & connectors**

- [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Marketo Engage connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Salesforce connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/crm/salesforce)

**Data modeling & identity**

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Profile overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

**Data governance & privacy**

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview)
- [Consent and preferences](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Monitoring & observability**

- [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Monitor destination dataflows](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Monitor source dataflows](https://experienceleague.adobe.com/en/docs/experience-platform/sources/api-tutorials/monitor)
- [License usage dashboard](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Reporting & analytics**

- [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Connections overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Data views overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)

**Tutorials & guides**

- [Getting started with Real-Time CDP B2B Edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro)
- [Create a schema for B2B sources](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Sandbox Tooling](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/sandbox-tooling-api/overview)
