---
title: Customer Analytics & Insight Generation
description: Learn how to build cross-channel analysis workspaces, computed metrics, and dashboards for behavior and performance analysis.
solution: Customer Journey Analytics, Experience Platform
exl-id: 235a4eb0-91ae-4030-b90e-7eda08c67ae1
---
# Customer analytics & insight generation

This guide provides a complete implementation reference for customer analytics and insight generation. It covers how to connect [!DNL Adobe Experience Platform] datasets to [!DNL Customer Journey Analytics], configure data views, build freeform analysis workspaces, create computed metrics, publish dashboards and mobile scorecards, and optionally publish CJA-defined audiences back to [!DNL Adobe Experience Platform] for activation.

It is designed for solution architects, marketing technologists, and implementation engineers who need to understand all viable implementation paths, the trade-offs between them, and the configuration decisions required at each phase.

Unlike the other patterns in the taxonomy which focus on activation and engagement (sending messages, personalizing content, activating audiences), this pattern focuses on understanding -- analyzing customer behavior, measuring campaign performance, identifying trends, and generating insights that inform strategy and optimization decisions. It is the most commonly composed pattern and pairs with nearly every activation or personalization pattern.

## Use case overview

Organizations need to understand how customers behave across channels, how campaigns perform, where customers drop off in their journeys, which content resonates, and how different segments retain over time. Customer analytics and insight generation addresses this need by connecting the rich cross-channel data in [!DNL Adobe Experience Platform] to [!DNL Customer Journey Analytics], where analysts can build freeform workspaces, create custom metrics, configure attribution models, and publish dashboards for stakeholder consumption.

The pattern serves multiple audiences: marketing analysts who need deep exploratory analysis, campaign managers who need performance dashboards, product managers who need engagement and retention insights, and executives who need at-a-glance KPI scorecards. The implementation approach varies based on the primary analytical focus -- campaign performance measurement, cross-channel journey analysis, analysis-driven audience activation, or guided product insights.

## Key business objectives

The following business objectives are supported by this use case pattern.

**Improve analytics & reporting**

Enhance reporting capabilities for faster, more actionable marketing insights through unified dashboards and self-service tools.

- **KPIs:** Efficiency, Productivity

See [Improve Analytics & Reporting](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md) for more information on this business objective.

**Enable data-driven decision making**

Empower teams with self-service analytics, real-time customer insights, and AI-powered predictions to guide strategy.

- **KPIs:** Efficiency, Productivity

See [Enable Data-Driven Decision Making](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md) for more information on this business objective.

**Improve marketing attribution**

Accurately measure the impact of marketing touchpoints, channels, and campaigns on conversion and revenue outcomes.

- **KPIs:** Efficiency, Incremental Revenue

See [Improve Marketing Attribution](/help/blueprints/business-objectives/analytics-insights/improve-marketing-attribution.md) for more information on this business objective.

**Optimize marketing spend & ROI**

Optimize marketing budget allocation by understanding which channels and campaigns deliver the highest return.

- **KPIs:** Efficiency, Incremental Revenue

See [Optimize Marketing Spend & ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md) for more information on this business objective.

## Example tactical use cases

The following are examples of tactical use cases that can be implemented with this pattern.

- Campaign performance dashboard -- delivery metrics, engagement rates, conversion, and revenue attribution across email, SMS, push, and paid media campaigns
- Customer journey fallout analysis -- identify where customers drop off in purchase, registration, or onboarding funnels
- Cohort retention analysis -- measure how well different acquisition cohorts retain over weeks, months, and quarters
- Channel attribution modeling -- compare first-touch, last-touch, linear, and time-decay attribution to understand which channels drive conversions
- Content performance analysis -- identify which content resonates most by segment, channel, and lifecycle stage
- Product usage and adoption analytics -- track feature adoption, engagement frequency, and user growth trends
- Customer lifecycle stage analysis -- segment and analyze customers by lifecycle stage (new, active, at-risk, lapsed)
- Marketing mix optimization dashboard -- compare channel investment against revenue contribution
- Cross-channel engagement scoring and reporting -- build composite engagement scores from web, app, email, and campaign interactions

## Key performance indicators

The following KPIs help measure the success of this use case pattern.

| KPI | Description | Measurement approach |
| --- | --- | --- |
| Efficiency | Reduction in time-to-insight and manual reporting effort | Track analyst time spent building reports before and after CJA implementation |
| Productivity | Number of self-service analyses created by business users | Monitor Workspace project creation and dashboard usage |
| Incremental Revenue | Revenue attributed to insights-driven optimization decisions | Measure revenue lift from campaigns optimized based on CJA analysis |
| Conversion Rates | Funnel completion rates across key customer journeys | Track fallout rates at each journey step using CJA fallout visualization |
| Engagement | Depth and frequency of customer interaction across channels | Build computed metrics for engagement scoring in CJA |
| Retention | Customer return rates over defined time periods | Use CJA cohort analysis to measure retention curves |

## Use case pattern

**Customer analytics & insight generation**

Build cross-channel analysis workspaces, computed metrics, and dashboards to understand customer behavior and campaign performance.

**Function chain:** Data Connection > Data View Configuration > Workspace Analysis > Computed Metric Creation > Dashboard Publishing

