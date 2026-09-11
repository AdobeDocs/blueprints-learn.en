---
title: Create Datastream
description: Create and configure a datastream with Event Forwarding and Adobe Experience Platform services to route incoming edge events.
doc-type: article
solution: Experience Platform
exl-id: f7ada451-2f87-48f4-8673-7bfa0df9d0d3
---

# Create Datastream

A Datastream defines which services will utilize it.

- When sending data to the Edge you specify which Datastream to use
- Data sent to these Datastreams can then take action according to the service configured
  - Event Forwarding 
  - Adobe Experience Platform

## Create a new datastream

1. In the left rail under **Data Collection** click on **Datastreams**
1. Then click on **New Datastream** to create one

![Datastreams list with the New Datastream button highlighted](assets/create-datastream-new-datastream-button.png)

## Configure datastream

Configure the datastream with following information:

1. Name -> **Datastream SB + \<sandbox name> (i.e. Datastream SB01)**
1. Event Schema -> **dep: Web**
1. Toggle **on** all the options under **Geolocation and Network Lookup**
1. Click on the **Save** button when done

>[!WARNING]
>
>Do not click on Save and Add Mapping.  If you accidently do just cancel out

![Datastream configuration form with name, event schema, and geolocation lookup options set](assets/create-datastream-configure-datastream-form.png "Configure the datastream")



After you save your datastream you see the following screen:

![Confirmation screen shown immediately after saving the new datastream](assets/create-datastream-created-confirmation-screen.png "Datastream created final screen")

## Add event forwarding service

This allows you to use Event Forwarding for data received by this Datastream.



1. Click on **Add Service**

   ![Datastream detail page with the Add Service button highlighted](assets/create-datastream-add-service-button.png "Add Service")

1. Configure the following items:

   - Service -> Event Forwarding
   - Property -> Select the property you created in the previous step.  It should be named like so: Event Forwarding Property SB + \<your sandbox number>
   - Environment -> Development

1. When done click **Save**

![Event Forwarding service configuration with property and Development environment selected](assets/create-datastream-event-forwarding-service-config.png "Event Forwarding Configuration Screen")



## Add Adobe Experience Platform service

This allows you to send data to the Hub and land in a dataset for data received by this Datastream.



1. Click on **Add Service**

   ![Datastream detail page with Add Service button highlighted to add the Adobe Experience Platform service](assets/create-datastream-add-second-service-button.png "Add a new service")

1. Configure the following items:

   - Service -> Adobe Experience Platform
   - Event Dataset -> dep: Web
   - Profile Dataset -> dep: Customer Account
   - Select Checkbox -> Edge Segmentation
   - Select Checkbox -> Personalization Destination

   ![Adobe Experience Platform service configuration with event dataset, profile dataset, and segmentation checkboxes set](assets/create-datastream-aep-service-config.png "Configure Service")

1. When done click **Save**.  

1. Your final screen should look like below with two services present. **Copy** and **save** the **Datastream ID** to your local computer (you use it later in Postman)

![Final datastream configuration with both Event Forwarding and Adobe Experience Platform services listed](assets/create-datastream-final-configuration-both-services.png "Final Datastream Configuration")
