---
title: Configure SMS Message
description: Configure SMS Message
doc-type: article
solution: Experience Platform
exl-id: e6673838-958b-41da-b725-8fc8378a59a5
---

# Add SMS Activity

The goal of adding SMS message step is to target opt-in users who have multiple active lines on their account, while intentionally excluding the primary line. The activity identifies accounts with two or more active lines and delivers the SMS only to the secondary lines (such as dependent or kids’ lines). This approach is commonly used for:

- Device upgrade reminders 
- Usage or threshold alerts 
- Add-on or accessory promotions 
- Messages specifically intended for dependent lines 

This ensures relevant communication reaches the right users and prevents over-messaging the primary account holder, who typically already receives account-level notifications.

On the canvas, add an **SMS **activity to the **second branch **of the **Split **activity.


## **Configure the SMS Activity**

1. Click **Create/Edit SMS** on the activity card to begin configuring the message.

![Image](assets/51BN2aLaItaR3eMVJQATB_image.png)

1. On the **Actions** tab, select an SMS configuration from the dropdown. (**Note:** This is the same configuration completed in the previous exercise). 

![TqCojTab2X5Rl   image](assets/pSDIN_TqCojTab2X5Rl-__image.png)

>[!NOTE]
>
>If no configuration is available, make sure to complete the [Configure SMS Message](../../orchestrated-campaigns/flagship-phone-launch/configure-sms-channel.md) lab to see the required configuration under this option. 

## **Compose SMS Message**

Create your message and add personalization fields.

1. Click the **Edit content **button, or navigate directly to the **Content **tab. 

![Image](assets/1kw6sL8YdFKLjTJe6JX3k_image.png)

1. Use the **Personalization** button to insert attribute fields.. 

![5Q7S7Ew iQF8FzqlJ image](assets/Zz-_5Q7S7Ew_iQF8FzqlJ_image.png)

1. If preferred, you can add personalization by navigating through **Target attributes**:
   - Expand entities under the **Target Dimension** 
   - Select the fields to include in the message or simply paste the following text. 

>Hi 
>\{\{ target.dep\_rel\_customer\_account.first\_name\}\}
>Your line \{\{target.dep\_rel\_customer\_line.mobile\_phone\}\}
>using a \{\{target.dep\_rel\_customer\_line.product\_lookup.model\}\} : \{\{target.dep\_rel\_customer\_line.product\_lookup.make\}\} is eligible for an upgrade.

1. Click **validate **on the editor and make sure there are no validation errors. 

![R4G7PW10het image](assets/uJ28sEiDi_R4G7PW10het_image.png)

1. Click **Save**.(Might have to scroll to the right view this button). 

![Image](assets/K6wjPdjmjqp4q0YWvBEFm_image.png)

## Preview SMS Content

After saving, you will return to the activity view where the **SMS preview** displays your configured message as below. 

![Image](assets/mw8bGhK67SwdJnTzROd1b_image.png)

## Save Orchestration. 

- Navigate back to the Canvas using the back button on the top left button and click **Save**. 

![Image](assets/8AOl8jgSzRmICp4nn0kdP_image.png)

