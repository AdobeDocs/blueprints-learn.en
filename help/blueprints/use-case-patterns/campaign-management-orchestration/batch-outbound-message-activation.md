---
title: Batch Outbound Message Activation
description: Learn how to evaluate an audience and deliver a scheduled outbound message in a single batch execution.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 192853ce-02ab-46e6-9092-3db5354bc19c
---
# Batch outbound message activation

This guide provides a complete implementation reference for delivering scheduled outbound messages to defined audience segments using [!DNL Adobe Journey Optimizer] (AJO) and [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP). It is designed for solution architects, marketing technologists, and implementation engineers who need to understand all viable implementation approaches, the decision considerations that drive each choice, and where to find detailed documentation on [!DNL Adobe Experience League].

Batch outbound message activation is the foundational campaign pattern for one-to-many outbound messaging. It covers the full lifecycle from audience definition through message delivery and performance analysis. This guide presents three implementation options -- Scheduled Campaign, Audience-Triggered Journey, and API-Triggered Campaign -- and provides structured decision guidance for selecting the right approach for each use case.

It provides implementation options, trade-off analysis, UI navigation paths, and [!DNL Experience League] documentation references.

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

## Use case pattern

**Batch outbound message activation**

Evaluate an audience, then deliver a scheduled outbound message (email, SMS, push) to all qualifying profiles in a single batch execution.

**Function chain:** Audience Evaluation > Message Authoring > Campaign Execution > Reporting

## Applications

The following applications are used to implement this pattern.

- **[!DNL Adobe Journey Optimizer] (AJO)** -- Message authoring, channel configuration, campaign execution, journey orchestration, content experimentation, frequency rules, and reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** -- Audience evaluation, consent and governance enforcement
- **[!DNL Adobe Experience Platform] (AEP)** -- Profile store, identity service, schemas, datasets, data collection

## Foundational functions

The following foundational capabilities must be in place for this use case pattern. For each function, the status indicates whether it is typically required, assumed to be pre-configured, or not applicable.

