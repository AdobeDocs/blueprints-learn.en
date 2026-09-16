---
title: RTCDP + Target Integration Overview
description: Understand how Real-Time Customer Data Platform audiences and profile context integrate with Adobe Target through the Edge Network.
landing-page-description: Understand how Real-Time Customer Data Platform audiences and profile context integrate with Adobe Target through the Edge Network.
short-description: Understand how Real-Time Customer Data Platform audiences and profile context integrate with Adobe Target through the Edge Network.
solution: Real-Time Customer Data Platform, Target, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
TQID: https://experienceleague.adobe.com/1ti2SqfAFOgnKbaJ70xwGI-xHDE1WXJ7-oTStcJJy1E
product_v2:
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
    internal-label: Real-Time Customer Data Platform
feature_v2:
  - id: a37e4ecd-c740-426a-addf-cb1b483c5c5a
    internal-label: Segmentation
  - id: adee20bd-51f4-461d-b9db-d215f8756eeb
    internal-label: Audiences
  - id: ba929a52-9339-4154-9487-317dc875a3c7
    internal-label: Use cases
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
    internal-label: Implementation
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
subfeature_v2:
  - id: cbd4a8d8-97a6-4ac9-b8d6-b6c1f28d3342
    internal-label: Segments
  - id: cdd3e38b-fec2-4f39-8b10-83ddaab1ac16
    internal-label: B2B
  - id: d1823595-9241-4128-8a33-e4ac3bf08773
    internal-label: Audiences
  - id: ee602049-8a18-43df-9299-a689a025a371
    internal-label: Use cases
  - id: fd0ff162-b6d3-4a11-8aeb-e165a01c0f0a
    internal-label: at.js
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
    internal-label: Measurement
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
---
# RTCDP + Target Integration Overview

This architecture shows how [!DNL Real-Time Customer Data Platform] and [!DNL Adobe Target] integrate through the Edge Network. It helps you select between real-time audience evaluation at the edge and sharing streaming or batch audiences with Target.

## Applications

* [!DNL Real-Time Customer Data Platform]
* [!DNL Adobe Target]
* [!DNL Experience Platform] Edge Network
* Experience Platform Web SDK or Edge Network Server API

## Choose an integration approach

### Real-time audience evaluation at the edge

Use this approach when [!DNL Adobe Target] needs edge-evaluated audiences and profile attributes for same-page or next-page personalization. Implement the Web SDK or Edge Network Server API and configure a datastream with the [!DNL Adobe Target] and [!DNL Experience Platform] services enabled.

### Streaming and batch audience sharing to Target

Use this approach when audiences evaluated in [!DNL Real-Time Customer Data Platform] need to be available in [!DNL Adobe Target] without real-time edge evaluation. Configure the [!DNL Adobe Target] destination in the default production sandbox. Web SDK or Edge Network Server API implementation is required only for real-time edge evaluation or custom identity namespace lookups.

## Architecture diagram

This diagram shows the primary integration points among data collection, the Edge Network, [!DNL Real-Time Customer Data Platform], and [!DNL Adobe Target].

<img src="assets/RTCDP-Target.png" alt="Architecture for Real-Time Customer Data Platform and Adobe Target integration" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Data flow diagram

This sequence shows how a client request reaches the Edge Network, evaluates audiences and profile context, sends a personalization request to [!DNL Adobe Target], and returns the resulting experience to the client.

<img src="assets/RTCDP-Target_flow.png" alt="Data flow for Real-Time Customer Data Platform and Adobe Target integration" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Implementation considerations

* [!DNL Adobe Target] and [!DNL Real-Time Customer Data Platform] must use the same IMS organization.
* The [!DNL Adobe Target] destination supports the default production sandbox in [!DNL Real-Time Customer Data Platform].
* For custom identity namespace lookups at the edge, use Web SDK or Edge Network Server API and include each identity in the identity map.
* If using at.js, profile integration supports only the ECID identity namespace.

## Related documentation

### Configure the integration

* [Adobe Target Connection for Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html)
* [Edge datastream configuration](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)

### Implement at the edge

* [Experience Platform Web SDK documentation](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Experience Platform Tags documentation](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)
* [Experience Cloud ID Service documentation](https://experienceleague.adobe.com/docs/id-service/using/home.html)

### Evaluate audiences

* [Experience Platform Segmentation Overview](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html)
* [Real-time Segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html)
* [Streaming Segmentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Merge Policy Configuration](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=en#create-a-merge-policy)
