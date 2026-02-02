---
title: Real-time Edge Profile Access for Web and Mobile Personalization
description: "[!UICONTROL Real-time Customer Profile] access at the edge to provide context for real-time web and mobile personalization."
solution: Real-Time Customer Data Platform, Data Collection
kt: 719
---
# Real-time Edge Profile Access for Web and Mobile Personalization

Real-time Edge Profile Access for Web and Mobile Personalization blueprint shows how web and mobile applications can access Adobe Experience Platform's [!UICONTROL Real-time Customer Profile] at the edge for high-throughput, low-latency personalization.

Applications can access real-time profile attributes and audiences at the edge with millisecond latency. Attributes, audience memberships, and model-driven features stored in the profile as attributes can be accessed in real-time for same-page and next-page personalization across web and mobile channels.

With this capability, you can deliver highly personalized experiences on your websites and mobile applications based on the Real-time Customer Profile, including audiences derived from real-time behaviors, attributes ingested into the Real-time Customer Profile, and calculated insights.

>[!NOTE]
>
>Edge profile access is specifically designed for high throughput, low latency use cases such as web/mobile inbound personalization and real-time offer decisioning. For lower throughput scenarios such as agent assisted support or sales interactions, the Hub profile lookup API is more appropriate. See the [Real-time Profile Access for Support and Sales Scenarios blueprint](customer-activity.md) for hub-based profile access.

## Applications

* Real-time Customer Data Platform
* Adobe Experience Platform Data Collection (Web SDK / Mobile SDK)
* Edge Network Server API

## Use cases

* Real-time personalization on web and mobile channels for known customer experiences
* Same-page and next-page personalization based on real-time profile attributes and audiences
* Content and offer personalization based on customer profiles including real-time behavioral data, attributes, and calculated insights
* Integration with personalization engines, content management systems, and external applications for real-time decisioning
* Testing and content optimization with real-time profile context

## Prerequisites

This blueprint requires the use of one of the following data collection methods if you would like the profile to be updated in real-time with streaming data. It is possible to get real-time access the Edge Profile without having to collect data directly to the Edge Profile; data can be collected to the Hub and projected to the Edge Profile as well. Note that there will be added latency for data collected to the Hub and then projected to the Edge.

* Use the [Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html) if you want to collect data from your website.
* Use the [Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/) if you want to collect data from your mobile application.
* Use the [Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html) if you are not using the Web SDK or Mobile SDK, or are implementing a more direct server to server connection.

>[!IMPORTANT]
>
>Before implementing edge personalization, read the guide on how to [activate audience data to edge personalization destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations). This guide takes you through the required configuration steps for same-page and next-page personalization use cases, across multiple Experience Platform components.

## Architecture Diagram

<img src="assets/real-time-edge-lookup.svg" alt="Reference Architecture for Edge Profile Access for Web and Mobile Personalization" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## Guardrails

