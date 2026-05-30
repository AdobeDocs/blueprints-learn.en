---
title: Multi-Step Orchestrated Journey
description: Learn how to guide a profile through a branching, multi-touch journey with waits, conditions, and multiple message actions over time.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 5667b188-1b20-4a85-aebb-74efd5f771a1
---
# Multi-step orchestrated journey

This guide describes the multi-step orchestrated journey use case pattern, which uses [!DNL Adobe Journey Optimizer] (AJO) and [!DNL Real-Time Customer Data Platform] (RT-CDP) to orchestrate branching, multi-touch customer journeys that deliver multiple messages over time. It is designed for solution architects, marketing technologists, and implementation engineers who need to understand what this pattern does, the business objectives it supports, the tactical use cases it enables, and the Adobe applications involved.

## Use case pattern

**Multi-Step Orchestrated Journey**

Guide a profile through a branching, multi-touch journey with waits, conditions, and multiple message actions over time.

**Execution plan:** Audience Evaluation > Journey Execution (multi-node) > Condition Branching > Message Delivery (xN) > Exit Criteria > Reporting

## Use case overview

Multi-step orchestrated journeys address business scenarios where a single message is insufficient to achieve the desired customer outcome. Instead of a one-time send, the journey guides each profile through a sequence of touchpoints -- emails, SMS messages, push notifications, or in-app messages -- spaced over days or weeks, with branching logic that adapts the path based on profile attributes, behavioral signals, or event data.

These journeys are the most complex campaign pattern in AJO. They combine audience-based or event-based entry with a canvas of action nodes (messages), condition nodes (branching logic), wait nodes (time delays), and exit criteria (conversion events or timeouts). Each profile progresses through the journey independently, at their own pace, receiving contextually relevant content at each step.

This pattern subsumes the simpler patterns -- batch outbound message activation for single-send campaigns and event-triggered messaging for single-event responses. Use this pattern when the use case requires nurturing a profile through multiple interactions over time.

>[!NOTE]
>If your journey requires dynamic selection of the optimal offer, content, or channel at individual decision points, see [Cross-channel journey with decisioning](cross-channel-journey-with-decisioning.md). That pattern extends this one with AJO Decisioning integration.

## Key business objectives

The following business objectives are supported by this use case pattern.

### Improve customer retention

Keep existing customers engaged and renewing through value-driven experiences and ongoing relationship nurturing.

**KPIs:** Retention, Customer Lifetime Value, Engagement

[Learn more about improving customer retention](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### Improve customer onboarding

Accelerate time-to-value for new customers with streamlined, personalized welcome experiences and activation journeys.

**KPIs:** Engagement, Retention, Conversion Rates

[Learn more about improving customer onboarding](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)

### Re-engage dormant customers

Win back inactive or lapsed customers with targeted reactivation campaigns based on behavioral signals.

**KPIs:** Engagement, Retention, Conversion Rates

[Learn more about improving customer retention](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### Recover abandoned carts and journeys

Re-engage users who dropped off during purchase, application, or enrollment flows with timely, personalized follow-ups.

**KPIs:** Conversion Rates, Incremental Revenue, Engagement

[Learn more about recovering abandoned carts and journeys](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)

## Example tactical use cases

The following scenarios illustrate common applications of the multi-step orchestrated journey pattern.

- **Customer onboarding series** -- Welcome email, followed by feature education, then an activation prompt over the first 14 days after registration
- **Re-engagement drip campaign** -- A reminder email, then an incentive offer, then a final notice for lapsed customers over 3 weeks
- **Loyalty milestone journey** -- Tier upgrade notification, followed by an exclusive offer, then a renewal reminder as the membership anniversary approaches
- **Win-back sequence** -- "We miss you" email, then a discount offer via email, then a final SMS reminder for lapsed purchasers
- **Product adoption journey** -- Trial welcome, usage tips, then an upgrade prompt as the trial period progresses
- **Subscription renewal sequence** -- 30-day notice, 7-day reminder, then an expiry-day message for upcoming subscription renewals
- **Post-purchase nurture** -- Thank-you email, how-to-use guide, cross-sell recommendation, then a review request over 30 days after purchase

## Key performance indicators

Use the following KPIs to measure the effectiveness of your multi-step orchestrated journey implementation.

| KPI | Description | Measurement approach |
| --- | --- | --- |
| Journey Completion Rate | Percentage of profiles that complete the full journey without early exit | Journey report: Exited (completed) / Entered |
| Step Conversion Rate | Percentage of profiles that progress from one step to the next | Per-node metrics in the journey report |
| Channel Engagement Rate | Open rates, click-through rates, and response rates at each touchpoint | Per-message delivery and engagement metrics |
| Exit Criteria Conversion Rate | Percentage of profiles that trigger the exit event (for example, purchase, sign-up) before journey timeout | Exit criteria hit count / Total entered |
| Time to Conversion | Average duration from journey entry to exit-criteria event | Journey analytics: entry timestamp to conversion event timestamp |
| Journey Drop-off Rate | Percentage of profiles that stop engaging at each step (fallout analysis) | CJA fallout visualization across journey steps |
| Retention / Re-engagement Rate | Percentage of targeted profiles who return to active status | Post-journey behavioral analysis in CJA |

## Applications

The following applications are used to implement this use case pattern.

- **[!DNL Adobe Journey Optimizer] (AJO)** -- Journey orchestration engine, message authoring, channel configuration, content experimentation, frequency and conflict management, and reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** -- Audience evaluation and definition for journey entry audiences, profile data for personalization and condition branching
- **[!DNL Adobe Experience Platform] (AEP)** -- Profile store, identity service, event data ingestion, and foundational data infrastructure

## Related documentation

The following resources provide additional detail on the capabilities used in this implementation.

### Journeys

- [Get started with journeys](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Create a journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journey properties](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Publish the journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [Test your journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)

### Journey activities

- [Read audience activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [General events](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Audience qualification events](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Condition activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Wait activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Add a message in a journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [End activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [Configure a custom action](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions)

### Entry and exit management

- [Journey entry management](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Exit criteria](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### Channel configuration

- [Get started with email configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Set up channel surfaces](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delegate subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Create IP pools](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP warmup plans](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Configure SMS channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configure push notification channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Message authoring and personalization

- [Create an email](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Design email content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Use Email Designer content components](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Helper functions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Work with content templates](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Work with content fragments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Preview and test your content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Content experimentation

- [Get started with content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Create a content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Content experiment report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Statistical calculations](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### Frequency, conflict, and priority

- [Frequency rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Business rules overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Get started with conflict and priority management](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Priority scores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Journey capping and arbitration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Identify potential conflicts](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Audiences and segmentation

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language reference](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/streaming-segmentation)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/edge-segmentation)

### Reporting and analytics

- [Journey live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Journey global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Work with Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

### Consent and governance

- [Consent in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Manage suppression list](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Data foundation

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Profile overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
