---
title: Batch Outbound Message Activation
description: Learn how to evaluate an audience and deliver a scheduled outbound message in a single batch execution.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 192853ce-02ab-46e6-9092-3db5354bc19c
---
# Batch outbound message activation

This guide describes the batch outbound message activation use case pattern, which uses [!DNL Adobe Journey Optimizer] (AJO) and [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) to deliver scheduled outbound messages to defined audience segments. It is designed for solution architects, marketing technologists, and implementation engineers who need to understand what this pattern does, the business objectives it supports, the tactical use cases it enables, and the Adobe applications involved.

Batch outbound message activation is the foundational campaign pattern for one-to-many outbound messaging. It covers the full lifecycle from audience definition through message delivery and performance analysis.

## Use case pattern

**Batch outbound message activation**

Evaluate an audience, then deliver a scheduled outbound message (email, SMS, push) to all qualifying profiles in a single batch execution.

**Execution plan:** Audience Evaluation > Message Authoring > Campaign Execution > Reporting

## Use case overview

Organizations frequently need to deliver a single message to a known audience segment at a specific time or in response to a system event. This pattern addresses that requirement by combining audience evaluation in [!DNL RT-CDP] with message authoring and campaign execution in [!DNL Journey Optimizer].

The business scenario is straightforward: define who should receive the message, create the message content with personalization, bind the audience and message into a campaign or journey, and execute the send on a schedule, via audience qualification, or through a system trigger. The result is a delivered message with full reporting on delivery, engagement, and conversion metrics.

This pattern applies whenever a business objective can be advanced by delivering a single message to a known audience in one execution. It differs from event-triggered messaging, which responds to real-time behavioral events, and from multi-step orchestrated journeys, which guide profiles through multiple touchpoints over time. Batch activation is the simplest campaign pattern and the most common starting point for outbound messaging use cases.

## Key business objectives

This section identifies the primary business objectives that batch outbound message activation supports.

### Increase email and campaign engagement

**Description:** Improve open rates, click-through rates, and overall campaign response through optimized content and targeting.

**KPIs:** Open Rates, Engagement, Conversion Rates

### Increase revenue and sales

**Description:** Drive top-line revenue growth through optimized digital channels, campaigns, and customer journeys.

**KPIs:** Conversion Rates, Incremental Revenue, Average Order Value

**Related business objective:** [Increase Revenue & Sales](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

### Streamline campaign execution

**Description:** Reduce campaign build time and simplify multi-channel campaign delivery through templates, automation, and standardized processes.

**KPIs:** Speed To Market, Efficiency, On Time Completion %

## Example tactical use cases

The following scenarios illustrate common applications of batch outbound message activation.

- **Sale announcement or promotional email blast** -- Broadcast a promotional offer to a segment of eligible customers on a scheduled date
- **Product launch push notification** -- Notify interested customers about a new product availability via push
- **Newsletter or digest email** -- Deliver periodic content roundups to subscriber audiences
- **Event registration invitation** -- Invite qualified prospects to webinars, conferences, or in-person events
- **Subscription renewal reminder email** -- Remind customers approaching renewal dates to take action
- **Loyalty program milestone notification** -- Congratulate members who reach loyalty tiers or point thresholds
- **Specific call-to-action email** -- Drive a targeted action such as completing a purchase, updating preferences, or registering for a program
- **SMS campaign for flash sale or time-limited offer** -- Send urgent, time-bound promotions via SMS to opted-in audiences

## Key performance indicators

The following table defines the KPIs used to measure campaign effectiveness.

| KPI | Description | Measurement approach |
| --- | --- | --- |
| Delivery Rate | Percentage of messages successfully delivered to recipients | Delivered / Sent x 100 |
| Open Rate | Percentage of delivered messages opened by recipients | Unique Opens / Delivered x 100 |
| Click-Through Rate (CTR) | Percentage of delivered messages where a link was clicked | Unique Clicks / Delivered x 100 |
| Click-to-Open Rate (CTOR) | Percentage of opened messages where a link was clicked | Unique Clicks / Unique Opens x 100 |
| Conversion Rate | Percentage of recipients who completed the desired action | Conversions / Delivered x 100 |
| Unsubscribe Rate | Percentage of recipients who unsubscribed after receiving the message | Unsubscribes / Delivered x 100 |
| Bounce Rate | Percentage of messages that could not be delivered | Bounces / Sent x 100 |
| Revenue per Email Sent | Revenue attributed to the campaign divided by messages sent | Total Revenue / Sent |

## Applications

The following applications are used to implement this pattern.

- **[!DNL Adobe Journey Optimizer] (AJO)** -- Message authoring, channel configuration, campaign execution, journey orchestration, content experimentation, frequency rules, and reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** -- Audience evaluation, consent and governance enforcement
- **[!DNL Adobe Experience Platform] (AEP)** -- Profile store, identity service, schemas, datasets, data collection

## Related documentation

This section provides comprehensive links to [!DNL Experience League] documentation organized by topic.

### Campaigns

- [Get started with campaigns](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Create a campaign](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [API-triggered campaigns](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### Journeys

- [Get started with journeys](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Read Audience journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### Channel configuration

- [Get started with email configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delegate subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Create IP pools](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP warmup plans](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Email surface settings](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configure SMS channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configure push notification channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Manage suppression list](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Message authoring and personalization

- [Create an email](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Design email content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Use Email Designer content components](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [Import or code email content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/code-content)
- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Helper functions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### Content management

- [Work with content templates](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Work with content fragments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Preview and test your content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Send email proofs](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [Email rendering](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)

### Content experimentation

- [Get started with content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Create a content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Content experiment report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Statistical calculations](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### Frequency and conflict management

- [Frequency rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Business rules overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Get started with conflict and priority management](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Priority scores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identify potential conflicts](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Journey capping and arbitration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### Audiences and segmentation

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Audience Composition](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language reference](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Reporting

- [Campaign live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Campaign global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Journey live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Journey global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Work with Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### Data governance and consent

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview)
- [Consent and preferences field group](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Consent in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Data modeling and identity

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Guardrails

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Ingestion guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Tutorials and getting started

- [Get started with Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/get-started)
- [Create your first campaign](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Create your first journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
