---
title: Audience and Profile Activation with Experience Cloud Applications blueprint
description: Manage profiles and audiences in Experience Platform and share them with Experience Cloud applications.
solution: Real-Time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services
kt: 7722
exl-id: f36014e8-170d-47e1-b4ec-10c0ea70612d
---
# Audience and Profile Activation with Experience Cloud Applications blueprint

Manage profiles and audiences in Experience Platform and share them with Experience Cloud Applications. Build and share rich customer segments and insights in Experience Platform and share them with Experience Cloud applications.

Activation with Experience Cloud Applications aligns with the [Known Customer Activation blueprint](known.md).

## Use cases

* Personalize and target across customer interaction channels powered by Experience Cloud.
* Share audience and profile data between Experience Platform and Experience Cloud applications.
* Build rich insigths from multi-channel data including online behavioral data and data science models to enrich real-time customer profile in Experience Platform that can then be shared with Experience Cloud applications.

## Applications

* Adobe Experience Platform
* [!UICONTROL Real-time Customer Data Platform]
* Experience Platform Activation
* Experience Cloud Applications
    * Adobe Audience Manager
    * Adobe Target
    * Adobe Campaign
    * Journey Optimizer
    * Marketo Engage
    * Adobe Commerce
    * Customer Journey Analytics 
 
## Architecture

See the [Experience Platform and Applications Architecture Section](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-applications.html) for additional architecture diagrams related to Experience Platform integrations with Experience Cloud Applications.

### Audience and Profile Activation with Experience Cloud applications

<img src="../experience-platform/assets/aep+apps.svg" alt="Reference architecture for the Audience and Profile Activation with Experience Cloud applications" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />
<br>

## Guardrails

Refer to the [guardrails on the Audience and Profile Activation Overview page](overview.md) and the [deployment guardrails](../experience-platform/deployment/guardrails.md) page. 

## Implementation considerations

* Sharing profile data to destinations requires that you include the specific identity value used by the destination in the destination payload. Any identity that is necessary for a target destination must be ingested into Platform and configured as an identity for the [!UICONTROL Real-time Customer Profile].

### Audience sharing from Real-time Customer Data Platform to Audience Manager

* Refer to the following documentation for futher details. [Experience Platform segment sharing with Audience Manager and other Experience Cloud solutions](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html).

* Audience membership from RT-CDP is shared to Audience Manager in a streaming fashion as soon as segment evaluation is complete and written to the Real-time Customer profile, whether the segment evaluation occurred in batch or streaming. 
* If the qualified profile contains the regional routing information for related profile devices then the audience membership from RTCDP is qualified in streaming fashion on the associated Audience Manager Edge. If the regional routing information was applied to a profile with a timestamp in the past 14 days it will be evaluated on the Audience Manager Edge in streaming. If the profiles from RTCDP does not contain regional routing information or the regional routing information is greater than 14 days old, then the RTCDP audience memberships are sent to the Audience Manager hub location for batch based evaluation and activation. 
* With regional routing information these profiles are eligible for Edge activation and will activate within minutes of segment qualification from RTCDP, profiles that do not qualify for Edge activation will qualify in the Audience Manager hub and may have a 12-24 hour timeframe for processing. 
* Regional routing information for which Edge the Audience Manager profile is stored on can be collected to Experience Platform from Audience Manager, the Visitor ID Service, Analytics, Launch, or directly from the Web SDK as a separate profile record class dataset using the "data capture region information" XDM field group. See the get regional information document for further details [Link](https://experienceleague.adobe.com/docs/id-service/using/reference/regions.html?lang=en).
* For activation scenarios where audiences are shared from Experience Platform to Audience Manager the following identities are shared automatically: ECID, IDFA, GAID, hashed email addresses (EMAIL_LC_SHA256), AdCloud ID. Currently, custom namespaces are not shared.
* The audiences from Experience Platform can be shared through Audience Manager destinations when the required destination identities are included in the [!UICONTROL Real-time Customer Profile], or where identities in the [!UICONTROL Real-time Customer Profile] can be related to the required destination identities that are linked in Audience Manager.

### Audience sharing from Real-time Customer Data Platform to Target

* See the [Known Customer Personalization - Target & RTCDP Blueprint](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/web-personalization/known-personalization.html) for additional details on sharing profiles and audiences from Real-time Customer Data Platform to Target.

### Audience sharing from Real-time Customer Data Platform to Campaign and Journey Optimizer

* See the [Customer Journeys Blueprints](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=en) for additional details on sharing profiles and audiences from Real-time Customer Data Platform to Campaign and Journey Optimizer.

### Audience sharing from Real-time Customer Data Platform to Marketo Engage

* See the [B2B Activation Blueprints](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=en) for additional details on sharing profiles and audiences from Real-time Customer Data Platform to Marketo Engage.

### Audience sharing from Real-time Customer Data Platform to Customer Journey Analytics

* See the [RTCDP audiences shared with Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/ingest-aep-segments.html?lang=en) for additional details on shareing Real-time Customer Data Platform audiences to Customer Journey Analytics.

## Related documentation

* [[!UICONTROL Real-time Customer Data Platform] Product Description](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Profile and segmentation guidelines](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Segmentation documentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Destinations documentation](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## Related videos & tutorials

* [[!UICONTROL Real-time Customer Data Platform] overview](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo of [!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Create segments](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
