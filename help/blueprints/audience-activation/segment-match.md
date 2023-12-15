---
title: Segment Match blueprint
description: Learn about [!UICONTROL Segment Match] for Adobe Experience Platform (AEP). [!UICONTROL Segment Match] is a data collaboration service that enables you to exchange segment data based on common industry identifiers in a secured, governed, and privacy-friendly manner.
solution: Experience Platform
exl-id: d7e6d555-56aa-4818-8218-b87f6286a75e
---
# Segment Match blueprint

Segment Match enables partner brands to share audiences across their respective Experience Platform environments. The key for brands is to connect with customers based on data gathered from their direct relationships with consumers. With better governance, permissions, and preference management systems, marketers can further enhance their first-party authenticated audiences with key partners. 

[!UICONTROL Segment Match] is a data collaboration service to allow Experience Platform (AEP) customers (referred to as _partners_) to exchange segment data based on common industry identifiers in a secured, governed, and privacy-friendly manner.

The service enables customers to securely identify matching IDs in a safe, neutral way without having to disclose their entire database. Partners receive only designated attributes (segment name) for overlapping IDs, enabling faster and easier sharing in a controllable, consent-governed manner.

[!UICONTROL Segment Match] uses AEP data governance and consent framework as its backbone. It is available for all B2C and B2P Real-time Customer Data Platform customers. Key features of [!UICONTROL [!UICONTROL Segment Match]] include:

* Segment sharing for overlapping consenting customers
* Pre-share overlap reports for insights on estimated match volume
* Fully integrated DULE policy and permission enforcement
* Data sharing consent framework backbone
* Data feeds for organizing segments and partners

## Applications

Brand to Publisher:

The 'publisher use case' is the most impacted by the deprecation of third-party cookies and mobile advertising id data. This use case has a major impact on the media and entertainment industry who focus on selling advertising as a business model. [!UICONTROL Segment Match] is a path for publishers with large first party audiences looking to collaborate directly with their advertisers. Advertisers may work directly with publishers to advertise against matched audiences on publisher properties for granular targeting or prospecting campaigns.

### Brand to Brand

Consumer journeys are never linear. For example, a customer may be loyal to an airline and to their credit card company. By using [!UICONTROL Segment Match], the airline and the credit card company can create a data partnership to understand overlapping audiences and then tailor offers to personalize experiences to loyal consumers of each of the companies.

### BU to BU

Global multinationals have challenges with data collaboration among independently operating business units. Combining data into a single sandbox may not be possible due to varying privacy policy, acquisitions, or managing permissions across BUs.

[!UICONTROL Segment Match] helps disparate marketing teams across massive organizations collaborate more efficiently, while continuing to operate independently

## Architecture

![Segment Match Architecture](assets/architecture-segment-match.png){zoomable="yes"}

[!UICONTROL Segment Match] is not a data marketplace where data can be purchased. Rather, it's an AEP feature that works with first-party data with select partners, using privacy and consent controls to help collaborate. [!UICONTROL Segment Match] helps focus efforts on improving customer relationships and growing the brand. It is beneficial where pre-existing brands or partner relationships exist. [!UICONTROL Segment Match] experience is easy to manage, scalable, and allows for administrators to share segments in an opt-in, controllable manner.

[!UICONTROL Segment Match] enables:

* Segment membership data to be ported securely across organizations using standard people-level identifiers, like hashed email or phone number
* An audience sharing UI and workflows with notifications
* Pre-shared overlap estimates
* Self-serve partner setup
* Overlaps on select standardized namespaces (hashed email, hashed phone, ECID, IDFA, GAID)
* Data sharing consent enforcement
* Shared audience lifecycle management
* DULE enforcement in sharing workflow
* Daily batch updates

[!UICONTROL Segment Match] allows to create inter-connected customer experience. The durable identifiers supported are hashed emails, hashed phone numbers and identifiers like ECID, IDFA and GAID. Customers can build feeds that match and move audience data between brand sandboxes, with strong governance, transparency, and revoke capabilities for use in advertising and marketing activations

## Pre-requisites

The pre-requisites for [!UICONTROL Segment Match] are:

* RT-CDP active licensed
* Standard hashed identifiers supported are SHA256 hashed email, hashed phone, ECID, Apple IDFA and GAID
* Privacy Framework and Consent strategy
* Data share agreements in place between the customers

## Security

### RBAC

