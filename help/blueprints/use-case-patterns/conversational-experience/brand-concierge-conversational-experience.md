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

**KPIs:** New Customers, Customer Acquisition Cost, Prospect/Lead Conversion

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

## Related documentation

For implementation guidance and further information, see the [Brand Concierge overview](https://experienceleague.adobe.com/en/docs/brand-concierge/content/documentation/overview) on Adobe Experience League.
