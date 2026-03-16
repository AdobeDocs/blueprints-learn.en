---
title: B2B Analytics
description: Learn how to include B2B account-level information in cross-channel customer journey analysis.
solution: Customer Journey Analytics, Real-Time Customer Data Platform
exl-id: 9d576e5c-cbd2-4c60-a6b0-88f8b8b963b4
---
# B2B analytics

This guide provides a comprehensive implementation reference for B2B account-level analytics using [!DNL Customer Journey Analytics] ([!DNL CJA]) B2B Edition and [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B Edition. It is designed for solution architects, marketing technologists, and implementation engineers who need to incorporate B2B account-level information into cross-channel customer journey analysis.

It covers all viable approaches for account-centric analytics, from flat account structures to complex global account hierarchies, with guidance on when to choose each option. The plan addresses B2B data connections, account data view configuration, workspace analysis, and dashboard publishing.

B2B Analytics extends standard [!DNL CJA] capabilities with account-based connections, B2B-specific containers (Account, Global Account, Opportunity, Buying Group), and account-level reporting. This capability enables organizations to analyze marketing and sales engagement at the account level, track opportunity progression, measure buying group completeness, and attribute revenue to marketing touchpoints across extended B2B sales cycles.

## Use case overview

B2B organizations face a fundamental analytics challenge: their customers are not individual people but accounts composed of multiple stakeholders, buying groups, and opportunities. Standard person-based analytics cannot answer questions like "Which accounts are most engaged?", "How complete are our buying groups?", or "Which marketing touchpoints drive opportunity progression?"

B2B Analytics addresses this by leveraging [!DNL CJA] B2B Edition to create account-centric analytical views that combine person-level behavioral data with account, opportunity, and buying group dimensions. [!DNL RT-CDP] B2B Edition provides the underlying account profile unification and B2B identity resolution that feeds the analytics layer. Together, these solutions enable organizations to build cross-channel journey analysis at the account level, correlate marketing engagement with pipeline progression, and deliver actionable insights to both marketing and sales teams.

The target audience includes B2B marketing operations teams, demand generation leaders, revenue operations analysts, and sales leadership who need visibility into account-level engagement and pipeline health.

## Key business objectives

The following business objectives are supported by this use case pattern.

### Improve analytics & reporting

Enhance reporting capabilities for faster, more actionable marketing insights through unified dashboards and self-service tools. B2B Analytics enables organizations to consolidate account-level engagement data from multiple sources into a single analytical environment, providing cross-channel visibility into how marketing programs influence pipeline and revenue.

**KPIs:** Efficiency, Productivity

[Learn more about improving analytics & reporting](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)

### Enable data-driven decision making

Empower teams with self-service analytics, real-time customer insights, and AI-powered predictions to guide strategy. Account-level analytics equip marketing and sales teams with the data needed to prioritize accounts, optimize engagement strategies, and align on pipeline opportunities.

**KPIs:** Efficiency, Productivity

[Learn more about enabling data-driven decision making](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)

### Improve lead qualification & conversion

Increase lead quality and accelerate pipeline progression through scoring, nurturing, and personalized follow-up. CJA B2B Edition provides extended 13-month account lookback windows specifically designed for B2B sales cycles, enabling accurate multi-touch attribution across the full account journey.

**KPIs:** Efficiency, Incremental Revenue

[Learn more about improving lead qualification & conversion](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

## Example tactical use cases

The following scenarios illustrate how this pattern can be applied in practice.

- **Account engagement scoring analysis** -- Measure and rank accounts by their aggregate engagement across web, email, events, and content interactions to identify high-intent accounts for sales follow-up
- **Buying group completeness tracking** -- Analyze buying group composition across accounts to identify gaps in role coverage and prioritize lead acquisition for incomplete buying groups
- **Opportunity pipeline correlation** -- Correlate marketing engagement data with opportunity stage progression to understand which campaigns and touchpoints drive pipeline advancement
- **Multi-touch B2B attribution** -- Apply attribution models with 13-month lookback windows to credit marketing touchpoints across the full B2B buying journey from first touch to closed-won
- **Account journey mapping** -- Visualize the cross-channel account journey from initial awareness through opportunity creation and close, identifying common paths and friction points
- **Campaign influence on pipeline** -- Measure how specific campaigns influence account pipeline creation, opportunity advancement, and revenue generation
- **Buying group engagement progression** -- Track how buying group engagement scores evolve over time and correlate engagement thresholds with opportunity outcomes
- **Account-based content performance** -- Analyze which content assets and topics resonate with specific account segments, industries, or buying group roles
- **Sales and marketing alignment dashboards** -- Build shared dashboards that provide both marketing and sales teams with a unified view of account engagement, pipeline health, and revenue attribution
- **Account segmentation for activation** -- Create B2B segments based on account-level analytics (for example, "highly engaged accounts without open opportunities") and publish them for downstream activation

## Key performance indicators

The following KPIs help measure the success of this use case pattern.

| KPI | Description | Measurement approach |
| --- | --- | --- |
| Account Engagement Score | Aggregate engagement metric across all contacts within an account | Computed metric combining web visits, email interactions, event attendance, and content downloads at the account level |
| Buying Group Completeness | Percentage of required roles filled within a buying group | Ratio of filled roles to total required roles per buying group, tracked over time |
| Pipeline Influenced by Marketing | Revenue in pipeline that has been touched by marketing activities | Opportunity value where associated account contacts have marketing touchpoints within the attribution window |
| Account-to-Opportunity Conversion Rate | Percentage of engaged accounts that generate qualified opportunities | Accounts with opportunities divided by total engaged accounts over a defined period |
| Average Deal Cycle Length | Time from first marketing touch to closed-won | Average duration from first attributed touchpoint to opportunity close date |
| Marketing Attribution Revenue | Revenue attributed to marketing touchpoints | Revenue from closed-won opportunities with marketing touches, distributed by attribution model |
| Account Reach and Penetration | Number of contacts engaged per target account | Unique contacts with marketing interactions per account, compared to total known contacts |
| Content Engagement by Buying Role | Engagement metrics segmented by buying group role | Page views, downloads, and time spent broken down by persona/role within buying groups |

## Use case pattern

**B2B analytics**

Include B2B account-level information in cross-channel customer journey analysis.

**Function chain:** B2B Data Connection > Account Data View Configuration > Workspace Analysis > Dashboard Publishing

## Applications

The following applications are used to implement this use case pattern.

- **[!DNL Customer Journey Analytics] B2B Edition** -- Provides account-based connections, B2B-specific data view containers, account-level workspace analysis, buying group analysis, opportunity analysis, B2B segmentation, and B2B attribution with extended lookback windows
- **[!DNL Real-Time CDP] B2B Edition** -- Provides the B2B data foundation including account profile unification, B2B identity resolution, B2B schema classes (Account, Opportunity, Buying Group), and [!DNL Marketo Engage] integration for ingesting B2B engagement data

## Foundational functions

The following foundational capabilities must be in place for this use case pattern. For each function, the status indicates whether it is typically required, assumed to be pre-configured, or not applicable.

| Foundational function | Status | What must be in place | Experience League reference |
| --- | --- | --- | --- |
| Administration & Governance | Required | Sandbox configured with [!DNL CJA] B2B Edition and [!DNL RT-CDP] B2B Edition entitlements. Roles provisioned for data engineers, analysts, and marketing operations users with access to [!DNL CJA] and the B2B data model. | [Sandboxes overview](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home) |
| Data Modeling & Preparation | Required | B2B XDM schemas configured using B2B classes: XDM Business Account, XDM Business Opportunity, XDM Business Account Person Relation, XDM Business Opportunity Person Relation, and XDM Business Marketing List Members. Field groups for account attributes, opportunity stages, and buying group roles must be defined. Datasets created and enabled for Profile. | [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [B2B edition schemas](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b) |
| Data Sources & Collection | Required | B2B data sources connected, typically via the [!DNL Marketo Engage] source connector or [!DNL Salesforce] CRM source connector. Account records, opportunity records, person-account relationships, and behavioral engagement events must be flowing into AEP datasets. [!DNL Web SDK] or [!DNL Marketo] integration must be capturing behavioral events with account association. | [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home), [Marketo Engage connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| Identity & Profile Configuration | Required | B2B identity resolution configured to resolve person-to-account relationships. Account ID, Person ID ([!DNL Marketo] Lead ID or CRM Contact ID), and cross-device identities (ECID, email) must be linked. Identity graph must support the many-to-many person-to-account mapping inherent in B2B data models. | [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [B2B identity resolution](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b) |
| Audience Definition & Segmentation | Assumed in Place | Account-level audience definitions should be available if B2B segments will be published from [!DNL CJA] back to AEP for activation. For analytics-only use cases, this is not a strict prerequisite but is recommended for segment-based analysis. | [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## Supporting functions

The following capabilities augment this use case pattern but are not required for core execution.

| Supporting function | Status | Why it matters | Experience League reference |
| --- | --- | --- | --- |
| Computed / Derived Attribute Creation | Recommended | Computed attributes on account profiles (for example, total engagement score, days since last activity, opportunity count) enrich the analytical dimensions available in [!DNL CJA] for account-level analysis. | [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Recommended | B2B datasets, particularly behavioral event data from [!DNL Marketo Engage], can grow rapidly. Dataset expiration policies help manage storage and ensure compliance with data retention requirements. | [Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Data Usage Labeling & Enforcement | Recommended | B2B data often contains sensitive business information (contract values, competitive intelligence). Data usage labels and governance policies ensure this data is used appropriately across analytics and activation workflows. | [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Monitoring & Observability | Recommended | B2B source connectors ([!DNL Marketo], [!DNL Salesforce]) require monitoring for ingestion health. Connection health monitoring in [!DNL CJA] ensures data freshness for analytics. Alert rules for ingestion failures prevent stale dashboards. | [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting & Analysis | Included | This pattern is itself an analytics pattern. This function is inherently included as the core function chain delivers reporting and analysis capabilities. | [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Application functions

This plan exercises the following functions from the Application Function Catalog. Functions are mapped to implementation phases rather than numbered steps.

### [!DNL Customer Journey Analytics] B2B Edition

| Function | Implementation phase | Description |
| --- | --- | --- |
| Account-Based Connection | Phase 1: B2B Data Connection | Configure connections using Account or Global Account as the primary identifier for organization-level analysis |
| B2B Data View Configuration | Phase 2: Account Data View Configuration | Define data views with B2B-specific containers (Account, Global Account, Opportunity, Buying Group) alongside standard Person, Session, and Event containers |
| Account-Level Workspace Analysis | Phase 3: Workspace Analysis | Build freeform analysis using account-level dimensions, metrics, and B2B containers for organization-level journey insights |
| Buying Group Analysis | Phase 3: Workspace Analysis | Analyze buying group composition, engagement, and progression through the purchase decision process |
| Opportunity Analysis | Phase 3: Workspace Analysis | Track opportunity progression through sales funnel stages and correlate with marketing engagement data |
| B2B Segmentation | Phase 3: Workspace Analysis | Create segments using B2B containers for filtered account-level analysis |
| B2B Attribution | Phase 3: Workspace Analysis | Apply attribution models with extended 13-month account lookback windows for B2B sales cycle analysis |
| Computed Metric Creation | Phase 3: Workspace Analysis | Define calculated metrics for B2B KPIs such as account engagement rate, buying group completeness, and pipeline influence |
| Dashboard & Scorecard Publishing | Phase 4: Dashboard Publishing | Create and share dashboards and mobile scorecards for marketing and sales leadership |
| Audience Publishing | Phase 4: Dashboard Publishing | Publish [!DNL CJA]-defined account-based audiences back to AEP for downstream activation |

### [!DNL Customer Journey Analytics] -- standard functions

| Function | Implementation phase | Description |
| --- | --- | --- |
| Data Connection | Phase 1: B2B Data Connection | Bind AEP B2B datasets to [!DNL CJA] connections for cross-channel analysis |
| Data View Configuration | Phase 2: Account Data View Configuration | Configure standard dimensions, metrics, attribution, and persistence settings within the B2B data view |
| Workspace Analysis | Phase 3: Workspace Analysis | Build freeform analysis with tables, fallout, flow, cohort, and attribution visualizations |
| Guided Analysis | Phase 3: Workspace Analysis | Use guided workflows for funnel, trend, and retention analysis at the account level |

### [!DNL Real-Time CDP] B2B Edition

| Function | Implementation phase | Description |
| --- | --- | --- |
| Account Profile Unification | Prerequisite (F2/F4) | Consolidate cross-source B2B data into unified account profiles using specialized XDM B2B schema classes |
| B2B Identity Resolution | Prerequisite (F4) | Resolve person-to-account relationships supporting multi-level account hierarchies and many-to-many mappings |
| [!DNL Marketo Engage] Integration | Prerequisite (F3) | Ingest behavioral engagement data and account/lead records from [!DNL Marketo Engage] via native B2B source connectors |

## Prerequisites

The following items must be in place before implementation begins.

- [!DNL CJA] B2B Edition license is active and provisioned for the organization
- [!DNL RT-CDP] B2B Edition license is active with B2B schemas and account profiles configured
- B2B XDM schemas are defined (Account, Opportunity, Account Person Relation, Opportunity Person Relation, Marketing List Members)
- [!DNL Marketo Engage] and/or CRM source connectors are configured and actively ingesting data
- Account-level behavioral event data (web visits, email interactions, form submissions) is flowing into AEP with account association
- Person-to-account relationships are established in the identity graph
- At least 30 days of historical B2B engagement data is available for meaningful analysis
- Stakeholders have agreed on buying group role definitions and solution interest mappings
- [!DNL CJA] user accounts are provisioned with appropriate product profiles for B2B Edition features
- Target KPIs and reporting requirements have been defined by marketing and sales leadership

## Implementation options

The following sections describe different approaches for implementing this use case pattern.

### Option A: Account-centric analytics

**Best for:** Organizations that want to analyze all engagement and pipeline data through the lens of the account. This approach uses the Account container as the primary analytical unit, providing a top-down view of how accounts progress through the buying journey.

**How it works:**

Configure a [!DNL CJA] B2B connection with Account as the primary identifier. All behavioral events, opportunities, and buying group data roll up to the account level. The data view uses Account as the highest-level container, with Person, Session, and Event nested within it. This enables analysis like "How many accounts visited the pricing page and then created an opportunity within 30 days?"

Account-centric analytics provides the most natural view for B2B organizations where the account is the unit of purchase. Dimensions like industry, company size, account tier, and account owner can be used to break down engagement patterns and pipeline metrics. Attribution is applied at the account level with 13-month lookback windows that accommodate long B2B sales cycles.

**Key considerations:**

- Requires clean account-to-person mapping in the identity graph
- All person-level events must be attributable to an account
- Anonymous web traffic that cannot be associated with an account will not appear in account-level analysis

**Advantages:**

- Provides a true account-level view of the entire buying journey
- Enables account-based attribution that matches how B2B revenue is generated
- Supports buying group and opportunity analysis as nested containers within the account
- Aligns analytics with account-based marketing (ABM) strategy

**Limitations:**

- Requires robust person-to-account identity resolution
- Anonymous or unmatched engagement data is excluded from analysis
- More complex to configure than person-centric analytics

**Experience League:**

- [CJA B2B Edition overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [B2B edition schemas](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)

### Option B: Global account-centric analytics

**Best for:** Enterprise organizations with complex account hierarchies where a parent company has multiple subsidiary accounts. This approach uses Global Account as the primary identifier, rolling up all subsidiary account activity to the parent organization level.

**How it works:**

Configure the [!DNL CJA] B2B connection with Global Account as the primary identifier instead of Account. This aggregates engagement data from all subsidiary accounts under their parent organization. For example, if "Acme Corp" has regional subsidiaries "Acme EMEA" and "Acme APAC," a Global Account connection consolidates all engagement from all three entities into a single analytical view.

The data view includes Global Account as the top-level container, with Account, Person, Session, and Event as nested containers. This enables analysis at both the global and subsidiary account levels within the same workspace project. Attribution lookback windows apply at the global account level, capturing all touchpoints across the entire corporate hierarchy.

**Key considerations:**

- Requires account hierarchy data with parent-child relationships defined in the B2B data model
- Global Account ID must be populated and accurate across all account records
- Subsidiary accounts must be correctly mapped to their parent

**Advantages:**

- Provides consolidated visibility across complex enterprise account structures
- Prevents fragmented analysis when a single enterprise customer has multiple account records
- Enables comparison between regional subsidiaries within a single global account
- Supports enterprise-level pipeline and revenue reporting

**Limitations:**

- Requires accurate account hierarchy data, which many organizations struggle to maintain
- May obscure subsidiary-level patterns when viewed only at the global level
- Additional data modeling effort to establish and maintain hierarchy relationships

**Experience League:**

- [CJA B2B Edition overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### Option C: Hybrid person + account analytics

**Best for:** Organizations transitioning from person-based analytics to account-based analytics, or those that need both person-level and account-level views. This approach creates two data views from the same connection -- one person-centric and one account-centric.

**How it works:**

Configure a single [!DNL CJA] B2B connection that includes all B2B datasets (event, account, opportunity, buying group, person-account relations). Then create two data views: one using Person as the primary container (similar to standard [!DNL CJA]) and one using Account as the primary container. Analysts can switch between data views depending on the question being asked.

The person-centric data view provides traditional individual-level journey analysis (for example, "What is the conversion path for leads who become opportunities?"), while the account-centric data view provides organization-level analysis (for example, "Which accounts have the highest engagement-to-pipeline conversion rate?"). Both views use the same underlying data, ensuring consistency.

**Key considerations:**

- Requires two data views with potentially different dimension and metric configurations
- Analysts need training on when to use each view
- Computed metrics may need to be created separately for each data view

**Advantages:**

- Provides flexibility to analyze data at both the person and account level
- Easier adoption path for teams accustomed to person-level analytics
- Enables comparison between person-level and account-level metrics
- Supports both lead-based and account-based marketing strategies

**Limitations:**

- Two data views to maintain and keep in sync
- Potential confusion for analysts about which view to use
- Computed metrics and filters may need duplication across views

**Experience League:**

- [Create or edit a data view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Data views overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)

### Option comparison

| Criteria | Option A: Account-centric | Option B: Global account-centric | Option C: Hybrid person + account |
| --- | --- | --- | --- |
| Best for | Standard B2B with flat account structure | Enterprise with parent-child hierarchies | Transitioning organizations or dual needs |
| Complexity | Medium | High | Medium-High |
| Data requirements | Account-person mapping | Account hierarchy + mapping | Account-person mapping |
| Attribution scope | Account level (13-month lookback) | Global account level (13-month lookback) | Both person and account level |
| Anonymous data | Excluded from account view | Excluded from global view | Included in person view, excluded from account view |
| Requires | [!DNL RT-CDP] B2B Edition, [!DNL CJA] B2B Edition | [!DNL RT-CDP] B2B Edition, [!DNL CJA] B2B Edition, hierarchy data | [!DNL RT-CDP] B2B Edition, [!DNL CJA] B2B Edition |
| Maintenance effort | Single data view | Single data view | Two data views |

### Choose the right option

- **Choose Option A** if your organization has a flat account structure (no parent-child hierarchies), your ABM strategy operates at the individual account level, and you want the simplest path to account-level analytics.
- **Choose Option B** if your target accounts are large enterprises with subsidiary accounts across regions or divisions, and you need consolidated reporting at the corporate parent level. This option requires high-quality account hierarchy data.
- **Choose Option C** if your organization is transitioning from lead-based to account-based marketing, your analysts need both person-level funnel analysis and account-level engagement analysis, or you have a mix of B2B and B2C business lines.

## Implementation phases

The following phases outline the recommended implementation sequence.

### Phase 1: B2B data connection

**Application function:** [!DNL CJA] B2B: Account-Based Connection, [!DNL CJA]: Data Connection

Configure the [!DNL CJA] connection that binds your AEP B2B datasets to [!DNL CJA] for analysis. This connection defines which datasets flow into [!DNL CJA], the primary identifier type (Account or Global Account), and how historical and streaming data are ingested. The connection is the foundation of all subsequent analysis.

#### Decision: Primary identifier type

Determine whether the connection should use Account ID or Global Account ID as the primary identifier.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Account ID | Flat account structure, no parent-child hierarchies | Simpler setup; each account analyzed independently. Most common choice for SMB-focused B2B. |
| Global Account ID | Enterprise accounts with subsidiary hierarchies | Requires hierarchy data; aggregates all subsidiaries under parent. Best for enterprise ABM programs. |

#### Decision: Dataset selection and type designation

Determine which B2B datasets should be included and how each should be typed.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Event datasets (behavioral) | Always include | Web interactions, email events, form submissions, content downloads. Must have timestamp field. These are the engagement signals. |
| Account record datasets (profile) | Always include | Account attributes like industry, size, tier, owner. Provides the dimensional context for account analysis. |
| Opportunity datasets (lookup/profile) | Include for pipeline analysis | Opportunity stage, value, close date. Required for pipeline and revenue attribution analysis. |
| Buying group datasets (lookup/profile) | Include for buying group analysis | Buying group roles, engagement scores, completeness. Required for buying group composition analysis. |
| Person-account relation datasets (lookup) | Always include | Maps people to accounts. Critical for associating person-level events with account-level analysis. |
| Campaign/program datasets (lookup) | Include for attribution | Campaign metadata, program types, channels. Enables campaign influence analysis. |

#### Decision: Backfill range

Determine how much historical data should be imported into the connection.

| Option | When to choose | Considerations |
| --- | --- | --- |
| All existing data | B2B sales cycles are long (6-18 months) and you need full history | Recommended for B2B. Backfill may take days for large datasets but provides complete attribution data. |
| Custom date range (last 2-3 years) | Data quality degrades beyond a certain point | Balances completeness with data quality. Common when CRM data has historical inconsistencies. |
| No backfill | Testing or development only | Only new data flows in. Not suitable for production B2B analytics. |

#### Configure the B2B data connection

**UI navigation:** [!DNL Customer Journey Analytics] > Connections > Create new connection

Key configuration details:

- Select the AEP sandbox containing B2B datasets
- Set the average number of daily events for capacity planning
- Add each dataset and designate its type (event, lookup, or profile)
- Configure the person ID field to use Account ID or Global Account ID for B2B connections
- Enable streaming for datasets that require near-real-time updates
- Enable "Import all existing data" for historical backfill

**Where options diverge:**

**For Option A (Account-Centric):**
Set the primary identifier to Account ID. Add account record, opportunity, buying group, and person-account relation datasets. Configure person-level event datasets with the Account ID field for cross-dataset joining.

**For Option B (Global Account-Centric):**
Set the primary identifier to Global Account ID. Ensure account hierarchy data includes the Global Account ID field. All datasets must include or be joinable to the Global Account ID for proper roll-up.

**For Option C (Hybrid):**
Create a single connection with all B2B datasets. Use Account ID as the primary identifier. The person-centric view will be created in Phase 2 by using a different data view configuration on the same connection.

**Experience League documentation:**

- [Connections overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Create or edit a connection](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Manage connections](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)
- [CJA B2B Edition overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### Phase 2: Account data view configuration

**Application function:** [!DNL CJA] B2B: B2B Data View Configuration, [!DNL CJA]: Data View Configuration

Configure the data view that defines how connection data appears in analysis. For B2B analytics, this includes configuring B2B-specific containers (Account, Opportunity, Buying Group), mapping B2B schema fields to dimensions and metrics, setting attribution models with B2B-appropriate lookback windows, and creating derived fields for B2B business logic.

#### Decision: Container configuration

Determine which B2B containers should be enabled and how they should be named.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Account + Person + Session + Event | Standard B2B without buying group or opportunity analysis | Simplest B2B container hierarchy. Account is the top-level container. |
| Account + Opportunity + Person + Session + Event | Pipeline and revenue analysis required | Adds opportunity as a container level, enabling opportunity-scoped analysis. |
| Account + Buying Group + Opportunity + Person + Session + Event | Full B2B analysis including buying group composition | Most comprehensive. Enables analysis at every level of the B2B data model. |
| Global Account + Account + Person + Session + Event | Global account hierarchy analysis | Adds Global Account as the highest-level container above Account. |

#### Decision: Attribution model for B2B metrics

Determine which attribution model should be the default for conversion metrics.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Linear attribution (13-month lookback) | Equal credit to all touchpoints in the B2B journey | Best for understanding the full mix of marketing activities. Recommended starting point for B2B. |
| U-shaped attribution (13-month lookback) | Emphasis on first and last touch with credit to middle touches | Highlights lead creation and opportunity conversion moments. Common in demand generation analysis. |
| Time decay (13-month lookback) | More recent touchpoints should receive more credit | Best when recency of engagement is an important signal for sales readiness. |
| Last touch | Simple reporting of the final touchpoint before conversion | Easy to understand but undervalues early-stage marketing. Use for quick operational reporting only. |

#### Decision: Session definition for B2B

Determine how sessions should be defined for B2B engagement.

| Option | When to choose | Considerations |
| --- | --- | --- |
| 30-minute timeout (default) | Standard web analytics session behavior | Standard for web engagement analysis. May fragment long content consumption sessions. |
| Extended timeout (60-120 minutes) | B2B users engage in longer research sessions | B2B buyers often spend extended time reviewing technical content, pricing, and documentation. |
| Event-based new session | Specific events should always start a new session | Use when campaign click-throughs or demo requests should always begin a new analytical session. |

#### Configure the account data view

**UI navigation:** [!DNL Customer Journey Analytics] > Data views > Create new data view

Key configuration details:

- Select the connection created in Phase 1
- Configure time zone and calendar type appropriate for the organization
- Rename containers to B2B-relevant terminology (for example, Account/Engagement/Touchpoint)
- Map B2B schema fields to dimensions: account name, account ID, industry, company size, account tier, account owner, opportunity stage, opportunity value, buying group role, solution interest
- Map engagement metrics: events (occurrences), people, sessions, page views, form submissions, email opens, email clicks
- Configure persistence for key dimensions (for example, account industry persists at the account level)
- Set attribution to linear with 13-month lookback as the default for conversion metrics
- Create derived fields for marketing channel classification, engagement scoring tiers, and opportunity stage grouping

**Where options diverge:**

**For Option A (Account-Centric):**
Configure a single data view with Account as the top-level container. Include Opportunity and Buying Group containers if pipeline and buying group analysis is needed.

**For Option B (Global Account-Centric):**
Configure Global Account as the top-level container. Include Account as a sub-container to enable both global and subsidiary analysis.

**For Option C (Hybrid):**
Create two data views from the same connection. Data View 1 uses Person as the primary container (standard [!DNL CJA] behavior). Data View 2 uses Account as the primary container with B2B containers. Map identical metrics to both views where applicable.

**Experience League documentation:**

- [Data views overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Create or edit a data view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Component settings overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Persistence settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Attribution settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Derived fields](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [Session settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)

### Phase 3: Workspace analysis

**Application function:** [!DNL CJA] B2B: Account-Level Workspace Analysis, Buying Group Analysis, Opportunity Analysis, B2B Segmentation, B2B Attribution, [!DNL CJA]: Workspace Analysis, Computed Metric Creation, Guided Analysis

Build workspace projects that deliver the analytical insights defined in the KPIs. This phase includes building freeform tables with B2B dimensions and metrics, creating computed metrics for B2B KPIs, configuring B2B-specific visualizations (account-level flow, opportunity funnel, buying group engagement), creating filters/segments using B2B containers, and applying B2B attribution models.

#### Decision: Analysis workspace structure

Determine how the workspace project should be organized.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Single comprehensive project with multiple panels | Small team, all stakeholders view the same reports | Easier to maintain. Use panels to separate topics (engagement, pipeline, attribution). Up to 40 panels per project. |
| Multiple focused projects by audience | Different stakeholders need different views | Marketing gets engagement/attribution. Sales gets pipeline/account health. Operations gets data quality. More maintenance but better targeted. |
| Template-based projects with guided analysis | Self-service analytics for non-expert users | Use guided analysis for funnel and trend views. Save as templates for repeatable analysis. Best for broad adoption. |

#### Decision: B2B computed metrics

Determine which calculated metrics are needed for B2B KPIs.

| Metric | Formula | When to create |
| --- | --- | --- |
| Account Engagement Rate | (Total Account Events / Total Accounts) | Always -- core B2B metric |
| Buying Group Completeness % | (Filled Roles / Required Roles) * 100 | When buying group analysis is in scope |
| Account-to-Opportunity Conversion | Accounts with Opportunities / Engaged Accounts | When pipeline analysis is needed |
| Pipeline Influence % | Influenced Pipeline Value / Total Pipeline Value | When marketing attribution is required |
| Average Engagement per Contact | Events / Unique People per Account | When account penetration analysis is needed |
| Content Engagement by Role | Events filtered by Buying Group Role | When content optimization for B2B is needed |

#### Decision: B2B filter/segment scope

Determine at which container level filters should be created.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Account-level filters | Analysis scoped to accounts matching criteria (for example, enterprise accounts, specific industries) | Includes all events from qualifying accounts. Most common for B2B. |
| Opportunity-level filters | Analysis scoped to specific opportunity types or stages | Includes all events associated with qualifying opportunities. |
| Buying group-level filters | Analysis scoped to specific buying group states | Includes events from people in qualifying buying groups. |
| Person-level filters | Analysis scoped to individuals matching criteria (for example, specific roles, titles) | Standard filter behavior. Use when analyzing individual engagement within the B2B context. |

#### Build the workspace analysis

**UI navigation:** [!DNL Customer Journey Analytics] > Workspace > Projects > Create project

Key configuration details:

- Select the B2B data view created in Phase 2
- Build freeform tables with account-level dimensions (account name, industry, tier) broken down by engagement metrics
- Create opportunity funnel visualizations showing opportunity progression through stages
- Build buying group composition tables showing role fill rates and engagement per role
- Configure B2B attribution panels comparing attribution models (linear, U-shaped, time decay) with 13-month lookback
- Create account flow visualizations showing common paths through the buying journey
- Build cohort tables analyzing account retention and re-engagement over time
- Apply B2B filters to segment analysis by account tier, industry, or engagement level
- Create annotations for significant events (campaign launches, product releases, pricing changes)

**Experience League documentation:**

- [Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Create a project](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Freeform table](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Attribution panel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Flow visualization](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Fallout visualization](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Cohort table](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Filters overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Calculated metrics overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Create calculated metrics](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Annotations overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Guided analysis overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Breakdown dimensions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

### Phase 4: Dashboard publishing

**Application function:** [!DNL CJA]: Dashboard & Scorecard Publishing, [!DNL CJA]: Audience Publishing

Create shareable dashboards and mobile scorecards that deliver B2B analytics insights to stakeholders. This phase also covers publishing [!DNL CJA]-defined B2B audiences back to AEP for activation in downstream use cases such as B2B audience activation.

#### Decision: Dashboard delivery method

Determine how B2B analytics insights should be delivered to stakeholders.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Workspace project (desktop) | Analysts and marketing operations who need interactive exploration | Full interactivity, drill-down, filter toggling. Requires [!DNL CJA] access. |
| Mobile scorecard | Executives and sales leaders who need at-a-glance KPIs | Summary numbers with trend lines. Accessible via [!DNL Adobe Analytics] dashboards app. Limited interactivity. |
| Scheduled PDF/CSV export | Stakeholders without [!DNL CJA] access who need regular updates | Automated delivery on a schedule. No interactivity. Best for weekly/monthly executive summaries. |
| All of the above | Large organizations with diverse stakeholder needs | Maximum reach. Higher maintenance effort. Recommended for mature B2B analytics programs. |

#### Decision: Audience publishing from [!DNL CJA]

Determine whether B2B segments should be published back to AEP for activation.

| Option | When to choose | Considerations |
| --- | --- | --- |
| Publish account-based audiences | Analytics insights should inform targeting and suppression | Enables activation of [!DNL CJA]-defined segments (for example, "highly engaged accounts without open opportunities") via [!DNL RT-CDP]. Refresh cadence: 4 hours to weekly. |
| Do not publish | Analytics is for reporting only, not activation | Simpler configuration. Activation handled separately in [!DNL RT-CDP]. |

#### Publish dashboards and audiences

**UI navigation:** [!DNL Customer Journey Analytics] > Projects > Share (for Workspace), Projects > Create > Mobile scorecard (for scorecards), Components > Audiences > Publish (for audience publishing)

Key configuration details:

- Build executive dashboards with summary numbers for key B2B KPIs (total engaged accounts, pipeline value, buying group completeness)
- Configure comparison periods (month-over-month, quarter-over-quarter) for trend indicators
- Create mobile scorecards with tiles for account engagement, pipeline health, and attribution metrics
- Add filters for executives to toggle views by region, industry, or account tier
- Configure scheduled project delivery for weekly executive reports
- For audience publishing: select the B2B filter, configure the identity namespace (Account ID), and set the refresh cadence

**Experience League documentation:**

- [Create a mobile scorecard](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Share projects](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Schedule projects](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Configure and curate scorecards](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics dashboards -- executive guide](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Audiences overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Create and publish audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)

## Implementation considerations

The following sections cover guardrails, common pitfalls, best practices, and trade-off decisions to keep in mind during implementation.

### Guardrails and limits

- [!DNL CJA] connections can include datasets from only one AEP sandbox -- [CJA guardrails](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)
- Maximum of 5,000 dimensions and 5,000 metrics per data view
- Maximum of 100 derived fields per data view
- B2B attribution supports lookback windows up to 13 months for account-level analysis
- Maximum of 75 published audiences per [!DNL CJA] customer across all sandboxes
- Audience publishing minimum refresh cadence is every 4 hours
- Streaming latency from AEP to [!DNL CJA] is typically under 90 minutes
- Freeform tables support up to 10 dimension breakdowns deep
- Mobile scorecards support up to 16 tiles per scorecard
- Workspace projects support up to 40 panels per project
- Backfill for large B2B datasets (billions of records) may take days to complete

### Common pitfalls

- **Incomplete person-to-account mapping:** If person-level events cannot be associated with an account, they will not appear in account-level analysis. Ensure all event datasets include a field that can be joined to the Account ID, either directly or through a person-account relation lookup dataset. Audit the percentage of events with missing account association before building analysis.
- **Incorrect dataset type designation:** B2B lookup datasets (opportunity, buying group, person-account relations) must be correctly designated as lookup or profile type in the [!DNL CJA] connection. Mistyping a lookup dataset as an event dataset will produce incorrect results because [!DNL CJA] will attempt to treat each record as a timestamped event.
- **Attribution window too short for B2B:** Using default 30-day attribution windows will miss early-stage touchpoints in B2B journeys that typically span 6-18 months. Always configure 13-month lookback windows for B2B attribution metrics.
- **Mixing account-level and person-level metrics incorrectly:** Counting "people" in an account-level analysis can be misleading. Ensure computed metrics are defined at the appropriate container level. An "account engagement rate" should use account-level events divided by accounts, not by people.
- **Stale buying group data:** Buying group composition and role assignments change over time. If buying group datasets are not refreshed regularly, completeness metrics will be inaccurate. Ensure the source system ([!DNL Marketo Engage] or [!DNL AJO] B2B Edition) is actively syncing buying group data.
- **Overloading a single workspace project:** B2B analytics spans engagement, pipeline, attribution, and buying groups. Attempting to put everything in one project leads to slow loading and confusing navigation. Use multiple focused projects or clearly labeled panels.

### Best practices

- Start with Option A (Account-Centric) even if you plan to use Option B (Global Account) later. Account-centric analytics is simpler and validates your data model before adding hierarchy complexity.
- Create a dedicated "B2B Data Quality" workspace project that tracks the percentage of events with account association, the number of orphaned accounts, and buying group completeness metrics. Run this weekly to catch data issues early.
- Use derived fields to create engagement scoring tiers (High/Medium/Low) based on account-level event counts. This simplifies analysis and makes dashboards more actionable for non-technical stakeholders.
- When configuring B2B attribution, start with linear attribution as a baseline, then compare against U-shaped and time-decay models. The differences between models often reveal whether your marketing mix is weighted toward awareness or conversion activities.
- Publish a "B2B Executive Summary" mobile scorecard with no more than 8 tiles covering the KPIs that matter most to leadership. Keep it focused -- executive scorecards should answer "How are we doing?" not "Why?"
- Annotate key events (product launches, major campaign launches, pricing changes, sales process changes) to provide context for data trends. B2B data often shows spikes and dips that are unexplainable without event context.
- When publishing B2B audiences from [!DNL CJA], use daily refresh for standard activation segments and 4-hour refresh only for time-sensitive segments. Frequent refreshes consume processing resources.

### Trade-off decisions

>[!NOTE]
>The following trade-off decisions should be evaluated based on your organization's specific requirements and constraints.

**Data completeness vs. analytical accuracy**

Including all person-level events in account analysis (even those with weak account association) improves data completeness but may reduce analytical accuracy if the account mapping is unreliable.

- **Including all events favors:** Comprehensive engagement measurement, higher account engagement scores, broader visibility
- **Excluding unmatched events favors:** Accurate account-level metrics, trustworthy attribution, reliable pipeline correlation
- **Recommendation:** Exclude unmatched events from account-level analysis but include them in a separate person-level data view (Option C) to understand the full picture. Prioritize improving account association data quality as a parallel workstream.

**B2B attribution lookback window length**

Longer lookback windows (13 months) capture more touchpoints but may include marketing activities that are no longer relevant to the current buying decision.

- **Longer lookback (13 months) favors:** Capturing the full B2B journey, crediting awareness-stage activities, accommodating long sales cycles
- **Shorter lookback (6 months) favors:** Focusing on recent engagement, reducing noise from old touchpoints, better reflection of current buying intent
- **Recommendation:** Use 13-month lookback for enterprise accounts with long sales cycles (12+ months). Use 6-month lookback for mid-market accounts with shorter cycles. Create separate computed metrics for each window to compare.

**Single comprehensive data view vs. multiple focused data views**

One data view with all B2B containers and dimensions is simpler to maintain but may overwhelm analysts with complexity. Multiple focused data views (engagement, pipeline, attribution) are easier to use but harder to maintain.

- **Single view favors:** Consistency, easier maintenance, cross-domain analysis within a single project
- **Multiple views favors:** Simplicity for analysts, faster loading times, tailored component lists per use case
- **Recommendation:** Start with a single comprehensive data view. If analysts report difficulty finding the right dimensions and metrics, create curated component groups within the same view before splitting into multiple views. Use workspace templates to guide analysts to the right components.

## Related documentation

The following resources provide additional information for implementing this use case pattern.

**[!DNL CJA] B2B Edition**

- [CJA B2B Edition overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [CJA guardrails](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

**Connections**

- [Connections overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Create or edit a connection](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Manage connections](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)

**Data views**

- [Data views overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Create or edit a data view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Component settings overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Persistence settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Attribution settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Format settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Derived fields](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [Session settings](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)

**Workspace and analysis**

- [Workspace overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Create a project](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Freeform table](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Flow visualization](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Fallout visualization](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Cohort table](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Attribution panel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Share projects](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Schedule projects](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Breakdown dimensions](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

**Components**

- [Filters overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Create filters](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Calculated metrics overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Create calculated metrics](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Annotations overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Date ranges](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

**Audiences**

- [Audiences overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Create and publish audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [Manage audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)

**Dashboards and scorecards**

- [Create a mobile scorecard](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Configure and curate scorecards](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics dashboards -- executive guide](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)

**Guided analysis**

- [Guided analysis overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Funnel view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Trends view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Retention view](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

**[!DNL RT-CDP] B2B Edition**

- [RT-CDP B2B Edition overview](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#702702)
- [B2B edition schemas](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [B2B sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/sources/b2b)

**AEP data foundation**

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Marketo Engage connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Sandboxes overview](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home)

**Data governance and lifecycle**

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

**Tutorials and guides**

- [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
