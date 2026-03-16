---
title: Cross-Channel Journey with Decisioning
description: "Learn how to orchestrate a multi-step journey incorporating real-time decisioning to select optimal channel, content, or offer."
solution: Journey Optimizer, Real-Time Customer Data Platform
---

# Cross-channel journey with decisioning

This guide provides a complete implementation reference for cross-channel journey with decisioning. It is designed for solution architects, marketing technologists, and implementation engineers who need to orchestrate multi-step, multi-channel journeys that incorporate real-time decisioning at one or more journey nodes.

Use this guide to understand the full landscape of implementation choices, evaluate trade-offs, and navigate to the relevant Experience League documentation for detailed configuration instructions.

Cross-channel journey with decisioning is the most sophisticated campaign orchestration pattern in the [!DNL Adobe Experience Platform] ecosystem. It extends multi-step orchestrated journeys by incorporating real-time decisioning — using [!DNL AJO] Decisioning to evaluate a profile's current context and dynamically select the optimal channel, content, or offer at one or more decision points within the journey canvas.

## Use case overview

Organizations increasingly need to deliver adaptive, personalized customer journeys that respond dynamically to each individual's real-time context rather than following a fixed, predetermined sequence. A customer's preferred channel, their engagement history, their loyalty tier, their predicted lifetime value, and their current product interests all factor into what the next-best action should be at each touchpoint.

Cross-channel journey with decisioning addresses this need by combining two powerful [!DNL AJO] capabilities: journey orchestration (which manages the multi-step flow, timing, conditions, and channel delivery) and decisioning (which evaluates eligibility rules, applies ranking strategies, and selects the optimal offer or content variant at each decision point).

This pattern is appropriate when:

- The journey must adapt dynamically to each profile's real-time state rather than following a fixed channel or content sequence
- Multiple offers, content variants, or channels are candidates at one or more journey nodes, and the best option should be selected based on profile context
- AI-assisted or formula-based ranking is needed to optimize offer selection across the journey
- The organization wants to consolidate channel selection logic and offer management into a centralized decision framework rather than maintaining complex branching logic

The target audience includes marketers managing lifecycle programs, loyalty journeys, win-back sequences, and onboarding flows where personalization at scale requires automated decision-making at each touchpoint.

## Key business objectives

The following business objectives are addressed by this use case pattern.

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

## Use case pattern

**Cross-channel journey with decisioning**

Orchestrate a multi-step, multi-channel journey that incorporates real-time decisioning at one or more nodes to select the optimal channel, content, or offer.

**Function chain:** Audience Evaluation > Journey Execution > Decision Node > Channel Selection > Message Delivery > Reporting

## Applications

The following applications are used to implement this use case pattern.

- **[!DNL Adobe Journey Optimizer] ([!DNL AJO])** — Journey orchestration (multi-step canvas design, entry conditions, waits, conditions, exit criteria), message authoring across channels, channel surface configuration, conflict and priority management
- **[!DNL Adobe Journey Optimizer] Decisioning** — Offer and content item management, eligibility rules, ranking strategies (priority, formula, AI), decision policies, placements, fallback offers
- **[!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP])** — Audience evaluation for journey entry and offer eligibility segments, profile enrichment with computed attributes and propensity scores, consent and governance enforcement
- **[!DNL Adobe Experience Platform] ([!DNL AEP])** — Real-Time Customer Profile store, Identity Service for cross-channel resolution, data modeling and ingestion infrastructure

## Foundational functions

The following foundational capabilities must be in place for this use case pattern. For each function, the status indicates whether it is typically required, assumed to be pre-configured, or not applicable.

