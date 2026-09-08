---
hold: true
title: Build an Audience
description: Build an Audience
doc-type: article

solution: Experience Platform
exl-id: 697d3edb-2b63-4038-a934-3587495e17f7
---

# Objective

In next few steps you will be creating the audience you want to target for the campaign which is the all the active line holders who have a make that matches the flagship phone that is launching.  The goal being this is the group you want to target with a SMS message nudging them to upgrade their phones.



## Add Build Audience Activity

1. On the canvas click the **+ symbol** and then select the** Build audience** activity to add it to the workflow

![Add build audience activity](assets/build-an-audience-3.png)



1. In the right rail you see the Build audience properties. Update the Label to state the following: `Active Lines with Apple`

![Build audience label](assets/build-an-audience-13.png)


## Select Targeting Dimension

The next step is to select the **Targeting dimension** (i.e. what table you want to query). Do the following steps:

1. Click on the **search icon** in the Targeting dimension box

![Select targeting dimension](assets/build-an-audience-2.png)

1. On the popup, search for and select the table named **dep-rel: Customer Line **and then click the **Confirm **button.

![Select dep-rel: Customer Line](assets/build-an-audience-11.png)

>[!NOTE]
>
>**Note: **Always remember the **targeting dimension** of each audience you create. You’ll learn its significance in the next steps.

>[!NOTE]
>
>**Note: **if you ever select an Adobe created schema you note the schema starts with -> *(caas)*. This is just a namespace applied to the tables within the relational store and stands for Campaign as a Service :)



## Create Audience

Now that you have selected your targeting dimension (what relational schema you are going to query) you can start creating your definition.

1. In the right rail click on the **Create Audience **button

![Create audience](assets/build-an-audience-7.png)

1. Next click on the **Add condition** button

![Add condition](assets/build-an-audience-4.png)



## Create Condition(s)

Now its time to write the logic of the audience using the attributes found in the schema. The goal is to find all customer lines who are active and using a make of Apple.

### Create condition #1 

1. Using the following information and then click on the refresh icon to view the count.
   - **Attribute**:  `Active Line`
   - **Value**:  `true`

![ATKkrA 20260115 223752](assets/build-an-audience-14.png)

1. Click **Refresh **icon to view the qualifying counts on the condition. 

![R2Dclw4l I2sB2VHLJEhQ 20260115 224023](assets/build-an-audience-10.png)

>[!TIP]
>
>You should see a result of 241 if you've built the condition correctly



### Create condition #2 

1. Clicking the** Add condition** button and select the **dep-rel: ****Product \[Lookup] **schema by clicking on the **>** icon

![Selec the dep-rel: Product [Lookup] schema](assets/rqsHFzLBxbqvu-SnaRsml-20260609-202010.png)


1. Look for the field named **Make** and click on the three dots and select **Distribution of values**

![A4mBwu1QS6emUQIRLGJ 20260609 202430](assets/build-an-audience-12.png)



1. Note the various values. You only want `Apple` and thankfully it doesn't have a 100 different spellings. Click on the **Apple field** to select it and then click the **Select attribute and value button** in the upper right.

![XiRNtvbQF4NOMEEO RZCe 20260609 202625](assets/build-an-audience-6.png)

>[!NOTE]
>
>This is a prime example of where the data architect should have designed the schema with enumerations.  This way a marketer doesn't have to manually select/type in the value.  Shame on the data architect!



1. The `Make` field is automatically added along with conditions shown below.
   - **Operator:**  `Equal to`
   - **Value:**  `Apple`
   - **Case sensitive:**  `Enabled`

Click on the **calculate icon** and you should see 85 as the result.

![Condition #2 Final Count](assets/build-an-audience-5.png)

>[!NOTE]
>
>Note the use of the AND operator in the group. Whether you build this in a single group like shown or multiple groups the AND is important because it tells Orchestrated Campaigns both conditions must be true.



## Verify counts

1. Click on the **Calculate icon** found in the right rail under the heading Profiles targeted to get an exact estimate of the audience size. You should see **65 **as the **final count**.

![Calculate exact audience size](assets/build-an-audience-8.png)

>[!NOTE]
>
>Notice how each individual condition returned a different number (condition #1 --> 241 and condition #2 --> 85) but the final audience size was the lesser of the two conditions.  This is because of that AND operator.



1. If you see final count of **65 **click the **Confirm **button in the top right of the screen and then click the **Save **button in the top right to save your work.



## Challenge

Assume for a moment you had typed in the last condition such that `Make` was equal to `apple` (lowercased) and you had left the configuration option for `Case sensitive` toggled `on`.  This would make that conditions record count equal to 0.  So you would have 241 active lines and 0 where the make is apple.



**What would be the final audience size it this case?**

![1qx59JI8OEoY C 20260115 225804.png "Last condition is 0"](assets/Qa5xNh_1qx59JI8OEoY-C-20260115-225804.png "Last condition is 0")

## Answer

Its zero :) Do you know why?

![JX6 20260115 225933](assets/build-an-audience-9.png)



## Recap

You have successfully created your first audience and should now see how easy it is to develop and validate your counts within the Build Audience activity.

![Image](assets/build-an-audience-1.png)

