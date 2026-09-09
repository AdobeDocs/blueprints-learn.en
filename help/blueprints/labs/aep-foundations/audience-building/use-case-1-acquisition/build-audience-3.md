---
title: Build Audience #3
description: Build an audience of iPhone 14 product page visitors and combine it with other audiences using audience-of-audiences to enable streaming activation.
doc-type: article
solution: Experience Platform
exl-id: 999f9a20-1655-4eab-a796-a19d69a06879
---

# Build Audience #3

## Lab Objective

Build an audience that visitied an iPhone 14 product page



## Analysis Tasks

This Audience should be straight forward.  We might have multiple product pages, but nothing tricky here.



## Create an Audience (Visited Any Page)

1. Find Page View event on the Event tab under Event Types in the left rail and add to the Audience

![LiM find pag](assets/find-pag.png)

>[!NOTE]
>
>**Using Event Types**
>
>By using the Page View Event we ensure the Audience is only evaluating Page Name in the context of a Page View. It should be redundant since a Page Name only exists on a Page View, but provides two benefits:
>
>- Provides high level visual documentation to the user when looking in the UI
>- Provides filtering to ensure as new events are added that they are not included when that was not the intent
>
>For this reason, we recommend each Event Schema you build should have a lot of thought put into the Event Types you use. They are fundamental to filtering and visual guides.



2\. Provide a description and make it Streaming.  

3\. Above the Placed Event, change "Any time" to "Today"

![S2l0SJwJLf 6dmK1KhT 20250715 192957](assets/use-case-1-acquisition-1.png)

4\. Save this Audience as “*Visited Any Page*”

5\. Click the blue button **Activate Audience** to Destination

6\. Select the **Streaming DEP Webhook** Destination and click next

7\. Click Next and Finish

## Create an Audience (Visited iPhone 14 Page but Not Owns/Ordered it)

1. Create a new Audience and add the Page Views Event

![5MGYCxJ EfgS create a new audience and add the page views event](assets/create-a-new-audience-and-add-the-page-views-event.png)



2\. Navigate to where Page Name is and add the Page Name field to the Event so we can filter on it.

- XDM ExperienceEvent --> Web --> Web page details --> Name

![Xdm experienceevent greater web greater web page details greater name](assets/xdm-experienceevent-greater-web-greater-web-page-details-greater-name.png)



3\. Add contains “iPhone 14”

![Add contains iphone 14](assets/add-contains-iphone-14.png)

>[!CAUTION]
>
>**Searching for "Page"**
>
>Rather than navigating to the field, try searching for "Page"
>
>You will see Page Name does not come up. This is because of how it is named:
>
>- XDM ExperienceEvent > Web > Web page details > Name
>
>So your folder will come up, but not the field itself. When you are putting your naming conventions together, consider this and other common terms people might search on and incorporate those into your naming.
>
>Search does not search descriptions
>
>![W3bu8fPD U2 searching for 22page 22](assets/searching-for-22page-22.png)



4\. Above the Placed Event, change "Any time" to "Today"

![S2l0SJwJLf 6dmK1KhT 20250715 192957](assets/use-case-1-acquisition-1.png)

>[!NOTE]
>
>Since we are activating based on events that happened today, we only focus on page views for today.



5\. Validate this is Streaming and provide a description.

6\. Save Audience as "*Visited iPhone 14 Page*"

![6PRF save audience as 22visited iphone 14 page](assets/save-audience-as-22visited-iphone-14-page.png)



7\. Click the blue button **Activate Audience** to Destination

8\. Select the **Streaming DEP Webhook** Destination and click next

9\. Click Next and Finish



## Create an Audience of Audiences

1. Navigate to the Audiences tab in the top left nav
1. Drill down to Experience Platform
1. Pull in the three other Audiences we previously created
1. Change the Include to Does not include for Owns iPhone 14 and Placed Order iPhone 14.

![Provide a description](assets/provide-a-description.png)



5\. Provide a description.

6\. Change to Streaming

7\. Save as “*Visited iPhone 14 Page but Not Owns/Ordered it*” 

8\. Click the blue button **Activate Audience** to Destination

9\. Select the **Streaming DEP Webhook** Destination and click next

10\. Click Next and Finish

>[!NOTE]
>
>**Time Filter**
>
>The requirements had no time requirements, so if someone visited three years ago, they would qualify. Depending on our use case that may or may not work. It is worth asking. We added one because we are activating based on people who visited our website today.  That may not work in all use cases.  If we add a time filter, how far back can we go before an Edge Audience becomes Streaming or even Batch? 

>[!WARNING]
>
>**Ramifications of breaking this up**
>
>We have split what is a simple requirement up into many Audiences for a few reasons. The requirement is for a Streaming, but these two requirements turn our Audience into Batch. More detail here on the Streaming eligibility rules here:
>
>[https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/streaming-segmentation.html](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/streaming-segmentation.html)

>[!NOTE]
>
>**What are Audiences of Audiences Streaming**
>
>Our *Peeking Underneath the Hood of Audience* blog (link below), talks a little about this below. It shows how the result of a Audience is stored on the Profile. This is important since as data streams in it is looking at the results of a Audience stored on the Profile, it is not rerunning the Audience at that point in time! A simple nuance but worth understanding. Most Profile attributes are updated periodically, so this approach makes sense. 
>
>We need to understand that when using a Audience within a Audience, AEP will attempt to sequence when it can. There are edge cases where this is not possible, e.g. If a Audience of Audiences is used, profile disqualification will happen every 24 hours. 
>
>[https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-blogs/peeking-underneath-the-hood-of-segments-in-aep-adobe-experience/ba-p/453535](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-blogs/peeking-underneath-the-hood-of-segments-in-aep-adobe-experience/ba-p/453535)



## Why Create Multiple Audiences?

If we were to have built all these Audiences in one Audience instead of four, we would get a batch evaluation method even though each Audience individually is Streaming.

![Why are we creating multiple audiences](assets/why-are-we-creating-multiple-audiences.png)



By breaking up these Audiences and using a Audience of Audiences, we get this behavior.  Real-time qualification of these Audience as data streams in 

- Ordered iPhone 14
- Owns iPhone 14
- Visited iPhone 14 Page

>[!WARNING]
>
>Today there is a daily/24 hours latency disqualification of Audiences



Bottom line: we traded off faster entry into the Audience by breaking it into pieces with a 24 hour latency of them falling out of the Audience.

>[!TIP]
>
>**Optional Challenge Lab**
>
>Finished early?
>
>I want to target people with an email if they have an old phone.  Create an Audience of "Has Old Phone".  How might we target them?
