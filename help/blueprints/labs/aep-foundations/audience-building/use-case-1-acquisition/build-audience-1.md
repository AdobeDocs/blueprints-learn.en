---
hold: true
title: Build Audience #1
description: Build Audience #1
doc-type: article

solution: Experience Platform
exl-id: b8c1080e-b093-4d50-94da-5aced6bf0a08
---

# Lab Objective

Build an audience that only finds profiles who placed an order for an iPhone 14

## Breaking Down the Audience

Let us start by creating our first audience. It is composed of many pieces that we need to incorporate. Click on Audience on the left rail and create Audience button in the top right.  

![Click on](assets/click-on.png)



We are going to break this Use Case up into pieces and solve them with multiple Audiences. The reason for this is we are trying to make this a streaming and two things are preventing this:

1. The exclude clause “no order exists for iPhone 14/Pixel 7”
1. The exclude clause “no active iPhone 14/Pixel 7” We will go over the ramifications of this at the end. 

## Part 1 - Discovery

The first part of our Audience is to look for “no order exists for an iPhone 14”. Imagine we are a new Marketer to AEP and did not design the Schema. Do a search for “Order” in the Events tab on the left rail 

![Ek1cGeisQd9hKALh do a search for order in the events tab on the left rail](assets/do-a-search-for-order-in-the-events-tab-on-the-left-rail.png)



We get a lot of objects related to an order

- Attributes: e.g. Order ID, Order Date
- Folders: e.g. Order, Plan Order Details
- Event Types: e.g. Order Placed, Order Shipped, etc.

>[!NOTE]
>
>* There is no “i” for the Order “folder”. Even though our description has been populated, it does not have it and this may be a source of confusion for your Marketer as they may try and use that or want to know what it is. 
>* The "i" for Event Cards just repeats what the type is since the Event Type is one field, not many.
>* Summary data will only show if the value is present in more than 2% of merged profiles. This also drives any autocomplete when filtering on a String.



Let's use Order Placed Event Type card and Drag that onto the canvas.

![C let s use order placed event type card and drag that onto the canvas](assets/let-s-use-order-placed-event-type-card-and-drag-that-onto-the-canvas.png)

>[!NOTE]
>
>**Optional:**
>
>Every Event has an Event Type.  We can filter on the Event Type instead of using an event type card.
>
>Remember back to when we extended the Order Schema Event Type. We added the values we now see in the drop down.  These same values appear as Event Type cards
>
>If you want you can use either approach.  
>
>In a new Audience, go into XDM Experience Event and drag on Event Type.
>
>![In a new audience go into xdm experience event and drag on event type](assets/in-a-new-audience-go-into-xdm-experience-event-and-drag-on-event-type.png)
>
>Filtering using Event Type cards is the same as filtering using the Event Type Field
>
>![The same as filtering using the event type fiel](assets/the-same-as-filtering-using-the-event-type-fiel.png)
>
>Benefit of using Event Type Cards: 
>
>- It shows the name of the Event Type in the Audience making it easy and quick to understand
>- It is quick and requires less steps
>
>Benefit of using Event Type Field:
>
>- It allows selecting multiple Event Types (e.g. “Order Picked Up” or “Order Delivered”) if we wanted to include multiple types in one criteria
>- It supports case sensitivity

>[!NOTE]
>
>There are a few options to consider for "No Order Exists".  We are choosing a simple approach, but here are things to think about in the real world:
>
>- Order Placed but Picked up or Shipped
>- Order Placed but Cancelled
>- Multiple Orders Placed but one Cancelled



Our Marketer knows from their training that more than one data sources was loaded: 

- Orders (captured by the Order system across all channels)
- Web (client side tracking of what people are clicking on, including Orders placed on the site)
- eCommerce (captured by the eCommerce system on the site)

Which source should we use? They all logically represent the same event “Order Placed”. But they physically stored in different systems. How do we know which to use? The best way is to look at the descriptions on each Schema object and each field to know. 

>[!NOTE]
>
>Descriptions should have relevant info to help make these decisions, such as:
>
>1. Where is the data coming from?
>2. What does it contain or not contain?
>3. What is the latency?
>4. Has any system been designated “source of truth”?
>5. Are there any nuances we need to take into consideration?



For us, we want to use Order Placed, but keep in mind, depending on our use case we could have had the following requirements, that may influence which source we pull from: 

- Onsite purchases in last 30 minutes
- Orders placed and not Cancelled
- Orders picked up within 1 day of being Ready

>[!TIP]
>
>Optional thought exercise, imagine we placed a single Order on our site today (remember that Order is recorded by all three systems):
>
>1. How many events would be counted for orders placed today?
>2. How many orders were placed from the customers perspective?
>3. How many events would be counted if we filtered on Shipping Method = overnight (assuming they chose this)?
>4. How should we address this (Audience or Data Model)?



After doing some analysis, we are going to go with the `Orders Event of Event Type=”order. placed”`. We want to ensure our Audience is using the source of truth at the tradeoff of speed (the web data streams in with each click while the Order goes through some processing before sent). Plus in the future we may want to exclude those who Cancelled and that could be done through any channel. 

