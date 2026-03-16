---
title: Behavioral Recommendation
description: "Learn how to generate item and content recommendations using selection strategies and ranking models."
solution: Journey Optimizer, Real-Time Customer Data Platform
---

# Behavioral recommendation

This guide covers how to implement behavioral product and content recommendations using [!DNL Adobe Journey Optimizer] (AJO) Decisioning, [!DNL Real-Time Customer Data Platform] (RT-CDP), and [!DNL Adobe Experience Platform] (AEP). It is designed for solution architects, marketing technologists, and implementation engineers who need to deliver personalized recommendation experiences across web, mobile app, and email channels.

It presents all viable implementation options, decision considerations at each phase, and links to [!DNL Adobe Experience League] documentation. Behavioral Recommendation generates item-level or content-level recommendations using behavioral signals -- product views, purchases, content interactions, search queries -- combined with AJO Decisioning selection strategies and ranking models. Unlike offer decisioning, which selects from a curated set of marketing offers using explicit eligibility rules, this pattern operates on large item catalogs (products, articles, videos) and uses behavioral affinity signals and ML-based ranking to surface the most relevant items for each visitor.

## Use case overview

Organizations with product catalogs, content libraries, or media libraries need to surface the most relevant items to each visitor based on their behavioral history and in-session activity. Whether it is a "recommended for you" carousel on a homepage, a cross-sell widget on a product detail page, or product recommendations embedded in an email campaign, the underlying challenge is the same: match each visitor's behavioral profile to the most relevant items from a catalog, then deliver those recommendations in the right channel at the right moment.

This pattern addresses that challenge by ingesting behavioral signals in real time via [!DNL Web SDK] or [!DNL Mobile SDK], processing them through AJO Decisioning selection strategies that combine item attributes with behavioral context, and delivering the recommended items through web, in-app, or email channels. Ranking models can be formula-based (e.g., sort by category affinity score) or AI-ranked (e.g., personalized recommendation model). The pattern also handles cold-start scenarios for new visitors with no behavioral history by configuring fallback recommendations.

The target audience for this pattern includes ecommerce merchandising teams, content personalization teams, and digital experience teams seeking to improve engagement, conversion, and average order value through personalized recommendations driven by real user behavior.

## Key business objectives

The following business objectives are supported by this use case pattern.

### [Drive cross-sell and upsell revenue](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)

Promote complementary and premium products or services to existing customers based on behavior and purchase history.

| KPI | Description |
| --- | --- |
| Upsell/Cross-Sell % | Percentage of customers who purchase recommended complementary or premium items |
| Incremental Revenue | Additional revenue attributable to recommendation-driven purchases |
| Customer Lifetime Value | Long-term value increase from deeper product engagement |

### [Increase conversion rates](../../business-objectives/revenue-monetization/increase-conversion-rates.md)

Improve the percentage of visitors and prospects who complete desired actions such as purchases, sign-ups, or form submissions.

| KPI | Description |
| --- | --- |
| Conversion Rates | Percentage of visitors who convert after engaging with recommendations |
| Lead Conversion | Rate at which recommendation-engaged visitors become customers |
| Cost Per Lead | Reduction in acquisition cost through organic recommendation engagement |

### [Deliver personalized customer experiences](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

Tailor content, offers, and messaging to individual preferences, behaviors, and lifecycle stage.

| KPI | Description |
| --- | --- |
| Engagement | Interaction frequency with recommendation surfaces (clicks, views, add-to-cart) |
| Conversion Rates | Lift in conversion rates for recommendation-engaged visitors vs. control |
| Customer Satisfaction (CSAT) | Customer satisfaction improvement from relevant, personalized experiences |

## Example tactical use cases

The following are common tactical implementations of this pattern:

- Product cross-sell widget on product detail page ("customers also bought")
- "Recommended for you" carousel on homepage based on browse history
- Content recommendations on media site based on reading behavior
- "Recently viewed" combined with similar items widget
- Post-purchase complementary product recommendations
- Email product recommendations based on behavioral affinity
- Category-specific recommendations based on in-session browse behavior
- Search result re-ranking based on behavioral signals

## Key performance indicators

The following KPIs help measure the effectiveness of behavioral recommendation implementations.

| KPI | Measurement Approach |
| --- | --- |
| Recommendation Click-Through Rate (CTR) | Clicks on recommended items divided by recommendation impressions |
| Recommendation Conversion Rate | Purchases or desired actions from recommendation clicks divided by total recommendation clicks |
| Revenue Influenced by Recommendations | Total revenue from orders that included at least one recommendation-driven product |
| Average Order Value (AOV) Lift | Increase in AOV for sessions that engaged with recommendations vs. sessions without |
| Items Per Order | Number of items per order for recommendation-engaged sessions |
| Recommendation Coverage | Percentage of eligible page views or sessions that received personalized (non-fallback) recommendations |
| Cold-Start Fallback Rate | Percentage of recommendation requests served by fallback logic due to insufficient behavioral history |

## Use case pattern

**Behavioral Recommendation**

