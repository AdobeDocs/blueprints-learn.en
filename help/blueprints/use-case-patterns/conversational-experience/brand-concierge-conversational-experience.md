---
title: Brand Concierge Conversational Experience
description: Learn how to transform digital properties into AI-powered, brand-safe conversational experiences that guide customer discovery.
solution: Experience Platform, Real-Time Customer Data Platform
exl-id: a9545328-316d-446a-9308-18af61c58d1c
---
# Brand Concierge conversational experience

This guide provides a comprehensive implementation reference for AI-powered conversational experiences using [!DNL Adobe Brand Concierge], integrated with [!DNL Adobe Experience Platform] (AEP) and [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]). It is designed for solution architects, marketing technologists, and implementation engineers who need to deploy brand-safe conversational agents across digital properties.

It covers all viable approaches for deploying conversational experiences, from product advisory chatbots to full site navigation assistants, with guidance on when to choose each option. The plan addresses agent configuration, brand governance, content integration, deployment strategies, profile enrichment from conversation signals, and analytics optimization.

[!DNL Brand Concierge] enables brands to deploy intelligent conversational agents that understand brand voice, access approved product catalogs and content, deliver personalized recommendations based on real-time profile data, and capture intent and sentiment signals back into the unified customer profile. The result is a conversational experience that feels natural and on-brand while enriching the organization's understanding of each customer.

## Use case overview

Organizations increasingly seek to transform static digital experiences into dynamic, AI-powered conversations that guide customers through discovery, product selection, and purchase decisions. [!DNL Adobe Brand Concierge] addresses this by providing an orchestrated conversational AI layer that sits atop existing digital properties, powered by AEP Agent Orchestrator.

This pattern is distinct from traditional chatbot implementations because it is natively integrated with AEP's unified profile, uses brand governance guardrails to ensure every response aligns with brand standards, and feeds conversational signals back into the customer data platform for downstream personalization and activation.

The target audience includes digital experience teams, e-commerce managers, content strategists, and marketing technologists who need to deploy intelligent conversational experiences that drive engagement, conversion, and profile enrichment.

## Key business objectives

The following business objectives are supported by this use case pattern.

### Deliver personalized customer experiences

Tailor content, offers, and messaging to individual preferences, behaviors, and lifecycle stage.

**KPIs:** Engagement, Conversion Rates, Customer Satisfaction (CSAT)