## Part 2 - Build the Audience

Turn on Show Full Schema



![Turn on show full schema 1](assets/turn-on-show-full-schema-1.png)



![Turn on show full schema 2](assets/turn-on-show-full-schema-2.png)

Let's build on what we started.  Click on the Placed card, then **clear “placed” from the Search** on the left rail and drill down into:

XDM Experience Event -> Product List items folder 

>[!WARNING]
>
>A common confusion for your Marketer would be to use Device instead of Product here (since we will filter on iPhone). Again, another reason for good descriptions.

![L9WbTFv again another reason for good descriptions](assets/again-another-reason-for-good-descriptions.png)

We are looking for something that we can filter on that might have iPhone. Notice we have three options 

- Name
- Product
- SKU

![DrG53WgMychk4qtND we are l](assets/we-are-l.png)

They all could be good candidates, but we don’t know.  Click on the "i" for more detail on each one.

>[!NOTE]
>
>You can change the descriptions for any OOTB fields. Update or even hide the fields not being used to reduce confusion for your users. These OOTB descriptions may not make sense in your industry/business. 
>
>A good description might even contain examples
>
>- Name Description = The display name for the product as presented to the user for this product view. For example: iPhone 14, Pixel 7
>- SKU Description = Stock keeping unit (SKU), the unique identifier for a product defined by the vendor. For example: iP14, Pix7
>- Product Description = The XDM identifier of the product itself. For example: 123, 456

Turn "show only fields with data" on

![Turn 22show only fields with data 22 on](assets/turn-22show-only-fields-with-data-22-on.png)

>[!NOTE]
>
>**Observable Schema**
>
>This is only what fields have data in them.  It is a way for Apps built on AEP to exclude from using fields that are effectively useless.
>
>**Full XDM Schema**
>
>This is all the fields in the Union Schema regardless if any data has been loaded into them.

Once we turn on "show only fields with data" we notice the fields we were thinking of using go away.

Drill down to XDM ExperienceEvent > Product list items > Dep > Model

![Drill do](assets/drill-do.png)

Model looks like it, but doesn't have any descriptions.

Drag it onto the Placed Event Card.

![P7s04WPQDpIS7LhDLmmk drag it onto the placed event card](assets/drag-it-onto-the-placed-event-card.png)

Add iPhone 14

![Add iphone 14](assets/add-iphone-14.png)

Above the Placed Event, change "Any time" to "Today"

![S2l0SJwJLf 6dmK1KhT 20250715 192957](assets/use-case-1-acquisition-1.png)

>[!NOTE]
>
>We filter on today because we don't care about orders placed a week, a month or a year ago.  Also, a longer lookback will be covered in the next section.  At some point the order turns into "*owned*", and we will build a segment for that.  



Provide a description

Change evaluation method to **Streaming**

![Change evaluation method to streamin](assets/change-evaluation-method-to-streamin.png)

**Save Audience** as “*Placed Order iPhone 14*” 

Click the blue button **Activate Audience** to Destination

![Activate audience to destination](assets/activate-audience-to-destination-2.png)

Select the **Streaming DEP Webhook** Destination and click Next

![Streaming dep webhook destination](assets/streaming-dep-webhook-destination.png)

Do not change the mapping, click Next and Finish

>[!NOTE]
>
>**Containers**
>
>Notice when we filter on Name in the Product list it added some containers automatically. The reason for this is that Product list items is an Array data type. When filtering on an Array, a Container is created (called Product list items in our example). 
>
>
>
>![Called product list items in our example](assets/called-product-list-items-in-our-example.png)
>
>Containers are a way of referencing an Event variable or Array element. You can read more about what the ramification of this is in this Blog, but for simplicity’s sake, this allows you to specify if a single element in the array meets both conditions or the condition can be spread across two elements. 
>
>[https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-blogs/how-exactly-do-containers-work-in-aep-segmentation-a-deeper-look/ba-p/458780](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-blogs/how-exactly-do-containers-work-in-aep-segmentation-a-deeper-look/ba-p/458780)

>[!WARNING]
>
>**Time Filters**
>
>While nothing is specified in the requirements, this Audience has a problem that we should go back and clarify with the business. 
>
>The requirements had no time filter. What this means is that if someone placed an order a year or five years ago they would qualify for this. Always try to incorporate a method to ensure you don’t fall into this trap or have to always update your Audiences as the new version comes out. 
>
>If we change the time filter we added, how far back can we go before an Edge Segment becomes Streaming or even Batch?

>[!CAUTION]
>
>**Is Product stored in two places?**
>
>Note the different path naming convention and description. Compare it with the previous Audience 
>
>- XDM Individual Profile > Dep > Active Products > Product ID properties > Product Name 
>  - Description: Name of the product.
>- XDM ExperienceEvent > Product list items > Dep > Model
>  - Description: The display name for the product as presented to the user for this product view.
>
>When we start storing the same value in different places for different reasons and purposes, we need to think through the ramifications to our Users and how the Profile will merge these (and how a Merge Policy will resolve this conflict if needed).
>
>Our current descriptions make it difficult for the Marketer to know which to use

