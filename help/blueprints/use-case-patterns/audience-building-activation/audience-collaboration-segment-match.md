---
title: Audience Collaboration
description: Learn how to share and match audience segments across sandboxes or organizations using Segment Match.
solution: Real-Time Customer Data Platform, Experience Platform
exl-id: 7014849c-5e32-4ec3-a531-c0e8ce896f44
---
# Audience Collaboration

This guide describes the audience collaboration use case pattern, which uses [!DNL Segment Match] in [!DNL Real-Time CDP] and [!DNL Adobe Experience Platform] to share and match audience segments across sandboxes or organizations in a privacy-safe manner. It is designed for solution architects, marketing technologists, and implementation engineers who need to understand what this pattern does, the business objectives it supports, the tactical use cases it enables, and the Adobe applications involved.

[!DNL Segment Match] enables two or more [!DNL Experience Platform] organizations (or sandboxes within an organization) to collaborate on audience data by sharing segment membership information without exposing underlying PII. Participants can estimate overlap, share audiences, and activate matched profiles to downstream destinations.

## Use case pattern

This use case follows the Audience Collaboration pattern.

Share and match audience segments across sandboxes or organizations using [!DNL Segment Match].

**Execution plan:** Segment Selection > Match Configuration > Overlap Estimation > Audience Sharing > Activation

## Use case overview

Organizations increasingly need to collaborate on audience data with partners, subsidiaries, or across business units while maintaining strict privacy controls. Audience collaboration addresses this need by enabling secure segment sharing through [!DNL Segment Match] -- a feature within [!DNL Real-Time CDP] that allows two or more [!DNL Experience Platform] organizations (or sandboxes) to exchange audience membership information using hashed, privacy-safe identifiers.

The business scenario typically involves one organization (the sender) that has built a valuable audience segment and wants to share it with a partner organization (the receiver) for joint targeting, suppression, or enrichment. Before sharing, both parties can estimate audience overlap to assess value. Once shared, the receiving organization can activate the matched audience through their own destinations.

This pattern is distinct from standard audience activation because it operates between organizations or sandboxes rather than to external advertising or marketing destinations. It is also distinct from data clean rooms or third-party collaboration platforms because it operates natively within the Adobe ecosystem using [!DNL Experience Platform] identity infrastructure.

## Key business objectives

The following business objectives are supported by this use case pattern.

### Acquire new customers

Expand the customer base through targeted acquisition campaigns, lookalike audiences, and paid media optimization. Audience collaboration enables organizations to discover new prospect pools by matching their segments against partner audiences, identifying high-value overlap, and reaching net-new customers through joint activation.

- **KPIs:** New Customers, Customer Acquisition Cost, Prospect/Lead Conversion
- [Acquire new customers](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Reduce customer acquisition cost

Improve targeting efficiency, suppress existing customers from acquisition campaigns, and optimize media spend. By sharing suppression segments across organizations or business units, teams can avoid wasted spend on already-converted customers and focus budgets on genuinely new prospects.

- **KPIs:** Customer Acquisition Cost, Cost Per Lead, Efficiency
- [Reduce customer acquisition cost](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### Optimize marketing spend and ROI

Improve return on marketing investment through better targeting, attribution, audience suppression, and budget allocation. [!DNL Segment Match] enables cross-organization audience suppression and joint targeting that reduces duplication and improves precision.

- **KPIs:** Cost Savings, Customer Acquisition Cost, Incremental Revenue
- [Optimize marketing spend and ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Example tactical use cases

- **Publisher-advertiser audience matching** -- A brand shares its high-value customer segment with a media publisher to estimate overlap and target matched users with personalized ads, improving campaign relevance without exposing PII.
- **Cross-brand suppression within a holding company** -- Multiple brands under a parent organization share customer segments to suppress existing customers of sister brands from acquisition campaigns, reducing wasted ad spend.
- **Retail media network audience enrichment** -- A retailer shares purchase-based segments with CPG brand partners, enabling the brands to target proven buyers on the retailer's media network with higher conversion rates.
- **Co-marketing partner audience discovery** -- Two non-competing brands evaluate audience overlap to assess partnership potential before launching a joint campaign, using overlap estimation to validate audience alignment.
- **Data cooperative segment sharing** -- Organizations in a data cooperative share hashed audience segments to expand targeting reach while maintaining privacy compliance and data governance controls.
- **Multi-sandbox audience federation** -- A global enterprise shares audience segments across regional sandboxes to enable consistent customer targeting across markets while respecting regional data residency requirements.
- **Loyalty program cross-partner activation** -- A loyalty coalition shares loyalty tier segments with participating merchants so each partner can offer tier-appropriate promotions to the shared customer base.
- **Measurement and attribution collaboration** -- An advertiser shares a conversion segment with a media partner so the partner can measure campaign effectiveness by matching exposed users against converters.

## Key performance indicators

The following KPIs help measure the success of audience collaboration implementations.

| KPI | Description | Measurement approach |
| --- | --- | --- |
| Audience Overlap Rate | Percentage of profiles in the shared segment that match between sender and receiver | [!DNL Segment Match] overlap estimation report |
| Matched Audience Size | Number of profiles successfully matched and available for activation | [!DNL Segment Match] share status and audience population count |
| New Customer Acquisition from Matched Audiences | Net-new customers acquired through campaigns targeting matched segments | Conversion tracking on campaigns using matched audiences |
| Customer Acquisition Cost Reduction | Decrease in cost per acquisition when using matched audiences vs. broad targeting | Campaign cost analysis comparing matched vs. unmatched audience performance |
| Suppression Savings | Media spend saved by suppressing known customers from acquisition campaigns | Pre/post suppression media spend comparison |
| Campaign Performance Lift | Improvement in conversion rate, click-through rate, or engagement for campaigns using matched audiences | A/B test comparing matched audience campaigns vs. control |
| Time to Collaboration | Elapsed time from segment share initiation to activation readiness | [!DNL Segment Match] workflow timestamps |

## Applications

The following applications are used in this use case pattern.

- **[!DNL Real-Time CDP]** -- Provides the [!DNL Segment Match] capability for privacy-safe audience sharing, audience evaluation for segment creation, and destination activation for downstream use of matched audiences.
- **[!DNL Adobe Experience Platform]** -- Provides the foundational data infrastructure including identity resolution, profile unification, data governance, and consent enforcement that [!DNL Segment Match] depends on.

## Related documentation

The following resources provide additional detail on the capabilities used in this use case pattern.

### [!DNL Segment Match]

- [Segment Match overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Segment Match troubleshooting](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Segmentation and audiences

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Audience Composition overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language reference](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Identity and profile

- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Identity namespaces overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Real-Time Customer Profile overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Data governance and consent

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview)
- [Policy enforcement](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [Consent and preferences](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Consent and preferences field group](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

### Destinations and activation

- [Destinations overview](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Destinations catalog](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Monitor dataflows for destinations](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)

### Data modeling and schema

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Schema composition basics](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### Administration and access control

- [Access control overview](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home)
- [Sandboxes overview](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home)

### Monitoring and observability

- [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### Guardrails

- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Segmentation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [Activation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

### Tutorials

- [Create a schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [Enable a dataset for Profile](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/enable-for-profile)