[Learn more about delivering personalized customer experiences](/help/blueprints/business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

### Improve customer engagement

Increase interaction frequency and depth across all digital and physical touchpoints.

**KPIs:** Engagement, Time On (web) Page, Open Rates

[Learn more about improving customer engagement](/help/blueprints/business-objectives/qualification-sales-b2b/improve-customer-engagement.md)

### Increase conversion rates

Improve the percentage of visitors and prospects who complete desired actions such as purchases, sign-ups, or form submissions.

**KPIs:** Conversion Rates, Lead Conversion, Cost Per Lead

[Learn more about increasing conversion rates](/help/blueprints/business-objectives/revenue-monetization/increase-conversion-rates.md)

### Acquire new customers

Expand the customer base through targeted acquisition campaigns, lookalike audiences, and paid media optimization.

**KPIs:** Upsell/Cross Sell %, Incremental Revenue, Customer Lifetime Value

[Learn more about acquiring new customers](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

## Example tactical use cases

The following scenarios illustrate how this pattern can be applied in practice.

- **Product discovery assistant** -- Deploy a conversational agent on product listing pages that asks qualifying questions and narrows product recommendations based on customer needs, preferences, and budget
- **Guided comparison advisor** -- Help customers compare products side-by-side through natural dialogue, highlighting differences relevant to their stated priorities
- **Size and fit concierge** -- Guide apparel or footwear shoppers through size selection using conversational Q&A, reducing returns and increasing purchase confidence
- **Subscription or plan selector** -- Walk customers through service tier or subscription plan options with personalized recommendations based on usage patterns and stated needs
- **Site navigation assistant** -- Help visitors find relevant content, support resources, or product categories based on their stated intent, reducing bounce rates on complex sites
- **Pre-purchase consultation** -- Provide high-consideration purchase guidance (for example, electronics, financial products, insurance) through multi-turn conversations that build toward a recommendation
- **Loyalty program concierge** -- Help loyalty members discover rewards, understand tier benefits, and find redemption opportunities through conversational interaction
- **Re-engagement conversation** -- Initiate proactive conversational outreach to returning visitors based on previous browse history or abandoned cart items
- **Live agent escalation with context** -- Seamlessly hand off complex inquiries to live sales or support agents while preserving full conversation context and customer profile data
- **Post-purchase support and upsell** -- Engage customers after purchase with setup assistance, complementary product suggestions, and satisfaction check-ins through conversational channels

## Key performance indicators

The following KPIs help measure the success of this use case pattern.

| KPI | Description | Measurement approach |
| --- | --- | --- |
| Conversation Engagement Rate | Percentage of visitors who initiate and sustain a conversation | Conversations started / eligible page views |
| Conversation Completion Rate | Percentage of conversations that reach a meaningful resolution | Completed conversations / conversations started |
| Conversational Conversion Rate | Percentage of conversations that lead to a desired action (purchase, sign-up, lead form) | Conversions from conversation / total conversations |
| Average Conversation Depth | Number of turns per conversation, indicating engagement quality | Average message count per session |
| Customer Satisfaction (CSAT) | Post-conversation satisfaction score from in-experience feedback | Survey responses or thumbs-up/down ratings |
| Recommendation Acceptance Rate | Percentage of product recommendations accepted or clicked | Recommendations acted on / recommendations served |
| Live Agent Handoff Rate | Percentage of conversations escalated to live agents | Handoffs / total conversations |
| Profile Enrichment Rate | Percentage of conversations that yield new intent or preference signals | Profiles enriched / total conversations |
| Revenue Influenced by Conversation | Revenue from purchases where a [!DNL Brand Concierge] conversation preceded the conversion | Attribution analysis on conversation-to-purchase journeys |
| Time to Resolution | Average duration from conversation start to resolution or handoff | Timestamp analysis across conversation events |

## Use case pattern

**Brand Concierge conversational experience**

Transform digital properties into AI-powered, brand-safe conversational experiences that guide customer discovery through natural dialogue, enrich profiles with intent and sentiment signals, and deliver personalized product recommendations.

**Function chain:** Agent Configuration > Brand Governance Setup > Content Integration > Conversational Experience Deployment > Profile Enrichment > Analytics & Optimization

## Applications

The following applications are used to implement this use case pattern.

- **[!DNL Brand Concierge]** -- AI-powered conversational experience application providing the agent orchestrator, Product Advisor Agent, Site Advisory Agent, brand governance, and conversational analytics
- **[!DNL Adobe Experience Platform] (AEP)** -- Unified data foundation providing XDM schemas, identity resolution, real-time customer profiles, and data collection infrastructure for conversational signals
- **[!DNL Real-Time CDP] ([!DNL RT-CDP])** -- Customer data platform providing real-time profile lookup for personalized conversations, audience segmentation from conversational signals, and profile enrichment with intent and sentiment data

## Foundational functions

The following foundational capabilities must be in place for this use case pattern. For each function, the status indicates whether it is typically required, assumed to be pre-configured, or not applicable.

| Foundational function | Status | What must be in place | Experience League reference |
| --- | --- | --- | --- |
| Administration & Governance | Required | Sandbox provisioned with [!DNL Brand Concierge] entitlement enabled; roles configured for conversational experience administrators, content managers, and analytics users; ABAC policies in place for conversational data containing PII or sensitive customer signals | [Access control overview](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Data Modeling & Preparation | Required | XDM schemas for conversational events (ExperienceEvent class with conversation-specific field groups capturing intent, sentiment, product interactions, and handoff events); profile schema extended with conversational preference and intent attributes; product catalog lookup schema for grounding recommendations | [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Data Sources & Collection | Required | [!DNL Web SDK] or [!DNL Mobile SDK] configured with datastreams routing conversational event data to AEP datasets; [!DNL Edge Network] integration for real-time event capture during conversations; product catalog data ingested via source connectors or batch ingestion | [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home) |
| Identity & Profile Configuration | Required | Identity namespaces configured for visitor identification (ECID for anonymous, CRM ID or email for authenticated); merge policy configured with edge activation for real-time profile lookup during conversations; identity linking rules for cross-device conversation continuity | [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| Audience Definition & Segmentation | Assumed in Place | Audiences not required for core conversational deployment but needed for personalized conversation strategies (for example, high-value customer segments receive different conversation flows); streaming or edge evaluation recommended for real-time conversation personalization | [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## Supporting functions

The following capabilities augment this use case pattern but are not required for core execution.

| Supporting function | Status | Why it matters | Experience League reference |
| --- | --- | --- | --- |
| Computed / Derived Attribute Creation | Recommended | Aggregate conversational signals into profile-level attributes (for example, total conversations, dominant product interests, average sentiment score) for use in downstream segmentation and personalization | [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Recommended | Configure retention policies for conversational event data, manage consent for conversation recording and profiling, and support privacy deletion requests for conversation transcripts | [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Data Usage Labeling & Enforcement | Recommended | Label conversational data fields containing PII, sentiment, or intent signals; enforce governance policies preventing sensitive conversational data from reaching unauthorized destinations | [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Monitoring & Observability | Recommended | Monitor conversational event ingestion pipelines, track profile enrichment success rates, and alert on data flow failures that could affect conversation personalization quality | [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting & Analysis | Included | Analyze conversation performance, customer feedback, conversion attribution, and agent effectiveness using [!DNL Brand Concierge] built-in analytics and [!DNL CJA] for cross-channel conversation impact analysis | [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Application functions

This plan exercises the following functions from the Application Function Catalog. Functions are mapped to implementation phases rather than numbered steps.

### [!DNL Brand Concierge]

| Function | Implementation phase | Description |
| --- | --- | --- |
| Agent Configuration | Phase 1: Agent Configuration | Configure the [!DNL Brand Concierge] agent orchestrator with agent specializations (Product Advisor, Site Advisory) and base behavior settings |
| Brand Governance Setup | Phase 2: Brand Governance Setup | Define brand voice, tone, messaging guardrails, approved content boundaries, and prohibited topics that shape all conversational interactions |
| Content Integration | Phase 3: Content Integration | Connect brand-approved content sources including AEM content, product catalogs, knowledge bases, and other trusted data for grounding responses |
| Product Advisor Configuration | Phase 3: Content Integration | Configure the Product Advisor Agent for personalized product recommendations, guided comparisons, and brand-aligned response delivery |
| Site Advisory Configuration | Phase 3: Content Integration | Configure the Site Advisory Agent to enhance navigation by adapting interactions based on visitor behavior and intent signals |
| Conversational Experience Deployment | Phase 4: Conversational Experience Deployment | Deploy conversational experiences across supported channels (web, mobile app, custom SDK) with text and voice interaction support |
| Low-Code Flow Management | Phase 4: Conversational Experience Deployment | Enable marketing teams to update conversational tone, flows, and content using low-code configuration tools |
| Conversational Profile Enrichment | Phase 5: Profile Enrichment | Enrich AEP customer profiles with intent, sentiment, product affinity, and behavioral signals captured during conversations |
| Conversational Analytics | Phase 6: Analytics & Optimization | Monitor engagement metrics, customer feedback, conversion data, and conversation quality via built-in analytics dashboards |
| Live Agent Handoff | Phase 4: Conversational Experience Deployment | Configure seamless handoff to live sales or support agents while preserving full conversation context |

### [!DNL Real-Time CDP]

| Function | Implementation phase | Description |
| --- | --- | --- |
| Real-Time Profile Lookup | Phase 4: Conversational Experience Deployment | Access real-time customer profile attributes and segment memberships to personalize conversational responses based on known customer data |
| Profile Enrichment | Phase 5: Profile Enrichment | Enrich profiles with computed attributes derived from conversational behavioral events (intent scores, sentiment trends, product affinity) |
| Audience Evaluation | Phase 5: Profile Enrichment | Evaluate audience membership based on conversational signals to enable downstream targeting of engaged conversational segments |

## Prerequisites

The following items must be in place before implementation begins.

- [!DNL Adobe Brand Concierge] entitlement is active for the organization
- AEP and [!DNL RT-CDP] licenses are provisioned with sufficient profile and event volume entitlements
- Brand guidelines document available defining voice, tone, approved messaging, and prohibited topics
- Product catalog or content repository prepared for integration (AEM assets, PIM data, or structured product feed)
- Web properties identified for conversational experience deployment with technical access for SDK integration
- Live agent infrastructure available if handoff is required (contact center platform, CRM integration)
- Consent management framework in place for conversational data capture and profiling
- [!DNL Web SDK] or [!DNL Mobile SDK] already deployed on target properties (or planned for concurrent deployment)
- Stakeholder alignment on conversation scope (product advisory only, site navigation, or both)
- Privacy and legal review completed for AI-powered conversational data capture and usage

## Implementation options

The following sections describe different approaches for implementing this use case pattern.

### Option A: Product Advisor deployment

**Best for:** E-commerce and retail organizations focused on guided product discovery, comparison, and recommendation experiences that drive conversion and average order value.

**How it works:**

The Product Advisor Agent is configured as the primary conversational specialization. It connects to the product catalog, understands product attributes and relationships, and guides customers through natural dialogue to arrive at personalized recommendations. The agent uses brand governance guardrails to ensure recommendations align with business priorities (for example, promoting in-stock items, highlighting margin-favorable products).

Product Advisor integrates with the real-time customer profile to access purchase history, browse behavior, and preference data, enabling recommendations that account for what the customer already owns, has previously considered, or is likely to need based on their profile. Conversations are captured as experience events and intent signals flow back into the profile for downstream use.

**Key considerations:**

- Requires a well-structured product catalog with rich attribute data for effective recommendations
- Product data must be kept current to avoid recommending out-of-stock or discontinued items
- Brand governance must define how the agent handles competitive product mentions and price comparisons

**Advantages:**

- Directly drives measurable revenue impact through guided purchase conversion
- Reduces product return rates through better-informed purchase decisions
- Captures high-value product affinity and intent signals for downstream personalization
- Natural extension of existing e-commerce experiences

**Limitations:**

- Requires ongoing product catalog maintenance and synchronization
- Limited to product-centric conversations; site navigation questions may go unaddressed
- Effectiveness depends on catalog data quality and completeness

**Experience League:**

- [Brand Concierge overview](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge product advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)

### Option B: Site Advisory deployment

**Best for:** Organizations with complex digital properties (media, financial services, healthcare, technology) where visitors need navigation assistance to find relevant content, resources, or self-service tools.

**How it works:**

The Site Advisory Agent is configured as the primary conversational specialization. It indexes the site content structure, understands page relationships and content categories, and adapts its guidance based on visitor behavior signals and stated intent. When a visitor engages, the agent interprets their needs and directs them to the most relevant content, tools, or resources.

Site Advisory uses real-time behavioral signals (current page, referral source, navigation path) combined with profile data (previous visits, content preferences, customer tier) to provide contextually relevant navigation assistance. This is particularly valuable on sites with deep content hierarchies, multiple product lines, or complex self-service workflows.

**Key considerations:**

- Requires comprehensive content indexing and regular re-crawling as site content changes
- Most effective on sites with significant content breadth where visitors commonly struggle to find what they need
- Brand governance should define scope boundaries (which site areas the agent can navigate to)

**Advantages:**

- Reduces bounce rates and improves content discoverability on complex sites
- Captures navigation intent signals that reveal content gaps and user experience issues
- Lower implementation complexity than Product Advisor (no product catalog integration required)
- Provides analytics insights into what visitors are looking for but cannot find

**Limitations:**

- Less directly tied to revenue conversion than product-focused conversations
- Requires content to be well-structured and regularly updated for accurate guidance
- May need frequent retraining as site structure evolves

**Experience League:**

- [Brand Concierge overview](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge site advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)

### Option C: Combined Product Advisor + Site Advisory deployment

**Best for:** Organizations that want a comprehensive conversational experience covering both product discovery and site navigation, typically large retail or B2C brands with extensive digital properties and diverse visitor intents.

**How it works:**

Both the Product Advisor Agent and Site Advisory Agent are configured within the [!DNL Brand Concierge] orchestrator. The agent orchestrator uses intent detection to route conversations to the appropriate specialization -- product-related queries go to Product Advisor while navigation and content-finding queries go to Site Advisory. The orchestrator manages seamless transitions between specializations within a single conversation.

This approach provides the most complete conversational experience, handling the full range of visitor needs from "Help me find a product" to "Where can I check my order status?" Brand governance guardrails apply uniformly across both specializations, ensuring consistent brand voice regardless of conversation topic.

**Key considerations:**

- Higher implementation complexity requiring both product catalog and content integration
- Intent routing between specializations must be well-tuned to avoid misdirected conversations
- Brand governance setup is more extensive to cover both product and navigation contexts

**Advantages:**

- Provides the most comprehensive conversational experience for visitors
- Single entry point handles diverse visitor intents without requiring separate interfaces
- Cross-specialization conversations (for example, product question that leads to support navigation) handled naturally
- Richest profile enrichment from diverse conversation signals

**Limitations:**

- Highest implementation effort and ongoing maintenance
- Requires coordination between product catalog and content teams
- More complex testing and quality assurance requirements
- Brand governance configuration is more involved

**Experience League:**

- [Brand Concierge overview](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)

### Option comparison

| Criteria | Option A: Product Advisor | Option B: Site Advisory | Option C: Combined |
| --- | --- | --- | --- |
| Best for | E-commerce, product-driven conversion | Content-heavy sites, self-service navigation | Full-scope digital experience |
| Complexity | Medium | Low-Medium | High |
| Time to value | 4-6 weeks | 3-5 weeks | 6-10 weeks |
| Revenue impact | High (direct conversion influence) | Medium (indirect via engagement) | Highest (both conversion and engagement) |
| Content requirements | Product catalog with rich attributes | Site content index | Both product catalog and content index |
| Profile enrichment | Product affinity, purchase intent | Navigation intent, content preferences | Full signal spectrum |
| Maintenance effort | Product catalog sync | Content re-indexing | Both ongoing |

### Choose the right option

Start by assessing your primary business objective and digital property characteristics:

1. **If your primary goal is driving product conversion** and your digital property is commerce-focused, choose **Option A (Product Advisor)**. This is the most common starting point for retail and e-commerce brands.

2. **If your primary goal is improving content discoverability** and your site has deep content hierarchies or complex self-service workflows, choose **Option B (Site Advisory)**. This is ideal for media, financial services, healthcare, and technology companies.

3. **If you need comprehensive coverage** and have both product commerce and content navigation needs, choose **Option C (Combined)**. Consider starting with one specialization and adding the second after the first is stable and optimized.

A phased approach is recommended for most organizations: deploy one specialization first, validate performance and gather learnings, then expand to the combined deployment.

## Implementation phases

The following phases outline the recommended implementation sequence.

### Phase 1: Agent configuration

**Application function:** [!DNL Brand Concierge]: Agent Configuration

Configure the core [!DNL Brand Concierge] agent orchestrator, including selecting agent specializations (Product Advisor, Site Advisory, or both), configuring base agent behavior, and establishing the connection between [!DNL Brand Concierge] and AEP for profile access and event capture.

#### Decision: Agent specialization selection

Determine which agent specializations should be activated for this deployment.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Product Advisor only | Commerce-focused deployment targeting product discovery and conversion | Requires product catalog integration; fastest path to revenue impact |
| Site Advisory only | Content and navigation-focused deployment | Lower integration complexity; best for non-commerce sites |
| Both specializations | Comprehensive conversational coverage across product and content | Higher complexity; consider phased rollout starting with one |

#### Decision: Conversation initiation model

Determine how conversations should begin on the digital property.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Visitor-initiated (passive) | Default approach where the chat widget is available but does not proactively engage | Lower interruption risk; relies on visitor awareness of the chat option |
| Proactive engagement (triggered) | Agent initiates conversation based on behavioral signals (for example, extended dwell time, repeated page visits, cart hesitation) | Higher engagement rates but risks visitor annoyance if triggers are too aggressive; requires behavioral trigger tuning |
| Hybrid (passive with contextual prompts) | Chat widget is passive but displays contextual prompts based on page content or visitor behavior | Balanced approach; prompts guide without forcing engagement |

#### Configure the agent

**UI navigation:** [!DNL Experience Platform] > AI Assistant > [!DNL Brand Concierge] > Agent Configuration

Key configuration details:

- Define the agent name and description that will appear in the conversational interface
- Select which AEP sandbox contains the customer profile and event data the agent should access
- Configure the agent orchestrator to route queries between specializations based on intent detection
- Set conversation session parameters (timeout duration, maximum conversation length, concurrent session limits)
- Enable real-time profile lookup integration so the agent can access visitor profile data during conversations

**Where options diverge:**

**For Option A (Product Advisor):**
Enable the Product Advisor specialization and configure its connection to the product catalog data source. Set product recommendation parameters including maximum recommendations per response, product attribute display preferences, and comparison handling rules.

**For Option B (Site Advisory):**
Enable the Site Advisory specialization and configure its connection to the site content index. Set navigation parameters including content scope boundaries, page category handling, and deep-link generation preferences.

**For Option C (Combined):**
Enable both specializations and configure the orchestrator's intent routing logic. Define routing rules that determine when a conversation should be handled by Product Advisor versus Site Advisory, and how transitions between specializations should be managed within a single conversation.

**Experience League documentation:**

- [Brand Concierge overview](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [AI Assistant overview](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/home)
- [AEP Agent Orchestrator](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)

### Phase 2: Brand governance setup

**Application function:** [!DNL Brand Concierge]: Brand Governance Setup

Configure the brand governance guardrails that shape all conversational interactions. This includes brand voice and tone definitions, approved content boundaries, prohibited topics, response style guidelines, and escalation rules. Brand governance ensures every AI-generated response aligns with brand standards.

#### Decision: Governance strictness level

Determine how tightly the brand governance guardrails should constrain conversational responses.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Strict governance | Highly regulated industries (financial services, healthcare, insurance) or premium brands requiring precise tone control | Limits conversational flexibility; may result in more frequent "I cannot help with that" responses; highest brand safety |
| Moderate governance | Most consumer brands where brand voice consistency matters but some conversational flexibility is acceptable | Good balance of brand safety and conversational naturalness; recommended starting point for most implementations |
| Flexible governance | Casual or lifestyle brands where conversational personality and engagement are prioritized | Most natural conversational feel; requires more ongoing monitoring for off-brand responses |

#### Decision: Off-topic handling strategy

Determine how the agent should handle questions outside its configured scope.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Redirect to scope | Agent acknowledges the question and redirects to topics it can help with | Maintains engagement but may frustrate visitors with legitimate off-topic needs |
| Handoff to live agent | Agent offers to connect the visitor with a human agent for off-topic questions | Best customer experience but requires live agent infrastructure and staffing |
| Graceful decline with resources | Agent explains it cannot help with that topic and provides links to relevant resources or support channels | Low-friction fallback; does not require live agent availability |

#### Configure brand governance

**UI navigation:** [!DNL Experience Platform] > AI Assistant > [!DNL Brand Concierge] > Brand Governance

Key configuration details:

- Define brand attributes: brand name, tagline, mission, values, and personality traits that inform conversational tone
- Set tone parameters: formality level, humor tolerance, empathy level, and assertiveness for product recommendations
- Configure approved content boundaries: topics the agent is authorized to discuss and topics that are explicitly prohibited
- Define response format guidelines: maximum response length, use of lists versus prose, emoji policy, and link formatting
- Set escalation triggers: conditions that should automatically route a conversation to a live agent (for example, complaint detection, repeated dissatisfaction signals, high-value customer identification)
- Configure competitive mention handling: how the agent should respond when visitors ask about competitor products
- Define disclaimer and legal notice requirements: mandatory disclosures for regulated industries

**Experience League documentation:**

- [Brand Concierge brand governance](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [AI Assistant operational insights](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/home)

### Phase 3: Content integration

**Application function:** [!DNL Brand Concierge]: Content Integration, Product Advisor Configuration, Site Advisory Configuration

Configure the content sources that ground conversational responses in accurate, brand-approved information. This includes product catalog integration, AEM content connections, knowledge base imports, and content refresh schedules.

#### Decision: Product catalog integration method

Determine how product data should be provided to the Product Advisor Agent. (Option A and C only)

| Option | When to choose | Considerations |
| --- | --- | --- |
| AEP dataset integration | Product catalog is already ingested into AEP as a lookup dataset via source connectors | Leverages existing data infrastructure; keeps product data synchronized with profile data; requires foundational data modeling and collection to include product catalog |
| Direct feed integration | Product catalog exists in a PIM or commerce platform that can provide a structured feed | May offer more real-time inventory and pricing data; requires feed configuration and scheduling |
| AEM Content integration | Product content is managed in AEM and should serve as the authoritative product data source | Best for brands where AEM is the content hub; ensures consistency between web content and conversational responses |

#### Decision: Content refresh frequency

Determine how often the agent's content knowledge base should be updated.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Real-time / near real-time | Product availability, pricing, or content changes frequently (for example, flash sales, inventory-sensitive retail) | Highest accuracy but higher infrastructure load; critical for inventory-sensitive recommendations |
| Daily refresh | Content changes are planned and scheduled (for example, editorial calendars, weekly promotions) | Good balance of accuracy and performance; suitable for most implementations |
| On-demand refresh | Content changes are infrequent and can be triggered manually when updates occur | Lowest overhead; suitable for static product catalogs or stable content sites |

#### Configure content sources

**UI navigation:** [!DNL Experience Platform] > AI Assistant > [!DNL Brand Concierge] > Content Sources

Key configuration details:

- Connect product catalog data sources with field mapping for product name, description, attributes, pricing, availability, images, and category hierarchy
- Configure content indexing for site pages, knowledge base articles, FAQ content, and support documentation
- Set content scope boundaries defining which content the agent can reference and which is excluded
- Configure content fallback behavior when the agent cannot find relevant content to answer a question
- Set up content quality rules: minimum content confidence threshold for inclusion in responses, citation requirements, and source attribution

**Where options diverge:**

**For Option A (Product Advisor):**
Focus on product catalog integration with rich product attribute mapping. Configure the Product Advisor Agent's recommendation logic including how many products to suggest, how to handle out-of-stock items, how to present product comparisons, and how to incorporate customer profile data (purchase history, browse behavior) into recommendation ranking.

**For Option B (Site Advisory):**
Focus on site content indexing with page hierarchy mapping. Configure the Site Advisory Agent's navigation logic including how to interpret visitor intent, which content categories to prioritize, how to handle ambiguous navigation requests, and how to adapt suggestions based on the visitor's current page context and session behavior.

**For Option C (Combined):**
Configure both product catalog and site content sources. Ensure the content routing logic correctly assigns content to the appropriate specialization and that cross-references between product content and site navigation content are properly mapped.

**Experience League documentation:**

- [Brand Concierge content configuration](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge product advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)
- [Brand Concierge site advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)
- [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)

### Phase 4: Conversational experience deployment

**Application function:** [!DNL Brand Concierge]: Conversational Experience Deployment, Low-Code Flow Management, Live Agent Handoff; [!DNL RT-CDP]: Real-Time Profile Lookup

Deploy the conversational experience on target digital properties, including channel configuration, widget customization, profile lookup integration for personalization, live agent handoff rules, and low-code tools for ongoing content management.

#### Decision: Deployment channel

Determine which channel(s) the conversational experience should be deployed to.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Web (embedded widget) | Primary web property is the main customer touchpoint | Most common starting point; requires [!DNL Web SDK] integration; supports both anonymous and authenticated visitors |
| Mobile app (SDK integration) | Mobile app is a significant customer engagement channel | Requires [!DNL Mobile SDK] integration; consider screen real estate constraints for conversation UI |
| Custom SDK deployment | Conversational experience needs to be embedded in a custom application, kiosk, or non-standard digital property | Maximum flexibility; requires more development effort; suitable for in-store kiosks or proprietary platforms |
| Multi-channel deployment | Conversational experience needed across web, mobile, and other channels simultaneously | Highest reach; requires consistent brand governance across channels; conversation context should persist across channels when possible |

#### Decision: Personalization depth for conversations

Determine how much customer profile data the agent should use to personalize conversations.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Anonymous-only (session context) | Privacy-first approach or when most visitors are unidentified | Uses only in-session behavioral signals; no profile lookup required; suitable for anonymous product discovery |
| Profile-aware (authenticated visitors) | Visitors are typically logged in and personalized recommendations based on history add value | Requires real-time profile lookup via [!DNL RT-CDP]; significantly better recommendation quality for known customers |
| Progressive personalization | Blend of anonymous and authenticated with progressive profile building during conversation | Starts with session context; enriches as visitor provides information or authenticates; balances privacy and personalization |

#### Decision: Live agent handoff configuration

Determine whether conversations should be escalable to live human agents.

| Option | When to choose | Considerations |
| --- | --- | --- |
| No handoff (self-service only) | AI agent can handle all expected conversation types, or live agents are not available | Simplest deployment; may frustrate visitors with complex needs; suitable for low-risk, product-browsing scenarios |
| Rule-based handoff | Specific triggers should escalate to live agents (for example, complaint detection, high-value customer, complex inquiry) | Predictable escalation behavior; requires defining escalation rules and triggers; needs live agent platform integration |
| Visitor-requested handoff | Visitors can request a live agent at any point in the conversation | Best customer experience; requires always-available agent staffing or queue management; conversation context must transfer |

#### Deploy the conversational experience

**UI navigation:** [!DNL Experience Platform] > AI Assistant > [!DNL Brand Concierge] > Deployment

Key configuration details:

- Configure the conversational widget appearance: position, color scheme, avatar, welcome message, and interaction style (text, voice, or both)
- Integrate with [!DNL Web SDK] or [!DNL Mobile SDK] for event capture and profile resolution
- Configure real-time profile lookup to access customer attributes, segment memberships, and recent activity during conversations
- Set up live agent handoff integration with the contact center platform, including context transfer protocol, queue routing, and agent notification
- Enable low-code flow management tools for marketing teams to update conversation starters, promotional messaging, seasonal content, and flow variations without developer involvement
- Configure conversation session persistence rules: how long conversation history is retained, whether conversations can resume across sessions, and cross-device conversation continuity

**Experience League documentation:**

- [Brand Concierge deployment](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Edge Network Server API overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Profile API entities endpoint](https://experienceleague.adobe.com/en/docs/experience-platform/profile/api/entities)
- [Real-Time Customer Profile overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Phase 5: Profile enrichment

**Application function:** [!DNL Brand Concierge]: Conversational Profile Enrichment; [!DNL RT-CDP]: Profile Enrichment, Audience Evaluation

Configure the capture and enrichment pipeline that feeds conversational signals back into the AEP unified customer profile. This includes mapping conversation events to XDM, extracting intent and sentiment signals, creating computed attributes from conversational data, and building audiences based on conversational behaviors.

#### Decision: Conversational signal capture scope

Determine which conversational signals should be captured and written to the customer profile.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Core engagement signals only | Minimal profile enrichment; capture conversation start, end, duration, and completion status | Lowest data volume; sufficient for basic analytics; limited personalization value |
| Intent and preference signals | Capture inferred product interests, stated preferences, and topic categories discussed | High personalization value; moderate data volume; most commonly recommended |
| Full signal capture | Capture intent, sentiment, product interactions, recommendation responses, handoff events, and feedback scores | Richest profile enrichment; highest data volume; enables advanced analytics and ML-driven personalization |

#### Decision: Audience creation from conversational data

Determine whether audiences should be created based on conversational behaviors for downstream activation.

| Option | When to choose | Considerations |
| --- | --- | --- |
| No conversational audiences | Conversational data used for analytics only, not for audience activation | Simplest approach; suitable if conversations are supplementary to existing engagement channels |
| Intent-based audiences | Create audiences based on stated product interests or navigation intents from conversations | Enables retargeting visitors who expressed interest but did not convert; high-value for commerce |
| Behavioral audiences | Create audiences based on conversation engagement patterns (for example, high engagement, abandoned conversation, repeated visits) | Enables conversation-informed journey orchestration and cross-channel follow-up |

#### Configure profile enrichment

**UI navigation:** [!DNL Experience Platform] > Customer > Profiles > Computed attributes (for derived signals); Customer > Audiences > Create audience (for conversational audiences)

Key configuration details:

- Map conversational events to XDM ExperienceEvent schema fields capturing conversation ID, message count, topics discussed, products referenced, sentiment scores, and resolution status
- Configure [!DNL Brand Concierge] profile enrichment to write intent and preference signals to the unified profile
- Create computed attributes from conversational event data: total conversations (lifetime), dominant product category interest (30 days), average sentiment score (90 days), conversation-to-purchase conversion rate
- Define streaming or batch audience segments based on conversational signals for downstream activation (for example, "Visitors who discussed Product Category X in the last 7 days but did not purchase")
- Validate profile enrichment by looking up sample profiles to confirm conversational attributes are populated

**Experience League documentation:**

- [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Computed attributes UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Real-Time Customer Profile overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Phase 6: Analytics and optimization

**Application function:** [!DNL Brand Concierge]: Conversational Analytics

Set up analytics dashboards and reporting for measuring conversational experience performance, identifying optimization opportunities, and tracking KPIs. This includes [!DNL Brand Concierge] built-in analytics, optional [!DNL CJA] integration for cross-channel conversation impact analysis, and ongoing optimization workflows.

#### Decision: Analytics depth

Determine what level of conversational analytics is needed.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Built-in [!DNL Brand Concierge] analytics | Standard reporting on conversation volume, engagement, satisfaction, and conversion is sufficient | Fastest to activate; covers core KPIs; limited cross-channel correlation |
| [!DNL Brand Concierge] + [!DNL CJA] integration | Cross-channel analysis needed to understand how conversations influence broader customer journeys | Requires [!DNL CJA] connection and data view setup; enables attribution analysis across conversation and other channels |
| Full analytics stack ([!DNL Brand Concierge] + [!DNL CJA] + custom dashboards) | Executive-level reporting, advanced attribution modeling, and custom audience creation from analytics insights | Highest analytical capability; requires [!DNL CJA] expertise; enables data-driven conversation optimization |

#### Configure analytics and optimization

**UI navigation:** [!DNL Experience Platform] > AI Assistant > [!DNL Brand Concierge] > Analytics; [!DNL Analytics Platform] > Workspace (for [!DNL CJA])

Key configuration details:

- Review [!DNL Brand Concierge] built-in analytics dashboards: conversation volume trends, engagement rate, completion rate, CSAT scores, recommendation acceptance rate, and handoff frequency
- Configure [!DNL CJA] connection to include conversational event datasets for cross-channel analysis (if choosing [!DNL CJA] integration)
- Build [!DNL CJA] workspace analysis for conversation-to-conversion attribution, identifying which conversation topics correlate with purchase behavior
- Set up conversation quality monitoring: track topics where the agent struggles, common unanswered questions, and sentiment trends over time
- Define optimization workflows: regular review cadence for brand governance updates, content refresh triggers, and conversation flow improvements based on analytics insights

**Experience League documentation:**

- [Brand Concierge analytics](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [CJA Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Create or edit a CJA connection](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Create or edit a CJA data view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)

## Implementation considerations

The following sections cover guardrails, common pitfalls, best practices, and trade-off decisions to keep in mind during implementation.

### Guardrails and limits

- [!DNL Brand Concierge] conversational experiences are subject to AI response generation rate limits; concurrent conversation capacity depends on entitlement tier
- Real-time profile lookup during conversations is subject to Profile API rate limits per sandbox -- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Conversational event data ingestion follows standard AEP streaming ingestion limits -- [Ingestion guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- Product catalog size and content index volume are subject to [!DNL Brand Concierge] content integration limits
- Maximum of 25 computed attributes per sandbox applies to conversational signal aggregations -- [Computed attributes guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- Maximum of 4,000 segment definitions per sandbox applies to conversational audiences -- [Segmentation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### Common pitfalls

- **Insufficient brand governance definition:** Deploying without thorough brand governance configuration results in off-brand responses that damage customer trust. Invest significant time in Phase 2 defining tone, boundaries, and escalation rules before deployment.
- **Stale product catalog data:** Product Advisor recommendations based on outdated inventory, pricing, or availability data frustrate customers and erode confidence. Establish automated content refresh pipelines with validation checks.
- **Overaggressive proactive engagement triggers:** Setting behavioral triggers too aggressively (for example, triggering conversation after 3 seconds on page) annoys visitors and increases bounce rates. Start with conservative triggers and tune based on engagement data.
- **Neglecting anonymous visitor experience:** Focusing personalization only on authenticated visitors ignores the majority of traffic. Design conversation flows that provide value to anonymous visitors using in-session behavioral signals.
- **Skipping profile enrichment configuration:** Deploying conversations without capturing signals back to the profile wastes valuable intent and preference data. Configure profile enrichment in parallel with deployment, not as an afterthought.
- **Ignoring live agent handoff experience:** Poor handoff experiences (lost context, repeated questions, long wait times) damage the overall conversational experience more than not offering handoff at all. Test the full handoff flow end-to-end before launch.

### Best practices

- Start with a single agent specialization (Product Advisor or Site Advisory) and expand after establishing baseline performance.
- Conduct brand governance workshops with marketing, legal, and customer experience stakeholders before configuring guardrails.
- Use progressive personalization: start conversations with session-context-based responses and deepen personalization as the visitor provides information or authenticates.
- Implement A/B testing of conversation starters, prompts, and recommendation presentation formats using the low-code flow management tools.
- Schedule regular (weekly or biweekly) review of conversation analytics to identify content gaps, common failure points, and optimization opportunities.
- Create a feedback loop between conversational analytics and brand governance updates -- use conversation data to refine tone, add new approved topics, and adjust escalation rules.
- Monitor conversation sentiment trends as an early warning system for product issues, site problems, or brand perception shifts.
- Design conversation flows that naturally capture profile-enriching signals without making the interaction feel like an interrogation.

### Trade-off decisions

>[!NOTE]
>The following trade-off decisions should be evaluated based on your organization's specific requirements and constraints.

**Conversation personalization depth vs. privacy simplicity**

Deeper profile integration enables more personalized and effective conversations, but increases data collection complexity, consent requirements, and privacy compliance burden.

- **Deep personalization favors:** Higher conversion rates, better recommendation quality, richer profile enrichment, and more engaging conversations for returning customers
- **Privacy simplicity favors:** Faster deployment, simpler consent management, lower regulatory risk, and a privacy-first brand positioning
- **Recommendation:** Start with progressive personalization that works well for anonymous visitors and adds profile-based personalization for authenticated sessions. This provides value at all identification levels while keeping privacy compliance manageable. Implement consent capture for conversational profiling aligned with existing consent frameworks.

**Brand governance strictness vs. conversational naturalness**

Strict brand governance guardrails ensure every response aligns with brand standards, but overly rigid constraints make conversations feel robotic and reduce engagement.

- **Strict governance favors:** Brand safety, regulatory compliance, consistent messaging, and predictable agent behavior
- **Flexible governance favors:** Natural conversation flow, higher engagement, better customer satisfaction, and the ability to handle a wider range of queries
- **Recommendation:** Begin with moderate governance and tighten or loosen based on conversation analytics. Monitor the rate of "I cannot help with that" responses as an indicator of over-restriction. Use the low-code flow management tools to iterate on governance settings quickly without developer involvement.

**Real-time content refresh vs. system performance**

Real-time content synchronization ensures the agent always has current product and content data, but continuous refresh consumes more infrastructure resources and can introduce latency.

- **Real-time refresh favors:** Accuracy for inventory-sensitive recommendations, time-sensitive promotions, and rapidly changing content
- **Scheduled refresh favors:** System stability, predictable resource consumption, and lower infrastructure costs
- **Recommendation:** Use daily content refresh as the default, with near-real-time refresh only for inventory availability and pricing data that materially affects the customer experience. Monitor content accuracy metrics to determine if the refresh frequency is adequate.

**Comprehensive signal capture vs. data management overhead**

Capturing every conversational signal provides the richest profile enrichment and analytics, but increases data volume, storage costs, and governance complexity.

- **Full signal capture favors:** Advanced analytics, ML model training, comprehensive profile enrichment, and maximum downstream personalization value
- **Selective capture favors:** Lower storage costs, simpler data governance, faster profile lookup performance, and easier compliance with data minimization principles
- **Recommendation:** Start with intent and preference signal capture (the middle ground) and expand to full signal capture only after validating that the additional data creates measurable downstream value. Apply dataset expiration policies to conversational event data to manage storage growth.

## Related documentation

The following resources provide additional information for implementing this use case pattern.

**[!DNL Brand Concierge]**

- [Brand Concierge overview](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge product advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)
- [Brand Concierge site advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)
- [AI Assistant overview](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/home)

**[!DNL Adobe Experience Platform]**

- [AEP overview](https://experienceleague.adobe.com/en/docs/experience-platform/landing/home)
- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Real-Time Customer Profile overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

**Data collection and integration**

- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Mobile SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Edge Network Server API overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)

**Identity and profile**

- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Identity namespaces overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)

**Audiences and segmentation**

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

**Data governance and privacy**

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Consent and preferences field group](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Privacy Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/home)
- [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

**Monitoring and observability**

- [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
- [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

**Analytics and reporting**

- [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [CJA Connections overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [CJA Data views overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Analysis Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

**Guardrails**

- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Ingestion guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Segmentation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
