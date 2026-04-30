---
title: Real-time Edge Profile Access for Web and Mobile Personalization
description: '[!UICONTROL Real-time Customer Profile] access at the edge to provide context for real-time web and mobile personalization.'
solution: Real-Time Customer Data Platform, Data Collection
kt: 719
exl-id: 61b81d00-c4bd-41b2-8161-683814947b56
---
# Real-time Edge Profile Access for Web and Mobile Personalization

>[!TIP]
>This blueprint is also available as a [use case pattern](/help/blueprints/use-case-patterns/personalization/edge-profile-access.md) under Personalization.

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

## Architecture Diagram

<img src="assets/real-time-edge-lookup.svg" alt="Reference Architecture for Edge Profile Access for Web and Mobile Personalization" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## Guardrails

* [Guardrails for [!UICONTROL Real-time Customer Profile] data](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
* [Edge Network Guardrails](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* Edge profiles have a 14-day time-to-live (TTL). If a user has not been active on the edge for 14 days, the edge profile may expire and need to be fetched from the hub, which may impact first-page personalization.
* Edge personalization supports real-time audience membership evaluation for audiences that meet edge segmentation criteria. Batch and streaming audiences from the hub are also available at the edge with appropriate configuration.

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
