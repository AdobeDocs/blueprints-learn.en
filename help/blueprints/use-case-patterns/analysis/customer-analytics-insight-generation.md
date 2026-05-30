---
title: Customer Analytics & Insight Generation
description: Learn how to build cross-channel analysis workspaces, computed metrics, and dashboards for behavior and performance analysis.
solution: Customer Journey Analytics, Experience Platform
exl-id: 235a4eb0-91ae-4030-b90e-7eda08c67ae1
---
# Customer analytics & insight generation

This guide describes the customer analytics and insight generation use case pattern, which connects [!DNL Adobe Experience Platform] datasets to [!DNL Customer Journey Analytics] to build data views, freeform analysis workspaces, computed metrics, dashboards, and mobile scorecards, and to optionally publish CJA-defined audiences back to [!DNL Adobe Experience Platform] for activation.

It is designed for solution architects, marketing technologists, and implementation engineers who need to understand what this pattern does, the business objectives it supports, the tactical use cases it enables, and the Adobe applications involved.

Unlike the other patterns in the taxonomy which focus on activation and engagement (sending messages, personalizing content, activating audiences), this pattern focuses on understanding -- analyzing customer behavior, measuring campaign performance, identifying trends, and generating insights that inform strategy and optimization decisions.

## Use case pattern

**Customer analytics & insight generation**

Build cross-channel analysis workspaces, computed metrics, and dashboards to understand customer behavior and campaign performance.

**Execution plan:** Data Connection > Data View Configuration > Workspace Analysis > Dashboard Publishing

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

## Applications

The following applications are used in this use case pattern.

- **[!DNL Customer Journey Analytics] (CJA)** -- Connections, data views, workspace analysis, guided analysis, computed metrics, dashboards, audience publishing, and content analytics
- **[!DNL Adobe Experience Platform] (AEP)** -- Data lake, datasets, XDM schemas, profile and event data that feed CJA connections

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
