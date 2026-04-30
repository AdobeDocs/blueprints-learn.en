---
title: Use Case Patterns
description: Learn about the use case patterns for implementing Adobe Experience Platform and applications to achieve key business objectives.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
doc-type: overview-page
exl-id: 58caa6ad-0d1c-4290-9614-c68c9c9028bb
---
# Use case patterns

Use case patterns define repeatable implementation approaches for Adobe Experience Platform and applications. Each pattern describes a specific capability, the function chain that delivers it, the applications involved, and the [key business objectives](/help/blueprints/business-objectives/overview.md) it supports.

Use the tables below to find the pattern that matches your implementation needs, then follow the link to the full implementation reference including options, phases, decision guidance, and Experience League documentation.

## Audience building & activation

The following patterns help you build, evaluate, and activate audience segments across channels and destinations.

| Pattern | Primary Capability | Core Solutions |
| --- | --- | --- |
| [Audience activation to destinations](audience-building-activation/audience-activation-to-destinations.md) | Evaluate and publish audience segments to external destinations for targeting or suppression | [!DNL Real-Time CDP] |
| [Audience Collaboration](audience-building-activation/audience-collaboration-segment-match.md) | Share and match audience segments across sandboxes or organizations using Segment Match | [!DNL Real-Time CDP], [!DNL Experience Platform] |
| [Event forwarding](audience-building-activation/event-forwarding.md) | Forward real-time event data collected via Edge Network to non-Adobe destinations | [!DNL Experience Platform] (Edge Network, event forwarding) |
| [Real-Time Profile Lookup for Support and Sales](audience-building-activation/real-time-profile-lookup.md) | Real-time Customer Profile lookups providing context for agent-assisted support and sales scenarios | [!DNL Real-Time CDP], [!DNL Experience Platform] |
| [Custom Data Science for Profile Enrichment](audience-building-activation/data-science-profile-enrichment.md) | Ingest data-science-based insights into Experience Platform to enrich the Real-Time Customer Profile | [!DNL Experience Platform] |

## Personalization

The following patterns deliver tailored experiences to known and unknown visitors across web and app surfaces.

| Pattern | Primary Capability | Core Solutions |
| --- | --- | --- |
| [Anonymous visitor web personalization](personalization/anonymous-visitor-web-personalization.md) | Deliver personalized content based on in-session behavioral signals for unidentified visitors | [!DNL Journey Optimizer] (web channel), [!DNL Real-Time CDP] |
| [Known-visitor web/app personalization](personalization/known-visitor-web-app-personalization.md) | Deliver personalized content, offers, or promotions to identified visitors based on real-time profile and segment membership | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Offer decisioning](personalization/offer-decisioning.md) | Use centralized decision logic to select the next-best offer or content for a profile across channels | [!DNL Journey Optimizer] (Decisioning), [!DNL Real-Time CDP] |
| [Behavioral recommendation](personalization/behavioral-recommendation.md) | Generate item and content recommendations using selection strategies and ranking models | [!DNL Journey Optimizer] (Decisioning), [!DNL Real-Time CDP] |
| [Edge Profile Access for Web/Mobile Personalization](personalization/edge-profile-access.md) | Real-time edge profile access for high-throughput, low-latency web and mobile personalization | [!DNL Real-Time CDP], [!DNL Experience Platform] (Edge Network) |
| [Audience Sharing with Adobe Target](personalization/audience-sharing-with-target.md) | Share Real-Time CDP profiles and audiences with Adobe Target for known-customer web and mobile personalization | [!DNL Real-Time CDP], [!DNL Target], [!DNL Experience Platform] |

## Campaign management & orchestration

The following patterns cover scheduled, triggered, and multi-step message delivery across channels.

| Pattern | Primary Capability | Core Solutions |
| --- | --- | --- |
| [Batch outbound message activation](campaign-management-orchestration/batch-outbound-message-activation.md) | Evaluate an audience, then deliver a scheduled outbound message in a single batch execution | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Event-triggered messaging](campaign-management-orchestration/event-triggered-messaging.md) | Listen for a real-time behavioral or system event, then deliver a contextual message to the triggering profile | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Multi-step orchestrated journey](campaign-management-orchestration/multi-step-orchestrated-journey.md) | Guide a profile through a branching, multi-touch journey with waits, conditions, and multiple message actions | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Cross-channel journey with decisioning](campaign-management-orchestration/cross-channel-journey-with-decisioning.md) | Orchestrate a multi-step journey incorporating real-time decisioning to select optimal channel, content, or offer | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Campaign v8 Batch Orchestration & Transactional Messaging](campaign-management-orchestration/campaign-v8-orchestration.md) | Batch campaign execution, multi-touch orchestration, ETL-driven data management, and transactional messaging on Campaign v8 | [!DNL Campaign] v8 |
| [Third-party Messaging Integration with Journey Optimizer](campaign-management-orchestration/third-party-messaging.md) | Integrate Journey Optimizer with third-party messaging systems for personalized communications via REST API | [!DNL Journey Optimizer] |

## Analysis

The following patterns support cross-channel behavioral and performance analysis.

