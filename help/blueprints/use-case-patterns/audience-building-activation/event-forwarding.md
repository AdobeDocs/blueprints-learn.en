---
title: Event Forwarding
description: "Learn how to forward real-time event data collected via Edge Network to non-Adobe destinations for analytics, storage, or advertising."
solution: Experience Platform
---

# Event forwarding

This guide covers the implementation of server-side event forwarding using [!DNL Adobe Experience Platform] Edge Network. It is designed for solution architects, marketing technologists, and implementation engineers who need to distribute real-time event data collected via the Edge Network to non-Adobe destinations — such as third-party analytics platforms, cloud storage endpoints, advertising networks, or custom webhooks.

It presents all viable approaches for configuring event forwarding, explains the trade-offs between them, and links to [!DNL Adobe Experience League] documentation for detailed procedural guidance.

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

## Use case pattern

This section describes the pattern and function chain used to implement event forwarding.

**Event Forwarding** — Forward real-time event data collected via Edge Network to non-Adobe destinations for analytics, storage, or advertising.

**Function Chain:** Datastream Configuration > Event Rule Definition > Destination Mapping > Forwarding Execution > Monitoring

## Applications

The following applications are used in this use case pattern.

- **[!DNL Adobe Experience Platform] (Edge Network)** — Receives and routes real-time event data from Web SDK, Mobile SDK, or Server API through configured datastreams
- **[!DNL Adobe Experience Platform] (Event Forwarding)** — Provides the server-side rule engine for evaluating, filtering, transforming, and forwarding event data to external destinations
- **[!DNL Adobe Experience Platform] (Tags / Data Collection)** — Manages the event forwarding property lifecycle, extensions, rules, and publishing workflow

## Foundational functions

The following foundational capabilities must be in place for this use case pattern. For each function, the status indicates whether it is typically required, assumed to be pre-configured, or not applicable.