* [Guardrails for [!UICONTROL Real-time Customer Profile] data](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
* [Edge Network Guardrails](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* Edge profiles have a 14-day time-to-live (TTL). If a user has not been active on the edge for 14 days, the edge profile may expire and need to be fetched from the hub, which may impact first-page personalization.
* Edge personalization supports real-time audience membership evaluation for audiences that meet edge segmentation criteria. Batch and streaming audiences from the hub are also available at the edge with appropriate configuration.

## Implementation patterns

Edge personalization can be implemented using the [Custom Personalization Connection](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) destination in Real-time Customer Data Platform. This destination supports multiple data collection methods depending on your use case.

### Pattern 1: Audience membership-based personalization with Web SDK / Mobile SDK

* Use the Adobe Experience Platform Web SDK or Mobile SDK with the Edge Network for audience membership-based personalization.
* This approach provides low latency and best performance for edge personalization based on audience memberships.
* Real-time edge segmentation requires the Web/Mobile SDK implementation.
* Web SDK and Mobile SDK **alone support personalization based on audience membership only**.
* [Refer to the Experience Platform Web and Mobile SDK Blueprint](../experience-platform/deployment/websdk.md) for SDK-based implementation.
* For Mobile SDK implementation, the [Adobe Journey Optimizer - Decisioning extension](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/) must be installed in the Mobile SDK.

### Pattern 2: Attribute-based personalization with Edge Network Server API (Required for Profile Attributes)

>[!IMPORTANT]
>
>**Attribute-based personalization requirements:** If you want to personalize based on profile attributes (not just audience membership), you **must** use the [Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html) with authenticated server-side integration, regardless of whether you are also using Web SDK or Mobile SDK for data collection.

* Enables integration with third-party personalization engines and CDN-based personalization.
* The Edge Network Server API is **required** to securely retrieve profile attributes for personalization.
* You can retrieve profile attributes via the Edge Network Server API by adding a server-side integration that utilizes the same datastream that you are already using for your Web or Mobile SDK implementation.
* All Edge Network Server API calls for profile attributes must be made in an authenticated context to protect sensitive data.
* This pattern enables both audience membership-based personalization and attribute-based personalization.
* Appropriate for server-side personalization use cases, API-based integrations, and scenarios requiring profile attribute access.

## Implementation steps

1. [Create schemas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) for data to be ingested.
1. [Create datasets](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) for data to be ingested.
1. [Configure the correct identities and identity namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html) on the schema to ensure that ingested data can stitch into a unified profile.
1. [Enable the schemas and datasets for profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Ingest data](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) into Experience Platform.
1. [Set up merge policies](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) to ensure correct identity stitching and profile merging.
1. [Configure a datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html) in Experience Platform Data Collection with the destination configuration enabled. The datastream determines in which Data Collection datastream the audiences will be included in the response to the page.
1. Implement [Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html) or [Mobile SDK](https://developer.adobe.com/client-sdks/home/) on web and mobile properties for data collection.
1. Configure edge segmentation for audiences that require real-time evaluation. [Edge segmentation documentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html).
1. In the Destinations catalog, set up the [Custom Personalization Connection](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) destination:
1. [Activate audiences to the edge personalization destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations). Select which audiences you want to activate to the destination.
1. (Optional for attribute-based personalization) If you need to personalize based on profile attributes in addition to audience membership, implement the [Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html) with authenticated server-side integration using the same datastream. This is **required** for accessing profile attributes.
1. Implement personalization logic in your web/mobile application to consume the exported audience data and profile attributes:
    * If using Tags in Adobe Experience Platform, use the [send event complete functionality](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html) to access `event.destinations` variable with the exported data.
    * If not using Tags, use [command responses](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html) to parse the JSON response from Adobe Experience Platform and retrieve audience IDs and profile attributes.

## Implementation considerations

### Identity considerations

* Any primary identity can be used for edge personalization when using the Web SDK or Mobile SDK with the Edge Network.
* For first login personalization with known customer data, the personalization request must use a primary identity that matches the known customer identity in Real-time Customer Data Platform. If the primary ID is set to ECID or an anonymous identity that has not yet been stitched with the known customer profile, it will take time for the identity stitch to be realized, which may impact the availability of historical profile data for personalization.
* Edge profiles must be initialized before they can be used for personalization. First-time visitors or returning visitors whose edge profile has expired (14-day TTL) may experience initial personalization based on limited profile data until the edge profile is fully populated.

### Attribute-based personalization

>[!IMPORTANT]
>
>Profile attributes may contain sensitive data. To protect this data, you **must** use the [Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html) when configuring the Custom Personalization destination for attribute-based personalization. All Edge Network Server API calls must be made in an authenticated context.

* For attribute-based personalization using profile attributes, you must add a server-side integration with the Edge Network Server API that utilizes the same datastream you are using for your Web or Mobile SDK implementation.
* You must configure which profile attributes to include in the edge projection through the Custom Personalization Connection destination configuration.
* **Web SDK and Mobile SDK alone only support personalization based on audience membership**. The Edge Network Server API is **required** to securely retrieve profile attributes for personalization.
* If you do not implement the Edge Network Server API for attribute access, personalization will be based on audience membership only.
* The API response for Custom Personalization with Attributes includes an `attributes` section in addition to the audience segments.

### Audience considerations

* Audiences evaluated through streaming or batch segmentation on the hub are projected to the edge and can be used for personalization.
* Audiences that meet edge segmentation criteria are evaluated in real-time on the edge for same-page personalization.
* Configure appropriate audiences for edge evaluation based on their use in real-time personalization use cases.

## Related documentation

### Destination configurations

* [Custom Personalization Connection](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) - Primary implementation guide
* [Personalization destinations overview](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/overview)
* [Activate audiences to edge personalization destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)
* [Look up profile attributes on the edge in real-time](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-profile-lookup)

### SDK documentation

* [Experience Platform Web SDK documentation](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html)
* [Experience Platform Mobile SDK documentation](https://developer.adobe.com/client-sdks/home/)
* [Edge Network Server API documentation](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html)
* [Experience Platform Tags documentation](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)
* [Command Responses in Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html)

### Profile and segmentation documentation

* [[!UICONTROL Real-time Customer Profile] documentation](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)
* [Profile Guardrails](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

### Tutorials

* [Next-hit personalization with Real-Time CDP and Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html)
* [Datastream Configuration](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html)
