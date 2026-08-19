---
title: Buying Group-Based Marketing & Journey Management
description: Learn how to develop account-level journeys that qualify leads into buying groups to improve B2B marketing effectiveness.
solution: Journey Optimizer B2B Edition, Real-Time Customer Data Platform
exl-id: 2bf57f67-80c8-4368-98d2-05706427772d
---
# Buying group-based marketing & journey management

This guide describes the buying group-based marketing and journey management use case pattern, which uses [!DNL Adobe Journey Optimizer B2B Edition] and [!DNL Real-Time CDP B2B Edition] to implement account-level journey orchestration with buying group management. It is designed for solution architects, marketing technologists, and implementation engineers who need to understand what this pattern does, the business objectives it supports, the tactical use cases it enables, and the Adobe applications involved.

Unlike person-level journey patterns, this pattern operates at the account level, qualifying individual leads into buying groups associated with solution interests, scoring engagement at the buying group level, and orchestrating multi-step account journeys that progress accounts through pipeline stages toward sales readiness.

## Use case pattern

**Buying group-based marketing & journey management**

Develop account-level journeys that qualify leads into buying groups to improve B2B marketing effectiveness.

**Execution plan:** Account Identification > Buying Group Definition > Lead Qualification > Account Journey Execution > Engagement Scoring > Reporting

## Use case overview

B2B organizations face a fundamental challenge: purchase decisions are rarely made by a single individual. Complex B2B purchases involve multiple stakeholders -- decision makers, influencers, champions, budget holders, and technical evaluators -- who collectively form a "buying group." Traditional lead-based marketing treats each person independently, missing the critical signal of whether the right combination of roles within an account is engaged and ready to buy.

Buying group-based marketing and journey management addresses this by shifting the unit of orchestration from individual leads to accounts and buying groups. The pattern enables B2B marketers to define solution interests (the products or services being sold), create buying group templates that specify which roles are needed for a purchase decision, qualify incoming leads against those roles, score engagement at the buying group level, and orchestrate account journeys that respond to buying group completeness and readiness signals.

The desired outcome is improved pipeline quality and velocity: marketing delivers accounts to sales only when the right people within the account are engaged and the buying group is sufficiently complete, reducing wasted sales effort and accelerating deal progression.

## Key business objectives

This use case pattern supports the following business objectives.

### Improve lead qualification & conversion

Increase lead quality and accelerate pipeline progression through scoring, nurturing, and personalized follow-up.

**KPIs:** Lead Conversion, Prospect/Lead Conversion, Efficiency

