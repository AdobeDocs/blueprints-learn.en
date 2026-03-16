---
title: Anonymous Visitor Web Personalization
description: "Learn how to deliver personalized web content to unidentified visitors based on in-session behavioral signals."
solution: Journey Optimizer, Real-Time Customer Data Platform
---

# Anonymous visitor web personalization

This reference plan provides implementation guidance for delivering personalized web content to anonymous (unidentified) visitors based on in-session behavioral signals. It covers the complete implementation lifecycle -- from [!DNL Web SDK] configuration and edge audience definition through content delivery and performance reporting -- and is designed for solution architects, marketing technologists, and implementation engineers working with [!DNL Adobe Journey Optimizer] (AJO), [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP), and [!DNL Adobe Experience Platform] (AEP).

Use this plan to understand the architecture, evaluate implementation options, make informed configuration decisions, and locate the relevant Experience League documentation for each phase of implementation.

The pattern operates with limited data -- only what can be observed in the current session and any anonymous edge profile accumulated from prior visits with the same device or cookie. This makes it suitable for top-of-funnel personalization where the visitor has no account or has not authenticated.

## Use case overview

Anonymous Visitor Web Personalization addresses the business need to deliver relevant, personalized content to website visitors who have not yet been identified -- they have not logged in, have no known identity, and cannot be resolved to a unified customer profile. Despite this limitation, meaningful personalization is achievable using in-session behavioral signals: pages viewed, time on site, scroll depth, referral source, geographic location, device type, and UTM campaign parameters.

This pattern uses AJO's web channel surfaces and code-based experiences to modify page content in real time. Edge segmentation is the primary evaluation method since decisions must be made with sub-second latency as the visitor navigates the site. The [!DNL Web SDK] collects behavioral signals and sends them to the [!DNL AEP Edge Network], where edge-evaluated audience rules determine which content variant to deliver.

Unlike known-visitor web/app personalization, which leverages the full unified profile and segment membership, this pattern is constrained to data observable in the current session and any anonymous edge profile associated with the visitor's ECID ([!DNL Experience Cloud ID]). This distinction is critical for implementation planning: the behavioral signals available for personalization are limited to what the [!DNL Web SDK] captures and what persists in the edge profile store across sessions via the cookie-based ECID.

## Key business objectives

The following business objectives are supported by this use case pattern.

**[Increase website engagement](../../../business-objectives/acquisition-growth/increase-website-engagement.md)**

Improve time on site, pages per session, and interaction with web content through relevant experiences tailored to anonymous visitor signals.

| KPIs |
| --- |
| Time On (web) Page |
| Engagement |
| Conversion Rates |