| Foundational function | Status | What must be in place | Experience League reference |
| --- | --- | --- | --- |
| Administration & Governance | Assumed in Place | [!DNL AJO] sandbox with journey, campaign, and decisioning permissions configured. Channel surfaces for all possible delivery channels. User roles for journey designers, decisioning managers, and content authors. | [Sandboxes overview](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Access control overview](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Data Modeling & Preparation | Required | Profile schema must include attributes used for decisioning (for example, loyalty tier, purchase history, channel preferences, engagement scores). Offer catalog and decision item schemas must be configured. ExperienceEvent schemas must capture behavioral signals used by eligibility rules and ranking formulas. | [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Data Sources & Collection | Assumed in Place | Profile attributes and behavioral signals used by decisioning must be current. Real-time event streaming is needed if the journey uses event-triggered entry or exit criteria. Web SDK, Mobile SDK, or server-side collection must be active for channels that feed decisioning context. | [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Identity & Profile Configuration | Required | Cross-channel identity resolution is critical — the journey must resolve profiles across email, push, SMS, and web. Merge policies must produce a unified profile for decisioning. Identity namespaces for all customer identifiers (CRM ID, email, ECID, phone) must be configured. | [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Audience Definition & Segmentation | Required | Entry audience definition for the journey. Additional segments used for offer eligibility rules and condition branching within the journey. Evaluation method must match latency requirements (streaming for real-time entry, batch for scheduled). | [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Supporting functions

The following capabilities augment this use case pattern but are not required for core execution.

| Supporting function | Status | Why it matters | Experience League reference |
| --- | --- | --- | --- |
| Computed / Derived Attribute Creation | Recommended | Computed attributes such as Customer AI propensity scores, engagement scores, channel preference scores, and lifetime value calculations significantly improve decisioning quality. These enriched profile attributes enable more sophisticated eligibility rules and ranking formulas. | [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview), [Customer AI overview](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Data Lifecycle Management | Recommended | Offer history and decision event data accumulate over time and should have retention policies. Consent enforcement across multiple channels is critical — profiles without valid consent for a channel must be excluded from that channel's delivery path. | [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Consent in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted) |
| Data Usage Labeling & Enforcement | Recommended | Governance enforcement across multiple channels and offer types is important when decisioning may route profiles to different channels with different data usage restrictions. Ensures compliant offer delivery across all channels. | [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Policy enforcement](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview) |
| Monitoring & Observability | Included | Journey and decisioning monitoring is essential for production operations. Alerts for journey entry failures, decisioning fallback spikes, and delivery errors enable rapid issue resolution. | [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting & Analysis | Included | Journey and decisioning reports are covered in the reporting phase. CJA analysis of decisioning effectiveness, channel mix optimization, offer performance, and journey ROI provides the insights needed to refine ranking strategies and optimize the journey over time. | [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Application functions

This plan exercises the following functions from the application function catalog. Functions are mapped to implementation phases rather than numbered steps.

### [!DNL Journey Optimizer] ([!DNL AJO])

| Function | Implementation phase | Description |
| --- | --- | --- |
| Channel Configuration | Phase 2: Channel Configuration | Configure channel surfaces for all channels that decisioning may select or that the journey uses (email, SMS, push, in-app) |
| Message Authoring | Phase 4: Message Authoring | Author message content for each channel and integrate decision output — offer placements, dynamic content blocks, personalization tokens from selected offers |
| Decisioning | Phase 3: Decisioning Setup | Configure offer items, eligibility rules, ranking strategies, decision policies, and fallback offers for each decision point in the journey |
| Journey Orchestration | Phase 5: Journey Design & Activation | Design the multi-step journey canvas with entry conditions, decision nodes, channel routing, wait steps, message actions, and exit criteria |
| Conflict & Priority Management | Phase 5: Journey Design & Activation | Configure priority scores and conflict detection if multiple journeys may target the same profiles simultaneously |
| Frequency & Business Rules | Phase 5: Journey Design & Activation | Enforce message frequency caps across channels to prevent over-messaging within the multi-channel journey |
| Reporting & Performance Analysis | Phase 6: Reporting & Monitoring | Monitor journey and per-node delivery metrics, decisioning performance, and channel engagement |

### [!DNL Real-Time CDP] ([!DNL RT-CDP])

| Function | Implementation phase | Description |
| --- | --- | --- |
| Audience Evaluation | Phase 1: Audience Evaluation | Define and evaluate the entry audience or qualifying entry event; create eligibility segments used by decisioning |
| Profile Enrichment | Prerequisite / Supporting | Enrich profiles with computed attributes and propensity scores that improve decisioning quality |
| Consent & Governance Enforcement | Phase 2: Channel Configuration | Enforce consent preferences across all channels; ensure compliant offer delivery |

## Prerequisites

Complete the following before beginning implementation.

- [ ] [!DNL AJO] sandbox is provisioned with journey orchestration and decisioning capabilities enabled
- [ ] All target channels (email, SMS, push) have active, verified channel surfaces
- [ ] Profile schema includes attributes required for decisioning (loyalty tier, purchase history, channel preferences, engagement scores)
- [ ] Cross-channel identity resolution is configured — profiles can be resolved across email, push token, phone number, and web identifiers
- [ ] Entry audience is defined and evaluating with a non-zero population
- [ ] Offer catalog content (creative assets, copy, legal disclaimers) is approved and ready for configuration
- [ ] Consent data is being ingested and consent enforcement is active for all target channels
- [ ] Content templates and fragments for each channel are designed and approved
- [ ] Frequency capping rules are defined and deployed if the organization has cross-campaign frequency policies
- [ ] If using AI-ranked decisioning, a minimum of 1,000 conversion events exist for model training

## Implementation options

Review the following options and select the approach that best fits your requirements.

### Option A: Journey with offer decisioning (fixed channel, dynamic content)

**Best for:** Journeys where the channel sequence is predetermined but the content or offer at each touchpoint should be dynamically selected — loyalty journeys with personalized rewards, re-engagement with dynamic incentives, lifecycle nurture with AI-ranked content recommendations.

#### How it works

The journey canvas defines the fixed sequence of channels and timing (for example, Day 0: Email, Day 3: Push, Day 7: SMS). At each message action node, a decision policy selects the best offer or content to include in the message from a configured catalog of eligible items. Offers are managed in the [!DNL AJO] Decisioning catalog with eligibility rules that filter which offers a profile qualifies for, and ranking strategies that determine which eligible offer is the best fit.

This approach separates the "when and where" (journey orchestration) from the "what" (decisioning). The journey designer controls the channel flow, while the decisioning manager controls the offer catalog, eligibility rules, and ranking logic independently. This separation of concerns makes the implementation more maintainable and allows the offer catalog to evolve without modifying the journey canvas.

Offer placements are embedded directly into message content using the Email Designer or other channel editors. When the message is rendered at delivery time, the decisioning engine evaluates the profile's eligibility and ranking to select the optimal offer for each placement in the message.

#### Key considerations

- Channel sequence is static — all profiles follow the same channel path regardless of their preferences
- Decisioning complexity is lower since it only selects content/offers, not channels
- Offer catalog can be managed independently from the journey
- Fallback offers must be configured for each placement to handle profiles with no eligible personalized offers

#### Advantages

- Simpler journey canvas — no branching logic for channel selection
- Clear separation of concerns between journey design and offer management
- Easier to test and validate — each channel path is deterministic
- Lower implementation complexity and faster time to market
- Offer catalog changes take effect immediately without journey modifications

#### Limitations

- Cannot adapt the channel based on individual profile behavior or preferences
- Profiles who prefer one channel over another still receive messages on the predetermined channels
- Does not optimize for channel-level engagement rates

#### Experience League references

- [Deliver offers in messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Decision Management overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)

### Option B: Journey with dynamic channel selection (fixed content, dynamic channel)

**Best for:** Journeys where the content at each touchpoint is similar but the channel should be dynamically selected based on profile context — adaptive win-back (email vs. push vs. SMS based on engagement), next-best-action programs where channel optimization is the primary goal.

#### How it works

The journey uses condition nodes informed by profile attributes (such as channel preference scores, last engagement channel, or consent status) or decisioning output to route profiles to different channel paths. Each path delivers channel-specific content through its own message action node. The decisioning logic determines which channel is most likely to elicit engagement based on the profile's behavioral history.

Channel selection can be implemented using journey condition nodes with profile attribute evaluations (for example, if `channelPreference = "push"` route to the push path), or by using decisioning with channel-specific items where each "offer" represents a channel and the ranking strategy determines the best channel.

This approach optimizes the delivery channel while keeping content relatively consistent across channels. It requires message content to be authored for each possible channel, and channel surfaces must be configured for all candidate channels.

#### Key considerations

- Requires message content variants for each candidate channel
- Channel surfaces must be active for all possible channels
- Condition logic or decisioning configuration must account for consent — profiles without SMS consent cannot be routed to the SMS path
- Journey canvas is more complex with branching paths for each channel

#### Advantages

- Optimizes channel selection for each individual profile
- Increases overall engagement by reaching profiles on their preferred channel
- Respects channel-specific consent automatically through consent-aware routing
- Can incorporate engagement history and channel preference scores into routing decisions

#### Limitations

- More complex journey canvas with multiple channel branches
- Content must be authored separately for each channel (though the message intent is the same)
- Harder to test — must validate all possible channel paths
- Content personalization within each channel is static (no offer decisioning)

#### Experience League references

- [Condition activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Create a journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)

### Option C: Full adaptive journey (dynamic channel + dynamic content)

**Best for:** Maximum personalization — both the channel and the content/offer are dynamically selected at each node. Appropriate for high-value customer segments, sophisticated loyalty programs, and organizations with mature decisioning practices and rich profile data.

#### How it works

This option combines Options A and B. The journey uses decisioning at two levels: first, to determine which channel to use for each touchpoint, and second, to determine what content or offer to deliver in the selected channel. Each decision point in the journey evaluates the profile's current context to make both the channel and content selection.

The implementation requires comprehensive decisioning setup with decision policies for both channel selection and content/offer selection. Channel selection may use a decision policy where each item represents a channel with eligibility rules based on consent and engagement, while content selection uses a separate decision policy with offer items ranked by relevance.

This is the most complex variant and requires the deepest integration between journey orchestration and decisioning. It delivers the highest degree of personalization but also demands the most configuration, testing, and ongoing management.

#### Key considerations

- Requires two layers of decisioning — channel selection and content selection
- Journey canvas complexity is highest with nested branching and decisioning at each node
- Extensive testing required across all possible channel-content combinations
- Demands rich profile data (engagement history, channel preferences, product affinity, propensity scores) for effective decisioning
- AI-ranked decisioning benefits significantly from computed attributes

#### Advantages

- Maximum personalization — every touchpoint is optimized for channel and content
- Best engagement and conversion potential for well-configured implementations
- Centralizes all personalization logic in decisioning rather than static journey branches
- Can continuously improve through AI ranking model learning

#### Limitations

- Highest implementation complexity and longest time to market
- Requires the most extensive offer catalog and channel content preparation
- More difficult to troubleshoot when delivery issues arise
- Demands mature data infrastructure with rich profile attributes
- AI ranking requires sufficient conversion event volume for model training

#### Experience League references

- [Decision Management overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Ranking strategies](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Option comparison

Use the following table to compare the three implementation options at a glance.

| Criteria | Option A: Offer decisioning | Option B: Dynamic channel | Option C: Full adaptive |
| --- | --- | --- | --- |
| Best for | Fixed channel sequence, dynamic content | Channel optimization, consistent content | Maximum personalization across both dimensions |
| Complexity | Medium | Medium-High | High |
| Journey canvas | Simple (linear with decisioning at action nodes) | Moderate (branching for channel paths) | Complex (nested branching with multi-level decisioning) |
| Decisioning scope | Content/offer selection only | Channel selection only | Both channel and content selection |
| Content requirements | One set of content per channel (with offer placements) | Content for each candidate channel | Content with offer placements for each candidate channel |
| Profile data needs | Moderate (offer eligibility attributes) | Moderate (channel preference, engagement) | High (both channel and offer attributes) |
| Time to market | Faster | Moderate | Longest |
| Ongoing management | Offer catalog management | Channel routing logic management | Both offer catalog and channel routing |
| Personalization depth | Content varies, channel fixed | Channel varies, content similar | Both channel and content vary |

### Choose the right option

Use the following guidance to determine the best option for your situation.

- **Start with Option A** if your channel strategy is already defined (for example, "we always send email first, then push, then SMS") and the primary personalization need is selecting the right offer or content at each touchpoint. This is the most common starting point for organizations new to decisioning.

- **Choose Option B** if channel optimization is your primary goal — you want to reach each customer on the channel they are most likely to engage with, but the message content is relatively consistent across channels. This requires channel preference data on profiles.

- **Choose Option C** only when you have mature decisioning infrastructure, rich profile data (including computed attributes and propensity scores), a well-populated offer catalog, and the organizational capacity to manage the complexity. Many organizations start with Option A or B and evolve to Option C as their decisioning maturity increases.

- **If you are uncertain**, begin with Option A. It delivers meaningful personalization with the lowest complexity, and the offer catalog you build for Option A is directly reusable if you later evolve to Option C.

## Implementation phases

The following phases walk through the end-to-end implementation of this use case pattern.

### Phase 1: Audience evaluation

**Application function:** [!DNL RT-CDP]: Audience Evaluation

This phase configures the entry audience that determines which profiles enter the journey, and any additional segments used for offer eligibility rules or condition branching within the journey. The audience definition is the foundation for all downstream journey and decisioning logic.

#### Decision: Entry type

How should profiles enter the journey — via a scheduled audience read or a real-time event trigger?

>[!NOTE]
>Select one entry type based on your journey's timing and triggering requirements.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Read Audience (batch entry) | Lifecycle programs, loyalty journeys, scheduled re-engagement campaigns | Profiles enter in batches at scheduled times; audience is evaluated at read time; supports large audience sizes |
| Audience Qualification (streaming) | Behavior-triggered journeys where entry should happen when a profile enters or exits a segment | Near real-time entry; requires streaming-eligible segment definition; good for milestone-based journeys |
| Unitary Event (event trigger) | Specific event should trigger the journey (for example, purchase, cart abandonment, registration) | Real-time entry on event; requires event schema configuration; limited to 5,000 events/second |

#### Decision: Audience evaluation method

How quickly must the audience qualify profiles?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Batch | Daily or periodic audience updates are sufficient; scheduled campaign-style journeys | Processes up to 24M profiles per job; schedule-based; most segment rule expressions supported |
| Streaming | Real-time audience membership is needed for event-triggered or qualification-based entry | Near real-time; limited segment rule function set; no time-based aggregations |
| Edge | Same-session qualification needed | Millisecond latency; simple attribute checks only; limited to edge profile attributes |

#### Key configuration details

**UI navigation:** Customer > Audiences > Create audience > Build rule

- Define the entry audience using Segment Builder with segment rule expressions targeting the relevant profile attributes and behavioral events
- Create additional eligibility segments if offer eligibility rules will reference segment membership (for example, "High Value Customers", "Loyalty Gold Tier")
- Verify audience population is non-zero before proceeding to journey configuration
- Select the merge policy that produces the unified profile view needed for decisioning

#### Experience League documentation

- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Profile Query Language reference](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Phase 2: Channel configuration

**Application function:** [!DNL AJO]: Channel Configuration

This phase configures channel surfaces for every channel that the journey may use for message delivery. All candidate channels must have active, verified surfaces before messages can be authored or the journey can be published. For this pattern, you will typically configure surfaces for email, SMS, and push at minimum — and potentially in-app or web if decisioning may select those channels.

#### Decision: Which channels to configure

Which channels are candidates for the journey — either as fixed journey steps (Options A/B) or as decisioning-selectable channels (Options B/C)?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Email only | Single-channel journey with offer decisioning (Option A, email only) | Simplest configuration; requires subdomain delegation and IP warmup |
| Email + Push | Two-channel journey; common for engagement-focused journeys | Push requires APNs/FCM credentials; mobile app must have SDK integrated |
| Email + SMS + Push | Full cross-channel journey; most common for Options B and C | SMS requires provider credentials (Sinch, Twilio, Infobip); each channel needs its own surface |
| Email + SMS + Push + In-App | Maximum channel coverage including in-session surfaces | In-app requires mobile SDK and app surface configuration |

#### Decision: Subdomain delegation method (email)

How should the sending subdomain be delegated to Adobe?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Full delegation | Organization wants Adobe to manage all DNS records for the sending subdomain | Simplest setup; Adobe handles SPF, DKIM, DMARC; less control over DNS |
| CNAME delegation | Organization needs to maintain control of DNS records | More complex setup; customer manages DNS; provides more flexibility |

#### Key configuration details

**UI navigation:** Administration > Channels > Channel surfaces > Create surface

- For email: configure subdomain, IP pool, sender name, reply-to address, and unsubscribe handling
- For SMS: configure SMS provider credentials and sender number
- For push: configure APNs and FCM credentials for iOS and Android
- Verify each surface is in Active status before proceeding
- Confirm IP warmup is complete for email sending IPs

#### Experience League documentation

- [Get started with email configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delegate subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Create IP pools](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Configure SMS channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configure push notification channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Phase 3: Decisioning setup

**Application function:** [!DNL AJO]: Decisioning

This phase configures the complete decisioning framework including placements, eligibility rules, personalized offers, fallback offers, collection qualifiers, collections, ranking strategies, and decision policies. This phase creates the decision logic that will be invoked at journey decision points.

#### Decision: Decisioning scope

What should decisioning select — offers/content (Option A), channels (Option B), or both (Option C)?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Offer/content selection only | Channel sequence is fixed; personalization is in the content | Decision policies target offer items with content representations per placement |
| Channel selection only | Content is consistent; optimization is on the delivery channel | Decision items represent channels; eligibility includes consent checks; ranking uses engagement data |
| Both channel and content | Full adaptive personalization across channel and content | Requires two layers of decision policies; most complex but highest personalization |

#### Decision: Ranking strategy

How should eligible offers be ranked to select the best one?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Priority-based (manual) | Simple ranking where business rules determine offer importance | Each offer gets a priority score; highest priority wins; deterministic and easy to understand |
| Formula-based (custom expression) | Ranking should factor in profile attributes (for example, CLV, tier, affinity score) | Custom ranking formula evaluates profile context; more dynamic than priority; no ML required |
| AI-ranked (auto-optimization) | Ranking should be optimized automatically based on historical conversion data | AI model learns from conversion events; requires minimum 1,000 events for training; continuously improves |

#### Decision: Offer capping

Should there be limits on how many times an offer is shown?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Per-profile cap | Prevent the same offer from being shown repeatedly to the same profile | Protects against offer fatigue; counter lag possible under high throughput |
| Global cap | Limit total impressions across all profiles (for example, limited inventory promotions) | Controls total exposure; useful for supply-limited offers |
| No cap | Every eligible impression should show the offer | Simplest; appropriate for evergreen content or unlimited offers |

#### Key configuration details

**UI navigation:** Components > Decision Management > Placements / Offers / Decisions

- Create placements for each channel and content type combination (for example, email HTML banner, push JSON, SMS text)
- Define eligibility rules using segment rule expressions that reference profile attributes or audience membership
- Create personalized offers with representations for each placement, assign eligibility rules, and set priority
- Create a fallback offer covering all placements — this is returned when no personalized offer qualifies
- Organize offers into collections using collection qualifiers (tags)
- Configure ranking strategy — priority-based, formula-based, or AI-ranked
- Create decision policies that bind placements, collections, ranking strategy, and fallback offer
- Approve all offers before they can be selected by decisioning

#### Where options diverge

**For Option A (Offer Decisioning):**
Create placements and offers focused on content personalization within each channel (for example, email hero banner offer, email footer offer, push notification body offer). Decision policies select the best content for each placement in the message.

**For Option B (Dynamic Channel Selection):**
Create decision items that represent each channel. Eligibility rules include consent checks (for example, a profile must have SMS consent to be eligible for the SMS item). Ranking uses channel engagement scores or formula-based expressions.

**For Option C (Full Adaptive):**
Configure two layers of decisioning: one set of decision policies for channel selection and a separate set for content/offer selection within the selected channel. Both layers require placements, offers, eligibility rules, and ranking strategies.

#### Experience League documentation

- [Decision Management overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Create placements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Create decision rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Create personalized offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Create fallback offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Create collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Create decisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Ranking strategies](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Phase 4: Message authoring

**Application function:** [!DNL AJO]: Message Authoring

This phase configures message content for each channel and touchpoint in the journey, integrating decisioning output (selected offer content) into the message templates. Each message action node in the journey requires authored content with the appropriate channel surface, personalization tokens, and offer placement integrations.

#### Decision: Content approach

How should message content be created for each channel?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Template-based | Organization has established brand templates; consistency is important | Faster authoring; ensures brand consistency; may limit design flexibility |
| Design from scratch | Unique creative for this journey; no existing templates | Full design control; longer authoring time; use Email Designer drag-and-drop |
| Import HTML | Creative team produces HTML externally; import into [!DNL AJO] | Preserves external design workflow; requires HTML compatibility with Email Designer |

#### Decision: Personalization scope

What level of personalization should messages include beyond decisioning output?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Basic personalization (name, greeting) | Minimal personalization needs beyond offer selection | Simple Handlebars expressions; low complexity |
| Conditional content blocks | Different content sections for different segments or attributes | Uses dynamic content rules; content varies by profile attribute or segment membership |
| Full personalization with decisioning integration | Offer placements embedded in message, combined with profile-based personalization | Combines offer decisioning output with Handlebars personalization tokens; richest experience |

#### Key configuration details

**UI navigation:** Select campaign or journey action > Edit content > Email Designer / Channel editor

- Author message content for each channel used in the journey (email, SMS, push, in-app)
- Embed offer decision placements into message content where decisioning-selected offers should appear
- Add personalization expressions using Handlebars syntax for profile attributes (for example, `{{profile.person.name.firstName}}`)
- Configure conditional content blocks for segment-specific messaging
- Create reusable content fragments for shared elements (headers, footers, legal disclaimers)
- Preview and test with sample profiles to verify personalization renders correctly
- Send proof messages for stakeholder review

#### Where options diverge

**For Option A (Offer Decisioning):**
Each message includes offer placements where decisioning-selected content appears. The message layout is consistent, but the offer area dynamically shows the best offer for each profile.

**For Option B (Dynamic Channel Selection):**
Each channel has its own message content authored separately. Content is similar across channels but adapted to channel constraints (email HTML vs. SMS text vs. push notification format).

**For Option C (Full Adaptive):**
Each channel has its own message content with embedded offer placements. Both the channel and the offer content within that channel are dynamically selected.

#### Experience League documentation

- [Design email content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Deliver offers in messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Work with content templates](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Work with content fragments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Create an SMS message](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Design a push notification](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### Phase 5: Journey design and activation

**Application function:** [!DNL AJO]: Journey Orchestration, [!DNL AJO]: Conflict & Priority Management, [!DNL AJO]: Frequency & Business Rules

This phase configures the complete journey canvas including entry configuration, decision nodes linked to configured decision policies, condition splits for channel routing (Options B/C), message action nodes for each channel path, wait nodes between touchpoints, exit criteria, conflict/priority settings, and frequency capping rules. This phase assembles all previously configured components into the orchestrated journey flow and activates it.

#### Decision: Re-entrance policy

Can profiles re-enter the journey after completing or exiting?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Allow re-entrance (with cooldown) | Recurring journeys where profiles may qualify again (for example, quarterly loyalty renewal) | Set a cooldown period (minimum 5 minutes) to prevent immediate re-entry; profile restarts from the beginning |
| No re-entrance | One-time journeys where each profile should only traverse once (for example, onboarding) | Profile cannot re-enter after completion or exit; simpler behavior |

#### Decision: Exit criteria

Under what conditions should a profile be removed from the journey before completion?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Audience membership change | Profile should exit when they leave the entry audience or enter a suppression audience | Real-time exit on segment change; useful for "converted" or "opted out" exits |
| Event occurrence | A specific event (for example, purchase, unsubscribe) should trigger exit | Real-time exit on event; requires event schema configuration |
| Timeout | Maximum duration in the journey has elapsed | Default max is 91 days; prevents profiles from remaining indefinitely |

#### Decision: Journey timeout

What is the maximum duration a profile can remain in the journey?

| Option | When to choose | Considerations |
| --- | --- | --- |
| 91 days (maximum) | Long-running lifecycle journeys with extended nurture sequences | Maximum allowed duration; profiles exit after 91 days regardless |
| Custom shorter duration | Time-bound campaigns or seasonal journeys | Set based on journey business logic; shorter timeout reduces stale profiles |

#### Decision: Conflict and priority settings

Should this journey have priority scoring for conflict resolution with other journeys/campaigns?

| Option | When to choose | Considerations |
| --- | --- | --- |
| High priority (70-100) | Critical customer journeys (retention, loyalty) that should take precedence | Higher priority wins when multiple communications compete; use sparingly |
| Medium priority (30-69) | Standard lifecycle journeys | Balanced priority; may be suppressed by higher-priority communications |
| Low priority (0-29) | Supplemental or informational journeys | Will be suppressed when competing with more important communications |

#### Key configuration details

**UI navigation:** Journeys > Create Journey

- Create the journey and configure properties (name, description, timezone, timeout)
- Configure entry: Read Audience (for batch) or event trigger (for real-time)
- Add decision nodes linked to configured decision policies from Phase 3
- Add condition splits for channel routing based on decision output or profile attributes (Options B/C)
- Add message action nodes for each channel path, linking to the authored content from Phase 4
- Add wait nodes between touchpoints (minimum 1 hour for audience-read journeys)
- Define exit criteria (audience change, event, timeout)
- Assign priority score for conflict resolution
- Configure frequency capping if cross-journey frequency limits apply
- Test the journey in test mode with test profiles before publishing
- Publish the journey to make it live

#### Where options diverge

**For Option A (Offer Decisioning):**
The journey canvas is linear with decision policies embedded in each message action node. No branching for channel selection. The offer decision is made at message render time within the action node.

**For Option B (Dynamic Channel Selection):**
After each wait step, add a condition node that evaluates channel selection criteria (profile attributes, decisioning output, or consent status). Each condition branch leads to a channel-specific message action node. Include a default/else path for profiles that do not match any condition.

**For Option C (Full Adaptive):**
Combine channel selection condition nodes with decision policy-embedded message action nodes. At each touchpoint: first, a condition or decision determines the channel; then, within the selected channel's message action, a decision policy selects the optimal offer/content.

#### Experience League documentation

- [Create a journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journey properties](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Read audience activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Condition activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Wait activity](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Add a message in a journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Exit criteria](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Journey entry management](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Test your journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Publish the journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [Priority scores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Conflict and priority management overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Frequency rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### Phase 6: Reporting and monitoring

**Application function:** [!DNL AJO]: Reporting & Performance Analysis

This phase configures journey and decisioning performance monitoring through live reports (during execution) and historical reports (after completion). Decisioning-specific metrics including offer selection distribution, fallback rates, and ranking effectiveness. Optionally, CJA workspace analysis for deep cross-channel journey and decisioning ROI analysis.

#### Decision: Reporting depth

What level of reporting analysis is needed?

| Option | When to choose | Considerations |
| --- | --- | --- |
| [!DNL AJO] native reports only | Operational monitoring of delivery and engagement metrics | Built-in live and historical reports; no additional configuration; limited to [!DNL AJO] metrics |
| [!DNL AJO] + CJA analysis | Deep cross-channel analysis, decisioning effectiveness, journey ROI, cohort analysis | Requires CJA connection and data view; provides attribution, funnel, and cohort analysis capabilities |

#### Key configuration details

**UI navigation:** Journeys > Select journey > Live report / All time report

- Monitor journey live report during initial execution for entry, exit, and per-node metrics
- Review decisioning performance: offer selection distribution, fallback offer rate, ranking effectiveness
- After journey completion, review historical reports for end-to-end funnel analysis
- For CJA analysis: ensure CJA connection includes [!DNL AJO] datasets (Message Feedback Event, Email Tracking Event)
- Build CJA workspace with panels for channel mix analysis, offer performance comparison, and journey conversion funnels
- Create annotations for journey launch dates and significant configuration changes

#### Experience League documentation

- [Journey live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Journey global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Work with Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Implementation considerations

Review the following guardrails, common pitfalls, best practices, and trade-off decisions before and during implementation.

### Guardrails and limits

- Maximum of 500 live journeys per sandbox — [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum journey duration is 91 days (global timeout)
- Maximum of 50 activities per journey canvas
- Read Audience journeys can process up to 20,000 profiles per second
- Unitary event journeys support up to 5,000 events per second per sandbox
- Maximum of 10,000 approved personalized offers per sandbox
- Maximum of 30 placements per decision
- Offer Delivery response time SLA: less than 500ms at P95 for single-scope requests
- AI ranking models require a minimum of 1,000 conversion events for training
- Maximum of 10 channel surfaces per channel type per sandbox
- Wait steps have a minimum duration of 1 hour for audience-read journeys
- Journey re-entrance cooldown minimum is 5 minutes
- Maximum of 4,000 segment definitions per sandbox — [Platform guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### Common pitfalls

**Decision always returns fallback offer:** Verify that personalized offers are approved (not in draft state), within their validity date range, and that eligibility rules match the target profiles' attributes. Check that offer capping limits have not been reached. Test with a profile that should clearly qualify for a personalized offer.

**Journey publishes but profiles are not entering:** For audience-read journeys, confirm the audience has an evaluated population greater than zero. For event-triggered journeys, verify the event schema, triggering conditions, and that events are being sent. Check that the entry audience merge policy matches the journey's expected merge policy.

**Ranking formula not applied correctly:** Verify the formula syntax is valid and references accessible profile attributes. Formula errors silently fall back to priority-based ranking without warning. Test ranking with profiles that have different attribute values to confirm the formula produces the expected ordering.

**Channel routing ignores consent:** Condition nodes for channel selection must include consent checks. A profile without SMS consent must not be routed to the SMS path. Build consent into eligibility rules when using decisioning for channel selection (Option B/C).

**Offer capping counters lag under high throughput:** Offer capping counters may have a delay of a few seconds in high-throughput scenarios. If exact capping is critical, use global caps with a buffer or combine with frequency rules.

**Journey canvas exceeds 50-activity limit:** Complex Option C journeys with many channel branches and decision nodes can approach the 50-activity limit. Simplify by consolidating condition logic, reducing the number of touchpoints, or splitting into multiple sequential journeys.

**Edge decisions return empty personalization:** If using edge decisioning for real-time decisions, ensure the datastream has the [!DNL Adobe Journey Optimizer] service enabled and that the decision scope is correctly formatted. Edge decisions are limited to profile attributes available in the edge profile store.

### Best practices

**Start simple and evolve:** Begin with Option A (fixed channel, dynamic offers) to validate the decisioning framework, then evolve to Options B or C as your data maturity and organizational capacity increase.

**Invest in profile enrichment:** Computed attributes such as engagement scores, channel preference indices, and Customer AI propensity scores dramatically improve decisioning quality. Build these enrichment attributes before configuring complex ranking strategies.

**Always configure fallback offers:** Every decision policy must have a fallback offer. Design fallback offers as genuinely valuable content (not empty placeholders) since they serve profiles who do not qualify for any personalized offer.

**Test with diverse profiles:** Use test mode with profiles that represent different eligibility paths, channel preferences, and attribute combinations. Verify that each possible journey path and decisioning outcome works correctly before publishing.

**Monitor fallback rates as a health metric:** A high fallback offer rate indicates that eligibility rules are too restrictive or the offer catalog does not cover enough profile segments. Target a fallback rate below 20% for well-configured decisioning.

**Use content fragments for cross-channel consistency:** Create shared content fragments (headers, footers, legal disclaimers, unsubscribe blocks) to maintain brand consistency across email, SMS, and push messages within the journey.

**Configure exit criteria proactively:** Define exit criteria for conversion events (for example, purchase, registration) so that profiles who complete the desired action are removed from the journey immediately rather than continuing to receive messages.

**Assign meaningful priority scores:** When running multiple journeys and campaigns, assign priority scores based on business impact. High-value retention journeys should have higher priority than informational communications.

### Trade-off decisions

Review the following trade-offs to inform your implementation choices.

#### Decisioning complexity vs. time to market

More sophisticated decisioning (Option C with AI ranking) delivers higher personalization but requires significantly more configuration, data preparation, and testing time.

- **Option A/B favors:** Faster deployment, simpler testing, lower ongoing management overhead
- **Option C favors:** Maximum personalization, continuous AI-driven optimization, highest engagement potential
- **Recommendation:** Start with Option A or B for initial launch. Collect performance data and build profile enrichment attributes in parallel. Evolve to Option C when you have at least 1,000 conversion events for AI ranking training and a well-populated offer catalog.

#### Static branching vs. decisioning for channel selection

Channel selection can be implemented through simple journey condition nodes (evaluating profile attributes directly) or through the decisioning framework (where channels are modeled as decision items with eligibility and ranking).

- **Static condition nodes favor:** Simplicity, transparency, easy troubleshooting. Best when channel selection logic is straightforward (for example, "if push token exists and last push open within 30 days, use push; otherwise email").
- **Decisioning-based channel selection favors:** Centralized management, AI optimization potential, ability to evolve ranking logic without modifying the journey canvas. Best when channel selection is complex and should improve over time.
- **Recommendation:** Use static condition nodes for Option B when channel selection criteria are simple and well-defined. Use decisioning-based channel selection when you want AI to optimize channel selection over time or when the channel selection logic is complex enough to benefit from centralized eligibility and ranking management.

#### Offer granularity vs. catalog manageability

A large, granular offer catalog with many targeted offers produces more precise personalization but requires more management effort. A smaller catalog with broader eligibility is easier to manage but less personalized.

- **Large catalog (many specific offers) favors:** Higher personalization precision, more relevant selections for diverse audiences, lower fallback rates
- **Small catalog (fewer broad offers) favors:** Easier management, faster setup, simpler testing, lower risk of orphaned offers
- **Recommendation:** Start with 5-15 personalized offers plus a fallback per decision. Add more offers as you observe which segments receive fallback offers most frequently. Use collection qualifiers to organize offers by category, tier, or product line for manageable growth.

#### Priority-based vs. AI-ranked decisioning

Priority-based ranking is deterministic and transparent. AI-ranked decisioning optimizes automatically but requires training data and is less transparent.

- **Priority-based ranking favors:** Predictability, transparency, immediate deployment, no training data requirement
- **AI-ranked decisioning favors:** Continuous optimization, data-driven selection, ability to discover non-obvious offer-profile affinities
- **Recommendation:** Use priority-based or formula-based ranking for initial deployment. Transition to AI-ranked decisioning once you have accumulated at least 1,000 conversion events and want to move from rule-based to model-based optimization.

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