The [!UICONTROL Segment Match] flow to manage partners is secured by RBAC. Only individuals with the right permission can initiate, accept, or manage partners. This can be done in the Data Ingestion section of the Product Profile. The following permissions are required:

![Audience Share Connection](assets/data-ingestion.png){zoomable="yes"}

|Permission |Description |
|---|---|
|**Manage Audience Share Connections**|This permission allows you to complete the partner handshake process, which connects two IMS Organizations to enable [!UICONTROL Segment Match] flows.|
|**Manage Audience Shares**|This permission allows you to create, edit, and publish feeds (the package of data used for [!UICONTROL Segment Match]) with active partners (partners who have been connected by the admin user with **Audience Share Connections** access).|

Refer the [official documentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/overview.html?lang=en#understanding-segment-match-permissions) to learn more about the permissions.

### Connect ID

The partner connect process is managed by the **[!UICONTROL Connect ID],** which is a randomly generated identifier that maps to a specific AEP sandbox. This Connect ID is required to initiate and manage partner sandboxes. There is also the ability to regenerate Connect ID to reconfigure a partner connection, if needed.

### Governance

Any dataset or data attributes with *C11* contract label are restricted for the [!UICONTROL Segment Match] service. Segments using those attributes cannot be used for [!UICONTROL Segment Match]. This provides the control on which segments can or cannot be used for [!UICONTROL Segment Match]. In addition, custom policies and marketing actions created are also enforced. By default, policies are disabled and need to be enabled for enforcement. Restrictions like email marketing and onsite advertising that are chosen while sharing segments are also propagated and shared with the partners.

### Consent

The consent settings for [!UICONTROL Segment Match] can be managed in the following ways:

* At the organization level, during onboarding, using the opt-out or opt-in setting for consent checks. 

    This setting determines if user data can be shared or not. The default is set to opt-out indicating user data can be shared with the assumption that the AEP customer already has the required consent agreement for data sharing use. This setting can be changed to opt in by contacting the Adobe Account Manager, putting an extra check in place to force AEP customers to explicitly track consent.

* Setting the share attribute specific to identities (idSpecific) using the [Consents and Preferences Field Group](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/consents.html?lang=en). 

    This field group provides a single object-type field, consents, to capture consent and preference information. [!UICONTROL Segment Match], by default, will include all identities that have not been explicitly opted out, example:

    ```
    "share": {
    `                `"val": "n"
    `     `}
    ```

    This setting can be changed by contacting the Adobe Account Manager, to only include     identities with explicit opt-in, example:

    ```
    "share": {
    `                `"val": "y"
    `     `}
    ```

### Alerts

Alerts are generated when a partner connection is initiated or when segment feeds are shared with partners.

## Setup workflow

The workflow for setting up partner connection is managed with the RBAC as mentioned above. With the right permissions in place, connection to a partner sandbox requires the Connect ID of that sandbox/instance within the partner's org to be shared. 

Once a connection is requested from the sending partner, it must be approved at the receiving side to ensure a safe and secure partner setup. The partner connection handshake ensures that the agreement exists between the two organizations and allows Adobe to facilitate the [!UICONTROL Segment Match] process on the organization's behalf. With the connection approved and in active state, the segment sharing process can be initiated from either side.

### Segment sharing

Segment sharing with partner happens only when a match exists on the selected identifier. There can be a one-to-many partner relationship, which means segments can be shared with multiple partners. 

To initiate segment sharing after the partner connection is set up, the sending partner should create a feed. Then, select the marketing use cases or actions that the segment data should be excluded from along with the durable identifiers. Relevant segments can then be added to the feed for sharing.  

As part of this segment-sharing workflow, the sending partner can discover potential high-value segments via estimated overlaps before any data is moved. 

The overall process flow is: 

![Segment sharing](assets/segment-sharing.png){zoomable="yes"}

These overlap estimates offer key insights, partner discovery, and data to fuel data collaboration agreements. No customer or segment data is moved across sandboxes to obtain these overlap estimate metrics. The customer-selected, pre-hashed applicable identities in any given sandbox are added to a probabilistic data structure that allows Adobe to perform union and intersection operations between them. These operations help [!UICONTROL Segment Match] get the estimated intersection of two data structures composed of identities from two different sandboxes without having to compare the actual values

The identity overlap process depends on the **daily full profile export** dataset from both sender and receiver sandboxes to identify common profiles that belong to the shared segments. The detailed process flow for the overlap process is shown below:

![Identity overlap process](assets/overlap-process.png){zoomable="yes"}

After segment sharing is complete from the sending partner, the receiver gets a notification about the segment feed shared. This segment feed must be enabled for profile at the receiver to initiate the segment membership dataflow. Only segment membership is ingested into the receiver IMS Organization's overlapping profile fragments and no additional identity is transferred from the sender to the receiver. 

The shared segment is available under the `AEPSegmentMatch` section of the **[!UICONTROL Audiences]** tab in the **[!UICONTROL Segment Builder]** and can be used for inclusion or suppression of audiences while building segments in the receiver sandbox.

Daily overlap process keeps the segment membership in sync between the sender and receiver. The receiver can disable profile for the segment feed received to pause the segment sharing process.

#### Segment exit/entry

As part of the full profile export, the status for the shared segment-IDs under the segment membership for profiles have one of the corresponding values - _realized_, _exited_, or _existing_ to reflect the current state. 

During the daily identity overlap process, if the corresponding identity exists in the receiver sandbox, these segment membership statuses for shared segments are sent across to the receiver for ingestion.

#### Segment revocation

Segment revocation/deletion from the sender is an on-demand process where the list of all profiles with the revoked segment-IDs are obtained from the receiver. The segment-IDs are removed from the segment membership of those identities and reingested at the receiver. This action overwrites the existing segment membership fragment, which deletes the membership for that segment.

## Use Segment Match in Programmatic Deals

With the growing restrictions around third-party cookies and device identifiers, programmatic advertising is looking for new ways to build and target audiences. A growing number of 'universal ID' solutions have been proposed however the industry is still in flux with no agreed upon, scalable way to achieve the same level of targeting while balancing applicable privacy concerns. 

You can use Adobe Experience Platform Segment Match in privacy-centric audience collaboration and enhance programmatic private deals between advertisers and publishers. With Segment Match, you can:

* Split **Ad trafficking** and **Audience** workflows.
* Allow partner brands to share audience metadata for mutually shared, and consenting identities using durable identifiers such as hashed email and hashed phone number within a consent-enforced process.

### Use cases

* Targeting first-party audiences through programmatic private deals.
* Suppression of first-party audience via programmatic private deals.
* Targeting look-alike audiences from first-party audiences seeded via programmatic private deals.

>[!BEGINSHADEBOX]

**Consider the following example workflow between a brand (Luma) and a media network (ACME):**

1. A brand (Luma) conducts an audience match with a media network (ACME) via Segment Match.
2. ACME pushes the audience(s) to ad server or Programmatic SSP via Adobe Real-Time CDP Destination(s).
3. ACME sets up a Private Inventory Deal (ID) with the applicable targeting criteria, including the audience established in the previous step. The Private Inventory Deal ID is then pushed to Luma's DSP.
4. Luma sets up a Private Inventory Deal and traffic campaign/ad creative.
5. The campaign then delivers via programmatic Private Inventory Deal.
6. Next, the ad server or SSP delivers ad impressions that meet the established targeting criteria. (Additional targeting criteria, such as frequency capping, are available through ad server and/or DSP, depending on whether a Guaranteed deal or a Preferred deal was established in the agreement).
7. Traffic is driven to Luma's brand properties.
8. ACME then shares back the post-campaign insights or audiences via Segment Match for re-targeting.

>[!ENDSHADEBOX]

![A diagram of the workflow between brand and publisher.](./assets/segment-match-blueprints.png)

>[!IMPORTANT]
>
> While the solution outlined above provides an easy way to target first-party data via programmatic private deals, there may be some considerations before executing, including, but not limited to the following examples:
>
>* Consent: Applicable consent collection by the brand, publisher, or retail media network, to leverage data in this manner.
>
>* Policies amd License agreements: Adherence to any applicable policies (including privacy policies, third-party vendor agreements) by the brand, publisher, or retail media network, to leverage and activate data in this manner.



## More information

* [Segment Match](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/overview.html?lang=en#) 
* [Permissions](https://experienceleague.adobe.com/docs/experience-platform/access-control/home.html?lang=en)
* [Trouble shooting](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/troubleshooting.html?lang=en)
* [XID](https://experienceleague.adobe.com/docs/experience-platform/identity/api/list-native-id.html?lang=en)
