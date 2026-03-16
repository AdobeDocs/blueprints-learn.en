---
title: Event-Triggered Messaging
description: Learn how to deliver contextual, real-time messages in response to behavioral or system events.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 75137990-9848-40c0-abf3-adbd21d2de52
---
# Event-triggered messaging

This guide provides a comprehensive implementation blueprint for event-triggered messaging using [!DNL Adobe Journey Optimizer] (AJO), [!DNL Real-Time Customer Data Platform] (RT-CDP), and [!DNL Adobe Experience Platform] (AEP). It is designed for solution architects, marketing technologists, and implementation engineers who need to deliver contextual, real-time messages in response to behavioral or system events.

Use this guide to understand what to configure, where implementation choices exist, and what trade-offs drive each decision.

The guide covers the full lifecycle from event ingestion and journey creation through message delivery and performance reporting, with detailed decision guidance for three distinct implementation options.

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

| KPI | Description | Measurement |
| --- | --- | --- |
| Conversion Rate | Percentage of triggered message recipients who complete the desired action (purchase, sign-up, renewal) | Conversions / Messages Delivered * 100 |
| Incremental Revenue | Additional revenue attributable to event-triggered messages compared to no-send control groups | Revenue from triggered sends - Control group baseline |
| Open Rate | Percentage of delivered messages that are opened by recipients | Opens / Delivered * 100 |
| Click-Through Rate (CTR) | Percentage of delivered messages that generate at least one click | Clicks / Delivered * 100 |
| Time to Conversion | Average elapsed time between message delivery and conversion event | Avg(conversion timestamp - delivery timestamp) |
| Journey Completion Rate | Percentage of profiles that enter the journey and reach the message delivery step (not dropped by conditions or exits) | Profiles reaching delivery / Profiles entering journey * 100 |
| Message Suppression Rate | Percentage of qualifying profiles suppressed due to frequency caps, consent, or condition evaluation | Suppressed profiles / Total qualifying profiles * 100 |
| Bounce Rate | Percentage of messages that could not be delivered due to hard or soft bounces | Bounces / Sent * 100 |

## Use case pattern

This section describes the core pattern and the function chain that drives event-triggered messaging.

**Event-Triggered Messaging**

Listen for a real-time behavioral or system event, then deliver a contextual message to the triggering profile.

**Function Chain:** Event Ingestion > Journey Entry > Condition Evaluation > Message Delivery > Reporting

## Applications

The following Adobe applications are used in this use case pattern.

- **[!DNL Adobe Journey Optimizer] (AJO)** -- Journey orchestration with unitary event entry, condition evaluation, wait steps, message authoring, channel configuration, frequency governance, and delivery reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** -- Audience evaluation for condition-based filtering within journeys, consent and governance enforcement, profile enrichment
- **[!DNL Adobe Experience Platform] (AEP)** -- Real-time event ingestion via Web SDK, Mobile SDK, or server-side API; data modeling; identity resolution; Edge Network

## Foundational functions

The following foundational capabilities must be in place for this use case pattern. For each function, the status indicates whether it is typically required, assumed to be pre-configured, or not applicable.

