---
hold: true
title: Build journey
description: Build a unitary journey that responds to an Order Shipped event, calls a custom action for shipping ETA, and sends a personalized email.
doc-type: article
solution: Experience Platform
exl-id: 4dd15071-51e5-445a-932d-690d9a73a913
---

# Build journey

## Learning objective

Create a unitary journey that begins with the configured Order Shipped event, gets the ETA from an external service and sends an email.

## Create journey

Go to **Journeys** and click **Create Journey - Create from scratch**

![Create Journey - Create from scratch screen in Adobe Journey Optimizer](assets/build-journey-create-journey-from-scratch.png)



## Journey properties

1. Update the Journey Properties in the right rail with the following:
   - **Name**: `Order Shipped Journey`
   - **Description**: `Notify customer that order has shipped. Include shipping details.`
   - **Tags**: `Default`
   - **Journey metrics**: *leave blank*

      >[!NOTE]
      >
      >**Empty Drop Down?**
      >
      >Don't worry and move on. The very first journey created in a sandbox needs to "prime the pump".  Once we publish the journey, this drop down will have options to choose from.

   - **Allow reentrance**: `checked`

   - **Reentrance wait period:**  `5 minutes`

   - **Access labels**: *leave blank*

   - **Time Zone**: `Your Local timezone`

   - **Use Profile time zone in waits and conditions**: `NOT checked`

   - **Start/End Date**: *leave blank*

   - **Timeout or error**: `30`

   - **Capping rules:** *leave blank*

   - **Priority**: `0`



2. If everything looks good click the **Save** button

![Save button for the Journey Properties panel](assets/build-journey-save-journey-properties.png)




## Journey canvas

### Add a unitary event

From the left pane under the **Events menu** drag 'n drop the **orderShipped** event onto the canvas as shown below

![Drag the orderShipped event from the Events menu onto the journey canvas](assets/build-journey-drag-order-shipped-event-onto-canvas.png)



![Order Shipped event placed on the journey canvas](assets/build-journey-drag-order-shipped-event-onto-canvas--2.png)





### Add a custom action

1. If the left pane expand the **Actions menu** and then drag 'n drop onto the canvas the action you built named **GetShippingDetails** after the orderShipped event

![Drag the GetShippingDetails custom action onto the canvas after the orderShipped event](assets/build-journey-drag-getshippingdetails-action-onto-canvas.png)

2. In the right rail, under Access and privacy configuration --> Marketing Action drop-down ensure the value is set to **None**

![Marketing Action drop-down set to None in Access and privacy configuration](assets/build-journey-set-marketing-action-to-none.png)

3. Under the Endpoint configuration --> Query Parameters menu click on the **Pencil icon** next to orderid

![Pencil icon to edit the orderid query parameter in Endpoint configuration](assets/build-journey-edit-orderid-query-parameter.png)

4. In the modal that appears expand **Context** -> **orderShipped** -> **Order** and then select **Order ID (orderID)** and click **OK**

![Select Order ID (orderID) from the orderShipped Order context fields](assets/build-journey-select-order-id-context-field.png)

5. Back in the right rail, ensure the option for Timeout or error is **unchecked** and then click the **Save button**

![Timeout or error option unchecked with Save button highlighted](assets/build-journey-uncheck-timeout-or-error.png)



### Add email action

1. Under the Actions menu drag 'n drop the **Action** action onto the canvas after the GetShippingDetails action

![Drag the Action node onto the canvas after the GetShippingDetails action](assets/build-journey-drag-email-action-onto-canvas.png)

2. Select **Email** for the marketing action, then **Add**.

![Select Email as the marketing action and click Add](assets/build-journey-select-email-marketing-action.png)

3. In the right rail, click **Configure action**

![Configure action button in the right rail](assets/build-journey-click-configure-action.png)

4. set **Email channel Configuration** to `Profile-Email` and then click on **Edit Content**

![Email channel Configuration set to Profile-Email with Edit Content link](assets/build-journey-set-profile-email-channel-configuration.png)



### Add email body content

For content, you are going to keep things simple. Like stupid simple.

