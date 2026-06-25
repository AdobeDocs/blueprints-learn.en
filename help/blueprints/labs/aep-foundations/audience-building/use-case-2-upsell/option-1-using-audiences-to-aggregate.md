---
title: Option #1 - Using Audiences to Aggregate
description: Option #1 - Using Audiences to Aggregate
doc-type: article
solution: Experience Platform
exl-id: da019755-07a3-406c-8ac7-7878325a14bf
---

Aggregates in Audiences allow us to aggregate Events in the Audience rule. But since we can only do one aggregate at a time, we need to split the two from our use case. 

# Audience #1 - Billing Data Usage in the Last 6 Months > 140GB

In this audience build we will need to determine total billing data usage in the last 6 months > 140gb. To do so perform the following:

1. Create a new Audience.  Use the Billing Statement Event Card.

![QPzeyFejTc 8hjTOkT create a new audience use the billing statement event card](assets/px_qPzeyFejTc_8hjTOkT_create-a-new-audience-use-the-billing-statement-event-card.png)

>[!NOTE]
>
>A good Event Type structure makes it easy for your users to use and understand.  Take time to develop a standardized approach across your schemas.
>
>It helps with misspellings.
>
>You can always fall back on the Event Type field and manually type things in.



2\. Click on the Ellipse in the bottom right rules and choose Aggregate. Click on Select an Attribute and type Usage. Select the Billing Data Usage field.



![Select the billing data usage field 1](assets/RjsOp4wq2Y69QdzZzNTjc_select-the-billing-data-usage-field-1.png)



![YCpKnuB4ahBt1 select the billing data usage field 2](assets/WvsHAZ0_YCpKnuB4ahBt1_select-the-billing-data-usage-field-2.png)



3\. Change the Equals to Greater than and the value of 140.

4\. Change the time above the Event card from Any Time to In Last and the value to 6 and the days to months

![Change t](assets/z60-lRWO6zEQPsJGtVE-m_change-t.png)



5\. Provide a description and save.  

6\. Give the Audience the name “*Billing Usage Sum > 140 GB (last 6 months)*”

>[!NOTE]
>
>Aggregate Audiences can only be saved as Batch

>[!NOTE]
>
>There are two ways to use aggregates in Audiences.
>
>- Sum/Count/Min/Max/Average (like we did above)
>- Counts only (this counts each Event as 1)
>
>![Counts only this counts each event as 1](assets/uzn0zTYzRuEOzJ01IlEC6_counts-only-this-counts-each-event-as-1.png)
>
>Both can be used together if desired
>
>![Both can be used together if desired](assets/fGNSR67CZBkgdLe34m3fh_both-can-be-used-together-if-desired.png)

## Audience #2 - Rolling 6 Month Avg. Monthly Data Usage of >= 20GB 

1. Do not click on the hyperlink, but select the row in the Audience List UI so it is highlighting the one we just created. Once it is highlighted, click copy.

![E4Z21gQIQtPK v once it is highlighted click copy](assets/LcaeHU_E4Z21gQIQtPK-v_once-it-is-highlighted-click-copy.png)



2\. Click the copy and Edit it.  Click on the Event card and change the Sum to Average. Change the greater than to greater than or equal to, and the value to 20. Copy the pseudo code into the description.

![7jXI8ncd copy the pseudo code into the description](assets/YdSYiI-b9VRZ_7jXI8ncd_copy-the-pseudo-code-into-the-description.png)



3\. Give the Audience the name “*Billing Usage Avg > 20 GB (last 6 months)*” 

## Audience #3 - Does Not Have an Ultimate Phone Plan

1. Create a new Audience
1. In Attributes, search for Plan Name
1. Add Plan Name (Plan Name)  
1. Select "Ultimate".  Change to Does Not Equal

>[!NOTE]
>
>Remember our Pre-Work? We are going to use a field on our lookup dimension:
>
>XDM Individual Profile > Devbc> Plan Details > Plan ID properties > **Plan Name (Plan Name)**

![Eb9q22 select 22ultimate 22 change to does not equal](assets/ZPDWk4jACy7PbG_eb9q22_select-22ultimate-22-change-to-does-not-equal.png)



5\. Click on Audiences --> Experience Platform. Drag Billing Usage Sum > 140 GB and Billing Usage Avg >= 20 GB next to Plan Name.

![20 gb next to plan name](assets/YKV8tSsAjn1gkShNtXYOm_20-gb-next-to-plan-name.png)



6\. Copy the pseudo code into the description

7\. Check this can be Streaming. **It can’t be Streaming**. Let’s make some changes

>[!NOTE]
>
>Any use of a Lookup dataset creates a Multi-Entity Audience which becomes evaluated in Batch.  We used a field in our Audience:
>
>XDM Individual Profile > Devbc> Plan Details > Plan ID properties > Plan Name (Plan Name)



8\. Replace **Plan Name (Plan Name)** with: XDM Individual Profile > Devbc > Plan Details > **Plan Name**

![Plan name](assets/Yj0bYLNwN7NYvkH1evela_plan-name.png)

>[!NOTE]
>
>Remember during the LID Denormalize step we added Plan Name to the Profile?  Doing this allows us to refer to it in a Audience.  Thus, we remove a join to the lookup and we can now make our evaluation method Streaming.
>
>The tradeoff here is we have moved this logic upstream to pre data ingest instead of during Audience evaluation.
>
>We also now have to update any Profile if that Plan Name changes.
>
>The benefit though is we can now react in real time.



9\. Validate we can now be able to save this as Streaming. Save Audience as “*Billing Data Usage High But No Ultimate Plan*” 

>[!WARNING]
>
>While this evaluation method is Streaming, it is basing Audience qualification on two batch Audiences.

>[!NOTE]
>
>This approach will work, but we now have an Streaming Audience (real time), using Batch Audiences (that will run once every 24 hours). If this works for our use cases and data loads, then this is a good choice (e.g. maybe our billing data is loaded daily or monthly which is highly likely but not all use cases will be like this). If not, a common approach is to aggregate the data before sending to AEP. Let’s look at another option if we need a more real time approach.

