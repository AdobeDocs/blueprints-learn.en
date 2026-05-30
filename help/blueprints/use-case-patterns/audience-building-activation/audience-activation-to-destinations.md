---
title: Audience activation to destinations
description: Learn how to evaluate and publish audience segments to external destinations for targeting or suppression using Adobe Real-Time CDP.
solution: Real-Time Customer Data Platform, Experience Platform
exl-id: b0b9d937-45d2-48f9-ac4c-3611c6e35f58
---
# Audience activation to destinations

This guide describes the audience activation to destinations use case pattern, which evaluates audience segments in Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP) and publishes them to ad platforms, cloud storage, CRM systems, or data partners for targeting, suppression, lookalike modeling, or analytics enrichment. It is designed for solution architects, marketing technologists, and implementation engineers who need to understand what this pattern does, the business objectives it supports, the tactical use cases it enables, and the Adobe applications involved.

This pattern covers the full lifecycle of audience activation -- from defining and evaluating audience segments through configuring destination connections and publishing audiences, to monitoring activation health and enforcing governance compliance.

## Use case pattern

**Audience Activation to Destinations** -- Evaluate and publish an audience segment to external destinations for targeting or suppression.

**Execution plan:** Audience Evaluation > Destination Configuration > Audience Activation > Monitoring

## Use case overview

Organizations need to deliver audience data to external systems to power paid media campaigns, enrich CRM records, share data with partners, or feed downstream analytics. Audience Activation to Destinations is the foundational activation pattern in RT-CDP: it evaluates which profiles qualify for a target audience, connects to one or more external destinations, maps profile attributes to destination-specific fields, and publishes the audience for downstream consumption.

This pattern applies whenever the goal is to get audience data to an external system in the right format at the right time. It does not involve message delivery, on-site personalization, or analytics. It is the most common starting point for RT-CDP implementations and serves as a building block that other patterns compose on top of.

Typical stakeholders include digital marketing teams managing paid media, data teams enriching warehouses, CRM teams preparing contact lists for campaigns, and privacy teams ensuring governance compliance on outbound data flows.

>[!NOTE]
>If your organization uses [!DNL Real-Time CDP] B2B Edition and activates to account-based destinations, see [B2B audience activation](../b2b/account-audience-activation.md). That pattern shares the same activation mechanics but uses a B2B account-and-person data model and requires the B2B Edition license.

## Key business objectives

The following business objectives are supported by this use case pattern.

### Acquire new customers

Expand the customer base through targeted acquisition campaigns, lookalike audiences, and paid media optimization.

**KPIs:** New Customers, Customer Acquisition Cost, Prospect/Lead Conversion

[Learn more about acquiring new customers](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Reduce customer acquisition cost

Improve targeting efficiency, suppress existing customers from acquisition campaigns, and optimize media spend.

**KPIs:** Customer Acquisition Cost, Cost Per Lead, Efficiency

[Learn more about reducing customer acquisition cost](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### Optimize marketing spend and ROI

Improve return on marketing investment through better targeting, attribution, audience suppression, and budget allocation.

**KPIs:** Cost Savings, Customer Acquisition Cost, Incremental Revenue

[Learn more about optimizing marketing spend and ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Example tactical use cases

- **Ad platform audience targeting** -- Push qualified segments to paid media platforms for campaign targeting
- **Paid media suppression of existing customers** -- Exclude known customers from acquisition campaigns on ad platforms to eliminate wasted spend
- **Lookalike seed audiences** -- Push high-value customer segments to Facebook, Google Ads, or The Trade Desk as seed audiences for lookalike expansion
- **CRM sync for sales enablement** -- Activate high-intent or high-value audiences so sales teams can prioritize outreach
- **Data partner audience sharing** -- Share qualified audience segments with data partners for co-op targeting or measurement
- **Cloud storage export for data warehouse enrichment** -- Export audience membership and profile attributes to Amazon S3, Azure Blob, Google Cloud Storage, or SFTP for downstream analytics
- **Retargeting audience activation** -- Activate site visitors who did not convert to retargeting platforms
- **Contact list sync to email service providers** -- Push audience membership to third-party email platforms for coordinated outreach

## Key performance indicators

| KPI | Description | Measurement approach |
| --- | --- | --- |
| Customer Acquisition Cost (CAC) | Cost to acquire a new customer via activated audiences | Total media spend / new customers attributed to activated audiences |
| Audience Match Rate | Percentage of activated profiles successfully matched at the destination | Profiles matched at destination / profiles exported from RT-CDP |
| Suppression Savings | Media spend avoided by suppressing existing customers from acquisition campaigns | Estimated CPM x suppressed audience size |
| Activation Delivery Rate | Percentage of profiles successfully delivered to the destination | Profiles delivered / profiles in the source audience |
| Time to Activation | Elapsed time from audience definition to first delivery at the destination | Measure from segment creation to first confirmed dataflow run |
| Audience Population Accuracy | Alignment between expected and actual audience sizes at the destination | Destination audience count / RT-CDP audience count |

## Applications

- **Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP)** -- Audience evaluation, destination management, audience activation, consent and governance enforcement
- **Adobe [!DNL Experience Platform] (AEP)** -- Profile store, identity service, segmentation engine, data governance

## Architecture

The following reference architecture illustrates how audience and profile data flows from Real-Time CDP to enterprise destinations including cloud storage, streaming endpoints, and SaaS applications.

![Reference architecture for audience and profile activation to enterprise destinations](/help/blueprints/audience-activation/assets/known_activation.png)

## Related documentation

**Destinations**

- [Destinations overview](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Destinations catalog](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Activate audiences to streaming destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Activate audiences to batch profile export destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Activate audiences on-demand to batch destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [Destinations guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- [Destination SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/destination-sdk/overview)

**Audiences and segmentation**

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language reference](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Audience Composition overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Segmentation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

**Identity and profile**

- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Identity namespaces overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Identity graph linking rules](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Profile overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

**Data modeling and schemas**

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

**Data governance**

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview)
- [Data governance policies](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/policies/overview)
- [Policy enforcement](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [Consent and preferences](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Monitoring and observability**

- [Monitor dataflows for destinations](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
- [License usage dashboard](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Computed attributes**

- [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Computed attributes UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)

**Data collection and sources**

- [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Configure datastreams](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)

**Administration**

- [Sandboxes overview](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home)
- [Access control overview](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home)
- [Attribute-based access control](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/abac/overview)

**Guardrails**

- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identity Service guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
- [Activation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- [Ingestion guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
