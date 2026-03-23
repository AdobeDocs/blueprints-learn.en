---
title: Technology Use Cases
description: Discover how technology organizations use Adobe Experience Platform to unify data collection, forward events in real time, and power analytics and activation across digital products.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: 2e4d9a1e-af46-4422-b00c-224a955101ee
---
# Technology Use Cases

Technology organizations use Adobe Experience Platform to centralize data collection from web, mobile, and product surfaces and distribute real-time events to the analytics, data warehouse, and activation destinations that power their products and marketing programs. By consolidating event collection at the edge, technology teams reduce client-side complexity, improve data quality, and ensure all downstream systems receive consistent behavioral data from a single authoritative source.

## Real-Time Event Forwarding

Forward real-time behavioral events collected via the Edge Network to third-party analytics, data warehouses, and partner platforms for enrichment and activation. Centralizing event collection at the edge and forwarding to multiple destinations reduces client-side tag overhead, improves data quality, and ensures all downstream systems receive consistent event data from a single authoritative source.

### Business impact

Technology organizations implementing real-time event forwarding reduce client-side tag load and associated performance overhead while improving consistency of event data across analytics, data warehouse, and activation destinations. Server-side forwarding also reduces page weight and improves load performance, directly benefiting user experience metrics.

### How to implement

Use the [Event Forwarding](/help/blueprints/use-case-patterns/audience-building-activation/event-forwarding.md) pattern to route events collected by Adobe Experience Platform Web SDK through the Edge Network to configured server-side destinations. This is the right pattern when the objective is server-to-server event distribution from a single collection point — rather than managing separate tags for each destination on the client side, which adds page weight and creates data inconsistency across systems.

### Technical considerations

- Edge Network event forwarding requires migration of event collection to Adobe Experience Platform Web SDK or Mobile SDK; existing tag-based implementations must be assessed for compatibility before forwarding destinations are configured.
- Forwarding rules must be configured to send only the fields required by each destination — avoid forwarding full XDM payloads to destinations that only need a small subset of fields, as this increases data transfer costs and creates compliance exposure.
- Destination connectors must handle failure gracefully; event forwarding pipelines should implement retry logic and alerting for destinations that become unavailable to prevent data loss during outages.
- Data governance policies must be reviewed for each forwarding destination to ensure that user consent preferences captured at the edge are honored in the forwarding configuration.
