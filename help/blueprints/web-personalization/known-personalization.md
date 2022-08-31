---
title: Web/Mobile Personalization Overview
description: Synchronize web personalization with email and other known and anonymous channel personalization.
landing-page-description: Synchronize web personalization with email and other known and anonymous channel personalization.
solution: Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection, Experience Platform
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
---

# Web/Mobile Personalization with known customer data

## Use Cases

* Online personalization with known customer data
* Landing page optimization
* Personalization based on prior product/content views, product/content affinity, environmental attributes, and demographics in addition to offline data such as transactions, loyalty and CRM data, and modeled insights
* Share and target audiences defined in Real-time Customer Data Platform on websites and mobile apps using Adobe Target.

## Applications

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (optional): Adds third-party audience data.
* Adobe Analytics or Customer Journey Analytics(optional): Adds the ability to build segments based on historical customer and behavioral data with fine grained segmentation

## Integration Patterns

| Integration Pattern | Capability |  Pre-Requisites |
|---|---|---|
|Real-time segment evaluation on the Edge shared from Real-time Customer Data Platform to Target|<ul><li>Evaluate audiences in real-time for same or next page personalization on the Edge.</li><li>In addition, any segments evaluated in streaming or batch fashion will also be projected to the Edge Network to be included in edge segment evaluation and personalization.</li></ul>|<ul><li>Web/Mobile SDK must be implemented or the Edge Network Server API</li><li>Datastream must be configured in Experience Edge with the Target and Experience Platform extension enabled</li><li>Target destination must be configured in Real-time Customer Data Platform Destinations.</li><li>Integration with Target requires the same IMS Org as the Experience Platform instance.</li></ul>|
|Streaming and batch audience sharing from Real-time Customer Data Platform to Target via the Edge approach|<ul><li>Share streaming and batch audiences from Real-time Customer Data Platform to Target through the Edge Network. Audiences evaluated in real-time require the WebSDK and Edge Network implementation.</li></ul>|<ul><li>Web/Mobile SDK is not required for sharing of streaming and batch audiences to Target though it is required to enable real-time edge segment evaluation.</li><li>If using AT.js, only profile integration against the ECID identity namespace is supported.</li><li>For custom identity namespace lookups on the Edge, the WebSDK/Edge API deployment is required and each identity must be set as an identity in the identity map.</li><li>Target destination must be configured in Real-time Customer Data Platform Destinations, only the production sandbox in RTCDP is supported.</li><li>Integration with Target requires the same IMS Org as the Experience Platform instance.</li></ul>|
|Streaming and batch audience sharing from Real-time Customer Data Platform to Target and Audience Manager via the Audience Sharing Service Approach|<ul><li>This integration pattern can be leveraged when additional enrichment from 3rd party data and audiences in Audience Manager is desired.</li></ul>|<ul><li>Web/Mobile SDK is not required for sharing of streaming and batch audiences to Target though it is required to enable real-time edge segment evaluation.</li><li>If using AT.js, only profile integration against the ECID identity namespace is supported.</li><li>For custom identity namespace lookups on the Edge, the WebSDK/Edge API deployment is required and each identity must be set as an identity in the identity map.</li><li>Audience projection via audience sharing service must be provisioned.</li><li>Integration with Target requires the same IMS Org as the Experience Platform instance.</li><li>Only audiences from the prod sandbox support the audience sharing core service.</li></ul>|

## Real-time, Streaming, and Batch Audience Sharing to Adobe Target

Architecture

<img src="assets/RTCDP+Target.png" alt="Reference architecture for the Online/Offline Web Personalization Blueprint" style="width:90%; border:1px solid #4a4a4a" />

Sequence Detail

<img src="assets/RTCDP+Target_flow.png" alt="Reference architecture for the Online/Offline Web Personalization Blueprint" style="width:90%; border:1px solid #4a4a4a" />

Overview Architecture

<img src="assets/personalization_with_apps.png" alt="Reference architecture for the Online/Offline Web Personalization Blueprint" style="width:90%; border:1px solid #4a4a4a"/>

## Implementation Patterns

Known Customer Personalization is supported via several implementation approaches.

### Implementation Pattern 1 - Edge Network with Web/Mobile SDK or Edge Network API (Recommended Approach)

