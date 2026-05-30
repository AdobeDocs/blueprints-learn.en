---
title: B2B Analytics
description: Learn how to include B2B account-level information in cross-channel customer journey analysis.
solution: Customer Journey Analytics, Real-Time Customer Data Platform
exl-id: 9d576e5c-cbd2-4c60-a6b0-88f8b8b963b4
---
# B2B analytics

This guide describes the B2B analytics use case pattern, which uses [!DNL Customer Journey Analytics] ([!DNL CJA]) B2B Edition and [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B Edition to incorporate B2B account-level information into cross-channel customer journey analysis. It is designed for solution architects, marketing technologists, and implementation engineers who need to understand what this pattern does, the business objectives it supports, the tactical use cases it enables, and the Adobe applications involved.

B2B Analytics extends standard [!DNL CJA] capabilities with account-based connections, B2B-specific containers (Account, Global Account, Opportunity, Buying Group), and account-level reporting. This capability enables organizations to analyze marketing and sales engagement at the account level, track opportunity progression, measure buying group completeness, and attribute revenue to marketing touchpoints across extended B2B sales cycles.

## Use case pattern

**B2B analytics**

Include B2B account-level information in cross-channel customer journey analysis.

**Execution plan:** B2B Data Connection > Account Data View Configuration > Workspace Analysis > Dashboard Publishing

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

## Applications

The following applications are used to implement this use case pattern.

- **[!DNL Customer Journey Analytics] B2B Edition** -- Provides account-based connections, B2B-specific data view containers, account-level workspace analysis, buying group analysis, opportunity analysis, B2B segmentation, and B2B attribution with extended lookback windows
- **[!DNL Real-Time CDP] B2B Edition** -- Provides the B2B data foundation including account profile unification, B2B identity resolution, B2B schema classes (Account, Opportunity, Buying Group), and [!DNL Marketo Engage] integration for ingesting B2B engagement data

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
