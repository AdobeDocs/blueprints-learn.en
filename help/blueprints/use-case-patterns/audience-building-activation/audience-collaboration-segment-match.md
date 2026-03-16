---
title: Audience Collaboration with Segment Match
description: Learn how to share and match audience segments across sandboxes or organizations using Segment Match.
solution: Real-Time Customer Data Platform, Experience Platform
exl-id: 7014849c-5e32-4ec3-a531-c0e8ce896f44
---
# Audience collaboration with Segment Match

This guide provides a comprehensive implementation reference for audience collaboration using [!DNL Segment Match] in [!DNL Real-Time CDP] and [!DNL Adobe Experience Platform]. It is designed for solution architects, marketing technologists, and implementation engineers who need to share and match audience segments across sandboxes or organizations in a privacy-safe manner.

Use this plan to understand the available approaches, evaluate trade-offs, and navigate [!DNL Adobe Experience League] for detailed configuration instructions.

[!DNL Segment Match] enables two or more [!DNL Experience Platform] organizations (or sandboxes within an organization) to collaborate on audience data by sharing segment membership information without exposing underlying PII. Participants can estimate overlap, share audiences, and activate matched profiles to downstream destinations.

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

| KPI | Description | Measurement method |
| --- | --- | --- |
| Audience Overlap Rate | Percentage of profiles in the shared segment that match between sender and receiver | [!DNL Segment Match] overlap estimation report |
| Matched Audience Size | Number of profiles successfully matched and available for activation | [!DNL Segment Match] share status and audience population count |
| New Customer Acquisition from Matched Audiences | Net-new customers acquired through campaigns targeting matched segments | Conversion tracking on campaigns using matched audiences |
| Customer Acquisition Cost Reduction | Decrease in cost per acquisition when using matched audiences vs. broad targeting | Campaign cost analysis comparing matched vs. unmatched audience performance |
| Suppression Savings | Media spend saved by suppressing known customers from acquisition campaigns | Pre/post suppression media spend comparison |
| Campaign Performance Lift | Improvement in conversion rate, click-through rate, or engagement for campaigns using matched audiences | A/B test comparing matched audience campaigns vs. control |
| Time to Collaboration | Elapsed time from segment share initiation to activation readiness | [!DNL Segment Match] workflow timestamps |

## Use case pattern

This use case follows the Audience Collaboration pattern.

Share and match audience segments across sandboxes or organizations using [!DNL Segment Match].

**Function chain:** Segment Selection > Match Configuration > Overlap Estimation > Audience Sharing > Activation

## Applications

The following applications are used in this use case pattern.

- **[!DNL Real-Time CDP]** -- Provides the [!DNL Segment Match] capability for privacy-safe audience sharing, audience evaluation for segment creation, and destination activation for downstream use of matched audiences.
- **[!DNL Adobe Experience Platform]** -- Provides the foundational data infrastructure including identity resolution, profile unification, data governance, and consent enforcement that [!DNL Segment Match] depends on.

## Foundational functions

The following foundational capabilities must be in place for this use case pattern. For each function, the status indicates whether it is typically required, assumed to be pre-configured, or not applicable.