* Using the Edge Network with the Web/Mobile SDK. Real-time edge segmentation requires the Web/Mobile SDK or Edge API implementation approach.
* [Refer to the Experience Platform Web and Mobile SDK Blueprint](../data-ingestion/websdk.md) for the SDK based implementation.
* For use in the Mobile SDK the [Adobe Journey Optimizer - Decisioning extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer-decisioning) must be installed in the Mobile SDK.
* [Refer to the Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html) for an API based implementation of Adobe Target with Edge Profile.

### Implementation Pattern 2 - Application specific SDKs

Using traditional application-specific SDKs (for example, AT.js and AppMeasurement.js). Real-time Edge segment evaluation is not supported using this implementation approach. However streaming and batch audience sharing from Experience Platform hub are supported using this implemenation approach.

[Refer to the application specific SDK Blueprint](../data-ingestion/appsdk.md) 

### Implementation Steps

1. [Implement Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html) for your web or mobile applications
1. [Implement Experience Platform and [!UICONTROL Real-time Customer Profile]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html) ensure that audiences created are activated to the Edge by configuring the applicable [merge policy](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=en#create-a-merge-policy) as active on the Edge. 
1. Implement [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) or the [Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/) with the correct extension (Target or Adobe Journey Optimizer - Decisioning) installed. Experience Platform Web/Mobile SDK or EDGE API are required for real-time Edge segmentation, but not required for sharing of streaming and batch audiences from Real-time Customer Data Platform to Target.
1. [Configure the Edge Network with a Edge Datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)
1. [Enable Adobe Target as a destination within Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en)
1. (Optional) [Implement Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html).
1. (Optional) [Request provisioning for Audience Sharing between Experience Platform and Adobe Target (Shared Audiences)](https://www.adobe.com/go/audiences) to share audiences from Experience Platform to Target.

## Guardrails

[Refer to the guardrails on the Web and Mobile Personalization Blueprints Overview page.](overview.md)

## Implementation Considerations

Identity pre-requisites

* Any primary identity can be leveraged when utilizing implementation pattern 1 outlined above with the Edge network and WebSDK. First login personalization requires the personalization request set primary identity match the primary identity of the profile from Real-time Customer Data Platform. Identity stitching between anonymous devices and known customers is processed on the hub and subsequently projected to the edge.
* Note that data uploaded to the hub prior to a consumer visiting or logging into a website will not be immediately available for personalization. An active edge profile must first exist for hub data to be synced to. Once created the edge profile will sync with the hub profile asynchronously resulting in next page personalization. 
* Sharing audiences from Adobe Experience Platform to Adobe Target requires the use of ECID as a identity when using the audience sharing service as outlined in integration patter 2 and 3 above.
* Alternate identities can be used to share Experience Platform audiences to Adobe Target via Audience Manager as well. Experience Platform activates audiences to Audience Manager via the following supported namespaces: IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Note that Audience Manager and Target resolve audience memberships via the ECID identity, so ECID is still required to be in the identity graph for the consumer for the final audience sharing to Adobe Target.  

## Related Documentation

### SDK Documentation

* [Experience Platform Web SDK documentation](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Experience Platform Tags documentation](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)
* [Experience Cloud ID Service documentation](https://experienceleague.adobe.com/docs/id-service/using/home.html)

### Connection Documentation

* [Adobe Target Connection for Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en)
* [Edge Datastream Configuration](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)
* [Experience Platform segment sharing with Audience Manager and other Experience Cloud solutions](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html)

### Segmentation Documentation

* [Experience Platform Segmentation Overview](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html)
* [Real-time Segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html)
* [Streaming Segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Adobe Analytics Segment Sharing through Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)
* [Merge Policy Configuration](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=en#create-a-merge-policy)

### Tutorials

* [Next-hit personalization with Real-time CDP and Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=en)

### Related Blog Posts

* [Adobe announces Same Page Enhanced Personalization with Adobe Target and Real-time Customer Data Platform](https://blog.adobe.com/en/publish/2021/10/05/adobe-announces-same-page-enhanced-personalization-with-adobe-target-real-time-customer-data-platform)
* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Adobe Experience Platform’s Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
