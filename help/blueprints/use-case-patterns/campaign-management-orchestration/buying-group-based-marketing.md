---
title: Buying Group-Based Marketing & Journey Management
description: "Learn how to develop account-level journeys that qualify leads into buying groups to improve B2B marketing effectiveness."
solution: Journey Optimizer, Real-Time Customer Data Platform
---

# Buying group-based marketing & journey management

This guide provides a comprehensive implementation reference for buying group-based marketing and journey management. It is designed for solution architects, marketing technologists, and implementation engineers who need to implement account-level journey orchestration with buying group management using [!DNL Adobe Journey Optimizer B2B Edition] and [!DNL Real-Time CDP B2B Edition].

Use this document to understand what to configure, where implementation choices exist, and what trade-offs drive each decision.

Unlike person-level journey patterns, this pattern operates at the account level, qualifying individual leads into buying groups associated with solution interests, scoring engagement at the buying group level, and orchestrating multi-step account journeys that progress accounts through pipeline stages toward sales readiness.

## Use case overview

B2B organizations face a fundamental challenge: purchase decisions are rarely made by a single individual. Complex B2B purchases involve multiple stakeholders -- decision makers, influencers, champions, budget holders, and technical evaluators -- who collectively form a "buying group." Traditional lead-based marketing treats each person independently, missing the critical signal of whether the right combination of roles within an account is engaged and ready to buy.

Buying group-based marketing and journey management addresses this by shifting the unit of orchestration from individual leads to accounts and buying groups. The pattern enables B2B marketers to define solution interests (the products or services being sold), create buying group templates that specify which roles are needed for a purchase decision, qualify incoming leads against those roles, score engagement at the buying group level, and orchestrate account journeys that respond to buying group completeness and readiness signals.

The desired outcome is improved pipeline quality and velocity: marketing delivers accounts to sales only when the right people within the account are engaged and the buying group is sufficiently complete, reducing wasted sales effort and accelerating deal progression.

## Key business objectives

This use case pattern supports the following business objectives.

### Improve lead qualification & conversion

Increase lead quality and accelerate pipeline progression through scoring, nurturing, and personalized follow-up.

**KPIs:** Lead Conversion, Prospect/Lead Conversion, Efficiency

