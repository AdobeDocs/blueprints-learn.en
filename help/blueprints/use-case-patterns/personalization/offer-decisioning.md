---
title: Offer Decisioning
description: Learn how to use centralized decision logic to select the next-best offer or content for a profile across channels.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 8fd511b3-0200-41bf-aff1-e3f2a00a578e
---
# Offer decisioning

This guide provides a comprehensive implementation reference for offer decisioning using [!DNL Adobe Journey Optimizer] (AJO) Decisioning and [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP). It is designed for solution architects, marketing technologists, and implementation engineers who need to implement centralized offer selection logic that determines the next-best offer for each customer profile across channels.

Use this guide to understand what needs to be configured, where choices exist, and what trade-offs apply to each decision.

The pattern decouples the "what to show" decision from the "where to show it" channel logic, enabling consistent, optimized offer selection across email, web, mobile app, and any other touchpoint. AJO Decisioning manages the full offer lifecycle: offer creation and catalog management, eligibility rules (who can see each offer), ranking strategies (how to select among eligible offers), placements (where offers appear), and decision policies (which bind everything together).

## Use case overview

Organizations frequently need to present the most relevant offer, promotion, or incentive to each customer at the moment of interaction. Whether the interaction occurs in an email campaign, on a website homepage, within a mobile app, or at a decision point within a multi-step journey, the challenge is the same: select the optimal offer from a catalog of available options based on who the customer is, what they qualify for, and which offer is most likely to drive the desired outcome.

Offer decisioning addresses this by centralizing all offer selection logic in AJO's Decision Management engine. Rather than hardcoding offer assignments into individual campaigns or channels, the decision engine evaluates each profile's attributes, audience membership, and contextual signals to determine the best offer in real time. This centralization ensures that the same customer receives consistent, optimized offers regardless of which channel they engage through.

This pattern differs from known-visitor web/app personalization in scope -- offer decisioning is channel-agnostic and centralized, while known-visitor personalization focuses on digital surface personalization. It differs from behavioral recommendation in approach -- offer decisioning uses explicit eligibility rules and ranking strategies, while behavioral recommendation emphasizes behavioral signal-driven recommendations using selection strategies and ML models.

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

## Use case pattern

This section describes the function chain and pattern definition for offer decisioning.

**Offer decisioning**

Use centralized decision logic to select the next-best offer or content for a profile across channels.

**Function chain:** Audience Evaluation > Offer Eligibility > Ranking Strategy > Decision Execution > Delivery > Reporting

