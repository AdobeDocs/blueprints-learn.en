---
title: Filter the Lines
description: Learn how to filter out opted-out customer lines with a Split activity and use Change Dimension to align a workflow's target dimension with the SMS channel configuration.
doc-type: article
solution: Experience Platform
exl-id: fb556a27-5c73-4457-ae98-dba43d445c7f
---

# Objective

In the next set of steps you are going to filter out all the lines that are actually not allowed to be targeted with a SMS message due to the their opt'ing out at the line level.  You can not rely here on Profile consent because this is a line level target.



## Setup Split activity

1. Click the **+** icon on the bottom transition of the Fork activity and select the **Split** activity on the popup. 

![Add split activity to bottom branch](assets/filter-the-lines-13.png)



2. In the right rail update the Label to state the following:  `Filter out opt'd out lines`

![Split label](assets/filter-the-lines-7.png)



3. In the right rail expand the default segment **Subset** section and click the **Create filter** button

![Add a filter to the split](assets/filter-the-lines-6.png)



4. Add a condition to ensure that you remove all Customer Lines that are opt'd out of SMS messaging and then click **Confirm**.

![SMS Opt-in condition](assets/filter-the-lines-1.png)

>[!NOTE]
>
>You need to figure out how to create the condition but the final result should match the screenshot above.  You got this!



5. Click the Save button in the upper to save your work.  Your canvas should look like so now\...

![MXUocahyDcGV47CCwO 20260119 192633](assets/filter-the-lines-3.png)



## Add the SMS Activity

1. On the workflow canvas, click the **+** icon after the split condition you added and select the **SMS Activity**

![Add the SMS activity](assets/filter-the-lines-8.png)

![SMS activity on the canvas](assets/filter-the-lines-4.png)



2. In the right rail click on the Edit SMS button to start configuration of the SMS message

![Edit SMS](assets/filter-the-lines-12.png)



3. In the top nav click on the Actions menu item and then from the SMS configuration drop-down select the channel you previously created.

![AAdFEQXocBhN76EZqlRis 20260609 204837](assets/filter-the-lines-2.png)

>[!CAUTION]
>
>Oh no 🫨!  Why are you getting No results?  Didn't you setup your SMS channel already?  Is the product broken?
>
>FREAK OUT!!!!!!!!!



## Freak Out Moment

The transition of the fork currently has a targeting dimension of Customer Line (i.e what table the current result relates to in the Relational Store).  What is unique with Orchestrated Campaigns though is you always join back to the Real-Time Customer Profile at send time so delivery and tracking information from messages is attributed to a profile.  This join was pre-build for you  from the Customer Account table. 

The channel configuration for SMS was already setup for you beforehand and it currently looks like so...

![UMCuyvc 20260115 220814](assets/flagship-phone-launch-1.png)

**How you read this is as follows:**

- Deliver one message per the target dimension (i.e. Customer Account) on the number of related records found in the secondary dimension (i.e. Customer Line)
- Execute each SMS delivery using the mobile phone number found in the secondary dimension (i.e. Customer Line)

This unique ability to send many messages to one profile is one of the primary features of Orchestrated Campaigns that makes it different from Journeys.


So how do you get this to work?  Add a change dimension 😀



## Add Change dimension

1. Click the back button on the SMS edit screen

![Exit the sms activity](assets/filter-the-lines-9.png)



2. On the workflow canvas, click the **+** **icon** between the Filter and SMS activities and select **Change Dimension**. 

![Add change dimension](assets/filter-the-lines-11.png)



3. In the right update the change dimension with the following information:
   - **Label:**  `Convert Line to Account`
   - **New target dimension:**`dep-rel: Customer Account`

![Change dimension configuration](assets/filter-the-lines-14.png)



4. Click the **Save** button in the upper right of the canvas to save your work. When done your workflow should now look like this...

![Final workflow after change dimension](assets/filter-the-lines-10.png)



## SMS Message Configuration

Now that you've fixed the workflow let's try re-configurating the SMS.



1. Click on the SMS activity in the workflow canvas and then, in the left rail, click on the **Edit SMS** button

![Edit SMS](assets/filter-the-lines-12.png)

>[!NOTE]
>
>This screen takes a while to load.  I know its annoying, trust me its being fixed





2. In the top nav click on the **Actions** menu item and then from the SMS configuration drop-down select the channel you previously created.

![SMS configuration with your sms channel](assets/filter-the-lines-5.png)

>[!TIP]
>
>Feels good doesn't it 😮‍💨



## Recap

You made it through this one and hopefully learned two very important things:

1. You final results targeting dimension has to match the channel configuration you want to use
1. The Change dimension activity is likely going to become your best friend for ensuring this happens
