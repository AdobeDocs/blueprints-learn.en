---
title: Create Code-Based Experience Channel
description: Create Code-Based Experience Channel
doc-type: article
solution: Experience Platform
exl-id: c3353d3d-cd97-46b7-8ef8-c72fa9e7dfe5
---

# Objective

Recall that the business requirements are that any of Connection 5G's systems should be able to return an appropriate offer. Whether it's a customer agent's computer, an in-store kiosk, a mobile app, or the website, the customer should receive the same offer experience. The only AJO channel that can do that is a Code-based Experience (CBE), one of the inbound AJO channels. While a CBE can return HTML, its primary function is to return information about what offer should be presented to the receiving system, with that system knowing what to do with that offer information. Unlike the web channel, CBEs aren't automatically rendered or reported. While it's a little more manual work for the customer, they offer a lot of flexibility as they can be configured to return JSON that any mobile, web, or IOT system can use to execute decisions.

1. If necessary, expand the **Administration** menu item in the left rail (you will likely need to scroll down) and click on **Channels**. You will land on the 'Channel configurations' page.
1. Click the blue **Create channel configuration** button
1. On the 'Channel configuration details' page, name the channel **jsonOffer\_cbe**

>[!NOTE]
>
>Since a CBE can be called by any number of clients across *N* number of platforms, we're going to name this CBE something generic to location, but specific to the fact that it returns offers in the JSON format. 

1. Set the **Select channel **drop-down to **Code-based experience.**

>[!WARNING]
>
>We won't set a Marketing action in this lab because it adds unneeded complexity for our demonstration, but since CBEs can be accessed by any number of systems, you'll want to ensure that in a real use case, you'd set all the possible marketing actions for this channel so that DULE labels are enforced.

1. Tick the **Web** box in the 'Code-based experience settings' area and keep the **Single page** option selected.
1. In the **Page URL** text box, enter the text `https://connection5g.com/home`
1. In the **Location on page** text box, enter the text **jsonOfferContainer**

>[!NOTE]
>
>Not every Experience Event sent to the Edge triggers a request for personalized offers. You'll create a Journey in the next section where this CBE will be configured with the selection strategy you just configured. The 'Location on page' setting is the name of the parameter passed in Experience Events that tells the Experience Edge to return any offers that are assigned to that CBE. It's also often referred to as a surface. Be it a mobile app, web page, or some other IOT device, if the jsonOfferContainer value is passed to the Edge, along with the correct eventType via an Experience Event, the Edge will execute the logic configured thus far in the lab and return the appropriate offer.

1. Click the **JSON** radio button in the 'Format' section. When finished, your CBE channel config should look like this:

![Complete CBE Validation](assets/lw49s_9AsVEzbN1wgSfKL-20251211-220316.png)

1. Once everything looks correct, click the blue **Submit** button in the upper right corner.

>[!TIP]
>
>Once it saves, you will be taken back to the Channel configuration page, and you should see your newly created CBE.

## Recap

On this page, you configured a Code-Based Experience (CBE) channel and set up a new inbound channel that can return offer decisions in JSON format so external systems (like web pages, apps, or kiosks) can request and receive the appropriate offers based on the selection strategy you built earlier.

