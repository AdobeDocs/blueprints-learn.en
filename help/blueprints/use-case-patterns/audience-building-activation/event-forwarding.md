---
title: Event Forwarding
description: Learn how to forward real-time event data collected via Edge Network to non-Adobe destinations for analytics, storage, or advertising.
solution: Experience Platform
exl-id: 24964d27-db56-4fa4-a79f-1b6750564b34
---
# Event forwarding

This guide describes the event forwarding use case pattern, which uses server-side processing on [!DNL Adobe Experience Platform] Edge Network to distribute real-time event data to non-Adobe destinations — such as third-party analytics platforms, cloud storage endpoints, advertising networks, or custom webhooks. It is designed for solution architects, marketing technologists, and implementation engineers who need to understand what this pattern does, the business objectives it supports, the tactical use cases it enables, and the Adobe applications involved.

## Use case pattern

This section describes the pattern and execution plan used to implement event forwarding.

**Event Forwarding** — Forward real-time event data collected via Edge Network to non-Adobe destinations for analytics, storage, or advertising.

**Execution plan:** Datastream Configuration > Event Rule Definition > Destination Mapping > Forwarding Execution > Monitoring

## Use case overview

Organizations collecting behavioral data through the [!DNL Adobe Experience Platform] Web SDK, Mobile SDK, or Server API often need to share that same event stream with non-Adobe systems — analytics platforms like [!DNL Google Analytics] or [!DNL Snowflake], advertising networks for conversion tracking, data warehouses for long-term storage, or custom internal services. Traditionally this required client-side tag proliferation, which increases page weight, introduces latency, and creates privacy and governance risks.

Event forwarding solves this by operating server-side on the Edge Network. When a visitor interaction triggers an event through the Web SDK or Server API, that event is routed through a datastream to the Edge Network. Event forwarding rules — configured in a dedicated event forwarding property — evaluate the incoming event data and selectively forward it to one or more configured destinations. This server-side approach reduces client-side tag bloat, improves page performance, centralizes data governance, and gives the organization control over exactly what data leaves the Adobe ecosystem.

The target audience for this pattern includes organizations that have already deployed (or plan to deploy) the [!DNL Adobe Experience Platform] Web SDK or Server API for data collection and want to extend that investment by distributing event data to non-Adobe endpoints without adding client-side JavaScript tags.

## Key business objectives

The following business objectives are supported by this use case pattern.

### Improve data quality and governance

Ensure clean, complete, and compliant data for accurate targeting, reduced waste, and reliable analytics. Event forwarding centralizes data distribution at the server side, giving the organization a single control point for what data is shared with external systems, reducing the risk of data leakage, and ensuring governance policies are applied before data leaves the [!DNL Adobe] Edge Network.

**KPIs:** Efficiency, Cost Savings

For more information, see [Improve data quality and governance](../../business-objectives/cost-efficiency/improve-data-quality-governance.md).

### Consolidate and modernize marketing technology

Reduce tool fragmentation and technical debt by migrating to unified, scalable platforms. Event forwarding enables organizations to replace multiple client-side vendor tags with a single server-side data distribution mechanism, reducing page load overhead and simplifying the technology stack.

**KPIs:** Cost Savings, Efficiency, Speed To Market

For more information, see [Consolidate and modernize marketing technology](../../business-objectives/cost-efficiency/consolidate-modernize-marketing-technology.md).

## Example tactical use cases

The following are common tactical scenarios where this use case pattern applies.

- **Third-party analytics enrichment** — Forward page view, click, and conversion events to [!DNL Google Analytics], [!DNL Snowflake], or other analytics platforms in real time without adding client-side tags
- **Advertising conversion tracking** — Send purchase and lead-generation events to [!DNL Meta] Conversions API, [!DNL Google Ads], [!DNL TikTok], or [!DNL Snap] for server-side conversion measurement and optimization
- **Data warehouse streaming** — Route raw event data to a cloud data warehouse ([!DNL Google BigQuery], [!DNL Amazon S3], [!DNL Azure Event Hubs]) for long-term storage and offline analysis
- **Custom webhook integration** — Forward filtered or transformed event data to internal microservices, CRM systems, or partner platforms via HTTP endpoints
- **Tag reduction and page performance improvement** — Replace multiple client-side vendor JavaScript tags with a single Web SDK implementation plus server-side event forwarding rules, reducing page weight and improving Core Web Vitals
- **Privacy-compliant data sharing** — Apply data filtering and field-level redaction rules server-side before sharing event data with third parties, ensuring PII is stripped or hashed before it reaches external systems
- **Multi-cloud event distribution** — Simultaneously forward the same event stream to multiple destinations (for example, analytics, advertising, and data warehouse) from a single server-side rule set
- **Real-time fraud signal forwarding** — Forward high-value transaction events to fraud detection systems for real-time risk scoring and alerting

## Key performance indicators

The following KPIs help measure the success of this use case pattern.

- **Page load time reduction** — Measured improvement in page load speed and Core Web Vitals after migrating client-side tags to server-side event forwarding
- **Data delivery success rate** — Percentage of events successfully forwarded to destination endpoints without errors or timeouts
- **Tag count reduction** — Number of client-side vendor tags removed after implementing server-side equivalents
- **Data freshness / latency** — Time between event occurrence on the client and event arrival at the destination endpoint (target: sub-second to seconds)
- **Governance compliance rate** — Percentage of outbound data shares that pass through server-side filtering rules, ensuring no PII or restricted data reaches unauthorized destinations
- **Operational efficiency** — Reduction in developer hours spent managing client-side tag deployments and troubleshooting tag conflicts

## Applications

The following applications are used in this use case pattern.

- **[!DNL Adobe Experience Platform] (Edge Network)** — Receives and routes real-time event data from Web SDK, Mobile SDK, or Server API through configured datastreams
- **[!DNL Adobe Experience Platform] (Event Forwarding)** — Provides the server-side rule engine for evaluating, filtering, transforming, and forwarding event data to external destinations
- **[!DNL Adobe Experience Platform] (Tags / Data Collection)** — Manages the event forwarding property lifecycle, extensions, rules, and publishing workflow

## Related documentation

The following resources provide additional detail on the topics covered in this guide.

**Event forwarding**

- [Event forwarding overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [Getting started with event forwarding](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)
- [Event forwarding monitoring](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring)
- [Event forwarding secrets](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)

**Event forwarding extensions**

- [Server-side extensions catalog](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [Adobe Cloud Connector extension](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [Meta Conversions API extension](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/meta/overview)
- [Google Cloud Platform extension](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [AWS extension](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/aws/overview)
- [Snowflake extension](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/snowflake/overview)
- [Google Ads Enhanced Conversions extension](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-ads-enhanced-conversions/overview)
- [Mailchimp extension](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/mailchimp/overview)

**Data collection and Edge Network**

- [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Datastreams overview](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview)
- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Edge Network Server API overview](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Tags overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
