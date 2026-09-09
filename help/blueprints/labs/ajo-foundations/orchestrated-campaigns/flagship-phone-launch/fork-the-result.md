---
title: Fork the Result
description: Learn how to add a Fork activity to an Orchestrated Campaign to branch a result for saving an audience and sending SMS messages.
doc-type: article
solution: Experience Platform
exl-id: 8f1d0839-e4ca-4b7c-bc97-4e271a457296
---

# Fork the Result

## Objective

This step is simple in that all you want to do is add a Fork activity such that you can duplicate the result to do two different things with it in future steps:

1. Save the audience for others to use for advertising or cross-channel purposes
1. Send SMS messages to the individual lines.



## Create the Fork

1. On the workflow canvas, click the **+** **icon** after Build Audience activity and select the **Fork Activity**

![Add a fork activity](assets/fork-the-result-4.png)



2. Update the names of each transition in the fork by click on the transition and then assigningthe names as outlined below:
   - **Top** --> `Save Audience`
   - **Bottom** --> `SMS`

![Update the transition names](assets/fork-the-result-1.png)



When done your canvas should now look like so...

![Final result with fork activity](assets/fork-the-result-3.png)

>[!NOTE]
>
>A fork activity essentially is just duplicating the result from the previous activity into two independent branches



3. Click **Save** on the top of the workflow canvas.

![Save your work](assets/fork-the-result-2.png)

>[!TIP]
>
>That was pretty difficult, wasn't it 😁



## Recap

Welp, you created a Fork of the result (i.e. duplicate the result) which allows you to clearly dictate a branch to process a Save Audience whereas the other one can be used for SMS sending. 

>[!NOTE]
>
>You need to use Forks especially if you plan to save the audience as a Save Audience activity does not allow activites to follow it.