[Learn more about improving lead qualification & conversion](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### Increase lead generation

Generate more qualified leads for the sales pipeline through forms, events, content, and multi-channel engagement.

**KPIs:** Prospects, Cost Per Lead, Lead Conversion

[Learn more about increasing lead generation](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### Increase revenue & sales

Drive top-line revenue growth through optimized digital channels, campaigns, and customer journeys.

**KPIs:** Revenue growth, pipeline velocity, deal close rate

[Learn more about increasing revenue & sales](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

## Example tactical use cases

The following are specific scenarios where this pattern can be applied.

- **Solution-specific buying group qualification** -- Define buying groups for each product line (for example, "Enterprise CRM," "Data Platform," "Security Suite") with role templates specifying required personas (Economic Buyer, Technical Evaluator, Champion, End User) and qualify leads from the CRM and marketing automation system against those roles.
- **Account journey for pipeline acceleration** -- Orchestrate a multi-step account journey that sends targeted nurture emails to under-engaged roles within a buying group, triggers sales alerts when engagement thresholds are reached, and transitions the account to a sales-ready stage.
- **Buying group completeness campaigns** -- Identify accounts where buying groups have missing roles (for example, no Economic Buyer identified) and launch targeted acquisition campaigns to engage the right personas within those accounts.
- **Cross-sell account journeys** -- After an initial deal closes, create new buying groups for complementary solution interests and orchestrate account journeys that nurture the expanded buying committee.
- **Re-engagement for stalled deals** -- Detect accounts where buying group engagement scores have declined and trigger re-engagement journeys with fresh content, executive outreach, or event invitations.
- **Sales and marketing alignment via CRM insights** -- Surface buying group status, engagement data, and account journey progress directly within [!DNL Salesforce] or [!DNL Dynamics 365] so sales representatives have real-time visibility into marketing-qualified accounts.
- **Event-driven buying group updates** -- Automatically update buying group membership and engagement scores when leads attend webinars, download whitepapers, visit pricing pages, or request demos.
- **Multi-region account coordination** -- Manage buying groups across global accounts where different regional contacts hold different roles, unifying engagement scoring across geographies.

## Key performance indicators

The following KPIs help measure the effectiveness of this use case pattern.

| KPI | Description | Measurement approach |
| --- | --- | --- |
| Buying Group Completeness Rate | Percentage of buying groups with all required roles filled | [!DNL AJO B2B] Analytics Dashboards: track role coverage per buying group |
| Buying Group Engagement Score | Aggregate engagement score across all members of a buying group | [!DNL AJO B2B] Engagement Scoring: person-level scores rolled up to buying group |
| Marketing Qualified Account (MQA) Rate | Percentage of accounts that reach the marketing-qualified threshold | Account journey exit criteria: accounts transitioning to sales-ready stage |
| Pipeline Velocity | Average time from buying group creation to sales-qualified opportunity | CRM integration: track stage transitions from [!DNL AJO B2B] to CRM pipeline |
| Lead-to-Buying Group Qualification Rate | Percentage of leads successfully qualified into buying group roles | [!DNL AJO B2B] Buying Group Management: qualified vs. unqualified lead ratio |
| Sales Alert Response Rate | Percentage of sales alerts that result in sales follow-up activity | CRM Sales Insights: track alert-to-activity conversion |
| Account Journey Completion Rate | Percentage of accounts that complete the intended journey path | [!DNL AJO B2B] Analytics Dashboards: journey completion metrics |
| Email Engagement Rate (B2B) | Open and click-through rates for B2B nurture emails | [!DNL AJO B2B] reporting: email delivery and engagement metrics |

## Use case pattern

**Buying group-based marketing & journey management**

Develop account-level journeys that qualify leads into buying groups to improve B2B marketing effectiveness.

**Function chain:** Account Identification > Buying Group Definition > Lead Qualification > Account Journey Execution > Engagement Scoring > Reporting

## Applications

The following Adobe applications are used in this use case pattern.

- **[!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])** -- Orchestrates account-level journeys, manages buying groups with role templates and solution interests, scores engagement at the person and buying group level, authors B2B email content, sends SMS messages, configures sales alerts, and provides B2B analytics dashboards.
- **[!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])** -- Unifies account profiles from cross-source B2B data, resolves person-to-account relationships, evaluates account-level audiences, configures B2B-specific destinations ([!DNL Marketo Engage], [!DNL LinkedIn], CRM), and enforces data governance across B2B data.

## Foundational functions

The following foundational capabilities must be in place for this use case pattern. For each function, the status indicates whether it is typically required, assumed to be pre-configured, or not applicable.

| Foundational function | Status | What must be in place | Experience League reference |
| --- | --- | --- | --- |
| Administration & Governance | Required | Sandbox provisioned with [!DNL AJO B2B Edition] and [!DNL RT-CDP B2B Edition] entitlements enabled. Roles configured for B2B marketers, sales operations, and administrators with appropriate permissions for buying group management, account journeys, and CRM integration settings. | [Sandboxes overview](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [Access control overview](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Data Modeling & Preparation | Required | B2B XDM schemas configured using B2B-specific classes: XDM Business Account, XDM Business Opportunity, XDM Business Person (lead/contact), XDM Business Campaign, and XDM Business Marketing List. Field groups for account attributes, person attributes, and activity/engagement data must be in place. Datasets created and Profile-enabled for each schema. | [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [B2B schema classes](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Data Sources & Collection | Required | B2B data ingestion pipelines established, typically via the [!DNL Marketo Engage] source connector or [!DNL Salesforce]/[!DNL Dynamics] CRM source connectors. Account, person, opportunity, campaign, and campaign member data must flow into AEP datasets. Behavioral engagement data (web visits, email interactions, content downloads) must also be ingested for engagement scoring. | [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home), [Marketo Engage connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| Identity & Profile Configuration | Required | B2B identity resolution configured to resolve person-to-account relationships. Identity namespaces for B2B identifiers ([!DNL Marketo] Person ID, [!DNL Salesforce] Lead/Contact ID, Account ID) must exist. Merge policies configured for B2B profile unification. Account profiles must be unified from cross-source data. | [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [B2B Identity Resolution](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) |
| Audience Definition & Segmentation | Required | Account-level audience definitions created using account attributes, person attributes, and activity data. Account audiences identify which accounts enter buying group journeys. Batch evaluation is typically sufficient for B2B account journeys, though streaming evaluation can be used for real-time account qualification triggers. | [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences) |

## Supporting functions

The following capabilities augment this use case pattern but are not required for core execution.

| Supporting function | Status | Why it matters | Experience League reference |
| --- | --- | --- | --- |
| Computed / Derived Attribute Creation | Recommended | Computed attributes can aggregate person-level engagement events (email opens, content downloads, webinar attendance) into account-level engagement metrics that feed buying group scoring and account qualification logic. | [Computed attributes overview](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Recommended | Consent management is critical for B2B email and SMS communications. Dataset expiration policies help manage the lifecycle of transient engagement data and ensure compliance with data retention requirements. | [Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Data Usage Labeling & Enforcement | Recommended | B2B data often contains sensitive company information and personal data of business contacts. Data governance policies ensure compliant use of B2B data across destinations, particularly when activating to advertising platforms or third-party systems. | [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Monitoring & Observability | Recommended | Monitoring ensures B2B data pipelines (CRM/[!DNL Marketo] syncs) are healthy, account profiles are updating, and account journey executions are proceeding without failures. Alerts on source dataflow failures are critical for maintaining data currency. | [Observability Insights overview](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting & Analysis | Included | B2B analytics dashboards within [!DNL AJO B2B Edition] provide buying group engagement, account journey performance, and pipeline metrics. [!DNL CJA B2B Edition] extends analysis with account-level workspace analysis, buying group analysis, and opportunity correlation. | [CJA overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Application functions

This plan exercises the following functions from the application function catalog. Functions are mapped to implementation phases rather than numbered steps.

### [!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])

| Function | Implementation phase | Description |
| --- | --- | --- |
| Solution Interest Configuration | Phase 1: Solution Interest & Buying Group Setup | Define solution interests that map products or services to buying group qualification criteria |
| Buying Group Management | Phase 1: Solution Interest & Buying Group Setup | Create and manage buying groups with role templates, persona mapping, and solution interest definitions |
| Account Journey Orchestration | Phase 3: Account Journey Design & Execution | Design and manage multi-step account journeys with conditions, actions, and engagement-based branching |
| Engagement Scoring | Phase 2: Lead Qualification & Engagement Scoring | Score person-level engagement within buying groups to measure buying group completeness and readiness |
| Account Qualification | Phase 2: Lead Qualification & Engagement Scoring | Use AI-powered account qualification agents to assess account readiness and pipeline quality |
| B2B Email Authoring | Phase 3: Account Journey Design & Execution | Create B2B email content with templates, visual fragments, brand themes, and AI-assisted content generation |
| SMS Channel Management | Phase 3: Account Journey Design & Execution | Configure and manage SMS communications within B2B account journeys |
| Sales Alert Configuration | Phase 4: Sales Alignment & CRM Integration | Configure sales alert emails to notify sales teams of account engagement milestones and buying signals |
| CRM Sales Insights | Phase 4: Sales Alignment & CRM Integration | Provide in-CRM visibility ([!DNL Salesforce], [!DNL Dynamics]) for buying group status, engagement data, and account journey progress |
| B2B Analytics Dashboards | Phase 5: Reporting & Optimization | Monitor account journey performance, buying group engagement, and pipeline metrics via intelligent and engagement dashboards |

### [!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])

| Function | Implementation phase | Description |
| --- | --- | --- |
| Account Profile Unification | Phase 0: B2B Data Foundation | Consolidate cross-source B2B data into unified account profiles using specialized XDM B2B schema classes and field groups |
| B2B Identity Resolution | Phase 0: B2B Data Foundation | Resolve person-to-account relationships using primary identifiers, supporting multi-level account hierarchies and many-to-many person-to-account mappings |
| Account Audience Evaluation | Phase 0: B2B Data Foundation | Evaluate account-level segment membership combining account attributes, person attributes, and activity data |
| Account Destination Configuration | Phase 4: Sales Alignment & CRM Integration | Configure connections to B2B-specific destinations ([!DNL Marketo Engage], [!DNL LinkedIn], CRM systems) with account-level field mapping |
| Account Audience Activation | Phase 4: Sales Alignment & CRM Integration | Publish account-based audiences to destinations for account-based targeting and suppression |
| [!DNL Marketo Engage] Integration | Phase 0: B2B Data Foundation | Ingest and activate data bidirectionally with [!DNL Marketo Engage] using native B2B source and destination connectors |
| B2B Data Governance | Phase 0: B2B Data Foundation | Enforce data usage policies and consent across B2B account data centralization and activation processes |

## Prerequisites

Complete the following before beginning implementation.

- [!DNL AJO B2B Edition] license provisioned and enabled on the target sandbox
- [!DNL RT-CDP B2B Edition] license provisioned and enabled on the target sandbox
- CRM system ([!DNL Salesforce] or [!DNL Microsoft Dynamics 365]) accessible with appropriate API credentials for bidirectional data sync
- [!DNL Marketo Engage] instance connected (if using [!DNL Marketo] as the marketing automation platform) with source connector configured
- B2B XDM schemas deployed: Account, Person, Opportunity, Campaign, and Campaign Member classes with required field groups
- Account and person data ingested into AEP with person-to-account relationships resolved
- Email channel configured: subdomain delegated, IP pool warmed, and channel surface created for B2B email sending
- SMS provider configured (if SMS channel is used in account journeys): [!DNL Sinch], [!DNL Twilio], or [!DNL Infobip] credentials provisioned
- Sales team onboarded to CRM Sales Insights component ([!DNL Salesforce] AppExchange package or [!DNL Dynamics] solution installed)
- Content assets prepared: B2B email templates, brand themes, and visual fragments for nurture and sales alert emails
- Solution interest taxonomy defined: list of products/services that will have associated buying groups
- Buying group role templates designed: personas and roles required for each solution interest (for example, Economic Buyer, Technical Evaluator, Champion)

## Implementation options

This section describes the available implementation approaches, each tailored to different organizational needs and maturity levels.

### Option A: Single solution interest with linear account journey

**Best for:** Organizations new to buying group management who want to start with a single product line or solution offering, validate the approach, and iterate before scaling to multiple solution interests.

**How it works:**

This approach focuses on a single solution interest (one product or service) with one buying group template. A linear account journey is designed with sequential stages: account identification, buying group formation, nurture engagement, engagement scoring threshold, and sales handoff. The journey follows a straightforward path without complex branching or parallel tracks.

Leads are qualified into buying group roles as they are ingested from the CRM or [!DNL Marketo Engage]. The account journey sends nurture emails to under-engaged roles, monitors engagement scores, and triggers a sales alert when the buying group reaches a defined completeness and engagement threshold. This approach provides a clear, measurable proof of concept before introducing complexity.

**Key considerations:**

- Simpler to implement and validate, making it suitable for a first deployment
- Limited to one product/service buying motion at a time
- Linear journey structure may not accommodate complex multi-stage buying cycles

**Advantages:**

- Fastest time to value with minimal configuration complexity
- Clear success metrics tied to a single solution interest
- Easier to explain and gain organizational buy-in
- Straightforward reporting and KPI measurement

**Limitations:**

- Does not address cross-sell or multi-product scenarios
- Accounts interested in multiple solutions require separate, uncoordinated journeys
- May not fully leverage the buying group management capabilities

**Experience League:**

- [AJO B2B Edition overview](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [Create buying groups](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)

### Option B: Multiple solution interests with branching account journeys

**Best for:** Organizations with multiple product lines or service offerings that need to manage distinct buying groups per solution interest, with account journeys that branch based on which solution interests are active and how far along each buying group is in the qualification process.

**How it works:**

Multiple solution interests are defined, each with its own buying group role template. An account journey begins with account identification and evaluates which solution interests apply to each account based on behavioral signals, firmographic data, or explicit intent. The journey branches to address each active solution interest, running parallel nurture tracks for different buying groups within the same account.

Engagement scoring operates independently per buying group, allowing one buying group to reach sales readiness while another is still being nurtured. Sales alerts are configured per solution interest, so the appropriate sales team or specialist is notified when a specific buying group qualifies. CRM insights surface all active buying groups for an account, giving sales a holistic view.

**Key considerations:**

- Requires well-defined solution interest taxonomy and distinct buying group templates
- Journey complexity increases with each additional solution interest
- Cross-buying-group coordination (for example, shared contacts who hold roles in multiple buying groups) must be planned

**Advantages:**

- Supports cross-sell and multi-product account strategies
- Independent scoring per buying group provides granular pipeline visibility
- Sales teams receive targeted alerts per solution interest
- Maximizes [!DNL AJO B2B Edition] buying group management capabilities

**Limitations:**

- Higher implementation complexity and longer time to deploy
- More content assets required (separate email tracks per solution interest)
- Reporting is more complex with multiple buying groups per account
- Risk of over-messaging contacts who are in multiple buying groups (requires frequency management)

**Experience League:**

- [Solution interests](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Account journeys](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)

### Option C: AI-assisted account qualification with automated journey progression

**Best for:** Mature B2B organizations with significant historical data who want to leverage AI-powered account qualification agents to automate the assessment of account readiness, reduce manual qualification effort, and dynamically adjust journey paths based on AI-generated readiness scores.

**How it works:**

This approach builds on Option B's multi-solution-interest foundation but adds AI-powered account qualification to automate the transition between journey stages. Instead of relying solely on rule-based engagement score thresholds, the AI qualification agent evaluates account readiness using a broader set of signals -- buying group completeness, engagement velocity, firmographic fit, historical conversion patterns, and intent data.

Account journeys use the AI qualification output to determine next steps: accounts scoring high on readiness are fast-tracked to sales alerts, accounts in the middle tier receive intensified nurture, and low-readiness accounts are placed in long-term awareness tracks. The AI agent continuously re-evaluates as new engagement data arrives, enabling dynamic journey progression without manual intervention.

**Key considerations:**

- Requires sufficient historical data to train effective qualification models
- AI outputs should be validated against actual pipeline outcomes before full deployment
- Combines well with [!DNL CJA B2B Edition] for analyzing qualification accuracy and pipeline correlation

**Advantages:**

- Reduces manual qualification effort and eliminates arbitrary threshold-based handoffs
- Dynamically adapts to changing account behavior and engagement patterns
- Higher pipeline quality by incorporating multiple signals beyond simple engagement scores
- Continuous re-evaluation prevents accounts from being stuck in incorrect journey stages

**Limitations:**

- Requires historical conversion data for meaningful AI training
- "Black box" qualification decisions may be harder for sales teams to understand and trust initially
- More complex to troubleshoot when accounts are qualified unexpectedly or not at all
- Dependent on data quality and completeness across all input signals

**Experience League:**

- [Account qualification](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [AI Assistant in AJO B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)

### Option comparison

| Criteria | Option A: Single solution interest | Option B: Multiple solution interests | Option C: AI-assisted qualification |
| --- | --- | --- | --- |
| Best for | First deployment, single product line | Multi-product organizations | Mature orgs with historical data |
| Complexity | Low | Medium-High | High |
| Time to value | 2-4 weeks | 4-8 weeks | 6-12 weeks |
| Solution interests | 1 | Multiple | Multiple |
| Journey structure | Linear | Branching, parallel tracks | Dynamic, AI-driven progression |
| Scoring approach | Rule-based thresholds | Rule-based per buying group | AI-powered qualification + rules |
| Content requirements | Minimal (one nurture track) | High (per solution interest) | High + dynamic content selection |
| Sales alignment | Single alert workflow | Per-solution-interest alerts | Prioritized, AI-scored alerts |
| Requires | Basic B2B data foundation | Well-defined solution taxonomy | Historical conversion data + taxonomy |

### Choose the right option

Start with these questions to determine the best implementation approach:

1. **How many distinct products or services have independent buying committees?** If the answer is one (or the organization wants to prove the concept first), start with Option A. If multiple, go to question 2.

2. **Is there sufficient historical data on won/lost deals, buying committee composition, and engagement patterns?** If yes and the organization wants to minimize manual qualification, Option C provides the most automated approach. If not, Option B provides multi-solution-interest support with rule-based scoring.

3. **What is the organization's change management capacity?** Options B and C require more organizational alignment (content production, sales enablement, cross-functional coordination). If capacity is limited, start with Option A and expand.

A common progression path is: start with Option A to prove the concept with one solution interest, expand to Option B by adding solution interests as confidence grows, then layer in Option C's AI qualification once enough historical data is available to train the models effectively.

## Implementation phases

The following phases describe the step-by-step implementation process for this use case pattern.

### Phase 0: B2B data foundation

**Application functions:** [!DNL RT-CDP B2B]: Account Profile Unification, B2B Identity Resolution, [!DNL Marketo Engage] Integration, B2B Data Governance, Account Audience Evaluation

This phase establishes the B2B data infrastructure in [!DNL RT-CDP B2B Edition]. You will unify account data from CRM, marketing automation, and other sources into a single account profile, resolve person-to-account relationships, configure B2B data governance, and create account-level audiences that feed into [!DNL AJO B2B Edition] buying group management.

#### Decision: B2B data source strategy

Which systems serve as the primary sources for account, person, and engagement data?

| Option | When to choose | Considerations |
| --- | --- | --- |
| [!DNL Marketo Engage] as primary source | [!DNL Marketo] is the organization's marketing automation platform with rich engagement history | Native bidirectional connector simplifies setup; engagement data flows automatically; person-to-account relationships inherited from [!DNL Marketo] |
| CRM ([!DNL Salesforce]/[!DNL Dynamics]) as primary source | CRM is the system of record for accounts and contacts; [!DNL Marketo] is not used | Requires CRM source connector configuration; engagement data may need supplemental sources; person-to-account relationships from CRM account-contact associations |
| Hybrid: CRM for accounts + [!DNL Marketo] for engagement | CRM owns account/contact master data while [!DNL Marketo] captures behavioral engagement | Most common pattern for organizations using both; requires careful identity resolution to link [!DNL Marketo] persons to CRM contacts |

#### Decision: Account audience strategy

How should account audiences be defined for journey entry?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Firmographic-based account audiences | Target accounts based on industry, company size, revenue tier, or geography | Good for ABM target lists; does not require engagement data; can be broad |
| Engagement-based account audiences | Target accounts where people have shown behavioral intent signals | Requires engagement data flowing; more precise targeting; may miss accounts with latent interest |
| Combined firmographic + engagement | Target accounts that match ideal customer profile AND show engagement | Most precise; requires both data types; recommended for qualified pipeline generation |

**UI navigation:** Platform > Sources > Catalog > Select source ([!DNL Marketo Engage], [!DNL Salesforce], etc.) > Set up dataflow

**Key configuration details:**

- Configure B2B XDM schemas for each B2B entity (Account, Person, Opportunity, Campaign, Campaign Member) with required field groups
- Set up source connectors for CRM and/or [!DNL Marketo Engage] with appropriate scheduling (typically 1-4 hour intervals for B2B data)
- Configure identity namespaces for B2B identifiers ([!DNL Marketo] Person ID, SFDC Lead ID, SFDC Contact ID, Account ID)
- Enable B2B identity resolution to link persons to accounts
- Create account-level audiences using the Account Audiences capability in [!DNL RT-CDP]

**Experience League documentation:**

- [RT-CDP B2B Edition overview](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [B2B schemas in Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Marketo Engage source connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [B2B identity resolution](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)

### Phase 1: Solution interest & buying group setup

**Application functions:** [!DNL AJO B2B]: Solution Interest Configuration, Buying Group Management

This phase defines the solution interests (products/services) and buying group templates that form the core of the buying group management model. You will create solution interests, define role templates with persona requirements, and configure how leads are qualified into buying group roles.

#### Decision: Solution interest granularity

At what level should solution interests be defined?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Product-level solution interests | Each distinct product has its own buying group | Most granular; enables product-specific buying group templates; may result in many buying groups per account |
| Solution-category-level interests | Group related products into solution categories (for example, "Marketing Cloud" instead of individual products) | Simpler to manage; fewer buying groups; roles may be more generic; recommended for initial deployments |
| Use-case-level interests | Define interests around business outcomes rather than products (for example, "Digital Transformation") | Aligns with consultative selling; buying group roles may span multiple products; harder to map to CRM pipeline stages |

#### Decision: Buying group role template design

How should roles be defined within each buying group?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Standard role template | Use a common set of roles across all solution interests (for example, Economic Buyer, Technical Evaluator, Champion, End User) | Consistent scoring and qualification; easier to manage; may not capture solution-specific roles |
| Solution-specific role templates | Define unique roles per solution interest based on the actual buying committee for that product | More accurate qualification; requires deeper knowledge of each buying process; higher maintenance |
| Tiered role templates | Define required roles (must-have for qualification) and optional roles (enhance completeness but not required) | Balances precision with flexibility; prevents over-stringent qualification criteria from blocking pipeline |

**UI navigation:** [!DNL AJO B2B Edition] > Buying Groups > Solution Interests > Create Solution Interest

**UI navigation:** [!DNL AJO B2B Edition] > Buying Groups > Role Templates > Create Role Template

**Key configuration details:**

- Define each solution interest with a name, description, and the business outcome it addresses
- Create role templates specifying the personas required for each buying group (for example, "Decision Maker," "Influencer," "Practitioner," "Executive Sponsor")
- Configure lead-to-role qualification criteria: how the system determines which persona a lead maps to (based on job title, department, seniority, or custom attributes)
- Set completeness thresholds: define what percentage of roles must be filled for a buying group to be considered "complete"
- Link solution interests to account audiences or account attributes that indicate potential interest

**Where options diverge:**

**For Option A (Single Solution Interest):**
Create one solution interest and one role template. Focus on a clear, well-understood buying motion for the organization's primary product or service.

**For Option B (Multiple Solution Interests):**
Create multiple solution interests, each with its own role template. Map each solution interest to the appropriate CRM product/opportunity type for downstream pipeline tracking.

**For Option C (AI-Assisted Qualification):**
Configure solution interests and role templates as in Option B, but additionally configure the AI qualification agent with historical data on successful buying group compositions and deal outcomes to train the qualification model.

**Experience League documentation:**

- [Buying groups overview](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [Solution interests](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Role templates](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [Create buying groups](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)

### Phase 2: Lead qualification & engagement scoring

**Application functions:** [!DNL AJO B2B]: Engagement Scoring, Account Qualification

This phase sets up the engagement scoring model that measures person-level engagement within buying groups and rolls it up to buying group and account-level readiness scores. You will configure scoring rules, define engagement thresholds for qualification, and optionally enable AI-powered account qualification.

#### Decision: Engagement scoring model

How should engagement be scored at the person and buying group level?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Activity-based scoring | Assign point values to specific actions (email open = 5 pts, content download = 15 pts, demo request = 50 pts) | Transparent and easy to tune; requires ongoing maintenance as content and channels change; most familiar to [!DNL Marketo] users |
| Recency-weighted scoring | Weight recent activities higher than older ones (decaying score model) | Better reflects current intent; prevents stale high scores from inflating qualification; more complex to configure |
| AI-powered scoring | Use the [!DNL AJO B2B] AI qualification agent to generate readiness scores based on pattern recognition | Most sophisticated; adapts automatically; requires historical data; may be opaque to sales teams initially |

#### Decision: Qualification threshold approach

When should a buying group be considered ready for sales handoff?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Score threshold only | Buying group qualifies when aggregate engagement score exceeds a defined value | Simple to implement; score threshold may need tuning over time; does not consider role composition |
| Completeness + score threshold | Buying group qualifies when minimum role coverage AND score threshold are both met | More robust qualification; prevents handoff of buying groups with high scores but missing key roles |
| AI-determined readiness | AI qualification agent determines readiness using multiple signals beyond score and completeness | Most sophisticated; accounts for buying velocity, competitive signals, and historical patterns; Option C only |

**UI navigation:** [!DNL AJO B2B Edition] > Buying Groups > Engagement Scoring > Configure Scoring Rules

**Key configuration details:**

- Define engagement scoring rules: assign point values to behavioral events (email opens, clicks, web page visits, content downloads, form submissions, webinar attendance, demo requests)
- Configure score decay or recency weighting if using time-sensitive scoring
- Set buying group-level score aggregation: how person scores combine into a buying group score (sum, weighted average, or minimum-threshold-per-role)
- Define qualification thresholds: the score and completeness levels that trigger transition to the next buying stage
- Configure the AI qualification agent (Option C): train with historical deal data, define the signals the agent should consider, and set confidence thresholds

**Experience League documentation:**

- [Engagement scoring](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Buying group stages](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Account qualification](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)

### Phase 3: Account journey design & execution

**Application functions:** [!DNL AJO B2B]: Account Journey Orchestration, B2B Email Authoring, SMS Channel Management

This phase designs and deploys the account journey that orchestrates engagement with buying group members. You will create account journeys with entry conditions, action nodes (email, SMS), condition branches (based on buying group stage, engagement score, role coverage), wait steps, and exit criteria.

#### Decision: Journey entry trigger

What event or condition causes an account to enter the journey?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Account audience qualification | Account enters when it joins a target account audience | Batch-oriented; good for ABM list-based entry; audience must be pre-defined |
| Buying group creation event | Account enters when a buying group is first created for the account | Event-driven; triggered by lead qualification into a buying group role; more real-time |
| Account attribute change | Account enters when a specific attribute changes (for example, intent score, account tier) | Requires the triggering attribute to be updated in real-time or near-real-time |

#### Decision: Channel mix for B2B nurture

Which channels should the account journey use to engage buying group members?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Email only | Most B2B interactions happen via email; no SMS opt-in infrastructure exists | Simplest to configure; most common B2B pattern; may miss mobile-first contacts |
| Email + SMS | Organization has SMS opt-in from business contacts; high-urgency notifications warranted | SMS effective for time-sensitive alerts (event reminders, meeting confirmations); requires SMS provider configuration |
| Email + SMS + Sales alerts | Full-spectrum: marketing nurture via email/SMS plus sales team notifications | Most comprehensive; requires sales team adoption of alert workflow; coordinates marketing and sales touchpoints |

#### Decision: Journey branching strategy

How should the journey branch based on account and buying group status?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Stage-based branching | Branch based on buying group stage (for example, Awareness, Consideration, Decision) | Aligns with traditional funnel stages; content mapped to stages; clear progression path |
| Role-based branching | Branch to send different content to different buying group roles (technical content to evaluators, ROI content to economic buyers) | More personalized; requires role-specific content assets; higher content production effort |
| Engagement-based branching | Branch based on engagement score thresholds (low engagement = re-engage, high = accelerate) | Dynamic and responsive; adapts to actual behavior; may create complex branching trees |

**UI navigation:** [!DNL AJO B2B Edition] > Account Journeys > Create Journey

**Key configuration details:**

- Create the account journey canvas with the selected entry condition
- Add account journey nodes: email actions, SMS actions, wait steps, condition splits, and path branching
- Author B2B email content using the B2B Email Designer with brand themes, visual fragments, and AI-assisted content generation
- Configure personalization tokens referencing account attributes, person attributes, and buying group data
- Set wait durations between touchpoints (B2B journeys typically use longer waits: 3-7 days between emails)
- Define exit criteria: conditions under which accounts leave the journey (buying group reaches qualification threshold, opportunity created in CRM, account opts out)
- Configure SMS actions if using SMS channel (requires SMS provider configuration and contact opt-in)
- Test the journey with test accounts before publishing

**Where options diverge:**

**For Option A (Single Solution Interest):**
Design a linear journey with sequential stages. Entry is based on a single account audience or buying group creation event. One email nurture track with increasing urgency and depth of content.

**For Option B (Multiple Solution Interests):**
Design a journey with parallel branches per solution interest. Use condition nodes to route accounts to the appropriate nurture track based on which buying groups exist. Each branch has its own content and scoring thresholds.

**For Option C (AI-Assisted Qualification):**
Design a journey where condition nodes evaluate the AI qualification score rather than (or in addition to) rule-based thresholds. Include dynamic path selection where the AI determines whether to accelerate, maintain, or de-prioritize an account.

**Experience League documentation:**

- [Account journeys overview](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [Account journey nodes](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [B2B email authoring](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [SMS channel in AJO B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [AI Assistant for email authoring](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### Phase 4: Sales alignment & CRM integration

**Application functions:** [!DNL AJO B2B]: Sales Alert Configuration, CRM Sales Insights; [!DNL RT-CDP B2B]: Account Destination Configuration, Account Audience Activation

This phase establishes the bridge between marketing and sales by configuring sales alert emails, deploying CRM Sales Insights for in-CRM visibility, and optionally activating account audiences to B2B destinations ([!DNL LinkedIn], [!DNL Marketo], CRM systems).

#### Decision: Sales alert trigger strategy

When should sales be notified about an account's buying group status?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Milestone-based alerts | Notify sales when buying group reaches specific milestones (qualified, complete, high engagement) | Clear, discrete notifications; prevents alert fatigue; may miss gradual engagement trends |
| Threshold-based alerts | Notify sales when engagement score crosses a defined threshold | Continuous monitoring; may trigger multiple alerts as scores fluctuate near the threshold |
| Stage-transition alerts | Notify sales when buying group transitions to a new stage (for example, from Consideration to Decision) | Aligns with pipeline stages; clearest signal for sales action; requires well-defined stage definitions |

#### Decision: CRM integration depth

How deeply should buying group data be surfaced in the CRM?

| Option | When to choose | Considerations |
| --- | --- | --- |
| Sales alerts only (no in-CRM component) | Organization does not use [!DNL Salesforce] or [!DNL Dynamics], or CRM integration is not feasible | Lowest integration effort; sales receives email notifications but no CRM dashboard; limited visibility |
| CRM Sales Insights dashboard | Organization uses [!DNL Salesforce] or [!DNL Dynamics] and wants buying group status visible within the CRM | Requires installing the CRM Sales Insights package; provides rich account-level intelligence; recommended for most implementations |
| Full bidirectional CRM sync | Buying group stages and scores write back to CRM objects, influencing CRM workflow and reporting | Highest integration complexity; enables CRM-native pipeline reporting; requires custom CRM configuration |

**UI navigation:** [!DNL AJO B2B Edition] > Administration > Sales Alert Configuration

**UI navigation:** [!DNL AJO B2B Edition] > Administration > CRM Sales Insights > Configure

**Key configuration details:**

- Configure sales alert email templates: include buying group status, engaged personas, engagement score, and recommended next actions
- Define alert routing rules: which sales representatives or teams receive alerts based on account ownership, territory, or solution interest
- Install and configure CRM Sales Insights for [!DNL Salesforce] or [!DNL Dynamics 365]
- Map buying group data to CRM objects so sales can view buying group composition, engagement, and journey progress within their CRM workflow
- Optionally configure account destination connections to activate account audiences to [!DNL LinkedIn] (for ABM advertising), [!DNL Marketo Engage] (for lead-level follow-up), or other B2B destinations

**Experience League documentation:**

- [Sales alert emails](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [CRM Sales Insights](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)
- [Destinations overview](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [LinkedIn Matched Audiences destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)

### Phase 5: Reporting & optimization

**Application functions:** [!DNL AJO B2B]: B2B Analytics Dashboards

This phase establishes the reporting and analytics framework to measure buying group performance, account journey effectiveness, and pipeline impact. [!DNL AJO B2B Edition] provides built-in analytics dashboards; [!DNL CJA B2B Edition] (if licensed) extends analysis with deeper cross-channel account-level insights.

#### Decision: Reporting approach

Which analytics tools should be configured for ongoing performance monitoring?

| Option | When to choose | Considerations |
| --- | --- | --- |
| [!DNL AJO B2B] dashboards only | [!DNL AJO B2B Edition]'s built-in dashboards are sufficient for buying group and journey metrics | Fastest to configure; covers core B2B metrics; limited custom analysis capability |
| [!DNL AJO B2B] dashboards + [!DNL CJA B2B Edition] | Organization needs deeper cross-channel analysis, buying group analysis, opportunity correlation, and custom attribution | Requires [!DNL CJA B2B Edition] license; most comprehensive; supports account-level freeform analysis |
| [!DNL AJO B2B] dashboards + CRM reporting | Organization prefers to centralize pipeline reporting in the CRM alongside buying group metrics | Requires CRM dashboard development; combines marketing and sales metrics in one place; limited to CRM reporting capabilities |

**UI navigation:** [!DNL AJO B2B Edition] > Dashboards > Engagement Overview / Intelligent Dashboard

**Key configuration details:**

- Access the [!DNL AJO B2B] Engagement Dashboard to monitor buying group engagement scores, completeness rates, and stage distribution
- Access the Intelligent Dashboard for AI-driven insights on account readiness and pipeline quality
- If using [!DNL CJA B2B Edition]: configure an account-based CJA connection including [!DNL AJO B2B] datasets, set up a B2B data view with Buying Group and Account containers, and build workspace analysis for buying group progression, opportunity correlation, and attribution
- Define reporting cadence: weekly buying group performance reviews, monthly pipeline impact analysis, quarterly program optimization
- Create annotations for significant events (campaign launches, content refreshes, scoring model changes) to correlate with performance trends

**Experience League documentation:**

- [B2B analytics dashboards](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [Engagement dashboard](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [Intelligent dashboard](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [CJA B2B Edition overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

## Implementation considerations

The following sections cover guardrails, common pitfalls, best practices, and trade-off decisions to keep in mind during implementation.

### Guardrails & limits

- [!DNL AJO B2B Edition] account journey limits, including maximum concurrent journeys and maximum accounts per journey, follow the [!DNL AJO B2B Edition] product guardrails -- [AJO B2B guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [!DNL RT-CDP B2B Edition] supports up to 50 B2B schema classes and follows standard profile and segmentation guardrails -- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Account audience evaluation operates on batch schedules; real-time account audience updates are not supported for all segment types -- [Segmentation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- B2B source connector ingestion has minimum scheduling intervals (typically 15 minutes for [!DNL Marketo], varying for CRM sources) -- [Ingestion guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- Email channel surfaces are limited to 10 per channel type per sandbox -- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

### Common pitfalls

- **Defining too many roles per buying group:** Over-specifying roles (for example, requiring 8-10 distinct personas) makes it nearly impossible for buying groups to reach completeness thresholds. Start with 3-5 essential roles and expand as the model matures.
- **Setting engagement score thresholds too high or too low:** If thresholds are too high, no buying groups qualify, starving the pipeline. If too low, unqualified accounts flood sales. Begin with historical data analysis (if available) and iterate based on sales feedback.
- **Ignoring person-to-account resolution quality:** If persons are not correctly linked to accounts, buying groups will have missing members even when the right people are engaged. Invest in identity resolution quality before launching buying group journeys.
- **Over-messaging contacts in multiple buying groups:** A single contact may hold roles in multiple buying groups (for example, a CTO who is a Technical Evaluator for both CRM and Data Platform purchases). Without frequency management, this person receives emails from every active journey. Implement cross-journey frequency rules.
- **Neglecting sales enablement:** Sales teams must understand how to interpret buying group data, engagement scores, and sales alerts. Without training and adoption, the marketing-to-sales handoff fails regardless of data quality.
- **Treating account journeys like person journeys:** Account journeys operate at the account level, sending emails to persons within the account's buying groups. Journey design must consider that multiple persons receive messages per account node execution, which is fundamentally different from person-level [!DNL AJO] journeys.

### Best practices

- **Start with one solution interest and expand** -- Prove the model works for one buying motion before scaling to multiple solution interests. This allows the team to refine role templates, scoring models, and content before adding complexity.
- **Align buying group roles with CRM sales process** -- Map buying group roles to the personas the sales team already recognizes. Use the same language (Economic Buyer, Champion, etc.) so the handoff is intuitive.
- **Implement a feedback loop with sales** -- Regularly collect sales feedback on the quality of marketing-qualified accounts. Use this feedback to tune engagement scoring thresholds and role qualification criteria.
- **Design content for roles, not just stages** -- Different buying group roles need different content: executives want ROI and strategic impact, technical evaluators want architecture and integration details, end users want ease-of-use demonstrations. Map content assets to roles for more effective nurture.
- **Set up CRM Sales Insights early** -- Do not wait until the full journey is live to deploy CRM visibility. Sales teams need to see buying group data forming early to provide feedback on role accuracy and account targeting.
- **Use wait steps strategically** -- B2B buying cycles are long. Account journey wait steps should reflect this reality (5-14 day intervals between touches) rather than consumer-style urgency (1-3 days).
- **Monitor engagement velocity, not just engagement score** -- A buying group that goes from score 20 to 80 in two weeks signals stronger intent than one that reaches 80 over six months. Configure scoring and qualification to account for velocity.

### Trade-off decisions

The following trade-offs should be evaluated based on your organization's specific needs.

#### Buying group completeness vs. pipeline volume

Requiring all roles to be filled before qualifying a buying group maximizes pipeline quality but may severely limit the volume of qualified accounts, especially for new products or markets where the organization's database has limited coverage.

- **Higher completeness threshold favors:** Pipeline quality; sales receives fully formed buying groups; higher win rates per account
- **Lower completeness threshold favors:** Pipeline volume; more accounts reach sales; broader coverage; higher volume but potentially lower quality
- **Recommendation:** Start with a moderate threshold (60-70% role coverage) and adjust based on actual win rate data. For established markets with good data coverage, increase toward 80%+. For new markets, accept 50-60% initially and use buying group completeness campaigns to fill gaps.

#### Scoring granularity vs. operational simplicity

Highly granular scoring models (with dozens of activity types, recency weighting, and role-specific scoring) provide more precise qualification signals but are harder to maintain, explain, and troubleshoot.

- **Higher granularity favors:** Precision of qualification; nuanced differentiation between accounts; better alignment with complex buying processes
- **Lower granularity favors:** Operational simplicity; easier to maintain and explain to sales; faster implementation; fewer edge cases
- **Recommendation:** Start with a simple scoring model (10-15 activity types, uniform point values) and add complexity only where the simple model fails to differentiate account quality. Document the scoring model thoroughly for sales alignment.

#### Single journey vs. multiple specialized journeys

A single, comprehensive account journey that handles all stages and solution interests in one canvas provides unified control but can become unwieldy. Multiple specialized journeys (one per stage or solution interest) are simpler individually but harder to coordinate.

- **Single journey favors:** Holistic view; easier to ensure consistent timing and messaging; simpler to monitor; one place for all logic
- **Multiple journeys favor:** Modularity; easier to update one stage without affecting others; different teams can own different journeys; cleaner canvas design
- **Recommendation:** For Option A, a single journey is appropriate. For Options B and C, use a primary "orchestration" journey that routes accounts to specialized sub-journeys per solution interest or buying stage.

## Related documentation

The following resources provide additional detail on the applications and capabilities referenced in this guide.

### [!DNL AJO B2B Edition]

- [AJO B2B Edition documentation home](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [Buying groups overview](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [Solution interests](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Role templates](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [Create buying groups](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)
- [Buying group stages](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Account journeys overview](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [Account journey nodes](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [Sales alert emails](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [CRM Sales Insights](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)

### B2B email & content

- [B2B email authoring](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [SMS authoring in AJO B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [AI Assistant for email authoring](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### B2B analytics & dashboards

- [Buying groups dashboard](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [Engagement dashboard](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [Intelligent dashboard](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [CJA B2B Edition overview](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### [!DNL RT-CDP B2B Edition]

- [RT-CDP B2B Edition overview](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [B2B schemas in Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [Marketo Engage source connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)

### Data foundation

- [XDM System overview](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Identity Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Sources overview](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Segmentation Service overview](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)

### Channel configuration

- [Get started with email configuration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Configure SMS channel](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### Data governance & privacy

- [Data governance overview](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Advanced Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### Destinations

- [Destinations overview](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Destinations catalog](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [LinkedIn Matched Audiences destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)

### Guardrails

- [Real-Time Customer Profile guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Segmentation guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [Ingestion guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

### Tutorials & getting started

- [AJO B2B Edition getting started](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [RT-CDP B2B Edition tutorial](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-tutorial)
