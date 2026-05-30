---
title: Event-Triggered Messaging
description: Learn how to deliver contextual, real-time messages in response to behavioral or system events.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 75137990-9848-40c0-abf3-adbd21d2de52
---
# Event-triggered messaging

This guide describes the event-triggered messaging use case pattern, which uses [!DNL Adobe Journey Optimizer] (AJO), [!DNL Real-Time Customer Data Platform] (RT-CDP), and [!DNL Adobe Experience Platform] (AEP) to deliver contextual, real-time messages in response to behavioral or system events. It is designed for solution architects, marketing technologists, and implementation engineers who need to understand what this pattern does, the business objectives it supports, the tactical use cases it enables, and the Adobe applications involved.

This pattern covers the full lifecycle from event ingestion and journey creation through message delivery and performance reporting.

## Use case pattern

This section describes the core pattern and the execution plan that drives event-triggered messaging.

**Event-Triggered Messaging**

Listen for a real-time behavioral or system event, then deliver a contextual message to the triggering profile.

**Execution plan:** Event Ingestion > Journey Entry > Condition Evaluation > Message Delivery > Reporting

## Use case overview

Event-triggered messaging delivers a contextual message in response to a real-time behavioral or system event. Unlike batch outbound message activation, which sends to a pre-evaluated audience on a schedule, this pattern listens for a qualifying event -- such as a cart abandonment, a browse session, a form submission, or a system status change -- and immediately enters the triggering profile into a journey that evaluates conditions and delivers a message.

The pattern relies on real-time event streaming into AEP (via Web SDK, Mobile SDK, or server-side API), a journey with a unitary event entry in AJO, and condition evaluation logic that determines whether and what to send. The message is typically sent within minutes of the triggering event, making this pattern ideal for time-sensitive, contextually relevant communications.

Organizations use this pattern to respond to customer actions in real time, increasing relevance and driving higher engagement and conversion rates compared to scheduled batch communications. Common scenarios include abandoned cart recovery, post-purchase follow-up, welcome messages after registration, and time-sensitive notifications like payment failures or price drop alerts.

## Key business objectives

The following business objectives are supported by this use case pattern.

**[Recover abandoned carts & journeys](../../business-objectives/customer-experience/recover-abandoned-carts-journeys.md)**

Re-engage users who dropped off during purchase, application, or enrollment flows with timely, personalized follow-ups.

| KPIs |
| --- |
| Conversion Rates, Incremental Revenue, Engagement |

**[Increase conversion rates](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

Improve the percentage of visitors and prospects who complete desired actions such as purchases, sign-ups, or form submissions.

| KPIs |
| --- |
| Conversion Rates, Lead Conversion, Cost Per Lead |

**[Deliver personalized customer experiences](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

Tailor content, offers, and messaging to individual preferences, behaviors, and lifecycle stage.

| KPIs |
| --- |
| Engagement, Conversion Rates, Customer Satisfaction (CSAT) |

**[Improve customer onboarding](../../business-objectives/customer-experience/improve-customer-onboarding.md)**

Accelerate time-to-value for new customers with streamlined, personalized welcome experiences and activation journeys.

| KPIs |
| --- |
| Engagement, Retention, Conversion Rates |

## Example tactical use cases

The following scenarios illustrate how event-triggered messaging can be applied across different business contexts.

- **Cart abandonment email or SMS** -- Send a reminder message when a customer adds items to their cart but does not complete the purchase within a defined time window
- **Browse abandonment follow-up** -- Re-engage visitors who viewed products or content but did not take a conversion action
- **Post-purchase thank-you or cross-sell** -- Deliver a confirmation and cross-sell recommendation immediately after a purchase event
- **Trial expiry reminder** -- Notify users approaching the end of a free trial with renewal or conversion messaging
- **Welcome message after registration** -- Send an immediate onboarding message when a new user registers or creates an account
- **Form submission confirmation** -- Acknowledge form submissions (contact requests, applications, enrollments) with a contextual confirmation
- **Payment failure notification** -- Alert customers when a recurring payment fails, prompting them to update payment information
- **App uninstall win-back push notification** -- Trigger a win-back message when a user uninstalls a mobile application
- **Booking or appointment confirmation** -- Send immediate confirmation after a booking, reservation, or appointment is scheduled
- **Price drop alert for wishlisted items** -- Notify customers when a product on their wishlist drops in price

## Key performance indicators

The following KPIs help measure the effectiveness of event-triggered messaging implementations.

| KPI | Description | Measurement approach |
| --- | --- | --- |
| Conversion Rate | Percentage of triggered message recipients who complete the desired action (purchase, sign-up, renewal) | Conversions / Messages Delivered * 100 |
| Incremental Revenue | Additional revenue attributable to event-triggered messages compared to no-send control groups | Revenue from triggered sends - Control group baseline |
| Open Rate | Percentage of delivered messages that are opened by recipients | Opens / Delivered * 100 |
| Click-Through Rate (CTR) | Percentage of delivered messages that generate at least one click | Clicks / Delivered * 100 |
| Time to Conversion | Average elapsed time between message delivery and conversion event | Avg(conversion timestamp - delivery timestamp) |
| Journey Completion Rate | Percentage of profiles that enter the journey and reach the message delivery step (not dropped by conditions or exits) | Profiles reaching delivery / Profiles entering journey * 100 |
| Message Suppression Rate | Percentage of qualifying profiles suppressed due to frequency caps, consent, or condition evaluation | Suppressed profiles / Total qualifying profiles * 100 |
| Bounce Rate | Percentage of messages that could not be delivered due to hard or soft bounces | Bounces / Sent * 100 |

## Applications

The following Adobe applications are used in this use case pattern.

- **[!DNL Adobe Journey Optimizer] (AJO)** -- Journey orchestration with unitary event entry, condition evaluation, wait steps, message authoring, channel configuration, frequency governance, and delivery reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** -- Audience evaluation for condition-based filtering within journeys, consent and governance enforcement, profile enrichment
- **[!DNL Adobe Experience Platform] (AEP)** -- Real-time event ingestion via Web SDK, Mobile SDK, or server-side API; data modeling; identity resolution; Edge Network

## Related documentation

The following resources provide additional detail on the capabilities used in this implementation.

### Journey orchestration

- [Get started with journeys](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Create a journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journey properties](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [General events](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Audience qualification events](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Condition activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Wait activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Add a message in a journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Exit criteria](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Journey entry management](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Test your journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Publish the journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

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
- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Helper functions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Work with content templates](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Work with content fragments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Preview and test your content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Create an SMS message](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Design a push notification](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### Frequency and business rules

- [Frequency rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Business rules overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Capping API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/channel-surfaces/capping)

### Conflict and priority management

- [Get started with conflict and priority management](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Identify potential conflicts](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Priority scores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Journey capping and arbitration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### Reporting and performance

- [Journey live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Journey global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### Data collection and ingestion

- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Mobile SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Edge Network Server API overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Streaming ingestion overview](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)

### Data modeling and schemas

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### Identity and profile

- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Identity namespaces overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Identity graph linking rules](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Profile overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Segmentation and audiences

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

### Data governance and consent

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview)
- [Consent and preferences field group](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Consent in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Computed attributes

- [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Computed attributes UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)

### Monitoring and observability

- [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### Guardrails

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Ingestion guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Tutorials and guides

- [Create a journey tutorial](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Install Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
