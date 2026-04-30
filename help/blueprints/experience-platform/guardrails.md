---
title: Experience Platform and Application Guardrails
description: Guardrails define the performance expectations and impact for the components and services within Adobe Experience Platform and Applications
solution: Experience Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
TQID: https://experienceleague.adobe.com/ZSHbFR3sEy4C-876IU3yN8U5vOUVvDWIP-O3l-wKm78
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: a37e4ecd-c740-426a-addf-cb1b483c5c5a
    internal-label: Segmentation
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
subfeature_v2:
  - id: d1823595-9241-4128-8a33-e4ac3bf08773
    internal-label: Audiences
  - id: e5ae22e3-a3b0-46ed-804f-9abf1bbe3e74
    internal-label: Guardrails
  - id: ee602049-8a18-43df-9299-a689a025a371
    internal-label: Use cases
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
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
> For use cases with strict latency or performance needs, Adobe suggests discussing the details with your Adobe Account Team and Implementation Partner. Each customer setup can vary across data ingestion patterns, profile counts and richness, segment rules, and activation channels. As such it is important to architect and test your use case to optimize its performance and fully understand expected performance characteristics. 

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

![Experience Platform [!DNL Edge Network] and hub primary observed latencies.](/help/blueprints/experience-platform/assets/aep_edge_hub_latency_v1.svg "Experience Platform Edge Network and hub primary observed latencies"){width="1000" zoomable="yes"}