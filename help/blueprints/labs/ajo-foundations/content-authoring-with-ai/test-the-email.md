---
title: Test the email
description: Learn how to send and verify proof emails in Adobe Journey Optimizer to validate personalized content and conditional variants before activation.
doc-type: article
solution: Experience Platform
exl-id: 1abab39e-811c-4010-a4f5-a7adc9e4e0a4
---

# Test the email

## Learning objectives

By the end of this module, you will be able to:

- Send proof emails from the Adobe Journey Optimizer email editor. 
- Validate personalized content and conditional variants using proof emails. 
- Verify proof email delivery in your inbox, including handling spam and clipped messages. 
- Review proof delivery logs, timestamps, and variants within Adobe Journey Optimizer. 
- Confirm that email content is accurate, personalized, and ready for activation.


## Send proof emails (optional, but recommended)

At this point, you have learned that we can not only personalize the profile attributes but also use attributes to create conditional logic that would determine the content you want to show. Adobe Journey Optimizer is extremely powerful and gives marketers a lot of flexibility. 

1. Click **Simulate Content**.
2. Select **Simulate content variation**.

![Clicking Simulate Content and selecting Simulate content variation](assets/content-simulation-click-simulate-content-variation.png)

A simulation panel opens.

3. Click **Send Proof**.

![Send Proof button in the simulation panel](assets/test-the-email-click-send-proof-button.png)

4. Add your own personal email address.

>[!NOTE]
>
>Note that at times your corporate email will block emails from the sandbox. I would recommend you to use your personal email. 



5. Select both variants.
6. Add Subject Line Prefix
   1. Variant 1: Above 40 
   2. Variant 2: Below 40 
7. Click **Send Proof**. You get a green confirmation message "**Proofs sent successfully**"

![Green confirmation message showing proofs sent successfully](assets/test-the-email-proofs-sent-successfully-confirmation.png)

Verify that both emails have landed in your inbox.

>[!NOTE]
>
>Proof emails may land in **Spam** depending on filters. 



![Proof email that landed in the Spam folder](assets/test-the-email-proof-email-in-spam-folder.png)

You may experience clipped message but it is fine, since some of the footer links are not real. If you click on the link you see both emails with variants have come through. 

![Clipped proof email showing both variants after clicking the link](assets/test-the-email-clipped-proof-email-variants.png)

### Verify proof delivery in AJO

Finally, you can also see proof delivery in Adobe Journey Optimizer.

1. Return to the email editor.
2. Go back to the email creation screen and click **View Proof**.
3. Review delivery logs, timestamps, and sent variants.

![View Proof button on the email creation screen](assets/test-the-email-click-view-proof-button.png)

You notice your proof email details. 

![Proof email delivery logs, timestamps, and sent variants in AJO](assets/test-the-email-proof-email-delivery-details.png)


## Recap

In this module, you successfully:

- Sent and verified proof emails in AJO

You have now completed the full Connection 5G AJO Lab Journey and validated that your email is accurate, personalised, and ready to activate.