| Foundational Function | Status | What Must Be in Place | Experience League Reference |
| --- | --- | --- | --- |
| Administration & Governance | Assumed in Place | AJO sandbox provisioned with an active channel configuration. Sending subdomain delegated, IP pool assigned, and IP warmup complete. User roles with campaign/journey creation permissions assigned. | [Sandboxes overview](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Access control overview](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Data Modeling & Preparation | Required | XDM Individual Profile schema with attributes used for segmentation and personalization (e.g., name, email, preferences, tier). XDM ExperienceEvent schema capturing the target conversion action (e.g., `commerce.purchases`, `web.webInteraction`) for post-campaign conversion tracking. Profile-enabled datasets for both schemas. | [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Data Sources & Collection | Assumed in Place | Web SDK or Analytics tagging on the CTA destination must be active to capture conversion events. Streaming or batch ingestion pipelines for profile attributes must be operational. | [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Identity & Profile Configuration | Assumed in Place | Identity namespaces for email (and any cross-device identifiers) configured. Profile attributes required for personalization mapped, ingested, and resolvable at send time. Merge policy configured. | [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Audience Definition & Segmentation | Required | Target audience defined in RT-CDP using Segment Builder or Audience Composition. Audience published and evaluating with a non-zero population. Covered in Implementation Phase 1 via RT-CDP Audience Evaluation. | [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Supporting functions

The following capabilities augment this use case pattern but are not required for core execution.

| Supporting Function | Status | Why It Matters | Experience League Reference |
| --- | --- | --- | --- |
| Computed / Derived Attribute Creation | Recommended | Computed attributes such as days since last purchase, lifetime order count, or engagement score improve audience precision and enable richer message personalization. | [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Recommended | Data retention policies (expiration) should be in place for event datasets that drive conversion tracking. Consent schema fields must be configured for channel-level opt-in/opt-out enforcement. | [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Consent and preferences field group](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents) |
| Data Usage Labeling & Enforcement | Recommended | Governance labels on PII fields used in personalization ensure compliance during activation. Prevents unauthorized use of sensitive profile data in message content or audience exports. | [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) |
| Monitoring & Observability | Included | Real-time send monitoring is part of the Reporting phase. Platform-level alerting on ingestion failures or license usage provides operational visibility beyond campaign-level metrics. | [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home), [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| Reporting & Analysis | Included | Campaign and journey reports are covered in the Reporting phase. For deeper cross-channel analysis, CJA integration provides funnel analysis, attribution modeling, and cohort analysis beyond AJO built-in reports. | [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Application functions

This plan exercises the following functions from the application function catalog. Functions are mapped to implementation phases rather than numbered steps.

### [!DNL Journey Optimizer] (AJO)

| Function | Implementation Phase | Description |
| --- | --- | --- |
| Channel Configuration | Phase 2: Channel Configuration | Configure or validate the channel surface (email, SMS, or push) including subdomain, IP pool, sender settings, and suppression list |
| Message Authoring | Phase 3: Message Authoring | Create message content using templates, the Email Designer, personalization expressions, conditional content blocks, and content fragments |
| Campaign Execution | Phase 4: Campaign or Journey Creation | Create, configure, and activate a scheduled or API-triggered campaign that binds audience, message, and execution schedule |
| Content Experimentation | Phase 4: Campaign or Journey Creation | Optionally configure A/B or multivariate content experiments to optimize message performance |
| Frequency & Business Rules | Phase 4: Campaign or Journey Creation | Optionally apply frequency capping rules to prevent over-messaging across concurrent campaigns |
| Conflict & Priority Management | Phase 4: Campaign or Journey Creation | Assign priority scores and configure conflict resolution when multiple campaigns target overlapping audiences |
| Reporting & Performance Analysis | Phase 5: Reporting & Performance Analysis | Monitor delivery metrics via live reports during execution and analyze campaign performance via historical reports after completion |

### [!DNL Real-Time CDP] (RT-CDP)

| Function | Implementation Phase | Description |
| --- | --- | --- |
| Audience Evaluation | Phase 1: Audience Evaluation | Define audience rules using Segment Builder or Audience Composition, select the evaluation method (batch, streaming, or edge), and validate audience population |
| Consent & Governance Enforcement | Phase 1: Audience Evaluation | Enforce consent preferences and data usage policies to ensure only consented profiles receive the campaign message |

## Prerequisites

Complete the following before beginning implementation.

- [ ] AJO sandbox is provisioned and active
- [ ] Sending subdomain is delegated and verified (SPF, DKIM, DMARC configured)
- [ ] IP pool is assigned and warmed up for production sending volume
- [ ] At least one active channel surface (email, SMS, or push) exists
- [ ] User accounts have campaign/journey creation and content authoring permissions
- [ ] XDM profile schema includes attributes needed for audience segmentation and message personalization
- [ ] XDM event schema captures conversion events for post-campaign tracking
- [ ] Profile data is ingested and unified via Identity Service
- [ ] Web SDK or Analytics tagging is active on the CTA destination page to capture conversion events
- [ ] Consent fields are populated on profiles for the target messaging channel
- [ ] Content assets (images, logos, brand guidelines) are available for message design

## Implementation options

This section describes three implementation options for batch outbound message activation, along with a comparison and decision guidance.

### Option A: Scheduled campaign (one-time batch send)

**Best for:** Date-anchored sends -- sale announcements, product launches, event registration deadlines, renewal reminders, newsletter blasts, and any send where the execution date is known in advance.

**How it works:**

A scheduled campaign is the simplest variant of batch outbound messaging. The marketer defines the target audience, authors the message content, sets a send date and time, and activates the campaign. At the scheduled execution time, AJO evaluates the audience to determine the current qualifying population, then delivers the message to all qualifying profiles in a single batch.

The entire configuration happens within the AJO Campaigns interface -- there is no journey canvas, no branching logic, and no wait steps. This makes scheduled campaigns the fastest to configure and the easiest to manage. The campaign can be set for immediate execution, a specific future date/time, or a recurring schedule (daily, weekly, monthly).

**Key considerations:**

- Audience is evaluated at execution time, so profiles that qualify between scheduling and execution are included
- No branching, wait, or condition logic is available -- the message is delivered to all qualifying profiles
- Supports content experimentation (A/B testing) directly within the campaign configuration
- Campaign properties include a priority score for conflict resolution with other campaigns

**Advantages:**

- Simplest configuration with the least overhead
- Fastest time-to-launch for straightforward batch sends
- Built-in support for recurring schedules
- Content experimentation natively supported
- Audience re-evaluated at execution time for freshness

**Limitations:**

- No wait steps, conditions, or branching before delivery
- Cannot react to profile behavior between scheduling and execution
- Single message action only -- no multi-touch sequences
- Cannot be edited once activated (must duplicate and modify)

**Experience League:**

- [Get started with campaigns](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Create a campaign](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

### Option B: Audience-triggered journey

**Best for:** Behavior-driven sends -- abandoned cart notifications, trial expiry reminders, milestone celebrations, qualification-based outreach, and any send where the trigger is audience qualification or a business event rather than a calendar date.

**How it works:**

An audience-triggered journey uses the journey canvas to deliver a message when a profile qualifies for a defined audience or fires a qualifying event. The journey entry is triggered by audience membership changes (profiles entering the audience) rather than a fixed schedule. The journey canvas allows optional wait steps, condition branches, and suppression logic before the message action, providing more flexibility than a scheduled campaign.

The journey is configured in the AJO Journeys interface using the Read Audience entry event. When profiles qualify for the audience, they enter the journey and proceed through the canvas nodes. A simple implementation may contain only a single email action node, making it functionally similar to a scheduled campaign but with audience-qualification-based entry timing. More complex implementations can add wait nodes (e.g., wait 24 hours after qualification), condition nodes (e.g., check if profile opened a previous email), or suppression logic before the message delivery.

**Key considerations:**

- Journey entry is triggered by audience qualification, not a calendar date
- The journey canvas supports wait, condition, and split nodes for pre-delivery logic
- Journey re-entry rules control whether profiles can enter the journey multiple times
- Journey arbitration settings determine behavior when a profile is already in a competing journey

**Advantages:**

- Flexible entry timing based on audience qualification rather than fixed schedule
- Wait and condition nodes allow pre-delivery logic (e.g., delay, check, suppress)
- Re-entry controls prevent duplicate sends to the same profile
- Can be extended into a multi-step journey if the use case evolves
- Supports journey-level reporting with entry, exit, and node-level metrics

**Limitations:**

- More configuration overhead than a scheduled campaign
- Journey canvas adds complexity even for single-message use cases
- Journey must be published and cannot be edited while live (must create a new version)
- Entry capping may limit the number of profiles that enter within a time window

**Experience League:**

- [Get started with journeys](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Read Audience journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### Option C: API-triggered campaign

**Best for:** System-initiated sends -- order confirmation with upsell content, support ticket resolution follow-ups, transactional notifications with marketing content, and any send where the triggering event originates from an external system at a specific moment.

**How it works:**

An API-triggered campaign is activated via a REST API call at the moment a triggering system event occurs. The campaign is pre-configured in AJO with message content and channel settings, but instead of binding a pre-defined audience, the API call specifies the recipient profiles and can pass contextual data that populates dynamic message parameters.

This variant is ideal when the send timing is determined by an external system (e.g., an order management system, a CRM workflow, or a support platform) rather than by audience evaluation or a calendar schedule. Contextual data passed in the API trigger payload -- such as order details, ticket numbers, or product names -- can personalize the message content using contextual attributes that are not stored on the profile.

**Key considerations:**

- No pre-bound audience is required -- recipients are specified in the API trigger request
- Contextual data in the trigger payload enables dynamic personalization beyond profile attributes
- The campaign must be of type "API-triggered" and must be activated before it can receive trigger requests
- Each API trigger request supports up to 20 profile recipients
- Audience Evaluation (Phase 1) may be skipped since recipients come from the API call

**Advantages:**

- Real-time triggering from external systems at the moment of the event
- Contextual personalization with data not stored on the profile (order details, ticket info)
- No audience evaluation overhead -- recipients are specified directly
- Supports transactional + marketing hybrid messaging

**Limitations:**

- Requires external system integration to send the API trigger
- Maximum 20 recipients per API trigger request
- No built-in audience evaluation -- the calling system must determine recipients
- More technical complexity due to API integration requirements
- Content experimentation is not supported for API-triggered campaigns

**Experience League:**

- [API-triggered campaigns](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)
- [Trigger campaigns using APIs](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### Option comparison

The following table compares the three implementation options across key criteria.

| Criteria | Option A: Scheduled Campaign | Option B: Audience-Triggered Journey | Option C: API-Triggered Campaign |
| --- | --- | --- | --- |
| Best for | Date-anchored sends (promotions, launches, newsletters) | Behavior-driven sends (qualification events, milestones) | System-initiated sends (order confirmations, transactional) |
| Complexity | Low | Medium | Medium-High |
| Trigger type | Calendar date/time or recurring schedule | Audience qualification or business event | External system API call |
| Pre-delivery logic | None | Wait, condition, split nodes available | None (logic in calling system) |
| Audience binding | Pre-defined RT-CDP audience | Pre-defined RT-CDP audience | Recipients specified in API payload |
| Contextual data | Profile attributes only | Profile attributes only | Profile attributes + API payload data |
| Content experimentation | Supported | Supported (on message action) | Not supported |
| Frequency capping | Supported | Supported | Supported |
| Re-entry control | N/A (one-time execution) | Configurable re-entry rules | N/A (per-request) |
| Configuration interface | AJO Campaigns | AJO Journeys | AJO Campaigns + external system |
| Requires | Audience, channel surface, message | Audience, channel surface, message, journey canvas | Channel surface, message, API integration |

### Choose the right option

Use the following decision flow to select the appropriate implementation option:

1. **Is the send triggered by an external system event (e.g., order placed, ticket resolved)?** If yes, choose **Option C: API-Triggered Campaign**. This is the only option that supports system-initiated triggers with contextual payload data.

2. **Is the send anchored to a specific calendar date or recurring schedule?** If yes, choose **Option A: Scheduled Campaign**. This is the simplest and fastest to configure for date-driven sends.

3. **Does the send need to react to audience qualification or require pre-delivery logic (wait, condition, suppression)?** If yes, choose **Option B: Audience-Triggered Journey**. The journey canvas provides the flexibility for behavior-driven entry and pre-delivery decision logic.

4. **Is the send a simple broadcast to a known audience with no special timing or logic requirements?** Choose **Option A: Scheduled Campaign** for the lowest configuration overhead.

## Implementation phases

This section walks through each phase of implementation in detail, including decision points and option-specific guidance.

### Phase 1: Evaluate the audience

**Application function:** RT-CDP: Audience Evaluation

This phase defines and evaluates the target audience segment that will receive the campaign message. It determines which profiles qualify for the send based on profile attributes, behavioral signals, and suppression rules.

>[!NOTE]
>For Option C (API-Triggered Campaign), this phase may be skipped if recipients are specified entirely in the API trigger payload. However, even API-triggered campaigns benefit from having a suppression audience to filter out profiles that should not receive messages.

#### Decision: Audience criteria

What conditions define the target audience? What suppression rules should exclude profiles?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Profile attribute-based audience | Target audience is defined by demographic, preference, or status attributes | Simplest to build; supports all evaluation methods |
| Behavioral event-based audience | Target audience is defined by actions taken (or not taken) within a time window | Requires event data ingestion; time-window rules may limit streaming eligibility |
| Audience Composition (derived audience) | Target audience requires rank, split, exclude, or enrich operations across multiple source audiences | More powerful but batch-only evaluation; limited to 10 compositions per sandbox |

#### Decision: Evaluation method

How quickly must the audience update to reflect new qualifying or disqualifying profiles?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Batch evaluation | Scheduled campaigns where audience freshness within a day is acceptable; large, complex audiences | Default for most segment types; processes on a daily schedule or on-demand; supports all segment rule functions |
| Streaming evaluation | Audience-triggered journeys where profiles must enter near-real-time as they qualify | Automatic for eligible segment rule expressions; not all segment types qualify for streaming; near-real-time latency (seconds to minutes) |
| Edge evaluation | Not typical for this pattern (used for same-page personalization) | Limited segment rule support; millisecond latency; relevant only if combining with web personalization patterns |

#### Decision: Merge policy

Which merge policy should the audience use to resolve profile fragments?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Default merge policy (timestamp ordered) | Most common for batch campaign use cases | Most recent attribute value wins; standard for outbound messaging |
| Custom merge policy (dataset precedence) | When a specific data source should take priority for key attributes | Useful when CRM data should override web-collected data for certain fields |

#### UI navigation

Customer > Audiences > Create audience > Build rule

#### Key configuration details

- Define the audience using Segment Builder with segment rules for profile attributes, behavioral events, and segment membership
- Apply suppression rules to exclude profiles who have already converted, recently received a similar message, or have opted out
- Verify the audience has a non-zero population before proceeding
- For batch campaigns, ensure a segment evaluation schedule is active or trigger on-demand evaluation
- Confirm consent fields (`consents.marketing.email.val`, `consents.marketing.sms.val`, etc.) are populated and enforced

#### Where options diverge

**For Option A (Scheduled Campaign):**

Batch evaluation is typical. The audience is re-evaluated at campaign execution time, so the most current qualifying population is targeted. Define the audience and verify its population, then proceed to campaign creation.

**For Option B (Audience-Triggered Journey):**

Streaming evaluation is preferred so profiles enter the journey as they qualify. Ensure the segment rule expression is streaming-eligible (simple event triggers, attribute comparisons, limited time windows). Configure the audience and verify streaming qualification is active.

**For Option C (API-Triggered Campaign):**

Audience evaluation may be skipped entirely. If used, create a suppression audience to filter profiles that should not receive the message (e.g., recently unsubscribed, already converted). The calling system determines the primary recipients.

#### Experience League documentation

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Audience Composition](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language reference](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Phase 2: Configure the channel

**Application function:** AJO: Channel Configuration

This phase validates or creates the channel surface (preset) that defines the sending infrastructure for the message -- subdomain, IP pool, sender identity, reply-to address, and unsubscribe settings. A valid channel surface must exist before message content can be authored or campaigns can be activated.

#### Decision: Target channel

Which messaging channel will deliver the campaign message?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Email | Most campaign types -- newsletters, promotions, notifications, renewals | Requires delegated subdomain, warmed IP pool, sender identity, and unsubscribe configuration |
| SMS | Time-sensitive or brief messages -- flash sales, appointment reminders, OTP codes | Requires SMS provider credentials (Sinch, Twilio, or Infobip); higher per-message cost; stricter consent requirements |
| Push notification | Mobile-engaged audiences -- app updates, location-based offers, in-app feature announcements | Requires APNs (iOS) and/or FCM (Android) credentials; users must have app installed with push permissions granted |

#### Decision: Channel surface selection

Does a suitable channel surface already exist in the sandbox, or must a new one be created?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Reuse existing surface | A verified, active surface matches the required subdomain, sender identity, and channel type | Fastest path; no DNS or warmup configuration needed |
| Create new surface | No existing surface matches requirements, or a new subdomain/sender identity is needed | Requires subdomain delegation, DNS verification, IP pool assignment, and potentially IP warmup (2-4 weeks for new IPs) |

#### Decision: Unsubscribe handling

How should opt-out be managed on the channel surface?

| Option | When to choose | Considerations |
| --- | --- | --- |
| One-click list-unsubscribe header | Standard for all marketing emails; required by major ISPs (Gmail, Yahoo) for deliverability | Adds a mailto: or URL-based unsubscribe header that ISPs surface as an "Unsubscribe" button |
| Unsubscribe link in email body | Required as a fallback for email clients that do not support list-unsubscribe headers | Include an unsubscribe link in the email footer alongside the list-unsubscribe header |
| Both (recommended) | Best practice for all marketing emails | Maximum compliance coverage and best deliverability profile |

#### UI navigation

Administration > Channels > Channel surfaces > Create surface (or select existing)

#### Key configuration details

- For email: bind the sending subdomain, IP pool, sender name, sender email, reply-to address, and BCC address (if audit copy is required)
- For SMS: configure SMS provider credentials and short code or long code settings
- For push: configure APNs and/or FCM credentials with the app's certificate or server key
- Verify the channel surface shows "Active" status before proceeding
- Confirm DNS records (SPF, DKIM, DMARC) are correctly configured for the sending subdomain
- Review the suppression list for stale entries; clean up before activation

#### Experience League documentation

- [Get started with email configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delegate subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Create IP pools](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP warmup plans](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Email surface settings](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configure SMS channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configure push notification channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Manage suppression list](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Phase 3: Author the message

**Application function:** AJO: Message Authoring

This phase creates the message content that will be delivered to the audience. It includes selecting or creating a content template, designing the message layout, adding personalization using profile attributes, configuring conditional content blocks for audience-specific variations, creating reusable content fragments, and previewing/testing the message with sample profiles.

#### Decision: Content approach

How should the message content be created?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Start from existing template | Brand-approved templates exist and match the message type (promotional, transactional, newsletter) | Fastest authoring path; ensures brand consistency; templates are sandbox-specific |
| Design from scratch | No suitable template exists or the message requires a unique layout | More flexibility but more effort; consider saving as a template for reuse |
| Import HTML | Message design was created externally (e.g., in a design tool) and HTML is ready for import | Preserves external design; may need adjustments for AJO compatibility and personalization tokens |

#### Decision: Personalization depth

Which profile attributes should personalize the message, and are conditional content blocks needed?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Basic personalization (name, greeting) | Simple campaigns where generic content with a personalized salutation is sufficient | Low effort; minimal risk of rendering issues; uses standard profile attributes |
| Attribute-based personalization | Message content varies based on profile attributes (tier, preference, location) | Requires verified XDM paths; test with multiple profiles to ensure all variations render correctly |
| Conditional content blocks | Different content sections must be shown to different audience segments within the same message | More complex authoring; each condition needs a default fallback; test all permutations |
| Contextual personalization (Option C only) | API-triggered campaigns need to render data passed in the trigger payload (order details, ticket info) | Contextual attributes are not stored on the profile; define placeholders in the message and map to payload fields |

#### Decision: Fragment strategy

Should shared content blocks be created as reusable fragments?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Reusable fragments | Headers, footers, legal disclaimers, or unsubscribe blocks are shared across multiple campaigns | Changes to a fragment propagate to all messages referencing it (live and draft); maximum 30 fragments per message |
| Inline content | One-off message with no shared elements across other campaigns | Simpler for single-use content; no propagation risk |

#### UI navigation

Campaigns > Select campaign > Edit content > Email Designer (or SMS/Push editor)

#### Key configuration details

- Design the message layout using drag-and-drop content components (text, image, button, divider, columns)
- Set the email header properties: subject line, preheader text, and sender surface
- Insert personalization expressions using Handlebars syntax (e.g., `{{profile.person.name.firstName}}`)
- Configure helper functions for formatting (date, number, string manipulation)
- Add conditional content rules to display different content based on profile attributes or segment membership
- Configure default fallback content when no conditions are met
- For SMS, compose the message body within character limit considerations
- For push, configure title, body, image, and action (deep link or URL)
- Preview the message with sample profiles to verify personalization rendering
- Send proof emails to internal stakeholders for review
- Test rendering across email clients using the email rendering feature

#### Experience League documentation

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
- [Send email proofs](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [Email rendering](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)
- [Create an SMS message](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Design a push notification](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### Phase 4: Create the campaign or journey

**Application function:** AJO: Campaign Execution (Options A and C) or AJO: Journey Orchestration (Option B)

This phase creates the campaign or journey that binds the audience, message, and execution mechanism into a deliverable unit. This is where the three implementation options diverge most significantly.

#### Decision: Content experimentation

Should the campaign include an A/B test or multivariate experiment to optimize message performance?

| Option | When to choose | Considerations |
| --- | --- | --- |
| No experiment | Single message variant with high confidence in content effectiveness | Simplest configuration; fastest activation |
| A/B test (2 variants) | Testing subject lines, CTAs, or content layouts with a clear hypothesis | Split traffic 50/50 or with a weighted allocation; requires sufficient audience size for statistical significance |
| Multivariate test (3+ variants) | Testing multiple content elements simultaneously | Requires larger audiences; longer duration to reach confidence threshold; maximum 10 treatments per experiment |

#### Decision: Frequency capping

Should this campaign respect global frequency capping rules to prevent over-messaging?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Apply frequency rules | Campaign is part of a broader messaging program with multiple concurrent sends | Prevents customer fatigue; profiles that exceed the cap are suppressed from delivery |
| Exempt from capping | Campaign is time-critical or transactional and must reach all qualifying profiles regardless of recent message history | Use sparingly; exempting campaigns from frequency rules risks over-messaging |

#### Decision: Priority score

What priority level should this campaign have relative to other active campaigns?

| Option | When to choose | Considerations |
| --- | --- | --- |
| High priority (75-100) | Critical campaigns -- major product launches, limited-time offers, regulatory notifications | Will take precedence over lower-priority campaigns when conflicts arise |
| Medium priority (25-74) | Standard marketing campaigns -- newsletters, engagement campaigns, general promotions | Balanced against other campaigns; may be suppressed if a higher-priority campaign conflicts |
| Low priority (0-24) | Nice-to-have sends -- informational updates, secondary promotions | Will be suppressed in favor of higher-priority campaigns |

#### Where options diverge

**For Option A (Scheduled Campaign):**

**UI navigation:** Campaigns > Create Campaign > Scheduled > Marketing

1. Create a new scheduled marketing campaign
2. Select the target audience from the audience picker
3. Select the channel surface and link the authored message content
4. Configure the execution schedule: immediate, specific date/time, or recurring
5. Optionally enable content experimentation and define treatment variants
6. Optionally configure frequency capping and priority score
7. Review the complete campaign configuration
8. Activate the campaign

**For Option B (Audience-Triggered Journey):**

**UI navigation:** Journeys > Create Journey

1. Create a new journey with a "Read Audience" entry event
2. Select the target audience as the entry source
3. Configure re-entry rules (allow re-entry, one-time entry, or re-entry after wait period)
4. Optionally add wait nodes (e.g., wait 24 hours after qualification)
5. Optionally add condition nodes (e.g., check if profile meets additional criteria)
6. Add the message action node and select the channel surface and authored content
7. Configure exit criteria (e.g., profile converts, profile unsubscribes)
8. Optionally enable content experimentation on the message action
9. Review and publish the journey

**For Option C (API-Triggered Campaign):**

**UI navigation:** Campaigns > Create Campaign > API-triggered

1. Create a new API-triggered campaign
2. Select the channel surface and link the authored message content
3. Configure contextual personalization tokens for data that will be passed in the API trigger payload
4. Review and activate the campaign
5. Note the campaign ID for use in the external system's API trigger integration
6. The calling system sends trigger requests to the campaign endpoint with recipient profiles and contextual data

#### Experience League documentation

- [Create a campaign](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Get started with campaigns](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [API-triggered campaigns](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)
- [Get started with journeys](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Read Audience journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Get started with content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Create a content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Frequency rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Priority scores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identify potential conflicts](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Phase 5: Analyze reporting and performance

**Application function:** AJO: Reporting & Performance Analysis

This phase monitors delivery metrics during execution via live reports and analyzes campaign performance after completion via historical reports. Optionally configure CJA integration for deeper cross-channel analysis.

#### Decision: Reporting method

What level of reporting is needed for this campaign?

| Option | When to choose | Considerations |
| --- | --- | --- |
| AJO native reports only | Standard delivery and engagement metrics are sufficient (sent, delivered, opens, clicks, bounces) | No additional configuration; reports are built into the campaign/journey UI |
| AJO native reports + CJA analysis | Cross-channel impact analysis, attribution modeling, or funnel analysis is needed beyond delivery metrics | Requires a CJA connection and data view linked to AJO datasets; provides deeper analytical capability |
| CJA programmatic reporting | Automated dashboards or scheduled report delivery is needed for stakeholders | Requires CJA Reporting API integration; useful for executive dashboards and recurring performance summaries |

#### Decision: Conversion tracking

How will campaign success be measured beyond delivery and engagement metrics?

| Option | When to choose | Considerations |
| --- | --- | --- |
| No conversion tracking | Campaign goal is awareness or engagement (opens, clicks) with no specific downstream action | Simplest; no additional event tracking required |
| Web conversion tracking | Campaign CTA links to a web page where conversion events (purchase, registration, form submit) are tracked | Requires Web SDK or Analytics tagging on the destination page; events must be captured in AEP datasets |
| Custom conversion event | Campaign success is measured by a business-specific event not captured on the web (e.g., in-store purchase, call center interaction) | Requires the custom event to be ingested into AEP and included in reporting datasets |

#### UI navigation

- Live reports: Campaigns > Select campaign > Live report (or Journeys > Select journey > Live report)
- Historical reports: Campaigns > Select campaign > All time report (or Journeys > Select journey > All time report)

#### Key configuration details

- Access live reports during campaign execution to monitor real-time delivery and engagement
- Review key metrics: Sent, Delivered, Bounces, Opens, Clicks, Unsubscribes (email); Sent, Delivered, Clicks, Errors (SMS); Sent, Delivered, Opens, Actions (push)
- After campaign completion, access historical (all time) reports for comprehensive analysis
- Analyze the delivery funnel: Targeted > Sent > Delivered > Opens > Clicks
- Review error and exclusion reasons to identify delivery issues
- If content experimentation was enabled, review experiment results and wait for statistical confidence before declaring a winner
- For CJA integration, verify the AJO data view includes the relevant AJO datasets (Message Feedback Event Dataset, Email Tracking Experience Event Dataset)

#### Experience League documentation

- [Campaign live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Campaign global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Journey live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Journey global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Content experiment report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Work with Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Implementation considerations

This section covers guardrails, common pitfalls, best practices, and trade-off decisions.

### Guardrails and limits

- Maximum of 500 active live campaigns per sandbox -- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum of 4,000 segment definitions per sandbox -- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximum of 10 channel surfaces per channel type per sandbox
- API-triggered campaigns support up to 20 profile recipients per trigger request
- Campaigns cannot be edited once activated -- duplicate and modify instead
- Live reports refresh every 60 seconds and show the last 24 hours of data
- Historical reports may take up to 2 hours to fully populate after campaign completion
- Maximum of 10 treatments (variants) per content experiment
- Maximum of 10 capping configurations per sandbox
- Maximum of 30 content fragments per message
- Maximum email size of 100 KB is recommended for optimal deliverability
- IP warmup plans should ramp volume gradually over 2-4 weeks for new IPs
- Suppression list entries are retained for a configurable period (default 14 days for soft bounces)

### Common pitfalls

- **Sending before IP warmup is complete:** New IP addresses that send high volumes immediately will be flagged by ISPs, resulting in poor deliverability and potential blacklisting. Always complete an IP warmup plan before production sends on new IPs.

- **Not testing personalization across multiple profiles:** Personalization tokens that work for one test profile may fail for others if the referenced XDM path does not exist or is null on some profiles. Always preview with multiple test profiles that represent different data completeness levels.

- **Skipping suppression list review:** Stale suppression list entries may block delivery to valid addresses, while missing entries may result in delivery to invalid addresses that generate bounces. Review and clean the suppression list before major campaigns.

- **Ignoring frequency capping for promotional campaigns:** Sending a promotional campaign without frequency capping while other campaigns are also active can result in profiles receiving multiple messages in a short period, driving unsubscribes and spam complaints.

- **Scheduling campaigns without verifying audience population:** Activating a campaign before confirming the target audience has a non-zero evaluated population results in zero messages delivered. Always verify audience size before activation.

- **Using batch evaluation for audience-triggered journeys:** If the journey uses a Read Audience entry with batch evaluation, profiles will not enter in near-real-time. Use streaming evaluation for the audience when near-real-time journey entry is required.

- **Not configuring consent enforcement:** Sending messages to profiles without valid marketing consent violates regulations and damages deliverability reputation. Ensure consent fields are populated and enforced at the channel surface level.

### Best practices

- Start with Option A (Scheduled Campaign) for simple broadcast use cases and graduate to Option B (Audience-Triggered Journey) only when pre-delivery logic or behavior-driven timing is needed
- Always include both a one-click list-unsubscribe header and an unsubscribe link in the email body for maximum compliance
- Create reusable content fragments for headers, footers, and legal disclaimers to ensure consistency across campaigns
- Set frequency capping rules before activating campaigns to prevent over-messaging across concurrent sends
- Use content experimentation to optimize subject lines and CTAs, starting with A/B tests before progressing to multivariate experiments
- Assign priority scores to all active campaigns to ensure consistent conflict resolution
- Schedule batch audience evaluation to complete before the campaign execution time to ensure fresh audience data
- Send proof emails and use the email rendering feature to verify the message displays correctly across email clients before activation
- Monitor the live report immediately after campaign activation to catch delivery issues early
- Archive campaign configurations and experiment results for future reference and continuous optimization

### Trade-off decisions

The following trade-offs should be evaluated when making implementation choices.

#### Simplicity vs. flexibility

Scheduled campaigns (Option A) offer the simplest configuration but no pre-delivery logic. Audience-triggered journeys (Option B) provide pre-delivery logic but add configuration complexity.

- **Option A favors:** Speed to launch, operational simplicity, marketer self-service
- **Option B favors:** Behavioral targeting, conditional suppression, extensibility to multi-step journeys
- **Recommendation:** Start with Option A for straightforward sends. Move to Option B only when the use case genuinely requires wait, condition, or branching logic before delivery. Avoid using the journey canvas for simple batch sends that do not benefit from orchestration capabilities.

#### Audience freshness vs. evaluation cost

Streaming evaluation provides near-real-time audience updates but has segment rule restrictions. Batch evaluation supports all segment rule functions but evaluates on a daily schedule.

- **Streaming favors:** Timeliness, behavior-driven accuracy, audience-triggered journey entry
- **Batch favors:** Complex audience logic, large populations, lower evaluation overhead
- **Recommendation:** Use batch evaluation for scheduled campaigns (Option A) where daily freshness is sufficient. Use streaming evaluation for audience-triggered journeys (Option B) where profiles must enter as they qualify. If the audience segment rule expression is not streaming-eligible, restructure the rules or accept batch-level latency.

#### Personalization depth vs. authoring complexity

Deeper personalization (conditional content blocks, dynamic sections) improves engagement but increases authoring and testing effort.

- **Deep personalization favors:** Higher engagement rates, more relevant customer experience, better conversion
- **Simple personalization favors:** Faster time to launch, lower testing burden, reduced risk of rendering errors
- **Recommendation:** Start with basic personalization (first name, relevant product category) and layer in conditional content blocks based on measured performance gains. Always test all content variations across multiple test profiles before activation.

#### Frequency control vs. message reach

Strict frequency capping prevents over-messaging but may suppress campaign delivery to profiles who have recently received other messages.

- **Strict capping favors:** Customer experience quality, lower unsubscribe rates, brand reputation
- **Relaxed capping favors:** Maximum message reach, higher total impressions, campaign coverage
- **Recommendation:** Always enable frequency capping for marketing campaigns. Set channel-specific caps (e.g., 3-5 emails per week, 1-2 SMS per week). Exempt only truly time-critical or transactional messages from capping rules.

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
