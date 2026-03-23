---
title: Known-Visitor Web/App Personalization
description: Learn how to deliver personalized content, offers, or promotions to identified visitors based on real-time profile and segment membership.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 585adc0e-f528-4a09-b931-ef6b45fa8ec8
---
# Known-visitor web/app personalization

This reference plan provides a complete implementation guide for delivering personalized content to identified visitors across digital surfaces using [!DNL Adobe Journey Optimizer] (AJO) and [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP). It is designed for solution architects, marketing technologists, and implementation engineers who need to understand all viable implementation approaches, the decisions that must be made at each phase, and the Experience League documentation that supports configuration.

Known-visitor web/app personalization is the primary personalization pattern for authenticated digital experiences. Unlike anonymous visitor personalization, which relies solely on in-session behavioral signals, this pattern leverages the full unified profile: historical behavioral data, segment membership, loyalty tier, purchase history, lifecycle stage, computed attributes, and propensity scores. It supports personalization across web pages (via AJO web channel), mobile in-app messages, and content cards.

This guide presents all viable implementation options -- segment-based, decisioning-based, and multi-surface -- with trade-offs, decision guidance, and references to [!DNL Adobe Experience League] documentation.

## Use case overview

Organizations with authenticated digital properties -- e-commerce sites, banking portals, subscription services, loyalty programs, mobile apps -- need to deliver personalized experiences that reflect each customer's relationship with the brand. When a visitor logs in or is recognized through identity resolution, the platform can access their full unified profile and deliver content tailored to their specific attributes, behaviors, and preferences.

This pattern addresses the scenario where an identified visitor arrives on a web property or opens a mobile app, and the system must determine the optimal content, offer, or promotion to display based on real-time profile data and audience membership. The personalization decision happens at the edge in milliseconds, enabling sub-second content delivery without perceptible latency.

The pattern supports both deterministic personalization (where specific content maps to specific audience segments) and dynamic decisioning (where AJO Decisioning evaluates eligibility rules and ranking strategies to select the optimal content per profile). It spans multiple digital surfaces -- web pages, mobile in-app messages, and content cards -- enabling consistent personalization across the customer's digital journey.

## Key business objectives

The following business objectives are supported by this use case pattern.

### Deliver personalized customer experiences

Tailor content, offers, and messaging to individual preferences, behaviors, and lifecycle stage. For more information, see [Deliver personalized customer experiences](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md).

**KPIs:** Engagement, Conversion Rates, Customer Satisfaction (CSAT)

### Increase website engagement

Improve time on site, pages per session, and interaction with web content through relevant experiences. For more information, see [Increase website engagement](../../business-objectives/acquisition-growth/increase-website-engagement.md).

**KPIs:** Time On (web) Page, Engagement, Conversion Rates

### Increase mobile app engagement

Drive daily active usage, feature adoption, and in-app conversions through personalized in-app experiences.

**KPIs:** Engagement, Retention, Conversion Rates

## Example tactical use cases

The following are common tactical implementations of this pattern:

- Homepage hero personalization by loyalty tier or lifecycle stage -- display different hero banners based on whether the customer is new, active, at-risk, or VIP
- Product recommendation carousel based on purchase history -- surface relevant product suggestions using past purchase data and product affinity scores
- Personalized promotional banner by customer segment -- show different promotions to high-value, at-risk, and new customer segments
- In-app message for mobile users based on feature adoption -- guide users to underutilized features based on their usage patterns
- Content card with personalized offer on account dashboard -- persistent, dismissible offers tailored to the customer's profile
- Personalized pricing or discount display based on customer tier -- show tier-specific pricing or exclusive discounts to loyalty program members
- Cross-sell recommendation widget based on owned products -- suggest complementary products or services based on current portfolio
- Personalized navigation or content ordering based on interests -- reorder content modules or navigation elements based on demonstrated preferences

## Key performance indicators

The following KPIs help measure the effectiveness of this use case pattern.

| KPI | Measurement approach | Benchmark guidance |
| --- | --- | --- |
| Personalization Engagement Rate | Clicks and interactions with personalized content elements divided by impressions | Personalized content should outperform default content by 20-50% |
| Conversion Rate Lift | Conversion rate for personalized experiences versus control/default experiences | Target 10-30% lift over non-personalized experiences |
| Click-Through Rate (CTR) | Clicks on personalized CTAs, offers, and recommendations divided by impressions | Monitor per surface (web, in-app, content card) and per segment |
| Revenue per Visit | Revenue attributed to sessions with personalized experiences | Compare personalized versus non-personalized visitor cohorts |
| Content Card Interaction Rate | Content card clicks and dismissals relative to impressions | Track per card type and audience segment |
| In-App Message Engagement | In-app message interactions (CTA clicks, dismissals) relative to impressions | Compare across audience segments and message types |
| Time on Page | Average time spent on pages with personalized content versus default | Personalized pages should show increased dwell time |
| Offer Acceptance Rate | Percentage of decisioning-selected offers that result in a conversion event | Track per offer, per placement, and per ranking strategy |

