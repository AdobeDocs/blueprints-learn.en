---
title: B2B Audience and Profile Activation
description: Deliver account-based and people-based audiences with Real-Time Customer Data Platform B2B Edition for activation across channels and destinations.
solution: Real-Time Customer Data Platform
product_v2:
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
    internal-label: Real-Time Customer Data Platform
---

# B2B Audience and Profile Activation

Use **Real-Time Customer Data Platform B2B Edition** to bring together account, opportunity, and person data into unified B2B profiles, then activate both people audiences and account audiences across destinations such as LinkedIn, Marketo Engage, and cloud storage. This blueprint describes how to design B2B schemas, build multi-entity audiences, and export them for activation across multiple channels and destinations, as well as for orchestration and analytics in applications like **Journey Optimizer B2B Edition** and **Customer Journey Analytics B2B Edition**.

## Use cases

- Create audiences of people for targeting and personalization across channels based on B2B data including accounts, opportunities, and leads.
- Create multi-entity audiences that combine account- and opportunity-level attributes with person-level behavior by using a **segment-of-segments** approach (for example, "People who visited the pricing page in the last 3 days and are decision makers in opportunities at stage X for accounts in industry Y").
- Activate people audiences to supported Experience Platform destinations for targeting and personalization, and account audiences to supported advertising and cloud storage destinations for targeting, sales outreach, and analytics. Destination support differs by audience type; see [Account audience destinations](#account-audience-destinations) for account activation.

### Account-based use cases

- **Fill buying group gaps:** Build an audience of accounts without contacts in roles such as CMO or CIO. Activate it to LinkedIn Matched Audiences or another supported advertising destination, then use the destination's job-title targeting to reach new contacts in those roles.
- **Upsell or cross-sell to other divisions of an existing customer:** Build an account audience that purchased product X between 3 and 9 months ago but does not yet own product Y. Activate it to supported advertising destinations or export it to cloud storage for sales and marketing outreach.
- **Target companies using competing products:** Use partner or intent data to identify accounts using a competitor's product, even when no contacts are known. Activate the account audience to supported advertising destinations to reach contacts at those companies.

## Applications

- Real-Time Customer Data Platform B2B Edition
- (Optional) **Customer Journey Analytics B2B Edition**
- (Optional) **Journey Optimizer B2B Edition**

## Integration patterns

Typical B2B integration patterns for this blueprint include:

- **B2B engagement and CRM sources → RTCDP B2B → destinations**

  B2B engagement and CRM systems such as Marketo Engage, Salesforce, and Microsoft Dynamics send leads/contacts, accounts, and opportunities into **Real-Time CDP B2B Edition** using the standard B2B schemas and relationships. From there, people audiences are activated to supported destinations including:

  - Marketo Engage
  - LinkedIn / LinkedIn Matched Audiences
  - Google Customer Match & DV360
  - The Trade Desk
  - Amazon Ads
  - Trade Desk CRM, Criteo, Bing, and other advertising platforms
  - Cloud storage destinations such as Amazon S3, ADLS, and Snowflake for downstream use

  Account audiences use the same unified B2B data model and are activated separately to supported advertising and file destinations listed under [Account audience destinations](#account-audience-destinations).

- **B2B intent and event sources → RTCDP B2B → audiences → destinations**

  B2B intent and event sources such as Bombora Intent, Demandbase Intent, PathFactory, and RainFocus stream intent and engagement events into RTCDP B2B. These events are mapped to standard B2B schemas and used to build people and account audiences that can be activated to advertising and marketing destinations. For example, accounts showing intent on competitor topics can be activated to supported account destinations such as Bombora and Demandbase.

Various B2B data sources can be used to map account, lead, opportunity, and person data to the B2B Edition of Real-Time Customer Data Platform using the standard **B2B schemas and relationships**.

## Architecture

![Reference architecture for the B2B Audience and Profile Activation blueprint](assets/b2b-audience-profile-activation.png){width="1000" zoomable="yes"}

## Account audience destinations

Account audiences can be activated to the following advertising and cloud storage destinations:

- LinkedIn Matched Audiences
- Bombora
- Demandbase
- Azure Data Lake Storage Gen2
- Data Landing Zone
- SFTP
- Azure Blob
- AWS S3

Refer to [Activate account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en) for the latest supported destinations and required mappings. The people-audience destinations listed in the integration patterns do not necessarily support account audiences.

## Guardrails

Refer to the following guardrails and eligibility documentation when designing B2B audiences and profiles:

- [Guardrails for Real-Time Customer Data Platform B2B Edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails?lang=en)
- [Account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences?lang=en)
- [Activate account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)
- [Segmentation use cases for Real-Time CDP B2B Edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/segmentation/b2b)
- [Profile and Segmentation Guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Streaming segmentation eligibility criteria update](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/eligibility-criteria-update)

### Multiple Instance and IMS Org Support

The following outlines the supported patterns of mapping Experience Platform and Marketo Engage instances.

#### Marketo as a data source to Experience Platform

- Multiple Marketo Engage instances to one Experience Platform instance is supported.
- One Marketo Engage instance to many Experience Platform instances is not supported.
- One Marketo Engage instance to one Experience Platform instance and multiple sandboxes is supported.

#### Marketo as a destination to Experience Platform

- Experience Platform to many Marketo Engage instances is supported.
- Many Experience Platform instances to one Marketo Engage instance is supported.

#### Experience Platform Profile and Segmentation Guardrails

See the Experience Platform profile and segmentation guardrails here: [Profile and Segmentation Guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails).

Segments that include B2B entities such as accounts, leads, or opportunities rely on multi-entity relationships and are evaluated in **batch**. By contrast, **streaming segmentation** is supported for audiences limited to people and events that do not incorporate B2B entities. For near-real-time B2B activation scenarios, consider using batch-evaluated B2B audiences as inputs to streaming or edge audiences where supported.

#### Experience Platform – Marketo Engage Source Connector

- Refer documentation [here](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo).

#### Experience Platform – Marketo Destination Connector

- Refer documentation [here](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage-connection).

#### Destination Guardrails

- Please refer to the destination documentation for specific guidance on each destination: [Destination Guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails).
- For advertising destinations such as Facebook, Google Customer Match & DV360, Microsoft Bing, The Trade Desk, Amazon Ads, Bombora, Demandbase, and others, ensure that the identifiers you choose in your schema and identity strategy (email, mobile advertising IDs, address fields, account IDs) align with the mapping capabilities and supported identities for those destinations.

## Implementation steps

For guidance on how to implement and configure the B2B Edition of the Real-Time Customer Data Platform, see the Real-Time CDP B2B Edition documentation: [B2B Edition of Real-Time Customer Data Platform](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview).

Two implementation patterns are common:

- Ingest B2B data and profiles from Marketo Engage (and its connected CRM) into RTCDP B2B Edition.
- Ingest B2B data directly from CRM or other B2B systems into RTCDP B2B Edition using the relevant source connectors.

As part of the RTCDP B2B architecture upgrades, some previously used patterns are now deprecated for B2B entities. For more in-depth details refer detailed documentation [here](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-architecture-upgrade).

For account audience creation and activation, see:

- [Create account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences?lang=en).
- [Activate account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en).
- [Required mappings for LinkedIn Matched Audiences](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en#required-mappings).

## Implementation considerations

Guidance on key considerations and configurations of the blueprint.

- **CRM Integration with and without Marketo**

  - If the implementation uses Marketo Engage as a source and Marketo Engage is connected to the CRM, then CRM data that is synchronized into Marketo (for example, leads/contacts, accounts, opportunities) will flow into RTCDP B2B Edition via the Marketo source connector.
  - If there are additional CRM tables or attributes that are not passed through Marketo (for example, custom objects or additional fields), connect the CRM source directly to Experience Platform using the CRM source connectors and map those tables to the standard B2B schemas and relationships.
  - Design CRM + Marketo ingestion together to avoid duplicate or conflicting representations of B2B entities in RTCDP B2B and ensure that all B2B entities conform to the standard schemas.

- **LinkedIn Matched Audiences minimum audience size**

  LinkedIn Matched Audiences has a minimum audience size requirement (for example, 300 matched members). If an activated account audience does not meet the requirement, broaden the audience definition to increase the matchable audience size before launching a campaign. Refer to the [LinkedIn destination documentation](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin?lang=en) for current requirements.

## Related documentation

- [B2B Edition of Real-Time Customer Data Platform](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
- [Getting Started with Real-Time Customer Data Platform B2B Edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial?lang=en)
- [Create and activate account audiences tutorial](https://experienceleague.adobe.com/en/docs/platform-learn/tutorials/audiences/create-audiences-with-b2b-data?lang=en)
- [Create account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences?lang=en)
- [Activate account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)
- [LinkedIn destination connector](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin?lang=en)
- [Guardrails for Real-Time Customer Data Platform B2B Edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails?lang=en)
- [Schemas in Real-Time Customer Data Platform B2B Edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Architecture upgrades to Real-Time CDP B2B Edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-architecture-upgrade)
- [Adobe Experience Platform](https://experienceleague.adobe.com/en/docs/experience-platform)
- [Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home)
- [Adobe Experience Platform – Marketo Source Connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Adobe Experience Platform – Marketo Destination Connector](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-platform-segment-to-a-marketo-static-list)
- [Destination Guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
