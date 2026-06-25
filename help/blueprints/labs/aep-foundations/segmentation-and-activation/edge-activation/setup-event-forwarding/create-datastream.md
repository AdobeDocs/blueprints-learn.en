---
hold: true
title: Create Datastream
description: Create Datastream
doc-type: article

solution: Experience Platform
exl-id: f7ada451-2f87-48f4-8673-7bfa0df9d0d3
---

A Datastream defines which services that will utilize it.

- When sending data to the Edge you specify which Datastream to use
- Data sent to these Datastreams can then take action according to the service configured
  - Event Forwarding 
  - Adobe Experience Platform

# Create a New Datastream

1. In the left rail under **Data Collection** click on **Datastreams**
1. Then click on **New Datastream** to create one

![Create a new datastream](assets/1yZa63vN0lS5E5z7BIQEH_create-a-new-datastream.png)

## Configure Datastream

Configure the datastream with following information:

1. Name -> **Datastream SB + \<sandbox name> (i.e Datastream SB01)**
1. Event Schema -> **dep: Web**
1. Toggle **on **all the options under **Geolocation and Network Lookup**
1. Click on the **Save **button when done

>[!WARNING]
>
>Do not click on Save and Add Mapping.  If you accidently do just cancel out

![LxxLyKc0x1oi  tJx3hj5wB Cgwl5BpaRg 20241021 190409.png "Configure the datastream"](assets/n-ADAXZy_lxxLyKc0x1oi-_tJx3hj5wB_Cgwl5BpaRg-20241021-190409.png "Configure the datastream")



After you save your datastream you will see the following screen:

![LxxLyKc0x1oi RBmeY EjKJ1cbWOCIvhKZ 20241021 190553.png "Datastream created final screen"](assets/n-ADAXZy_lxxLyKc0x1oi-RBmeY-EjKJ1cbWOCIvhKZ-20241021-190553.png "Datastream created final screen")

## Add Event Forwarding Service

This will allow us to use Event Forwarding for data received by this Datastream.



1. Click on **Add Service**

![Add service.png "Add Service"](assets/L81jKr4HtTTW683Shkwun_add-service.png "Add Service")

2\. Configure the following items:

- Service -> Event Forwarding
- Property -> Select the property you created in the previous step.  It should be named like so: Event Forwarding Property SB + \<your sandbox number>
- Environment -> Development

3\. When done click **Save**

![Event forwarding configuration screen.png "Event Forwarding Configuration Screen"](assets/eFIwixSj4GQCD17lOQ8HU_event-forwarding-configuration-screen.png "Event Forwarding Configuration Screen")



## Add Adobe Experience Platform Service

This will allow us to send data to the Hub and land in a dataset for data received by this Datastream.



1. Click on **Add Service**

![Add a new service.png "Add a new service"](assets/wFj3svksizSadXWKxtdPt_add-a-new-service.png "Add a new service")

2\. Configure the following items:

- Service -> Adobe Experience Platform
- Event Dataset -> dep: Web
- Profile Dataset -> dep: Customer Account
- Select Checkbox -> Edge Segmentation
- Select Checkbox -> Personalization Destination

3\. When done click **Save**

![LsJ configure service.png "Configure Service"](assets/Mq5HASl-P06nRWE9h_LsJ_configure-service.png "Configure Service")



You should the service now added to your datastream

![Adobe experience platform service added in datastream.png "Adobe Experience Platform Service added in datastream"](assets/dljvg2SwEkYDDcJ-DJG2H_adobe-experience-platform-service-added-in-datastream.png "Adobe Experience Platform Service added in datastream")


![Event forwarding configuration screen.png "Event Forwarding Configuration Screen"](assets/eFIwixSj4GQCD17lOQ8HU_event-forwarding-configuration-screen.png "Event Forwarding Configuration Screen")



When done your final screen should look like below with two services present. **Copy **and **save **the **Datastream ID** to your local computer (we will use it later in Postman)

![Final datastream configuration.png "Final Datastream Configuration"](assets/b4RE5cQh9vL9Odnlcivds_final-datastream-configuration.png "Final Datastream Configuration")

