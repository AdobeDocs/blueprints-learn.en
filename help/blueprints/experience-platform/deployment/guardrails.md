---
title: Experience Platform and Application Guardrails 
description: Guardrails define the performance expectations and impact for the components and services within Adobe Experience Platform and Applications
solution: Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
---

# Guardrails

Guardrails reflect system constraints, expected latencies, and performance expectations to optimize customer architecture and use case performance and help to ensure stability, avoid errors or unexpected results.

## Types of Guardrails

| Guardrail type | Description |
|---|---|
| Performance guardrail (Soft limit) | Performance guardrails are usage limits that relate to the scoping of your use cases and outline expected performance under normal conditions. When exceeded, you may experience performance degradation and latency. Performance Guardrails are documented in the Experience League documents under the guardrail sections for each Solution as outlined below.|
| Static Limit (Hard limit) | These are system enforced limits that cannot be exceeded. Static limits are typically contractually bound and outlined in the customer contract and the [Product Descriptions](https://helpx.adobe.com/legal/product-descriptions.html).|

>[!NOTE]
>
> Guardrails are not intended to be Service Level Agreements, but rather guidance for optimal configurations and expected system behavior. Any guardrails that are system or contractual limits or Service Level Agreements will be documented specifically in the customer contracts and product descriptions. If you are interested in learning about custom limits, please contact your customer care representative.

>[!NOTE]
>
> For use cases with strict latency or performance needs, Adobe suggests discussing the details with your Adobe Account Team and Implementation Partner. Each customer setup can vary across data ingestion patterns, segment rules, and activation channels. It's important to test and review your use case before launching to understand how it will behave.

## Guardrails Reference Documentation for Adobe Experience Platform and Applications

The following pages provide information about guardrails for Adobe Experience Platform features, services, and applications:

**Experience Platform applications**

* [Real-Time CDP guardrails overview](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Customer Journey Analytics audience sharing guardrails](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
* [Customer Journey Analytics data ingestion guardrails](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Journey Optimizer guardrails](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html)

**Experience Platform services**

* [Data ingestion guardrails](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html)
* [[!DNL Edge Network] API Guardrails](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [Real-time Customer Profile and Segmentation Guardrails](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
* [Identity Guardrails](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=en)
* [Query Service Guardrails](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=en)
* [Destination Activation Guardrails](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html)

## End-to-end latency diagrams {#end-to-end-latency}

### Experience Platform Edge Network and Hub Primary Observed Latencies {#edge-hub-latencies}

The following diagram depicts the primary edge and hub observed latencies to be aware of when architecting use case on the Experience Platform and Applications. 

![Experience Platform [!DNL Edge Network] and hub primary observed latencies.](/help/blueprints/experience-platform/deployment/assets/aep_edge_hub_latency_v1.svg "Experience Platform Edge Network and hub primary observed latencies"){width="1000" zoomable="yes"}

### Data ingestion {#data-ingestion}

The diagram below displays expected data ingestion latency values through [streaming ingestion](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html) and [batch ingestion](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=en) when bringing data into Real-Time CDP. Click the image to see a high-resolution version.

![Data ingestion high-level visual overview.](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg "Data ingestion high-level visual overview and latency values"){width="1000" zoomable="yes"}

### Segmentation {#segmentation}

The diagram below displays expected latency values when working with audiences in the [Real-Time CDP segmentation service](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html). Click the image to see a high-resolution version.

![Segmentation high-level visual overview.](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg "Segmentation high-level visual overview and latency values"){width="1000" zoomable="yes"}

### Real-time Customer Data Platform & [!DNL Edge Network] {#adobe-edge-latency}

The diagram below displays expected latency values when leveraging the [!DNL Edge Network] - for example to leverage RTCDP audiences in [Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en). Click the image to see a high-resolution version.

![Adobe Edge Network and Experience Platform high-level visual overview.](/help/blueprints/experience-platform/deployment/assets/RTCDP_Edge_guardrails.svg "Exporting audiences to Adobe Target high-level visual overview and latency"){width="1000" zoomable="yes"}

### Customer Journey Analytics {#customer-journey-analytics}

The diagram below displays expected latency values when working with [Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=en). Click the image to see a high-resolution version.

![Working with Customer Journey Analytics high-level visual overview.](/help/blueprints/experience-platform/deployment/assets/CJA_guardrails.svg "Working with Customer Journey Analytics high-level visual overview and latency values"){width="1000" zoomable="yes"}

### Journey Optimizer {#journey-optimizer}

The diagram below displays expected latency values when working with [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=en). Click the image to see a high-resolution version.

![Working with Adobe Journey Optimizer high-level visual overview.](/help/blueprints/experience-platform/deployment/assets/AJO_guardrails.svg "Working with Adobe Journey Optimizer high-level visual overview and latency values"){width="1000" zoomable="yes"}