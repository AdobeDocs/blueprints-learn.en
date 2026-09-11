---
title: Build Audience #2
description: Build an audience of profiles without an active iPhone 14 line, then convert it from batch to streaming evaluation using a profile-based field.
doc-type: article
solution: Experience Platform
exl-id: 5a598e9b-9969-4287-8bbd-9de8864b3025
---

# Build Audience #2

## Lab objective

Build an audience that finds all profiles who do not have an active line that is an iPhone 14


## Analysis tasks

This Audience is "those who do not have an active iPhone 14"

- How do we know someone does not “have an active iPhone 14”?  Ideas: 
  - Include those who purchased an iPhone 14
  - Include those who have Billing data for an iPhone 14
  - Include those who have any web data coming from an iPhone 14
  - Any others?

In the end, this boils down to a business choice on who they want to market to. In our case, the company has deemed this so important we built a schema that defines Active Lines, so use that. 

>[!NOTE]
>
>Since Active Lines is an array stored on a Profile, this is going to select the owner of the account vs each individual owner of the device. Make sure the Marketing team is aware of and wants that. Otherwise, you might want a different approach.

## Create a new Audience (Owns iPhone 14)

1. On the Attributes tab in the left rail, navigate down to Product Name (or search for it).
   - XDM Individual Profile --> \<tenant name> --> Active Products --> Product ID properties --> Product Name
1. Drag Product Name onto the canvas 

![Drag Product Name onto the canvas](assets/build-audience-2-drag-product-name-onto-the-canvas.png)



## Save the Audience

1. Type iPhone 14 (keep as Batch evaluation)
1. Provide a Description
1. Save Audience as “*Owns iPhone 14*” 
   - Go through the same steps above for the Pixel 7 (if you have time).

![Save the audience as "Owns iPhone 14"](assets/build-audience-2-save-audience-as-owns-iphone-14.png)

>[!TIP]
>
>**Side Thought, “couldn’t we just filter on the Events, rather than having another field on Profile store the same thing”?**
>
>Yes we could, but we have to go into some business and technical nuances that make the Audiences complex and introduce some challenges:
>
>1. If we use the Purchase Event: 
>   1. What if they didn’t buy from us, but have an active line?
>   1. What if they purchased 2 years ago, my rule has to look back N number of years and we only kept 1 year of Events on Profile?
>1. The Billing Event seems like a better fit:
>   1. But now the data is up to a month old.
>   1. What if the last Billing Event was 2 years ago, this could include people who aren’t customers
>   1. What if my data load failed, my count might drop to zero if I’m only looking back one month in order to exclude old data
>   1. Do we even capture the Device for a Billing Event? No, so we would have to change our data feed
>
>In the end, we will have to make some trade offs for this Audience. If your heart is still set on using Events for this rule, read this Blog about it: https\://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-blogs/how-to-capture-latest-experience-event-in-adobe-experience/ba-p/430941 

>[!NOTE]
>
>**Enabling a Merge Policy for Edge**
>
>Ensure your Merge Policy is configured for Edge Audiences. Go to your Merge Policies and Edit the Default Merge Policy for \_xdm.context.profile.  Turn on the Active-On-Edge Merge Policy and save.
>
>![Edit the Default Merge Policy for _xdm.context.profile](assets/build-audience-2-enabling-a-merge-policy-for-edge-1.png)
>
>
>
>![Turn on the Active-On-Edge Merge Policy and save](assets/build-audience-2-enabling-a-merge-policy-for-edge-2.png)

## Rebuild the Audience

Marketing walked in today and gave us a requirement to have this Streaming and unfortunately the way we have this built is Batch. Fix that:

1. Open the "*Owns iPhone 14*" Audience and change the name to "*Owns iPhone 14 Batch*".

   >[!WARNING]
   >
   >Today we cannot change the Evaluation Method in the UI. Any Audiences that reference this Audience also have to be deleted. Keep this in mind when deciding on your building strategy of using Segments within Segments.



2. Create a new Audience. Add the "Owns iPhone 14 Audience Batch" Audience to the canvas and click Convert to Rules.

   ![Add the Owns iPhone 14 Batch audience to the canvas and click Convert to Rules](assets/build-audience-2-audience-to-the-canvas-and-click-convert-to-rules.png)

   ![Audience converted to rules on the canvas](assets/build-audience-2-audience-to-the-canvas-and-click-convert-to-rules-2.png)



3. Update the Description, Name and Evaluation Method to Streaming on the bottom right corner, then click on the folder icon next to the Evaluation Method. You should see this: 

   ![Evaluation Method set to Streaming after clicking the folder icon](assets/build-audience-2-evaluation-method-streaming-folder-icon.png)



   While not obvious, the reason for this is we are using Product Name on a lookup schema

   >[!NOTE]
   >
   >Whenever we use a lookup, our evaluation method is forced to Batch.
   >
   >You can tell this if you look at the path and it has "properties" in it anywhere
   >
   >![Path containing "properties" forces the evaluation method to Batch](assets/build-audience-2-path-contains-properties-forces-batch.png)





4. Replace the existing value for product name to now come from the XDM Individual Profile schema

   Replace the following path:

   - XDM Individual Profile > Dep > Active Products > Product ID properties > Product Name

   Add the new path:

   - XDM Individual Profile > Dep > Active Products > Model

   ![Replace the product name path with the XDM Individual Profile Active Products Model path](assets/build-audience-2-replace-with-xdm-individual-profile-path.png)

   ![Updated audience rule referencing the XDM Individual Profile Model path](assets/build-audience-2-replace-with-xdm-individual-profile-path--2.png)



5. Change the Evaluation Method to Streaming and click the folder icon 

   ![Change the Evaluation Method to Streaming and click the folder icon](assets/build-audience-2-change-evaluation-method-to-streaming.png)



6. For your new Streaming eligible Audience, provide a description.

   - Save the Audience as "*Owns iPhone 14*" Audience.
   - Click the blue button **Activate Audience** to Destination

   ![Click Activate Audience to Destination for the streaming-eligible audience](assets/build-audience-2-activate-audience-to-destination.png)



7. Select the **Streaming DEP Webhook** Destination and click **Next**

8. Click **Next** and **Finish**

>[!NOTE]
>
>Considerations why you may want to select Batch vs Streaming or Edge:
>
>Latest guardrails: [https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

>[!TIP]
>
>**Optional Challenge Lab**
>
>Finished early?
>
>Create an Audience of "Apple Device Loyalty" in one family.  All the people on the plan have the same type of device (Apple).
