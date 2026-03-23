---
title: Multi-Step Orchestrated Journey
description: Learn how to guide a profile through a branching, multi-touch journey with waits, conditions, and multiple message actions over time.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 5667b188-1b20-4a85-aebb-74efd5f771a1
---
# Multi-step orchestrated journey

This guide provides a comprehensive implementation blueprint for building multi-step orchestrated journeys using [!DNL Adobe Journey Optimizer] (AJO) and [!DNL Real-Time Customer Data Platform] (RT-CDP). It is designed for solution architects, marketing technologists, and implementation engineers who need to orchestrate branching, multi-touch customer journeys that deliver multiple messages over time.

It presents all viable implementation options, decision considerations at every configuration point, and links to [!DNL Adobe Experience League] documentation. Use this guide to plan, configure, and validate your multi-step journey implementation.

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

## Use case pattern

**Multi-Step Orchestrated Journey**

Guide a profile through a branching, multi-touch journey with waits, conditions, and multiple message actions over time.

**Function chain:** Audience Evaluation > Journey Execution (multi-node) > Condition Branching > Message Delivery (xN) > Exit Criteria > Reporting

## Applications

The following applications are used to implement this use case pattern.

- **[!DNL Adobe Journey Optimizer] (AJO)** -- Journey orchestration engine, message authoring, channel configuration, content experimentation, frequency and conflict management, and reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** -- Audience evaluation and definition for journey entry audiences, profile data for personalization and condition branching
- **[!DNL Adobe Experience Platform] (AEP)** -- Profile store, identity service, event data ingestion, and foundational data infrastructure

## Foundational functions

The following foundational capabilities must be in place for this use case pattern. For each function, the status indicates whether it is typically required, assumed to be pre-configured, or not applicable.

