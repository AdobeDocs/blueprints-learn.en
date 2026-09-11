---
title: Create datastream
description: Learn how to create and configure a datastream with Adobe Experience Platform, Offer Decisioning, and Journey Optimizer services to enable Edge event processing.
doc-type: article
solution: Experience Platform
exl-id: 37873340-476a-4303-886d-de4835bba8df
---

# Create datastream

## Learning objective

Create and configure a datastream with the required services to enable Edge event processing.

A Datastream defines which services that will utilize it.

- When sending data to the Edge you specify which Datastream to use
- Data sent to these Datastreams can then take action according to the service configured
  - Adobe Experience Platform

## Create a new datastream

1. In the left rail under **Data Collection** click on **Datastreams**
1. Then click on **New Datastream** to create one

![Datastreams list with the New Datastream button highlighted](assets/create-datastream-new-datastream-button.png)

## Configure datastream

Configure the datastream with following information:

1. Name -> **Datastream SB + \<sandbox name> (i.e. Datastream SB01)**
1. Mapping Schema -> **dep: Web**
1. Toggle **on** all the options under **Geolocation and Network Lookup** if you want to capture this info.
1. Click on the **Save** button when done

>[!WARNING]
>
>Do not click on Save and Add Mapping.  If you accidentally do, just cancel out

![Datastream configuration form with name and mapping schema fields](assets/create-datastream-configure-datastream-form.png "Configure the datastream")



After you save your datastream, you see the following screen:

![Confirmation screen after saving the new datastream](assets/create-datastream-created-confirmation.png "Datastream created final screen")

## Add Adobe Experience Platform service

This allows you to send data to the Hub and land in a dataset for data received by this Datastream.

1. Click the blue **Add Service** button found in the middle of the screen

   ![Add Service button on the datastream configuration screen](assets/create-datastream-add-service-button.png)

2. Configure the following items:
   - **Service** -> `Adobe Experience Platform`
   - **Event Dataset** -> `dep: Web`
   - **Profile Dataset** -> `dep: Customer Account`
   - **Select Checkbox** -> `Offer Decisioning`
   - **Select Checkbox** -> `Adobe Journey Optimizer`
3. When done click **Save**

![Adobe Experience Platform service configuration dialog with event and profile dataset fields](assets/create-datastream-configure-aep-service.png)

You see the service now added to your datastream

![Adobe Experience Platform service added to the datastream](assets/create-datastream-aep-service-added.png "Adobe Experience Platform Service added in datastream")

**Copy** and **save** the **Datastream ID** to your local computer (we will use it later in Postman)

![Datastream ID field to copy and save for later use](assets/create-datastream-copy-datastream-id.png)

## Recap

You should have a functioning datastream with Adobe Experience Platform service configured.
