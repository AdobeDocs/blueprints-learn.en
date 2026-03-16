---
title: B2B Audience Activation
description: Learn how to activate account-based B2B audiences across web, email, and advertising channels.
solution: Real-Time Customer Data Platform
exl-id: 2b979159-37aa-41d4-a6b4-1105538f6546
---
# B2B audience activation

This guide provides a comprehensive implementation reference for activating account-based B2B audiences using [!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B Edition. It is designed for solution architects, marketing technologists, and implementation engineers who need to build, evaluate, and activate account-level audiences across web, email, advertising, and CRM channels.

It covers the full lifecycle from account profile unification through audience evaluation and activation to B2B-specific destinations such as [!DNL Marketo Engage], [!DNL LinkedIn], and CRM systems. All viable implementation approaches are presented with trade-offs and decision guidance to help you select the right path for your organization.

## Use case overview

B2B marketing teams need to target and activate audiences at the account level rather than the individual person level. Unlike B2C audience activation where the unit of targeting is a single consumer profile, B2B audience activation requires understanding the relationship between people and the accounts they belong to, evaluating audience membership based on account-level attributes combined with person-level engagement signals, and delivering those audiences to destinations that support account-based targeting.

[!DNL RT-CDP] B2B Edition extends the standard [!DNL Real-Time Customer Data Platform] with specialized XDM classes for accounts, opportunities, and campaigns, along with B2B identity resolution that maps person-to-account relationships. This enables marketers to build account audiences that combine firmographic data (industry, revenue, employee count), technographic data (technology stack, product usage), and behavioral data (web visits, email engagement, event attendance) from the people associated with those accounts.

The activated account audiences power use cases across the demand generation funnel: top-of-funnel awareness campaigns on [!DNL LinkedIn] and display advertising, mid-funnel nurture programs in [!DNL Marketo Engage], and bottom-funnel sales enablement through CRM integration. Account suppression audiences prevent wasted spend by excluding existing customers, closed-lost accounts, or accounts already in active sales cycles.

## Key business objectives

The following business objectives are supported by this use case pattern.

### Increase lead generation

Generate more qualified leads for the sales pipeline through forms, events, content, and multi-channel engagement.

**KPIs:** Prospects, Cost Per Lead, Lead Conversion

[Learn more about increasing lead generation](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### Improve lead qualification & conversion

Increase lead quality and accelerate pipeline progression through scoring, nurturing, and personalized follow-up.

**KPIs:** Lead Conversion, Prospect/Lead Conversion, Efficiency

[Learn more about improving lead qualification & conversion](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### Acquire new customers

Expand the customer base through targeted acquisition campaigns, lookalike audiences, and paid media optimization.

**KPIs:** New Customers, Customer Acquisition Cost, Prospect/Lead Conversion

[Learn more about acquiring new customers](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Optimize marketing spend & ROI

Improve return on marketing investment through better targeting, attribution, audience suppression, and budget allocation.

**KPIs:** Cost Savings, Customer Acquisition Cost, Incremental Revenue

## Example tactical use cases

The following scenarios illustrate how this pattern can be applied in practice.

- **Account-based advertising on [!DNL LinkedIn]** -- Target accounts matching your ideal customer profile (ICP) with sponsored content and InMail campaigns on [!DNL LinkedIn], using account lists activated from [!DNL RT-CDP] B2B Edition
- **[!DNL Marketo Engage] nurture program targeting** -- Activate account audiences to [!DNL Marketo Engage] to enroll associated leads and contacts into targeted nurture streams based on account-level qualification criteria
- **CRM account list synchronization** -- Push qualified account lists to [!DNL Salesforce] or [!DNL Microsoft Dynamics] for sales team visibility, territory assignment, and outbound prospecting workflows
- **Account suppression for paid media** -- Suppress existing customers, closed-won accounts, or accounts in active sales cycles from paid acquisition campaigns to reduce wasted spend
- **Intent-based account targeting** -- Combine third-party intent signals with first-party engagement data at the account level to identify and activate audiences of in-market accounts
- **Product cross-sell to existing accounts** -- Build audiences of accounts using one product line but not another, then activate to email and advertising channels for cross-sell campaigns
- **Event and webinar targeting** -- Activate account audiences to advertising and email channels to drive event registration from target accounts
- **Competitive displacement campaigns** -- Target accounts using competitor products with tailored messaging activated through advertising and email channels
- **Tiered account engagement** -- Segment accounts into engagement tiers (high, medium, low) based on aggregated person-level activity and activate differentiated campaigns for each tier
- **Partner co-marketing audiences** -- Share account audience segments with channel partners or co-marketing programs through cloud storage destinations

## Key performance indicators

The following KPIs help measure the success of this use case pattern.

| KPI | Description | Measurement approach |
| --- | --- | --- |
| Account Reach | Number of target accounts reached across activation channels | Track unique accounts activated per destination |
| Account Engagement Rate | Percentage of activated accounts showing engagement signals | Measure person-level engagement aggregated to account |
| Pipeline Influence | Revenue pipeline attributed to account-based activation campaigns | Track opportunities created from activated account audiences |
| Cost Per Engaged Account | Marketing spend divided by the number of accounts showing engagement | Calculate across advertising and email channel costs |
| Lead Conversion Rate | Percentage of leads from activated accounts that convert to opportunities | Track lead-to-opportunity conversion for activated audiences |
| Audience Suppression Savings | Cost avoided by suppressing ineligible accounts from paid campaigns | Measure spend reduction from suppression audiences |
| Account Coverage | Percentage of total addressable market (TAM) covered by activated audiences | Compare activated accounts against total ICP universe |

## Use case pattern

**B2B audience activation**

Activate account-based B2B audiences across web, email, and advertising channels.

**Function chain:** Account Profile Enrichment > Account Audience Evaluation > Destination Configuration > Audience Activation > Monitoring

## Applications

The following applications are used to implement this use case pattern.

- **[!DNL Real-Time CDP] B2B Edition** -- Core platform for account profile unification, B2B identity resolution, account audience evaluation, B2B-specific destination configuration, and account audience activation
- **[!DNL Adobe Experience Platform] (AEP)** -- Foundational infrastructure for B2B XDM data modeling, data ingestion from CRM and marketing automation sources, identity service, and governance
- **[!DNL Marketo Engage]** -- Primary B2B marketing automation destination for lead nurture programs, scoring, and campaign execution fed by activated account audiences

## Foundational functions

The following foundational capabilities must be in place for this use case pattern. For each function, the status indicates whether it is typically required, assumed to be pre-configured, or not applicable.

| Foundational function | Status | What must be in place | Experience League reference |
| --- | --- | --- | --- |
| Administration & Governance | Required | Sandbox provisioned with [!DNL RT-CDP] B2B Edition enabled. Roles configured for B2B data management, audience creation, and destination activation. ABAC policies in place if account data contains restricted fields. | [Sandboxes overview](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Access control overview](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Data Modeling & Preparation | Required | B2B XDM schemas configured using XDM Business Account, XDM Business Opportunity, XDM Business Campaign, and XDM Individual Profile classes. B2B field groups applied for account attributes, person-account relationships, and opportunity data. Datasets created and Profile-enabled for each B2B entity. Schema relationships defined between account, person, opportunity, and campaign entities. | [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [B2B schemas in Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b) |
| Data Sources & Collection | Required | Source connectors configured for CRM ([!DNL Salesforce], [!DNL Microsoft Dynamics]) and marketing automation ([!DNL Marketo Engage]) to ingest account, person, opportunity, and campaign data. Batch or streaming ingestion pipelines active. Data Prep mappings configured to transform source data to B2B XDM schemas. | [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home), [Marketo Engage connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| Identity & Profile Configuration | Required | B2B identity namespaces configured for account identifiers (Account ID, CRM Account ID) and person identifiers (Email, CRM Contact ID, Marketo Lead ID). Person-to-account relationships resolved through B2B identity resolution. Merge policies configured for account profile unification. | [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [B2B edition of Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b) |
| Audience Definition & Segmentation | Required | Account-level audience definitions created using account attributes, person attributes, and activity data. Evaluation schedules configured for account audiences. Suppression audiences defined for excluding ineligible accounts. | [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences) |

## Supporting functions

The following capabilities augment this use case pattern but are not required for core execution.

| Supporting function | Status | Why it matters | Experience League reference |
| --- | --- | --- | --- |
| Computed / Derived Attribute Creation | Recommended | Aggregated engagement scores, lifetime value, and activity metrics at the account level improve audience precision. Computed attributes can roll up person-level events (email opens, web visits, content downloads) to the account level for use in segmentation. | [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Recommended | B2B data retention policies ensure stale account and opportunity data is cleaned up. Consent management for B2B contacts ensures compliance with email marketing regulations. Dataset expiration policies prevent accumulation of outdated CRM sync data. | [Advanced Data Lifecycle Management overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Data Usage Labeling & Enforcement | Included | B2B account data often contains contractual restrictions (revenue figures, employee counts from third-party providers). Data usage labels prevent restricted account attributes from being activated to unauthorized destinations. Governance policies ensure PII fields from contact records are handled appropriately during activation. | [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Monitoring & Observability | Included | Monitoring CRM and [!DNL Marketo Engage] source connector dataflows ensures account data stays current. Destination activation monitoring confirms audiences are successfully delivered to [!DNL LinkedIn], [!DNL Marketo], and CRM targets. Alert rules catch ingestion failures that would cause stale account data. | [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [Monitor destination dataflows](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations) |
| Reporting & Analysis | Recommended | [!DNL CJA] B2B Edition provides account-level analytics including audience reach, engagement, and pipeline influence. Account-based attribution helps measure the impact of activation campaigns on opportunity progression and revenue. | [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Application functions

This plan exercises the following functions from the Application Function Catalog. Functions are mapped to implementation phases rather than numbered steps.

### [!DNL Real-Time CDP] B2B Edition ([!DNL RT-CDP] B2B)

| Function | Implementation phase | Description |
| --- | --- | --- |
| Account Profile Unification | Phase 1: Account Profile Enrichment | Consolidate account data from CRM, marketing automation, and third-party sources into unified account profiles using B2B XDM schema classes |
| B2B Identity Resolution | Phase 1: Account Profile Enrichment | Resolve person-to-account relationships using primary identifiers, mapping contacts and leads to their associated accounts |
| Account Audience Evaluation | Phase 2: Account Audience Evaluation | Evaluate account-level segment membership by combining account attributes, person attributes, and person activity data |
| Account Destination Configuration | Phase 3: Destination Configuration | Configure connections to B2B-specific destinations ([!DNL Marketo Engage], [!DNL LinkedIn], CRM, cloud storage) with account-level field mapping |
| Account Audience Activation | Phase 4: Audience Activation | Publish account-based audiences to configured destinations for targeting, suppression, or CRM synchronization |
| [!DNL Marketo Engage] Integration | Phase 3: Destination Configuration | Configure bidirectional data flow with [!DNL Marketo Engage] using native B2B source and destination connectors |
| B2B Data Governance | Phase 5: Governance & Monitoring | Enforce data usage policies and consent across B2B account data activation to prevent unauthorized data exposure |

### [!DNL Real-Time CDP] ([!DNL RT-CDP]) -- standard functions

| Function | Implementation phase | Description |
| --- | --- | --- |
| Audience Evaluation | Phase 2: Account Audience Evaluation | Underlying evaluation engine for account audiences, supporting batch evaluation of account-level segment definitions |
| Destination Configuration | Phase 3: Destination Configuration | Core destination connection infrastructure used by B2B-specific destination configuration |
| Audience Activation | Phase 4: Audience Activation | Core activation dataflow infrastructure used by account audience activation |
| Consent & Governance Enforcement | Phase 5: Governance & Monitoring | Enforce consent preferences and data usage policies at activation time |

## Prerequisites

Complete the following before starting implementation.

- [ ] [!DNL RT-CDP] B2B Edition license provisioned and activated on the organization
- [ ] CRM system ([!DNL Salesforce] or [!DNL Microsoft Dynamics]) accessible with API credentials for source connector configuration
- [ ] [!DNL Marketo Engage] instance provisioned with API access (Munchkin ID, Client ID, Client Secret) if using [!DNL Marketo] as a destination
- [ ] [!DNL LinkedIn] Campaign Manager account with matched audiences capability if using [!DNL LinkedIn] as a destination
- [ ] B2B XDM schemas created with account, person, opportunity, and campaign classes (F2)
- [ ] Source connectors configured and actively ingesting CRM and marketing automation data (F3)
- [ ] Person-to-account identity relationships resolved and account profiles unified (F4)
- [ ] Account naming conventions and taxonomy agreed upon for audience definitions
- [ ] Data governance policies defined for account-level data sensitivity classifications

## Implementation options

The following options describe different approaches for implementing this use case pattern. Review each option and select the one that best fits your requirements.

### Option A: Streaming audience activation to [!DNL Marketo Engage]

**Best for:** Organizations using [!DNL Marketo Engage] as their primary B2B marketing automation platform, needing near-real-time audience membership updates to trigger nurture programs, update lead scores, or modify campaign membership as accounts qualify or disqualify.

**How it works:**

This option uses the native [!DNL Marketo Engage] destination connector in [!DNL RT-CDP] to stream account audience membership changes directly to [!DNL Marketo Engage]. When an account qualifies for or exits an audience segment, the associated leads and contacts in [!DNL Marketo] are updated with segment membership attributes. [!DNL Marketo] smart campaigns can then trigger based on these membership changes.

The [!DNL Marketo Engage] destination is a streaming destination, meaning audience membership changes are sent incrementally as they occur rather than in scheduled batches. This provides faster time-to-action for campaigns that need to respond to account qualification changes. Field mappings connect [!DNL RT-CDP] profile attributes to [!DNL Marketo] lead/contact fields, enabling enrichment of [!DNL Marketo] records with account-level data from [!DNL RT-CDP].

**Key considerations:**

- Requires active [!DNL Marketo Engage] subscription with API access
- Streaming activation sends incremental updates, not full audience snapshots
- Person-level records in [!DNL Marketo] are updated, not account-level records directly
- [!DNL Marketo] smart campaigns must be configured to act on the segment membership field updates

**Advantages:**

- Near-real-time audience membership updates in [!DNL Marketo]
- Native bidirectional connector simplifies integration
- Incremental updates minimize data transfer volume
- [!DNL Marketo] can immediately trigger nurture programs based on audience changes

**Limitations:**

- Limited to [!DNL Marketo Engage] as the activation target
- Streaming evaluation eligibility constraints apply to the underlying audience definitions
- Requires mapping between [!DNL RT-CDP] account audiences and [!DNL Marketo] lead/contact records
- Complex [!DNL Marketo] program logic may be needed to translate person-level updates into account-level actions

**Experience League:**

- [Marketo Engage destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [Activate audiences to the Marketo Engage destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage#activate)

### Option B: Batch audience activation to advertising platforms

**Best for:** Account-based advertising campaigns on [!DNL LinkedIn], display networks, or other advertising platforms where daily audience refreshes are sufficient and the primary goal is account-level reach and awareness rather than real-time response.

**How it works:**

This option activates account audiences to advertising platform destinations ([!DNL LinkedIn] Matched Audiences, [!DNL Google] Customer Match, [!DNL Facebook] Custom Audiences, or [!DNL The Trade Desk]) on a scheduled batch cadence. The activation dataflow exports account audience members with mapped identity fields (typically hashed email addresses of associated contacts) that the advertising platform uses to match against its user base.

For [!DNL LinkedIn] specifically, the [!DNL LinkedIn] Matched Audiences destination accepts company name and domain-based matching in addition to email-based matching, enabling true account-level targeting. Other advertising platforms typically require person-level identifiers (email, phone) from the contacts associated with qualifying accounts.

Batch activation runs on a configurable schedule (daily, every 6 hours, etc.) and exports either full audience snapshots or incremental changes depending on the destination type. This approach is well-suited for sustained awareness campaigns where audience freshness requirements are measured in hours rather than minutes.

**Key considerations:**

- Audience freshness depends on the batch schedule (typically daily)
- Advertising platforms have their own match rate limitations
- [!DNL LinkedIn] supports account-level matching; other platforms require person-level identifiers
- Export file formats and identity requirements vary by destination

**Advantages:**

- Supports multiple advertising platforms simultaneously
- Batch processing handles large audience volumes efficiently
- Account suppression audiences reduce wasted ad spend
- [!DNL LinkedIn] Matched Audiences enables native account-level targeting

**Limitations:**

- Audience updates are not real-time; latency depends on batch schedule
- Match rates vary by platform and available identity fields
- Some platforms do not support true account-level matching, only person-level
- Requires separate destination configuration for each advertising platform

**Experience League:**

- [LinkedIn Matched Audiences destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Google Customer Match destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/advertising/google-customer-match)
- [Destinations catalog](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)

### Option C: File-based activation to cloud storage

**Best for:** Organizations needing maximum flexibility in how account audiences are consumed downstream, including CRM imports, data warehouse enrichment, partner data sharing, or custom integrations where a file-based handoff is preferred.

**How it works:**

This option exports account audiences as CSV, JSON, or Parquet files to cloud storage destinations ([!DNL Amazon S3], [!DNL Azure Blob Storage], [!DNL Google Cloud Storage], SFTP) on a scheduled cadence. The export includes account attributes, person-level fields from associated contacts, and audience membership metadata. Downstream systems consume these files through their own import processes.

File-based activation offers the most control over export format, field selection, and scheduling. It supports both full export (complete audience snapshot each run) and incremental export (only changes since the last run). This approach is commonly used when the target system does not have a native [!DNL RT-CDP] destination connector, or when the organization needs to pre-process or transform the data before loading it into the target system.

**Key considerations:**

- Requires cloud storage infrastructure ([!DNL S3], [!DNL Azure Blob], [!DNL GCS], or SFTP)
- Downstream import processes must be built and maintained
- File format (CSV, JSON, Parquet) must match downstream system requirements
- Export scheduling must align with downstream processing windows

**Advantages:**

- Maximum flexibility in how audience data is consumed
- Supports any downstream system that can read files
- Full control over export format, fields, and scheduling
- Can serve multiple downstream consumers from a single export
- Supports full and incremental export modes

**Limitations:**

- Highest latency of all options (batch only)
- Requires building and maintaining downstream import workflows
- No native integration -- additional development effort required
- File management (cleanup, archival) must be handled separately

**Experience League:**

- [Amazon S3 destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [Azure Blob Storage destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/azure-blob)
- [Activate audiences to batch destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/api/connect-activate-batch-destinations)

### Option D: Streaming activation to CRM systems

**Best for:** Sales-marketing alignment use cases where account qualification changes must be reflected in the CRM ([!DNL Salesforce] or [!DNL Dynamics]) in near-real-time for sales team visibility, territory assignment updates, or automated sales workflows.

**How it works:**

This option uses streaming destination connectors ([!DNL Salesforce] CRM, [!DNL Microsoft Dynamics]) to push account audience membership changes directly to CRM account or contact records. When an account qualifies for or exits an audience, the CRM record is updated with a custom field indicating segment membership. Sales teams can then build CRM reports, views, and alerts based on these fields.

The streaming connector sends incremental updates as audience membership changes occur. Field mappings connect [!DNL RT-CDP] account and person attributes to CRM fields, enabling enrichment of CRM records with unified data from [!DNL RT-CDP]. This approach closes the loop between marketing intelligence (account qualification) and sales execution (CRM workflows).

**Key considerations:**

- Requires CRM API access with appropriate write permissions
- CRM custom fields must be created to receive audience membership data
- Streaming volume must be within CRM API rate limits
- CRM workflow automation must be configured to act on field updates

**Advantages:**

- Near-real-time CRM updates for sales team visibility
- Enables automated CRM workflows triggered by audience changes
- Enriches CRM records with unified account data from [!DNL RT-CDP]
- Supports both account-level and contact-level field updates

**Limitations:**

- CRM API rate limits may throttle high-volume updates
- Requires CRM customization (custom fields, workflows)
- Limited to [!DNL Salesforce] and [!DNL Microsoft Dynamics] as native connectors
- Streaming evaluation constraints apply to underlying audiences

**Experience League:**

- [Salesforce CRM destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Microsoft Dynamics 365 destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)

### Option comparison

The following table compares the key characteristics of each implementation option.

| Criteria | Option A: [!DNL Marketo] Streaming | Option B: Advertising Batch | Option C: Cloud Storage | Option D: CRM Streaming |
| --- | --- | --- | --- | --- |
| Best for | Nurture program activation | Account-based advertising | Flexible downstream integration | Sales-marketing alignment |
| Complexity | Low | Medium | Medium-High | Medium |
| Latency | Near real-time (minutes) | Batch (hours) | Batch (hours) | Near real-time (minutes) |
| Flexibility | Low ([!DNL Marketo] only) | Medium (advertising platforms) | High (any downstream system) | Low (CRM only) |
| Requires | [!DNL Marketo Engage] license | Advertising platform accounts | Cloud storage infrastructure | CRM API access |
| Account-level targeting | Via person records | [!DNL LinkedIn] only (others person-level) | Configurable | Via account/contact records |
| Maintenance effort | Low | Low-Medium | High | Medium |

### Choose the right option

Use the following decision guidance to select the right activation approach:

1. **If your primary goal is B2B lead nurturing and you use [!DNL Marketo Engage]**, choose Option A. The native streaming connector provides the fastest time-to-action for marketing automation workflows.

2. **If your primary goal is account-based awareness and demand generation through advertising**, choose Option B. [!DNL LinkedIn] Matched Audiences provides the strongest account-level targeting. Use other advertising platforms for broader reach.

3. **If you need to feed account audiences to systems without native [!DNL RT-CDP] connectors**, or if you need maximum control over data format and downstream processing, choose Option C. This is also the best choice for partner data sharing or data warehouse enrichment.

4. **If your primary goal is sales enablement and CRM visibility of marketing-qualified accounts**, choose Option D. This closes the marketing-to-sales handoff loop by updating CRM records in near-real-time.

Most B2B organizations will implement multiple options simultaneously -- for example, Option A for nurture programs, Option B for [!DNL LinkedIn] advertising, and Option D for CRM synchronization. These options are not mutually exclusive; the same account audience can be activated to multiple destinations simultaneously.

## Implementation phases

The following phases describe the step-by-step process for implementing this use case pattern.

### Phase 1: Account profile enrichment

This phase establishes unified account profiles by consolidating data from CRM, marketing automation, and third-party sources.

**Application function:** [!DNL RT-CDP] B2B: Account Profile Unification, [!DNL RT-CDP] B2B: B2B Identity Resolution

**What you will configure:** This phase establishes unified account profiles by consolidating data from CRM, marketing automation, and third-party sources. B2B identity resolution maps person-to-account relationships so that person-level engagement data (email opens, web visits, content downloads) can be aggregated and used in account-level audience evaluation. This phase builds on foundational functions F2, F3, and F4 which must already be in place.

**Decision points in this phase:**

>[!NOTE]
>**Decision: Account identifier strategy**
>
>Which identifier serves as the primary account key across systems?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| CRM Account ID (e.g., [!DNL Salesforce] Account ID) | CRM is the system of record for accounts | Most common approach. Ensures alignment between [!DNL RT-CDP] and CRM. Requires all source systems to reference the same CRM Account ID. |
>| Custom Account ID | Multiple CRM instances or a proprietary account master | Requires a mapping layer between source system IDs and the canonical account ID. More flexible but adds complexity. |
>| DUNS number or domain | Third-party data enrichment is the primary account source | Useful when firmographic data providers are the primary source. May require fuzzy matching for domain-based resolution. |

>[!NOTE]
>**Decision: Person-to-account relationship model**
>
>How are people (leads, contacts) associated with accounts?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| One-to-one (each person belongs to one account) | Simple B2B model with clean CRM data | Straightforward resolution. Most common for mid-market B2B. |
>| Many-to-many (people can belong to multiple accounts) | Complex enterprise relationships, consultants, or partner networks | [!DNL RT-CDP] B2B Edition supports this natively. Increases audience complexity but reflects real-world relationships accurately. |

**UI navigation:** Platform > Profiles > Browse (to verify unified account profiles)

**Key configuration details:**

- Verify that B2B XDM schemas (XDM Business Account, XDM Business Person Account) are in place from F2
- Confirm CRM and [!DNL Marketo] source connectors are actively ingesting account and person data from F3
- Validate that person-to-account relationships are resolved in the identity graph from F4
- Review account profile completeness by browsing sample account profiles

**Experience League documentation:**

- [Real-Time CDP B2B Edition overview](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [B2B schemas in Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Marketo Engage connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Salesforce connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/crm/salesforce)

### Phase 2: Account audience evaluation

This phase defines and evaluates account-level audiences using a combination of account attributes, person attributes, and person activity data.

**Application function:** [!DNL RT-CDP] B2B: Account Audience Evaluation, [!DNL RT-CDP]: Audience Evaluation

**What you will configure:** This phase defines and evaluates account-level audiences using a combination of account attributes, person attributes, and person activity data. Account audiences in [!DNL RT-CDP] B2B Edition allow you to segment accounts based on both firmographic characteristics (industry, revenue, employee count) and the engagement behavior of people associated with those accounts.

**Decision points in this phase:**

>[!NOTE]
>**Decision: Audience evaluation method**
>
>How quickly must account audience membership update?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Batch evaluation (daily) | Campaign audiences refreshed on a daily cadence, file-based activations, advertising platform audiences | Most account audiences use batch evaluation. Handles complex multi-entity queries that combine account and person attributes. Sufficient for most B2B use cases where daily refresh is acceptable. |
>| Streaming evaluation | [!DNL Marketo] or CRM activation where near-real-time qualification is needed | Account audiences have limited streaming eligibility. Only simple account attribute conditions qualify for streaming evaluation. Person-level behavioral conditions typically require batch. |

>[!NOTE]
>**Decision: Account audience definition approach**
>
>How will you define the account audience criteria?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Account attributes only | Simple firmographic targeting (industry, revenue, region) | Fastest to implement. Limited to account-level data. Use for broad targeting. |
>| Account + person attributes | Targeting accounts where associated people match specific criteria (job title, department) | More precise targeting. Combines firmographic and demographic data. |
>| Account + person attributes + person activity | Targeting accounts with engaged contacts (email opens, web visits, content downloads) | Most powerful but most complex. Requires behavioral event data from F3. Typically requires batch evaluation. |
>| Audience Composition | Complex audience logic requiring rank, split, exclude, or enrich operations | Use the visual Audience Composition canvas for derived account audiences. Limited to batch evaluation. |

>[!NOTE]
>**Decision: Suppression audience strategy**
>
>Which accounts should be excluded from activation?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Existing customer suppression | Acquisition campaigns targeting net-new accounts | Exclude accounts with active subscriptions or closed-won opportunities |
>| Active sales cycle suppression | Avoid interfering with accounts in active sales engagement | Exclude accounts with open opportunities above a certain stage |
>| Recent engagement suppression | Prevent over-messaging of recently contacted accounts | Exclude accounts engaged within a lookback window (e.g., 30 days) |
>| No suppression | Brand awareness campaigns targeting all qualifying accounts | Use with caution; may result in wasted spend on ineligible accounts |

**UI navigation:** Customer > Audiences > Create audience > Build rule (select Account as the audience type)

**Key configuration details:**

- Select "Account" as the audience type when creating a new audience in Segment Builder
- Account attributes appear under the Account section in Segment Builder (industry, revenue, account status)
- Person attributes and activities can be added through the "People" relationship in the account audience builder
- Configure batch evaluation schedule if one does not already exist for the sandbox
- Create both targeting audiences (accounts to include) and suppression audiences (accounts to exclude)

**Experience League documentation:**

- [Account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Audience Composition](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)

### Phase 3: Destination configuration

This phase establishes authenticated connections to the target destinations where account audiences will be delivered.

**Application function:** [!DNL RT-CDP] B2B: Account Destination Configuration, [!DNL RT-CDP] B2B: [!DNL Marketo Engage] Integration, [!DNL RT-CDP]: Destination Configuration

**What you will configure:** This phase establishes authenticated connections to the target destinations where account audiences will be delivered. Configuration includes selecting the destination from the catalog, providing authentication credentials, configuring account-level and person-level field mappings, and setting the export schedule. Each destination type has unique requirements and capabilities.

**Decision points in this phase:**

>[!NOTE]
>**Decision: Destination selection**
>
>Which destination(s) will receive the activated account audiences?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| [!DNL Marketo Engage] | B2B lead nurture, scoring, and campaign execution | Native streaming connector. Updates lead/contact records. Requires [!DNL Marketo] API credentials (Munchkin ID, Client ID, Client Secret). |
>| [!DNL LinkedIn] Matched Audiences | Account-based advertising on [!DNL LinkedIn] | Supports company name and domain matching for account-level targeting. Batch activation. Requires [!DNL LinkedIn] Campaign Manager access. |
>| [!DNL Salesforce] CRM | Sales enablement and CRM account list synchronization | Streaming connector updates account or contact records. Requires [!DNL Salesforce] API access with write permissions. |
>| [!DNL Microsoft Dynamics 365] | Sales enablement for [!DNL Dynamics]-based organizations | Streaming connector. Requires [!DNL Dynamics 365] API access. |
>| Cloud storage ([!DNL S3], [!DNL Azure Blob], [!DNL GCS], SFTP) | Custom integrations, data warehouse, partner sharing | File-based batch export. Maximum flexibility but requires downstream processing. |
>| [!DNL Google] Customer Match | Search and display advertising targeting | Person-level matching via hashed email. Batch activation. |
>| [!DNL The Trade Desk] | Programmatic display and video advertising | Person-level matching. Batch activation. |

>[!NOTE]
>**Decision: Field mapping strategy**
>
>Which account and person fields should be mapped to the destination?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Identity fields only | Advertising platforms that only need matching identifiers | Minimal data transfer. Destination matches on email or company domain. |
>| Identity + core account attributes | CRM or [!DNL Marketo] where account context improves targeting | Include industry, revenue, employee count, account tier. Enrich downstream records. |
>| Full attribute set | Cloud storage or data warehouse exports | Include all relevant account and person attributes. Largest export payload. |

**UI navigation:** Connections > Destinations > Catalog > Search for destination > Configure

**Key configuration details:**

- Navigate to the Destinations catalog and select the target destination
- Provide authentication credentials specific to the destination type
- Configure field mappings connecting [!DNL RT-CDP] XDM fields to destination fields
- For [!DNL Marketo Engage]: provide Munchkin ID, Client ID, and Client Secret
- For [!DNL LinkedIn]: authorize via OAuth and select the [!DNL LinkedIn] ad account
- For cloud storage: provide bucket/container name, path, file format, and credentials
- For CRM: provide instance URL, API credentials, and target object type (Account or Contact)

**Where options diverge:**

**For Option A ([!DNL Marketo Engage] Streaming):**

Navigate to Destinations > Catalog > Adobe > [!DNL Marketo Engage]. Configure the Munchkin ID and API credentials. Map [!DNL RT-CDP] identity fields (email) and profile attributes to [!DNL Marketo] lead fields. The destination automatically handles incremental streaming updates.

**For Option B (Advertising Platform Batch):**

Navigate to Destinations > Catalog > Advertising/Social > select platform. Authorize via OAuth. Configure the export schedule (recommended: daily). Map hashed email identifiers and any supported matching fields. For [!DNL LinkedIn], additionally map company name and domain fields for account-level matching.

**For Option C (Cloud Storage File-Based):**

Navigate to Destinations > Catalog > Cloud Storage > select provider. Configure bucket/container, file path template, and file format (CSV, JSON, or Parquet). Set the export schedule and choose full or incremental export. Map all desired account and person attribute fields.

**For Option D (CRM Streaming):**

Navigate to Destinations > Catalog > CRM > select [!DNL Salesforce] or [!DNL Dynamics]. Provide API credentials and instance URL. Map [!DNL RT-CDP] fields to CRM account or contact fields. Ensure custom fields exist in the CRM to receive audience membership data.

**Experience League documentation:**

- [Destinations overview](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Destinations catalog](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Marketo Engage destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [LinkedIn Matched Audiences destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Salesforce CRM destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Amazon S3 destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)

### Phase 4: Audience activation

This phase publishes the evaluated account audiences to the configured destinations.

**Application function:** [!DNL RT-CDP] B2B: Account Audience Activation, [!DNL RT-CDP]: Audience Activation

**What you will configure:** This phase publishes the evaluated account audiences to the configured destinations. Activation creates the dataflow connecting the account audience (source) to the external destination (target), applies attribute mappings, and initiates the export according to the configured schedule or streaming behavior. You will also configure suppression audiences to exclude ineligible accounts from activation.

**Decision points in this phase:**

>[!NOTE]
>**Decision: Export type**
>
>Should the activation export full audience snapshots or only incremental changes?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Incremental export | Streaming destinations ([!DNL Marketo], CRM) or batch destinations where downstream systems handle deltas | Smaller data volume per export. Faster processing. Requires downstream systems to manage state. Default for streaming destinations. |
>| Full export | Batch destinations where the downstream system replaces the full audience each run | Larger data volume but simpler downstream logic. Useful when downstream systems do not maintain state. Available for file-based destinations. |

>[!NOTE]
>**Decision: Activation scope**
>
>How many audiences should be activated per destination?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Single audience per dataflow | Simple activation with clear audience-to-destination mapping | Easiest to monitor and troubleshoot. One audience failure does not affect others. |
>| Multiple audiences per dataflow | Multiple related audiences going to the same destination | More efficient use of destination connections. All audiences share the same field mapping and schedule. |

**UI navigation:** Connections > Destinations > Browse > Select destination > Activate audiences

**Key configuration details:**

- Select the target audience(s) from the audience list
- Review and confirm the field mappings configured in Phase 3
- For batch destinations: configure the export schedule (time, frequency)
- For streaming destinations: activation begins immediately after configuration
- Optionally add suppression audiences using the exclude functionality
- Trigger an initial test activation run to validate the dataflow

**Where options diverge:**

**For Option A ([!DNL Marketo Engage] Streaming):**

Select account audiences to activate. Activation begins streaming immediately. Verify in [!DNL Marketo] that lead/contact records are being updated with segment membership fields. Configure [!DNL Marketo] smart campaigns to trigger based on these field changes.

**For Option B (Advertising Platform Batch):**

Select account audiences and configure the daily export schedule. After the first export completes, verify in the advertising platform that the audience appears and has a populated member count. Allow 24-48 hours for the platform to process the initial audience file.

**For Option C (Cloud Storage File-Based):**

Select account audiences and configure the export schedule and file format. After the first export, verify files appear in the target storage location with the expected format and content. Confirm downstream import processes successfully consume the exported files.

**For Option D (CRM Streaming):**

Select account audiences to activate. Activation begins streaming immediately. Verify in the CRM that account or contact records are being updated with the mapped fields. Configure CRM reports, list views, or workflow automation to act on the updated fields.

**Experience League documentation:**

- [Activate audiences to streaming destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Activate audiences to batch destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Activation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- [Destinations overview](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)

### Phase 5: Governance & monitoring

This phase ensures that account audience activation complies with data governance policies and consent preferences, and that ongoing activation dataflows are monitored for health.

**Application function:** [!DNL RT-CDP] B2B: B2B Data Governance, [!DNL RT-CDP]: Consent & Governance Enforcement

**What you will configure:** This phase ensures that account audience activation complies with data governance policies and consent preferences, and that ongoing activation dataflows are monitored for health. B2B data governance enforces restrictions on sensitive account attributes (revenue, employee count from third-party providers), while consent enforcement ensures that person-level communications respect opt-out preferences. Monitoring confirms that activation dataflows are completing successfully.

**Decision points in this phase:**

>[!NOTE]
>**Decision: Governance enforcement level**
>
>How strictly should data governance be enforced for B2B activations?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Full enforcement (block on violation) | Production activations with sensitive data | Prevents any activation that violates governance policies. May require iterative field mapping adjustments to resolve violations. |
>| Warn and proceed | Development or testing environments | Allows activation to proceed but logs warnings. Useful during initial setup to identify potential issues. |

>[!NOTE]
>**Decision: Monitoring approach**
>
>How should activation health be monitored?
>
>| Option | When to choose | Considerations |
>| --- | --- | --- |
>| Alert-based monitoring | Production environments where failures must be caught quickly | Configure alerts for destination activation failures, source flow failures, and dataflow delays. Requires alert subscription setup. |
>| Manual monitoring | Development or low-volume activations | Periodically review dataflow runs in the Destinations UI. Less overhead but risk of delayed failure detection. |
>| Both | Production environments with complex multi-destination activation | Alerts for critical failures plus periodic dashboard review for trends. Recommended for most B2B implementations. |

**UI navigation:** Privacy > Policies (for governance), Connections > Destinations > Browse > Select destination > Dataflow runs (for monitoring)

**Key configuration details:**

- Apply data usage labels to B2B datasets containing restricted attributes
- Verify governance policies are enforced by evaluating the activation against the target marketing action
- Configure alerts for destination activation failures and source connector failures
- Review dataflow run metrics (profiles exported, records failed) after each activation cycle
- Set up license usage dashboard review to track account profile volume against entitlements

**Experience League documentation:**

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Consent and preferences](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Monitor destination dataflows](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Activation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

## Implementation considerations

The following sections provide additional guidance for a successful implementation.

### Guardrails & limits

Review the following platform guardrails and limits that apply to this use case pattern.

- Maximum of 4,000 segment definitions per sandbox, including account audiences -- [Segmentation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Account audiences are primarily evaluated using batch evaluation; streaming eligibility is limited to simple account attribute conditions
- Maximum of 100 dataflows per destination connection -- [Destinations guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- Batch destinations export up to 5 million profiles per file segment
- Streaming destinations have per-second throughput limits set by the destination partner (e.g., [!DNL Marketo] API rate limits)
- Composed audiences (from Audience Composition) are limited to batch evaluation and cannot use streaming
- Maximum of 10 composition blocks per Audience Composition canvas
- [!DNL LinkedIn] Matched Audiences require a minimum audience size (typically 300 members) for activation
- CRM streaming destinations are subject to the CRM provider's API rate limits (e.g., [!DNL Salesforce] bulk API daily limits)
- [!DNL RT-CDP] B2B Edition license governs the total number of business account profiles -- [RT-CDP product description](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

### Common pitfalls

Be aware of the following common issues when implementing this use case pattern.

- **Incomplete person-to-account mapping:** If person records (leads, contacts) are not properly linked to account records through B2B identity resolution, account audiences that depend on person attributes or activities will undercount qualifying accounts. Validate person-to-account relationships in F4 before building account audiences.

- **Stale CRM data causing audience drift:** If CRM source connectors are not running on a regular schedule or are failing silently, account attributes (industry, revenue, status) become stale. This causes audiences to include accounts that no longer qualify or exclude accounts that should qualify. Monitor source connector dataflow health.

- **Advertising platform match rate expectations:** When activating account audiences to advertising platforms other than [!DNL LinkedIn], the match rate depends on having valid person-level identifiers (hashed email) for contacts associated with qualifying accounts. Accounts with no associated contacts that have email addresses will not match. Monitor match rates and consider enriching contact data.

- **[!DNL Marketo] field mapping misalignment:** When streaming to [!DNL Marketo Engage], the [!DNL RT-CDP] field mapping must target existing [!DNL Marketo] lead or contact fields. If the mapped [!DNL Marketo] field does not exist, the update will silently fail. Pre-create all target fields in [!DNL Marketo] before configuring the destination.

- **Governance policy blocking activation:** Data usage labels on account attribute fields (especially third-party firmographic data) may trigger governance violations when activating to advertising destinations. Evaluate governance compliance before activating and adjust field mappings to exclude restricted fields if needed.

- **Account audience combining account and person data with batch-only evaluation:** Account audiences that reference person-level behavioral events (e.g., "accounts where at least one contact opened an email in the last 30 days") require batch evaluation. If the use case expects real-time qualification, this constraint may cause unexpected latency.

### Best practices

Follow these recommendations for optimal results.

- Start with a small number of well-defined account audiences (ICP tier, industry vertical, engagement tier) before expanding to complex multi-attribute definitions
- Create dedicated suppression audiences for existing customers, active opportunities, and recently engaged accounts to avoid wasted spend and channel conflict
- Use Audience Composition to build tiered account audiences (high/medium/low engagement) by ranking accounts on aggregated engagement scores
- Activate the same account audience to multiple destinations simultaneously for coordinated multi-channel campaigns (e.g., [!DNL LinkedIn] for advertising, [!DNL Marketo] for email, CRM for sales visibility)
- Implement a consistent naming convention for account audiences that includes the targeting criteria and intended channel (e.g., "B2B_ICP_Enterprise_Tech_LinkedIn" or "B2B_Suppression_ActiveOpps")
- Schedule batch activation during off-peak hours to minimize impact on downstream systems and align with advertising platform processing windows
- Monitor match rates per destination after the initial activation and iterate on identity field mappings to improve matching
- Maintain bidirectional data flow with [!DNL Marketo Engage]: ingest engagement data from [!DNL Marketo] into [!DNL RT-CDP] (source connector) and activate audiences back to [!DNL Marketo] (destination connector) for a closed-loop system

### Trade-off decisions

Consider the following trade-offs when making implementation decisions.

>[!NOTE]
>**Trade-off: Audience freshness vs. evaluation complexity**
>
>Account audiences that combine account attributes with person-level behavioral data provide the most precise targeting but are limited to batch evaluation (daily refresh). Simpler audiences based on account attributes alone may qualify for streaming evaluation with near-real-time updates.
>
>- **Batch (complex criteria) favors:** Targeting precision, combining firmographic and behavioral signals, comprehensive account scoring
>- **Streaming (simple criteria) favors:** Speed of audience updates, real-time response to account changes, faster time-to-action in [!DNL Marketo] and CRM
>- **Recommendation:** Use batch evaluation for primary targeting audiences where daily refresh is acceptable (most B2B use cases). Reserve streaming evaluation for time-sensitive triggers such as account status changes or high-value account alerts.

>[!NOTE]
>**Trade-off: Centralized activation vs. destination-specific audiences**
>
>You can activate a single unified account audience to multiple destinations, or create destination-specific audiences tailored to each channel's capabilities and requirements.
>
>- **Centralized audience favors:** Consistency across channels, simpler audience management, unified reporting
>- **Destination-specific audiences favors:** Optimized targeting per channel (e.g., [!DNL LinkedIn] benefits from company-level attributes while [!DNL Marketo] needs lead-level details), channel-specific suppression rules
>- **Recommendation:** Start with centralized audiences for consistency, then create destination-specific variants only when channel requirements diverge significantly (e.g., different suppression windows for advertising vs. email).

>[!NOTE]
>**Trade-off: Real-time CRM sync vs. batch CRM updates**
>
>Streaming to CRM provides immediate sales visibility but consumes CRM API quota. Batch file exports are more efficient but introduce latency.
>
>- **Streaming CRM sync favors:** Sales responsiveness, immediate account alerts, real-time pipeline visibility
>- **Batch CRM updates favors:** API quota conservation, bulk update efficiency, alignment with CRM data loading windows
>- **Recommendation:** Use streaming CRM sync for high-priority account qualification changes (e.g., account moves to "Sales Ready" tier). Use batch file exports for bulk updates like monthly account scoring refreshes or territory reassignment lists.

## Related documentation

The following resources provide additional context and detailed guidance for the capabilities used in this use case pattern.

**[!DNL RT-CDP] B2B Edition**

- [Real-Time CDP B2B Edition overview](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [B2B schemas in Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [RT-CDP B2B Edition product description](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

**Audience evaluation & segmentation**

- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Segment Builder UI guide](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Audience Composition](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Streaming segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmentation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

**Destinations & activation**

- [Destinations overview](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Destinations catalog](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Marketo Engage destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [LinkedIn Matched Audiences destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Salesforce CRM destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Microsoft Dynamics 365 destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)
- [Amazon S3 destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [Activate audiences to streaming destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Activate audiences to batch destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Activation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

**Data sources & connectors**

- [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Marketo Engage connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Salesforce connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/crm/salesforce)

**Data modeling & identity**

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Profile overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Merge policies overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

**Data governance & privacy**

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Data usage labels overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview)
- [Consent and preferences](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Monitoring & observability**

- [Alerts overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Monitor destination dataflows](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Monitor source dataflows](https://experienceleague.adobe.com/en/docs/experience-platform/sources/api-tutorials/monitor)
- [License usage dashboard](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Reporting & analytics**

- [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Connections overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Data views overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)

**Tutorials & guides**

- [Getting started with Real-Time CDP B2B Edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro)
- [Create a schema for B2B sources](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Sandbox Tooling](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/sandbox-tooling-api/overview)
