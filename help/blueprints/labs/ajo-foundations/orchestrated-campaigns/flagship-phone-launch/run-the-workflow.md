---
title: Run the Workflow
description: Run the Workflow
doc-type: article
solution: Experience Platform
exl-id: c3b35b27-92ae-44ca-a5fb-3f76990f9db4
---

# Objective

In the next few steps you will learn how to test your workflow and more importantly your SMS activity using test mode. 



## Verify Workflow

1. The final workflow should look something like below when you are done. Double check everything looks good. You should see

![Final workflow](assets/1QCUb1fIuTmw7XhAI-81H-20260120-165125.png)

1. If you haven't already stopped your workflow ensure you do so now by clicking the **Stop **button in the upper right.

![DIEFIBX1zRN2ymj4kcPPo 20260119 223109](assets/DIEFIBX1zRN2ymj4kcPPo-20260119-223109.png)

>[!NOTE]
>
>Optionally you can try clicking on the Restart button but its likely you will see an error since you've added activities since the workflow and its cache is no longer valid.



1. Next click the **Start **button to execute and test the workflow end to end

![Start the workflow](assets/jUmPKSTwtXX9Wx4F6BzPM_image.png)



1. Review the result coming into the SMS activity by clicking on **Result** (there are two Results so use the left one as shown below) and then in the left rail clicking on **Preview results** button.

![YMsYL09mFzWqWTjUIzVjT 20260128 213646](assets/YMsYL09mFzWqWTjUIzVjT-20260128-213646.png)

![Preview results](assets/30fb2uTgdLpOonGWwAiZ1-20260119-223609.png)



1. You should see **33 records** and the targeting dimension matches the Customer ID (the join key if you will to profile)

![Records in the result](assets/WOoLb9RNhqJ4EsheV4WmB-20260119-223803.png)



## Test the SMS Activity

1. Close out of the previous window and click on the **SMS activity** and then click the **Run test** button in the right rail

![Click the Run test on the SMS activity](assets/tNWdaQK_7CkXZ9JeiJFBb-20260119-224217.png)



1. Almost immediately you will see a new button appear labeled **View report**.  Click the **View report **button to launch into the report screen.

![View report of the SMS activity](assets/Py_qJMpBByQaMedatrUZa-20260119-224516.png)

>[!NOTE]
>
>This screen will not be populated initially as it takes some time to execute the test run. You may need to refresh a few times before you see results.



1. When you do get results you should see 100% were targeted!

![SMS test send results](assets/_au3MjDVTzAtLfio30Gxg-20260120-173424.png)

`Wait, a minute...the incoming result  was 33 records so where did the 4 go?`



1. Go back to the workflow canvas and click on the transition **Result **coming into the SMS activity and then click on **Preview results** in the right rail.

![Re-review the transition results](assets/xxPvfI_kJwLU999uQfAr--20260120-174005.png)



1. In the Preview results screen scroll all the way to bottom of the table and you'll notice that **4 records** have a **blank Targeting dimension**.

![4 records missing a targeting dimension](assets/xh03ZU9WXda3zyJ6yVvmn-20260120-174234.png)



## Explanation

So here is what happened.

- You had 33 customer lines that you wanted to send a SMS message
- After the change dimension activity 4 of those customer lines had no associated customer account
- The join to the Real-Time Customer Profile requires you have a Customer ID and since there is none on those 4 records there is no way to lookup a profile or create a new one on the fly

Result --> Orchestrated Campaigns drops those 4 records on message execution 

>[!NOTE]
>
>There is an enhancement coming to help address this issue in two ways:
>
>1. Make sure an exclusion log is created for records that are missing a targeting dimension on send
>2. Update the Change dimension activity to do an inner join vs. external join which would drop those 4 records up front

>[!TIP]
>
>Congratulations! You are now officially certified to unleash your very own Orchestrated Campaigns and broadcast messages to the world—responsibly, we hope. Go forth and market like a majestic digital wizard!



## Publishing the Workflow

You are not going to do this in the lab, but for context here is what happens at publication time:

1. Scheduler kicks in if the campaign has a schedule set
1. Save Audience activities create the audience shell within in the Audience Portal and the qualified profiles start ingesting
1. Message execution starts for the first message activity in the workflow
   - Profile lookups occur against the Profile snapshot
     - Matching profiles honor the consent found on the profile
     - Non-matching profiles are created on the fly
   - Delivery logs are created in the `AJO Message Feedback Event Dataset`