[Learn more about improving lead qualification & conversion](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### Increase lead generation

Generate more qualified leads for the sales pipeline through forms, events, content, and multi-channel engagement.

**KPIs:** Prospects, Cost Per Lead, Lead Conversion

[Learn more about increasing lead generation](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### Increase revenue & sales

Drive top-line revenue growth through optimized digital channels, campaigns, and customer journeys.

**KPIs:** Revenue growth, pipeline velocity, deal close rate

[Learn more about increasing revenue & sales](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

## Example tactical use cases

The following are specific scenarios where this pattern can be applied.

- **Solution-specific buying group qualification** -- Define buying groups for each product line (for example, "Enterprise CRM," "Data Platform," "Security Suite") with role templates specifying required personas (Economic Buyer, Technical Evaluator, Champion, End User) and qualify leads from the CRM and marketing automation system against those roles.
- **Account journey for pipeline acceleration** -- Orchestrate a multi-step account journey that sends targeted nurture emails to under-engaged roles within a buying group, triggers sales alerts when engagement thresholds are reached, and transitions the account to a sales-ready stage.
- **Buying group completeness campaigns** -- Identify accounts where buying groups have missing roles (for example, no Economic Buyer identified) and launch targeted acquisition campaigns to engage the right personas within those accounts.
- **Cross-sell account journeys** -- After an initial deal closes, create new buying groups for complementary solution interests and orchestrate account journeys that nurture the expanded buying committee.
- **Re-engagement for stalled deals** -- Detect accounts where buying group engagement scores have declined and trigger re-engagement journeys with fresh content, executive outreach, or event invitations.
- **Sales and marketing alignment via CRM insights** -- Surface buying group status, engagement data, and account journey progress directly within [!DNL Salesforce] or [!DNL Dynamics 365] so sales representatives have real-time visibility into marketing-qualified accounts.
- **Event-driven buying group updates** -- Automatically update buying group membership and engagement scores when leads attend webinars, download whitepapers, visit pricing pages, or request demos.
- **Multi-region account coordination** -- Manage buying groups across global accounts where different regional contacts hold different roles, unifying engagement scoring across geographies.

## Key performance indicators

The following KPIs help measure the effectiveness of this use case pattern.

| KPI | Description | Measurement approach |
| --- | --- | --- |
| Buying Group Completeness Rate | Percentage of buying groups with all required roles filled | [!DNL AJO B2B] Analytics Dashboards: track role coverage per buying group |
| Buying Group Engagement Score | Aggregate engagement score across all members of a buying group | [!DNL AJO B2B] Engagement Scoring: person-level scores rolled up to buying group |
| Marketing Qualified Account (MQA) Rate | Percentage of accounts that reach the marketing-qualified threshold | Account journey exit criteria: accounts transitioning to sales-ready stage |
| Pipeline Velocity | Average time from buying group creation to sales-qualified opportunity | CRM integration: track stage transitions from [!DNL AJO B2B] to CRM pipeline |
| Lead-to-Buying Group Qualification Rate | Percentage of leads successfully qualified into buying group roles | [!DNL AJO B2B] Buying Group Management: qualified vs. unqualified lead ratio |
| Sales Alert Response Rate | Percentage of sales alerts that result in sales follow-up activity | CRM Sales Insights: track alert-to-activity conversion |
| Account Journey Completion Rate | Percentage of accounts that complete the intended journey path | [!DNL AJO B2B] Analytics Dashboards: journey completion metrics |
| Email Engagement Rate (B2B) | Open and click-through rates for B2B nurture emails | [!DNL AJO B2B] reporting: email delivery and engagement metrics |

## Applications

The following Adobe applications are used in this use case pattern.

- **[!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])** -- Orchestrates account-level journeys, manages buying groups with role templates and solution interests, scores engagement at the person and buying group level, authors B2B email content, sends SMS messages, configures sales alerts, and provides B2B analytics dashboards.
- **[!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])** -- Unifies account profiles from cross-source B2B data, resolves person-to-account relationships, evaluates account-level audiences, configures B2B-specific destinations ([!DNL Marketo Engage], [!DNL LinkedIn], CRM), and enforces data governance across B2B data.

## Related documentation

The following resources provide additional detail on the applications and capabilities referenced in this guide.

### [!DNL Journey Optimizer B2B Edition]

- [Journey Optimizer Edition documentation home](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [Buying groups overview](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [Solution interests](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Role templates](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [Create buying groups](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)
- [Buying group stages](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Account journeys overview](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [Account journey nodes](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [Sales alert emails](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/journey-content/email-channel/sales-alert-email)
- [CRM Sales Insights](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/accounts/buying-groups/incrm-insights)

### B2B email & content

- [B2B email authoring](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/journey-content/email-channel/email-authoring)
- [B2B SMS authoring](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/journey-content/sms-authoring)
- [AI Assistant for email authoring](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/journey-content/email-channel/ai-assistant-emails)

### B2B analytics & dashboards

- [Buying groups dashboard](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [Engagement dashboard](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [Intelligent dashboard](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [CJA B2B Edition overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### [!DNL RT-CDP B2B Edition]

- [RT-CDP B2B Edition overview](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [B2B schemas in Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [Marketo Engage source connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)

### Data foundation

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)

### Channel configuration

- [Get started with email configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configure SMS channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### Data governance & privacy

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### Destinations

- [Destinations overview](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Destinations catalog](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [LinkedIn Matched Audiences destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)

### Guardrails

- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Segmentation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [Ingestion guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

### Tutorials & getting started

- [AJO B2B Edition getting started](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [RT-CDP B2B Edition tutorial](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-tutorial)
