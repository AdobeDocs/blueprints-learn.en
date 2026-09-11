---
title: Fork the result
description: Learn how to add a Fork activity to an Orchestrated Campaign to branch a result for saving an audience and sending SMS messages.
doc-type: article
solution: Experience Platform
exl-id: 8f1d0839-e4ca-4b7c-bc97-4e271a457296
---

# Fork the result

## Objective

This step is simple in that all you want to do is add a Fork activity such that you can duplicate the result to do two different things with it in future steps:

1. Save the audience for others to use for advertising or cross-channel purposes
1. Send SMS messages to the individual lines.



## Create the Fork

1. On the workflow canvas, click the **+** **icon** after Build Audience activity and select the **Fork Activity**

   ![Add a Fork activity after the Build Audience activity](assets/fork-the-result-add-fork-activity.png)



2. Update the names of each transition in the fork by clicking on the transition and then assigning the names as outlined below:
   - **Top** --> `Save Audience`
   - **Bottom** --> `SMS`

   ![Fork transitions renamed to Save Audience and SMS](assets/fork-the-result-rename-transitions.png)



   When done your canvas should now look like so...

   ![Workflow canvas after adding the fork activity](assets/fork-the-result-final-canvas.png)

   >[!NOTE]
   >
   >A fork activity essentially is just duplicating the result from the previous activity into two independent branches



3. Click **Save** on the top of the workflow canvas.

![Save button on the workflow canvas toolbar](assets/fork-the-result-click-save.png)

>[!TIP]
>
>That was pretty difficult, wasn't it 😁



## Recap

Welp, you created a Fork of the result (i.e. duplicate the result) which allows you to clearly dictate a branch to process a Save Audience whereas the other one can be used for SMS sending. 

>[!NOTE]
>
>You need to use Forks especially if you plan to save the audience as a Save Audience activity does not allow activities to follow it.
