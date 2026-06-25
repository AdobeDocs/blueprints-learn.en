---
title: Create Datastream
description: Create Datastream
doc-type: article
solution: Experience Platform
exl-id: 37873340-476a-4303-886d-de4835bba8df
---

# Learning Objective

Create and configure a datastream with the required services to enable Edge event processing.

A Datastream defines which services that will utilize it.

- When sending data to the Edge you specify which Datastream to use
- Data sent to these Datastreams can then take action according to the service configured
  - Adobe Experience Platform

## Create a New Datastream

1. In the left rail under **Data Collection** click on **Datastreams**
1. Then click on **New Datastream** to create one

![Create a new datastream](assets/1yZa63vN0lS5E5z7BIQEH_create-a-new-datastream.png)

## Configure Datastream

Configure the datastream with following information:

1. Name -> **Datastream SB + \<sandbox name> (i.e Datastream SB01)**
1. Mapping Schema -> **dep: Web**
1. Toggle **on **all the options under **Geolocation and Network Lookup**if you want to capture this info.
1. Click on the **Save **button when done

>[!WARNING]
>
>Do not click on Save and Add Mapping.  If you accidentally do, just cancel out

![LxxLyKc0x1oi  tJx3hj5wB Cgwl5BpaRg 20241021 190409.png "Configure the datastream"](assets/n-ADAXZy_lxxLyKc0x1oi-_tJx3hj5wB_Cgwl5BpaRg-20241021-190409.png "Configure the datastream")



After you save your datastream you will see the following screen:

![LxxLyKc0x1oi RBmeY EjKJ1cbWOCIvhKZ 20241021 190553.png "Datastream created final screen"](assets/n-ADAXZy_lxxLyKc0x1oi-RBmeY-EjKJ1cbWOCIvhKZ-20241021-190553.png "Datastream created final screen")

## Add Adobe Experience Platform Service

This will allow us to send data to the Hub and land in a dataset for data received by this Datastream.

1. Click the blue **Add Service **button found in the middle of the screen

![YUAtAJ3sUXP7ZCMCuTSPm 20260127 215802](assets/YUAtAJ3sUXP7ZCMCuTSPm-20260127-215802.png)

1. Configure the following items:
   - **Service **-> `Adobe Experience Platform`
   - **Event Dataset** -> `dep: Web`
   - **Profile Dataset** -> `dep: Customer Account`
   - **Select Checkbox** -> `Offer Decisioning`
   - **Select Checkbox** -> `Adobe Journey Optimizer`
1. When done click **Save**

![XEXihsnI1nn8gMjBEuIb  20251219 003026](assets/XEXihsnI1nn8gMjBEuIb--20251219-003026.png)

You should the service now added to your datastream

![Adobe experience platform service added in datastream.png "Adobe Experience Platform Service added in datastream"](assets/dljvg2SwEkYDDcJ-DJG2H_adobe-experience-platform-service-added-in-datastream.png "Adobe Experience Platform Service added in datastream")

**Copy **and **save **the **Datastream ID** to your local computer (we will use it later in Postman)

![AaljP9gL2OGb2Mz2IMI1y 20251028 165155](assets/AaljP9gL2OGb2Mz2IMI1y-20251028-165155.png)

## Recap

You should have a functioning datastream with Adobe Experience Platform service configured 
