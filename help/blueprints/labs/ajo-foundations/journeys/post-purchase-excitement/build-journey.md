---
hold: true
title: Build Journey
description: Build Journey
doc-type: article

solution: Experience Platform
exl-id: 4dd15071-51e5-445a-932d-690d9a73a913
---

# Learning Objective

Create a unitary journey that begins with the configured Order Shipped event, gets the ETA from an external service and sends an email.

## Create Journey

Go to **Journeys **and click **Create Journey - Create from scratch**

![RaGUUvFOSPhdhWYohoZ3T 20251112 205319](assets/raGUUvFOSPhdhWYohoZ3T-20251112-205319.png)



## Journey Properties

1. Update the Journey Properties in the right rail with the following:
   - **Name**: `Order Shipped Journey`
   - **Description**: `Notify customer that order has shipped. Include shipping details.`
   - **Tags**: `Default`
   - **Journey m****etrics**: *leave blank*

>[!NOTE]
>
>**Empty Drop Down?**
>
>Don't worry and move on. The very first journey created in a sandbox needs to "prime the pump".  Once we publish the journey, this drop down will have options to choose from.

**Allow reentrance**: `checked`

**Reentrance wait period:**  `5 minutes`

**Access labels**: *leave blank*

**Time Zone**: `Your Local timezone`


**Use Profile time zone in waits and conditions**: `NOT checked`

**Start/End Date**: *leave blank*

**Timeout or error**: `30`

**Capping rules:** *leave blank*

**Priority**: `0`



1. If everything looks good click the **Save **button

![MLQgSI5VZ6ayZeen 20251113 011132](assets/PEKi_MLQgSI5VZ6ayZeen-20251113-011132.png)




## Journey Canvas

## Add a Unitary Event

From the left pane under the **Events menu** drag 'n drop the **orderShipped **event onto the canvas as shown below

![48Vp2fxzZi18gKAc6RLW  20251113 012116](assets/48Vp2fxzZi18gKAc6RLW--20251113-012116.png)



![Lmn6jKE1hVlRvKw35tCVT 20251113 012227](assets/lmn6jKE1hVlRvKw35tCVT-20251113-012227.png)





## Add a Custom Action

1. If the left pane expand the **Actions menu** and then drag 'n drop onto the canvas the action you built named **GetShippingDetails **after the orderShipped event

![E8 e zCT 20251113 012517](assets/DCaEsLhrw6V7_E8-e-zCT-20251113-012517.png)

1. In the right rail, under Access and privacy configuration --> Marketing Action drop-down ensure the value is set to **None**

![Image](assets/sGs1WlhaNBhmUJrKOvd-g_image.png)

1. Under the Endpoint configuration --> Query Parameters menu click on the **Pencil icon** next to orderid

![YAaVRitMmP9hKpa3Q 20251121 192339](assets/rYX_yAaVRitMmP9hKpa3Q-20251121-192339.png)

1. In the modal that appears expand **Context **-> **orderShipped **-> **Order **and then select **Order ID (orderID) **and click **OK**

![NwJ7  20251113 013041](assets/bxa225WAk-ITAa8_NwJ7--20251113-013041.png)

1. Back in the right rail, ensure the option for Timeout or error is **unchecked **and then click the **Save button**

![KJCyB6WTtNyGhF2CC5cdX 20251117 231216](assets/kJCyB6WTtNyGhF2CC5cdX-20251117-231216.png)



## **Add Email Action**

1. Under the Actions menu drag 'n drop the **Action **action onto the canvas after the GetShippingDetails action

![EHlfUwB4FUguiZ38Wi7LV 20260610 171228](assets/eHlfUwB4FUguiZ38Wi7LV-20260610-171228.png)

1. Select **Email **for the marketing action, then **Add**.

![LsRb 20260615 094254](assets/FEZlIvih4P2bdzkw_LsRb-20260615-094254.png)

1. In the right rail, click **Configure action**

![9 20260615 094515](assets/21LK4kE4IaXibzcUMhB_9-20260615-094515.png)

1. set **Email channel Configuration **to `Profile-Email` and then click on **Edit Content**

![HQEokhDKs5xAZra7MaPg9 20260615 094856](assets/hQEokhDKs5xAZra7MaPg9-20260615-094856.png)



## Add Email Body Content

For content, you are going to keep things simple. Like stupid simple.

1. Update the Subject line to `Order Shipped`and then click on the **Edit email body button**

![FKmn1 vVHrim0K9CwfBTV 20251117 231415](assets/FKmn1-vVHrim0K9CwfBTV-20251117-231415.png)

