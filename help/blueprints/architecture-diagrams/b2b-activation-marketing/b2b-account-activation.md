---
title: B2B Account Activation to Advertising and File Destinations
description: Use account-based engagement to create account audiences and activate them to advertising destinations and cloud storage.
solution: Real-Time Customer Data Platform
exl-id: 578c0019-6133-4508-ae9d-8a8a463376f0
---

# B2B account activation to advertising destinations and file destinations

Account-based engagement allows B2B marketers to create audiences of accounts (lists of companies) in **Real-Time Customer Data Platform B2B Edition** and activate those account audiences to advertising destinations such as LinkedIn Matched Audiences, Bombora, and Demandbase, as well as to cloud storage destinations. These account audiences can be used for targeting, sales outreach, and downstream analytics.

## Use cases

Using account-based engagement, marketers can unlock three key use cases:

- **Fill buying group gaps:** A marketer can advertise on accounts where they do not yet have contacts for the CMO or CIO roles. They can first build an audience of accounts without a contact with the title "CMO" or "CIO" and then activate the audience on LinkedIn Matched Audiences or other supported advertising destinations. Within the destination, they can then launch a campaign targeting that audience and specific people with "CMO" or "CIO" job titles to reach these new contacts and highlight the benefits of their offerings.
- **Upsell or cross-sell to other divisions of a company that is an existing customer:** A marketer can build an account audience that purchased product X between 3 and 9 months ago but does not yet own product Y. They can then activate this account audience, highlighting the benefits of product Y to that target audience via LinkedIn Matched Audiences, other advertising platforms, or cloud storage exports for sales and marketing outreach.
- **Target companies that are using competing products:** A marketer can market to accounts to displace a competitor's products, even without any contacts at those accounts. They can create an audience of accounts based on partner or intent data showing ownership or usage of a competitor's product, then activate via LinkedIn Matched Audiences or other supported advertising destinations to source contacts at target accounts for expansion.

## Applications

- Real-Time Customer Data Platform B2B Edition
- (Optional) Customer Journey Analytics B2B Edition

## Integration patterns

Typical integration patterns for this blueprint include:

- **B2B engagement and CRM sources → RTCDP B2B Edition → account audiences → destinations**

  B2B engagement and CRM systems such as Marketo Engage, Salesforce, and Microsoft Dynamics send leads/contacts, accounts, and opportunities into **Real-Time CDP B2B Edition** using the standard B2B schemas and relationships. Account audiences are built on top of this unified B2B data model and activated to advertising and file destinations.

- **B2B intent and event sources → RTCDP B2B Edition → account audiences → destinations**

  B2B intent and event sources such as Bombora Intent and Demandbase Intent send intent and engagement events into Experience Platform. These data sets are mapped to the standard B2B schemas, allowing marketers to build account audiences (for example, accounts surging on competitor topics) and activate them to advertising and cloud storage destinations. Account audiences can then be activated to advertising partners such as Bombora and Demandbase where supported.

## Architecture

<img src="assets/b2b-account-activation.png" alt="Reference architecture for the B2B Account Activation blueprint" style="border:1px solid #4a4a4a"  width="100%" />

## Account audience destinations

- **LinkedIn Matched Audiences**
- **Bombora**
- **Demandbase**
- **Cloud storage destinations**
  - Azure Data Lake Storage Gen2
  - Data Landing Zone
  - SFTP
  - Azure Blob
  - AWS S3

Refer to the destination documentation for the latest list of destinations that support account audiences.

## Guardrails

Refer to the following guardrails when designing and activating account audiences:

- [Guardrails for Real-Time Customer Data Platform B2B Edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails?lang=en)
- [Account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences?lang=en)
- [Activate account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)
- [Profile and Segmentation Guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Streaming segmentation eligibility criteria update](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/eligibility-criteria-update)

## Implementation steps for Real-Time Customer Data Platform B2B Edition, account audience creation, and activation

- For implementation steps of Real-Time Customer Data Platform B2B Edition, see the documentation: [Getting started with Real-Time Customer Data Platform B2B Edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial?lang=en).
- For Account Audience creation steps, see the [Account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences?lang=en) documentation.
- For Account Audience activation steps, see the [Activate account audiences](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en) documentation:

  - Required mapping for [LinkedIn Matched Audiences destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en#required-mappings).

## Implementation considerations

LinkedIn Matched Audiences have a minimum audience size requirement (for example, 300 matched members). If the account audience activated to LinkedIn Matched Audiences does not meet this requirement, you may need to broaden the audience definition to increase the matchable audience size before launching a campaign.

## Related Documentation

- [B2B Audience and Profile Activation blueprint](b2bactivation.md) — parent blueprint covering both people-level and account-level B2B activation.
- [B2B Edition of Real-Time Customer Data Platform](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview?lang=en)
- [Create and activate Account Audience – tutorial video](https://experienceleague.adobe.com/en/docs/platform-learn/tutorials/audiences/create-audiences-with-b2b-data?lang=en)
- [Create Account Audiences](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences?lang=en)
- [Activate Account Audiences](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)
- [Adobe Experience Platform – LinkedIn Destination Connector](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin?lang=en)
- [Schemas in Real-Time CDP B2B Edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Architecture upgrades to Real-Time CDP B2B Edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-architecture-upgrade)
- [Destination Guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
