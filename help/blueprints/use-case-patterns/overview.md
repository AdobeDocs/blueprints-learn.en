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
| [Audience Activation to Destinations](audience-building-activation/audience-activation-to-destinations.md) | Evaluate and publish audience segments to external destinations for targeting or suppression | [!DNL Real-Time CDP] |
| [Audience Collaboration with Segment Match](audience-building-activation/audience-collaboration-segment-match.md) | Share and match audience segments across sandboxes or organizations using Segment Match | [!DNL Real-Time CDP], [!DNL Experience Platform] |
| [Event Forwarding](audience-building-activation/event-forwarding.md) | Forward real-time event data collected via Edge Network to non-Adobe destinations | [!DNL Experience Platform] (Edge Network, event forwarding) |
| [B2B Audience Activation](audience-building-activation/b2b-audience-activation.md) | Activate account-based B2B audiences across web, email, and advertising channels | [!DNL Real-Time CDP] B2B Edition |

## Personalization

The following patterns deliver tailored experiences to known and unknown visitors across web and app surfaces.

| Pattern | Primary Capability | Core Solutions |
| --- | --- | --- |
| [Anonymous Visitor Web Personalization](personalization/anonymous-visitor-web-personalization.md) | Deliver personalized content based on in-session behavioral signals for unidentified visitors | [!DNL Journey Optimizer] (web channel), [!DNL Real-Time CDP] |
| [Known-Visitor Web/App Personalization](personalization/known-visitor-web-app-personalization.md) | Deliver personalized content, offers, or promotions to identified visitors based on real-time profile and segment membership | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Offer Decisioning](personalization/offer-decisioning.md) | Use centralized decision logic to select the next-best offer or content for a profile across channels | [!DNL Journey Optimizer] (Decisioning), [!DNL Real-Time CDP] |
| [Behavioral Recommendation](personalization/behavioral-recommendation.md) | Generate item and content recommendations using selection strategies and ranking models | [!DNL Journey Optimizer] (Decisioning), [!DNL Real-Time CDP] |

## Campaign management & orchestration

The following patterns cover scheduled, triggered, and multi-step message delivery across channels.

| Pattern | Primary Capability | Core Solutions |
| --- | --- | --- |
| [Batch Outbound Message Activation](campaign-management-orchestration/batch-outbound-message-activation.md) | Evaluate an audience, then deliver a scheduled outbound message in a single batch execution | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Event-Triggered Messaging](campaign-management-orchestration/event-triggered-messaging.md) | Listen for a real-time behavioral or system event, then deliver a contextual message to the triggering profile | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Multi-Step Orchestrated Journey](campaign-management-orchestration/multi-step-orchestrated-journey.md) | Guide a profile through a branching, multi-touch journey with waits, conditions, and multiple message actions | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Cross-Channel Journey with Decisioning](campaign-management-orchestration/cross-channel-journey-with-decisioning.md) | Orchestrate a multi-step journey incorporating real-time decisioning to select optimal channel, content, or offer | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Buying Group-Based Marketing & Journey Management](campaign-management-orchestration/buying-group-based-marketing.md) | Develop account-level journeys that qualify leads into buying groups to improve B2B marketing effectiveness | [!DNL Journey Optimizer] B2B Edition, [!DNL Real-Time CDP] B2B Edition |

## Analysis

The following patterns support cross-channel behavioral and performance analysis.

| Pattern | Primary Capability | Core Solutions |
| --- | --- | --- |
| [Customer Analytics & Insight Generation](analysis/customer-analytics-insight-generation.md) | Build cross-channel analysis workspaces, computed metrics, and dashboards for behavior and performance analysis | [!DNL Customer Journey Analytics], [!DNL Experience Platform] |
| [B2B Analytics](analysis/b2b-analytics.md) | Include B2B account-level information in cross-channel customer journey analysis | [!DNL Customer Journey Analytics] B2B Edition, [!DNL Real-Time CDP] B2B Edition |

## Conversational experience

The following patterns enable AI-powered, brand-safe conversational interactions on digital properties.

| Pattern | Primary Capability | Core Solutions |
| --- | --- | --- |
| [Brand Concierge Conversational Experience](conversational-experience/brand-concierge-conversational-experience.md) | Transform digital properties into AI-powered, brand-safe conversational experiences that guide customer discovery | [!DNL Brand Concierge], [!DNL Experience Platform], [!DNL Real-Time CDP] |