| Foundational Function | Status | What Must Be in Place | Experience League Reference |
| --- | --- | --- | --- |
| Administration & Governance | Assumed in Place | AJO sandbox provisioned with active channel configuration. Journey creation and publish permissions assigned to the implementation team. User roles configured for journey management, content authoring, and channel administration. | [Sandboxes overview](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Access control overview](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Data Modeling & Preparation | Required | An XDM ExperienceEvent schema must capture the triggering event with all contextual fields needed for condition evaluation and message personalization (e.g., `commerce.productListAdds` for cart events, product details, cart value). The schema must be enabled for Real-Time Customer Profile. A corresponding dataset must be created and Profile-enabled. | [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Data Sources & Collection | Required | Real-time event streaming must be configured -- Web SDK for web events, Mobile SDK for app events, or Edge Network Server API for system events. A datastream must be configured with AEP and AJO services enabled, routing events to the correct dataset. This is a critical dependency since the pattern depends on real-time event ingestion. | [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Identity & Profile Configuration | Required | The triggering event must be associated with a known identity (email, CRM ID, or authenticated session) so the journey can resolve the profile and deliver the message. Identity namespaces must exist for the identifiers used by the triggering event. Anonymous events require identity stitching via the identity graph before a message can be delivered. A merge policy must be configured. | [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Audience Definition & Segmentation | Recommended | While not strictly required for event-triggered journeys (entry is event-based, not audience-based), audience segments may be used for condition evaluation within the journey (e.g., only send if the profile is in a "high-value customer" segment, or suppress if the profile is in a "recently contacted" segment). Streaming evaluation is recommended for real-time segment membership checks within journeys. | [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation) |

## Supporting functions

The following capabilities augment this use case pattern but are not required for core execution.

| Supporting Function | Status | Why It Matters | Experience League Reference |
| --- | --- | --- | --- |
| Computed / Derived Attribute Creation | Recommended | Computed attributes such as cart abandonment count, days since last purchase, average order value, and lifetime purchase total improve condition evaluation and personalization within triggered journeys. These behavioral aggregates enable more precise targeting decisions (e.g., differentiate first-time abandoners from repeat abandoners). | [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Recommended | Event data expiration should be configured for transient behavioral events (page views, searches, clicks) to manage storage costs and compliance. Consent schema fields must be present for channel-specific opt-in/opt-out enforcement during message delivery. | [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Dataset expirations](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| Data Usage Labeling & Enforcement | Recommended | Governance labels on event and profile fields ensure compliant personalization. If triggered messages include personalized content using PII or behavioral data, data usage labels and governance policies should be reviewed to prevent unauthorized data usage in message content. | [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) |
| Monitoring & Observability | Included | Journey execution monitoring is part of the reporting phase. Additionally, configure alerts for event ingestion failures or journey processing delays to detect pipeline issues that would prevent triggered messages from being sent. | [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting & Analysis | Included | Journey performance reports are covered in the reporting phase. For deeper analysis of triggered messaging effectiveness across channels and over time, configure CJA connections and workspaces to analyze conversion attribution, time-to-conversion, and channel performance. | [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Application functions

This plan exercises the following functions from the Application Function Catalog. Functions are mapped to implementation phases rather than numbered steps.

### [!DNL Journey Optimizer] (AJO)

| Function | Implementation Phase | Description |
| --- | --- | --- |
| Journey Orchestration | Journey Creation & Configuration | Create a journey with unitary event entry, configure the qualifying event, add condition nodes, wait steps, message actions, exit criteria, and re-entry rules |
| Channel Configuration | Channel Surface Setup | Configure or validate channel surfaces (email, SMS, push) including subdomain delegation, IP pools, sender settings, and suppression list management |
| Message Authoring | Message Content Creation | Author contextual message content with event-driven personalization, conditional content blocks, and reusable fragments |
| Frequency & Business Rules | Journey Creation & Configuration (Option C) | Configure frequency caps and deduplication rules to prevent over-messaging from high-frequency event sources |
| Conflict & Priority Management | Journey Creation & Configuration | Assign priority scores and configure conflict detection for journeys competing for the same profiles |
| Reporting & Performance Analysis | Reporting & Monitoring | Monitor journey delivery metrics via live and historical reports; access programmatic performance data via CJA |

### [!DNL Real-Time CDP] (RT-CDP)

| Function | Implementation Phase | Description |
| --- | --- | --- |
| Audience Evaluation | Foundational Setup (F5) | Evaluate audience segments used for condition-based filtering within the journey (e.g., high-value customer segments, suppression segments) |
| Consent & Governance Enforcement | Foundational Setup (S2/S3) | Enforce consent preferences and data usage governance policies during message delivery to ensure compliant communications |

## Prerequisites

Complete the following before beginning the implementation.

- [ ] AJO sandbox provisioned with journey creation and publish permissions (F1)
- [ ] XDM ExperienceEvent schema capturing the triggering event with contextual fields, enabled for Real-Time Customer Profile (F2)
- [ ] Real-time event streaming configured via Web SDK, Mobile SDK, or Edge Network Server API with a datastream routing events to the correct AEP dataset (F3)
- [ ] Identity namespaces configured for the identifiers on the triggering event; identity linking rules in place (F4)
- [ ] Channel surface (email, SMS, or push) configured and validated with a successful test send
- [ ] Message content authored, reviewed, and tested with sample profiles
- [ ] Consent fields populated on profiles for the target channel (e.g., `consents.marketing.email.val`)
- [ ] If using condition-based audience filtering (Option B/C), streaming-evaluated audience segments defined and actively evaluating

## Implementation options

This section describes three implementation options for event-triggered messaging. Each option builds on the previous one, adding additional capabilities.

### Option A: Simple event-triggered message

**Best for:** Immediate, single-message responses where no delay or conditional logic is needed -- order confirmation, welcome email, form submission acknowledgment, booking confirmation.

**How it works:**

The journey listens for a qualifying event via a unitary event entry node. When the event is received, the profile enters the journey, passes through minimal condition evaluation (consent check, profile existence verification), and immediately receives a single message via the configured channel action node.

This is the simplest implementation variant. The journey canvas contains an event entry node, an optional condition node for basic eligibility checks, a single message action node, and an end node. There are no wait steps, no complex branching, and no conversion checks. The message is typically delivered within seconds to minutes of the triggering event.

Event data from the triggering event (product name, order total, form details) can be used for message personalization via contextual attributes in the personalization editor. This approach maximizes speed-to-delivery and minimizes journey complexity.

**Key considerations:**

- Message is sent regardless of whether the customer self-converts after the event (no conversion check)
- Best suited for events that inherently warrant an immediate response (confirmations, acknowledgments)
- Re-entry rules should be configured carefully -- for confirmation-style messages, allow re-entry so each event generates a message; for welcome-style messages, prevent re-entry

**Advantages:**

- Fastest time-to-delivery (seconds to minutes after the event)
- Simplest journey configuration with minimal moving parts
- Lowest risk of journey failures or stuck profiles
- Easy to test and maintain

**Limitations:**

- No ability to check whether the customer self-converted before sending
- Cannot incorporate time-delayed conditional logic
- May generate unnecessary messages if the event occurs frequently without frequency governance

**Experience League:**

- [Create a journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [General events](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)

### Option B: Conditional event-triggered message with wait

**Best for:** Delayed, conditional responses where the customer should have time to self-convert before receiving the message -- cart abandonment (wait 1-4 hours, then check if cart is still abandoned), browse abandonment (wait 24 hours, check if purchase was made), trial expiry (wait until expiry date approaches).

**How it works:**

The journey listens for a qualifying event, enters the profile, and introduces a wait period before evaluating conditions. After the wait, a condition node checks whether the customer has self-converted (e.g., completed the purchase, renewed the subscription) or whether the original context is still valid. Only if the condition is met (e.g., cart still abandoned) does the journey proceed to message delivery.

The journey canvas contains an event entry node, a wait node (configurable duration or specific date/time), a condition node that checks for a conversion event or profile state change, branching paths (send message vs. exit without sending), a message action node on the qualifying path, and an end node on each branch. Exit criteria can be configured to automatically remove profiles from the journey if the conversion event occurs during the wait period, eliminating the need for the explicit condition check.

This approach reduces unnecessary messaging by giving customers time to self-convert, improving the customer experience and increasing the perceived relevance of messages that are sent.

**Key considerations:**

- Wait duration significantly impacts conversion rates -- shorter waits (1-2 hours) produce higher urgency but more unnecessary sends; longer waits (24-48 hours) reduce volume but may miss the relevance window
- Condition evaluation requires the conversion event to be captured in AEP and associated with the same profile identity
- Exit criteria provide a cleaner alternative to explicit condition nodes for conversion checking
- Re-entry rules must account for the wait period -- a profile should not re-enter the journey while already waiting

**Advantages:**

- Reduces unnecessary messaging by checking for self-conversion
- Produces higher-quality, more relevant communications
- Supports time-sensitive use cases with configurable delay windows
- Exit criteria enable automatic journey removal on conversion

**Limitations:**

- Increased journey complexity with wait and condition nodes
- Profiles occupy journey slots during wait periods (subject to 91-day journey timeout)
- Requires the conversion event to be ingested into AEP within the wait window for accurate condition evaluation
- Longer time-to-delivery compared to Option A

**Experience League:**

- [Wait activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Condition activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Exit criteria](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### Option C: Event-triggered with frequency governance

**Best for:** High-frequency event sources where message fatigue is a concern -- page views, product views, search queries, repeat cart additions. Can be applied as an overlay on top of Option A or Option B.

**How it works:**

This option adds frequency governance to either Option A or Option B to prevent over-messaging. High-frequency behavioral events (such as product views or repeated cart additions) can trigger the journey multiple times within a short period. Without frequency governance, a profile could receive duplicate or excessive messages.

Frequency governance is implemented through two complementary mechanisms: AJO business rules (frequency caps) that limit how many messages a profile receives per channel per time period, and journey-level re-entry rules that define a cooldown period before a profile can re-enter the same journey. Business rules operate at the organization level and enforce caps across all campaigns and journeys (e.g., maximum 3 emails per week), while re-entry cooldown operates at the individual journey level (e.g., a profile cannot re-enter this specific journey within 72 hours of the last entry).

Additionally, conflict and priority management can be configured to assign priority scores to the triggered journey, ensuring that when multiple journeys or campaigns compete for the same profile, the highest-priority communication wins.

**Key considerations:**

- Frequency caps must balance between preventing fatigue and ensuring important triggered messages are delivered
- Channel-specific caps are recommended -- email, SMS, and push have different fatigue thresholds
- Journey re-entry cooldown and organization-level frequency caps work together; both should be configured
- Priority scores determine which communication wins when caps are reached -- higher-priority journeys should be assigned higher scores

**Advantages:**

- Prevents message fatigue from high-frequency event sources
- Maintains brand reputation and subscriber satisfaction
- Organization-level caps provide a safety net across all campaigns and journeys
- Priority scoring ensures the most important messages are delivered when caps are reached

**Limitations:**

- Some qualifying profiles will be suppressed, potentially missing relevant messages
- Frequency cap configuration adds administrative complexity
- Caps may interact unexpectedly with other active campaigns and journeys sharing the same channel
- Requires ongoing monitoring and adjustment as the messaging portfolio changes

**Experience League:**

- [Frequency rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Business rules overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Priority scores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Journey entry management](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)

### Option comparison

The following table compares the three implementation options across key criteria.

| Criteria | Option A: Simple Event-Triggered | Option B: Conditional with Wait | Option C: Frequency Governance |
| --- | --- | --- | --- |
| Best for | Immediate confirmations, acknowledgments | Abandonment recovery, delayed conditional responses | High-frequency event sources, multi-journey environments |
| Complexity | Low | Medium | Medium-High (adds to A or B) |
| Message Latency | Seconds to minutes | Minutes to hours/days (configurable wait) | Same as underlying option (A or B) |
| Self-Conversion Check | No | Yes (via condition or exit criteria) | Depends on underlying option |
| Frequency Protection | None (unless combined with C) | None (unless combined with C) | Yes -- channel caps and re-entry cooldown |
| Journey Canvas Nodes | 3-4 (event, optional condition, action, end) | 5-7 (event, wait, condition, branches, action, ends) | Same as A or B, plus business rule configuration |
| Requires | Event schema, channel surface, message content | All of Option A + conversion event ingestion | All of Option A or B + frequency rule configuration |

### Choose the right option

Use the following decision guidance to select the right implementation option.

1. **Does the message need to be sent immediately with no delay?** If yes, start with **Option A**. Confirmation messages, welcome emails, and acknowledgments typically do not require a wait period.

2. **Should the customer have time to self-convert before receiving the message?** If yes, choose **Option B**. Cart abandonment, browse abandonment, and trial expiry use cases benefit from a wait period that allows customers to complete the action on their own.

3. **Is the triggering event high-frequency (occurs multiple times per session or per day for the same profile)?** If yes, add **Option C** as an overlay on top of Option A or B. Product views, page views, and search events can generate high volumes of triggers that require frequency protection.

4. **Are multiple triggered journeys and campaigns active in the sandbox?** If yes, add **Option C** regardless of event frequency to manage cross-journey communication load and prevent channel fatigue.

In practice, most production implementations use Option B + C for abandonment-style use cases (conditional wait with frequency governance) and Option A + C for confirmation-style use cases (immediate send with frequency governance as a safety net).

## Implementation phases

The following phases walk through the end-to-end implementation of event-triggered messaging.

### Phase 1: Configure event schema and data collection

**Application Function:** AEP: Data Modeling (F2), AEP: Data Sources & Collection (F3)

**What you will configure:** The XDM ExperienceEvent schema that captures the triggering event, the dataset that stores these events, and the real-time data collection pipeline (Web SDK, Mobile SDK, or Server API) that streams events into AEP. This phase establishes the data foundation that the journey will listen to.

**Decision points in this phase:**

>[!NOTE]
>
>**Decision: Triggering event type**
>
>What event triggers the message? The event type determines the schema fields required and the collection method.
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Commerce event (cart add, purchase, checkout) | Ecommerce use cases -- cart abandonment, post-purchase | Requires Commerce field group with `productListItems`, `cart`, `order` fields |
>| Web interaction event (page view, product view) | Browse abandonment, content engagement triggers | Requires Web Details field group with `webPageDetails`, `webInteraction` fields |
>| Application event (app install, uninstall, in-app action) | Mobile engagement triggers | Requires Mobile SDK implementation and Application field group |
>| System event (payment failure, subscription change, status update) | Operational notifications | Requires server-side API or source connector to ingest system events |
>| Form submission event | Lead generation, enrollment confirmation | Requires custom field group capturing form data fields |

>[!NOTE]
>
>**Decision: Collection method**
>
>How will the triggering event be captured and streamed into AEP?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Web SDK | Web-based behavioral events (cart adds, page views, form submissions) | Requires Web SDK installation on the website; events are streamed in real time via Edge Network |
>| Mobile SDK | Mobile app events (app opens, in-app actions, push token registration) | Requires Mobile SDK integration in the native app or React Native wrapper |
>| Edge Network Server API | Server-side system events (payment processing, subscription management, backend triggers) | No client-side dependency; events sent from the organization's backend systems |
>| Source connector | Events from external systems (CRM, marketing automation, legacy platforms) | Typically batch-based; may not support real-time triggering unless streaming-capable |

**UI navigation:** Data Collection > Datastreams > New Datastream (for datastream setup); Schemas > Create schema (for event schema); Datasets > Create dataset from schema (for dataset creation)

**Key configuration details:**

- The event schema must include all fields needed for journey condition evaluation and message personalization
- The datastream must have both [!DNL Adobe Experience Platform] and [!DNL Adobe Journey Optimizer] services enabled
- The dataset must be enabled for Real-Time Customer Profile so events are associated with unified profiles
- Event data must include an identity field (email, CRM ID, ECID) that can resolve to a known profile

**Experience League documentation:**

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Edge Network Server API overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Streaming ingestion overview](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)

### Phase 2: Configure identity and profile

**Application Function:** AEP: Identity & Profile Configuration (F4)

**What you will configure:** Identity namespaces for the identifiers on the triggering event, primary identity designation on the event schema, identity linking rules for cross-device resolution, and a merge policy for profile unification. This ensures the triggering event is associated with a unified customer profile so the journey can resolve contact information and deliver the message.

**Decision points in this phase:**

>[!NOTE]
>
>**Decision: Primary identity for event schema**
>
>Which identity field on the triggering event should serve as the primary identity for profile resolution?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Email address | Events from authenticated web sessions or forms where email is captured | Direct resolution to a contactable identity; simplest path to email delivery |
>| CRM ID | Events from authenticated systems where the CRM ID is the primary identifier | Requires CRM ID namespace creation; profile must have a linked email or phone for message delivery |
>| ECID (Experience Cloud ID) | Anonymous web or app events where no authenticated identity is available | Requires identity stitching to link ECID to a known identity; messages cannot be sent to ECID alone |
>| Phone number | Events from mobile or call center interactions | Supports SMS delivery; requires Phone namespace |

**UI navigation:** Identities > Create identity namespace; Schemas > Select schema > Select field > Identity > Set as primary identity; Profiles > Merge policies

**Key configuration details:**

- Anonymous events (ECID-only) cannot trigger message delivery until the ECID is linked to a known contactable identity (email, phone) via the identity graph
- The merge policy used by AJO must be consistent with the one used for audience evaluation
- For web-based triggered messaging, ensure the identity graph links ECID to authenticated identities through login events

**Experience League documentation:**

- [Identity namespaces overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Identity graph linking rules](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Phase 3: Set up channel surfaces

**Application Function:** AJO: Channel Configuration

**What you will configure:** The channel surface (preset) that defines the sending infrastructure for the triggered message -- subdomain delegation, IP pool, sender identity, reply-to address, unsubscribe handling, and channel-specific credentials (SMS provider, push certificates). A valid channel surface must exist before message content can be created or journeys can be published.

**Decision points in this phase:**

>[!NOTE]
>
>**Decision: Message channel**
>
>Which channel will the triggered message use?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Email | Most triggered messaging use cases -- abandonment recovery, confirmations, onboarding | Requires subdomain delegation, IP pool, sender configuration; supports rich HTML content and personalization |
>| SMS | Time-sensitive notifications, concise alerts, audiences with high SMS engagement | Requires SMS provider integration (Sinch, Twilio, Infobip); subject to character limits and stricter consent requirements |
>| Push notification | Mobile app engagement, re-engagement of app users | Requires push credential configuration (APNs for iOS, FCM for Android); user must have the app installed with push enabled |
>| Multiple channels | Comprehensive engagement strategy using channel preference or fallback logic | Requires multiple channel surfaces; channel selection can be managed via journey condition nodes |

>[!NOTE]
>
>**Decision: Subdomain delegation method (email)**
>
>How should the email sending subdomain be delegated to Adobe?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Full delegation | Organization wants Adobe to manage all DNS records for the sending subdomain | Simplest setup; Adobe manages SPF, DKIM, DMARC records automatically |
>| CNAME delegation | Organization wants to maintain DNS control while pointing to Adobe infrastructure | Requires manual DNS record management; provides more organizational control over DNS |

**UI navigation:** Administration > Channels > Subdomains (for subdomain setup); Administration > Channels > IP pools (for IP pool configuration); Administration > Channels > Channel surfaces > Create surface (for surface creation)

**Key configuration details:**

- Subdomain verification and DNS propagation can take up to 48 hours
- New IP pools require a warmup plan (2-4 weeks of gradual volume increase)
- Configure one-click list-unsubscribe headers for email compliance
- For SMS, configure the provider credentials before creating the SMS channel surface
- For push, configure APNs and FCM credentials before creating the push channel surface

**Experience League documentation:**

- [Get started with email configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delegate subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Create IP pools](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Set up channel surfaces](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Configure SMS channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configure push notification channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Phase 4: Create message content

**Application Function:** AJO: Message Authoring

**What you will configure:** The message content that will be delivered by the journey, including layout design, personalization tokens using profile and event attributes, conditional content blocks, reusable fragments (headers, footers, legal disclaimers), and content preview and testing.

**Decision points in this phase:**

>[!NOTE]
>
>**Decision: Content approach**
>
>How should the message content be created?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Start from an existing template | Organizational templates exist and brand consistency is required | Fastest path to content creation; ensures brand compliance; template changes propagate to new messages |
>| Design from scratch in Email Designer | Custom layout needed for this specific triggered message | Full creative control; drag-and-drop visual editor; slower but more flexible |
>| Import HTML | Content is designed by an external team or agency and provided as HTML | Requires HTML coding expertise; may not fully support all Email Designer features |

>[!NOTE]
>
>**Decision: Event personalization**
>
>What event data should be used in the message content?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Event contextual attributes | The message should include details from the triggering event (product name, cart value, form fields) | Use contextual event attributes in the personalization editor; data comes from the triggering event payload |
>| Profile attributes | The message should include profile-level data (first name, loyalty tier, location) | Use profile attributes via XDM paths (e.g., `profile.person.name.firstName`); data comes from the unified profile |
>| Both event and profile attributes | The message should combine event context with profile personalization | Most common approach for triggered messages; ensures both relevance (event) and personalization (profile) |

**UI navigation:** Content Management > Content Templates > Browse (for template selection); Campaign or Journey action > Edit content > Email Designer (for content design); Select text component > Personalization icon (for adding personalization)

**Key configuration details:**

- Use contextual attributes to personalize with data from the triggering event (e.g., product name, cart value)
- Use profile attributes for name, preferences, and loyalty data
- Configure conditional content blocks to vary content by profile segment or attribute (e.g., different CTA for loyalty members)
- Create reusable fragments for headers, footers, and legal disclaimers shared across triggered messages
- Preview with multiple test profiles to verify personalization renders correctly
- Send proofs to internal stakeholders before publishing the journey

**Experience League documentation:**

- [Design email content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Work with content templates](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Work with content fragments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Preview and test your content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Phase 5: Create and configure the journey

**Application Function:** AJO: Journey Orchestration, AJO: Frequency & Business Rules (Option C), AJO: Conflict & Priority Management

**What you will configure:** The journey that listens for the triggering event and orchestrates message delivery. This is the core implementation phase where the journey canvas is designed with the event entry node, condition nodes, wait steps (for Option B), message action nodes, and exit criteria. This phase also covers frequency governance (Option C) and conflict/priority configuration.

**Decision points in this phase:**

>[!NOTE]
>
>**Decision: Re-entry rules**
>
>Can a profile re-enter this journey if the triggering event occurs again?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Allow re-entry (with cooldown) | The event can legitimately recur and each occurrence warrants a message (e.g., each cart abandonment should trigger a recovery message) | Set a cooldown period (minimum 5 minutes) to prevent rapid re-entry from duplicate events; typical cooldown ranges from 1 hour to 72 hours |
>| No re-entry | The message should only be sent once per profile regardless of event recurrence (e.g., welcome message after first registration) | Profile is permanently excluded after first journey completion; appropriate for one-time lifecycle messages |

>[!NOTE]
>
>**Decision: Wait duration (Option B only)**
>
>How long should the journey wait before evaluating conditions and sending the message?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Short wait (1-4 hours) | High-urgency use cases like cart abandonment where immediate follow-up is effective | Higher message volume; may catch some self-converters; best for high-value cart recovery |
>| Medium wait (12-24 hours) | Moderate-urgency use cases like browse abandonment or content engagement | Balanced approach; reduces unnecessary sends while maintaining relevance |
>| Long wait (2-7 days) | Low-urgency use cases like trial expiry reminders or periodic check-ins | Lower message volume; higher risk of losing contextual relevance |
>| Custom date/time | Use cases tied to a specific date (e.g., send 3 days before trial expiry date) | Wait until a calculated date/time; uses the custom expression editor |

>[!NOTE]
>
>**Decision: Exit criteria**
>
>Under what conditions should a profile be removed from the journey before reaching the message action?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Conversion event (e.g., purchase completed) | Cart or browse abandonment where the goal is conversion | Profile exits automatically when the conversion event is detected; cleanest approach for Option B |
>| Audience membership change | Profile should exit if they leave a qualifying segment | Requires streaming-evaluated audience that updates in near real-time |
>| Journey timeout (91-day max) | Default behavior -- profile exits after the maximum journey duration | Safety net; should not be the primary exit mechanism for short-lived triggered journeys |
>| No explicit exit criteria | Simple confirmations (Option A) where every qualifying profile should receive the message | Profile exits naturally after the message action and end node |

>[!NOTE]
>
>**Decision: Frequency governance (Option C)**
>
>How many triggered messages should a profile receive per time period?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Channel-specific caps (e.g., 3 emails/week, 1 SMS/day) | Different channels have different fatigue thresholds | Recommended approach; respects the intrusiveness level of each channel |
>| Global cap (e.g., 5 messages/week across all channels) | Simplified governance across all communication types | Easier to manage but less nuanced; may over-restrict less intrusive channels |
>| Journey-level re-entry cooldown only | Frequency governance needed for this specific journey but not organization-wide | Simplest implementation; does not protect against cross-journey fatigue |

**UI navigation:** Journeys > Create Journey (for journey creation); Journey canvas > Drag event activity (for event entry); Journey canvas > Drag "Wait" activity (for wait configuration); Journey canvas > Drag "Condition" activity (for condition branching); Journey properties > Exit criteria (for exit configuration); Administration > Business rules > Create rule (for frequency caps)

**Key configuration details:**

- Configure the journey event by selecting the event schema and defining the qualifying conditions
- For Option B, add the wait node immediately after the event entry and before any condition evaluation
- Configure condition nodes using profile attributes, event data, or audience membership checks
- Link the message action node to the channel surface and authored content from Phases 3 and 4
- Set the journey timeout to an appropriate duration (shorter than 91 days for triggered journeys)
- For Option C, create frequency rules via Administration > Business rules before publishing the journey
- Assign a priority score to the journey if other campaigns or journeys target overlapping audiences

**Where options diverge:**

**For Option A (Simple Event-Triggered):**
The journey canvas is minimal: event entry > optional consent/eligibility condition > message action > end. No wait steps or conversion checks. Set re-entry rules based on whether the event should generate a message every time it occurs.

**For Option B (Conditional with Wait):**
Add a wait node after event entry. After the wait, add a condition node to check for conversion (e.g., check if `commerce.purchases` event occurred after journey entry) or use exit criteria to automatically remove converted profiles. Branch to the message action on the "not converted" path and to an end node on the "converted" path.

**For Option C (Frequency Governance):**
Configure organization-level frequency caps via Administration > Business rules before publishing. Set journey-level re-entry cooldown in the journey properties. Optionally, assign a priority score via journey properties to control which communication wins when caps are reached. This can be applied on top of either Option A or Option B.

**Experience League documentation:**

- [Create a journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journey properties](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [General events](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Condition activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Wait activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Add a message in a journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Exit criteria](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Journey entry management](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Frequency rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Priority scores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identify potential conflicts](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Phase 6: Test and deploy the journey

**Application Function:** AJO: Journey Orchestration

**What you will configure:** Test mode validation to verify the journey behaves as expected with test profiles, followed by journey publication to make it live.

**UI navigation:** Journey canvas > Test mode toggle (for testing); Journey canvas > Publish (for deployment)

**Key configuration details:**

- Enable test mode on the journey canvas to simulate event triggers with test profiles
- Select test profiles that have valid channel contact information (email address, phone number)
- Trigger the test event and verify the test profile traverses the expected path
- For Option B, verify that the wait step behaves correctly and that condition evaluation produces the expected branching
- Verify that personalization tokens render correctly in the test message
- After successful testing, publish the journey to make it live
- Monitor the journey status and initial profile entry metrics after publication

**Experience League documentation:**

- [Test your journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Publish the journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### Phase 7: Monitor and report on performance

**Application Function:** AJO: Reporting & Performance Analysis, S4: Monitoring & Observability, S5: Reporting & Analysis

**What you will configure:** Live and historical journey reports for delivery and engagement monitoring, platform alerts for event ingestion and journey processing failures, and optionally CJA workspaces for deeper cross-channel analysis of triggered messaging effectiveness.

**Decision points in this phase:**

>[!NOTE]
>
>**Decision: Reporting depth**
>
>How much reporting analysis is needed for this use case?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| AJO native reports only | Operational monitoring of delivery metrics is sufficient | Available immediately; covers sent, delivered, bounced, opened, clicked; no additional configuration needed |
>| AJO native + CJA integration | Cross-channel analysis, conversion attribution, and trend analysis are needed | Requires CJA connection and data view linked to AJO datasets; provides deeper analytical capabilities |

**UI navigation:** Journeys > Select journey > Live report (for live monitoring); Journeys > Select journey > All time report (for historical analysis); Alerts > Alert rules > Subscribe (for alert configuration)

**Key configuration details:**

- Access the journey live report during active execution to monitor profile entries, exits, and delivery metrics
- Review the historical report after the journey has been active for sufficient time to accumulate meaningful data
- Configure alerts for source flow run failures (event ingestion) and journey processing delays
- For CJA integration, ensure the CJA connection includes AJO experience event datasets (Message Feedback Event Dataset, Email Tracking Experience Event Dataset)

**Experience League documentation:**

- [Journey live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Journey global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Work with Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Implementation considerations

This section covers guardrails, common pitfalls, best practices, and trade-off decisions for event-triggered messaging implementations.

### Guardrails and limits

The following platform guardrails and limits apply to event-triggered messaging implementations.

- **Unitary event throughput:** Maximum 5,000 events per second per sandbox for unitary event journeys -- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- **Live journey limit:** Maximum 500 live journeys per sandbox -- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- **Journey canvas limit:** Maximum 50 activities per journey canvas
- **Journey timeout:** Maximum journey duration is 91 days (global timeout)
- **Re-entry cooldown:** Minimum re-entry cooldown is 5 minutes
- **Frequency cap configurations:** Maximum 10 capping configurations per sandbox
- **Channel surfaces:** Maximum 10 channel surfaces per channel type per sandbox
- **Streaming ingestion:** Maximum 20,000 records per second per HTTP connection -- [Ingestion guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- **Computed attributes:** Maximum 25 computed attributes per sandbox -- [Computed attributes guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview#guardrails)
- **Content fragments:** Maximum 30 content fragments per message
- **Live report refresh:** Live reports refresh every 60 seconds and show the last 24 hours of data
- **Historical report latency:** Historical (all time) reports may take up to 2 hours to fully populate after execution ends

### Common pitfalls

Be aware of the following common issues when implementing event-triggered messaging.

- **Anonymous events without identity resolution:** Triggering events that only carry an ECID (anonymous cookie ID) cannot resolve to a contactable profile for message delivery. Ensure the triggering event includes an authenticated identity or that the identity graph links the ECID to a known contact. Without identity resolution, profiles enter the journey but fail at the message delivery step.

- **Missing conversion event for Option B condition checks:** If the conversion event (e.g., purchase) is not ingested into AEP or is not associated with the same profile identity as the triggering event, the condition check will incorrectly evaluate as "not converted" and send unnecessary messages. Verify that conversion events flow into AEP in real time and share an identity with the triggering event.

- **Overly permissive re-entry rules:** Allowing re-entry without a cooldown period on high-frequency event sources can cause the same profile to receive multiple messages within minutes. Always set a re-entry cooldown that matches the business context (e.g., 4-hour cooldown for cart abandonment, 24-hour cooldown for browse abandonment).

- **Wait step timezone misalignment:** Wait steps process in UTC by default. If the journey targets profiles across multiple time zones and the wait should align with the recipient's local time, configure the timezone settings on the journey accordingly.

- **Frequency caps conflicting with other campaigns:** Organization-level frequency caps apply across all campaigns and journeys. A new triggered journey may be suppressed if profiles have already reached their cap from other active campaigns. Monitor the suppression rate and adjust priority scores to ensure important triggered messages are prioritized.

- **Journey publish failure due to missing dependencies:** Every branch in the journey canvas must terminate with an end activity. All action nodes must reference valid channel surfaces with active message content. Verify all dependencies before publishing.

### Best practices

Follow these recommendations for successful event-triggered messaging implementations.

- **Start simple, then iterate:** Begin with Option A for new triggered messaging use cases. Add wait and condition logic (Option B) only after validating the event pipeline and message delivery. Add frequency governance (Option C) when multiple triggered journeys are active.

- **Use exit criteria instead of condition nodes for conversion checks:** Exit criteria automatically remove profiles from the journey when a qualifying event (e.g., purchase) occurs, eliminating the need for an explicit condition node after the wait step. This produces a cleaner journey canvas and more responsive conversion detection.

- **Test with real event data in a development sandbox:** Use test mode with actual event payloads (not just test profiles) to validate that event schema fields, personalization tokens, and condition expressions work correctly with production-like data.

- **Set event-specific re-entry cooldowns:** Match the cooldown period to the business context of the triggering event. Cart abandonment journeys typically use a 4-24 hour cooldown; confirmation journeys may allow immediate re-entry; onboarding journeys should prevent re-entry entirely.

- **Monitor the suppression rate as a health metric:** If the suppression rate (profiles qualifying but not receiving messages due to frequency caps or conditions) exceeds 30-40%, review whether caps are too restrictive or whether the triggering event is too broadly defined.

- **Version journeys instead of editing live ones:** A live journey cannot be edited directly. Create a new version by duplicating the journey, making changes, then stopping the old version and publishing the new one. This avoids disrupting profiles currently in the journey.

- **Include a fallback/default path in condition nodes:** Always configure a default (else) path in condition nodes to handle unexpected profile states. Profiles that do not match any condition branch should exit gracefully rather than remaining stuck.

### Trade-off decisions

Consider the following trade-offs when designing your event-triggered messaging implementation.

>[!NOTE]
>
>**Trade-off: Message speed vs. message relevance**
>
>Immediate message delivery (Option A) maximizes speed but may send messages to customers who would have self-converted. Delayed conditional delivery (Option B) improves relevance by filtering out self-converters but introduces latency that may reduce urgency.
>
>- **Option A favors:** Speed, simplicity, confirmation-style use cases where every event warrants a message
>- **Option B favors:** Relevance, reduced message fatigue, abandonment-style use cases where self-conversion is common
>- **Recommendation:** Use Option A for transactional and confirmation messages where speed is the primary value. Use Option B for recovery and re-engagement messages where relevance outweighs speed. Experiment with wait durations to find the optimal balance for each use case.

>[!NOTE]
>
>**Trade-off: Frequency protection vs. message coverage**
>
>Strict frequency caps (Option C) prevent fatigue but may suppress important triggered messages when profiles are near their cap. Permissive or no caps maximize coverage but risk over-messaging and channel fatigue.
>
>- **Strict caps favor:** Customer experience, brand reputation, deliverability (fewer spam complaints)
>- **Permissive caps favor:** Message coverage, conversion opportunities, avoiding missed triggers
>- **Recommendation:** Start with industry-standard caps (3-5 emails/week, 1-2 SMS/week, 2-3 push/day) and adjust based on engagement metrics and unsubscribe rates. Assign higher priority scores to triggered messages so they win over batch campaigns when caps are reached.

>[!NOTE]
>
>**Trade-off: Journey simplicity vs. journey sophistication**
>
>Simple journeys (few nodes, no branching) are easier to build, test, and maintain but offer limited contextual adaptation. Sophisticated journeys (multiple conditions, branching paths, segment checks) enable more nuanced responses but increase complexity and risk of errors.
>
>- **Simple journeys favor:** Faster implementation, easier debugging, lower maintenance burden
>- **Sophisticated journeys favor:** More precise targeting, better personalization, reduced unnecessary sends
>- **Recommendation:** Start with the simplest journey that meets the business requirement. Add complexity incrementally based on performance data. A simple journey that works reliably is more valuable than a complex journey with undetected errors.

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
