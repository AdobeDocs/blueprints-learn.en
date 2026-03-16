---
title: B2B Customer Journey Analytics blueprint
description: Include B2B account, opportunity, and buying-group data in Customer Journey Analytics for account-based reporting and journey analysis.
solution: Customer Journey Analytics
exl-id: d55ed43d-aabf-4722-9ae9-a2aef99f19e0
---
# B2B Customer Journey Analytics blueprint

Customer Journey Analytics B2B Edition enables account-based reporting and analysis for B2B organizations. Unlike person-centric B2C analytics, this blueprint places the **account** at the center of the data model so you can analyze complex B2B purchase journeys across multiple stakeholders, buying groups, and sales cycles. Use [!DNL Customer Journey Analytics] to unify behavioral data with B2B dimensions—accounts, opportunities, campaigns, and marketing lists—for journey-based insights and audience creation.

## Applications

* Adobe [!DNL Customer Journey Analytics] (B2B Edition)
* Adobe Experience Platform (for B2B and event data)

## Use cases

* **Optimize account marketing** — Analyze marketing impact across campaigns, channels, and content on buying groups within accounts, pipeline progression, and upsell/cross-sell opportunities.
* **Grow key accounts** — Identify high-value touchpoints across buying groups within key accounts to inform marketing and sales actions, and calculate customer lifetime value at the account level.
* **Build product value** — Measure the impact of product releases and usage on customer satisfaction at account and user levels to optimize features and inform development.
* **Person-based B2B analysis** — Combine account and opportunity context with individual user behavior for lead scoring, engagement, and journey analysis.

## Prerequisites

* [!DNL Customer Journey Analytics] B2B Edition entitlement.
* B2B and behavioral data in Adobe Experience Platform: B2B datasets (accounts, opportunities, persons, campaigns, marketing lists, B2B activities) and event data (web, mobile, or other channels) available in a [CJA connection](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-connections/create-connection.html).
* [B2B naming for CJA](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-dataviews/b2b.html): B2B-specific data view settings (account ID, opportunity ID, and related dimensions) configured for the connection.

## Architecture

![Customer Journey Analytics architecture with B2B account and opportunity data unified for journey analysis](assets/CJA.svg){zoomable="yes"}

Data flows from Experience Platform (B2B and event datasets) into [!DNL Customer Journey Analytics] via a CJA connection. B2B dimensions are exposed in data views so analysis and audiences can be built at account, opportunity, and person levels.

## Guardrails

* For B2B Edition product limits and entitlements, see the [Customer Journey Analytics B2B product description](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics-b2b.html).
* For Analytics Platform and CJA technical limits, see [Analytics Platform guardrails](https://experienceleague.adobe.com/en/docs/analytics-platform/using/technotes/guardrails).
* For CJA data ingestion and connection limits, see [Customer Journey Analytics data ingestion guardrails](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F).
* If publishing CJA audiences to Real-time Customer Data Platform, see [Customer Journey Analytics audience sharing guardrails](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency).
* For end-to-end latencies and platform guardrails, refer to the [deployment guardrails document](../experience-platform/guardrails.md).

## Implementation steps

1. **Ingest B2B and event data into Experience Platform** — Bring in account, opportunity, person, campaign, and activity data, plus behavioral events, using [sources](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html) (e.g. [!DNL Marketo Engage], CRM, or other B2B connectors).
2. **Create a CJA connection** — [Add the relevant Experience Platform datasets](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-connections/create-connection.html) (B2B and event) to a Customer Journey Analytics connection.
3. **Configure B2B in the data view** — Enable [B2B naming and key dimensions](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-dataviews/b2b.html) (account ID, opportunity ID, etc.) in the connection’s data view(s).
4. **Build account-based analysis and audiences** — Use [CJA B2B use cases and reporting](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/b2b.html) to create reports, breakdowns, and audiences at account and opportunity level; optionally [publish audiences to Real-time CDP](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html) for activation.

## Related documentation

### Customer Journey Analytics B2B Edition

* [Customer Journey Analytics B2B Edition](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-b2b/cja-b2b-edition.html)
* [B2B use cases](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/b2b.html)
* [B2B Edition use cases overview](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/b2b/b2b-edition/use-cases-overview.html)
* [An example person-based B2B project](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/b2b/example.html)

### Connections and data views

* [Create a connection](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-connections/create-connection.html)
* [B2B data view settings](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-dataviews/b2b.html)

### Audiences and guardrails

* [Publish CJA audiences to Real-time CDP](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html)
* [Experience Platform and application guardrails](../experience-platform/guardrails.md)
