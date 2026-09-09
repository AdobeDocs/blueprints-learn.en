---
title: Add Email Activities
description: Learn how to add and configure two Email activities on separate Fork branches using different email channel configurations in an Orchestrated Campaign.
doc-type: article
solution: Experience Platform
exl-id: e911a251-9f9f-484c-a2de-101b0fc2c417
---

# Objective

In the next set of steps, you will build on the campaign to add two Email activities to the two Fork activity branches. You will configure the two Email activities to use the Email channels, created previously. Finally you will also add basic Email setup (subject and body) to each of these Email activity. 

>[!CAUTION]
>
>Before you continue you must ensure both of your email channel confgiurations are showing active in their status.
>
>![29YT96a7xEHLIn9UACU e 20260128 194420.png "Email channel configurations"](assets/29YT96a7xEHLIn9UACU-e-20260128-194420.png "Email channel configurations")



## Add Top Branch Email Acitivty

1. Click on the **+** of the top flow and select **Email** from the **Channel activities**

![Add Email activity](assets/add-email-activities-7.png)

The **Email** details pane opens

![Edit Email activity](assets/add-email-activities-6.png)

2. Rename the label to **Email using Profile attribute** for the **Email** activity and click on **Edit email**. Note that the email body creation is only for testing purposes

![Edit Email](assets/add-email-activities-4.png)

3. Select the **Actions** tab and from the drop down select **Profile-Email** channel config

![Configure Email Actions](assets/add-email-activities-12.png)

4. Next, click on **Edit content** to add some test content

![Edit content](assets/add-email-activities-10.png)

5. Provide a **Subject Line** ("Upgrade Offer for Basic plan members") and click on the **Edit email body** button

![Add subject line and edit email body](assets/add-email-activities-9.png)

6. There are many options, for this test, choose **Code your own** HTML option

![Code your own](assets/add-email-activities-11.png)

7. In the **Email Designer**, insert a test line "Upgrade Offer Available!" just before the `</body></html>` tags as shown and click on **Save**

![Email Designer](assets/add-email-activities-8.png)

8. Wait for the confirmation message to appear at the bottom-right corner

![Confirmation](assets/add-email-activities-5.png)

9. Click on the **left arrow** next to the **Email Designer** to exit

![Exit Email Designer](assets/add-email-activities-3.png)

10. A confirmation dialog pops up, click on the **Save & close** button

![Save & close](assets/add-email-activities-1.png)

11. Review the Email properties and actions including the text added to the Email body. Click on the **left arrow** to navigate back to the campaign canvas

![Back to Campaign canvas](assets/add-email-activities-2.png)

## Add Bottom Branch Email Activity

Back in the campaign canvas, click on the **+** of the bottom flow and select **Email** from the **Channel activities**. Follow the same steps as above (Steps 2 to 11) except for the following:

- Rename the label to **Email using Target Dimension** for the **Email** activity
- In the Email settings, choose the **Relational-Email** Email channel config

![TwepnVevrbnRDJHbMpRLt 20260114 224239.png "Add the second Email activity"](assets/TwepnVevrbnRDJHbMpRLt-20260114-224239.png "Add the second Email activity")

## Recap

You have now seen how to configure the Email activities with the Email channels. Each activity was then configured with a very basic Email subject and body. The entire campaign will be tested next.
