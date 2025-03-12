---
title: Real-time Customer Data Platform & Adobe Target
description: Integrate RTCDP profiles and audiences with Adobe Target.
landing-page-description: Integrate RTCDP profiles and audiences with Adobe Target.
short-description: Integrate RTCDP profiles and audiences with Adobe Target.
solution: Real-Time Customer Data Platform, Target, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
---

# Real-time Customer Data Platform integration with Adobe Target

## Use cases

* Online personalization with known customer data
* Landing page optimization
* Personalization based on prior product/content views, product/content affinity, environmental attributes, and demographics in addition to offline data such as transactions, loyalty and CRM data, and modeled insights
* Share and target audiences defined in Real-time Customer Data Platform on websites and mobile apps using Adobe Target

## Applications

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target

### Reference documentation

* [Adobe Target Connection for Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html)
* [Edge Datastream Configuration](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)

## Integration patterns

| Integration Pattern | Capability | Pre-Requisites |
|--------------------|------------|---------------|
| **Real-time segment evaluation on the Edge shared from Real-time Customer Data Platform to Target** | - Evaluate audiences in real-time for same or next page personalization on the Edge. <br>- Any segments evaluated in streaming or batch fashion will also be projected to the Edge Network to be included in edge segment evaluation and personalization. | - Web/Mobile SDK must be implemented or the Edge Network Server API. <br>- Datastream must be configured in Experience Edge with the Target and Experience Platform extension enabled. <br>- Target destination must be configured in Real-time Customer Data Platform Destinations. <br>- Integration with Target requires the same IMS Org as the Experience Platform instance. |
| **Streaming and batch audience sharing from Real-time Customer Data Platform to Target via the Edge approach** | - Share streaming and batch audiences from Real-time Customer Data Platform to Target through the Edge Network. <br>- Audiences evaluated in real-time require the Web SDK and Edge Network implementation. | - Web/Mobile SDK or Edge API implementation of Target is not required for sharing streaming and batch RTCDP audiences to Target but is required to enable real-time edge segment evaluation. <br>- If using AT.js, only profile integration against the ECID identity namespace is supported. <br>- For custom identity namespace lookups on the Edge, the Web SDK/Edge API deployment is required, and each identity must be set as an identity in the identity map. <br>- Target destination must be configured in Real-time Customer Data Platform Destinations, only the default production sandbox in RTCDP is supported. <br>- Integration with Target requires the same IMS Org as the Experience Platform instance. |
| **Streaming and batch audience sharing from Real-time Customer Data Platform to Target and Audience Manager via the Audience Sharing Service Approach** | - This integration pattern can be leveraged when additional enrichment from 3rd party data and audiences in Audience Manager is desired. | - Web/Mobile SDK is not required for sharing streaming and batch audiences to Target but is required to enable real-time edge segment evaluation. <br>- If using AT.js, only profile integration against the ECID identity namespace is supported. <br>- For custom identity namespace lookups on the Edge, the Web SDK/Edge API deployment is required, and each identity must be set as an identity in the identity map. <br>- Audience projection via audience sharing service must be provisioned. <br>- Integration with Target requires the same IMS Org as the Experience Platform instance. <br>- Only audiences from the default production sandbox support the audience sharing core service. |

## Real-time, streaming, and batch audience sharing to Adobe Target

Architecture

![Reference architecture for the Online/Offline Web Personalization Blueprint](assets/RTCDP+Target.svg)

Sequence Detail

![Reference architecture for the Online/Offline Web Personalization Blueprint](assets/RTCDP+Target_flow.svg)

Overview Architecture

![Reference architecture for the Online/Offline Web Personalization Blueprint](assets/personalization_with_apps.svg)

## Implementation patterns

Known Customer Personalization is supported via several implementation approaches.

### Implementation pattern 1 - [!DNL Edge Network] with Web/Mobile SDK or [!DNL Edge Network] API (Recommended Approach)

* Using the [!DNL Edge Network] with the Web/Mobile SDK. Real-time edge segmentation requires the Web/Mobile SDK or Edge API implementation approach.
* [Refer to the Experience Platform Web and Mobile SDK Blueprint](../experience-platform/deployment/websdk.md) for the SDK based implementation.
* For use in the Mobile SDK the [Adobe Journey Optimizer - Decisioning extension](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/) must be installed.
* [Refer to the [!DNL Edge Network] Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html) for an API based implementation of Adobe Target with Edge Profile.

### Implementation pattern 2 - Application specific SDKs

Using traditional application-specific SDKs (for example, AT.js and AppMeasurement.js). Real-time Edge segment evaluation is not supported using this implementation approach. However streaming and batch audience sharing from Experience Platform hub are supported using this implemenation approach.

[Refer to the Adobe Target Connector Documentation](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection)
[Refer to the application specific SDK Blueprint](../experience-platform/deployment/appsdk.md) 

## Implementation considerations

* Any primary identity can be leveraged when utilizing implementation pattern 1 outlined above with the [!DNL Edge Network] and Web SDK. 
* First login personalization with known customer data that was prior ingested into RTCDP requires that the personalization request has a primary identity which matches the known customer identity graph in the Real-time Customer Data Platform. If the primary ID is set to ECID or an identity that has not yet been stitched with the known customer profile, then it will take several minutes for the identity stitch to be realized on the edge and for edge personalization to include prior ingested known customer data.
* Edge profiles currently have a 14 day TTL. Hence if a user has not logged in or been active for 14 days on the edge, the profile on the edge may be expired, and thus the edge must fetch the profile from the hub to have the historic profile view to power personalization which includes prior ingested profile attributes and segments, this will result in personalization with the historic view of profiles happening on subsequent page views vs. the first login.

## Related documentation

### SDK documentation

* [Experience Platform Web SDK documentation](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Experience Platform Tags documentation](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)
* [Experience Cloud ID Service documentation](https://experienceleague.adobe.com/docs/id-service/using/home.html)

### Segmentation documentation

* [Experience Platform Segmentation Overview](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html)
* [Real-time Segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html)
* [Streaming Segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Adobe Analytics Segment Sharing through Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)
* [Merge Policy Configuration](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=en#create-a-merge-policy)

### Tutorials

* [Next-hit personalization with Real-Time CDP and Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=en)