Generate item-level or content-level recommendations based on behavioral signals, using AJO Decisioning selection strategies and ranking models to serve contextual content.

**Function chain:** Behavioral Signal Ingestion > Decisioning Strategy Evaluation > Recommendation Delivery > Reporting

See the Pattern Composition section under Implementation Considerations for guidance on combining patterns.

## Applications

The following applications are used in this use case pattern.

- **[!DNL Adobe Journey Optimizer] (AJO) Decisioning** -- Selection strategies, ranking models, item catalogs, and decision policies that evaluate behavioral signals and return the most relevant items for each visitor
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** -- Behavioral profile data accumulation, audience evaluation for recommendation scoping, and computed attributes for behavioral affinity scoring
- **[!DNL Adobe Experience Platform] (AEP)** -- Behavioral event ingestion via [!DNL Web SDK] and [!DNL Mobile SDK], [!DNL Edge Network] processing, XDM schema management for event and catalog data

## Foundational functions

The following foundational capabilities must be in place for this use case pattern. For each function, the status indicates whether it is typically required, assumed to be pre-configured, or not applicable.

| Foundational Function | Status | What Must Be in Place | Experience League Reference |
| --- | --- | --- | --- |
| Administration & Governance | Assumed in Place | AJO sandbox with Decisioning permissions enabled. User roles provisioned with access to item catalog management, selection strategy configuration, and channel surface administration. | [Sandboxes overview](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Access control overview](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Data Modeling & Preparation | Required | Experience Event schema capturing behavioral signals (product views, add-to-cart, purchases, content interactions) with item/product identifiers. Item catalog schema (product attributes, categories, images, prices) for the recommendation item set. Profile schema with identity fields. All schemas enabled for [!DNL Real-Time Customer Profile]. | [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition), [Create a dataset](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/create) |
| Data Sources & Collection | Required | Real-time behavioral event streaming via [!DNL Web SDK] or [!DNL Mobile SDK] is critical -- recommendation quality depends on fresh behavioral signals. Item catalog data must be ingested (batch or streaming). Datastreams configured with AJO service enabled for Edge decisioning. | [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Mobile SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview), [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Identity & Profile Configuration | Required | Behavioral signals must be associated with an identity (known or anonymous via ECID) to build behavioral profiles. For known-visitor recommendations, authenticated identity (CRM ID, email) must be configured. Merge policy active on Edge for real-time recommendation delivery. | [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Audience Definition & Segmentation | Recommended | Audiences may be used to scope recommendations (e.g., only recommend premium products to premium members) or for filtering. Not strictly required if recommendations are purely behavioral. Required for email-based recommendations (Option C) to define the target audience. | [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Supporting functions

The following capabilities augment this use case pattern but are not required for core execution.

| Supporting Function | Status | Why It Matters | Experience League Reference |
| --- | --- | --- | --- |
| Computed / Derived Attribute Creation | Recommended | Computed attributes such as category affinity scores, product interaction frequency, purchase recency, and total spend improve recommendation ranking quality. [!DNL Customer AI] propensity scores can further enhance relevance by predicting purchase likelihood. | [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview), [Customer AI overview](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Data Lifecycle Management | Recommended | Behavioral event data should have appropriate expiration policies -- recommendation relevance degrades with stale data. Setting dataset expiration policies on behavioral event datasets ensures freshness and manages storage. Consent enforcement ensures compliant use of behavioral data. | [Dataset expirations](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration), [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Data Usage Labeling & Enforcement | Recommended | Governance labels on behavioral data ensure compliant use of interaction history for recommendations. Particularly important when behavioral data includes browsing patterns, purchase history, or health/financial product interest signals. | [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) |
| Monitoring & Observability | Recommended | Recommendation delivery latency, fallback rates, and item catalog ingestion health should be monitored. Alerts on behavioral event ingestion failures and decisioning errors help maintain recommendation quality. | [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home), [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| Reporting & Analysis | Included | Recommendation performance reporting is part of Function Chain Step 4. [!DNL Customer Journey Analytics] analysis of recommendation effectiveness, revenue impact, and item-level performance across surfaces and segments provides optimization insights. | [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## Application functions

This plan exercises the following functions from the Application Function Catalog. Functions are mapped to implementation phases rather than numbered steps.

### [!DNL Journey Optimizer] (AJO)

| Function | Implementation Phase | Description |
| --- | --- | --- |
| Decisioning | Item Catalog & Selection Strategy Setup | Configure item catalogs (decision items), selection strategies with behavioral ranking models, filtering rules, and fallback recommendations |
| Channel Configuration | Channel & Surface Configuration | Configure delivery surfaces for web (code-based experiences), in-app, content card, or email channels where recommendations will be rendered |
| Message Authoring | Content & Delivery Configuration | Design recommendation rendering templates, item display layouts, and personalization expressions for recommended items |
| Reporting & Performance Analysis | Reporting & Optimization | Monitor recommendation click-through, conversion, and revenue metrics through AJO native reports and [!DNL Customer Journey Analytics] integration |

### [!DNL Real-Time CDP] (RT-CDP)

| Function | Implementation Phase | Description |
| --- | --- | --- |
| Audience Evaluation | Audience Scoping (Option C) | Evaluate audience segments used to scope recommendations or define the target population for email recommendation campaigns |
| Profile Enrichment | Behavioral Signal Enrichment | Enrich profiles with computed attributes (category affinity scores, interaction frequency) that improve recommendation ranking |

## Prerequisites

Complete the following before beginning implementation:

- AJO Decisioning is provisioned and enabled in the target sandbox
- [!DNL Web SDK] or [!DNL Mobile SDK] is deployed and collecting behavioral events with product/content identifiers
- Product or content catalog data is available for ingestion (product name, category, price, image URL, availability)
- Behavioral event schemas include item/product identifiers that link to catalog items
- Datastream is configured with [!DNL Adobe Journey Optimizer] service enabled (required for Edge decisioning)
- Merge policy with `isActiveOnEdge: true` is configured (required for real-time web/app recommendations)
- For email recommendations (Option C): email channel surface is configured and validated
- For email recommendations (Option C): target audience is defined and evaluating

## Implementation options

The following options describe different approaches for implementing behavioral recommendations. Choose the option that best fits your channel requirements and technical constraints.

### Option A: Web real-time recommendations

**Best for:** Product or content recommendations on web pages -- product detail page cross-sell widgets, homepage recommendation carousels, category page personalized listings, and search result personalization.

**How it works:**

Behavioral signals are collected in real time via [!DNL Web SDK] as visitors browse the site. Each page view, product interaction, or search query is streamed to AEP and associated with the visitor's profile (via ECID for anonymous visitors or authenticated identity for known visitors). When a page containing a recommendation surface loads, the [!DNL Web SDK] requests a decisioning evaluation from AJO via the [!DNL Edge Network]. The decisioning engine evaluates the visitor's behavioral profile against the selection strategy, applies ranking logic, filters out ineligible items (already purchased, out of stock), and returns the recommended items.

Recommendations are rendered on the page through code-based experiences or web channel surfaces. The rendering can be a carousel, grid, single-item widget, or any custom layout defined in the recommendation template. Impression and click events are automatically tracked back to AEP for performance reporting.

**Key considerations:**

- Edge decisioning requires the merge policy to be active on Edge
- Recommendation latency depends on [!DNL Edge Network] response time (sub-500ms SLA for single-scope requests)
- Anonymous visitors receive recommendations based on in-session behavior; known visitors benefit from cross-session behavioral history
- Cold-start visitors with no behavioral history receive fallback recommendations

**Advantages:**

- Real-time personalization based on in-session behavior
- Sub-second recommendation delivery via [!DNL Edge Network]
- Works for both anonymous and known visitors
- Automatic impression and click tracking
- No page reload required for fresh recommendations

**Limitations:**

- Edge profile store contains a subset of full profile attributes
- Complex ranking models with many profile attributes may require hub-side evaluation
- Requires [!DNL Web SDK] deployment with behavioral event tracking

**Experience League:**

- [Deliver offers using the Edge Decisioning API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)

### Option B: Mobile app recommendations

**Best for:** In-app product recommendations, personalized content feeds, notification-driven recommendations, and mobile commerce experiences.

**How it works:**

Behavioral signals are collected via the [!DNL Mobile SDK] as users interact with the app. Product views, content interactions, searches, and purchases are streamed to AEP. When a screen containing a recommendation surface loads, the [!DNL Mobile SDK] requests a decisioning evaluation. Recommendations are delivered through in-app messages, content cards, or code-based experiences within the mobile app.

Content cards are particularly well-suited for recommendation use cases in mobile apps because they persist in a feed-like experience that users can browse at their convenience. In-app messages can be used for contextual recommendations triggered by specific behaviors (e.g., showing complementary products after adding an item to cart).

**Key considerations:**

- [!DNL Mobile SDK] must be configured with behavioral event tracking for relevant interactions
- Content cards provide a persistent recommendation surface; in-app messages are ephemeral
- Offline behavior tracking requires SDK queue management for deferred event submission
- App store update cycles affect how quickly recommendation rendering changes can be deployed

**Advantages:**

- Native mobile experience with smooth, app-integrated recommendation rendering
- Content cards provide a persistent, browsable recommendation feed
- In-app messages enable contextual, behavior-triggered recommendations
- Leverages device-level signals (location, app usage patterns) for enhanced relevance

**Limitations:**

- Requires [!DNL Mobile SDK] integration and app development resources
- Rendering changes require app updates (unless using code-based experiences with server-driven layouts)
- Offline periods create gaps in behavioral signal collection

**Experience League:**

- [Mobile SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configure push notification channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Option C: Email behavioral recommendations

**Best for:** Product recommendations in email campaigns -- abandoned browse emails with viewed product recommendations, post-purchase cross-sell emails, periodic "picks for you" digests, and re-engagement emails with personalized product suggestions.

**How it works:**

Behavioral profile data accumulated from prior sessions informs recommendation selection at email send time or render time. An audience is defined to target the appropriate recipients (e.g., visitors who browsed but did not purchase, customers who made a recent purchase). A campaign or journey is configured to send an email that includes recommendation placements. At send time, AJO Decisioning evaluates each recipient's behavioral profile against the selection strategy and injects the recommended items into the email content.

This option relies on accumulated behavioral history rather than in-session signals. Computed attributes (category affinity scores, recent product views, purchase frequency) significantly improve recommendation quality for email because they distill behavioral history into profile-level signals that the selection strategy can evaluate efficiently.

**Key considerations:**

- Email recommendations are evaluated at send time, not open time -- the behavioral profile state at the moment of send determines the recommendations
- Computed attributes are strongly recommended to improve ranking quality
- Email rendering limitations (no JavaScript, limited CSS) constrain recommendation display formats
- Requires a configured and validated email channel surface

**Advantages:**

- Leverages full behavioral history across sessions for deeper personalization
- Integrates with existing campaign and journey workflows
- Effective for re-engagement and win-back scenarios where web/app touchpoints are unavailable
- Can include multiple recommendation placements within a single email

**Limitations:**

- Recommendations are static at send time -- they do not update when the email is opened
- Email rendering constraints limit recommendation display formats
- Requires audience evaluation and campaign/journey orchestration infrastructure
- Higher implementation complexity due to additional dependencies (channel configuration, audience definition, campaign execution)

**Experience League:**

- [Create an email](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Deliver offers in messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Option comparison

The following table summarizes the key differences between implementation options.

| Criteria | Option A: Web Real-Time | Option B: Mobile App | Option C: Email Behavioral |
| --- | --- | --- | --- |
| Best for | Web page recommendations (PDP, homepage, category) | In-app recommendations and content feeds | Email campaigns with product recommendations |
| Behavioral signal source | In-session + cross-session ([!DNL Web SDK]) | In-app interactions ([!DNL Mobile SDK]) | Accumulated behavioral history (profile) |
| Recommendation latency | Sub-second ([!DNL Edge Network]) | Sub-second ([!DNL Edge Network]) | At send time (hub-side evaluation) |
| Visitor type | Anonymous and known | Known (app users) | Known (email recipients) |
| Complexity | Medium | Medium-High | High |
| Channel dependency | [!DNL Web SDK], code-based experience surface | [!DNL Mobile SDK], in-app/content card surface | Email channel surface, audience, campaign/journey |
| Requires | [!DNL Web SDK] deployment, Edge merge policy | [!DNL Mobile SDK] deployment, Edge merge policy | Email surface, audience definition, campaign setup |

### Choose the right option

Use the following guidance to select the best option for your situation:

- **Start with Option A** if your primary goal is real-time product recommendations on your website. This is the most common starting point and provides immediate value with the lowest implementation complexity.
- **Choose Option B** if your mobile app is a primary engagement channel and in-app recommendations would drive meaningful conversion lift. Option B can run in parallel with Option A using the same selection strategies and item catalogs.
- **Add Option C** when you want to extend behavioral recommendations into email campaigns. This is typically layered on top of Option A or B, using the same item catalogs and selection strategies but with email-specific rendering templates and audience-based targeting.
- **Combine Options A + C** for a common pattern: real-time web recommendations for active visitors, plus abandoned browse or post-purchase email recommendations for visitors who leave without converting.

## Implementation phases

The following phases guide you through the end-to-end implementation of behavioral recommendations.

### Phase 1: Configure behavioral event schema and data collection

**Application Function:** AEP: Data Modeling & Preparation (F2), AEP: Data Sources & Collection (F3)

This phase establishes the XDM schemas, datasets, and data collection mechanisms that capture behavioral signals and item catalog data. This data foundation is what all recommendation logic depends on.

#### Decision: Behavioral event schema design

Which behavioral signals should drive recommendations?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Product views only | Simple cross-sell/upsell recommendations | Lowest implementation effort; limited signal depth |
| Product views + purchases | Recommendations with purchase exclusion and cross-sell logic | Moderate effort; enables "exclude already purchased" filtering |
| Full behavioral suite (views, purchases, add-to-cart, searches, content interactions) | Sophisticated recommendations with multi-signal ranking | Highest signal quality; requires comprehensive [!DNL Web SDK]/[!DNL Mobile SDK] instrumentation |

#### Decision: Item catalog ingestion method

How will the product or content catalog be ingested into AEP?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Batch ingestion via source connector | Catalog updates are periodic (daily/weekly) | Simpler setup; catalog changes not reflected in real time |
| Streaming ingestion | Catalog requires near-real-time updates (price changes, availability) | More complex; ensures recommendations reflect current inventory |
| Manual/API upload | Small catalog with infrequent changes | Simplest setup; not scalable for large or dynamic catalogs |

**UI navigation:** Data Management > Schemas > Create schema; Data Collection > Datastreams > New Datastream

**Key configuration details:**

- Experience Event schema must include product/item identifiers (SKU, product ID, content ID) in the event payload
- Item catalog schema should include attributes used for filtering and ranking: category, price, image URL, availability status, tags
- Datastream must have [!DNL Adobe Journey Optimizer] service enabled for Edge decisioning
- [!DNL Web SDK] `sendEvent` calls must include product interaction data mapped to XDM commerce fields

**Experience League documentation:**

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Define a relationship between two schemas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-api)

### Phase 2: Configure identity and profile

**Application Function:** AEP: Identity & Profile Configuration (F4)

This phase sets up identity namespaces, primary identity designations, and merge policies that ensure behavioral signals are correctly associated with visitor profiles and available for real-time recommendation delivery.

#### Decision: Merge policy for Edge decisioning

Does the recommendation use case require real-time Edge evaluation?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Active on Edge merge policy | Options A and B (web and mobile real-time recommendations) | Required for sub-second recommendation delivery; only one Edge merge policy per sandbox |
| Standard merge policy (not on Edge) | Option C only (email recommendations evaluated at send time) | Sufficient for hub-side evaluation; does not consume the Edge merge policy slot |

#### Decision: Anonymous vs. known visitor identity

How should behavioral signals from anonymous visitors be handled?

| Option | When to choose | Considerations |
| --- | --- | --- |
| ECID-only (anonymous) | Recommendations primarily for anonymous visitors based on in-session behavior | Simpler setup; no cross-session continuity unless visitor authenticates |
| ECID + authenticated identity (CRM ID, email) | Cross-session recommendations for known visitors with identity stitching | Richer behavioral profiles; requires authentication flow |
| Both with identity graph linking | Full anonymous-to-known journey with identity stitching | Most comprehensive; requires identity linking rules configuration |

**UI navigation:** Identities > Identity namespaces; Profiles > Merge policies

**Key configuration details:**

- ECID namespace is pre-configured and used automatically by [!DNL Web SDK] and [!DNL Mobile SDK]
- Custom identity namespaces (CRM ID, loyalty ID) must be created for authenticated identity
- Primary identity on Experience Event schema should be ECID for web/mobile behavioral events
- Merge policy must use Private Device Graph for identity stitching across devices

**Experience League documentation:**

- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Identity namespaces overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Identity graph linking rules](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)

### Phase 3: Set up item catalog and selection strategy

**Application Function:** AJO: Decisioning

This phase configures the item catalog (decision items), selection strategies that combine behavioral signals with item attributes for ranking, filtering rules to exclude ineligible items, and fallback recommendations for cold-start profiles.

#### Decision: Item catalog scope

What items are available for recommendation?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Product catalog (ecommerce) | Recommending physical or digital products for purchase | Item attributes include price, category, availability, images |
| Content catalog (media/publishing) | Recommending articles, videos, or educational content | Item attributes include topic, author, publish date, content type |
| Hybrid catalog | Recommending both products and content | Requires unified item schema accommodating both types |

#### Decision: Ranking approach

How should eligible items be ranked to determine the best recommendations?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Formula-based ranking | Clear business logic for ranking (e.g., sort by category affinity score multiplied by item popularity) | Transparent, auditable ranking; requires defined ranking formula |
| AI-ranked (auto-optimization) | Machine learning should determine optimal ranking based on conversion data | Requires minimum 1,000 conversion events for model training; less transparent |
| Priority-based (manual) | Simple, manually curated recommendation ordering | Easiest to configure; does not adapt to individual behavior |

#### Decision: Filtering rules

What items should be excluded from recommendations?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Exclude already-purchased items | Cross-sell and discovery recommendations | Requires purchase history in behavioral profile |
| Exclude out-of-stock items | Ecommerce with dynamic inventory | Requires real-time or near-real-time catalog updates |
| Exclude previously dismissed items | Content recommendations where users can dismiss suggestions | Requires dismissal tracking in behavioral events |
| Category-scoped filtering | Recommendations limited to specific categories | Uses item attributes for filtering |

#### Decision: Cold-start strategy

What should be shown for new visitors with no behavioral history?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Popular items (global bestsellers) | General-purpose fallback | Simple to maintain; not personalized |
| Category-specific popular items | Visitor has arrived on a category page | Contextually relevant fallback; requires page context |
| Curated editorial picks | Brand wants editorial control over cold-start experience | Requires manual curation and updates |
| Trending items (time-weighted popularity) | Dynamic fallback reflecting current trends | Requires trending signal computation |

**UI navigation:** [!DNL Journey Optimizer] > Components > Decision Management > Decisions; [!DNL Journey Optimizer] > Components > Decision Management > Offers; [!DNL Journey Optimizer] > Components > Decision Management > Placements

**Key configuration details:**

- Create decision items representing each product or content item in the catalog, with attributes (category, price, image URL, tags)
- Define selection strategies that combine item catalog filtering with behavioral ranking logic
- Configure ranking models -- formula-based expressions can reference profile attributes (e.g., category affinity scores from computed attributes)
- Create fallback offers/items that serve as default recommendations for cold-start profiles
- Organize items into collections using collection qualifiers (tags) for logical grouping
- Set up filtering rules within selection strategies to enforce business rules (exclude purchased, in-stock only)

**Experience League documentation:**

- [Decision Management overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Create placements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Create decision rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Create personalized offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Create fallback offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Create collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Create decisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Ranking strategies](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Phase 4: Configure channel and surface

**Application Function:** AJO: Channel Configuration

This phase configures the delivery surfaces where recommendations will be rendered. The configuration varies significantly by implementation option.

#### Decision: Delivery surface type

Where will recommendations be displayed?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Code-based experience (web) | Recommendation widget on web pages with custom rendering | Maximum flexibility for rendering; requires front-end development |
| Web channel surface | Standard web personalization surface | Uses AJO web designer; less flexible than code-based |
| In-app message | Contextual recommendations triggered by app behavior | Ephemeral; disappears after interaction or dismissal |
| Content card (mobile) | Persistent recommendation feed in mobile app | Persists until user acts; browsable feed experience |
| Email | Product recommendations embedded in email campaigns | Static at send time; subject to email rendering constraints |

**Where options diverge:**

**For Option A (Web Real-Time Recommendations):**
Configure a code-based experience surface or web channel surface. Code-based experiences provide the most flexibility for custom recommendation rendering (carousels, grids, item cards). The surface URI identifies where on the page recommendations appear.

**For Option B (Mobile App Recommendations):**
Configure in-app message or content card surfaces. Content cards are recommended for persistent recommendation feeds. In-app messages work well for contextual, behavior-triggered recommendations.

**For Option C (Email Behavioral Recommendations):**
Configure an email channel surface with subdomain delegation, IP pool assignment, and sender settings. Ensure the surface is validated for deliverability.

**UI navigation:** Administration > Channels > Channel surfaces > Create surface

**Experience League documentation:**

- [Set up channel surfaces](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Get started with email configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configure SMS channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Configure push notification channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Phase 5: Configure content and delivery

**Application Function:** AJO: Message Authoring

This phase defines the recommendation rendering templates that control how recommended items are displayed to the visitor. This includes item layout design, personalization expressions that pull item attributes (name, image, price, link), and the overall recommendation experience design.

#### Decision: Recommendation display format

How should recommended items be rendered?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Carousel (horizontal scroll) | Homepage or category page with limited vertical space | Familiar UX pattern; shows multiple items in compact space |
| Grid (multi-row) | Dedicated recommendation section with ample space | Shows more items at once; works well for "recommended for you" sections |
| Single item widget | Contextual recommendation in a specific page location (e.g., sidebar) | Minimal footprint; high-impact placement |
| Inline email block | Recommendations embedded within email body | Subject to email HTML/CSS constraints; typically 2-4 items |

#### Decision: Number of recommendations to display

How many items should the decision return per placement?

| Option | When to choose | Considerations |
| --- | --- | --- |
| 3-4 items | Standard recommendation widget | Balances relevance with visual density |
| 6-8 items | Carousel with scrolling or grid layout | More options for the visitor; requires sufficient catalog depth |
| 1 item | Contextual single-product recommendation | Highest relevance impact; simplest rendering |
| 10+ items | Feed-style recommendation experience | Content-heavy use cases (media, publishing) |

**Where options diverge:**

**For Option A (Web Real-Time Recommendations):**
Design the recommendation rendering using code-based experience templates. Use HTML/CSS/JavaScript to create the carousel, grid, or widget layout. Personalization expressions reference the decision response attributes (item name, image URL, price, product URL). Impression and click tracking are handled automatically by the [!DNL Web SDK].

**For Option B (Mobile App Recommendations):**
Configure content card or in-app message templates with item display logic. Use JSON-based content structures that the mobile app renders natively. Include deep links for each recommended item.

**For Option C (Email Behavioral Recommendations):**
Design email content using the Email Designer. Insert recommendation placements using decision-powered content blocks. Configure personalization expressions for item attributes within the email template. Subject line personalization can reference top recommended items.

**UI navigation:** Content Management > Content Templates; Campaign/Journey > Edit content > Email Designer

**Key configuration details:**

- Each recommendation placement must reference the decision created in Phase 3
- Personalization expressions use Handlebars syntax to render item attributes
- For web: configure the code-based experience to call the decision and render the response
- For email: embed the decision in the email action within the campaign or journey
- Preview recommendations using test profiles with known behavioral history

**Experience League documentation:**

- [Design email content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Deliver offers in messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Preview and test your content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Work with content templates](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### Phase 6: Set up audience scoping and campaign/journey (Option C only)

**Application Function:** RT-CDP: Audience Evaluation, AJO: Campaign Execution or Journey Orchestration

For email-based recommendations (Option C), this phase defines the target audience and configures the campaign or journey that delivers the recommendation email. Options A and B skip this phase because recommendations are delivered in real time at page/screen load.

#### Decision: Audience evaluation method

How should the target audience for recommendation emails be evaluated?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Batch evaluation | Scheduled recommendation email campaigns (daily, weekly digest) | Predictable send timing; audience evaluated before send |
| Streaming evaluation | Event-triggered recommendation emails (abandoned browse, post-purchase) | Near-real-time audience qualification; pairs with journey orchestration |

#### Decision: Delivery mechanism

Should the email be delivered via a campaign or a journey?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Scheduled campaign | One-time or recurring recommendation email blasts to a defined audience | Simpler setup; batch audience evaluation and send |
| Journey with audience entry | Ongoing recommendation emails triggered by audience qualification | Enables multi-step flows (e.g., recommendation email followed by reminder) |
| Event-triggered journey | Recommendation email triggered by a specific event (browse abandonment, purchase) | Real-time triggering; requires event-based journey entry |

**UI navigation:** Customer > Audiences > Create audience > Build rule; Campaigns > Create campaign; Journeys > Create journey

**Key configuration details:**

- Define the target audience using segment rule expressions referencing behavioral history (e.g., "viewed products in the last 7 days but did not purchase")
- Configure the campaign or journey with the email action referencing the channel surface from Phase 4
- Embed the decision from Phase 3 in the email content
- Set scheduling and frequency rules to avoid over-messaging

**Experience League documentation:**

- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Campaign live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)

### Phase 7: Configure reporting and optimization

**Application Function:** AJO: Reporting & Performance Analysis, S5: Reporting & Analysis

This phase establishes performance monitoring for recommendation click-through, conversion, and revenue metrics. It creates the reporting infrastructure to measure recommendation effectiveness and identify optimization opportunities.

#### Decision: Reporting depth

What level of reporting analysis is needed?

| Option | When to choose | Considerations |
| --- | --- | --- |
| AJO native reports only | Basic recommendation performance monitoring | Quick setup; limited to AJO-tracked metrics |
| AJO + [!DNL Customer Journey Analytics] integration | Cross-channel recommendation impact analysis and revenue attribution | Requires [!DNL Customer Journey Analytics] connection and data view; provides deeper insights |
| Full [!DNL Customer Journey Analytics] workspace with custom dashboards | Ongoing optimization program with item-level, segment-level, and surface-level analysis | Most comprehensive; requires [!DNL Customer Journey Analytics] expertise and setup |

**UI navigation:** Campaigns > Select campaign > All time report; Journeys > Select journey > All time report; [!DNL Customer Journey Analytics] > Projects > Create new project

**Key configuration details:**

- Review AJO campaign and journey reports for delivery and engagement metrics
- For [!DNL Customer Journey Analytics] integration, create a connection including AJO experience event datasets (Message Feedback, Email Tracking, Decisioning)
- Create a [!DNL Customer Journey Analytics] data view with recommendation-specific dimensions (item name, item category, recommendation surface) and metrics (impressions, clicks, conversions, revenue)
- Build calculated metrics for recommendation CTR, conversion rate, and revenue per impression
- Create [!DNL Customer Journey Analytics] workspace panels comparing recommendation performance across surfaces, segments, and time periods

**Experience League documentation:**

- [Campaign global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Journey global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Work with Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Create or edit a connection](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Create or edit a data view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Calculated metrics overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

## Implementation considerations

Review the following guardrails, pitfalls, best practices, and trade-offs before and during implementation.

### Guardrails and limits

- Maximum of 10,000 approved personalized offers (decision items) per sandbox -- [Decision Management guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum of 30 placements per decision
- Maximum of 30 collection scopes per decision request
- Offer Delivery response time SLA: less than 500ms at P95 for single-scope Edge requests
- AI ranking models require a minimum of 1,000 conversion events for training
- Offer capping counters may have a lag of up to a few seconds in high-throughput scenarios
- Edge decisions are limited to profile attributes available in the edge profile store
- Only one merge policy can be active on Edge per sandbox -- [Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximum of 25 active computed attributes per sandbox -- [Computed attributes guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- Maximum of 4,000 segment definitions per sandbox -- [Segmentation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Streaming ingestion: maximum 20,000 records per second per HTTP connection -- [Ingestion guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Common pitfalls

- **Decision returns only fallback items:** Verify that personalized decision items are approved, within their validity date range, and that eligibility rules match the visitor's profile attributes. Check that capping limits have not been reached.
- **Edge delivery returns empty personalization:** Ensure the datastream is configured with the [!DNL Adobe Journey Optimizer] service enabled and that the decision scope is correctly formatted in the [!DNL Web SDK] request.
- **Ranking formula not applied:** Verify that the formula is syntactically valid and references accessible profile attributes. Formula errors silently fall back to priority-based ranking.
- **Stale recommendations:** If behavioral event data is not flowing in real time, recommendations will be based on outdated behavioral profiles. Verify [!DNL Web SDK] or [!DNL Mobile SDK] is actively streaming events.
- **Cold-start fallback rate is too high:** If a large percentage of visitors receive fallback recommendations, consider enriching the cold-start strategy with contextual signals (current page category, referral source) rather than relying solely on behavioral history.
- **Recommendations not rendering on page:** Verify that the code-based experience surface URI matches the page URL pattern and that the [!DNL Web SDK] is correctly requesting and rendering the decision response.
- **Catalog items missing from recommendations:** Ensure all catalog items have been ingested as decision items, tagged with the correct collection qualifiers, and included in the appropriate collections referenced by the selection strategy.

### Best practices

- Start with a formula-based ranking model using computed attributes (category affinity, interaction recency) before investing in AI-ranked models. Formula-based models are transparent, auditable, and provide a solid baseline for comparison.
- Implement impression and click tracking from day one. Without interaction data, AI ranking models cannot train, and you cannot measure recommendation effectiveness.
- Create separate selection strategies for different recommendation surfaces (homepage, PDP, email) rather than reusing a single strategy everywhere. Different surfaces serve different user intents.
- Use computed attributes to distill behavioral history into ranking signals. Raw event data is too granular for effective formula-based ranking; aggregated signals like "category affinity score" and "days since last purchase" are more effective.
- Test fallback recommendations separately from personalized recommendations. Ensure fallback items are high-quality, brand-appropriate defaults that provide a good experience for new visitors.
- Monitor the cold-start fallback rate as a key health metric. A decreasing fallback rate over time indicates growing behavioral coverage.
- For email recommendations, schedule sends at times when the behavioral profile is most complete (e.g., after peak browsing hours, not during them).

### Trade-off decisions

The following trade-offs should be evaluated based on your specific requirements.

#### Real-time signals vs. accumulated history

In-session behavioral signals provide immediate relevance but limited depth. Accumulated behavioral history provides depth but may be stale. The balance between these sources affects recommendation quality.

- **Option A favors:** Real-time signals for immediate relevance, supplemented by accumulated history for known visitors
- **Option C favors:** Accumulated history exclusively, since emails are sent asynchronously
- **Recommendation:** For web and mobile (Options A, B), combine in-session signals with computed attributes derived from historical behavior. For email (Option C), invest heavily in computed attributes that summarize behavioral history into actionable profile-level signals.

#### Formula-based vs. AI-ranked models

Formula-based ranking is transparent and immediate. AI-ranked models adapt automatically but require training data and offer less visibility into ranking decisions.

- **Formula-based favors:** Transparency, auditability, immediate deployment, and fine-grained business control over ranking logic
- **AI-ranked favors:** Automated optimization, discovery of non-obvious patterns, and reduced manual tuning effort
- **Recommendation:** Start with formula-based ranking to establish a performance baseline and accumulate conversion data. Transition to AI-ranked models once you have sufficient training data (1,000+ conversion events) and want to optimize beyond what manual formula tuning can achieve.

#### Recommendation coverage vs. relevance

Broadening the item catalog and relaxing filtering rules increases the percentage of requests that receive personalized recommendations, but may reduce per-recommendation relevance.

- **High coverage favors:** Maximizing the number of visitors who see personalized recommendations; useful when the primary goal is engagement
- **High relevance favors:** Showing only highly relevant items, even if it means more visitors see fallback recommendations; useful when the primary goal is conversion
- **Recommendation:** Start with moderate filtering (exclude purchased items, out-of-stock items) and monitor both fallback rate and conversion rate. Tighten filtering rules only if conversion data supports it.

#### Personalization depth vs. implementation complexity

Richer behavioral signals and more sophisticated ranking models improve recommendation quality but increase implementation complexity and maintenance burden.

- **Simpler implementation favors:** Faster time to value, lower maintenance, easier to debug and iterate
- **Deeper personalization favors:** Higher conversion lift, better customer experience, competitive differentiation
- **Recommendation:** Implement in phases. Start with product view signals and formula-based ranking (Phase 1). Add computed attributes for behavioral enrichment (Phase 2). Evaluate AI-ranked models once the foundation is mature and sufficient training data is available (Phase 3).

## Related documentation

The following resources provide additional detail on the technologies and capabilities used in this pattern.

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
- [Deliver offers using the Edge Decisioning API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)

### Data collection and Web/Mobile SDK

- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Install Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Mobile SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Edge Network Server API overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### XDM and data modeling

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Create a dataset](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/create)
- [Define a relationship between two schemas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-api)

### Identity and profile

- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Identity namespaces overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Real-Time Customer Profile overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Audiences and segmentation

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Computed attributes and profile enrichment

- [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Computed attributes UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Customer AI overview](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Channel configuration

- [Get started with email configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Set up channel surfaces](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delegate subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)

### Message authoring and personalization

- [Design email content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Work with content templates](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### Reporting and analytics

- [Campaign global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Journey global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Work with Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Calculated metrics overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

### Data governance and lifecycle

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview)
- [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Dataset expirations](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration)

### Monitoring and observability

- [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
- [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

### Guardrails

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Ingestion guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Identity Service guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)

### Tutorials and guides

- [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Tags overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
- [Consent and preferences field group](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
