---
title: Adobe Commerce - RTCDP Blueprint
description: Adobe Experience Platform Integration with Adobe Commerce to create a single view of customers and intelligently personalize experiences on a digital storefront and across channels.
solution: Real-Time Customer Data Platform, Commerce
exl-id: e2fc5e1c-c865-4c24-9b82-861a34aba487
---
# Adobe Commerce & RTCDP

The [!DNL Data Connection] extension helps Adobe Commerce customers seamlessly intergrate with Adobe Experience Platform to enrich the customer profile and personalize experiences in digital storefront and other channels.

## Technical Capablities Enabled

* Storefront data (client side, such as add to cart, cart abandons, and so on) collected and sent into any Adobe Experience Cloud product.
* Back office order status to any Adobe Experience Cloud product
* Back office historical orders can be sent to Adobe Experience Platform
* Share and personalize RTCDP audiences to Adobe Commerce

## Pre-requisites

To use the [!DNL Data Connection] extension, you must have the following:

* Adobe Commerce 2.4.4 or newer
* Adobe ID and Organization ID
* Adobe Experience Platform/RTCDP
* [Adobe Client Data Layer (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). The ACDL is required to collect storefront event data.

## Onboarding steps

### Data Collection from Adobe Commerce to Adobe Experience Platform

* [Install](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/install.html) the [!DNL Data Connection] extension.
* [Sign in](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) to your Adobe account and view to confirm your organization ID. The organization ID is the ID associated with your provisioned Experience Cloud company. This ID is a 24-character alphanumeric string, followed by (and must include) @AdobeOrg.
* [Create or update](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/update-xdm.html) your XDM schema with Commerce-specific field groups.
* [Create a dataset](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) based off the schema you created or updated. This dataset will contain the Commerce data you send.
* [Create a datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) and select the XDM schema that contains the Commerce-specific field groups.
* [Connect to Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html).
* [Connect to Adobe Experience Platform](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/connect-data.html).

### Connect to the Commerce Destination from Adobe Experience Platform for Audience Sharing

To connect to the Adobe Commerce destination:

* In the [Adobe Experience Platform interface](https://experience.adobe.com/platform/), go to Destinations > Catalog.
* Select Personalization.
* Select the Adobe Commerce destination to highlight it, then select Set up.
* Follow the steps described in the [destination configuration tutorial](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/connect-destination.html).

## Out-of-Box Data

* Storefront (Browser/App) Events
* Back office events
* Historical order data

For complete list of events supported, please refer to [Commerce Events](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/event-forwarding/events.html)

## Architecture

<img src="../commerce/assets/commerce_rtcdp.png" alt="Adobe Commerce RTCDP architecture" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Related Implementation Guides

| Guide |Link|
|:----|:----|
|Platform Connector|[Adobe Commerce Experience Platform connector overview](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/overview.html)|
|Commerce Destination|[Adobe Commerce Connection in RTCDP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-commerce.html)|
|Edge Personalization|[Activate audiences to edge personalization destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations.html)| |