| Foundational function | Status | What must be in place | Experience League reference |
| --- | --- | --- | --- |
| Administration & Governance | Assumed in Place | AJO sandbox with journey creation and publish permissions. Channel surfaces for all channels used in the journey must be configured. Users must have the appropriate roles (Marketer, Journey Manager) with journey and campaign permissions. | [Sandboxes overview](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Access control overview](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Data Modeling & Preparation | Required | XDM profile schema with attributes used for condition branching and personalization across multiple messages (for example, loyalty tier, product interest, engagement score). Experience Event schemas for conversion events that drive exit criteria and condition evaluation (for example, purchase events, form submissions). | [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Data Sources & Collection | Assumed in Place | Event streaming must be active if exit criteria or conditions depend on real-time events (for example, purchase event to exit the journey). Batch ingestion for profile attributes used in branching. Web SDK or server-side API for behavioral event collection. | [Streaming ingestion overview](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview), [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Identity & Profile Configuration | Assumed in Place | Profiles must be resolvable across all channels used in the journey (email, SMS, push). Cross-device identity must be configured if the journey spans web and mobile touchpoints. Merge policy must be configured for the sandbox. | [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Audience Definition & Segmentation | Required | Entry audience must be defined for audience-read journeys. Segments may also be used in condition nodes for branching. Evaluation method (batch or streaming) must match the journey entry requirements. | [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Supporting functions

The following capabilities augment this use case pattern but are not required for core execution.

| Supporting function | Status | Why it matters | Experience League reference |
| --- | --- | --- | --- |
| Computed / Derived Attribute Creation | Recommended | Computed attributes such as engagement scores, days since last activity, or lifetime purchase value improve condition branching logic, enabling more intelligent journey path decisions. | [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Recommended | Journey event data retention should be configured with dataset expiration policies to manage storage and comply with data retention regulations. Consent enforcement ensures only opted-in profiles receive messages at each channel touchpoint. | [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Dataset expirations](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| Data Usage Labeling & Enforcement | Recommended | Governance labels ensure compliant personalization across multiple message touchpoints, particularly important when journeys use PII or sensitive data for personalization across channels. | [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) |
| Monitoring & Observability | Included | Journey execution monitoring alerts on processing failures, profile entry bottlenecks, and delivery issues. Essential for production journeys where delays or failures impact customer experience. | [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting & Analysis | Included | CJA funnel and fallout analysis across the full journey provides deeper insight than AJO native reports alone. Enables step-by-step conversion analysis, cohort comparison, and journey optimization. | [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## Application functions

This plan exercises the following functions from the Application Function Catalog. Functions are mapped to implementation phases rather than numbered steps.

### [!DNL Journey Optimizer] (AJO)

| Function | Implementation phase | Description |
| --- | --- | --- |
| Channel Configuration | Phase 1: Channel Setup | Configure channel surfaces (email, SMS, push) for each messaging touchpoint in the journey |
| Message Authoring | Phase 2: Message Content Creation | Author message content with personalization, dynamic content, and templates for each journey action node |
| Journey Orchestration | Phase 3: Journey Design & Activation | Design the multi-step journey canvas with entry, action, condition, wait, and exit nodes; test and publish |
| Frequency & Business Rules | Phase 4: Governance & Optimization | Configure frequency caps to prevent over-messaging across journey touchpoints and other concurrent campaigns |
| Conflict & Priority Management | Phase 4: Governance & Optimization | Assign priority scores and configure conflict detection for journeys competing with other active communications |
| Content Experimentation | Phase 4: Governance & Optimization | Run A/B tests on message content within journey action nodes to optimize performance |
| Reporting & Performance Analysis | Phase 5: Reporting & Monitoring | Monitor journey execution, per-step delivery metrics, and engagement performance |

### [!DNL Real-Time CDP] (RT-CDP)

| Function | Implementation phase | Description |
| --- | --- | --- |
| Audience Evaluation | Phase 1: Channel Setup (prerequisite) | Define and evaluate the entry audience for audience-read journeys; define condition audiences for branching |
| Consent & Governance Enforcement | Phase 4: Governance & Optimization | Enforce consent preferences and data usage policies across journey message actions |

## Prerequisites

Complete the following prerequisites before beginning the implementation.

- [ ] AJO sandbox is provisioned with journey creation and publish permissions
- [ ] At least one channel surface (email, SMS, or push) is configured and active
- [ ] Profile schema includes attributes needed for condition branching and personalization
- [ ] Experience Event schema is configured for conversion events used in exit criteria
- [ ] Event streaming is active for real-time events used in exit criteria or event-triggered entry
- [ ] Identity namespaces and merge policies are configured for cross-channel profile resolution
- [ ] Content assets (images, copy, CTAs) are prepared for each message touchpoint
- [ ] Entry audience is defined and evaluated (for audience-read journeys)
- [ ] Triggering event schema is configured (for event-triggered journeys)
- [ ] Test profiles are available for journey test mode validation
- [ ] Suppression list is reviewed and up to date for all channels used

## Implementation options

Review the following options to determine the best approach for your multi-step orchestrated journey.

### Option A: Audience-read orchestrated journey

**Best for:** Time-based nurture sequences where a known audience enters the journey and progresses through scheduled touchpoints -- onboarding series, renewal sequences, re-engagement drips, loyalty milestone journeys.

**How it works:**

An audience is read at journey entry, either as a one-time read or on a recurring schedule. All qualifying profiles enter the journey simultaneously and then progress through the canvas at their own pace, governed by wait durations and condition evaluations. Each profile's path through the journey is independent -- some may take the "engaged" branch while others take the "not engaged" branch based on their behavior or attributes.

The audience is evaluated at the time the Read Audience activity executes. For recurring journeys, the audience is re-evaluated on each recurrence, and new qualifying profiles enter the journey while profiles already in the journey continue their path. This approach provides predictable entry timing and is well-suited for scheduled lifecycle programs.

**Key considerations:**

- Audience must be defined and evaluated before journey activation
- Recurring read allows new qualifiers to enter on each cycle
- Profiles in the journey are not re-read; only new qualifiers enter on subsequent reads
- Wait steps have a minimum duration of 1 hour for audience-read journeys

**Advantages:**

- Predictable entry timing aligned with business schedules
- Supports large audience volumes (up to 20,000 profiles per second default throttle)
- Simple to test and monitor with known audience populations
- Can be scheduled for recurring entry (daily, weekly, monthly)

**Limitations:**

- Entry is batch-based, not real-time -- profiles enter at the scheduled read time, not when they qualify
- Not suitable for behavior-initiated sequences that require immediate response
- Audience changes between reads are not reflected for profiles already in the journey

**Experience League:**

- [Read audience activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Create a journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)

### Option B: Event-triggered orchestrated journey

**Best for:** Behavior-initiated sequences where a real-time event starts the journey -- cart abandonment escalation, post-purchase nurture, milestone-triggered loyalty journey, trial activation sequences.

**How it works:**

A unitary event (for example, a purchase, cart abandonment, form submission, or app install) triggers journey entry for individual profiles in real time. When the event is received, the profile enters the journey and then progresses through the sequence of touchpoints with conditions, waits, and branching. This approach combines the immediacy of event-triggered messaging with the multi-step orchestration of a full journey.

The triggering event must be configured as a journey event with its schema and conditions defined. The journey listens for the event continuously and enters profiles one at a time as events arrive. Subsequent journey nodes can evaluate the profile's response to determine which branch to follow.

**Key considerations:**

- Requires real-time event streaming to be active
- Event schema and conditions must be precisely configured to avoid false triggers
- Re-entry rules are critical -- determine whether a profile can re-enter if the event fires again
- Supports up to 5,000 events per second per sandbox

**Advantages:**

- Real-time entry based on customer behavior -- highly contextual
- Each profile enters independently when the event occurs, not on a schedule
- Natural fit for behavioral response sequences (cart abandonment, post-purchase)
- Can combine with profile data for personalized branching after entry

**Limitations:**

- Requires streaming event infrastructure to be in place
- Higher complexity in event schema configuration and testing
- Each event enters one profile -- not suitable for bulk audience activation
- Debugging requires tracing individual profile journeys

**Experience League:**

- [General events](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Audience qualification events](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)

### Option C: Multi-channel orchestrated journey

**Best for:** Cross-channel sequences that use different channels at each touchpoint -- email then SMS then push escalation, or email plus in-app complementary messaging. Can use either audience-read or event-triggered entry.

**How it works:**

This option extends Option A or Option B by incorporating multiple messaging channels within the same journey. Each action node in the journey can target a different channel (email, SMS, push, in-app, or web), requiring a separate channel surface for each. The journey designer selects the appropriate channel at each step, enabling escalation patterns (for example, email first, then SMS if no engagement) or complementary patterns (for example, email with in-app reinforcement).

Cross-channel journeys require channel surfaces for each channel used and must account for channel-specific personalization, character limits, and opt-in requirements. Condition nodes can check engagement with previous messages (for example, "opened email?" as a branch condition) to determine the next channel.

**Key considerations:**

- Requires active channel surfaces for each channel used in the journey
- Each channel has different personalization capabilities and content constraints
- Consent must be verified per channel -- a profile may be opted in for email but not SMS
- Channel-specific frequency caps should be configured to prevent over-messaging across channels

**Advantages:**

- Maximizes reach by engaging profiles across their preferred channels
- Enables escalation strategies for non-responsive profiles
- Supports complementary messaging across channels for reinforcement
- Most sophisticated customer experience possible

**Limitations:**

- Highest implementation complexity -- requires configuration for each channel
- Content must be authored for each channel at each touchpoint
- Consent and frequency management become more complex across channels
- Testing requires validation across all channel surfaces

**Experience League:**

- [Configure SMS channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configure push notification channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Option comparison

The following table compares the three implementation options across key criteria.

| Criteria | Option A: Audience-read | Option B: Event-triggered | Option C: Multi-channel |
| --- | --- | --- | --- |
| Best for | Scheduled lifecycle programs, nurture series | Behavioral response sequences, cart abandonment | Cross-channel escalation, complementary messaging |
| Entry timing | Scheduled (batch) | Real-time (event-driven) | Either scheduled or real-time |
| Complexity | Medium | Medium-High | High |
| Entry volume | Up to 20,000 profiles/sec | Up to 5,000 events/sec | Same as underlying entry method |
| Channel scope | Single or multiple channels | Single or multiple channels | Multiple channels required |
| Requires | Defined audience, evaluation schedule | Streaming event infrastructure | Channel surfaces for each channel |
| Real-time response | No -- batch entry | Yes -- immediate upon event | Depends on entry method |

### Choose the right option

Use the following decision flow to select the right implementation approach:

1. **Is the journey initiated by a customer behavior or event?** If yes, choose **Option B** (Event-Triggered). If the journey is initiated by a scheduled audience read, choose **Option A** (Audience-Read).

2. **Does the journey use multiple messaging channels (for example, email AND SMS)?** If yes, apply **Option C** (Multi-Channel) on top of your entry method choice (A or B). If the journey uses a single channel throughout, Option A or B alone is sufficient.

3. **Do you need to escalate to a different channel based on engagement?** If yes, choose **Option C** with condition nodes that check engagement with previous messages and branch to alternate channels.

4. **Is the audience known in advance and processed on a schedule?** If yes, choose **Option A**. If profiles should enter the journey the moment they perform an action, choose **Option B**.

## Implementation phases

The following phases walk through the end-to-end implementation of a multi-step orchestrated journey.

### Phase 1: Set up channels and prepare audiences

**Application functions:** AJO: Channel Configuration, RT-CDP: Audience Evaluation

Before designing the journey, all channel surfaces must be active and the entry audience (for Option A) must be defined and evaluated. This phase ensures the infrastructure is ready for message delivery.

#### Decide on channel type for each touchpoint

Which messaging channels will the journey use at each touchpoint?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Email only | Journey communicates exclusively via email (onboarding, nurture) | Simplest setup; requires email subdomain and IP pool; subject to inbox placement |
| SMS only | Time-sensitive alerts, appointment reminders | Requires SMS provider credentials (Sinch, Twilio, Infobip); higher cost per message; stricter opt-out rules |
| Push only | In-app engagement sequences for mobile users | Requires APNs/FCM credentials; users must have the app installed |
| Multi-channel | Escalation or complementary messaging across channels | Requires channel surface per channel; most complex but highest reach |

#### Decide on audience evaluation method (Option A)

How quickly must profiles qualify for the entry audience?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Batch evaluation | Audience is read on a schedule (daily, weekly); no real-time entry needed | Simple setup; audience evaluated before journey read; supports complex segment rules |
| Streaming evaluation | Profiles should qualify in near real-time as attributes change | Segment rule expression must be streaming-eligible; near real-time qualification |

#### Decide on subdomain delegation method (email channel)

How should the email sending subdomain be delegated to Adobe?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Full delegation | Adobe manages DNS records; simplest setup | Fastest to configure; Adobe handles SPF, DKIM, DMARC |
| CNAME delegation | Organization retains DNS control | Requires DNS administrator involvement; CNAME records must be configured |

#### UI navigation

- Channel surfaces: Administration > Channels > Channel surfaces > Create surface
- Subdomains: Administration > Channels > Subdomains
- SMS configuration: Administration > Channels > SMS configuration
- Push configuration: Administration > Channels > Push notification settings
- Audiences: Customer > Audiences > Create audience > Build rule

#### Key configuration details

- Verify IP pool warmup status for email -- new IP pools require a gradual warmup plan over 2-4 weeks
- For SMS, configure provider credentials and verify sender number registration
- For push, upload APNs certificates and FCM server keys
- Define the entry audience using Segment Builder with segment rules covering the target population
- Include suppression rules in the audience definition (exclude recently converted, globally unsubscribed)

#### Where options diverge

**For Option A (Audience-Read):**
Define and evaluate the entry audience. Confirm the audience has a non-zero population. Determine whether the journey will use a one-time audience read or recurring read schedule.

**For Option B (Event-Triggered):**
Verify that the triggering event schema is configured and that events are streaming into the platform. No pre-defined audience is required -- profiles enter individually upon event receipt.

**For Option C (Multi-Channel):**
Configure channel surfaces for EACH channel used in the journey (email, SMS, push, in-app). Verify consent status per channel for the target population.

#### Experience League documentation

- [Set up channel surfaces](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Get started with email configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configure SMS channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configure push notification channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [IP warmup plans](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)


### Phase 2: Create message content

**Application function:** AJO: Message Authoring

Author the message content for each touchpoint in the journey. Each message may have different content, personalization depth, and channel. This phase creates all the deliverable content that journey action nodes will reference.

#### Decide on content approach

Should each message start from a template, be designed from scratch, or import HTML?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Existing content template | Brand-consistent messages with established layouts | Fastest; ensures brand compliance; template must exist and match channel type |
| Design from scratch | Unique, custom layouts for each touchpoint | Most flexible; longer build time; use Email Designer drag-and-drop |
| Import HTML | Pre-built HTML from external design tools | Requires clean HTML; may need adjustment for responsiveness |

#### Decide on personalization depth

How much personalization should each message include?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Basic token insertion | First name, city, simple profile attributes | Low complexity; uses Handlebars syntax with XDM paths |
| Conditional content blocks | Different content shown based on segment or attribute | Medium complexity; requires dynamic content rules |
| Journey-contextual personalization | Content varies based on journey path, previous interactions | Higher complexity; leverages journey context variables and event data |

#### Decide on fragment strategy

Should shared content blocks (headers, footers, legal text) be created as reusable fragments?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Reusable fragments | Multiple messages share common elements; brand consistency required | Changes propagate to all messages using the fragment; maximum 30 fragments per message |
| Inline content | One-off messages with unique layouts | Faster for single-use content; no cross-message consistency benefit |

#### UI navigation

- Content Management > Content Templates > Browse
- Email Designer (within campaign or journey action)
- Content Management > Fragments > Create fragment

#### Key configuration details

- Author content for EACH message action in the journey -- a 4-step journey may require 4 separate message designs
- Use personalization expressions referencing XDM profile paths (for example, `{{profile.person.name.firstName}}`)
- Configure dynamic content blocks for segment-specific variations
- Preview each message with test profiles to verify personalization rendering
- Send proofs to internal stakeholders for content review
- For SMS, respect character limits (160 characters for standard GSM encoding)
- For push, configure title, body, image, and deep link/URL action

#### Experience League documentation

- [Design email content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Create an email](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Work with content templates](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Work with content fragments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Create an SMS message](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Design a push notification](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)
- [Preview and test your content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)


### Phase 3: Design and activate the journey

**Application function:** AJO: Journey Orchestration

Design the multi-step journey canvas including the entry node, action nodes (messages), condition nodes (branching), wait nodes (time delays), and exit criteria. Then test with test profiles and publish.

#### Decide on entry type

How should profiles enter the journey?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Read Audience | Scheduled nurture sequences; known audience processed in batch | Audience evaluated at read time; supports one-time or recurring reads; up to 20,000 profiles/sec |
| Unitary Event | Real-time behavioral triggers (purchase, cart abandonment) | Real-time entry; requires event streaming; up to 5,000 events/sec |
| Audience Qualification | Entry when a profile enters or exits an audience in near real-time | Streaming evaluation; triggered by segment membership change |
| Business Event | Organization-wide event triggers the journey for an audience | Useful for product launches, weather events, system alerts |

#### Decide on re-entrance policy

Can a profile re-enter the journey after completing or exiting?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Allow re-entrance (with cooldown) | Profiles may need to repeat the journey (recurring purchases, seasonal re-engagement) | Minimum cooldown of 5 minutes; prevents duplicate entries within cooldown window |
| No re-entrance | One-time journeys (onboarding, single lifecycle event) | Profile completes or exits the journey and cannot enter again |

#### Decide on wait durations between touchpoints

How long should the journey wait between each message?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Fixed duration (for example, 3 days) | Consistent pacing regardless of profile behavior | Simple; predictable timing; minimum 1 hour for audience-read journeys |
| Specific date/time | Message must arrive at a precise time (for example, renewal date) | Uses profile attribute or expression to determine the exact date/time |
| Custom expression | Dynamic wait based on profile data or journey context | Most flexible; requires expression authoring |

#### Decide on branching conditions

What conditions determine which path a profile takes?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Profile attribute check | Branch based on loyalty tier, product interest, geography | Uses profile data available at evaluation time |
| Segment membership check | Branch based on whether the profile belongs to a specific audience | Requires the audience to be defined and evaluating |
| Event data check | Branch based on whether the profile performed an action (opened email, clicked link) | Evaluates journey-scoped event data; useful for engagement-based branching |
| Percentage split | Randomly distribute profiles across paths (for A/B testing or controlled rollouts) | Does not use profile data; purely random allocation |

#### Decide on exit criteria

What event or condition causes a profile to exit the journey early?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Conversion event | Profile completes the desired action (purchase, sign-up, form submission) | Requires event streaming; most common exit criteria |
| Audience membership exit | Profile leaves the entry audience or joins an exclusion audience | Evaluates in near real-time for streaming audiences |
| Timeout | Maximum journey duration reached (up to 91 days) | Default safety net; configurable in journey properties |
| No exit criteria | Profile completes the entire journey path naturally | Simplest; all profiles traverse the full journey unless manually removed |

#### Decide on journey timeout

What is the maximum duration a profile can remain in the journey?

| Option | When to choose | Considerations |
| --- | --- | --- |
| 91 days (maximum) | Long-running journeys (quarterly renewal, extended onboarding) | Maximum allowed; profiles still in the journey at timeout are automatically exited |
| Custom shorter duration | Journey should complete within a defined window (7 days, 14 days, 30 days) | Set based on the natural lifecycle of the use case |

#### UI navigation

- Create journey: Journeys > Create Journey
- Journey properties: Journey canvas > Properties panel
- Entry node: Journey canvas > Drag "Read Audience" or event activity
- Action nodes: Journey canvas > Drag channel action (email, SMS, push)
- Condition nodes: Journey canvas > Drag "Condition" activity
- Wait nodes: Journey canvas > Drag "Wait" activity
- Exit criteria: Journey properties > Exit criteria > Configure
- Test mode: Journey canvas > Test mode toggle
- Publish: Journey canvas > Publish

#### Key configuration details

- Name the journey with a clear, descriptive convention (for example, "Onboarding_Series_Email_v1")
- Set the journey timezone for consistent wait step processing
- Configure each action node with the appropriate channel surface and link to authored message content
- Every branch must terminate with an End activity
- Configure re-entry rules appropriate to the use case
- Use test mode with test profiles to simulate the full journey path before publishing
- Verify that test profiles traverse expected paths and receive correct messages

#### Where options diverge

**For Option A (Audience-Read):**

- Drag the "Read Audience" activity as the entry node
- Select the target audience defined in Phase 1
- Optionally configure a recurring read schedule (daily, weekly)
- Configure the read rate throttle if downstream system load is a concern

**For Option B (Event-Triggered):**

- Drag the triggering event as the entry node
- Configure the event schema and entry conditions
- Set re-entry rules carefully to avoid duplicate entries from repeated events

**For Option C (Multi-Channel):**

- Use the entry method from Option A or B
- At each action node, select the appropriate channel surface for that touchpoint
- Add condition nodes between channels to check engagement (for example, "Did the profile open the email?") and route to alternate channels

#### Experience League documentation

- [Create a journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journey properties](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Read audience activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [General events](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Audience qualification events](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Add a message in a journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Condition activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Wait activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Exit criteria](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [End activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [Journey entry management](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Test your journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Publish the journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)


### Phase 4: Configure governance and optimization

**Application functions:** AJO: Frequency & Business Rules, AJO: Conflict & Priority Management, AJO: Content Experimentation, RT-CDP: Consent & Governance Enforcement

Apply frequency caps to prevent over-messaging, assign priority scores for conflict resolution with other active communications, optionally configure A/B tests within journey messages, and verify consent enforcement.

#### Decide on frequency cap configuration

Should journey messages respect global frequency caps?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Apply frequency rules | Journey operates alongside other campaigns and journeys; profiles should not be over-messaged | Messages may be suppressed if the profile has already hit the cap from other communications |
| Exempt from capping | Journey messages are critical and must always be delivered (transactional, regulatory) | Use sparingly; may contribute to message fatigue if overused |

#### Decide on priority score assignment

How should this journey rank relative to other active campaigns and journeys?

| Option | When to choose | Considerations |
| --- | --- | --- |
| High priority (70-100) | Journey messages are critical lifecycle communications (onboarding, renewal) | Higher priority wins when conflicts arise with other communications |
| Medium priority (30-69) | Journey messages are important but not urgent (nurture, education) | May be suppressed by higher-priority communications |
| Low priority (0-29) | Journey messages are supplementary or promotional | Will be suppressed when competing with higher-priority messages |

#### Decide on content experimentation

Should any journey message include an A/B or multivariate test?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Yes -- A/B test | Optimize subject lines, CTAs, or content layouts at a specific touchpoint | Requires sufficient volume per variant for statistical significance; 2-10 treatments supported |
| No experimentation | Content is finalized or volume is too low for meaningful testing | Simpler setup; no variant tracking needed |

#### UI navigation

- Frequency rules: Administration > Business rules > Create rule
- Priority scores: Journey properties > Priority score
- Conflict detection: Administration > Business rules > Conflict & Priority
- Content experiment: Journey canvas > Select message action > Content experiment toggle
- Consent policies: Privacy > Policies > Consent policies

#### Key configuration details

- Set channel-specific frequency caps (for example, max 3 emails/week, max 1 SMS/day, max 2 push/day)
- Assign a priority score to the journey (0-100) that reflects its business importance relative to other active communications
- Review the conflict detection panel to identify any overlapping campaigns or journeys
- If running a content experiment, define treatment variants, set traffic allocation, choose the success metric (opens, clicks, or conversions), and set the confidence threshold (typically 95%)
- Verify that consent enforcement is active for each channel used in the journey

#### Experience League documentation

- [Frequency rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Business rules overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Priority scores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identify potential conflicts](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Journey capping and arbitration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Get started with content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Create a content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Consent in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)


### Phase 5: Configure reporting and monitoring

**Application functions:** AJO: Reporting & Performance Analysis, Monitoring & Observability, Reporting & Analysis

Monitor journey execution during and after activation, review per-step delivery and engagement metrics, configure alerts for journey processing failures, and optionally build CJA workspace analysis for deep funnel and fallout visualization.

#### Decide on reporting method

Which reporting tools are needed for this journey?

| Option | When to choose | Considerations |
| --- | --- | --- |
| AJO native reports only | Basic delivery and engagement monitoring is sufficient | Live report (during execution) and All Time report (post-execution); refreshes every 60 seconds for live |
| AJO + CJA analysis | Deep funnel analysis, step conversion rates, fallout visualization, or cross-journey comparison is needed | Requires CJA connection and data view linked to AJO datasets; most comprehensive |
| CJA only | Organization uses CJA as the primary analytics platform | Requires CJA configuration; AJO native reports still available as a backup |

#### Decide on alert configuration

What journey failures should trigger alerts?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Journey processing alerts | Always recommended for production journeys | Alerts on profile entry failures, action node errors, and journey stalls |
| Delivery failure alerts | Critical for journeys with high-value communications | Alerts on bounce rates exceeding thresholds, delivery failures |

#### UI navigation

- Journey live report: Journeys > Select journey > Live report
- Journey all time report: Journeys > Select journey > All time report
- Alerts: Alerts > Alert rules > Subscribe
- CJA workspace: Projects > Create new project

#### Key configuration details

- Access the live report during journey execution to monitor profile entries, exits, and per-step delivery metrics in real time
- After journey completion (or after sufficient data accumulates), review the All Time report for comprehensive analysis
- Configure platform alerts for journey processing failures and delivery issues
- For CJA analysis, ensure the CJA connection includes AJO experience event datasets (Message Feedback, Email Tracking, Journey Step Events)
- Build a CJA Workspace with:
  - Funnel visualization showing profile counts at each journey step
  - Fallout visualization to identify drop-off points
  - Step conversion rate calculations
  - Time-to-conversion analysis
  - Channel-level engagement breakdown (for multi-channel journeys)

#### Experience League documentation

- [Journey live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Journey global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Work with Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Implementation considerations

Review the following guardrails, pitfalls, best practices, and trade-offs before and during your implementation.

### Guardrails and limits

- Maximum of **500 live journeys** per sandbox -- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum **journey duration is 91 days** (global timeout) -- profiles still in the journey at timeout are automatically exited
- Maximum of **50 activities** per journey canvas
- Read Audience journeys process up to **20,000 profiles per second** (default throttle)
- Unitary event journeys support up to **5,000 events per second** per sandbox
- Wait steps have a **minimum duration of 1 hour** for audience-read journeys
- Journey **re-entrance cooldown minimum is 5 minutes**
- Maximum of **10 channel surfaces per channel type** per sandbox
- Maximum email size of **100 KB** recommended for optimal deliverability
- Maximum of **30 content fragments** per message
- Maximum of **10 content experiment treatments** (variants) per experiment
- Maximum of **10 capping configurations** per sandbox
- Maximum of **4,000 segment definitions** per sandbox

### Common pitfalls

- **Publishing without testing:** Always use test mode with test profiles to validate the complete journey path before publishing. Verify that profiles traverse expected branches, wait steps advance correctly, and messages render properly.
- **Missing end activities on branches:** Every journey branch must terminate with an End activity. The journey will fail to publish if any branch is left without a termination node.
- **Overly broad entry conditions:** A loosely defined entry audience or event condition can flood the journey with unintended profiles. Refine entry criteria with specific attribute checks and suppression rules.
- **Ignoring re-entry rules:** For event-triggered journeys, profiles may fire the triggering event multiple times. Without proper re-entry configuration (deny re-entry or cooldown period), profiles can accumulate in the journey, causing duplicate messages.
- **Wait step timezone confusion:** Wait durations are processed in UTC. Set the journey timezone explicitly in journey properties to ensure wait steps advance at the expected local time.
- **Editing a live journey:** Live journeys cannot be edited directly. To make changes, duplicate the journey, modify the copy, stop the original, and publish the new version. Plan journey versioning before going live.
- **No exit criteria defined:** Without exit criteria, profiles who convert mid-journey will continue receiving subsequent messages -- potentially irrelevant or contradictory. Always configure exit criteria for conversion events.
- **Channel consent misalignment:** A profile may be opted in for email but not SMS. Multi-channel journeys must respect per-channel consent. Verify consent fields are populated and enforced at each channel surface.

### Best practices

- **Start simple, iterate:** Begin with a linear 2-3 step journey before adding complex branching. Validate the core flow works before layering in conditions and channels.
- **Use descriptive naming conventions:** Name journey nodes, conditions, and wait steps clearly (for example, "Wait_3_Days_After_Welcome" rather than "Wait 1"). This makes test mode debugging and report interpretation much easier.
- **Configure exit criteria early:** Define the conversion event as an exit criteria before designing the journey paths. This ensures profiles who convert are removed from the journey regardless of which step they are on.
- **Set meaningful wait durations:** Base wait durations on customer behavior data -- time between typical interactions, expected response windows, and channel-appropriate cadence (for example, 2-3 days between emails, 1 week between SMS).
- **Use condition nodes to check engagement:** After a message action, add a condition to check whether the profile engaged (opened, clicked). Route engaged profiles to one path and non-engaged profiles to an escalation or alternate channel path.
- **Leverage computed attributes for branching:** Use computed attributes such as engagement scores, purchase frequency, or days since last activity to make branching decisions data-driven rather than arbitrary.
- **Monitor and optimize iteratively:** Review journey reports weekly during the initial run. Identify drop-off points, adjust wait durations, refine conditions, and optimize message content based on per-step performance data.
- **Version your journeys:** When making changes, duplicate the journey to create a new version. Maintain a log of version changes for audit and optimization tracking.

### Trade-off decisions

The following trade-offs should be evaluated in the context of your specific business requirements.

#### Audience-read entry vs. event-triggered entry

Audience-read entry provides predictable, batch-based processing that is easier to manage and test. Event-triggered entry provides real-time responsiveness that is more contextually relevant but requires streaming infrastructure and more careful re-entry management.

- **Audience-Read favors:** Predictability, large-volume processing, scheduled lifecycle programs, simpler testing
- **Event-Triggered favors:** Real-time relevance, behavioral context, individual profile pacing, immediate response to customer actions
- **Recommendation:** Use audience-read for planned lifecycle programs (onboarding, renewal) where timing is business-driven. Use event-triggered for behavioral response sequences (cart abandonment, post-purchase) where timing is customer-driven.

#### Single channel vs. multi-channel journey

Single-channel journeys are simpler to implement, test, and manage. Multi-channel journeys provide broader reach and escalation capabilities but increase complexity in content creation, consent management, and frequency governance.

- **Single channel favors:** Faster implementation, simpler consent management, lower content production effort, easier debugging
- **Multi-channel favors:** Higher engagement potential, channel escalation for non-responsive profiles, more comprehensive customer experience
- **Recommendation:** Start with a single-channel journey and validate the flow and business impact before expanding to multi-channel. Add channels incrementally where engagement data shows the primary channel is not reaching the audience effectively.

#### Journey complexity vs. manageability

A highly branched journey with many conditions and paths can address more scenarios but becomes harder to test, debug, and optimize. A simpler journey with fewer branches is easier to manage but may deliver a less personalized experience.

- **Complex journeys favor:** Granular personalization, segment-specific paths, comprehensive scenario coverage
- **Simpler journeys favor:** Faster deployment, easier testing, clearer reporting, lower maintenance burden
- **Recommendation:** Limit journeys to 3-5 major branches and 15-25 activities. If the logic requires more complexity, consider splitting into multiple journeys with cross-journey coordination rather than a single monolithic journey.

#### Frequency cap strictness vs. journey completion

Strict frequency caps protect against over-messaging but may suppress journey messages, causing profiles to skip steps and reducing journey completion rates. Lenient caps ensure journey messages are delivered but risk channel fatigue.

- **Strict caps favor:** Customer experience protection, reduced unsubscribe rates, brand trust
- **Lenient caps favor:** Journey completion rates, full message sequence delivery, marketing program effectiveness
- **Recommendation:** Assign higher priority scores to critical journey messages (onboarding, renewal) so they take precedence over promotional campaigns when caps are reached. Reserve "exempt from capping" for truly essential communications only.

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
