---
title: Add email activities
description: Learn how to add and configure two Email activities on separate Fork branches using different email channel configurations in an Orchestrated Campaign.
doc-type: article
solution: Experience Platform
exl-id: e911a251-9f9f-484c-a2de-101b0fc2c417
---

# Add email activities

## Objective

In the next set of steps, you will build on the campaign to add two Email activities to the two Fork activity branches. You will configure the two Email activities to use the Email channels, created previously. Finally you will also add basic Email setup (subject and body) to each of these Email activity. 

>[!CAUTION]
>
>Before you continue you must ensure both of your email channel configurations are showing active in their status.
>
>![Both email channel configurations showing active status](assets/add-email-activities-email-channel-configs-active.png "Email channel configurations")



## Add top branch email activity

1. Click on the **+** of the top flow and select **Email** from the **Channel activities**

   ![Add Email activity](assets/add-email-activities-select-email-activity.png)

   The **Email** details pane opens

   ![Email details pane](assets/add-email-activities-email-details-pane.png)

2. Rename the label to **Email using Profile attribute** for the **Email** activity and click on **Edit email**. Note that the email body creation is only for testing purposes

   ![Rename Email activity label and click Edit email](assets/add-email-activities-rename-and-edit-email.png)

3. Select the **Actions** tab and from the drop down select **Profile-Email** channel config

   ![Select Profile-Email channel config in Actions tab](assets/add-email-activities-select-profile-email-channel.png)

4. Next, click on **Edit content** to add some test content

   ![Click Edit content to add test content](assets/add-email-activities-edit-content.png)

5. Provide a **Subject Line** ("Upgrade Offer for Basic plan members") and click on the **Edit email body** button

   ![Add subject line and edit email body](assets/add-email-activities-subject-line-edit-body.png)

6. There are many options, for this test, choose **Code your own** HTML option

   ![Choose Code your own HTML option](assets/add-email-activities-code-your-own-html.png)

7. In the **Email Designer**, insert a test line "Upgrade Offer Available!" just before the `</body></html>` tags as shown and click on **Save**

   ![Insert test line in Email Designer and click Save](assets/add-email-activities-email-designer-save.png)

8. Wait for the confirmation message to appear at the bottom-right corner

   ![Confirmation message appears](assets/add-email-activities-confirmation-message.png)

9. Click on the **left arrow** next to the **Email Designer** to exit

   ![Click left arrow to exit Email Designer](assets/add-email-activities-exit-email-designer.png)

10. A confirmation dialog pops up, click on the **Save & close** button

   ![Confirmation dialog with Save & close button](assets/add-email-activities-save-and-close-dialog.png)

11. Review the Email properties and actions including the text added to the Email body. Click on the **left arrow** to navigate back to the campaign canvas

![Navigate back to Campaign canvas](assets/add-email-activities-back-to-campaign-canvas.png)

## Add bottom branch email activity

Back in the campaign canvas, click on the **+** of the bottom flow and select **Email** from the **Channel activities**. Follow the same steps as above (Steps 2 to 11) except for the following:

- Rename the label to **Email using Target Dimension** for the **Email** activity
- In the Email settings, choose the **Relational-Email** Email channel config

![Second Email activity configured with Relational-Email channel](assets/add-email-activities-bottom-branch-relational-email.png "Add the second Email activity")

## Recap

You have now seen how to configure the Email activities with the Email channels. Each activity was then configured with a very basic Email subject and body. The entire campaign will be tested next.