| Foundational function | Status | What must be in place | Experience League reference |
| --- | --- | --- | --- |
| Administration & Governance | Required | Both sender and receiver organizations must have sandboxes provisioned with appropriate roles and permissions. Users managing [!DNL Segment Match] must have permissions to view and share segments, configure connections, and manage partner feeds. ABAC policies should be configured to control which users can initiate and accept segment shares. | [Access control overview](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Data Modeling & Preparation | Assumed in Place | XDM schemas for profiles and events must exist with the required field groups. Profile and event datasets must be created and enabled for [!DNL Real-Time Customer Profile]. The data model must support the identity namespaces used for segment matching (typically hashed email or hashed phone). | [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Data Sources & Collection | Assumed in Place | Customer data must be actively flowing into [!DNL Experience Platform] through configured data sources (SDKs, source connectors, batch ingestion). Profiles must be populated with the identity types used for [!DNL Segment Match] (e.g., hashed email). | [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Identity & Profile Configuration | Required | Identity namespaces must be configured for the identifiers used in segment matching. Both sender and receiver must use compatible identity namespaces. Merge policies must be configured to unify profiles correctly. Identity linking rules should be established to ensure accurate profile resolution. | [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| Audience Definition & Segmentation | Required | Source audiences must be defined and evaluated before they can be shared via [!DNL Segment Match]. Audiences should be built using [!DNL Segment Builder] or [!DNL Audience Composition] with batch evaluation completed. Only batch-evaluated audiences are eligible for [!DNL Segment Match] sharing. | [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## Supporting functions

The following capabilities augment this use case pattern but are not required for core execution.

| Supporting function | Status | Why it matters | Experience League reference |
| --- | --- | --- | --- |
| Computed / Derived Attribute Creation | Recommended | Computed attributes such as lifetime purchase value, engagement score, or product affinity can create more precise segments for sharing. Higher-quality input segments lead to more valuable audience collaboration. | [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Recommended | Consent and data retention policies ensure that shared segments comply with privacy regulations. Dataset expiration policies help manage the lifecycle of received audience data. Consent enforcement prevents sharing of profiles that have opted out. | [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Data Usage Labeling & Enforcement | Included | Data governance policies must be evaluated before sharing segments to ensure compliance. Labels on identity fields and profile attributes determine what can be shared. Governance enforcement prevents unauthorized data from being included in segment shares. | [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Monitoring & Observability | Recommended | Monitoring the [!DNL Segment Match] sharing process, overlap estimation jobs, and activation dataflows helps detect failures early. Alerts can be configured for share failures or unexpectedly low match rates. | [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting & Analysis | Recommended | Measuring the performance of campaigns that use matched audiences validates the value of the collaboration. [!DNL Customer Journey Analytics] analysis can compare matched audience campaign performance against control groups. | [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Application functions

This plan exercises the following functions from the application function catalog. Functions are mapped to implementation phases rather than numbered steps.

### [!DNL Real-Time CDP]

| Function | Implementation phase | Description |
| --- | --- | --- |
| Audience Evaluation | Phase 1: Segment Selection & Preparation | Evaluate segment membership using batch evaluation to produce the audiences that will be shared via [!DNL Segment Match] |
| Audience Composition | Phase 1: Segment Selection & Preparation | Optionally compose derived audiences (rank, split, exclude, enrich) to create more targeted segments for sharing |
| Consent & Governance Enforcement | Phase 2: Match Configuration & Governance | Enforce data usage policies and consent preferences before sharing segments to ensure compliance |
| Audience Activation | Phase 5: Matched Audience Activation | Publish matched audiences received via [!DNL Segment Match] to external destinations for targeting or suppression |
| Destination Configuration | Phase 5: Matched Audience Activation | Configure connections to external destinations where matched audiences will be activated |

## Prerequisites

- Both sender and receiver organizations have [!DNL Real-Time CDP] provisioned with [!DNL Segment Match] entitlement
- [!DNL Segment Match] is enabled for the organizations or sandboxes participating in the collaboration
- Partner connection has been established between the sender and receiver organizations in the [!DNL Segment Match] UI
- Both organizations use compatible identity namespaces (e.g., both have hashed email configured)
- Source audiences have been defined and evaluated with non-zero populations
- Data governance policies are configured and data usage labels are applied to relevant datasets and fields
- Users on both sides have the necessary permissions to manage [!DNL Segment Match] connections, shares, and feeds
- Consent fields are populated on profiles to enable consent-based filtering before sharing

## Implementation options

The following options describe different approaches for implementing audience collaboration with [!DNL Segment Match]. Select the option that best fits your organizational structure and collaboration requirements.

### Option A: Direct segment share (one-to-one)

This option is best for bilateral partnerships between two specific organizations, such as an advertiser and a publisher, or two brands in a co-marketing arrangement.

**How it works:**

In a direct one-to-one segment share, the sender organization selects one or more evaluated audiences, initiates a share with a specific partner organization, and the receiver accepts the share. The overlap estimation runs automatically to show both parties the percentage and volume of matched profiles before the share is finalized.

The sender defines which identity namespaces to use for matching and selects the segments to share. The receiver reviews the incoming share, accepts it, and the matched audience becomes available in their audience list for downstream activation. Only hashed identity overlap is exchanged -- no underlying PII or profile attribute data crosses organizational boundaries.

This approach is straightforward and provides full control to both parties. The sender chooses exactly what to share and with whom, and the receiver has the option to accept or reject each share.

**Key considerations:**

- Requires explicit partner connection setup between the two organizations
- Both organizations must agree on identity namespaces for matching
- Overlap estimation provides transparency before commitment
- Each share must be individually managed and monitored

**Advantages:**

- Simple, well-understood bilateral workflow
- Full transparency through overlap estimation before sharing
- Granular control -- sender chooses exactly which segments to share
- Privacy-safe -- only hashed identifiers are used for matching
- Receiver can selectively accept or reject shares

**Limitations:**

- Does not scale efficiently when collaborating with many partners simultaneously
- Each partnership requires separate connection setup and management
- Share configuration must be repeated for each new segment

**Experience League:**

- [Segment Match overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Segment Match troubleshooting](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Option B: Multi-partner segment distribution (one-to-many)

This option is best for organizations that need to share segments with multiple partners simultaneously, such as a retail media network sharing purchase-based segments with multiple brand advertisers, or a holding company distributing segments to subsidiary brands.

**How it works:**

In a one-to-many distribution model, the sender organization establishes [!DNL Segment Match] connections with multiple partner organizations and shares the same or different segments with each. The sender manages a portfolio of partner connections and can selectively share different audience segments with different partners based on the relationship and use case.

Each partner connection operates independently -- overlap estimation, share acceptance, and activation are managed per partner. The sender can control which segments each partner receives, enabling differentiated collaboration strategies (e.g., premium partners receive more granular segments, standard partners receive broader ones).

This approach uses the same underlying [!DNL Segment Match] mechanism as Option A but applies it at scale with an operational framework for managing multiple concurrent partnerships.

**Key considerations:**

- Requires robust operational processes for managing multiple partnerships
- Governance policies must account for sharing the same segments with multiple external parties
- Each partner may use different identity namespaces, requiring flexible configuration
- Overlap rates will vary by partner, requiring per-partner evaluation

**Advantages:**

- Scales audience collaboration across an ecosystem of partners
- Differentiated sharing strategies per partner
- Centralized management of all outbound segment shares from one organization
- Each partnership maintains independent governance and consent controls

**Limitations:**

- Operational complexity increases with each additional partner
- Monitoring and troubleshooting must be done per-partner
- Governance review required for each new partner connection
- Partners do not see each other's data or share status

**Experience League:**

- [Segment Match overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)

### Option C: Cross-sandbox audience federation

This option is best for large enterprises with multiple [!DNL Experience Platform] sandboxes (e.g., regional sandboxes, brand-specific sandboxes, or environment-specific sandboxes) that need to share audience segments across internal boundaries without moving raw data.

**How it works:**

Rather than sharing between separate organizations, cross-sandbox audience federation uses [!DNL Segment Match] to share audience segments between sandboxes within the same organization. This enables a global marketing team to build a segment in a central sandbox and share it with regional sandboxes, or allows brand-specific sandboxes to share suppression lists with each other.

The workflow mirrors the direct segment share (Option A) but operates within the organizational boundary. Sandbox-to-sandbox connections are established through [!DNL Segment Match], and segments are shared using the same privacy-safe matching process. The receiving sandbox gets the matched audience as a new audience that can be activated through its own locally configured destinations.

This approach is particularly valuable when data residency requirements prevent moving raw customer data between regions but audience-level collaboration is permitted.

**Key considerations:**

- Requires [!DNL Segment Match] entitlement that supports cross-sandbox sharing
- Identity namespaces must be consistent across sandboxes
- Merge policies in each sandbox may resolve profiles differently, potentially affecting match rates
- Governance policies apply independently per sandbox

**Advantages:**

- Enables audience collaboration without moving raw data across sandbox boundaries
- Supports data residency and regional compliance requirements
- Leverages existing organizational identity infrastructure
- Simpler governance review since sharing occurs within the same organization

**Limitations:**

- Requires consistent identity namespace configuration across sandboxes
- Match rates depend on merge policy consistency between sandboxes
- Does not address cross-organization collaboration needs
- Sandbox Tooling may be needed to synchronize schema and configuration

**Experience League:**

- [Segment Match overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Sandboxes overview](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home)

### Option comparison

The following table compares the three implementation options across key criteria.

| Criteria | Option A: Direct Segment Share | Option B: Multi-Partner Distribution | Option C: Cross-Sandbox Federation |
| --- | --- | --- | --- |
| Best for | Bilateral partnerships | Ecosystem-scale collaboration | Internal cross-sandbox sharing |
| Complexity | Low | High | Medium |
| Number of partners | 1 | Many | Internal sandboxes |
| Governance overhead | Low | High (per-partner review) | Medium (within organization) |
| Operational management | Simple | Requires partner management framework | Moderate |
| Data residency support | N/A | Depends on partner location | Strong |
| Requires | Partner connection setup | Multiple partner connections | Cross-sandbox [!DNL Segment Match] |

### Choose the right option

Use the following decision guidance to select the appropriate implementation approach:

1. **Are you collaborating with an external organization or within your own organization?**
   - External organization: proceed to question 2.
   - Within your own organization (across sandboxes): choose **Option C** (Cross-Sandbox Federation).

2. **How many external partners will you collaborate with?**
   - One partner: choose **Option A** (Direct Segment Share).
   - Multiple partners: choose **Option B** (Multi-Partner Distribution).

3. **Do you have data residency constraints that prevent moving raw data across regions?**
   - Yes: choose **Option C** regardless of whether partners are internal or external -- use cross-sandbox sharing to maintain data locality.

## Implementation phases

The following phases describe the end-to-end implementation process for audience collaboration with [!DNL Segment Match].

### Phase 1: Select and prepare segments

**Application function:** [!DNL Real-Time CDP]: Audience Evaluation, [!DNL Real-Time CDP]: Audience Composition

This phase involves defining and evaluating the audience segments that will be shared through [!DNL Segment Match]. The source segments must be fully evaluated with non-zero populations before they can be selected for sharing. This phase also covers optional audience composition to refine segments before sharing.

**Decision points in this phase:**

>[!NOTE]
>
>**Decision: Audience definition approach**
>
>How should the source audiences for sharing be created?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Segment Builder (segment rules) | Standard audience definitions based on profile attributes, events, or segment membership | Supports batch, streaming, and edge evaluation; most flexible for defining criteria |
>| Audience Composition | Derived audiences requiring rank, split, exclude, or enrich operations on existing segments | Only supports batch evaluation; limited to 10 composition canvases per sandbox |
>| Federated Audience Composition | Audiences built from external data warehouse queries without ingesting data into [!DNL Experience Platform] | Requires [!DNL Federated Audience Composition] entitlement; data stays in the warehouse |

>[!NOTE]
>
>**Decision: Audience evaluation method**
>
>[!DNL Segment Match] requires batch-evaluated audiences. How should evaluation be scheduled?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Scheduled batch (daily) | Standard use cases where daily audience refresh is sufficient | Default evaluation schedule; simplest to manage |
>| On-demand batch | Ad-hoc sharing needs where you want to share the most current audience immediately | Requires manual trigger; useful for time-sensitive collaborations |
>| Custom schedule | Specific timing requirements aligned with partner activation windows | Configure a custom cron schedule; more complex but precise |

**UI navigation:** Customer > Audiences > Create audience > Build rule (for [!DNL Segment Builder]) or Compose audience (for [!DNL Audience Composition])

**Key configuration details:**

- Define audience criteria using profile attributes, behavioral events, and/or segment membership
- Ensure the audience uses a merge policy compatible with the identity namespaces used for [!DNL Segment Match]
- Verify the audience population is non-zero after evaluation
- Apply suppression rules to exclude profiles that should not be shared (e.g., profiles that have opted out of data sharing)

**Where options diverge:**

**For Option A (Direct Segment Share):**
Prepare the specific segments you intend to share with your single partner. Focus on quality over quantity -- curate segments that provide clear value to the partnership.

**For Option B (Multi-Partner Distribution):**
Prepare a portfolio of segments that may be shared with different partners. Consider creating partner-specific segments if different partners need different audience definitions. Use consistent naming conventions to manage segments across partnerships.

**For Option C (Cross-Sandbox Federation):**
Ensure the source audiences in the sending sandbox use identity namespaces that exist in the receiving sandbox. Verify that merge policies are aligned across sandboxes.

**Experience League documentation:**

- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Audience Composition overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Evaluation methods](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home#evaluation-methods)
- [Profile Query Language reference](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Phase 2: Configure matching and governance

**Application function:** [!DNL Real-Time CDP]: Consent & Governance Enforcement

This phase establishes the [!DNL Segment Match] connection between organizations or sandboxes, configures the identity namespaces used for matching, and ensures data governance policies permit the sharing. Governance enforcement acts as a policy gate that must be cleared before any segment data is shared.

**Decision points in this phase:**

>[!NOTE]
>
>**Decision: Identity namespace for matching**
>
>Which identity namespace will be used to match profiles between sender and receiver?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Hashed email (SHA-256) | Both organizations collect email addresses and can hash them consistently | Most common matching key; high match rates for consumer use cases; both sides must use the same hashing algorithm |
>| Hashed phone number | Email is not consistently available but phone numbers are | Lower coverage than email in many markets; useful for mobile-first audiences |
>| Custom namespace (e.g., hashed loyalty ID) | Organizations share a common loyalty or membership program ID | Highest match rates for known shared customer bases; requires pre-existing shared ID infrastructure |
>| Multiple namespaces | Maximizing match rate is critical and both organizations have multiple consistent identifiers | Increases match rates but adds complexity; each namespace must be configured independently |

>[!NOTE]
>
>**Decision: Data governance review**
>
>What governance checks must be completed before sharing?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Standard governance evaluation | Typical use case with standard data usage labels and policies | Evaluate marketing action "Export to Third Party" against dataset labels; resolve any violations before sharing |
>| Enhanced governance with consent filtering | Sharing with external partners where consent must be explicitly verified | Add consent-based filtering to exclude profiles without sharing consent (e.g., consents.share.val = 'n'); stricter but safer |
>| Internal governance review | Cross-sandbox sharing within the same organization | Lighter governance requirements since data stays within organizational boundary; still verify data usage labels |

**UI navigation:** Customer > Audiences > Segment Match > Partner connections

**Key configuration details:**

- Establish a partner connection by exchanging connection identifiers between sender and receiver organizations
- Configure the identity namespaces that will be used for matching on both sides
- Run data governance policy evaluation against the marketing action associated with segment sharing
- Verify that consent fields are populated on profiles and that profiles without sharing consent are excluded
- Review data usage labels on the datasets and schema fields included in the share

**Where options diverge:**

**For Option A (Direct Segment Share):**
Establish a single partner connection. Configure identity namespaces with your specific partner. Governance review focuses on the bilateral relationship.

**For Option B (Multi-Partner Distribution):**
Establish and manage multiple partner connections. Each partner may require a separate governance review. Document the governance approval for each partnership. Consider creating a governance checklist to streamline partner onboarding.

**For Option C (Cross-Sandbox Federation):**
Establish sandbox-to-sandbox connections within the organization. Governance is typically simpler since sharing occurs internally. Ensure identity namespaces are consistent across sandboxes.

**Experience League documentation:**

- [Segment Match overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Policy enforcement](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [Consent and preferences](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

### Phase 3: Estimate overlap

**Application function:** [!DNL Real-Time CDP]: Audience Evaluation (for estimating overlap)

This phase runs the overlap estimation between the sender's segments and the receiver's profile base. Overlap estimation provides both parties with the expected match volume and percentage before committing to the full segment share, enabling informed decisions about the value of the collaboration.

**Decision points in this phase:**

>[!NOTE]
>
>**Decision: Overlap threshold for proceeding**
>
>What minimum overlap rate justifies proceeding with the full segment share?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| No minimum threshold | Exploratory partnerships or when any overlap provides value | Suitable for initial collaborations where you are testing the relationship |
>| Low threshold (1-5%) | Large-scale audience collaboration where even small overlap represents significant volume | Common for publisher-advertiser relationships with large audience bases |
>| Medium threshold (5-20%) | Standard partnerships where meaningful overlap is expected | Typical for co-marketing or same-industry collaborations |
>| High threshold (20%+) | Partnerships where strong audience alignment is a prerequisite | Common for loyalty coalitions or tightly integrated brand partnerships |

**UI navigation:** Customer > Audiences > Segment Match > Shares > Estimate overlap

**Key configuration details:**

- Select the segments to include in the overlap estimation
- Review the overlap report showing matched profile count and percentage
- Share the overlap estimation results with stakeholders on both sides for approval
- Document the overlap metrics as a baseline for measuring collaboration effectiveness
- If overlap is below the acceptable threshold, consider adjusting segment definitions or identity matching configuration before proceeding

**Experience League documentation:**

- [Segment Match overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)

### Phase 4: Share audiences

**Application function:** [!DNL Real-Time CDP]: Audience Evaluation (for share execution)

This phase executes the actual segment share from sender to receiver. The sender initiates the share for the selected segments, and the receiver accepts the incoming share. Once accepted, the matched audience appears in the receiver's audience list as a new audience available for downstream activation.

**Decision points in this phase:**

>[!NOTE]
>
>**Decision: Share direction**
>
>What is the sharing model for this collaboration?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| One-way share (sender to receiver) | Asymmetric partnership where only one party provides audience data | Simplest model; sender shares, receiver activates; common in advertiser-publisher relationships |
>| Bidirectional share | Both parties benefit from sharing audiences with each other | Both organizations act as sender and receiver simultaneously; requires two share configurations; common in co-marketing partnerships |

>[!NOTE]
>
>**Decision: Share refresh cadence**
>
>How often should the shared audience be refreshed with updated segment membership?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| One-time share | Testing the collaboration or for a specific campaign with a fixed audience | Simplest; no ongoing maintenance; audience becomes stale over time |
>| Recurring share (aligned with batch evaluation) | Ongoing partnerships where audience membership changes and needs to be kept current | Requires monitoring of refresh status; most common for production collaborations |

**UI navigation:** Customer > Audiences > Segment Match > Shares > Create share (sender) or Accept share (receiver)

**Key configuration details:**

- Sender selects the segments to share and initiates the share with the configured partner
- Receiver reviews the incoming share details (segment names, estimated size, identity namespaces used)
- Receiver accepts the share to create the matched audience in their sandbox
- Verify the matched audience appears in the receiver's audience list with the expected population
- Confirm that the matched audience is labeled appropriately for governance tracking

**Where options diverge:**

**For Option A (Direct Segment Share):**
Execute a single share with your partner. Monitor the share status and verify the matched audience on the receiver side.

**For Option B (Multi-Partner Distribution):**
Execute shares for each partner independently. Track share status across all partnerships. Consider staggering share initiation to manage processing load.

**For Option C (Cross-Sandbox Federation):**
Execute the cross-sandbox share. The matched audience appears in the receiving sandbox's audience list. Verify that the receiving sandbox has the necessary destination configurations for downstream activation.

**Experience League documentation:**

- [Segment Match overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Segment Match troubleshooting](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Phase 5: Activate matched audiences

**Application function:** [!DNL Real-Time CDP]: Destination Configuration, [!DNL Real-Time CDP]: Audience Activation

This phase activates the matched audience (on the receiver side) to external destinations for targeting, suppression, or downstream use. The matched audience is treated like any other audience in the receiver's sandbox and can be activated through the standard destination activation workflow.

**Decision points in this phase:**

>[!NOTE]
>
>**Decision: Destination type for matched audience**
>
>Where should the matched audience be activated?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Advertising destinations (Google, Meta, Trade Desk) | Using matched audiences for ad targeting or suppression | Requires destination connection and authentication; subject to destination-specific rate limits and format requirements |
>| Cloud storage destinations (S3, Azure, GCS) | Exporting matched audiences as files for use in external systems | Supports file format customization; batch export schedule required; flexible for downstream processing |
>| CRM / marketing automation destinations | Enriching CRM records or triggering automated marketing workflows with matched audience data | Requires field mapping to CRM schema; useful for sales-marketing alignment |
>| Personalization destinations (web, app) | Using matched audience membership for on-site personalization | Requires edge evaluation of the matched audience or streaming activation; latency varies by destination |

>[!NOTE]
>
>**Decision: Activation schedule**
>
>How frequently should the matched audience be exported to the destination?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Daily incremental export | Standard activation with regular audience updates | Only exports changed profiles; lower data volume; most common for ongoing campaigns |
>| Daily full export | Destinations that require a complete audience file each time | Higher data volume; ensures destination has complete audience state; some destinations require full exports |
>| On-demand activation | Ad-hoc campaign launches or time-sensitive activations | Manual trigger; bypasses scheduled cadence; available for batch destinations only |

**UI navigation:** Connections > Destinations > Catalog (for destination setup) or Browse > Select destination > Activate audiences (for activation)

**Key configuration details:**

- Configure the destination connection with appropriate authentication credentials
- Map profile attributes from the matched audience to destination fields (identity fields, profile attributes, segment membership)
- Configure the export schedule (incremental vs. full, daily vs. custom)
- Monitor the activation dataflow to confirm matched audience profiles are exported successfully
- Verify activation metrics (profiles exported, records failed) in the destination monitoring view

**Where options diverge:**

**For Option A (Direct Segment Share):**
The receiver activates the matched audience through their standard destination workflow. No special configuration is needed beyond normal destination activation.

**For Option B (Multi-Partner Distribution):**
Each receiver organization activates matched audiences independently through their own destinations. The sender has no visibility into receiver-side activation.

**For Option C (Cross-Sandbox Federation):**
The receiving sandbox must have its own destination configurations. Destinations cannot be shared across sandboxes. Ensure the receiving sandbox has the necessary destination connections established.

**Experience League documentation:**

- [Destinations overview](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Destinations catalog](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Monitor dataflows for destinations](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Activation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

## Implementation considerations

Review the following considerations before and during implementation to avoid common issues and optimize your audience collaboration.

### Guardrails and limits

- [!DNL Segment Match] uses hashed identifiers for matching -- no PII crosses organizational boundaries. See [Segment Match overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview).
- Only batch-evaluated audiences can be shared via [!DNL Segment Match]. Streaming and edge-evaluated segments must be converted to batch evaluation before sharing.
- Maximum of 4,000 segment definitions per sandbox applies to both source and received segments. See [Segmentation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails).
- Overlap estimation accuracy depends on the volume of matched identifiers. Small audiences may show less precise estimates.
- Activation guardrails apply to matched audiences the same as any other audience -- maximum of 100 dataflows per destination. See [Activation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails).
- Composed audiences are evaluated on a batch schedule and are limited to 10 composition canvases per sandbox. See [Audience Composition guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails).

### Common pitfalls

- **Inconsistent identity hashing between sender and receiver:** If both organizations hash email addresses but use different hashing algorithms, normalization rules, or salt values, match rates will be near zero. Both sides must agree on the exact hashing specification (e.g., SHA-256 on lowercased, trimmed email) before establishing the connection.
- **Sharing audiences without governance review:** Initiating a segment share without evaluating data usage policies can lead to compliance violations. Always run governance policy evaluation against the "Export to Third Party" marketing action before sharing segments with external organizations.
- **Low match rates due to identity coverage gaps:** If the sender's audience is primarily identified by ECID (anonymous cookie) but the matching namespace is hashed email, the match rate will be very low because anonymous profiles do not have email addresses. Verify that source audiences have sufficient coverage of the configured matching identity namespace.
- **Forgetting to accept the share on the receiver side:** The shared audience does not appear in the receiver's audience list until the share is explicitly accepted. Coordinate with the receiver to ensure timely acceptance, especially for time-sensitive campaigns.
- **Stale matched audiences due to evaluation schedule misalignment:** If the sender's source audience evaluates daily but the [!DNL Segment Match] refresh runs weekly, the matched audience on the receiver side may not reflect the latest membership. Align evaluation and share refresh cadences.

### Best practices

- Establish a formal data sharing agreement between organizations before configuring [!DNL Segment Match]. This should cover permitted use cases, data governance requirements, consent obligations, and termination procedures.
- Use overlap estimation as a validation tool before every major campaign -- run estimation before committing to ensure the matched audience meets minimum size and quality thresholds.
- Apply descriptive naming conventions to shared segments that include the partner name, use case, and date (e.g., "PartnerX_HighValue_Suppression_2026Q1") to maintain clarity across organizations.
- Monitor match rates over time. Declining match rates may indicate identity coverage degradation, data quality issues, or changes in the partner's customer base.
- Segment source audiences to exclude profiles without the matching identity namespace populated. This improves match rate percentages and provides more accurate overlap estimates.
- For bidirectional sharing partnerships, designate clear ownership of segment maintenance and refresh schedules to avoid confusion about which organization is responsible for updates.

### Trade-off decisions

>[!NOTE]
>
>**Trade-off: Match rate vs. privacy control**
>
>Using more identity namespaces (hashed email, hashed phone, device IDs) for matching increases match rates but broadens the surface area for potential re-identification. Using fewer namespaces (hashed email only) provides stronger privacy protection but may reduce the matched audience size.
>
>- **Multiple namespaces favor:** Higher match rates, larger matched audiences, more valuable for campaign targeting
>- **Single namespace favors:** Stronger privacy posture, simpler governance review, lower compliance risk
>- **Recommendation:** Start with a single namespace (hashed email is the most common) and add additional namespaces only if match rates are insufficient for the use case. Document the privacy impact assessment for each namespace added.

>[!NOTE]
>
>**Trade-off: Segment granularity vs. operational simplicity**
>
>Sharing many granular, highly targeted segments with a partner provides more flexibility for campaign targeting but increases operational complexity for both sender and receiver. Sharing fewer, broader segments simplifies management but reduces targeting precision.
>
>- **Granular segments favor:** Precise targeting, differentiated campaigns, higher relevance
>- **Broad segments favor:** Simpler management, fewer shares to monitor, lower operational overhead
>- **Recommendation:** Start with a small number of high-value segments (2-5) for a new partnership. Increase granularity as the partnership matures and operational processes are established. Use naming conventions and documentation to manage complexity as segment count grows.

>[!NOTE]
>
>**Trade-off: Refresh frequency vs. processing cost**
>
>Refreshing shared audiences more frequently keeps the matched audience current but increases processing load and may consume more license capacity. Less frequent refreshes reduce cost but allow the matched audience to become stale.
>
>- **Frequent refresh favors:** Current audience membership, higher campaign relevance, better suppression accuracy
>- **Infrequent refresh favors:** Lower processing cost, simpler monitoring, reduced license consumption
>- **Recommendation:** Daily refresh is appropriate for most production collaborations. For time-sensitive use cases (e.g., flash sales, event-based campaigns), consider on-demand re-evaluation and sharing immediately before the campaign launches.

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
