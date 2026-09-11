---
title: Option #2 - use pre-aggregates
description: Build a fully streaming audience by using pre-aggregated usage attributes calculated upstream instead of aggregating events inside the audience rule.
doc-type: article
solution: Experience Platform
exl-id: fe6ee041-814f-41c1-91cf-c3473cbca0c2
---

# Option #2 - use pre-aggregates

The challenge with Aggregates in our Audience is that our Audience (while Streaming), is built on aggregations done inside Audiences which are Batch Audiences. Since Marketing has determined a more real time approach is needed, we have done three things to work this into the design:

- Calculate the Aggregates before streaming the data in

>[!NOTE]
>
>This is quite uncommon as most streamed data is designed around a single event vs an aggregate

- Use the denormalized Plan Name
- Stream the data in 

## Create the Audience

Create an audience of all the profiles whose billing data usage is high but do not currently have an ultimate phone plan.

1. Create a new Audience
1. Search for “Agg” on the Attributes not Event tab and drag the two Aggregates onto the canvas. Set the appropriate operators and values for each.

![Set the appropriate operators and values for each aggregate](assets/option-2-use-pre-aggregates-set-operators-and-values.png)



3. Search for the Plan Name on the Profile and add it (XDM Individual Profile > Devbc > Plan Details > Plan Name). Select Does not Equal “Ultimate”

![Select Plan Name Does Not Equal Ultimate](assets/option-2-use-pre-aggregates-select-does-not-equal-ultimate.png)



4. Provide a description.  Validate evaluation method is Streaming.  

5. Save the Audience as “*Billing Data Usage High But No Ultimate Plan (Agg)*”

>[!NOTE]
>
>Remember, we shifted the aggregate logic into our upstream Streaming ETL layer.
>
>This choice is a trade off between have a Batch Audience where the marketer controls the logic vs a Streaming Audience but pushing the definition and control to the ETL layer where Engineering must be involved.

>[!TIP]
>
>**Optional Challenge Lab**
>
>Finished early?
>
>We would like to reach out to our VIPs in real time with a special message when they purchase.  Create an audience of "VIPs".  A VIP is someone who purchased more than $1,000 in the last month.