| Foundational Function | Status | What Must Be in Place | Experience League Reference |
| --- | --- | --- | --- |
| Administration & Governance | Required | A sandbox must be active with appropriate user roles and permissions configured. Users managing event forwarding need Data Collection permissions in [!DNL Adobe Admin Console], including rights to manage event forwarding properties, extensions, and rules. | [Access control overview](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Data Modeling & Preparation | Required | XDM schemas must be defined for the event data flowing through the Edge Network. The datastream must reference a valid XDM ExperienceEvent schema so that event forwarding rules can access structured fields for filtering, transformation, and mapping. | [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Data Sources & Collection | Required | A data collection mechanism must be active — Web SDK, Mobile SDK, or Edge Network Server API — sending events through a configured datastream. The datastream is the foundational routing layer that connects client-side collection to server-side event forwarding. | [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Identity & Profile Configuration | Not Applicable | Event forwarding operates on raw event data at the Edge Network layer, before identity resolution or profile unification occurs. Identity namespaces and merge policies are not required unless the forwarded events also need to contribute to the Real-Time Customer Profile (which is a separate datastream service configuration, not an event forwarding concern). | |
| Audience Definition & Segmentation | Not Applicable | Event forwarding processes individual events in real time and does not evaluate audience membership. Audience-based filtering is not part of the event forwarding function chain. If audience-based activation is needed, see the Audience Activation to Destinations reference plan. | |

## Supporting functions

The following capabilities augment this use case pattern but are not required for core execution.

| Supporting Function | Status | Why It Matters | Experience League Reference |
| --- | --- | --- | --- |
| Computed / Derived Attribute Creation | Not Applicable | Event forwarding operates on raw event data, not profile-level computed attributes. Computed attributes are not available in the event forwarding context. | |
| Data Lifecycle Management | Recommended | If event data is also being ingested into AEP datasets (via the same datastream), data retention policies (expiration) should be configured for those datasets to manage storage costs and regulatory compliance. Event forwarding itself does not store data, but the parallel AEP ingestion path does. | [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Data Usage Labeling & Enforcement | Recommended | While event forwarding rules provide field-level filtering (allowing you to exclude sensitive data from forwarded payloads), applying data usage labels to the underlying schemas and datasets ensures governance policies are enforced if the same data is used for audience activation or personalization. | [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Monitoring & Observability | Included | Monitoring is essential for event forwarding. The Event Forwarding Monitoring dashboard provides visibility into forwarding success rates, error rates, and destination response codes. Alerts should be configured for destination failures. | [Event forwarding monitoring](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring) |
| Reporting & Analysis | Recommended | If forwarded events feed a third-party analytics platform, consider connecting the same AEP event datasets to CJA for a unified cross-channel view. This enables comparison between Adobe-side and third-party-side analytics. | [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Application functions

This plan exercises the following functions from the Application Function Catalog. Functions are mapped to implementation phases rather than numbered steps.

### [!DNL Adobe Experience Platform] (AEP)

| Function | Implementation Phase | Description |
| --- | --- | --- |
| Datastream Configuration | Phase 1: Datastream Configuration | Configure a datastream to receive Edge Network events and enable the event forwarding service |
| Event Forwarding Property Setup | Phase 2: Event Forwarding Property & Extensions | Create an event forwarding property and install destination-specific extensions |
| Event Rule Definition | Phase 3: Event Rule Definition | Define rules that evaluate incoming event data and determine what to forward and where |
| Destination Mapping | Phase 3: Event Rule Definition | Map event data elements to destination-specific payload formats within forwarding rules |
| Forwarding Execution | Phase 4: Publishing & Activation | Publish the event forwarding configuration to the Edge Network for live execution |
| Monitoring | Phase 5: Monitoring & Validation | Monitor forwarding success rates, error codes, and destination health |

## Prerequisites

Ensure the following are in place before beginning implementation.

- [ ] [!DNL Adobe Experience Platform] license with Edge Network and Event Forwarding entitlement
- [ ] Data Collection permissions configured in [!DNL Adobe Admin Console] (manage properties, extensions, rules, and publishing for event forwarding)
- [ ] At least one active data collection mechanism (Web SDK, Mobile SDK, or Server API) sending events through a datastream
- [ ] XDM ExperienceEvent schema defined for the event data being collected
- [ ] Datastream created and linked to the collection mechanism
- [ ] Destination endpoint credentials and documentation available (for example, [!DNL Meta] Conversions API access token, [!DNL Google Analytics] measurement ID, webhook URL, cloud storage credentials)
- [ ] Understanding of the event data model and which fields/events each destination requires

## Implementation options

This section describes the available approaches for implementing event forwarding and provides guidance on choosing the right option.

### Option A: Extension-based event forwarding

**Best for:** Teams using well-supported destination platforms ([!DNL Meta], [!DNL Google], [!DNL AWS], [!DNL Azure], [!DNL Snowflake], etc.) that have pre-built event forwarding extensions available in the Data Collection catalog.

**How it works:**

Extension-based event forwarding leverages pre-built integrations maintained by Adobe or third-party partners. Each extension is purpose-built for a specific destination and handles authentication, payload formatting, and endpoint communication. The implementer installs the extension in the event forwarding property, configures authentication credentials, and builds rules that map XDM data elements to the extension's action fields.

This approach minimizes custom development because the extension abstracts the destination's API requirements. For example, the [!DNL Meta] Conversions API extension translates XDM commerce events into the format [!DNL Meta] expects, handling hashing of PII fields, deduplication parameters, and access token management. Similarly, the [!DNL Google Cloud Platform] or [!DNL AWS] extensions handle authentication and payload formatting for their respective cloud services.

The trade-off is that extension availability determines which destinations are supported. If no extension exists for a target destination, Option B (Custom Webhook) must be used instead.

**Key considerations:**

- Extension availability varies — check the [Data Collection extensions catalog](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview) before planning
- Extensions are maintained by Adobe or partners; updates may introduce breaking changes that require rule adjustments
- Some extensions support only specific event types or require specific XDM field mappings
- Extensions handle authentication and credential management within their configuration UI

**Advantages:**

- Fastest time to implementation for supported destinations
- Pre-built payload formatting reduces mapping errors
- Authentication and credential management handled by the extension
- Maintained and updated by Adobe or certified partners
- Reduced custom code and lower maintenance burden

**Limitations:**

- Limited to destinations with available extensions
- Less flexibility in payload customization compared to custom webhooks
- Extension updates may require rule reconfiguration
- Some extensions may not support all destination API features

**Experience League:**

- [Event forwarding extensions catalog](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [Meta Conversions API extension](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/meta/overview)
- [Google Cloud Platform extension](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [AWS extension](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/aws/overview)
- [Snowflake extension](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/snowflake/overview)

### Option B: Custom webhook (Fetch API) event forwarding

**Best for:** Teams that need to forward events to destinations without a pre-built extension, or that require full control over the HTTP request payload, headers, and authentication mechanism.

**How it works:**

Custom webhook-based event forwarding uses the [!DNL Adobe Cloud Connector] extension (included by default) to make arbitrary HTTP requests to any endpoint. The implementer defines data elements to extract and transform values from the incoming XDM event, then configures a rule action using the Cloud Connector's "Make Fetch Call" action type. This action allows full control over the HTTP method, URL, headers, and request body.

The request body is typically constructed using data elements and custom code to format the payload according to the destination's API specification. This approach supports any HTTP-accessible endpoint — REST APIs, webhooks, cloud functions, or internal services — making it the most flexible option.

The trade-off is higher implementation effort and ongoing maintenance. The implementer must understand the destination API, handle authentication manually (for example, setting Authorization headers, managing token refresh), and maintain the payload format if the destination API evolves.

**Key considerations:**

- Requires understanding of the destination API specification (HTTP method, URL structure, payload format, authentication)
- Authentication credentials must be managed manually in data elements or secrets
- Custom code may be needed for payload transformation (hashing, encoding, restructuring)
- No automatic updates when the destination API changes — manual maintenance required
- The Secrets feature in Data Collection can securely store API keys and tokens

**Advantages:**

- Supports any HTTP-accessible endpoint — no extension dependency
- Full control over request payload, headers, and authentication
- Can forward to internal services, custom APIs, or niche platforms
- Enables complex payload transformations using custom code
- Can implement retry logic and error handling within custom code

**Limitations:**

- Higher initial implementation effort
- Ongoing maintenance responsibility for payload format and authentication
- No pre-built error handling or credential rotation — must be implemented manually
- Requires developer expertise in HTTP protocols and destination API specifics

**Experience League:**

- [Adobe Cloud Connector extension](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [Event forwarding secrets](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)

### Option C: Hybrid (extensions + custom webhooks)

**Best for:** Organizations forwarding events to multiple destinations where some have pre-built extensions and others require custom integration.

**How it works:**

The hybrid approach combines extension-based forwarding for well-supported destinations with custom webhook actions for destinations that lack extensions. A single event forwarding property contains multiple rules — some using extension actions (for example, [!DNL Meta] Conversions API extension for advertising conversion tracking) and others using Cloud Connector fetch actions (for example, forwarding to an internal data lake endpoint).

This approach maximizes coverage while minimizing unnecessary custom development. Each rule operates independently, so extension-based rules benefit from pre-built payload formatting while custom rules maintain full flexibility.

**Key considerations:**

- Property complexity increases with the number of rules and destinations
- Testing and debugging may require different approaches for extension-based vs. custom rules
- Publishing changes affect all rules in the property — use libraries and environments to stage changes safely
- Consider organizing rules with clear naming conventions to distinguish extension-based from custom actions

**Advantages:**

- Best coverage across diverse destination types
- Leverages pre-built extensions where available, reducing effort
- Maintains flexibility for custom destinations
- Single event forwarding property manages all forwarding logic

**Limitations:**

- Higher property complexity with multiple rule types
- Mixed maintenance model — some rules auto-update via extensions, others require manual upkeep
- Debugging requires familiarity with both extension configurations and custom fetch call patterns

**Experience League:**

- [Event forwarding overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [Getting started with event forwarding](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)

### Option comparison

The following table compares the three implementation options.

| Criteria | Option A: Extension-Based | Option B: Custom Webhook | Option C: Hybrid |
| --- | --- | --- | --- |
| Best for | Supported destinations ([!DNL Meta], [!DNL Google], [!DNL AWS], etc.) | Custom endpoints, niche platforms, internal services | Multiple destinations with mixed support |
| Complexity | Low | Medium-High | Medium |
| Time to implement | Days | Days-Weeks | Varies by destination mix |
| Flexibility | Limited to extension capabilities | Full control | Full control where needed |
| Maintenance | Low (extension-managed) | High (manual upkeep) | Mixed |
| Requires | Extension available for destination | Destination API documentation | Both, depending on destination |
| Custom code needed | Minimal | Moderate-Significant | Varies |

### Choose the right option

Start by inventorying your target destinations and checking whether pre-built event forwarding extensions exist for each.

1. **If all destinations have extensions** — Choose Option A. This gives you the fastest implementation with the lowest maintenance burden. Extensions handle authentication, payload formatting, and API version management.

2. **If no destinations have extensions, or you need full payload control** — Choose Option B. Use the Cloud Connector extension to make custom HTTP requests to any endpoint. This is also the right choice when you need to apply complex transformations, custom hashing, or send to internal services.

3. **If you have a mix of supported and unsupported destinations** — Choose Option C. Use extensions for platforms like [!DNL Meta], [!DNL Google], and [!DNL AWS], and custom webhooks for everything else. This is the most common production scenario for organizations with diverse analytics and advertising stacks.

## Implementation phases

The following phases describe the end-to-end implementation process for event forwarding.

### Phase 1: Datastream configuration

**Application Function:** AEP: Datastream Configuration

**What you will configure:** A datastream that receives events from your Web SDK, Mobile SDK, or Server API implementation and routes them to the Edge Network where event forwarding rules can process them. If event forwarding is being added to an existing data collection deployment, you will enable event forwarding on the existing datastream.

**Decision points in this phase:**

>[!NOTE]
>
>**Decision: New datastream vs. existing datastream**
>
>Should you create a new datastream for event forwarding or enable event forwarding on an existing datastream?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Use existing datastream | You already have Web SDK or Server API sending events through a datastream | Most common scenario; event forwarding is simply enabled as an additional service on the datastream. No client-side changes needed. |
>| Create new datastream | This is a greenfield implementation with no existing data collection, or you need a separate data flow for specific event types | Requires client-side SDK configuration to point to the new datastream ID. Allows isolated configuration. |

>[!NOTE]
>
>**Decision: Which AEP services to enable alongside event forwarding**
>
>The datastream can route events to multiple AEP services simultaneously. Event forwarding is one service; others (AEP data ingestion, [!DNL Target], [!DNL Analytics]) can run in parallel.
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Event forwarding only | You only need to forward events to non-Adobe destinations and do not need the data in AEP datasets | Minimizes data processing costs. Events flow through the Edge Network to forwarding rules but are not ingested into AEP data lake. |
>| Event forwarding + AEP ingestion | You need the same events both in AEP (for profiles, audiences, journeys) and forwarded to external systems | Most common for organizations using [!DNL RT-CDP] or [!DNL AJO] alongside third-party analytics. The datastream sends events to both AEP datasets and event forwarding rules. |
>| Event forwarding + multiple Adobe services | You need events routed to AEP, [!DNL Target], [!DNL Analytics], and external destinations simultaneously | Enable all required services on the datastream. Each service receives the event independently. |

**UI navigation:** [!DNL Experience Platform] > Data Collection > Datastreams > Select or create datastream

**Key configuration details:**

- The datastream must have event forwarding enabled under its Advanced Settings or service configuration
- Link the event forwarding property (created in Phase 2) to the datastream
- Confirm the XDM schema assigned to the datastream matches the event structure your collection mechanism sends

**Experience League documentation:**

- [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Datastreams overview](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview)
- [Event forwarding overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)

### Phase 2: Event forwarding property and extensions

**Application Function:** AEP: Event Forwarding Property Setup

**What you will configure:** An event forwarding property in the Data Collection UI, along with the extensions needed for your target destinations. The event forwarding property is the container for all rules, data elements, and extensions that define your server-side forwarding logic.

**Decision points in this phase:**

>[!NOTE]
>
>**Decision: Single property vs. multiple properties**
>
>Should you use one event forwarding property for all destinations or separate properties?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Single property | Most implementations; all forwarding rules share the same event stream | Simpler to manage, single publishing workflow, all rules evaluate against every event. Use rule conditions to filter which events go to which destinations. |
>| Multiple properties | You need different teams to manage different destination integrations independently, or you have strict environment isolation requirements | Each property has its own publishing workflow and can be linked to different datastreams. Increases management overhead but improves access control boundaries. |

>[!NOTE]
>
>**Decision: Which extensions to install**
>
>Select extensions based on your target destinations and chosen implementation option (A, B, or C from above).
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Destination-specific extensions ([!DNL Meta], [!DNL Google], [!DNL AWS], etc.) | The destination has a pre-built extension and you want minimal custom configuration (Option A or C) | Each extension requires destination-specific credentials (API tokens, measurement IDs, account IDs). Review extension documentation for supported event types and required fields. |
>| Cloud Connector extension only | All destinations will use custom HTTP requests (Option B) | The Cloud Connector extension is installed by default. Use the Secrets feature to securely store API keys and authentication tokens. |
>| Both destination-specific and Cloud Connector | You have a mix of supported and custom destinations (Option C) | Install specific extensions for well-supported destinations and use Cloud Connector for the rest. |

**UI navigation:** [!DNL Experience Platform] > Data Collection > Event Forwarding > Create Property (or select existing)

**Key configuration details:**

- Name the property with a clear convention (for example, "Event Forwarding - Production" or "EF - Analytics & Advertising")
- Install the [!DNL Adobe Cloud Connector] extension (included by default for custom webhook actions)
- Install destination-specific extensions and configure their credentials
- Use the Secrets feature (Data Collection > Event Forwarding > Secrets) to securely store API keys, tokens, and credentials
- Configure environments (Development, Staging, Production) for safe publishing workflows

**Experience League documentation:**

- [Getting started with event forwarding](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)
- [Event forwarding extensions catalog](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [Event forwarding secrets](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)
- [Adobe Cloud Connector extension](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)

### Phase 3: Event rule definition

**Application Function:** AEP: Event Rule Definition, AEP: Destination Mapping

**What you will configure:** Rules that evaluate incoming event data, apply conditions to filter which events should be forwarded, and define actions that send the data to destination endpoints. Each rule consists of conditions (when to fire) and actions (what to do). Data elements extract and transform values from the XDM event payload for use in rule conditions and action configurations.

**Decision points in this phase:**

>[!NOTE]
>
>**Decision: Event filtering strategy**
>
>How should you determine which events are forwarded to each destination?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Forward all events | The destination needs a complete event stream (for example, data warehouse for raw event storage) | Simplest configuration — no conditions needed. High data volume at the destination. Consider destination cost and rate limits. |
>| Filter by event type | Different destinations need different event types (for example, purchases to advertising, page views to analytics) | Use conditions based on `arc.event.xdm.eventType` or similar XDM fields. Reduces unnecessary data at the destination. |
>| Filter by event attributes | Only specific events meeting certain criteria should be forwarded (for example, purchases above a threshold, events from specific page paths) | Use data element values in rule conditions. More complex but reduces noise at the destination. |

>[!NOTE]
>
>**Decision: Data transformation approach**
>
>How should XDM event data be transformed for the destination payload?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Direct XDM field mapping via data elements | The destination fields map cleanly to XDM fields (common with extension-based forwarding) | Create data elements that reference XDM paths (for example, `arc.event.xdm.commerce.order.priceTotal`). Extensions often provide a mapping UI. |
>| Custom code transformation | The destination requires a payload format significantly different from XDM, or fields need hashing, concatenation, or restructuring | Use custom code data elements or action-level custom code to transform the payload. More flexible but harder to maintain. |
>| Combination of data elements and custom code | Some fields map directly while others need transformation | Use data elements for simple mappings and custom code blocks for complex transformations. Balance maintainability with flexibility. |

>[!NOTE]
>
>**Decision: PII handling in forwarded data**
>
>How should personally identifiable information be handled before forwarding?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Exclude PII fields entirely | The destination does not need PII and governance policies restrict sharing | Configure rules to omit PII fields from the forwarded payload. Simplest approach for privacy compliance. |
>| Hash PII fields before forwarding | The destination requires hashed identifiers (for example, [!DNL Meta] requires SHA-256 hashed email for Conversions API) | Use custom code data elements to apply SHA-256 hashing. Some extensions handle hashing automatically. |
>| Forward PII with contractual basis | The destination has a data processing agreement and the legal basis exists for sharing PII | Ensure data usage labels and governance policies (S3) permit the sharing. Document the legal basis. |

**UI navigation:** [!DNL Experience Platform] > Data Collection > Event Forwarding > Select Property > Data Elements / Rules

**Key configuration details:**

- **Data elements** reference the incoming XDM event using the path prefix `arc.event.xdm.` (for example, `arc.event.xdm.web.webPageDetails.URL` for the page URL)
- **Rule conditions** evaluate data element values to determine if the rule should fire
- **Rule actions** use extension-specific actions (for Option A) or Cloud Connector "Make Fetch Call" actions (for Option B) to send data to destinations
- Each rule can have multiple actions, allowing a single event to be forwarded to multiple destinations
- Use rule ordering to control the sequence of evaluation when multiple rules may fire for the same event
- Test rules thoroughly in the Development environment before publishing to Production

**Where options diverge:**

**For Option A (Extension-Based):**

Configure rule actions using the destination extension's pre-built action types. For example, the [!DNL Meta] Conversions API extension provides a "Send Event" action where you map XDM fields to [!DNL Meta] event parameters (event_name, event_time, user_data, custom_data). The extension handles payload formatting, hashing, and API communication.

**For Option B (Custom Webhook):**

Configure rule actions using the Cloud Connector extension's "Make Fetch Call" action. Specify the destination URL, HTTP method (typically POST), request headers (including Authorization), and construct the request body using data elements and/or custom code. You are responsible for matching the destination API's expected payload format exactly.

**For Option C (Hybrid):**

Create separate rules for each destination. Extension-based rules use the extension's action types; custom rules use Cloud Connector fetch calls. All rules coexist in the same property and evaluate independently against each incoming event.

**Experience League documentation:**

- [Event forwarding rules](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [Data elements in event forwarding](https://experienceleague.adobe.com/en/docs/experience-platform/tags/ui/data-elements)
- [Rules in Data Collection](https://experienceleague.adobe.com/en/docs/experience-platform/tags/ui/rules)
- [Adobe Cloud Connector extension](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)

### Phase 4: Publishing and activation

**Application Function:** AEP: Forwarding Execution

**What you will configure:** The publishing workflow that promotes your event forwarding rules from Development through Staging to Production. Event forwarding uses the same library-based publishing model as Tags, with environments and build artifacts that control which configuration is active at the Edge Network.

**Decision points in this phase:**

>[!NOTE]
>
>**Decision: Publishing workflow rigor**
>
>How rigorous should the publishing process be?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Direct to Production (Development > Production) | Small teams, low-risk destinations, or proof-of-concept implementations | Faster deployment but higher risk of production issues. Suitable for initial testing with non-critical destinations. |
>| Full environment progression (Development > Staging > Production) | Production implementations with critical destinations (advertising platforms, data warehouses) | Recommended for all production use cases. Staging allows validation with real traffic before production deployment. |

**UI navigation:** [!DNL Experience Platform] > Data Collection > Event Forwarding > Select Property > Publishing Flow

**Key configuration details:**

- Create a library containing all rules, data elements, and extension configurations to publish
- Build and test in the Development environment first using the Event Forwarding Monitoring tool to verify events are being forwarded correctly
- Promote to Staging for pre-production validation with live traffic
- Publish to Production only after confirming successful event delivery in Staging
- Use library versioning to track changes and enable rollback if needed

**Experience League documentation:**

- [Publishing overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/overview)
- [Libraries](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/libraries)
- [Environments](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/environments)
- [Builds](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/builds)

### Phase 5: Monitoring and validation

**Application Function:** AEP: Monitoring

**What you will configure:** Monitoring dashboards and validation processes to confirm events are being forwarded successfully, diagnose failures, and maintain operational health of the event forwarding deployment.

**Decision points in this phase:**

>[!NOTE]
>
>**Decision: Monitoring depth**
>
>How deeply should event forwarding be monitored?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Event Forwarding Monitoring dashboard only | Basic monitoring for non-critical destinations or initial deployments | Provides overview of forwarding success/failure rates and destination response codes. Sufficient for most implementations. |
>| Event Forwarding Monitoring + destination-side validation | Critical destinations where data completeness directly affects business outcomes (advertising conversion tracking, data warehouse integrity) | Cross-reference Adobe-side forwarding metrics with destination-side receipt confirmation. Catches edge cases where the destination accepts the request but fails to process the data. |
>| Full observability stack (Event Forwarding Monitoring + destination validation + AEP Alerts) | Enterprise-scale deployments with SLA requirements on data delivery | Combine event forwarding monitoring with AEP platform alerts for a comprehensive view. Configure alert notifications for forwarding failure thresholds. |

**UI navigation:** [!DNL Experience Platform] > Data Collection > Event Forwarding > Select Property > Monitoring

**Key configuration details:**

- The Event Forwarding Monitoring tool shows event volume, success rates, and error details per rule and per destination
- Monitor HTTP response codes from destinations — 2xx indicates success, 4xx indicates client errors (likely payload or authentication issues), 5xx indicates destination-side failures
- Use the [!DNL Adobe Experience Platform Debugger] browser extension to inspect events flowing from the client through the Edge Network to event forwarding rules
- Validate end-to-end by checking that forwarded events appear in the destination system (for example, check [!DNL Google Analytics] real-time reports, [!DNL Meta] Events Manager, or data warehouse tables)
- Set up AEP Alerts for source and dataflow failures to catch upstream issues that would prevent events from reaching event forwarding rules

**Experience League documentation:**

- [Event forwarding monitoring](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring)
- [Adobe Experience Platform Debugger](https://experienceleague.adobe.com/en/docs/experience-platform/debugger/home)
- [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

## Implementation considerations

This section covers guardrails, common pitfalls, best practices, and trade-off decisions to keep in mind throughout the implementation.

### Guardrails and limits

- Event forwarding processes events in real time at the Edge Network — there is no batch mode or retry queue for failed deliveries by default
- Edge Network rate limits apply to the total event volume processed per datastream — [Edge Network guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/guardrails)
- Event forwarding rules execute server-side and cannot access client-side resources (DOM, cookies, localStorage)
- Custom code in event forwarding rules runs in a sandboxed environment — not all browser JavaScript APIs are available
- The Cloud Connector fetch call has timeout limits — destinations that respond slowly may cause timeouts
- Event forwarding is subject to Edge Network geographic routing — events are processed at the nearest Edge location
- Maximum payload size for forwarded requests is governed by Edge Network limits

### Common pitfalls

- **Forwarding all XDM fields without filtering:** Sending the entire XDM event payload to a destination that only needs a few fields wastes bandwidth, increases destination costs, and may inadvertently share PII. Always map only the required fields in your forwarding rules.

- **Not securing credentials with Secrets:** Hardcoding API keys or tokens in data elements or rule actions creates a security risk. Always use the Data Collection Secrets feature to store credentials securely and reference them in rules.

- **Ignoring destination rate limits:** Third-party destinations often have API rate limits. If your event volume exceeds a destination's capacity, events may be dropped or your API access may be throttled. Review destination documentation for rate limits and implement filtering to reduce event volume if needed.

- **Publishing directly to Production without staging:** Skipping the Staging environment means errors are only discovered in Production, potentially causing data loss at critical destinations. Always validate in Staging with live traffic first.

- **Not monitoring HTTP response codes:** A rule that fires without errors does not guarantee the destination successfully processed the data. Monitor destination response codes (available in the Event Forwarding Monitoring tool) and investigate any non-2xx responses.

- **Misconfigured XDM path references:** Data elements use the `arc.event.xdm.` prefix to reference incoming event fields. An incorrect path (for example, missing a level of nesting) silently produces null values rather than throwing errors. Validate data element values using the Debugger.

### Best practices

- **Start with a single destination and expand gradually** — Validate end-to-end event forwarding with one destination before adding additional rules and destinations. This simplifies debugging and builds confidence in the infrastructure.

- **Use consistent naming conventions** — Name data elements, rules, and libraries with a clear convention that identifies the destination, event type, and environment (for example, "Rule: Meta - Purchase Events", "DE: Order Total").

- **Implement field-level filtering for privacy** — Even if the destination claims to handle PII appropriately, apply server-side filtering to strip or hash sensitive fields before they leave the Edge Network. This is the primary governance advantage of event forwarding over client-side tags.

- **Version your configurations** — Use the library publishing workflow to maintain versioned snapshots of your event forwarding configuration. Document what each library version contains for audit and rollback purposes.

- **Test with the Platform Debugger** — The [!DNL Adobe Experience Platform Debugger] extension provides visibility into the event lifecycle from client-side SDK through Edge Network processing. Use it during development and troubleshooting.

- **Align event forwarding rules with your XDM schema design** — If event forwarding is a known requirement, design your XDM schema and event taxonomy to include the fields destinations will need. Retrofitting schema changes after deployment is more disruptive.

### Trade-off decisions

>[!NOTE]
>
>**Trade-off: Extension simplicity vs. webhook flexibility**
>
>Pre-built extensions minimize implementation effort and maintenance, but they limit you to the extension's supported features and payload formats. Custom webhooks provide full control but require more development and ongoing maintenance.
>
>- **Extension-based (Option A) favors:** Speed to market, reduced developer dependency, automatic credential management, lower maintenance
>- **Webhook-based (Option B) favors:** Full payload control, support for any HTTP endpoint, custom transformation logic, independence from extension release cycles
>- **Recommendation:** Use extensions when available and sufficient. Fall back to custom webhooks only when the destination lacks an extension or when the extension does not support the specific API features you need. The hybrid approach (Option C) is the pragmatic choice for most organizations.

>[!NOTE]
>
>**Trade-off: Forward all events vs. selective filtering**
>
>Forwarding all events to a destination ensures completeness but increases data volume, destination costs, and privacy exposure. Selective filtering reduces noise but risks missing events that may be valuable.
>
>- **Forward all events favors:** Data completeness, simplicity, future-proofing (the data is there if needed later)
>- **Selective filtering favors:** Cost efficiency, reduced privacy risk, cleaner destination data, compliance with data minimization principles
>- **Recommendation:** Default to selective filtering based on event type and business relevance. Forward only the events and fields each destination actually needs. This aligns with data minimization principles (GDPR Article 5) and reduces operational costs.

>[!NOTE]
>
>**Trade-off: Single property vs. multiple properties**
>
>A single event forwarding property is simpler to manage but means all rules share one publishing workflow. Multiple properties provide isolation but increase management overhead.
>
>- **Single property favors:** Simplicity, unified publishing, shared data elements, easier debugging
>- **Multiple properties favors:** Team-level access control, independent publishing cadences, isolation of destination failures
>- **Recommendation:** Start with a single property for most implementations. Only split into multiple properties if different teams own different destination integrations and need independent release cycles, or if regulatory requirements demand strict isolation between data flows.

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
