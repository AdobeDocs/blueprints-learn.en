---
title: Test the Email
description: Learn how to send and verify proof emails in Adobe Journey Optimizer to validate personalized content and conditional variants before activation.
doc-type: article
solution: Experience Platform
exl-id: 1abab39e-811c-4010-a4f5-a7adc9e4e0a4
---

# Learning Objectives

By the end of this module, you will be able to:

- Send proof emails from the Adobe Journey Optimizer email editor. 
- Validate personalized content and conditional variants using proof emails. 
- Verify proof email delivery in your inbox, including handling spam and clipped messages. 
- Review proof delivery logs, timestamps, and variants within Adobe Journey Optimizer. 
- Confirm that email content is accurate, personalized, and ready for activation.


## Send Proof Emails (Optional, but recommended)

At this point, you have learned that we can not only personalize the profile attributes but also use attributes to create conditional logic that would determine the content you want to show. Adobe Journey Optimizer is extremely powerful and gives marketers a lot of flexibility. 

1. Click **Simulate Content**.
2. Select **Simulate content variation**.

![CHBaM4efsxWxR image](assets/content-authoring-with-ai-1.png)

A simulation panel will open.

3. Click **Send Proof**.

![Image](assets/test-the-email-4.png)

4. Add your own personal email address.

>[!NOTE]
>
>Note that at times your corporate email will block emails from the sandbox. I would recommend you to use your personal email. 



5. Select both variants.
6. Add Sublect Line Prefix
   1. Variant 1: Above 40 
   2. Variant 2: Below 40 
7. Click **Send Proof**. You will get green confirmation message "**Proofs sent successfully**"

![JkDe7m2wFduz1 image](assets/test-the-email-5.png)

Verify that you have received both email should land on your inbox.

>[!NOTE]
>
>Proof emails may land in **Spam** depending on filters. 



![Image](assets/test-the-email-6.png)

You may experience clipped message but it is fine, since some of the footer links are not real. If you click on the link you should see both emails with variants has come through. 

![Image](assets/test-the-email-1.png)

Verify Proof Delivery in AJO

1. Return to the email editor.
1. Click **View Proof**.
1. Review delivery logs, timestamps, and sent variants.

Finally, you can also see proof delivery in Adobe Journey Optimizer. 

Go back to email creation screen and click on "**View Proof**"

![Image](assets/test-the-email-2.png)

You will notice your proof email details. 

![Image](assets/test-the-email-3.png)


## Recap

In this module, you successfully:

- Sent and verified proof emails in AJO

You have now completed the full Connection 5G AJO Lab Journey and validated that your email is accurate, personalised, and ready to activate.