**[Deliver personalized customer experiences](../../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

Tailor content, offers, and messaging to individual preferences, behaviors, and lifecycle stage -- even for visitors who have not yet identified themselves.

| KPIs |
| --- |
| Engagement |
| Conversion Rates |
| Customer Satisfaction (CSAT) |

**[Increase conversion rates](../../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

Improve the percentage of visitors and prospects who complete desired actions such as purchases, sign-ups, or form submissions by presenting the most relevant content based on behavioral context.

| KPIs |
| --- |
| Conversion Rates |
| Lead Conversion |
| Cost Per Lead |

## Example tactical use cases

The following examples illustrate specific scenarios where this pattern can be applied.

- **Landing page headline A/B test based on referral source** -- Test different headlines for visitors arriving from Google, social media, or direct traffic to optimize engagement by acquisition channel
- **Category affinity recommendations based on browse behavior** -- Display product or content recommendations based on pages viewed in the current session to increase discovery and conversion
- **Exit-intent offer for visitors about to leave** -- Present a promotional offer or lead capture form when behavioral signals indicate the visitor is about to abandon the site
- **Geo-targeted promotional banner** -- Show location-specific promotions, store locator content, or regional offers based on the visitor's geographic location
- **Device-specific content layout optimization** -- Adapt content layout, image sizes, and CTA placement based on whether the visitor is on desktop, tablet, or mobile
- **New vs. returning visitor welcome messaging** -- Differentiate the experience for first-time visitors versus returning anonymous visitors using ECID persistence across sessions
- **Content recommendations based on viewed pages in current session** -- Dynamically surface related articles, products, or resources based on the pages the visitor has already viewed
- **Dynamic hero banner based on UTM campaign parameters** -- Personalize the hero banner to match the messaging or creative from the referring campaign

## Key performance indicators

Use the following KPIs to measure the effectiveness of this use case pattern.

| KPI | Description | Measurement approach |
| --- | --- | --- |
| Personalization Impression Rate | Percentage of eligible page views where personalized content was delivered | AJO campaign report: impressions / total page views |
| Click-Through Rate (CTR) | Percentage of personalized content impressions that result in a click | AJO campaign report: clicks / impressions |
| Engagement Lift | Increase in time on page, pages per session, or scroll depth for personalized vs. default content | CJA workspace comparison: personalized cohort vs. control |
| Conversion Rate | Percentage of visitors exposed to personalized content who complete a desired action | CJA funnel analysis: impression > interaction > conversion |
| Bounce Rate Reduction | Decrease in single-page sessions for visitors who receive personalized content | CJA session analysis: bounce rate delta for personalized vs. default |
| Experiment Win Rate | Percentage of A/B tests that produce a statistically significant winner | AJO experiment report: experiments reaching confidence threshold |

## Use case pattern

The following describes the core pattern and function chain for this use case.

**Anonymous Visitor Web Personalization**

Deliver personalized content based on in-session behavioral signals for unidentified visitors via AJO web channel.

**Function chain:** Web Surface Configuration > Behavioral Rule Evaluation > Content Delivery > Impression Tracking > Reporting

## Applications

The following applications are used in this use case pattern.

- **[!DNL Adobe Journey Optimizer] (AJO)** -- Web channel surface configuration, content authoring (web and code-based experiences), campaign execution, content experimentation (A/B testing), decisioning (dynamic content selection), and reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** -- Edge segmentation for real-time audience evaluation based on in-session behavioral signals; anonymous edge profile management
- **[!DNL Adobe Experience Platform] (AEP)** -- [!DNL Web SDK] for behavioral signal collection, [!DNL Edge Network] for real-time data routing and personalization delivery, datastream configuration

## Foundational functions

The following foundational capabilities must be in place for this use case pattern. For each function, the status indicates whether it is typically required, assumed to be pre-configured, or not applicable.

| Foundational function | Status | What must be in place | Experience League reference |
| --- | --- | --- | --- |
| Administration & Governance | Assumed in Place | AJO sandbox with web channel permissions configured. [!DNL Web SDK] implementation permissions and datastream access granted to the implementation team. Users provisioned with roles that allow web channel configuration, audience management, and campaign execution. | [Access control overview](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Data Modeling & Preparation | Required | Experience Event schema capturing web behavioral signals (page views, clicks, scroll depth, referral data, UTM parameters). The schema must include standard web interaction field groups and be enabled for edge profile to support real-time evaluation. A corresponding dataset must be created and Profile-enabled. | [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Data Sources & Collection | Required | [!DNL Web SDK] must be implemented on all target web properties with a datastream configured to route data to [!DNL AEP Edge Network]. The datastream must have the [!DNL Adobe Experience Platform] and [!DNL Adobe Journey Optimizer] services enabled. This is a critical dependency -- without [!DNL Web SDK], no behavioral signal collection or experience delivery is possible. | [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home) |
| Identity & Profile Configuration | Required | ECID ([!DNL Experience Cloud ID]) configured as the primary identity namespace for anonymous visitors. Edge merge policy must be configured with `isActiveOnEdge: true` to resolve anonymous profile data at the edge. Only one merge policy can be active on edge per sandbox. | [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| Audience Definition & Segmentation | Required | Edge-evaluated audience segments defined based on in-session behavioral signals. Edge segmentation is mandatory for sub-second evaluation latency. Segment rules must use only edge-eligible segment rule expressions (simple attribute checks and segment membership -- no time-series queries or complex aggregations). | [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation) |

## Supporting functions

The following capabilities augment this use case pattern but are not required for core execution.

| Supporting function | Status | Why it matters | Experience League reference |
| --- | --- | --- | --- |
| Computed / Derived Attribute Creation | Not Applicable | Limited value for anonymous visitors since there is minimal historical profile data to aggregate. May become applicable if the edge profile accumulates meaningful behavioral data from prior anonymous visits across multiple sessions. | [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Recommended | Pseudonymous profile expiration should be configured for anonymous edge profiles to manage storage and comply with privacy requirements. ECID-only profiles can be set to expire between 14 and 365 days. Cookie consent policies should be enforced for behavioral data collection. | [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Data Usage Labeling & Enforcement | Recommended | Governance labels on behavioral data ensure compliance, particularly for geo-targeting (S2 sensitive geographic label) and device-based personalization. Labels prevent restricted behavioral data from being used in unauthorized personalization contexts. | [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Monitoring & Observability | Recommended | [!DNL Edge Network] and [!DNL Web SDK] data flow monitoring helps detect personalization delivery issues. Configure alerts for datastream failures, ingestion errors, and edge delivery anomalies. Critical for production deployments where personalization failures degrade the visitor experience. | [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting & Analysis | Included | Personalization performance reporting is part of the function chain (Phase 5). CJA analysis of anonymous visitor personalization effectiveness enables deep funnel analysis, cohort comparison, and conversion impact measurement beyond what AJO native reports provide. | [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Application functions

This plan exercises the following functions from the Application Function Catalog. Functions are mapped to implementation phases rather than numbered steps.

### [!DNL Journey Optimizer] (AJO)

| Function | Implementation phase | Description |
| --- | --- | --- |
| Channel Configuration | Phase 1: Web Surface Configuration | Configure web channel surfaces defining where personalized content will be delivered on target web properties |
| Message Authoring | Phase 3: Content Authoring & Variant Creation | Author personalized content variants for web surfaces using the web designer, code-based experience editor, or content templates |
| Campaign Execution | Phase 4: Campaign & Delivery Configuration | Create and activate web campaigns that bind audiences, content, and delivery configuration |
| Decisioning | Phase 3: Content Authoring & Variant Creation (Option C) | Configure decision policies, eligibility rules, and ranking strategies for dynamic content selection based on behavioral signals |
| Content Experimentation | Phase 3: Content Authoring & Variant Creation (Option B) | Configure A/B and multivariate content experiments with traffic allocation, success metrics, and confidence thresholds |
| Reporting & Performance Analysis | Phase 5: Reporting & Performance Analysis | Monitor personalization delivery metrics, variant effectiveness, experiment results, and conversion impact |

### [!DNL Real-Time CDP] (RT-CDP)

| Function | Implementation phase | Description |
| --- | --- | --- |
| Audience Evaluation | Phase 2: Behavioral Audience Definition | Define and evaluate edge-based audience segments using in-session behavioral signals for real-time personalization targeting |

## Prerequisites

Complete the following before beginning implementation.

- [ ] [!DNL Web SDK] is implemented on all target web properties with `sendEvent` calls capturing page views, clicks, and relevant behavioral interactions
- [ ] Datastream is configured in the Data Collection UI with [!DNL Adobe Experience Platform] and [!DNL Adobe Journey Optimizer] services enabled
- [ ] Experience Event schema exists with web interaction field groups (page views, referral data, UTM parameters, device context) and is enabled for Profile
- [ ] ECID identity namespace is configured and designated as primary identity on the web behavioral event schema
- [ ] Edge merge policy is configured with `isActiveOnEdge: true` in the target sandbox
- [ ] AJO web channel is provisioned and accessible in the target sandbox
- [ ] Content variants (copy, images, CTAs) are designed and approved for each personalization use case
- [ ] Success metrics are defined (what constitutes a conversion or engagement event for measurement)
- [ ] Cookie consent mechanism is implemented on the website to comply with privacy regulations before collecting behavioral data

## Implementation options

This section describes three implementation approaches. Select the option that best fits your personalization requirements.

### Option A: Rule-based web personalization

**Best for:** Simple, deterministic personalization -- geo-targeted banners, referral-source-specific headlines, device-specific layouts, new vs. returning visitor messaging. Choose this option when the content variant can be determined by straightforward conditional logic (if condition X, show content Y).

**How it works:**

Rule-based personalization uses edge-evaluated audience segments to determine which content variant a visitor sees. Each audience segment maps to a specific content variant through conditional rules defined in the campaign. When a visitor loads a page, the [!DNL Web SDK] sends behavioral signals to the [!DNL Edge Network], which evaluates the visitor's edge profile against the defined audience rules in milliseconds. The matching content variant is returned in the [!DNL Edge Network] response and rendered on the page.

This approach requires defining distinct audience segments in RT-CDP (e.g., "visitors from Google search," "visitors in California," "mobile device visitors") and creating corresponding content variants in AJO. The campaign binds each audience to its content variant using conditional content rules or separate campaigns per segment. No AI ranking or traffic splitting is involved -- the relationship between audience and content is deterministic.

**Key considerations:**

- Requires well-defined audience criteria that can be expressed as edge-eligible segment rule expressions
- Content variants must be pre-authored for each audience segment
- Adding new personalization rules requires creating new audience segments and content variants
- Does not provide statistical measurement of content variant effectiveness

**Advantages:**

- Simplest to implement and understand -- clear cause-and-effect relationship between audience and content
- No experimentation overhead or traffic splitting required
- Deterministic behavior makes testing and QA straightforward
- Low latency since edge evaluation is purely rule-based
- Works well when the business already knows which content performs best for each segment

**Limitations:**

- No built-in mechanism to measure whether personalization improves outcomes vs. default content
- Requires manual decision-making about which content to show each segment
- Does not adapt or optimize over time -- static rules until manually changed
- Scaling to many segments and variants increases configuration complexity

**Experience League:**

- [Get started with web channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Option B: Experimentation-based web personalization

**Best for:** A/B and multivariate testing -- testing headline variants, CTA button colors, layout alternatives, promotional offers -- with statistical significance measurement. Choose this option when you need to validate which content variant performs best before committing to a permanent personalization rule.

**How it works:**

Experimentation-based personalization uses AJO Content Experimentation to randomly allocate visitors to content treatment groups and measure which variant performs best against a defined success metric. Traffic is split across variants (e.g., 50/50 for A/B, 33/33/34 for A/B/C) and performance is tracked until statistical significance is reached.

The experiment is embedded in an AJO web campaign. When a visitor loads a page, the [!DNL Edge Network] assigns them to a treatment group based on the configured traffic allocation. The visitor consistently sees the same treatment for the duration of the experiment (session-level or visitor-level persistence depending on configuration). Success metrics (clicks, conversions, engagement events) are tracked via [!DNL Web SDK] and reported in the AJO experiment report.

This option does not require pre-defined audience segments for targeting -- all visitors (or a targeted subset) participate in the experiment. The goal is to discover which content performs best, not to target known segments with predetermined content.

**Key considerations:**

- Requires sufficient traffic volume to reach statistical significance within a reasonable timeframe
- Experiments use a Bayesian statistical model with anytime-valid confidence intervals
- A holdout group (receives no personalized content) is recommended to measure incremental lift
- Only one experiment can be active per campaign at a time
- Experiment modifications require stopping and restarting the campaign

**Advantages:**

- Provides statistically rigorous measurement of content variant effectiveness
- Removes guesswork from personalization decisions -- data-driven content selection
- Supports holdout groups for true incremental lift measurement
- Built-in experiment reporting with confidence intervals and winner declaration
- Results can inform future rule-based personalization (Option A) by identifying winning variants

**Limitations:**

- Requires meaningful traffic volume -- low-traffic pages may take weeks to reach significance
- Traffic splitting means some visitors see suboptimal content during the test period
- Cannot personalize by segment during the experiment (all visitors or a subset participate equally)
- Maximum of 10 treatment variants per experiment
- No continuous optimization -- experiments are discrete with a start and end

**Experience League:**

- [Get started with content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Create a content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Content experiment report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### Option C: Decisioning-based web personalization

**Best for:** Dynamic content selection -- category affinity recommendations, exit-intent offers, behavioral recommendations -- where a decision policy evaluates session signals and selects the optimal content from a catalog of eligible items. Choose this option when the content selection logic is too complex for simple rules, when you want AI-ranked optimization, or when the set of eligible content items is large and dynamic.

**How it works:**

Decisioning-based personalization uses AJO Decisioning to evaluate behavioral signals and select the best content variant for each visitor from a managed catalog of content items (offers). Each content item has eligibility rules (who qualifies), representations (what the content looks like in each placement), and optional capping constraints (how often it can be shown). A decision policy links placements (where content appears on the page) to collections of content items and applies a ranking strategy to select the best option.

When a visitor loads a page, the [!DNL Web SDK] sends an [!DNL Edge Network] request that includes the decision scope. The Decisioning engine evaluates the visitor's edge profile against content item eligibility rules, applies the ranking strategy (priority-based, formula-based, or AI-ranked), and returns the winning content item. This happens at the edge with sub-second latency.

The ranking strategy determines how eligible content items are ordered. Priority-based ranking uses manually assigned priority values. Formula-based ranking uses a custom expression (e.g., weighting recency of page views). AI-ranked ranking uses a machine learning model that optimizes for the selected success metric over time, but requires a minimum of 1,000 conversion events for training.

**Key considerations:**

- Requires setting up the Decisioning components: placements, eligibility rules, content items, fallback items, collections, and decision policies
- AI-ranked strategies require sufficient conversion volume (1,000+ events) to train the model
- Edge decisions are limited to profile attributes available in the edge profile store
- Content items must be managed and maintained in the Decisioning library
- Fallback content must be defined for cases where no personalized item qualifies

**Advantages:**

- Scales to large content catalogs without requiring individual audience-to-content mapping
- AI-ranked strategies continuously optimize content selection based on observed performance
- Eligibility rules and capping constraints provide fine-grained control over content delivery
- Supports complex business logic that would be difficult to express as audience segments
- Reusable across channels -- the same decision policy can power web, email, and mobile personalization

**Limitations:**

- Higher implementation complexity -- requires setting up the full Decisioning component stack
- AI ranking requires significant conversion volume and time to train effectively
- Edge profile data limitations constrain the eligibility rule complexity for anonymous visitors
- Content item management overhead -- each item needs representations, eligibility rules, and maintenance
- Debugging decisioning logic is more complex than rule-based approaches

**Experience League:**

- [Decision Management overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Create placements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Create personalized offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Create decisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)

### Option comparison

The following table compares the three implementation options across key criteria.

| Criteria | Option A: Rule-based | Option B: Experimentation | Option C: Decisioning |
| --- | --- | --- | --- |
| Best for | Known segment-to-content mappings | Discovering which content works best | Dynamic content selection from large catalogs |
| Complexity | Low | Medium | High |
| Latency | Sub-second (edge) | Sub-second (edge) | Sub-second (edge) |
| Personalization precision | Segment-level (audience rules) | Visitor-level (random assignment) | Visitor-level (eligibility + ranking) |
| Content optimization | Manual (no measurement) | Statistical testing (A/B) | Continuous (AI-ranked) or manual (priority) |
| Requires audience segments | Yes (edge-evaluated) | No (traffic splitting) | Optional (for eligibility rules) |
| Measurement capability | None built-in (requires CJA) | Built-in experiment reports | Built-in decisioning reports |
| Content catalog size | Small (1:1 segment-to-content) | Small (2-10 variants) | Large (unlimited eligible items) |
| Requires | Edge audiences, content variants | Campaign with experiment enabled | Decisioning components (placements, offers, policies) |

### Choose the right option

Use the following decision logic to select the appropriate implementation option:

1. **Do you already know which content should be shown to each visitor segment?**
   - Yes: Start with **Option A (Rule-Based)**. You have established content strategies per segment and need deterministic delivery.
   - No: Proceed to question 2.

2. **Do you need to test a small number of content variants to find the best performer?**
   - Yes: Choose **Option B (Experimentation)**. You want statistical validation before committing to a content strategy.
   - No: Proceed to question 3.

3. **Do you have a large catalog of content items with complex eligibility and ranking requirements?**
   - Yes: Choose **Option C (Decisioning)**. You need dynamic content selection that scales beyond simple rules.
   - No: Start with **Option A (Rule-Based)** for simplicity, then evolve to Option B or C as requirements grow.

**Combining options:** These options are not mutually exclusive. A common progression is to start with Option B (Experimentation) to discover winning content, then deploy winners using Option A (Rule-Based) for ongoing delivery. Option C (Decisioning) can be layered on top for use cases that require dynamic catalog-based selection, while Option A handles simpler deterministic rules.

## Implementation phases

The following phases describe the end-to-end implementation workflow.

### Phase 1: Configure web surfaces

**Application function:** AJO: Channel Configuration

Define the web channel surfaces that specify where on your website personalized content will be delivered. A web surface identifies a specific page URL or URL pattern and the location on the page (CSS selector or code-based experience surface) where AJO can inject or replace content.

**Decision points in this phase:**

>[!NOTE]
>**Decision: Surface type** -- How should personalized content be delivered to the page?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Web channel (visual editor) | The personalization involves modifying visible page elements (banners, headlines, images, CTAs) using a drag-and-drop visual editor | Requires the web designer browser extension. Best for marketing-led content changes. Limited to visual modifications of existing page elements. |
| Code-based experience | The personalization requires injecting structured data (JSON) that the website application code consumes and renders | Requires developer implementation to consume the JSON payload. Maximum flexibility for complex personalization. Best for SPAs, dynamic components, and programmatic rendering. |
| Both (hybrid) | Different personalizations on the same site need different delivery mechanisms | Use web channel for simple visual changes and code-based experiences for programmatic rendering. Increases implementation complexity but maximizes coverage. |

>[!NOTE]
>**Decision: Surface scope** -- What URL scope should the web surface cover?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Exact URL match | Personalization targets a specific page (e.g., homepage, landing page) | Most precise targeting. Requires separate surfaces for each page. |
| URL pattern with wildcards | Personalization applies across a category of pages (e.g., all product pages, all blog articles) | Reduces surface management overhead. Content variants must be designed to work across all matching pages. |
| Single-page application (SPA) surface | The website is a SPA where URL changes do not trigger full page reloads | Requires SPA-aware [!DNL Web SDK] configuration with `sendEvent` calls on view changes. Surface definitions use the SPA view name rather than URL. |

**UI navigation:** [!DNL Journey Optimizer] > Administration > Channels > Web configuration

**Key configuration details:**

- Define the page URL or URL pattern for the surface
- Specify the CSS selector or surface URI for content placement
- For code-based experiences, define the surface name that the application code will reference
- Associate the surface with the AJO sandbox where campaigns will be created

**Experience League documentation:**

- [Get started with web channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Create web experiences](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Code-based experience channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Code-based experience configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

### Phase 2: Define behavioral audiences

**Application function:** RT-CDP: Audience Evaluation

Define edge-evaluated audience segments based on in-session behavioral signals that drive personalization targeting. These audiences determine which visitors qualify for each personalized experience. Edge evaluation is mandatory for this pattern since personalization decisions must be made in sub-second timeframes as the visitor navigates the site.

**Decision points in this phase:**

>[!NOTE]
>**Decision: Behavioral signal selection** -- Which in-session signals should drive personalization targeting?

| Signal | When to use | Edge eligibility |
| --- | --- | --- |
| Referral source / UTM parameters | Campaign-specific landing page personalization | Eligible -- simple attribute check on the current event |
| Geographic location (country, region, city) | Regional promotions, language-specific content, store locator | Eligible -- profile attribute check |
| Device type (desktop, mobile, tablet) | Device-optimized content layouts and CTAs | Eligible -- profile attribute check |
| Pages viewed in session | Category affinity, content recommendations | Eligible with constraints -- simple event count checks only |
| New vs. returning visitor | Welcome messaging, progressive engagement | Eligible -- ECID persistence indicates returning visitor |
| Time on site / scroll depth | Exit-intent, engagement-based offers | May require custom implementation -- not natively edge-eligible |

>[!NOTE]
>**Decision: Audience evaluation method** -- All audiences for this pattern must use edge evaluation. Confirm eligibility before defining segments.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Edge evaluation | Required for this pattern | Segment rule expressions must be edge-eligible: simple attribute comparisons, segment membership checks, no time-series queries or aggregation functions. Sub-second evaluation latency. |
| Streaming evaluation (fallback) | When the segment rule expression is not edge-eligible but near-real-time is acceptable | Seconds-to-minutes latency. Supports more complex segment rule expressions. May introduce noticeable delay in personalization delivery. |

**UI navigation:** Customer > Audiences > Create audience > Build rule

**Key configuration details:**

- Use Segment Builder to define audience rules using behavioral attributes
- Verify edge eligibility by confirming the segment rule expression uses only supported functions (simple attribute comparisons, segment membership)
- Set the merge policy to the edge-active merge policy configured in F4
- Preview audience population to validate the segment returns expected results
- For audiences based on in-session page views, use event-level attributes from the current session rather than time-series queries

**Where options diverge:**

**For Option A (Rule-Based):**
Create distinct audience segments for each content variant. Each segment represents a specific behavioral condition (e.g., "Referral = Google AND Geo = US" maps to content variant A). The number of audiences equals the number of personalization rules.

**For Option B (Experimentation):**
Audience definition is optional. If the experiment targets all visitors, no audience is required -- traffic splitting handles variant assignment. If the experiment targets a specific subset (e.g., only mobile visitors), define a single targeting audience for experiment eligibility.

**For Option C (Decisioning):**
Define audiences for use as eligibility rules on content items. These audiences determine which visitors qualify for which content items in the decision policy. The decisioning engine handles content selection from among eligible items.

**Experience League documentation:**

- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Profile Query Language reference](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

### Phase 3: Author content and create variants

**Application function:** AJO: Message Authoring, AJO: Content Experimentation (Option B), AJO: Decisioning (Option C)

Create the personalized content variants that will be delivered to visitors based on audience membership (Option A), experiment assignment (Option B), or decisioning logic (Option C). This phase covers content creation using the AJO web designer or code-based experience editor, as well as the experiment or decisioning configuration that governs how content is selected.

**Decision points in this phase:**

>[!NOTE]
>**Decision: Content authoring approach** -- How should web content variants be authored?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Web visual editor | Marketing team can modify page elements visually without code | Requires browser extension. Best for text, image, and CTA modifications. Limited to modifying existing page elements. |
| Code-based experience editor | Content requires structured data (JSON) that application code renders | Maximum flexibility. Requires developer implementation to consume the payload. Best for dynamic components and SPAs. |
| HTML/CSS code editor | Content modifications require custom HTML or CSS | Direct code control. Requires HTML/CSS expertise. Best for complex layout changes. |

>[!NOTE]
>**Decision: Personalization tokens** -- Should content include dynamic personalization using profile or contextual attributes?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Static content variants | Each variant is a fixed piece of content with no dynamic tokens | Simplest approach. Content is predictable and easy to QA. No risk of missing attribute values. |
| Dynamic content with personalization expressions | Content includes Handlebars-style tokens that resolve to profile or event attributes (e.g., city name, referral source) | More relevant content. Requires fallback values for attributes that may be null on anonymous profiles. Use `{{profile.homeAddress.city}}` syntax with helpers. |
| Conditional content blocks | Different content blocks render based on attribute conditions within a single variant | Reduces the number of distinct variants needed. Increases content complexity. Good for minor variations within a shared layout. |

**UI navigation:** [!DNL Journey Optimizer] > Campaigns > Select campaign > Edit content

**Key configuration details:**

- Author content using the web designer (visual modifications) or code-based experience editor (JSON payload)
- Use the personalization expression editor to insert dynamic tokens from edge profile attributes
- Configure fallback content for personalization tokens that may be empty on anonymous profiles
- Preview content with test profiles to verify rendering across scenarios

**Where options diverge:**

**For Option A (Rule-Based):**
Author a distinct content variant for each audience segment defined in Phase 2. Bind each variant to its target audience using conditional content rules in the campaign configuration. Ensure a default content variant exists for visitors who do not match any audience rule.

**For Option B (Experimentation):**
Author treatment variants (A, B, C, etc.) for the experiment. Enable content experimentation on the campaign, define treatment variants with their content, set traffic allocation percentages, and configure the success metric.

- Define 2-10 treatment variants with distinct content
- Set traffic allocation (e.g., 50/50 for A/B, or weighted split for lower-risk testing)
- Optionally include a holdout group (e.g., 10% receives default content) to measure incremental lift
- Select the success metric: unique opens, unique clicks, conversions, or custom metric
- Set the confidence threshold: 95% for standard tests, 99% for high-stakes decisions, 90% for directional learning
- **UI navigation:** Campaign > Content experiment > Add treatment > Traffic allocation > Success metric

**For Option C (Decisioning):**
Set up the Decisioning component stack and integrate it into the campaign.

1. **Create placements** -- Define where on the page content items will appear (web HTML, web JSON, web image)
   - **UI navigation:** [!DNL Journey Optimizer] > Components > Decision Management > Placements
2. **Define eligibility rules** -- Create rules based on edge profile attributes that determine which visitors qualify for each content item
   - **UI navigation:** [!DNL Journey Optimizer] > Components > Decision Management > Rules
3. **Create content items (offers)** -- Author personalized content items with representations for each placement, eligibility rules, priority, and optional capping
   - **UI navigation:** [!DNL Journey Optimizer] > Components > Decision Management > Offers > Create offer
4. **Create fallback content** -- Define a fallback item returned when no personalized item qualifies
   - **UI navigation:** [!DNL Journey Optimizer] > Components > Decision Management > Offers > Create fallback offer
5. **Organize into collections** -- Group content items using collection qualifiers (tags) and create collections
   - **UI navigation:** [!DNL Journey Optimizer] > Components > Decision Management > Collection qualifiers / Collections
6. **Create decision policy** -- Link placements to collections and select the ranking strategy (priority-based, formula-based, or AI-ranked)
   - **UI navigation:** [!DNL Journey Optimizer] > Components > Decision Management > Decisions > Create decision

**Experience League documentation:**

- [Create web experiences](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Code-based experience channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Create a content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Create personalized offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Create decisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Ranking strategies](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Phase 4: Configure campaign and delivery

**Application function:** AJO: Campaign Execution

Create and activate the AJO web campaign that binds the web surface (Phase 1), the audience targeting or experiment configuration (Phases 2-3), and the content variants (Phase 3) into a deliverable unit. The campaign controls when and how personalized content is served to visitors.

**Decision points in this phase:**

>[!NOTE]
>**Decision: Campaign type** -- How should the campaign be triggered?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Scheduled campaign (always-on) | Personalization should run continuously for all qualifying visitors | Set start date with no end date for evergreen personalization. Audience evaluation happens at edge in real time. Most common for web personalization. |
| Scheduled campaign (time-bound) | Personalization is tied to a specific promotion period or seasonal event | Set explicit start and end dates. Campaign automatically deactivates at the end date. Good for promotional campaigns. |
| API-triggered campaign | Personalization delivery must be triggered by an external system event | Requires API integration. Less common for anonymous web personalization. Use when a backend system must control when personalization is active. |

**UI navigation:** [!DNL Journey Optimizer] > Campaigns > Create Campaign

**Key configuration details:**

- Select the web channel and the web surface configured in Phase 1
- Bind the target audience (for Option A) or configure experiment settings (for Option B) or embed the decision (for Option C)
- Set the campaign schedule (start date, end date, or always-on)
- Configure campaign-level frequency capping if applicable
- Review all configuration and activate the campaign

**Where options diverge:**

**For Option A (Rule-Based):**
Create one campaign per personalization rule, each targeting a different edge audience with its corresponding content variant. Alternatively, use a single campaign with conditional content rules that map audience membership to content variants within one campaign.

**For Option B (Experimentation):**
Create a single campaign with content experimentation enabled. The experiment configuration (variants, traffic allocation, success metric) was defined in Phase 3. Activate the campaign to start the experiment.

**For Option C (Decisioning):**
Create a campaign that embeds the decision policy configured in Phase 3. The campaign's content action references the decision scope, which triggers the Decisioning engine at the edge. Activate the campaign to begin decisioning-based content delivery.

**Experience League documentation:**

- [Create a campaign](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Get started with campaigns](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Deliver offers in messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Phase 5: Report and analyze performance

**Application function:** AJO: Reporting & Performance Analysis

Monitor personalization performance using AJO built-in reports and optionally extend analysis with CJA for deeper cross-channel insights. This phase covers accessing live and historical campaign reports, reviewing experiment results, and building custom analysis workspaces.

**Decision points in this phase:**

>[!NOTE]
>**Decision: Reporting depth** -- How deep should performance analysis go?

| Option | When to choose | Considerations |
| --- | --- | --- |
| AJO native reports only | Basic delivery and engagement metrics are sufficient | Provides impressions, clicks, CTR, and conversion metrics out of the box. Available immediately in the campaign UI. Limited customization. |
| AJO reports + CJA analysis | Deep funnel analysis, cohort comparison, or cross-channel impact measurement is needed | Requires CJA connection and data view linked to AJO datasets. Enables freeform analysis, custom calculated metrics, attribution modeling, and audience publishing. |

**UI navigation:** [!DNL Journey Optimizer] > Campaigns > Select campaign > View report

**Key configuration details:**

- Access the live report during active campaigns to monitor real-time delivery (refreshes every 60 seconds, shows last 24 hours)
- Access the historical (all time) report after campaign completion for comprehensive analysis (may take up to 2 hours to fully populate)
- For Option B (Experimentation): review the experiment report for treatment performance comparison, confidence intervals, and winner declaration
- For CJA analysis: ensure a CJA connection includes AJO experience event datasets and a data view is configured with web personalization metrics

**Where options diverge:**

**For Option A (Rule-Based):**
Review campaign reports for each audience segment to compare delivery and engagement metrics across personalized content variants. Use CJA to build a comparison workspace that measures the conversion impact of personalized vs. default content.

**For Option B (Experimentation):**
Review the experiment report for statistical confidence, treatment lift, and winner identification. Wait for the confidence threshold to be reached before declaring a winner. Apply winning content as the permanent variant (transitioning to Option A for ongoing delivery).

- **UI navigation:** Campaign > Content experiment > View report
- **Experience League:** [Content experiment report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

**For Option C (Decisioning):**
Review decisioning performance metrics including offer impression rates, selection frequency, and conversion attribution per content item. Analyze how ranking strategies are performing and whether fallback content is being served too frequently (indicating eligibility rules are too restrictive).

**Experience League documentation:**

- [Campaign live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Campaign global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Work with Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Statistical calculations in content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

## Implementation considerations

This section covers guardrails, common pitfalls, best practices, and trade-off decisions for this use case pattern.

### Guardrails and limits

Review the following guardrails before and during implementation.

- Edge segments are limited to simple attribute checks and segment membership -- no time-series queries or complex aggregations -- [Edge segmentation eligibility](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- Only one merge policy can be active on edge per sandbox -- [Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximum of 4,000 segment definitions per sandbox -- [Segmentation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximum of 500 active live campaigns per sandbox -- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum of 10 treatment variants per content experiment -- [Content experiment limits](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum of 10,000 approved personalized offers per sandbox (Option C) -- [Decision Management guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum of 30 placements per decision (Option C) -- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- AI ranking models require a minimum of 1,000 conversion events for training (Option C)
- [!DNL Edge Network] response time SLA: < 200ms for edge-evaluated segments
- Pseudonymous profile expiration: configurable from 14 to 365 days for ECID-only profiles
- Live reports refresh every 60 seconds and show the last 24 hours of data
- Historical reports may take up to 2 hours to fully populate after campaign completion

### Common pitfalls

Avoid the following common implementation mistakes.

- **[!DNL Web SDK] not sending behavioral signals to AEP:** Verify the datastream has the [!DNL Adobe Experience Platform] service enabled and the event dataset is correctly mapped. Without this, edge profiles are not populated and audience evaluation fails silently -- the visitor receives default content with no error indication.
- **Edge audience returning zero qualifications:** Edge segmentation has strict eligibility requirements. Time-series queries, aggregation functions, and multi-entity queries are not edge-eligible. Rewrite the segment rule expression using simple attribute comparisons or segment membership checks.
- **Merge policy not active on edge:** If the merge policy used by the audience segment does not have `isActiveOnEdge: true`, edge profile lookups will fail and personalization will not be delivered. Only one merge policy per sandbox can be active on edge -- verify no conflict exists.
- **Personalization flicker on page load:** The [!DNL Web SDK] `sendEvent` call that retrieves personalization propositions must execute before the page renders the target content area. Implement prehiding snippets or asynchronous rendering to prevent the default content from flashing before the personalized content loads.
- **Content not rendering on SPA route changes:** Single-page applications require explicit `sendEvent` calls with updated view information when the route changes. Without this, the [!DNL Edge Network] does not re-evaluate personalization for the new view.
- **Experiment not reaching statistical significance:** Insufficient traffic volume or too many treatment variants dilute the sample size per variant. Reduce the number of variants or increase the experiment duration. Do not stop experiments prematurely -- results may be misleading.
- **Decisioning returning only fallback content:** Check that personalized content items are approved, within their validity date range, and that eligibility rules match the anonymous visitor's edge profile attributes. Also verify capping limits have not been reached.

### Best practices

Follow these recommendations for a successful implementation.

- **Start simple, then iterate:** Begin with Option A (Rule-Based) for initial personalization, then use Option B (Experimentation) to validate assumptions and Option C (Decisioning) for advanced use cases. Each option builds on the foundational infrastructure.
- **Use prehiding for flicker prevention:** Implement the AEP prehiding snippet on pages where personalization will be delivered. This hides the target content area until the personalized content is ready to render, preventing visual flicker.
- **Design fallback content deliberately:** The default (non-personalized) content should be a high-quality experience on its own. Visitors who do not qualify for personalization -- or when the [!DNL Edge Network] response is delayed -- should not receive a degraded experience.
- **Validate edge eligibility before building audiences:** Before investing in audience rule development, confirm the segment rule expression is edge-eligible by reviewing the eligibility criteria in Experience League. Non-eligible expressions will silently fall back to batch or streaming evaluation with unacceptable latency for this pattern.
- **Monitor edge delivery performance:** Set up monitoring alerts for [!DNL Edge Network] response times and personalization delivery failures. Edge delivery issues are invisible to the visitor (they see default content) and may go undetected without proactive monitoring.
- **Configure pseudonymous profile expiration:** Set appropriate expiration periods for anonymous edge profiles to balance cross-session personalization (recognizing returning visitors) with privacy compliance and storage management.
- **Test with representative profiles:** When previewing personalized content, use test profiles that represent the actual anonymous visitor scenarios (no CRM data, limited behavioral history, various geographic locations and devices).

### Trade-off decisions

Consider the following trade-offs when planning your implementation.

>[!NOTE]
>**Trade-off: Personalization breadth vs. implementation complexity**
>
>More granular personalization (many audiences, many content variants) produces more relevant experiences but increases configuration complexity and content production overhead.
>
>- **Broad personalization favors:** Simplicity, faster time to market, lower content production cost. A small number of audiences and variants covers the majority of visitors with meaningful personalization.
>- **Granular personalization favors:** Maximum relevance, higher engagement lift, better conversion rates. Many audiences and variants address specific behavioral signals with tailored content.
>- **Recommendation:** Start with 3-5 high-impact personalization rules targeting the most common visitor segments (e.g., referral source, device type, geographic region). Measure the impact, then expand to more granular rules based on observed performance and business value.

>[!NOTE]
>**Trade-off: Rule-based determinism vs. AI-driven optimization**
>
>Rule-based approaches (Option A) give the business full control over which content each visitor sees. AI-ranked approaches (Option C) optimize content selection over time but reduce visibility into why specific content was selected.
>
>- **Rule-based favors:** Predictability, auditability, business control. Marketing teams know exactly which content each segment receives and can explain the logic to stakeholders.
>- **AI-driven favors:** Performance optimization, scalability, continuous improvement. The AI model discovers content-visitor affinities that human rule-writing might miss.
>- **Recommendation:** Use rule-based for high-stakes content decisions where brand consistency and stakeholder transparency are paramount. Use AI-ranked for large content catalogs where manual rule management becomes unwieldy and continuous optimization delivers measurable lift.

>[!NOTE]
>**Trade-off: Anonymous profile persistence vs. privacy compliance**
>
>Longer pseudonymous profile expiration enables better cross-session personalization (recognizing returning visitors, building behavioral context over time). Shorter expiration improves privacy compliance and reduces storage costs.
>
>- **Longer expiration favors:** Richer anonymous profiles, better returning visitor recognition, more data for personalization decisions. Set expiration to 90-365 days.
>- **Shorter expiration favors:** Privacy compliance (GDPR, CCPA), reduced storage costs, minimized risk of stale profile data. Set expiration to 14-30 days.
>- **Recommendation:** Align expiration with your organization's cookie consent policy and privacy requirements. For most implementations, 30-90 days provides a reasonable balance between personalization value and privacy compliance.

## Related documentation

The following Experience League resources provide additional detail on the capabilities used in this use case pattern.

**Web channel and code-based experiences**

- [Get started with web channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Create web experiences](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Code-based experience channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Code-based experience configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

**Audiences and segmentation**

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language reference](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

**Personalization and content**

- [Add personalization](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamic content](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Work with content templates](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Work with content fragments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

**Content experimentation**

- [Get started with content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Create a content experiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Content experiment report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Statistical calculations](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

**Decision Management**

- [Decision Management overview](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Create placements](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Create decision rules](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Create personalized offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Create fallback offers](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Create collections](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Create decisions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Ranking strategies](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Deliver offers in messages](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

**Campaigns**

- [Get started with campaigns](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Create a campaign](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

**[!DNL Web SDK] and data collection**

- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Install Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Tags overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)

**Identity and profile**

- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Identity namespaces overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Real-Time Customer Profile overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

**Data modeling**

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

**Reporting and analytics**

- [Campaign live report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Campaign global report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Work with Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

**Data governance and privacy**

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Consent and preferences field group](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

**Guardrails**

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identity Service guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