See the [Implementation options](#implementation-options) section for how each composition manifests.

## Applications

The following Adobe applications are used in this use case pattern.

- **[!DNL Adobe Journey Optimizer] (AJO)** -- Decision Management engine for offer creation, eligibility rules, ranking strategies, placements, and decision policies; channel configuration and message authoring for offer delivery; campaign and journey execution
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** -- Audience evaluation for offer eligibility segments; profile data and computed attributes used in eligibility and ranking
- **[!DNL Adobe Experience Platform] (AEP)** -- Unified profile store, identity resolution, and data foundation supporting both AJO and RT-CDP

## Foundational functions

The following foundational capabilities must be in place for this use case pattern. For each function, the status indicates whether it is typically required, assumed to be pre-configured, or not applicable.

| Foundational function | Status | What must be in place | Experience League reference |
| --- | --- | --- | --- |
| Administration & Governance | Assumed in Place | AJO sandbox with Decisioning permissions enabled. Offer management roles (Decision Manager, Offer Approver) assigned to the implementation team. | [Sandboxes overview](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Access control overview](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Data Modeling & Preparation | Required | Profile schema must include attributes used for offer eligibility rules (e.g., loyalty tier, purchase history, subscription type). An offer response/interaction schema for tracking offer impressions, clicks, and conversions should be in place. | [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Data Sources & Collection | Assumed in Place | Profile attributes used in eligibility rules must be current. For web delivery (Option B), Web SDK must be implemented with AJO service enabled on the datastream. For email delivery, profile attributes must be resolvable at send time. | [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Identity & Profile Configuration | Assumed in Place | Profiles must be resolvable across all channels where offers are delivered. For cross-channel offer consistency, unified identity is critical -- the same profile must be recognized in email, web, and mobile contexts. An edge-active merge policy is required for real-time web/app delivery. | [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Audience Definition & Segmentation | Required | Audiences used as offer eligibility criteria must be defined and evaluated (e.g., "high-value customers," "trial users," "loyalty gold tier"). Evaluation method must match delivery latency -- edge evaluation for real-time web/app, batch or streaming for email campaigns. | [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Supporting functions

The following capabilities augment this use case pattern but are not required for core execution.

| Supporting function | Status | Why it matters | Experience League reference |
| --- | --- | --- | --- |
| Computed / Derived Attribute Creation | Recommended | Customer AI propensity scores, lifetime value calculations, and engagement metrics significantly improve ranking strategy effectiveness. Computed attributes such as "days since last purchase" or "total spend in 90 days" enable more precise eligibility rules and formula-based ranking. | [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview), [Customer AI overview](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Data Lifecycle Management | Recommended | Offer history and decision event data accumulate over time. Retention policies (expiration) should be configured for offer interaction event datasets to manage storage and comply with data retention requirements. | [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Dataset expirations](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| Data Usage Labeling & Enforcement | Recommended | Governance labels ensure that offers with sensitive targeting criteria (e.g., financial status, health conditions) comply with data usage policies. Labels on fields used in eligibility rules prevent non-compliant offer targeting. | [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) |
| Monitoring & Observability | Recommended | Decision engine performance, fallback rates, and offer delivery health should be monitored. Alerts for high fallback rates can indicate eligibility rule misconfiguration or data freshness issues. | [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting & Analysis | Included | Offer performance reporting is part of the function chain (Phase 7). CJA analysis enables cross-channel offer effectiveness measurement, revenue impact attribution, and optimization opportunity identification. | [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## Application functions

This plan exercises the following functions from the Application Function Catalog. Functions are mapped to implementation phases rather than numbered steps.

### [!DNL Journey Optimizer] (AJO)

The following table lists AJO functions and the implementation phases where they are configured.

| Function | Implementation phase | Description |
| --- | --- | --- |
| Decisioning | Phase 3: Decisioning Setup | Create offer items, define eligibility rules, configure ranking strategies, create fallback offers, define placements, and build decision policies |
| Channel Configuration | Phase 4: Channel & Surface Configuration | Configure email, web, in-app, or code-based channel surfaces for offer delivery |
| Message Authoring | Phase 5: Content & Delivery Configuration | Design message templates with offer placement zones; configure code-based experiences for web/app delivery |
| Campaign Execution | Phase 5: Content & Delivery Configuration | Execute scheduled or API-triggered campaigns that invoke decision policies (Option A) |
| Content Experimentation | Phase 5: Content & Delivery Configuration | Optionally A/B test different ranking strategies or offer creative variants |
| Reporting & Performance Analysis | Phase 7: Reporting & Performance Monitoring | Monitor offer selection distribution, acceptance rates, fallback rates, and channel-level performance |

### [!DNL Real-Time CDP] (RT-CDP)

The following table lists RT-CDP functions and the implementation phases where they are configured.

| Function | Implementation phase | Description |
| --- | --- | --- |
| Audience Evaluation | Phase 2: Audience Evaluation | Define and evaluate audiences used for offer eligibility rules; select appropriate evaluation method (batch, streaming, or edge) |
| Profile Enrichment | Phase 1 (Supporting): Computed Attributes | Enrich profiles with computed attributes and propensity scores that improve ranking strategy effectiveness |

## Prerequisites

Complete the following prerequisites before beginning implementation.

- [ ] AJO sandbox with Decision Management capabilities enabled
- [ ] User roles with Decision Management permissions (create/edit offers, placements, decisions)
- [ ] Profile schema includes attributes required for offer eligibility (e.g., loyalty tier, customer segment, subscription level)
- [ ] Profile data is current and actively ingested for eligibility attribute freshness
- [ ] For Option A (Email): Email channel surface configured with verified subdomain and warmed IP pool
- [ ] For Option B (Web/App): Web SDK implemented with AJO service enabled on the datastream; edge-active merge policy configured
- [ ] For Option C (Journey): Journey canvas permissions and at least one journey entry event or audience configured
- [ ] Offer creative assets (images, copy, CTAs) prepared for each offer and placement combination
- [ ] Fallback offer content prepared for each placement
- [ ] Audiences for offer eligibility rules defined and evaluated in RT-CDP

## Implementation options

This section describes the available implementation options for offer decisioning. Each option serves a different delivery channel and use case context.

### Option A: Email offer decisioning

This option is best for selecting the best offer to include in outbound email campaigns -- promotional emails, newsletter personalization, lifecycle emails with dynamic offer content. The decision is made at message rendering time for each recipient.

#### How it works

Decision policies are invoked during email message rendering to select the best offer for each recipient. The email template includes an offer placement zone where the decisioning engine inserts the selected offer's content representation (image, HTML, or text). At send time, the engine evaluates each recipient's profile against offer eligibility rules, applies the ranking strategy, and embeds the winning offer's content into the email.

This approach works with both scheduled campaigns (evaluated at campaign execution time) and journey-embedded emails (evaluated when the profile reaches the message action node). The offer content -- image, headline, body copy, and CTA -- is personalized per recipient based on the decision outcome.

#### Key considerations

- Offer eligibility is evaluated at send time using the profile's current state
- Batch audience evaluation is sufficient since decisions happen during message rendering
- Each offer needs an HTML or image content representation for the email placement
- Fallback offer must have content for every email placement used

#### Advantages

- Simplest implementation path -- uses standard campaign or journey email delivery
- No client-side SDK requirements
- Works with existing email infrastructure and channel surfaces
- Supports large audience volumes through batch campaign execution

#### Limitations

- Decision is made at send time; cannot adapt to post-send behavior
- Offer content is static once the email is delivered (no real-time updates)
- Limited to profile attributes available in the hub profile store (not edge)

#### Experience League resources

- [Deliver offers in messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Create a campaign](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

### Option B: Web/app real-time offer decisioning

This option is best for real-time offer selection on web pages or mobile apps -- homepage promotional banners, account dashboard offer widgets, in-app offer cards, or any digital surface where the offer should be selected at the moment the page loads or the screen renders.

#### How it works

Decision policies are invoked at page load or app screen render via the Edge Decisioning network or code-based experiences. When a visitor loads a page, the Web SDK sends a request to the Edge Network, which evaluates the visitor's edge profile against offer eligibility rules and ranking strategies. The selected offer is returned in the response and rendered in the configured placement on the digital surface.

For code-based experiences, the application retrieves the decision response and renders the offer content using custom front-end logic. For web channel experiences, the AJO web channel can inject the offer content directly into the page using visual or code-based authoring.

#### Key considerations

- Requires Web SDK or Mobile SDK implementation with AJO service enabled on the datastream
- Edge-active merge policy is required for real-time profile lookups
- Audiences used for eligibility must support edge evaluation (simple attribute checks and segment membership)
- Offer content representations should use JSON or image URL formats for client-side rendering
- Impression tracking must be implemented to capture offer views and clicks

#### Advantages

- Real-time, in-session offer selection based on the visitor's current profile state
- Sub-second decision latency via Edge Network
- Offers adapt to the most current profile data available at the edge
- Supports A/B testing of offer strategies via content experimentation

#### Limitations

- Requires client-side SDK implementation (Web SDK or Mobile SDK)
- Edge profile has a subset of full hub profile attributes -- complex eligibility rules may not evaluate correctly
- Edge segments have segment rule complexity restrictions (no time-series queries)
- Requires front-end development for custom rendering in code-based experiences

#### Experience League resources

- [Deliver offers using the Edge Decisioning API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Code-based experience channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based-experience/get-started-code-based)

### Option C: Journey decision node

This option is best for offer selection within a multi-step journey -- selecting the best offer at a decision point in a customer journey, then delivering it through the next action node. Use this when the offer decision is part of a broader orchestration flow with waits, conditions, and multiple message actions.

#### How it works

Decision policies are invoked from a decision node within an AJO journey canvas. When a profile reaches the decision node, the engine evaluates offer eligibility and ranking to select the optimal offer. The selected offer informs the next message action -- which offer content to include, which channel to use, or which journey branch to take based on the offer outcome.

This approach enables adaptive journeys where the offer decision influences subsequent journey steps. For example, a journey might select the best offer, deliver it via email, wait for engagement, and then follow up with a push notification if the offer was not opened.

#### Key considerations

- The journey must be designed with a decision node followed by one or more message action nodes
- Offer eligibility is evaluated using the profile's state at the moment the profile reaches the decision node
- Journey wait steps between the decision and delivery can cause the profile's state to change
- Can combine with journey branching to take different paths based on which offer was selected

#### Advantages

- Integrates offer selection into multi-step orchestration flows
- Enables adaptive journeys where the offer choice influences subsequent steps
- Supports cross-channel delivery within the same journey (email, push, SMS)
- Can combine with journey conditions for post-offer engagement tracking

#### Limitations

- More complex to set up than standalone campaign decisioning
- Journey throughput limits apply (5,000 profiles per second entry rate)
- Decision is tied to the journey context -- changes require journey versioning
- Journey must be republished for offer catalog or decision policy updates to take effect

#### Experience League resources

- [Deliver offers in messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Get started with journeys](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)

### Option comparison

The following table compares the three implementation options across key criteria.

| Criteria | Option A: Email decisioning | Option B: Web/app real-time | Option C: Journey decision node |
| --- | --- | --- | --- |
| Best for | Batch email campaigns with per-recipient offer selection | Real-time offer banners on web/app surfaces | Offer selection within multi-step orchestrated journeys |
| Decision latency | At send time (seconds per recipient during batch rendering) | Sub-second (Edge Network) | At journey node execution (seconds) |
| Channel | Email | Web, mobile app, code-based surfaces | Any channel (email, push, SMS) within the journey |
| SDK required | No | Yes (Web SDK or Mobile SDK) | No (for email/push); Yes (if web channel is a journey action) |
| Audience evaluation | Batch or streaming | Edge | Batch, streaming, or edge (depending on journey entry) |
| Profile data scope | Full hub profile | Edge profile (subset) | Full hub profile |
| Complexity | Low | Medium-High | Medium |
| Throughput | High (batch campaign volumes) | High (Edge Network scale) | Medium (journey throughput limits apply) |

### Choose the right option

Use the following guidance to select the best implementation option for your use case.

- **Choose Option A** if the primary use case is selecting the best offer per recipient in outbound email campaigns and no client-side SDK is available. This is the simplest implementation path and works well for promotional emails, newsletters, and lifecycle campaigns.
- **Choose Option B** if offers must be selected in real time at the moment a visitor loads a web page or opens a mobile app. This requires Web SDK or Mobile SDK and an edge-active merge policy but delivers the fastest, most contextual offer selection.
- **Choose Option C** if the offer decision is part of a broader customer journey with multiple steps, waits, and conditional branching. This is the right choice when the selected offer should influence downstream journey actions or when multi-channel follow-up based on offer engagement is needed.
- **Combine options** when offers must be delivered consistently across channels. Use the same decision policy across all three options to ensure a customer sees the same offer in email (Option A), on the website (Option B), and within a journey follow-up (Option C).

## Implementation phases

The following phases outline the end-to-end implementation sequence for offer decisioning.

### Phase 1: Validate foundational prerequisites

**Application function:** AEP: Data Modeling & Preparation, AEP: Identity & Profile Configuration

This phase validates that the foundational data layer supports offer decisioning. Profile schemas must include the attributes used in offer eligibility rules, and identity configuration must enable cross-channel profile resolution.

#### Decision: Profile attributes for eligibility

Determine which profile attributes will be used in offer eligibility rules.

>[!NOTE]
>The choice of profile attributes affects both eligibility rule design and ranking strategy effectiveness. Consider computed attributes and propensity scores to enhance decision quality.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Standard profile attributes (loyalty tier, purchase history) | Attributes already exist in the profile schema | No schema changes needed; verify data freshness |
| Computed attributes (lifetime value, engagement score) | Eligibility or ranking depends on aggregated behavioral data | Requires S1 configuration; adds a dependency on computed attribute refresh cadence |
| Customer AI propensity scores | Ranking should leverage ML-based predictions | Requires sufficient training data (10,000+ profiles with target event); model training time |

#### Key configuration details

- Verify the profile schema includes fields referenced in eligibility rules (e.g., `_tenantId.loyaltyTier`, `_tenantId.subscriptionType`)
- Confirm offer interaction tracking schema exists for impression, click, and conversion events
- For Option B: Verify edge-active merge policy is configured and Web SDK datastream has AJO service enabled

#### Experience League documentation

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Enable a schema for Profile](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Phase 2: Configure audience evaluation

**Application function:** RT-CDP: Audience Evaluation

This phase defines and evaluates the audiences used as offer eligibility criteria. These audiences determine which customer segments qualify for specific offers (e.g., "high-value customers" qualify for premium offers, "trial users" qualify for conversion offers).

#### Decision: Audience evaluation method

Determine how quickly audience membership must update for offer eligibility.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Batch evaluation | Option A (email campaigns) where eligibility is evaluated at send time | Simplest; all segment rule expressions supported; daily or on-demand refresh |
| Streaming evaluation | Option A or C when near-real-time audience updates are needed between batches | Automatic for eligible segments; limited segment rule support (single events, attribute comparisons) |
| Edge evaluation | Option B (web/app real-time) where eligibility must evaluate at page load | Sub-second; required for real-time web/app offers; limited to simple attribute checks and segment membership |

**UI navigation:** Customer > Audiences > Create audience > Build rule

#### Key configuration details

- Define targeting audiences for offer eligibility (e.g., "Loyalty Gold Tier," "High-Value Customers," "Trial Users")
- Define suppression audiences if needed (e.g., "Recently Received Offer X")
- For Option B: Verify that eligibility audiences qualify for edge evaluation -- avoid time-series queries and complex aggregations in segment rule expressions

#### Where options diverge

**For Option A (Email Decisioning):**
Batch or streaming evaluation is sufficient. Audiences are evaluated before or during campaign execution. Complex segment rule expressions including time-based conditions and event aggregations are fully supported.

**For Option B (Web/App Real-Time):**
Edge evaluation is required. Audiences must use simple attribute checks or segment membership conditions. Test edge eligibility by verifying the segment rule expression qualifies for edge segmentation.

**For Option C (Journey Decision Node):**
Any evaluation method works depending on the journey entry criteria. If the journey uses audience-based entry, the audience evaluation method matches the journey's requirements.

#### Experience League documentation

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Phase 3: Set up decisioning

**Application function:** AJO: Decisioning

This is the core phase where the offer catalog, eligibility rules, ranking strategies, and decision policies are built. This phase creates the decision engine configuration that all delivery options (A, B, C) share.

#### Decision: Placement channel and content format

Determine where offers will appear and in what format.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Email (HTML) | Option A -- offer content rendered as HTML within email body | Supports rich formatting; must be compatible with email clients |
| Email (Image URL) | Option A -- offer rendered as a hosted image in email | Simpler; image must be hosted and accessible; no dynamic text |
| Web (HTML) | Option B -- offer rendered as HTML on a web page | Full layout control; supports interactive elements |
| Web/Mobile (JSON) | Option B -- offer data returned as JSON for custom rendering | Maximum flexibility; requires front-end development to render |
| Code-based (JSON) | Option B -- offer data for code-based experience surfaces | Application controls rendering; most flexible |

#### Decision: Ranking strategy

Determine how the best offer should be selected from eligible offers.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Priority-based (manual) | Small offer catalogs; explicit business rules for offer ordering | Simplest to configure; manually assign priority value per offer; deterministic |
| Formula-based (custom expression) | Ranking should consider profile attributes (e.g., loyalty tier, recency) | Flexible; uses profile data to compute a ranking score; requires segment rule expression design |
| AI-ranked (auto-optimization) | Large offer catalogs; want ML to optimize selection over time | Requires minimum 1,000 conversion events for model training; learns from offer performance data |

#### Decision: Offer capping

Determine whether there should be limits on how many times an offer is shown.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Per-profile cap | Prevent the same offer from being shown too many times to one customer | Avoids offer fatigue; counter lag of a few seconds in high-throughput scenarios |
| Global cap | Limit total impressions for an offer across all profiles (e.g., limited inventory) | Controls offer supply; once cap is reached, offer is excluded from decisions |
| No cap | Offers have unlimited availability | Simplest; suitable for always-on promotions |

**UI navigation:** Components > Decision Management > Placements / Rules / Offers / Decisions

#### Key configuration details

1. **Create placements** -- Define where offers appear by specifying the channel type and content format for each placement.
   - UI: Components > Decision Management > Placements
   - Create one placement per channel/format combination (e.g., "Email Hero Banner - HTML," "Web Homepage - JSON," "Mobile App Card - JSON")

2. **Define eligibility rules** -- Create rules using segment rule expressions that reference profile attributes or audience membership.
   - UI: Components > Decision Management > Rules
   - Rules can reference audience membership, profile attributes (loyalty tier, subscription type), date constraints, or contextual data

3. **Create personalized offers** -- Build each offer with content representations for every placement, assign eligibility rules, set priority, and configure optional capping.
   - UI: Components > Decision Management > Offers > Create offer
   - Each offer needs a content representation per placement (e.g., HTML for email, JSON for web)
   - Assign eligibility rules to control which profiles can see each offer
   - Set offer validity dates (start/end) and optional frequency capping
   - Approve each offer to make it eligible for decisioning

4. **Create fallback offers** -- Build a default offer for each placement that is shown when no personalized offer qualifies.
   - UI: Components > Decision Management > Offers > Create fallback offer
   - Fallback must have representations for every placement used in the decision

5. **Create collection qualifiers and collections** -- Organize offers into collections using qualifier tags.
   - UI: Components > Decision Management > Collection qualifiers
   - Group related offers (e.g., "Summer Promotions," "Loyalty Rewards") for use in decision scopes

6. **Create decision policies** -- Bind placements, collections, ranking strategies, and fallback offers into executable decisions.
   - UI: Components > Decision Management > Decisions > Create decision
   - Each decision scope links a placement to a collection and specifies the ranking method

#### Experience League documentation

- [Decision Management overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Create placements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Create decision rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Create personalized offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Create fallback offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Create collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Create collection qualifiers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Create decisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Ranking strategies](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Phase 4: Configure channel and surface

**Application function:** AJO: Channel Configuration

This phase configures the channel surfaces through which offers will be delivered. The configuration depends on which implementation option(s) are being used.

#### Decision: Channel type

Determine which messaging channel the use case requires.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Email | Option A or Option C with email delivery | Requires subdomain delegation, IP pool, sender settings |
| Web | Option B for web surface delivery | Requires Web SDK and datastream configuration |
| In-app | Option B for mobile app delivery | Requires Mobile SDK and push credentials |
| Code-based experience | Option B for custom rendering surfaces | Most flexible; application handles rendering |

#### Where options diverge

**For Option A (Email Decisioning):**
- UI: Administration > Channels > Channel surfaces > Create surface (Email)
- Configure subdomain, IP pool, sender name/email, reply-to, unsubscribe settings
- Verify SPF, DKIM, and DMARC records for the sending subdomain

**For Option B (Web/App Real-Time):**
- UI: Administration > Channels > Channel surfaces > Create surface (Web or In-app)
- For web: Configure the web surface URL pattern
- For code-based experiences: Define the surface URI for the application
- Verify the datastream has AJO service enabled

**For Option C (Journey Decision Node):**
- Configure channel surfaces for each channel used in the journey (email, push, SMS, or web)
- Each journey message action requires a corresponding active channel surface

#### Experience League documentation

- [Get started with email configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Email surface settings](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delegate subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Configure push notification channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Phase 5: Configure content and delivery

**Application function:** AJO: Message Authoring, AJO: Campaign Execution

This phase designs the message templates or experience surfaces that display the selected offer, then configures the delivery mechanism (campaign, journey, or code-based experience).

#### Decision: Content approach for offer rendering

Determine how the offer content should be integrated into the message or experience.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Offer decision component in Email Designer | Option A -- embed offer placement in email template | Drag-and-drop; offer content renders automatically based on decision outcome |
| Code-based experience with decision policy | Option B -- application retrieves and renders offer data | Maximum control over rendering; requires front-end development |
| Journey message action with embedded decision | Option C -- decision node feeds offer content to journey message | Offer selection and delivery are orchestrated within the journey flow |

#### Decision: Campaign type (Option A only)

Determine whether this is a scheduled marketing campaign or an API-triggered campaign.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Scheduled campaign | One-time or recurring batch sends to a defined audience | Audience evaluated at execution time; set date/time or recurrence |
| API-triggered campaign | Event-driven or system-triggered sends to specified profiles | Profiles specified in trigger payload; supports up to 20 recipients per request |

#### Where options diverge

**For Option A (Email Decisioning):**

1. Author the email message using the Email Designer
   - UI: Campaigns > Create Campaign > Select Email > Edit content
   - Insert an offer decision component into the email layout to define the placement zone
   - Add personalization tokens for profile-level content (name, loyalty tier)
   - Configure subject line and preheader with optional personalization
2. Create and configure the campaign
   - UI: Campaigns > Create Campaign > Scheduled or API-triggered
   - Bind the target audience and select the channel surface
   - Set the execution schedule or API trigger configuration
   - Review and activate the campaign

**For Option B (Web/App Real-Time):**

1. Configure the code-based experience or web channel
   - UI: Campaigns > Create Campaign > Code-based experience (or Web)
   - Link the decision policy to the experience surface
   - Define the rendering format (JSON response for code-based; visual editor for web channel)
2. Implement client-side rendering
   - Use the Web SDK `sendEvent` response to retrieve the selected offer
   - Render the offer content in the designated placement on the page
   - Implement impression and click tracking

**For Option C (Journey Decision Node):**

1. Design the journey with a decision node
   - UI: Journeys > Create Journey > Add decision node
   - Configure the decision node to invoke the decision policy from Phase 3
2. Add message action nodes after the decision
   - Configure email, push, or SMS actions that reference the selected offer
   - Add wait steps, conditions, or branching based on offer engagement
3. Publish the journey

#### Experience League documentation

- [Deliver offers in messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Design email content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Create a campaign](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Get started with journeys](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Preview and test your content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Phase 6: Test and validate

**Application function:** AJO: Decisioning, AJO: Message Authoring

This phase validates that the decisioning engine returns the correct offers for test profiles and that the offer content renders properly in each delivery channel.

#### Test decisioning logic

Use test profiles with known attributes to verify that the correct offers are selected based on eligibility and ranking.

- Create test profiles that match different eligibility criteria (e.g., Gold tier, Silver tier, Trial user)
- Verify each test profile receives the expected offer
- Verify that profiles matching no eligibility rules receive the fallback offer

#### Test content rendering

Preview the offer content in each delivery channel.

- For Option A: Use email preview with test profiles to verify offer content renders correctly
- For Option B: Test the Edge Decisioning response in a staging environment
- For Option C: Use journey test mode to verify the decision node selects correctly

#### Validate impression tracking

Confirm that offer impressions, clicks, and conversions are being tracked.

- Verify offer interaction events appear in the tracking datasets
- Confirm attribution between offer impressions and downstream conversions

#### Experience League documentation

- [Preview and test your content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Send email proofs](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)

### Phase 7: Configure reporting and performance monitoring

**Application function:** AJO: Reporting & Performance Analysis

This phase sets up reporting to track offer selection distribution, acceptance rates, conversion impact, and fallback rates. This phase covers both AJO native reports and CJA-based cross-channel analysis.

#### Decision: Reporting method

Determine which reporting tools are needed for offer performance analysis.

| Option | When to choose | Considerations |
| --- | --- | --- |
| AJO native reports only | Operational monitoring of individual campaigns or journeys | Quick access; built-in delivery and engagement metrics; limited cross-entity analysis |
| CJA workspace analysis | Cross-channel offer effectiveness, revenue attribution, funnel analysis | Requires CJA connection and data view; deeper analytical capabilities |
| Both AJO and CJA | Full operational and analytical coverage | Recommended for production implementations; AJO for real-time monitoring, CJA for strategic analysis |

#### Key configuration details

1. **AJO native reporting** -- Monitor campaign or journey performance using built-in reports.
   - UI: Campaigns > Select campaign > All time report (or Live report)
   - Review offer-specific metrics: impressions per offer, click-through rate per offer, fallback rate
   - Monitor delivery funnel: Targeted > Sent > Delivered > Opens > Clicks

2. **CJA analysis (recommended)** -- Build cross-channel offer performance dashboards.
   - Configure a CJA connection including AJO offer interaction datasets
   - Create a data view with offer-specific dimensions (offer name, placement, decision) and metrics (impressions, clicks, conversions)
   - Build workspace analysis for: offer selection distribution, acceptance rate by segment, revenue impact, cross-channel offer consistency

#### Experience League documentation

- [Campaign global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Journey global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Work with Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

## Implementation considerations

This section covers guardrails, common pitfalls, best practices, and trade-off decisions for offer decisioning implementations.

### Guardrails and limits

Be aware of the following platform guardrails and limits when planning your implementation.

- Maximum of 10,000 approved personalized offers per sandbox -- [Decision Management guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum of 30 placements per decision
- Maximum of 30 collection scopes per decision request
- AI ranking models require a minimum of 1,000 conversion events for training
- Offer capping counters may have a lag of up to a few seconds in high-throughput scenarios
- Edge decisions are limited to profile attributes available in the edge profile store
- Maximum of 4,000 segment definitions per sandbox -- [Platform guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Only one merge policy can be active on Edge per sandbox
- Maximum of 500 active live campaigns per sandbox
- Journey entry rate limit: 5,000 profiles per second
- Maximum of 10 channel surfaces per channel type per sandbox

### Common pitfalls

Avoid these frequently encountered issues during implementation.

- **Decision always returns fallback offer:** This typically means personalized offers are not approved, are outside their validity date range, or eligibility rules do not match the test profile's attributes. Verify each condition: approval status, date range, and segment rule expression accuracy. Also check that capping limits have not been reached.
- **Offer not appearing in collection:** Ensure the offer has been tagged with the correct collection qualifier and that the collection filter matches. Offers must be both tagged and approved to appear in collection-based decision scopes.
- **Ranking formula not applied:** Verify that the formula is syntactically valid and references accessible profile attributes. Formula errors silently fall back to priority-based ranking with no visible error.
- **Edge delivery returns empty personalization:** Ensure the datastream is configured with the [!DNL Adobe Journey Optimizer] service enabled and that the decision scope is correctly formatted. Verify the edge-active merge policy exists.
- **Inconsistent offers across channels:** If separate decision policies are used per channel, the same profile may receive different offers. Use a single decision policy across channels for consistency, or accept intentional divergence based on channel-specific placements.
- **Offer content not rendering in email:** Verify the offer has a content representation that matches the email placement format (HTML or image URL). Missing representations result in blank placement zones.

### Best practices

Follow these recommendations for a successful offer decisioning implementation.

- **Start with a small offer catalog and iterate** -- Begin with 5-10 offers and expand as the decisioning framework is validated. This simplifies troubleshooting and ensures eligibility rules work correctly before scaling.
- **Use collection qualifiers strategically** -- Tag offers by category (e.g., "Acquisition," "Retention," "Upsell") to enable flexible collection-based decision scopes that can be reused across campaigns and journeys.
- **Always create meaningful fallback offers** -- Fallback offers are not just a safety net; they are the default experience for profiles that do not match any eligibility rule. Invest in fallback content that provides value even without personalization.
- **Design eligibility rules to be mutually exclusive where possible** -- When multiple offers have overlapping eligibility, the ranking strategy becomes critical. If business requirements dictate a specific offer for a specific segment, make eligibility rules mutually exclusive rather than relying solely on ranking.
- **Test with edge-representative profiles for Option B** -- Edge profiles contain a subset of hub profile attributes. Test with profiles that have edge-available attributes to ensure eligibility evaluates correctly in production.
- **Monitor fallback rates as a health metric** -- A high fallback rate (above 20-30%) indicates that the offer catalog does not cover enough customer segments. Expand the offer catalog or broaden eligibility rules.
- **Version decision policies rather than editing live ones** -- Create a new decision policy version rather than modifying an active one. This prevents disruption to live campaigns and enables A/B comparison of decision strategies.

### Trade-off decisions

Consider the following trade-offs when making architectural and configuration decisions.

#### Eligibility precision vs. offer coverage

Tight eligibility rules ensure each offer reaches only the most relevant profiles, but may result in high fallback rates when profiles do not match any offer. Broad eligibility rules maximize offer coverage but reduce personalization precision.

- **Tight eligibility favors:** Higher acceptance rates, better personalization, lower offer fatigue
- **Broad eligibility favors:** Lower fallback rates, more profiles receive personalized offers, simpler rule management
- **Recommendation:** Start with broader eligibility rules and tighten them based on performance data. Monitor fallback rates and acceptance rates to find the right balance. Use ranking strategies to differentiate among broadly eligible offers.

#### Priority-based vs. AI-ranked ranking

Priority-based ranking gives the business full control over which offers are shown, while AI-ranked ranking optimizes for conversion but reduces human control over offer selection.

- **Priority-based favors:** Business control, predictability, no training data requirement, immediate deployment
- **AI-ranked favors:** Conversion optimization, discovery of unexpected patterns, automatic adaptation to changing customer behavior
- **Recommendation:** Use priority-based ranking for initial launches and regulatory-sensitive offers where business control is paramount. Transition to AI-ranked for high-volume, performance-optimized use cases once sufficient conversion data (1,000+ events) is available.

#### Single decision policy vs. per-channel decision policies

A single decision policy ensures offer consistency across all channels but constrains per-channel optimization. Per-channel policies allow channel-specific ranking and eligibility but risk inconsistent customer experiences.

- **Single policy favors:** Cross-channel consistency, simpler management, unified reporting
- **Per-channel policies favor:** Channel-optimized ranking, channel-specific eligibility (e.g., web-only offers), independent iteration
- **Recommendation:** Start with a single decision policy for cross-channel consistency. Create per-channel policies only when business requirements demand channel-specific offer strategies (e.g., web-exclusive flash sales).

#### Hub decisioning (Option A/C) vs. edge decisioning (Option B)

Hub decisioning has access to the full profile but operates at send time. Edge decisioning operates in real time with sub-second latency but is limited to edge-available profile attributes.

- **Hub decisioning favors:** Access to full profile data, complex eligibility rules, batch campaign volumes
- **Edge decisioning favors:** Real-time context, in-session personalization, sub-second response
- **Recommendation:** Use hub decisioning for outbound channels (email, push) where full profile data improves offer relevance. Use edge decisioning for inbound channels (web, app) where real-time response is critical. Ensure eligibility rules for edge use only edge-available attributes.

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