See the [Implementation options](#implementation-options) section for composition guidance.

## Applications

The following applications are used in this use case pattern.

- **[!DNL Customer Journey Analytics] (CJA)** -- Connections, data views, workspace analysis, guided analysis, computed metrics, dashboards, audience publishing, and content analytics
- **[!DNL Adobe Experience Platform] (AEP)** -- Data lake, datasets, XDM schemas, profile and event data that feed CJA connections

## Foundational functions

The following foundational capabilities must be in place for this use case pattern. For each function, the status indicates whether it is typically required, assumed to be pre-configured, or not applicable.

| Foundational function | Status | What must be in place | Experience League reference |
| --- | --- | --- | --- |
| Administration & Governance | Assumed in Place | CJA product profile provisioned with workspace creation and data view access permissions. AEP datasets accessible to the CJA connection. Users assigned to appropriate CJA roles. | [Access control overview](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Data Modeling & Preparation | Required | XDM schemas and datasets that will be connected to CJA must exist in AEP. Schema design directly impacts what dimensions and metrics are available in CJA data views. Event schemas need timestamp fields; lookup schemas need key fields. | [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Data Sources & Collection | Required | Data must be flowing into AEP datasets -- web events via Web SDK, app events via Mobile SDK, AJO campaign events, CRM data via source connectors. The richness of the analytics depends on the breadth of data collected. | [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Identity & Profile Configuration | Required | Person ID configuration in the CJA connection determines how events are stitched across datasets. Cross-device identity stitching in AEP improves CJA's ability to build complete customer journeys. Identity namespace must be configured for the Person ID field. | [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| Audience Definition & Segmentation | Not Applicable | CJA builds its own filters and audiences within the analysis context. RT-CDP audiences are not a prerequisite, though CJA can publish audiences back to AEP via audience publishing (Option C). | [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## Supporting functions

The following capabilities augment this use case pattern but are not required for core execution.

| Supporting function | Status | Why it matters | Experience League reference |
| --- | --- | --- | --- |
| Computed / Derived Attribute Creation | Recommended | AEP computed attributes can enrich the datasets connected to CJA, providing additional dimensions and metrics for analysis (e.g., lifetime purchase count, days since last activity). These profile-level aggregations become available as dimensions in CJA data views. | [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Recommended | Dataset retention policies affect what historical data is available in CJA. Long retention is typically desired for analytics to enable year-over-year comparisons and long-term trend analysis. Configure dataset TTLs to ensure adequate historical depth. | [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Data Usage Labeling & Enforcement | Recommended | Governance labels on sensitive fields can restrict what appears in CJA data views. If PII or sensitive data is included in the CJA connection, data governance labels ensure compliant access and prevent unauthorized exposure in shared dashboards. | [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Monitoring & Observability | Recommended | CJA connection health and data freshness should be monitored. Configure alerts for source dataflow failures and ingestion issues to ensure the data feeding CJA is reliable and current. | [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting & Analysis | Included | This is the reporting and analysis implementation. When a reference plan for another pattern includes S5, use this customer analytics and insight generation plan for the analytics implementation. | [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Application functions

This plan exercises the following functions from the application function catalog. Functions are mapped to implementation phases rather than numbered steps.

### [!DNL Customer Journey Analytics] (CJA)

The following table lists the CJA application functions used in this pattern.

| Function | Implementation phase | Description |
| --- | --- | --- |
| Data Connection | Phase 1: Data Connection | Bind AEP datasets to a CJA connection for cross-channel analysis, configuring dataset types and Person ID for cross-dataset stitching |
| Data View Configuration | Phase 2: Data View Configuration | Define dimensions, metrics, attribution models, persistence settings, session parameters, and derived fields that shape the analytical perspective |
| Workspace Analysis | Phase 3: Analysis & Metric Creation | Build freeform analysis projects with tables, visualizations, filters, annotations, and dimension breakdowns (Options A, B, C) |
| Guided Analysis | Phase 3: Analysis & Metric Creation | Use structured guided workflows for funnel, trends, retention, user growth, and engagement frequency analysis (Option D) |
| Computed Metric Creation | Phase 3: Analysis & Metric Creation | Define calculated metrics using formulas, filters, and functions for reusable KPIs like conversion rate, engagement score, and revenue per visit |
| Dashboard & Scorecard Publishing | Phase 4: Dashboard Publishing | Create and share interactive dashboards and mobile scorecards for stakeholder reporting |
| Audience Publishing | Phase 5: Audience Publishing (Option C only) | Publish CJA-defined audiences back to AEP Real-Time Customer Profile for downstream activation |
| Content Analytics | Phase 3: Analysis & Metric Creation | Analyze content performance trends, anomalies, and fatigue across digital properties (when content analysis is the focus) |

### [!DNL Adobe Experience Platform] (AEP)

The following table lists the AEP application functions used in this pattern.

| Function | Implementation phase | Description |
| --- | --- | --- |
| Data Lake & Datasets | Prerequisite (F2, F3) | Provide the source event, profile, and lookup datasets that feed the CJA connection |
| Identity Service | Prerequisite (F4) | Provide identity namespace configuration for Person ID stitching across datasets in the CJA connection |

## Prerequisites

The following prerequisites must be met before implementing this use case pattern.

- [ ] CJA product entitlement is provisioned for the organization
- [ ] CJA product profiles are configured with appropriate user access (workspace creation, data view access)
- [ ] AEP sandbox contains the target datasets with data flowing (web events, app events, campaign data, CRM records)
- [ ] XDM schemas are defined for all source datasets with appropriate field groups
- [ ] Person ID field is identified and consistently available across all datasets that will be connected
- [ ] Identity namespaces are configured in AEP for the Person ID used in CJA connection stitching
- [ ] Stakeholder requirements are documented -- which KPIs, which audiences will consume dashboards, what level of detail
- [ ] For mobile scorecards: stakeholders have the [!DNL Adobe Analytics] dashboards mobile app installed
- [ ] For Option C (Audience Publishing): AEP Real-Time Customer Profile is enabled in the target sandbox
- [ ] For Option D (Guided Analysis): CJA SKU includes guided analysis capabilities

## Implementation options

This section describes the available implementation options for this use case pattern.

### Option A: Campaign performance analytics

**Best for:** Measuring and optimizing campaign and journey effectiveness -- email campaign dashboards, journey funnel analysis, channel performance comparison, and marketing ROI reporting.

**How it works:**

This option connects AJO campaign and journey datasets to CJA, configures data views with delivery and engagement metrics (sends, deliveries, opens, clicks, bounces, unsubscribes), builds campaign performance dashboards, and publishes scorecards for marketing stakeholders. The focus is on understanding how marketing campaigns perform across channels and over time.

The data view is configured with campaign-specific dimensions (campaign name, journey name, channel type, message variant) and delivery metrics. Computed metrics are created for derived measures such as open rate, click-through rate, conversion rate, and revenue per message. Dashboards present these KPIs with comparison periods for trend analysis.

**Key considerations:**

- Requires AJO campaign and journey event datasets in AEP
- Attribution models should align with the organization's campaign measurement philosophy
- Consider including both AJO native reports (for operational delivery metrics) and CJA (for cross-channel business impact)

**Advantages:**

- Purpose-built for campaign measurement and optimization
- Enables cross-campaign comparison and channel mix analysis
- Computed metrics provide standardized KPI definitions across all campaigns
- Mobile scorecards deliver at-a-glance performance for marketing leaders

**Limitations:**

- Limited to campaign and journey data; does not provide full customer journey context
- Does not include journey pathing, fallout, or cohort analysis
- Attribution is scoped to campaign touchpoints rather than the full customer journey

**Experience League:**

- [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Option B: Customer journey analytics

**Best for:** Understanding cross-channel customer journeys -- fallout analysis, path analysis, cohort retention, attribution modeling, and lifecycle stage analysis across web, app, email, CRM, and offline touchpoints.

**How it works:**

This option connects multiple AEP datasets (web events, app events, CRM data, campaign interactions, transactional records) to build a unified cross-channel view of the customer journey. The data view is configured with dimensions and metrics spanning all channels. CJA's flow, fallout, cohort, and attribution visualizations are used to analyze how customers move through journeys, where they drop off, how different segments retain, and which channels deserve credit for conversions.

This is the most comprehensive analytical option, providing deep insight into the end-to-end customer experience. It is also the most complex to implement, requiring careful Person ID configuration for cross-dataset stitching and thoughtful data view design to expose the right dimensions and metrics.

**Key considerations:**

- Requires consistent Person ID across all connected datasets for accurate cross-channel analysis
- Schema design in AEP directly impacts the quality and depth of CJA analysis
- More datasets in the connection means richer analysis but longer backfill times
- Attribution modeling requires clear conversion event definitions

**Advantages:**

- Complete cross-channel customer journey visibility
- Full suite of CJA visualizations: flow, fallout, cohort, attribution, freeform tables
- Enables discovery of insights that are invisible in single-channel reporting
- Supports complex analytical questions about customer behavior and lifecycle

**Limitations:**

- Higher implementation complexity due to multi-dataset connections and cross-channel stitching
- Requires more upfront planning for data view configuration and derived fields
- Backfill for large multi-dataset connections can take days
- Analysis quality depends on the completeness and consistency of the underlying data

**Experience League:**

- [Connections overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Flow visualization](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Fallout visualization](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Cohort table](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Attribution panel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)

### Option C: Analytics with audience publishing

**Best for:** Analysis-driven activation -- discover interesting segments through CJA analysis, then publish them back to AEP for activation via RT-CDP destinations, AJO campaigns, or AJO journeys.

**How it works:**

This option extends Option A or Option B with audience publishing from CJA. Analysts build segments in CJA using cross-channel behavioral data and the full analytical power of CJA filters, then publish those audiences to AEP Real-Time Customer Profile for downstream activation. This bridges the gap between insight and action -- segments discovered during exploratory analysis become actionable audiences without requiring manual recreation in AEP Segment Builder.

Published audiences appear in the AEP Audience Portal with origin "CJA" and can be activated to any RT-CDP destination, used as campaign targets in AJO, or used as journey entry conditions.

**Key considerations:**

- Requires AEP Real-Time Customer Profile to be enabled in the target sandbox
- CJA connection must have a valid Person ID that resolves to an AEP identity namespace
- Published audiences count toward the organization's AEP audience entitlement
- Refresh cadence must be configured based on activation requirements (one-time, every 4 hours, daily, weekly)

**Advantages:**

- Closes the loop between analysis and activation
- Enables discovery of high-value segments using CJA's cross-channel behavioral data
- Audiences defined in CJA can leverage dimensions and filters not available in AEP Segment Builder
- Supports iterative refinement of audience criteria based on analytical insights

**Limitations:**

- Maximum of 75 published audiences per CJA customer
- Initial audience evaluation may take up to 24 hours for large datasets
- CJA-published audiences cannot be edited in AEP -- changes must be made in CJA
- Requires additional identity namespace and profile configuration beyond basic analytics

**Experience League:**

- [Audiences overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Create and publish audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)

### Option D: Guided analysis for product teams

**Best for:** Product experience insights -- feature adoption, user engagement trends, retention analysis, funnel conversion, and release impact analysis using CJA's guided analysis workflows without requiring complex freeform Workspace project setup.

**How it works:**

This option uses CJA Guided Analysis for structured, templated insight generation. Guided analysis provides pre-built analysis types -- funnel, trends, retention, user growth, engagement frequency, release impact, first use, and timeline -- that walk analysts through a structured workflow to answer specific product and experience questions. It is ideal for product managers and analysts who need quick, focused insights without building freeform projects from scratch.

The implementation connects AEP datasets to CJA, configures a data view with event-level dimensions and metrics, and then uses guided analysis workflows to generate insights. Results can be saved as panels within Workspace projects for further customization.

**Key considerations:**

- Guided analysis requires CJA product entitlement that includes guided analysis capabilities
- Best suited for product and experience analytics rather than campaign performance measurement
- Provides structured workflows that are more accessible to non-analyst users
- Can be combined with freeform Workspace analysis for deeper exploration

**Advantages:**

- Lower barrier to entry -- structured workflows guide users through the analysis
- Purpose-built for product experience questions (funnel, retention, growth, impact)
- Faster time-to-insight for common analytical questions
- Saved analyses can be embedded in Workspace projects alongside freeform analysis

**Limitations:**

- Less flexible than freeform Workspace analysis
- Limited to the pre-built analysis types (funnel, trends, retention, growth, frequency, impact, timeline)
- Segment comparisons support up to 3 segments simultaneously
- Funnel analysis supports a maximum of 15 steps

**Experience League:**

- [Guided analysis overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Funnel view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Retention view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

### Option comparison

The following table compares the available implementation options.

| Criteria | Option A: Campaign performance | Option B: Customer journey | Option C: Analytics + activation | Option D: Guided analysis |
| --- | --- | --- | --- | --- |
| Best for | Campaign measurement and optimization | Cross-channel journey understanding | Insight-driven audience activation | Product experience insights |
| Complexity | Low-Medium | High | High | Low |
| Datasets required | AJO campaign/journey events | Multiple cross-channel datasets | Same as A or B, plus profile identity | Event datasets with product interactions |
| Key visualizations | Freeform tables, summary numbers, trend lines | Flow, fallout, cohort, attribution | Same as A or B, plus audience publishing | Funnel, trends, retention, growth |
| Activation capability | No (reporting only) | No (reporting only) | Yes (publishes audiences to AEP) | No (reporting only) |
| Audience required | Marketing analysts, campaign managers | Data analysts, journey architects | Analysts + activation teams | Product managers, growth analysts |
| CJA functions used | Connection, Data View, Workspace, Computed Metrics, Dashboard | Connection, Data View, Workspace, Computed Metrics, Dashboard | Same as A or B, plus Audience Publishing | Connection, Data View, Guided Analysis, Dashboard |
| Time to first insight | Days | Weeks | Weeks | Hours-Days |

### Choose the right option

Use the following guidance to select the implementation option that best fits your needs.

- **If your primary goal is measuring campaign effectiveness** and you have AJO campaign data flowing into AEP, start with **Option A**. It delivers the fastest time-to-value for marketing performance reporting.

- **If you need to understand the full customer journey** across web, app, email, and offline touchpoints, and you have multiple datasets with a consistent Person ID, choose **Option B**. It provides the deepest analytical capabilities but requires more upfront investment in data view configuration.

- **If you want to act on insights** by publishing CJA-discovered segments back to AEP for activation in RT-CDP or AJO, choose **Option C**. This extends Option A or B with audience publishing and requires AEP Real-Time Customer Profile configuration.

- **If your team needs quick, structured product insights** without the complexity of freeform Workspace projects, and your CJA SKU includes guided analysis, choose **Option D**. It is the fastest path to answering specific product experience questions.

- **Many organizations implement multiple options**: Option A for marketing team campaign dashboards, Option B for the analytics team's cross-channel analysis, and Option D for product team self-service insights. These options share the same CJA connection and data view infrastructure.

## Implementation phases

This section details the step-by-step implementation phases for this use case pattern.

### Phase 1: Data connection

**Application function:** CJA: Data Connection

This phase configures a CJA connection that binds one or more AEP datasets to CJA for analysis. The connection defines which datasets flow into CJA, how events are stitched across datasets via the Person ID, and how historical and streaming data are ingested. This is the foundational link between AEP's data lake and CJA.

#### Decision points

The following decisions must be made during this phase.

>[!NOTE]
>**Decision: AEP sandbox selection**
>
>Which AEP sandbox contains the source datasets?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Production sandbox | Live customer data for production reporting | Use for production dashboards and stakeholder reporting |
>| Development sandbox | Testing and iteration before production deployment | Use for initial configuration and validation before promoting to production |

>[!NOTE]
>**Decision: Dataset selection and type designation**
>
>Which AEP datasets should be included in the connection, and what type should each be assigned?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Event datasets | Timestamped behavioral data (web interactions, app events, campaign interactions, transactions) | Require a timestamp field; form the core of most analyses |
>| Lookup datasets | Key-value reference data (product catalog, campaign metadata, store locations) | Joined to event data via a shared key; only latest state is used |
>| Profile datasets | Person-level attributes (loyalty tier, lifetime value, CRM attributes) | Provide enrichment at the person level; only latest state is used |

>[!NOTE]
>**Decision: Person ID configuration**
>
>What field serves as the Person ID for cross-dataset stitching?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| CRM ID | Organization has a consistent CRM identifier across channels | Provides the most accurate cross-channel stitching for known customers |
>| ECID (Experience Cloud ID) | Primarily analyzing anonymous web/app behavior | Device-scoped; does not stitch across devices without identity resolution |
>| Email (hashed) | Email is the common identifier across datasets | Works well when email is consistently captured across touchpoints |
>| Custom namespace | Organization uses a proprietary identifier | Must match an AEP identity namespace for audience publishing (Option C) |

>[!NOTE]
>**Decision: Backfill range**
>
>How much historical data should be imported into the connection?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| All existing data | Maximum historical depth needed for year-over-year comparisons and long-term trends | Backfill for large datasets (billions of records) may take days to complete |
>| Custom date range | Only recent history is relevant, or storage optimization is a concern | Limits the historical depth available for analysis |
>| No backfill | Only forward-looking analysis is needed | Fastest connection setup; no historical data available until new data flows in |

>[!NOTE]
>**Decision: Streaming enablement**
>
>Should new data flow into CJA in near real-time?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Enable streaming | Near real-time reporting is needed (data available within ~90 minutes of AEP ingestion) | Most common for production connections; enables timely analysis |
>| Batch only | Periodic refresh is sufficient and streaming is not needed | Simpler configuration; data available after batch processing |

#### Configure data connection

**UI navigation:** CJA > Connections > Create new connection

Key configuration details:

- Connection name and description should follow organizational naming conventions
- Average number of daily events is used for CJA capacity planning
- All datasets in a single connection must come from the same AEP sandbox
- Person ID fields must be consistent across all datasets for accurate cross-dataset stitching
- Verify that the Person ID field exists and is populated in each dataset before adding it to the connection

**Experience League documentation:**

- [Connections overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Create or edit a connection](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Manage connections](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)
- [CJA guardrails](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

### Phase 2: Data view configuration

**Application function:** CJA: Data View Configuration

This phase configures a data view that defines how connection data appears in analysis. The data view determines which schema fields are exposed as dimensions and metrics, how values are attributed and persisted, how sessions are defined, and what derived fields transform raw data into analysis-ready components. Multiple data views can be created from a single connection for different analytical perspectives.

#### Decision points

The following decisions must be made during this phase.

>[!NOTE]
>**Decision: Container naming**
>
>What terminology should the containers use to match the business domain?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Default (Person / Session / Event) | Standard analytics terminology is understood by the team | Works for most implementations |
>| Custom names (e.g., Shopper / Visit / Interaction) | Business domain-specific terminology improves user adoption | Helps non-technical stakeholders understand scope of analysis |
>| B2B names (e.g., Account / Engagement / Touchpoint) | B2B analytics where account-level analysis is the focus | Aligns container scope with B2B business concepts |

>[!NOTE]
>**Decision: Session timeout**
>
>How long of inactivity defines a session boundary?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| 30 minutes (default) | Standard web analytics session definition | Industry standard; aligns with most analytics benchmarks |
>| 15 minutes | Short-form content or transactional sites where users complete tasks quickly | Creates more sessions; may better capture distinct user intents |
>| 60 minutes or longer | Long-form content, complex B2B interactions, or research-heavy journeys | Fewer sessions; captures extended research as single sessions |
>| Custom with new session events | Certain events (e.g., app launch, campaign click-through) should always start a new session | Provides business-logic-driven session boundaries |

>[!NOTE]
>**Decision: Attribution model defaults**
>
>What default attribution model should be applied to conversion metrics?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Last touch (default) | Credit should go to the most recent touchpoint before conversion | Simple and intuitive; may undervalue awareness channels |
>| First touch | Understanding which channels drive initial awareness and acquisition | Useful for acquisition analysis; ignores nurture touchpoints |
>| Linear | All touchpoints should share equal credit | Fair distribution; may dilute the impact of key touchpoints |
>| Time decay | Recent touchpoints should receive more credit than distant ones | Balances recency with historical contribution |
>| U-shaped | First and last touchpoints deserve the most credit | Good for understanding both acquisition and closing channels |
>| Algorithmic | Data-driven attribution using CJA's AI models | Most accurate but requires sufficient conversion data volume |

>[!NOTE]
>**Decision: Derived field logic**
>
>Are custom business rules needed to transform raw data into analysis-ready dimensions?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Marketing channel classification (Case When) | Raw tracking codes need to be classified into channel groups | Most common derived field use case; critical for channel analysis |
>| Value bucketing | Continuous values need to be grouped into ranges (e.g., order value tiers) | Simplifies analysis of continuous metrics |
>| Field merging | Multiple source fields should be combined into a single dimension | Useful when the same concept exists in different schema paths across datasets |
>| Regex-based extraction | Structured values need to be parsed (e.g., extracting campaign type from campaign code) | Powerful but requires careful regex pattern design |

#### Configure data view

**UI navigation:** CJA > Data views > Create new data view

Key configuration details:

- Select the parent connection created in Phase 1
- Configure time zone and calendar type to match reporting requirements
- Map XDM schema fields to dimensions with appropriate persistence (allocation and expiration) settings
- Map XDM schema fields to metrics with format (decimal, integer, currency, percentage, time) and attribution settings
- Configure include/exclude rules on dimensions to filter out irrelevant values
- Enable metric deduplication where needed to prevent double-counting
- Create derived fields for marketing channel classification, value bucketing, or field merging
- Maximum of 5,000 dimensions and 5,000 metrics per data view
- Maximum of 100 derived fields per data view

#### Where options diverge

**For Option A (Campaign performance analytics):**

Map campaign-specific dimensions: campaign name, journey name, channel type, message variant, subject line. Map delivery metrics: sends, deliveries, opens, clicks, bounces, unsubscribes. Configure attribution on conversion metrics based on campaign measurement philosophy.

**For Option B (Customer journey analytics):**

Map cross-channel dimensions: page name, app screen, channel, campaign, product, content type. Map engagement and conversion metrics across all channels. Configure multiple attribution models for comparison analysis. Create derived fields for channel classification and journey stage identification.

**For Option D (Guided analysis):**

Map event-level dimensions and metrics relevant to product experience analysis: feature name, user action, engagement type. Focus on events that define funnel steps, retention criteria, and growth signals.

**Experience League documentation:**

- [Data views overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Create or edit a data view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Component settings overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Persistence settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Attribution settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Format settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Metric deduplication](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [Include/exclude values](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [Session settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)
- [Derived fields](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)

### Phase 3: Analysis & metric creation

**Application function:** CJA: Workspace Analysis, CJA: Guided Analysis, CJA: Computed Metric Creation

This phase builds the analysis workspaces (freeform projects or guided analysis), computed metrics for derived KPIs, filters for segmented analysis, and annotations for key events. This is where the analytical value is realized -- building the tables, visualizations, and metrics that answer business questions.

#### Decision points

The following decisions must be made during this phase.

>[!NOTE]
>**Decision: Analysis approach**
>
>Should this analysis use freeform Workspace projects or guided analysis workflows?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Freeform Workspace (Options A, B, C) | Deep exploratory analysis, custom layouts, complex breakdowns, advanced visualizations | Maximum flexibility; requires analyst skill; supports all visualization types |
>| Guided Analysis (Option D) | Structured product insights, quick answers to specific questions, less technical users | Faster time-to-insight; limited to pre-built analysis types; saves to Workspace for further customization |
>| Both | Organization needs both deep analysis and quick structured insights | Use guided analysis for common questions; Workspace for deep exploration |

>[!NOTE]
>**Decision: Visualization types**
>
>What visualizations best communicate the insights for this use case?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Freeform table | Detailed data exploration with dimension breakdowns | Foundation of most analyses; supports up to 10 breakdown levels |
>| Flow visualization | Understanding pathing behavior (page flow, channel transitions) | Excellent for journey path discovery; can be complex with high cardinality |
>| Fallout visualization | Measuring conversion through a defined sequence of touchpoints | Best for funnel analysis; clearly shows drop-off at each step |
>| Cohort table | Retention analysis over time by acquisition cohort | Shows how well different groups retain; critical for lifecycle analysis |
>| Attribution panel | Comparing attribution models for conversion metrics | Side-by-side model comparison; requires clear conversion event definition |
>| Summary number / change | Executive KPI display with period-over-period comparison | Clean, at-a-glance metric display; ideal for dashboard headers |

>[!NOTE]
>**Decision: Computed metric formulas**
>
>What business KPIs require computed metrics beyond base data view metrics?
>
>| Metric pattern | Formula example | When to use |
>| --- | --- | --- |
>| Ratio / Rate | Orders / Visits | Conversion rate, click-through rate, bounce rate |
>| Filtered metric | Revenue (where channel = "email") | Channel-specific or segment-specific measures |
>| Per-item average | Revenue / Orders | Average order value, revenue per visit |
>| Compound formula | (Revenue - Cost) / Revenue | Margin percentage, ROI calculations |
>| Engagement score | Weighted sum of interactions | Composite engagement scoring across channels |

#### Configure analysis and metrics

**UI navigation:**

- Workspace: CJA > Workspace > Projects > Create project > Blank project
- Guided Analysis: CJA > Home > Guided Analysis (or Workspace > Create > Guided analysis)
- Computed Metrics: CJA > Components > Calculated metrics > Create
- Filters: CJA > Components > Filters > Create filter

Key configuration details:

- Select the data view created in Phase 2 as the project data view
- Set appropriate date ranges and comparison periods for the analysis
- Build freeform tables by dragging dimensions to rows and metrics to columns
- Add dimension breakdowns to explore data at deeper levels (e.g., channel by campaign, page by product)
- Create reusable filters (segments) for audience-specific analysis (person-level, session-level, or event-level scope)
- Add annotations to mark key business events (product launches, campaigns, incidents)
- Set computed metric format (decimal, percent, currency, time) and polarity (up is good / up is bad)
- Share workspace projects with CJA users at view or edit permissions

#### Where options diverge

**For Option A (Campaign performance analytics):**

Build freeform tables with campaign dimensions broken down by delivery and engagement metrics. Create computed metrics for open rate, click-through rate, conversion rate, revenue per message, and campaign ROI. Add trend visualizations to track campaign performance over time. Compare campaign variants with segment comparison.

**For Option B (Customer journey analytics):**

Build fallout visualizations to identify journey drop-off points. Create flow visualizations to discover navigation patterns across channels. Build cohort tables to measure retention by acquisition cohort. Configure the attribution panel to compare attribution models for conversion metrics. Create computed metrics for journey completion rate, cross-channel engagement score, and lifecycle stage conversion.

**For Option C (Analytics with audience publishing):**

Build the analysis workspaces from Option A or B, then identify high-value or underperforming segments during analysis. Create CJA filters that capture these segments for publishing in Phase 5.

**For Option D (Guided analysis):**

Select the appropriate guided analysis type based on the business question. Configure key events, date ranges, counting methods, and segment comparisons. Save completed analyses as panels in Workspace projects for further customization.

**Experience League documentation:**

- [Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Create a project](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Freeform table](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Flow visualization](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Fallout visualization](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Cohort table](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Attribution panel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Breakdown dimensions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [Filters overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Create filters](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Annotations overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Calculated metrics overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Create calculated metrics](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Calculated metric functions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [Guided analysis overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Funnel view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Trends view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Retention view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [Active growth view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [Engagement frequency view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [Release impact view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/release)
- [Content Analytics](https://experienceleague.adobe.com/en/docs/analytics-platform/using/content-analytics/content-analytics)

### Phase 4: Dashboard publishing

**Application function:** CJA: Dashboard & Scorecard Publishing

This phase creates interactive dashboards (Workspace projects) and mobile scorecards that deliver KPI visibility to stakeholders. Dashboards provide executive and operational visibility through summary numbers, trend lines, breakdowns, and annotations. Mobile scorecards deliver at-a-glance performance data via the [!DNL Adobe Analytics] dashboards mobile app.

#### Decision points

The following decisions must be made during this phase.

>[!NOTE]
>**Decision: Dashboard type**
>
>Is this a desktop Workspace dashboard, a mobile scorecard, or both?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Workspace project (desktop) | Detailed interactive dashboards for analysts and marketers | Full visualization capabilities; supports panels, tables, and complex layouts |
>| Mobile scorecard | At-a-glance KPIs for executives and stakeholders on mobile devices | Limited to 16 tiles; summary numbers with trend sparklines; requires mobile app |
>| Both | Organization needs both detailed analysis and executive-level mobile reporting | Separate artifacts but can share the same data view and computed metrics |

>[!NOTE]
>**Decision: Sharing model**
>
>Who should receive the dashboard and how?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Share with specific users | Limited audience with specific access needs | Most granular control; requires individual user management |
>| Share with product profile group | Team-level access aligned with organizational roles | Efficient for team-wide distribution; managed via CJA product profiles |
>| Schedule email delivery | Recurring PDF/CSV reports for stakeholders who do not log into CJA | Automated delivery; maximum frequency is hourly; PDF and CSV formats |

>[!NOTE]
>**Decision: Annotation visibility**
>
>Should key events be annotated on dashboard trend lines?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Yes -- create annotations | Major campaigns, product launches, site incidents, or seasonal events may explain data trends | Annotations appear as markers on line charts and scorecard trends; provide context for data spikes or dips |
>| No | Dashboard audience is familiar with business context and annotations would add clutter | Simpler visual presentation |

#### Configure dashboards

**UI navigation:**

- Workspace dashboards: CJA > Workspace > Create project
- Mobile scorecards: CJA > Projects > Create > Mobile scorecard
- Sharing: CJA > Workspace > Share > Share with Workspace users
- Scheduled delivery: CJA > Workspace > Share > Schedule project

Key configuration details:

- For mobile scorecards, create tiles that display a single metric with a summary number and sparkline trend
- Configure default date ranges and comparison periods (e.g., last 30 days vs. previous period, or month-over-month)
- Add audience-scoped filters that executives can toggle on mobile scorecards
- Configure scheduled email delivery for recurring PDF or CSV reports
- Maximum of 16 tiles per mobile scorecard; maximum of 15 panels per Workspace project
- Annotations are limited to 100 per data view

**Experience League documentation:**

- [Create a mobile scorecard](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Configure and curate scorecards](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics dashboards -- executive guide](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Share projects](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Schedule projects](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Summary number visualization](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)
- [Date ranges](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

### Phase 5: Audience publishing (Option C only)

**Application function:** CJA: Audience Publishing

This phase configures CJA audience publishing to push analysis-discovered segments back to AEP Real-Time Customer Profile for downstream activation in RT-CDP destinations, AJO campaigns, or AJO journeys.

#### Decision points

The following decisions must be made during this phase.

>[!NOTE]
>**Decision: Refresh cadence**
>
>How frequently should the audience membership be refreshed?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| One-time (snapshot) | Campaign-specific audience that does not need ongoing refresh | No ongoing processing; must republish for updates |
>| Every 4 hours | Near-real-time activation requirements | Higher processing cost; best for time-sensitive audiences |
>| Daily | Standard marketing activation cadence | Balanced freshness and cost; most common choice |
>| Weekly | Stable, slow-changing audiences | Minimal processing; suitable for long-term segments |

>[!NOTE]
>**Decision: Identity namespace**
>
>Which identity namespace should CJA use for audience member resolution?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| CRM ID | Organization's primary customer identifier | Best accuracy for known customer matching |
>| ECID | Primarily web/app-based audiences | Device-scoped; may not resolve to all profile records |
>| Email (hashed) | Email is the common identifier for activation | Must match the namespace used in AEP identity configuration |
>| Custom namespace | Proprietary identifier used across the organization | Must be configured in AEP Identity Service |

#### Configure audience publishing

**UI navigation:** CJA > Components > Audiences > Publish audience

Key configuration details:

- Define audience criteria using CJA filters (person, session, or event container scope)
- Select the data view and filter to publish
- Configure the identity namespace for AEP profile resolution
- Set the refresh cadence based on activation needs
- Monitor publishing status in the CJA Audiences list (Components > Audiences > Status column)
- Verify the audience appears in AEP Audience Portal (Audiences > Browse > Filter by origin "CJA")
- Maximum of 75 published audiences per CJA customer (across all sandboxes)
- Initial audience evaluation may take up to 24 hours for large datasets

**Experience League documentation:**

- [Audiences overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Create and publish audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [Manage audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)
- [Audience Portal overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-portal)

## Implementation considerations

This section covers guardrails, common pitfalls, best practices, and trade-off decisions for this use case pattern.

### Guardrails & limits

The following guardrails and limits apply to this implementation.

- **Connection limits:** Maximum number of connections per organization is limited by CJA SKU entitlement. A single connection can include datasets from only one AEP sandbox. -- [CJA guardrails](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)
- **Data view limits:** Maximum of 5,000 dimensions and 5,000 metrics per data view. Maximum of 100 derived fields per data view with up to 5 levels of nested functions.
- **Workspace limits:** Maximum of 40 panels per project. Freeform tables support up to 10 dimension breakdowns deep. Maximum of 50,000 rows per report request.
- **Scorecard limits:** Maximum of 16 tiles per mobile scorecard.
- **Streaming latency:** Streaming data is typically available in CJA within 90 minutes of AEP ingestion.
- **Audience publishing limits:** Maximum of 75 published audiences per CJA customer. Minimum refresh cadence is every 4 hours.
- **Guided analysis limits:** Funnel analysis supports a maximum of 15 steps. Segment comparisons support up to 3 segments simultaneously.

### Common pitfalls

Be aware of the following common issues when implementing this pattern.

- **Person ID mismatch across datasets:** All datasets in a connection must use a consistent Person ID field for cross-dataset analysis. Mismatched Person IDs result in fragmented customer views where the same person appears as multiple people. Verify Person ID consistency before creating the connection.

- **Backfill taking unexpectedly long:** Large datasets with billions of records can take days to backfill. Plan for this during implementation timelines and start the backfill early. Monitor progress in the connection details view.

- **Data view showing "Unspecified" for most dimension values:** The mapped schema field may be sparsely populated in the source data. Check the source dataset for data quality before assuming a configuration error. Consider using a derived field to handle null values.

- **Session counts seem incorrect:** Session timeout settings dramatically affect session-scoped metrics. A very short timeout creates more sessions; a very long timeout creates fewer. New session start events may also fragment sessions unexpectedly. Review and test session settings against known user behavior patterns.

- **Attribution model not applying as expected:** Attribution models only apply to metrics, not dimensions. Verify the lookback window is set appropriately for the business cycle. Short lookback windows may miss early-funnel touchpoints.

- **Computed metrics returning zeros or unexpected values:** Verify that the base metrics referenced in the formula have data in the target data view for the selected date range. Check for division by zero in ratio metrics. Retrieve the metric definition and verify the formula structure.

- **Audience publishing fails (Option C):** The CJA connection must have a valid Person ID that resolves to an AEP identity namespace. Verify identity namespace configuration and that AEP Real-Time Customer Profile is enabled in the target sandbox.

### Best practices

Follow these best practices for a successful implementation.

- **Start with a single comprehensive connection:** Create one connection that includes all relevant datasets, then create multiple data views for different analytical perspectives. This avoids connection proliferation and simplifies management.

- **Use derived fields for marketing channel classification:** Rather than relying on raw tracking codes, create derived fields with Case When logic to classify traffic into marketing channels. This ensures consistent channel reporting across all analyses.

- **Create a metric dictionary:** Document all computed metrics with their formulas, intended use, and expected value ranges. Share this dictionary with the analysis team to ensure consistent metric usage across projects.

- **Design data views for your audience:** Create separate data views for different stakeholder groups -- a marketing data view with campaign-focused dimensions and metrics, and a product data view with feature and engagement dimensions. This simplifies the component lists for each user group.

- **Annotate everything:** Create annotations for campaign launches, site changes, technical incidents, seasonality, and any event that might explain data trends. Annotations provide critical context when reviewing dashboards months later.

- **Test computed metrics against manual calculations:** Before relying on a computed metric for dashboards, run a report with the computed metric and its base components side by side. Verify the computed values match a manual calculation.

- **Use filters strategically:** Create reusable filters for common segmentation patterns (new vs. returning, mobile vs. desktop, by geography). Apply these as panel-level filters rather than embedding them in every freeform table.

- **Monitor connection health regularly:** Check the connection details view for skipped records, failed batches, and streaming delays. Data quality issues at the connection level affect all downstream analysis.

### Trade-off decisions

Consider the following trade-offs when planning your implementation.

>[!NOTE]
>**Trade-off: Analysis depth vs. time-to-insight**
>
>Option B (Customer journey analytics) provides the deepest cross-channel insights but requires significant upfront investment in connection configuration, data view design, and derived field creation. Option D (Guided analysis) delivers faster time-to-insight with structured workflows but offers less analytical flexibility.
>
>- **Option B favors:** Comprehensive understanding, complex multi-channel analysis, attribution modeling, custom KPI development
>- **Option D favors:** Speed, accessibility for non-analyst users, structured product experience questions
>- **Recommendation:** Start with Option D for immediate product insights while building the Option B infrastructure in parallel. Many organizations run both simultaneously for different teams.

>[!NOTE]
>**Trade-off: Backfill completeness vs. connection readiness**
>
>Importing all historical data provides maximum analytical depth for year-over-year comparisons and long-term trend analysis, but backfill for large datasets can take days. Limiting backfill to a recent period gets the connection ready faster but limits historical analysis.
>
>- **All data favors:** Long-term trend analysis, year-over-year comparisons, cohort analysis with extended history
>- **Limited backfill favors:** Faster connection readiness, quicker time to first dashboard, storage optimization
>- **Recommendation:** Backfill all data for production connections that support strategic analysis. Use limited backfill for development connections and proof-of-concept implementations.

>[!NOTE]
>**Trade-off: Single comprehensive data view vs. multiple focused data views**
>
>A single data view with all dimensions and metrics provides a unified analytical workspace but can overwhelm users with component lists. Multiple focused data views (one per team or use case) simplify the component experience but require maintaining multiple configurations.
>
>- **Single data view favors:** Unified analysis, cross-domain breakdowns, simpler management
>- **Multiple data views favors:** Cleaner component lists, team-specific terminology, different session definitions per use case
>- **Recommendation:** Start with one primary data view, then create additional focused data views if component list complexity becomes a barrier to adoption. All data views can reference the same connection.

>[!NOTE]
>**Trade-off: Real-time streaming vs. batch-only ingestion**
>
>Enabling streaming on the CJA connection provides near-real-time data (within ~90 minutes of AEP ingestion) but processes more data continuously. Batch-only ingestion processes data periodically and may introduce delays.
>
>- **Streaming favors:** Timely reporting, monitoring active campaigns, near-real-time dashboards
>- **Batch-only favors:** Simpler configuration, predictable processing windows, sufficient for weekly or monthly reporting
>- **Recommendation:** Enable streaming for production connections. The incremental processing cost is minimal compared to the value of timely data for active campaign monitoring and operational dashboards.

## Related documentation

The following resources provide additional information for this use case pattern.

### [!DNL Customer Journey Analytics] -- Getting started

- [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [CJA guardrails](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

### Connections

- [Connections overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Create or edit a connection](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Manage connections](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)

### Data views

- [Data views overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Create or edit a data view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Component settings overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Persistence settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Attribution settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Format settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Metric deduplication](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [Include/exclude values](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [Session settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)
- [Derived fields](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)

### Workspace & analysis

- [Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Create a project](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Freeform table](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Flow visualization](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Fallout visualization](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Cohort table](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Attribution panel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Breakdown dimensions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [Share projects](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Schedule projects](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Export overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/export/export-cloud)

### Guided analysis

- [Guided analysis overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Funnel view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Trends view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Engagement frequency view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [Retention view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [Active growth view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [Release impact view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/release)
- [First use impact view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/first-use)
- [Timeline view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/streams/timeline)

### Components

- [Filters overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Create filters](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Calculated metrics overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Create calculated metrics](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Calculated metric functions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [Annotations overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Date ranges](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)
- [Metrics component](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/apply-create-metrics)

### Audience publishing

- [Audiences overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Create and publish audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [Manage audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)

### Content analytics

- [Content Analytics](https://experienceleague.adobe.com/en/docs/analytics-platform/using/content-analytics/content-analytics)
- [Content Analytics configuration](https://experienceleague.adobe.com/en/docs/analytics-platform/using/content-analytics/config/configuration)

### Dashboards & scorecards

- [Create a mobile scorecard](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Configure and curate scorecards](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics dashboards -- executive guide](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Summary number visualization](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)

### AEP foundations

- [Datasets overview](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/overview)
- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Audience Portal overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-portal)

### AJO reporting integration

- [AJO + CJA integration guide](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Campaign email report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/campaign-global-report-cja-email)
- [Journey email report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/journey-global-report-cja-email)

### Tutorials & guides

- [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
