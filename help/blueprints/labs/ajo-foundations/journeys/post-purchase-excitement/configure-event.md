---
title: Configure Event
description: Create and configure a unitary Order Shipped event, including identity namespace settings, to serve as a journey's entry trigger.
doc-type: article
solution: Experience Platform
exl-id: 4d1c1d4d-0dc6-4ea1-aa3c-f959bb3b9aa8
---

# Learning Objective

Create and configure an event that will trigger a customer journey when the post-purchase action (order shipped) occurs.

## Navigate to Journey Optimizer

In the upper right hand corner of your browser click on the **Cube **and then select **Journey Optimizer**

![ZgGK65uMAzKLBgLvmfotH 20251112 205222](assets/configure-event-11.png)



## Configure Order Shipped Event

In order to create a Journey that uses a Unitary Event, we need to first configure the event.

1. In the left rail under the  Adminstration menu click to **Configurations **and then on the Events tile click the **Manage** button

![8VoJ0QjbI 20251111 235439](assets/configure-event-8.png)

1. In the upper right click the **Create Event **button

![NUdw3bIS7tKY2KbbMdQxT 20251111 235549](assets/configure-event-10.png)

1. Update the settings of the event as follows:
   - **Name **= `orderShipped`
   - **Type **= `Unitary`
   - **Event Id type** = `Rule based`
   - **Schema **= `dep: Orders v.1`

![VgHKCtoI3Xv2O9rzuA8f6 20251117 220107](assets/configure-event-7.png)

1. In the `Fields`input box click on the **Pencil icon**

![NQwFV5yIRiAE211vPGCMl 20251112 184722](assets/configure-event-9.png)

1. Select the following fields to add to the event and when done click the **OK **button
   - `Event Type (eventType)`
   - `Order ID (orderID)`

![3jv DZLMzqdKKXcILSfco 20251117 221004](assets/configure-event-1.png)

>[!NOTE]
>
>Ensure you only select the Order ID field and not all the fields in the Order 😁



1. In the `Event Id condition input`, click on the** Pencil icon**

![HDhFL48Y10UWlf5hMm4fe 20251223 195045](assets/configure-event-5.png)

1. **Drag **the `Event Type` field onto the canvas

![Zne7T5aJ L14NVHJF3TZy 20251112 185032](assets/configure-event-12.png)

1. In the selection box that appears look for and check the value titled **orders.shipped.  **Then click the **OK **button.

![CpWajzr 20251112 185127](assets/configure-event-3.png)

1. Next update the last two values of Namespace and Profile Identifier with the values shown below:
   - **Namespace **--> `Email`
   - **Profile Identifier** --> `personalEmail`

![Selection of profile identifier](assets/configure-event-2.png)

![Final configuration ](assets/configure-event-4.png)

>[!NOTE]
>
>**What is the Namespace and Profile Identifier used for?**
>
>For any journey that uses an event you must specificy for that event what identity namespace and associated profile identifier should be used to lookup the profile. It's important to understand that choosing one identity over another can impact how the journey will work.
>
>*Quick Example:*
>
>Event payload is a page view containing identities like so:  ECID (primary identity) & Customer ID (optional)
>
>- ECID chosen --> its likely this is the first time identity service has seen this relationship so when journey's receives this event it will attempt to lookup the profile using the ECID and fail to find a profile.  Why? The relationalship doesn't exist yet between ECID and Customer ID and the traits of the profile are likely stored against the known identifer Customer ID
>- Customer ID chosen -->  this identity is not required to be populated and its likely on most page views it would be empty.  Therefore, if this identity was chosen the only time a Journey would fire is when there is an authenticated page view where the Customer ID is set.
>
>Short is there is no right answer just tradeoffs you need to make based on the use case 😃



## Final orderShipped Event Configuration

Verify your final event configuration matches below.  If everything looks good click the **Save **button

![0ScvXz Goy3AMYKZ 20251223 195856](assets/configure-event-6.png)

>[!TIP]
>
>You've configured your first AJO event. High-five yourself!

## Recap

A configured order shipped event in Adobe Journey Optimizer that can be used as the entry point for a journey