## Use case pattern

This section describes the core pattern and its function chain.

**Known-visitor web/app personalization**

Deliver personalized content, offers, or promotions to an identified visitor based on real-time profile and segment membership across web, mobile in-app, and content card surfaces.

**Function chain:** Audience Evaluation > Personalization Decisioning > Surface/Channel Configuration > Content Delivery > Impression Tracking > Reporting

## Applications

The following applications are used in this use case pattern.

- **[!DNL Adobe Journey Optimizer] (AJO)** -- Web channel configuration, in-app channel configuration, content card channel configuration, decisioning (offer selection and ranking), message authoring (personalized content creation), campaign execution, content experimentation, and reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** -- Audience evaluation (edge, streaming, and batch), real-time profile lookup via Edge Network, profile enrichment with computed attributes and propensity scores
- **[!DNL Adobe Experience Platform] (AEP)** -- Profile store, identity service, Web SDK, Mobile SDK, datastream configuration, edge network delivery

## Foundational functions

The following foundational capabilities must be in place for this use case pattern. For each function, the status indicates whether it is typically required, assumed to be pre-configured, or not applicable.

| Foundational Function | Status | What Must Be in Place | Experience League Reference |
| --- | --- | --- | --- |
| Administration & Governance | Assumed in Place | AJO sandbox with web channel, in-app channel, and decisioning permissions configured. Users provisioned with marketer and content author roles. | [Sandboxes overview](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Access control overview](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Data Modeling & Preparation | Required | Profile schema must include attributes used for personalization and segmentation (e.g., loyalty tier, purchase history, product interests, lifecycle stage). Experience Event schema for web/app interaction tracking and conversion events. Datasets enabled for [!DNL Real-Time Customer Profile]. | [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Data Sources & Collection | Required | Web SDK implemented on web properties for experience delivery and impression tracking. Mobile SDK implemented on mobile apps for in-app and content card delivery. Datastream configured with AJO service enabled for edge personalization. Real-time profile data available at the edge for sub-second personalization. | [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Mobile SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview), [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Identity & Profile Configuration | Required | Known identity namespaces (CRM ID, email, authenticated user ID) configured. Identity stitching between anonymous and authenticated sessions operational for seamless transition from anonymous to known-visitor personalization. Edge merge policy configured with `isActiveOnEdge: true` to resolve the authenticated profile at the edge. | [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Audience Definition & Segmentation | Required | Audiences defined using profile attributes, behavioral data, and computed attributes. Edge or streaming evaluation enabled for real-time personalization qualification. Audiences used for segment-based personalization must qualify for edge evaluation. | [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation) |

## Supporting functions

The following capabilities augment this use case pattern but are not required for core execution.

| Supporting Function | Status | Why It Matters | Experience League Reference |
| --- | --- | --- | --- |
| Computed / Derived Attribute Creation | Recommended | Computed attributes (e.g., [!DNL Customer AI] propensity scores, lifetime value, engagement score, product affinity, days since last purchase) significantly improve personalization quality by providing richer signals for audience definition and content selection. | [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview), [Customer AI overview](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Data Lifecycle Management | Recommended | Profile and event data retention policies ensure fresh, relevant data powers personalization decisions. Consent enforcement ensures personalization respects user preferences. | [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Consent in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted) |
| Data Usage Labeling & Enforcement | Recommended | Governance labels on profile attributes used for personalization (especially PII-adjacent attributes like purchase history, location, financial data) ensure compliance with data usage policies. | [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) |
| Monitoring & Observability | Recommended | Edge delivery and personalization performance monitoring helps detect latency issues, delivery failures, or data freshness problems that degrade the personalized experience. | [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home), [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| Reporting & Analysis | Included | Personalization performance reporting is part of Function Chain Step 6. [!DNL Customer Journey Analytics] analysis enables deep investigation of personalization impact on conversion, engagement, and revenue across visitor segments. | [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Application functions

This plan exercises the following functions from the Application Function Catalog. Functions are mapped to implementation phases rather than numbered steps.

### [!DNL Journey Optimizer] (AJO)

| Function | Implementation Phase | Description |
| --- | --- | --- |
| Channel Configuration | Surface & Channel Configuration | Configure web, in-app, and content card channel surfaces for personalization delivery |
| Message Authoring | Content Authoring | Author personalized content variants with dynamic content, personalization expressions, and conditional blocks for each surface |
| Campaign Execution | Campaign Setup & Activation | Create and activate web campaigns (scheduled or API-triggered) that bind audiences, surfaces, and content |
| Decisioning | Decisioning Setup (Option B/C) | Configure decision policies with eligibility rules, ranking strategies, and offer/content items for dynamic personalization |
| Content Experimentation | Optimization (optional) | Run A/B tests on personalized content variants to optimize performance |
| Frequency & Business Rules | Campaign Setup & Activation | Enforce impression frequency caps to prevent over-personalization fatigue |
| Reporting & Performance Analysis | Reporting & Optimization | Monitor personalization delivery, engagement, and conversion metrics per surface and segment |

### [!DNL Real-Time CDP] (RT-CDP)

| Function | Implementation Phase | Description |
| --- | --- | --- |
| Audience Evaluation | Audience Definition & Evaluation | Define and evaluate audiences using profile attributes, behavioral data, and computed attributes with edge or streaming evaluation |
| Real-Time Profile Lookup | Content Delivery (runtime) | Access real-time profile attributes and segment memberships via Edge Network for sub-second personalization decisions |
| Profile Enrichment | Pre-implementation (supporting) | Enrich profiles with computed attributes, [!DNL Customer AI] scores, and aggregated behavioral signals that improve personalization quality |

## Prerequisites

Before implementing this use case pattern, ensure the following are in place:

- [ ] Web SDK implemented on target web properties with `alloy("sendEvent")` configured for page views and interaction tracking
- [ ] Mobile SDK implemented on target mobile apps (if in-app or content card surfaces are used)
- [ ] Datastream configured with [!DNL Adobe Journey Optimizer] service enabled
- [ ] Profile schema includes attributes used for personalization (loyalty tier, purchase history, product interests, lifecycle stage)
- [ ] Experience Event schema configured for impression and conversion tracking
- [ ] Known identity namespaces created and identity stitching operational between anonymous (ECID) and authenticated identities
- [ ] Edge merge policy configured with `isActiveOnEdge: true`
- [ ] Audiences defined with edge-eligible evaluation for real-time personalization
- [ ] Content assets (images, copy, CTAs) prepared for each personalization variant
- [ ] Personalization strategy documented: which attributes drive which content, for which surfaces

## Implementation options

This section describes the available implementation approaches for this use case pattern.

### Option A: Segment-based web personalization

**Best for:** Deterministic personalization where specific content variants map directly to audience segments -- loyalty tier-specific hero banners, lifecycle stage messaging, customer segment promotional content. Ideal when the content-to-segment mapping is well-defined and does not require dynamic ranking or optimization.

**How it works:**

Segment-based personalization maps content variants directly to audience segments. When a known visitor's profile is evaluated against edge-eligible audiences at page load, the system determines which segments the visitor belongs to and displays the corresponding content variant. Selection is based on segment membership priority -- if a visitor qualifies for multiple segments, the highest-priority segment's content is displayed.

This approach uses AJO web channel campaigns (or in-app/content card campaigns) with conditional content rules or multiple treatment targeting configurations. Each audience segment is associated with a specific content experience. No decisioning engine is involved -- the content selection logic is entirely segment-driven.

Content is authored using the AJO message authoring interface with dynamic content blocks that render different content based on audience membership or profile attributes. The Web SDK or Mobile SDK delivers the personalized experience in real time via the Edge Network.

**Key considerations:**

- Content variants must be pre-authored for each segment
- Segment definitions must be edge-eligible for real-time qualification
- Adding new segments or content variants requires updating the campaign configuration
- Content selection is deterministic -- the same segment always sees the same content

**Advantages:**

- Simple to implement and maintain with clear content-to-segment mapping
- Easy to understand and explain the personalization logic to stakeholders
- No decisioning overhead -- faster content resolution
- Full control over which content each segment receives

**Limitations:**

- Limited flexibility when the number of segments and content variants grows
- Cannot dynamically optimize content selection based on profile-level signals beyond segment membership
- Adding new content variants requires manual campaign updates
- Does not support next-best-offer scenarios where multiple offers compete for the same placement

**Experience League:**

- [Get started with web channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Create web experiences](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### Option B: Decisioning-based personalization

**Best for:** Dynamic personalization where the optimal content or offer must be selected per profile using eligibility rules and ranking strategies -- next-best-offer on homepage, personalized product recommendations, dynamic promotional banner selection. Ideal when multiple offers or content items compete for the same placement and the system must choose the best one.

**How it works:**

Decisioning-based personalization uses AJO Decisioning to evaluate each visitor's profile against a catalog of content items or offers, applying eligibility rules to determine which items qualify, and then applying a ranking strategy (priority-based, formula-based, or AI-ranked) to select the optimal item for each placement.

The implementation involves creating placements (where content appears), defining offers with eligibility rules and content representations, organizing offers into collections, and creating decision policies that bind placements to collections with ranking strategies. At runtime, when a visitor loads a page, the Edge Network evaluates the decision policy against the visitor's profile and returns the selected offer content.

This approach supports sophisticated personalization scenarios including next-best-offer, personalized promotions with capping, and AI-optimized content selection. Offers can have per-profile and global capping limits, validity date ranges, and complex eligibility criteria combining profile attributes and audience membership.

**Key considerations:**

- Requires more upfront configuration (placements, offers, eligibility rules, collections, decisions)
- Ranking strategies can be priority-based (manual), formula-based (custom expression), or AI-ranked (auto-optimization)
- AI ranking requires a minimum of 1,000 conversion events for model training
- Offer capping counters may have a slight lag under high-throughput scenarios
- A fallback offer must be configured for cases where no personalized offer qualifies

**Advantages:**

- Dynamic, per-profile content selection without hardcoded segment-to-content mapping
- Supports complex eligibility criteria and ranking logic
- AI-ranked option enables automatic optimization without manual intervention
- Offer capping prevents over-exposure of specific content
- Centralized offer management -- offers can be reused across campaigns and channels

**Limitations:**

- Higher implementation complexity than segment-based personalization
- AI ranking requires sufficient conversion event volume for training
- Decisioning evaluation adds marginal latency compared to direct segment-based content delivery
- Formula-based ranking requires careful design to avoid unintended prioritization

**Experience League:**

- [Decision Management overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Create personalized offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Create decisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Ranking strategies](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

**How this differs from Offer decisioning Option B:**

The infrastructure is identical — both use AJO Decisioning at the edge with Web SDK and an edge-active merge policy. The difference is what is being selected. This option manages content items where the selection criterion is personalization fit (segment membership, behavioral ranking). [Offer decisioning](offer-decisioning.md) Option B manages a governed offer catalog where eligibility rules, capping limits, and validity windows are business requirements. If your item set requires per-profile impression capping, regulatory eligibility constraints, or offer lifecycle management, use Offer decisioning Option B instead.

### Option C: Multi-surface personalization (web + in-app + content card)

**Best for:** Consistent personalization across multiple digital surfaces -- delivering coordinated personalized experiences on web pages, mobile in-app messages, and content cards. Ideal when the organization has both web and mobile app properties and wants unified personalization logic across all digital touchpoints.

**How it works:**

Multi-surface personalization extends either Option A (segment-based) or Option B (decisioning-based) to deliver personalized content across multiple AJO surface types. Each surface type -- web, in-app, content card -- may have different content formats and delivery mechanisms, but the underlying personalization logic (audience membership or decisioning) is shared.

The implementation involves configuring channel surfaces for each surface type, authoring surface-specific content (web HTML/CSS for web surfaces, structured messages for in-app, card layouts for content cards), and creating campaigns that target the appropriate surface. The Web SDK handles web surface delivery, while the Mobile SDK handles in-app and content card delivery.

Content cards are particularly valuable for persistent, dismissible personalized messages on account dashboards or app home screens. In-app messages are ideal for contextual, session-specific communications. Web personalization handles hero banners, recommendation widgets, and promotional content.

**Key considerations:**

- Each surface type requires its own channel surface configuration and content authoring
- Web SDK and Mobile SDK must both be implemented and configured
- Content must be designed for each surface format (different dimensions, layouts, interaction patterns)
- Shared audiences and decisioning logic ensure consistency across surfaces
- Testing must cover all surface types across devices

**Advantages:**

- Consistent personalization experience across all digital touchpoints
- Shared audience and decisioning logic reduces duplication
- Content cards provide a persistent, non-intrusive personalization surface
- In-app messages enable contextual, session-specific personalization on mobile

**Limitations:**

- Highest implementation complexity -- requires configuration for each surface type
- Requires both Web SDK and Mobile SDK implementation
- Content must be designed and maintained for each surface format
- Testing scope increases with each additional surface type

**Experience League:**

- [In-app channel overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [Content card channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Get started with web channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)

### Option comparison

The following table compares the three implementation options.

| Criteria | Option A: Segment-Based | Option B: Decisioning-Based | Option C: Multi-Surface |
| --- | --- | --- | --- |
| Best for | Known segment-to-content mapping | Dynamic per-profile content selection | Consistent personalization across web + mobile |
| Complexity | Low | Medium-High | High (builds on A or B) |
| Latency | Fastest (direct segment resolution) | Slightly higher (decisioning evaluation) | Depends on underlying option (A or B) |
| Flexibility | Limited to predefined segment-content pairs | High -- dynamic ranking and eligibility | Highest -- multi-surface with shared logic |
| Content Management | Manual segment-to-content mapping | Centralized offer library with eligibility rules | Per-surface content with shared personalization logic |
| Optimization | Manual A/B testing | AI-ranked auto-optimization available | Per-surface optimization |
| Requires | Edge-eligible audiences, Web SDK | Placements, offers, eligibility rules, decisions | Web SDK + Mobile SDK, multiple surface configurations |
| Surfaces Supported | Web (primary) | Web (primary) | Web + In-App + Content Card |

### Choose the right option

Start with these questions to select the right implementation approach:

1. **How many surfaces?** If you need personalization on both web and mobile app, choose Option C (which builds on either A or B for the underlying logic). If web-only, choose between A and B.

2. **How dynamic is your content selection?** If you have a well-defined mapping of segments to content variants (e.g., 3-5 loyalty tiers, each with a specific hero banner), choose Option A. If you need to select from a catalog of offers with complex eligibility and ranking, choose Option B.

3. **Do you need AI-optimized selection?** If you want the system to automatically learn and optimize which content performs best for each profile, choose Option B with AI-ranked decisioning.

4. **How many content variants?** If you have fewer than 10 content variants with clear segment mappings, Option A is simpler. If you have dozens of offers that need eligibility filtering and ranking, Option B scales better.

5. **Do you plan to extend to other channels?** If your decisioning logic should eventually serve offers across email, web, and other channels, Option B provides the centralized decisioning foundation that cross-channel offer decisioning extends.

## Implementation phases

This section walks through each phase of the implementation in detail.

### Phase 1: Define audiences and configure evaluation

**Application function:** RT-CDP: Audience Evaluation

**What you will configure:** Define the audiences that drive personalization content selection. These audiences represent the visitor segments that will receive personalized experiences -- loyalty tiers, lifecycle stages, behavioral cohorts, or product affinity groups.

**Decision points in this phase:**

>[!NOTE]
>**Decision: Audience evaluation method**
>
>How quickly must audience membership be resolved for personalization? This directly impacts whether personalization can happen at page load or requires a delay.
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Edge evaluation | Real-time web/app personalization requiring sub-second qualification | Limited to simple profile attribute checks and segment membership. No time-series queries or complex aggregations. Required for known-visitor personalization. |
>| Streaming evaluation | Near real-time qualification when profiles enter/exit audiences based on behavioral events | Supports single event and limited time window queries. Audience changes reflected within minutes. Suitable for in-app and content card surfaces where slight delay is acceptable. |
>| Batch evaluation | Daily audience refreshes for segments based on complex aggregations or historical patterns | Full segment rule function support. Not suitable for real-time personalization but can complement edge audiences with complex pre-computed segments. |

>[!NOTE]
>**Decision: Personalization attributes**
>
>Which profile attributes should drive audience definition and content selection?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Profile attributes (loyalty tier, lifecycle stage) | Deterministic personalization based on known customer properties | Stable, well-defined attributes. Easy to map to content variants. Available at the edge if the profile is properly configured. |
>| Behavioral signals (purchase history, browsing patterns) | Personalization based on recent behaviors and engagement patterns | Requires computed attributes or streaming segments. More dynamic but more complex to maintain. |
>| Propensity scores ([!DNL Customer AI]) | Predictive personalization based on likelihood to convert, churn, or purchase | Requires computed attributes. Enables sophisticated personalization but requires ML model training data. |
>| Combined approach | Most production implementations | Uses profile attributes for primary segmentation with behavioral signals and propensity scores for refinement. |

**UI navigation:** Customer > Audiences > Create audience > Build rule

**Key configuration details:**

- Define audiences using Segment Builder with segment rule expressions referencing profile attributes
- Ensure segment rule expressions qualify for edge evaluation (simple attribute checks, segment membership)
- Configure edge-eligible audiences for real-time personalization use cases
- Consider suppression audiences to exclude recently converted or opted-out visitors

**Experience League documentation:**

- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language reference](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Phase 2: Set up decisioning (Option B and C only)

**Application function:** AJO: Decisioning

**What you will configure:** Set up the decisioning infrastructure that dynamically selects the optimal content or offer for each visitor. This includes placements (where offers appear), offers (what content is available), eligibility rules (who qualifies), ranking strategies (how to choose the best), and decision policies (how everything connects).

**Decision points in this phase:**

>[!NOTE]
>**Decision: Ranking strategy**
>
>How should eligible offers be ranked to select the best one for each visitor?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Priority-based (manual) | Simple use cases with clear offer hierarchy | Each offer has a manual priority value. Highest priority eligible offer wins. Easy to understand and control. |
>| Formula-based (custom expression) | When ranking should consider profile attributes | Custom ranking formulas reference profile data (e.g., score by loyalty tier + recency). Flexible but requires formula design and testing. |
>| AI-ranked (auto-optimization) | When you want the system to automatically optimize offer selection | ML model learns which offers perform best for which profiles. Requires minimum 1,000 conversion events for training. Best for high-traffic placements. |

>[!NOTE]
>**Decision: Offer capping**
>
>Should there be limits on how many times an offer is shown to a visitor or across all visitors?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Per-profile cap | Prevent fatigue from seeing the same offer repeatedly | Limits impressions per visitor over a time period. Ensures variety in the personalized experience. |
>| Global cap | Limit total impressions for a promotion or limited-availability offer | Caps total impressions across all visitors. Useful for limited-quantity promotions. |
>| No cap | Evergreen content or always-relevant offers | No impression limits. Suitable for persistent content like loyalty tier banners. |

**UI navigation:** [!DNL Journey Optimizer] > Components > Decision Management

**Key configuration details:**

- Create placements for each surface where offers will appear (web banner, in-app message area, content card slot)
- Define eligibility rules using segment rule expressions referencing profile attributes and audience membership
- Create personalized offers with content representations for each placement
- Create a fallback offer that covers all placements (displayed when no personalized offer qualifies)
- Organize offers with collection qualifiers (tags) and group into collections
- Create a decision policy binding placements to collections with the selected ranking strategy

**Experience League documentation:**

- [Create placements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Create decision rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Create personalized offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Create fallback offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Create collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Create decisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Ranking strategies](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Phase 3: Configure surfaces and channels

**Application function:** AJO: Channel Configuration

**What you will configure:** Configure the channel surfaces that define where personalized content will be delivered. Each surface type (web, in-app, content card) requires its own configuration specifying the surface URI, content format, and delivery parameters.

**Decision points in this phase:**

>[!NOTE]
>**Decision: Target surfaces**
>
>Which digital surfaces will receive personalized content?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Web channel only | Personalization focused on web properties | Requires Web SDK. Simplest implementation. Covers hero banners, promotional areas, recommendation widgets. |
>| In-app channel only | Personalization focused on mobile app experiences | Requires Mobile SDK. Covers contextual, session-specific messages within the app. |
>| Content card channel only | Persistent, dismissible personalized messages | Requires Mobile SDK or Web SDK. Cards persist until dismissed. Ideal for dashboards and home screens. |
>| Multiple surfaces (Option C) | Consistent personalization across web and mobile | Requires both Web SDK and Mobile SDK. Each surface needs separate configuration and content. |

>[!NOTE]
>**Decision: Web surface configuration approach**
>
>How should the web surface be configured for content delivery?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Single-page application (SPA) | Modern web apps with client-side routing | Use `renderDecisions: true` in Web SDK `sendEvent` calls. Content rendered automatically by the SDK. |
>| Multi-page application (MPA) | Traditional server-rendered web pages | Content delivered on page load via Edge Network response. May require page-level surface URI configuration. |

**UI navigation:** [!DNL Journey Optimizer] > Administration > Channels > Channel surfaces

**Key configuration details:**

- For web surfaces: configure the web surface URI matching the target page(s)
- For in-app surfaces: configure the mobile app surface with app ID and surface type
- For content card surfaces: configure the content card surface with app ID or web context
- Ensure the datastream has AJO service enabled for edge personalization delivery

**Experience League documentation:**

- [Get started with web channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Web channel configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)
- [In-app channel prerequisites](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [Content card configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)

### Phase 4: Author content

**Application function:** AJO: Message Authoring

**What you will configure:** Author the personalized content variants for each surface and segment or offer. This includes designing the visual layout, adding personalization expressions that reference profile attributes, configuring conditional content blocks, and creating reusable content fragments.

**Decision points in this phase:**

>[!NOTE]
>**Decision: Content approach**
>
>How should personalized content be structured for this use case?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Conditional content blocks | Different content sections within the same layout vary by audience | Single content asset with conditional rules. Efficient for minor variations (headline, CTA text, image swap). |
>| Separate content variants per treatment | Fundamentally different layouts or designs per audience | Multiple complete content assets. More flexible but more to maintain. Required for content experimentation. |
>| Decisioning-driven content | Content selected dynamically from an offer catalog | Offer representations define the content. Content management is centralized in the offer library. |

>[!NOTE]
>**Decision: Personalization depth**
>
>How much of the content should be personalized?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Surface-level personalization | Only specific elements are personalized (hero image, CTA, offer banner) | Lower complexity. Focused personalization on high-impact areas. Most common starting point. |
>| Full-page personalization | The entire page layout or content ordering is personalized | Higher complexity. Requires extensive content creation. Delivers the most tailored experience. |
>| Token-level personalization | Inline personalization tokens (name, tier, points balance) | Simplest form. Inserts profile attribute values into otherwise static content. |

**UI navigation:** [!DNL Journey Optimizer] > Campaigns > Create Campaign > Edit content

**Where options diverge:**

**For Option A (segment-based):**

- Author content variants for each audience segment using the web designer or code editor
- Use dynamic content blocks with conditions based on audience membership
- Configure personalization expressions referencing profile attributes (e.g., `{{profile.person.name.firstName}}`, `{{profile.loyalty.tier}}`)
- Set up conditional rules to display different content based on segment membership

**For Option B (decisioning-based):**

- Author offer content representations for each placement defined in Phase 2
- Each offer has one or more representations (HTML, image, JSON) matched to placements
- Integrate decisioning output into the web page or app by embedding decision placements
- The content is selected dynamically at runtime -- authoring focuses on individual offer items

**For Option C (multi-surface):**

- Author surface-specific content for each target surface (web HTML/CSS, in-app structured message, content card layout)
- Maintain consistent personalization logic across surfaces while adapting to each surface's format constraints
- Test content rendering on each surface type

**Experience League documentation:**

- [Create web experiences](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Helper functions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Deliver offers in messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Create in-app messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [Create content cards](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/create-content-card)

### Phase 5: Set up and activate campaigns

**Application function:** AJO: Campaign Execution

**What you will configure:** Create and activate the AJO campaign that binds the audience, surface, and content together for delivery. For web personalization, campaigns are typically configured for immediate or ongoing activation rather than one-time scheduled sends.

**Decision points in this phase:**

>[!NOTE]
>**Decision: Campaign type**
>
>How should the personalization campaign be triggered?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Scheduled campaign (always-on) | Ongoing personalization that runs continuously for all qualifying visitors | Set start date to immediate and no end date. Campaign remains active until manually stopped. Most common for web personalization. |
>| Scheduled campaign (time-bound) | Personalization tied to a specific promotion period | Set start and end dates. Campaign automatically stops after the end date. Suitable for seasonal promotions or limited-time offers. |
>| API-triggered campaign | Personalization triggered by a specific application event | Triggered programmatically. Useful when personalization should only appear in response to specific system events. |

>[!NOTE]
>**Decision: Frequency capping**
>
>Should impression frequency be limited for this personalization?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Apply frequency rules | Promotional or offer-based personalization that could fatigue visitors | Prevents the same personalization from appearing too many times. Configured via AJO business rules. |
>| No frequency cap | Evergreen content personalization (loyalty tier banner, dashboard content) | Always-relevant content that does not cause fatigue. No impression limits needed. |

**UI navigation:** [!DNL Journey Optimizer] > Campaigns > Create Campaign

**Key configuration details:**

- Select the web, in-app, or content card channel and the surface configured in Phase 3
- Bind the target audience defined in Phase 1
- Link the content authored in Phase 4
- Configure the campaign schedule (immediate, date range, or API-triggered)
- Review and activate the campaign
- For content experimentation: enable the experiment toggle, define treatments, set traffic allocation and success metrics before activation

**Experience League documentation:**

- [Create a campaign](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Get started with campaigns](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Frequency rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Get started with content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Create a content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### Phase 6: Track impressions and collect data

**Application function:** AEP: Data Sources & Collection

**What you will configure:** Ensure that impressions, interactions, and conversions from personalized experiences are tracked back to the platform for reporting, audience re-evaluation, and decisioning optimization.

**Key configuration details:**

- Verify Web SDK is sending `decisioning.propositionDisplay` events when personalized content is rendered
- Verify Web SDK is sending `decisioning.propositionInteract` events when visitors interact with personalized content (clicks, dismissals)
- For Mobile SDK: verify in-app message and content card interaction events are captured
- Configure conversion event tracking for downstream success metrics (purchases, sign-ups, feature adoption)
- Ensure events include the proposition ID for attribution to specific personalization decisions

**Experience League documentation:**

- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Track events with Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/commands/sendevent/overview)
- [Mobile SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)

### Phase 7: Report and optimize

**Application function:** AJO: Reporting & Performance Analysis, Reporting & Analysis

**What you will configure:** Set up performance monitoring and analysis to measure personalization effectiveness across surfaces, segments, and content variants. Use AJO native reports for operational metrics and [!DNL Customer Journey Analytics] for cross-channel business impact analysis.

**Decision points in this phase:**

>[!NOTE]
>**Decision: Reporting scope**
>
>What level of analysis is needed for this personalization use case?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| AJO native reports only | Operational monitoring of delivery and engagement metrics | Built-in campaign reports with impression, click, and conversion data. Quickest to set up. |
>| CJA cross-channel analysis | Deep analysis of personalization impact on business outcomes | Requires CJA connection and data view. Enables funnel analysis, cohort comparisons, and attribution modeling across channels. |
>| Both AJO + CJA | Complete operational and analytical visibility | Use AJO for day-to-day monitoring and CJA for strategic analysis. Recommended for production implementations. |

**UI navigation:**

- AJO reports: Campaigns > Select campaign > View report
- CJA: Projects > Create new project

**Key configuration details:**

- Access campaign live reports during active personalization delivery
- Review historical reports for completed campaigns or periodic analysis
- For CJA: configure a connection including AJO experience event datasets and create a data view with personalization metrics
- Build dashboards tracking personalization engagement rate, conversion lift, offer acceptance rate, and revenue per visit
- For decisioning-based personalization (Option B): monitor offer performance by placement and ranking strategy effectiveness

**Experience League documentation:**

- [Campaign live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Campaign global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Content experiment report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Implementation considerations

This section covers guardrails, common pitfalls, best practices, and trade-off decisions relevant to this use case pattern.

### Guardrails and limits

- Edge Network lookups have a response time SLA of less than 200ms for edge-evaluated segments -- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximum of 4,000 segment definitions per sandbox -- [Segmentation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Edge segments are limited to simple attribute checks and segment membership queries -- no time-series queries -- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- Only one merge policy can be active on Edge per sandbox -- [Merge policies](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- Maximum of 10,000 approved personalized offers per sandbox -- [Decision Management guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum of 30 placements per decision -- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- AI ranking models require a minimum of 1,000 conversion events for training
- Offer Delivery response time SLA is less than 500ms at P95 for single-scope requests
- Maximum of 500 active live campaigns per sandbox -- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum of 25 active computed attributes per sandbox -- [Computed attributes guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)

### Common pitfalls

- **Edge merge policy not configured:** Without an edge-active merge policy, the Edge Network cannot resolve the authenticated profile, causing personalization to fail or fall back to anonymous behavior. Ensure exactly one merge policy has `isActiveOnEdge: true` in the sandbox.
- **Audience not edge-eligible:** If audience segment rule expressions use time-series queries, complex aggregations, or `inSegment()` references to batch-only segments, they will not qualify for edge evaluation and cannot power real-time personalization. Validate edge eligibility during audience definition.
- **Identity stitching gap during authentication:** When a visitor transitions from anonymous to authenticated, there may be a brief moment where the profile has not yet resolved. Ensure identity stitching is properly configured and that the Web SDK sends the authenticated identity via `identityMap` immediately upon login.
- **Missing fallback offer in decisioning:** If no fallback offer is configured and no personalized offer qualifies for a visitor, the decision returns empty content, creating a broken experience. Always configure a fallback offer that covers all placements.
- **Web SDK not sending proposition display events:** If `renderDecisions` is set to `true` but display events are not being sent, reporting will not reflect actual impressions. Verify event tracking by inspecting network requests in browser developer tools.
- **Content flicker on page load:** If personalized content is not pre-hidden during the decisioning call, visitors may see default content briefly before it is replaced. Use the pre-hiding snippet or CSS-based pre-hiding to eliminate flicker.

### Best practices

- Start with segment-based personalization (Option A) for initial implementation, then evolve to decisioning-based (Option B) as the offer catalog grows and optimization needs increase
- Use edge-evaluated audiences whenever possible for real-time personalization; reserve streaming and batch audiences for complementary use cases
- Implement content experimentation on personalized experiences to validate that personalization drives measurable lift over default content
- Design personalization with a graceful degradation strategy -- if the profile cannot be resolved at the edge, display well-designed default content rather than a broken experience
- Use computed attributes to create high-value personalization signals like engagement score, product affinity, and days since last purchase, which improve both segment-based and decisioning-based personalization quality
- Maintain a content governance process to ensure personalized content stays current, on-brand, and compliant across all surfaces
- Monitor personalization performance by segment to identify which audiences benefit most from personalization and where the lift is strongest

### Trade-off decisions

>[!NOTE]
>**Trade-off: Personalization granularity vs. content management complexity**
>
>More granular personalization (more segments, more content variants, more surfaces) delivers increasingly tailored experiences but requires proportionally more content creation, maintenance, and governance effort.
>
>- **Higher granularity favors:** Better customer experience, higher engagement, stronger conversion lift
>- **Lower granularity favors:** Faster implementation, lower content maintenance burden, simpler governance
>- **Recommendation:** Start with 3-5 high-impact segments (e.g., loyalty tiers or lifecycle stages) with clear content differentiation. Expand granularity based on measured performance lift. Use decisioning (Option B) to scale granularity without proportional content management growth.

>[!NOTE]
>**Trade-off: Real-time decisioning vs. deterministic content control**
>
>Decisioning-based personalization (Option B) provides dynamic optimization but reduces direct control over which content each visitor sees. Segment-based personalization (Option A) provides full deterministic control but limits dynamic optimization.
>
>- **Decisioning favors:** Scalability, automatic optimization, complex eligibility scenarios
>- **Segment-based favors:** Predictability, compliance control, stakeholder transparency
>- **Recommendation:** Use segment-based personalization for compliance-sensitive content (regulatory messaging, tier-specific pricing) where exact control is required. Use decisioning for promotional content, offers, and recommendations where dynamic optimization adds value.

>[!NOTE]
>**Trade-off: Edge data availability vs. personalization richness**
>
>Edge-evaluated personalization is limited to attributes available in the edge profile store. Richer personalization signals (full behavioral history, complex computed attributes) may require server-side lookup or pre-computation.
>
>- **Edge-only favors:** Sub-second latency, simplest architecture
>- **Pre-computed enrichment favors:** Richer personalization signals, more sophisticated audience definitions
>- **Recommendation:** Use computed attributes to pre-aggregate rich behavioral signals into edge-available profile attributes. This provides the richness of behavioral data with the speed of edge evaluation.

## Related documentation

The following resources provide additional detail on the technologies and configurations referenced in this guide.

### Web channel personalization

- [Get started with web channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Create web experiences](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Web channel configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)

### In-app and content card channels

- [In-app channel overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [In-app channel prerequisites](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [Create in-app messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [Content card channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Content card configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)
- [Create content cards](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/create-content-card)

### Decision management

- [Decision Management overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Create placements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Create decision rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Create personalized offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Create fallback offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Create collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Create decisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Ranking strategies](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Deliver offers in messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Personalization and content

- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Helper functions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Work with content templates](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Work with content fragments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

### Audiences and segmentation

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language reference](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Identity and profile

- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Identity namespaces overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Identity graph linking rules](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Profile overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Data collection and SDK

- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Install Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Mobile SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Edge Network Server API overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### Campaigns and experimentation

- [Get started with campaigns](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Create a campaign](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Get started with content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Create a content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Content experiment report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### Computed attributes and enrichment

- [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Computed attributes UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Customer AI overview](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Reporting and analytics

- [Campaign live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Campaign global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Governance and privacy

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Consent in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### Guardrails

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identity Service guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