1. In the top bar click on the **Design from Scratch **content block

![6vtCM 7SERuC85HW7XJ 20251117 231709](assets/8_6vtCM_7SERuC85HW7XJ-20251117-231709.png)

1. From the left bar under the Structure container drag 'n drop the **1:1 Column **onto the canvas

![6dhPFQYOdTHlRw2swYNVW 20251113 180605](assets/6dhPFQYOdTHlRw2swYNVW-20251113-180605.png)

1. Then under the Contents container drag 'n drop the **Text **component into your** 1:1 Column**

![R5k4g3L9OQ6ldTmyWqkqj 20251113 180642](assets/R5k4g3L9OQ6ldTmyWqkqj-20251113-180642.png)

1. Click into the Text component and **delete the current text** and then click the **Add Personalization **icon

![KkU 20251113 180737](assets/g1PJXYbo3KeJ4FnAX_KkU-20251113-180737.png)

1. In the left rail click on the **Contextual Attributes** folder and then navigate thru **Journey Orchestration** -> **Actions **and select **GetShippingDetails**

![EpgPQiob6ESay4BzP9ilp 20251113 180824](assets/EpgPQiob6ESay4BzP9ilp-20251113-180824.png)

1. In the main body of the email now **copy & paste** the below JSON into the Personalization **editor**

```json
{{profile.person.name.firstName}}, your order has shipped
ETA: 
Tracking Number: 
```

1. Add the personalization fields as follows (**click the plus '+' sign next to the field on the left rail**):
   - **ETA: ** `eta`
   - **Tracking Number:**  `tracking_number`

![54bDWrDigSBU6GsKrKDAO 20251121 193136](assets/54bDWrDigSBU6GsKrKDAO-20251121-193136.png)

>[!NOTE]
>
>Click the **+ symbol** to add personalization attributes from the rail to the canvas.  It will place them where your cursor is so ensure you are "lined up" appropriately

>[!NOTE]
>
>Your email will use a combination of context attributes (ETA & tracking number) and Profile attributes (first Name). If you wanted to add other Profile attributes, you can click on the Profile Attributes tab and select anything you see.
>
>![VMjj8RIOkqFVcqrc7SU5b 20251119 011923](assets/VMjj8RIOkqFVcqrc7SU5b-20251119-011923.png)

1. On the bottom of the screen click the **Validate **button and ensure you have no errors

![DXZ9kxZKWZzBRR3WDdtbN 20251117 232100](assets/dXZ9kxZKWZzBRR3WDdtbN-20251117-232100.png)

1. If everything looks good click the **Save button **in the top right
1. Then click the **Save **button again in the top right and click the **\<- left arrow** in the top left

![GEau2 20251113 181826](assets/oDLQWz6U6NQE7Iz_gEau2-20251113-181826.png)

1. Finally, click the **\< Back icon **in top left to get back to the Journey Canvas

![8jWIbwxPB 5XZ8rq 20251113 182114](assets/fTHS_8jWIbwxPB-5XZ8rq-20251113-182114.png)

1. And then click the **Back **button again...

>[!TIP]
>
>Kidding! Thats was the last back button.....in this section 😜



## Override Email Parameters

Back on the main Journey Canvas, on the Email node, make sure you can see the read-only fields (you may need to click on the **Show read-only fields** icon)

![T9irNGuprlOaUDddCff1R 20251223 223958](assets/t9irNGuprlOaUDddCff1R-20251223-223958.png)

1. Scroll down to **Email Parameters **and click on the **Enable parameter override **icon

![TbwfBth tFmGR 20251223 224153](assets/ftkJuiy_TbwfBth_tFmGR-20251223-224153.png)

1. Click in the empty text box and then in the left rail drill down into **Context **-> **orderShipped **-> **\_dep **and click on the **personalEmail **field.  Then click the **OK button**

![TzhJOLofP 5pzYYO8aVJ  20251223 224541](assets/tzhJOLofP-5pzYYO8aVJ--20251223-224541.png)

>[!WARNING]
>
>This is a dangerous thing to do so avoid using it unless you need to in a production setting.  This will override the default location that Journeys looks for on the profile to execute messages.



1. Click the **Save button **in the top right and then click the **back arrow** \<- in the top left to **close **the Journey

![AR2 pJ8hT4GJh0D2vGP3J 20251117 232350](assets/aR2-pJ8hT4GJh0D2vGP3J-20251117-232350.png)

## Recap

A published journey capable of responding to the Order Shipped event trigger, get the ETA from an external service and send an email.