1. Update the Subject line to `Order Shipped` and then click on the **Edit email body button**

![Subject line updated to Order Shipped with Edit email body button](assets/build-journey-update-subject-line-order-shipped.png)

2. In the top bar click on the **Design from Scratch** content block

![Design from Scratch content block in the top bar](assets/build-journey-click-design-from-scratch.png)

3. From the left bar under the Structure container drag 'n drop the **1:1 Column** onto the canvas

![Drag the 1:1 Column structure element onto the email canvas](assets/build-journey-drag-1-1-column-onto-canvas.png)

4. Then under the Contents container drag 'n drop the **Text** component into your **1:1 Column**

![Drag the Text component into the 1:1 Column](assets/build-journey-drag-text-component-into-column.png)

5. Click into the Text component and **delete the current text** and then click the **Add Personalization** icon

![Add Personalization icon after deleting the default text](assets/build-journey-click-add-personalization-icon.png)

6. In the left rail click on the **Contextual Attributes** folder and then navigate thru **Journey Orchestration** -> **Actions** and select **GetShippingDetails**

![Select GetShippingDetails under Contextual Attributes - Journey Orchestration - Actions](assets/build-journey-select-getshippingdetails-contextual-attribute.png)

7. In the main body of the email now **copy & paste** the below JSON into the Personalization **editor**

```json
{{profile.person.name.firstName}}, your order has shipped
ETA: 
Tracking Number: 
```

8. Add the personalization fields as follows (**click the plus '+' sign next to the field on the left rail**):
   - **ETA:** `eta`
   - **Tracking Number:**  `tracking_number`

![ETA and Tracking Number personalization fields added to the email](assets/build-journey-add-eta-tracking-number-fields.png)

>[!NOTE]
>
>Click the **+ symbol** to add personalization attributes from the rail to the canvas.  It will place them where your cursor is so ensure you are "lined up" appropriately

>[!NOTE]
>
>Your email will use a combination of context attributes (ETA & tracking number) and Profile attributes (first Name). If you wanted to add other Profile attributes, you can click on the Profile Attributes tab and select anything you see.
>
>![Profile Attributes tab for adding additional profile attributes](assets/build-journey-profile-attributes-tab.png)

9. On the bottom of the screen click the **Validate** button and ensure you have no errors

![Validate button with no errors shown at the bottom of the screen](assets/build-journey-click-validate-button.png)

10. If everything looks good click the **Save button** in the top right
11. Then click the **Save** button again in the top right and click the **\<- left arrow** in the top left

![Save button and back arrow in the top right and top left](assets/build-journey-save-and-back-arrow.png)

12. Finally, click the **\< Back icon** in top left to get back to the Journey Canvas

![Back icon in the top left to return to the Journey Canvas](assets/build-journey-back-icon-to-journey-canvas.png)

>[!TIP]
>
>And then click the **Back** button again... Kidding! That's the last back button...in this section 😜



### Override email parameters

Back on the main Journey Canvas, on the Email node, make sure you can see the read-only fields (you may need to click on the **Show read-only fields** icon)

![Read-only fields shown on the Email node in the Journey Canvas](assets/build-journey-show-read-only-fields-email-node.png)

1. Scroll down to **Email Parameters** and click on the **Enable parameter override** icon

![Enable parameter override icon under Email Parameters](assets/build-journey-enable-parameter-override.png)

2. Click in the empty text box and then in the left rail drill down into **Context** -> **orderShipped** -> **\_dep** and click on the **personalEmail** field.  Then click the **OK button**

![Select the personalEmail field under orderShipped context _dep](assets/build-journey-select-personalemail-context-field.png)

>[!WARNING]
>
>This is a dangerous thing to do so avoid using it unless you need to in a production setting.  This will override the default location that Journeys looks for on the profile to execute messages.



3. Click the **Save button** in the top right and then click the **back arrow** \<- in the top left to **close** the Journey

![Save button and back arrow to close the Journey](assets/build-journey-save-and-close-journey.png)

## Recap

A published journey capable of responding to the Order Shipped event trigger, get the ETA from an external service and send an email.
