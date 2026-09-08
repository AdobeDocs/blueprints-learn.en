---
hold: true
title: Save the Audience
description: Save the Audience
doc-type: article

solution: Experience Platform
exl-id: 6422ea8d-146b-4fc7-86e6-491f77590ca1
---

# Objective

In the next set of steps you will be saving the audience your created back to the Audience Portal so other solutions across Adobe Experience Platform and its applications can leverage it for their own use cases.



## Change the Dimension

1. On the workflow canvas, click the **+**** icon** on **Save Audience** branch and from the list of activities, select the **Change Dimension **activity

![Image](assets/save-the-audience-11.png)



1. Update the properties of the change dimension as outlined below:
   - **Label:**  `Convert Line to Account`
   - **New target dimension:**  `dep-rel: Customer Account`

![Click arrow on targeting dimension](assets/save-the-audience-2.png)

![Select Customer Account](assets/save-the-audience-7.png)

>[!NOTE]
>
>**Why are you doing this you ask?**  Remember that to join to the Real-Time Customer Profile (which is where you save audiences to) you have to use the Profile Target Mapping you configured which only joins from the dep-rel: Customer Account schema.



1. When done, you should now see this in your canvas.  Save your work!

![IleMvhafPtBOxvsR3YRIM 20260609 203448](assets/save-the-audience-4.png)



## Deduplicate the Result

1. Click the **+**** icon** after the Change Dimension activity and from the list of activities select the **Deduplication **activity

![Add deduplication activity](assets/save-the-audience-5.png)



1. Update the label of the Deduplication activity to `Dedup customer id`

![Deduplication label and primary set](assets/save-the-audience-12.png)



1. Now click the **+ Add attribute** button and select the field from the schema titled **Customer ID**

![Add attribute](assets/save-the-audience-14.png)

![Select the Customer ID field](assets/save-the-audience-1.png)



1. Under the Deduplication settings, ensure you have the following set:
   - **Duplicates to keep:**  `1`
   - **Deduplication method:**  `Random selection`

![Deduplication settings](assets/save-the-audience-6.png)

>[!NOTE]
>
>**Note:** the other options for deduplication allow you to specify your own custom logic.  Most of the time if you need to deduplicate you'll be doing it using the primary key of the table.



1. When you are done your canvas should now look like this. Click the **Save **button in the upper right before moving on.

![Deduplication activity fully configured](assets/save-the-audience-13.png)



## Add Save Audience Activity

1. Click the **+** icon after the Deduplication activity and select the** Save Audience **activity

![Add the save audience activity](assets/save-the-audience-8.png)

1. In the right rail set the properties of the activity to the following:
   - **Audience Label**:  `Apple Upgrade Eligible Customer Accounts`
   - **Profile mapping field**:  `dep-rel: Customer Account - customer id`

![Save audience label and profile mapping](assets/save-the-audience-15.png)

>[!NOTE]
>
>**Note:** The "Profile mapping field" is what you setup previously so that the Relational Store can join to the Real-Time Customer Profile.  The profile has been modeled as a Customer Account level so you want to save the audience in the same.  Hence the need for the change dimension and the deduplication.



## Audience Field Mappings

By default the primary key of the targeting dimension (i.e., Customer ID) is added to the audience as a field. You can see this if you look in the right and expand the field.  Two things to note:

- **Source Audience Field** --> refers to the field coming from the relational schema
- **Target Audience Field** --> the name of the field that will be created as part of the audience save

![Default field added to Save Audience activity](assets/save-the-audience-9.png)

>[!NOTE]
>
>Note how terribly the Target Audience Field is named `Dep_rel_customer_account_Customer_id`.  You should always change this to something more legible to a marketer, no excuses.



## Fix Default Audience Field

1. Rename the default Target Audience Field to **Customer\_ID **like shown below:

![Default field renamed](assets/save-the-audience-3.png)

>[!TIP]
>
>Now you have a human legible field name 🎉



1. Click the **Start **button to run your workflow. Your workflow should now look like this and you should see the counts as follows:
   - Build audience: `65`
   - Convert Line to Account:  `65`
   - Dedup customer id:  `46`

![Workflow test run with save audience activity](assets/save-the-audience-10.png)

>[!NOTE]
>
>**Note:  **The save audience activity will only create the audience when the workflow is published, not when it is simply started. When the audience is created, it will include all the attributes you added to it and will join to the Real-Time Customer Profile during the next scheduled daily run of the segmentation service job.

>[!CAUTION]
>
>DO NOT PUBLISH YOUR WORKFLOW!



## Challenge

What happens if you do not deduplicate before saving the audience?  Will the audience store all 65 records or only the 46?

![Yz7Xqe1gkG  20260120 170353.png "Save audience with dedup activity beforehand"](assets/pL8lj05i_-yz7Xqe1gkG_-20260120-170353.png "Save audience with dedup activity beforehand")



## Answer

The audience will store all 65 records, but a read audience activity will dedup them on import based on the join condition 😁







## Recap

You should now have a good understanding of how the Save Audience works and why deduplication matters.  Remember that you always need to have the Profile Target Mapping defined because the Relational Store data has to know how to join to the Real-Time Customer Profile.  The Profile Target Mapping is the join condition 🙂

