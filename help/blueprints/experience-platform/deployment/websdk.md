---
title: Web/Mobile SDK, [!DNL Edge Network] Deployment architecture diagram
description: This blueprint shows the architecture and ingestion through the Experience Platform Web and Mobile SDK and [!DNL Edge Network]
solution: Experience Platform,Data Collection
kt: null
thumbnail: null
exl-id: 3cc9e849-a75d-40ad-a604-6acf4c2c9f89
TQID: https://experienceleague.adobe.com/s56Vkgc-UvIUNPhcB8x3WFlzhfeEUpRxXZCMu0zf58Y
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
feature_v2:
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
    internal-label: Data collection
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
---
# Experience Platform Web SDK & [!DNL Edge Network] architecture diagram

For an overview and detail on the Web and Mobile SDK, and the [!DNL Edge Network] Server API see the following.

* [Web SDK overview](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
* [Mobile SDK overview](https://developer.adobe.com/client-sdks/documentation/)
* [[!DNL Edge Network] Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html)

For a detailed outline of what application functionality is supported in the Web SDK see the following documentation.

* [Web SDK application functionality support](https://github.com/orgs/adobe/projects/18/views/1)

For details related to migration from application specific SDKs to the Web and Mobile SDKs see the following documentation.

* [Identity Services](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/overview.html)
* [Analytics](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/adobe-analytics/analytics-overview.html)
* [Target](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/target-overview.html)
* [Analytics for Target](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/adobe-target/a4t/overview.html)

## Experience Platform Web/Mobile SDK or [!DNL Edge Network] Server API deployment

The below architecture diagram illustrates the deployment and data collection utilizing the Experience Platform Web SDK.

<img src="assets/web_sdk_flow.svg" alt="Reference architecture for implementation using the Experience Platform Web and Mobile SDK" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

Sequence Diagram of Experience Edge, Experience Platform Services, and Applications

<img src="assets/web_sdk_sequence.svg" alt="Reference architecture for the Online/Offline Web Personalization Blueprint" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## Reference documentation

* [Implement Adobe Experience Cloud with Web SDK tutorial](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html)
* [Implement Adobe Experience Cloud in mobile apps tutorial](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html)