| Pattern | Primary Capability | Core Solutions |
| --- | --- | --- |
| [Customer analytics & insight generation](analysis/customer-analytics-insight-generation.md) | Build cross-channel analysis workspaces, computed metrics, and dashboards for behavior and performance analysis | [!DNL Customer Journey Analytics], [!DNL Experience Platform] |

## B2B activation & marketing

The following patterns address B2B-specific marketing scenarios — account-based audiences, buying-group orchestration, and B2B analytics.

| Pattern | Primary Capability | Core Solutions |
| --- | --- | --- |
| [B2B audience activation](b2b/account-audience-activation.md) | Activate account-based B2B audiences across web, email, and advertising channels | [!DNL Real-Time CDP] B2B Edition |
| [Buying group-based marketing & journey management](b2b/buying-group-marketing.md) | Develop account-level journeys that qualify leads into buying groups to improve B2B marketing effectiveness | [!DNL Journey Optimizer] B2B Edition, [!DNL Real-Time CDP] B2B Edition |
| [B2B analytics](b2b/account-analytics.md) | Include B2B account-level information in cross-channel customer journey analysis | [!DNL Customer Journey Analytics] B2B Edition, [!DNL Real-Time CDP] B2B Edition |
| [B2B Journeys using Marketo Data](b2b/marketo-data-journeys.md) | Deploy Journey Optimizer B2B Edition with Marketo data for orchestrating buying group journeys and account engagement | [!DNL Journey Optimizer] B2B Edition, [!DNL Marketo Engage], [!DNL Real-Time CDP] B2B Edition |
| [AJO B2B Paid Media Controller](b2b/paid-media-orchestration.md) | Orchestrate B2B paid media campaigns using waterfall logic to assign accounts to campaigns and activate to destinations | [!DNL Journey Optimizer] B2B Edition, [!DNL Real-Time CDP] B2B Edition |
| [Marketo & Workfront Intake and Create](b2b/campaign-intake-and-creation.md) | Automate marketing campaign request intake and Marketo Engage program creation using Workfront forms and Fusion | [!DNL Marketo Engage], [!DNL Workfront], [!DNL Workfront Fusion] |
| [Marketo & Workfront Review and Approve](b2b/campaign-review-and-approval.md) | Integrate Workfront proofing and approval workflows with Marketo Engage email assets using Fusion automation | [!DNL Marketo Engage], [!DNL Workfront], [!DNL Workfront Fusion] |

## Conversational experience

The following patterns enable AI-powered, brand-safe conversational interactions on digital properties.

| Pattern | Primary Capability | Core Solutions |
| --- | --- | --- |
| [Brand Concierge conversational experience](conversational-experience/brand-concierge-conversational-experience.md) | Transform digital properties into AI-powered, brand-safe conversational experiences that guide customer discovery | [!DNL Brand Concierge], [!DNL Experience Platform], [!DNL Real-Time CDP] |

## Scenario selector

Use this guide when a scenario could plausibly fit more than one pattern. Answer the branching questions to find the primary pattern, then optionally extend with the patterns listed.

### Win-back with incentive offer

*A lapsed customer has not purchased in 90 days. You want to re-engage them with a targeted offer.*

- **Is the offer selection dynamic (different customers receive different offers based on eligibility or ranking)?**
  - Yes → [Offer decisioning](personalization/offer-decisioning.md) as the offer layer, wrapped in [Multi-step orchestrated journey](campaign-management-orchestration/multi-step-orchestrated-journey.md) for the re-engagement sequence
  - No (same offer to all qualifying lapsed customers) → [Multi-step orchestrated journey](campaign-management-orchestration/multi-step-orchestrated-journey.md) alone

### Post-purchase follow-up

*A customer just completed a purchase. You want to send a confirmation, cross-sell recommendation, and loyalty reward notification.*

- **Does the sequence require adaptive branching based on real-time events (e.g., reward claimed, product reviewed)?**
  - Yes → [Multi-step orchestrated journey](campaign-management-orchestration/multi-step-orchestrated-journey.md)
  - No (fixed sequence, no branching) → [Batch outbound message activation](campaign-management-orchestration/batch-outbound-message-activation.md)
- **Does it include personalized product recommendations?**
  - Yes → Extend with [Behavioral recommendation](personalization/behavioral-recommendation.md) at the content layer

### Loyalty milestone personalization

*A customer reaches a new loyalty tier. You want to show personalized web content and send a congratulatory message.*

- **Is the web content personalized (different content per tier or segment)?**
  - Yes → [Known-visitor web/app personalization](personalization/known-visitor-web-app-personalization.md) for the web surface
- **Is the outbound message a single send or a nurture sequence?**
  - Single send → [Event-triggered messaging](campaign-management-orchestration/event-triggered-messaging.md)
  - Sequence → [Multi-step orchestrated journey](campaign-management-orchestration/multi-step-orchestrated-journey.md)

### Re-engagement campaign

*A segment of inactive users needs a multi-touch reactivation sequence.*

- **Do individual messages need to select from multiple offer variants in real time?**
  - Yes → [Cross-channel journey with decisioning](campaign-management-orchestration/cross-channel-journey-with-decisioning.md)
  - No → [Multi-step orchestrated journey](campaign-management-orchestration/multi-step-orchestrated-journey.md)
