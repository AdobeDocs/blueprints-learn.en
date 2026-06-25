---
title: Create Property
description: Create Property
doc-type: article
exl-id: eabd5f75-7706-4c96-982e-2512509bdc55
---

We want to forward an Experience Event out to usually to a third party (but doesn't have to be). This is usually used when a copy of an Event is needed in real time to notify a third party under specific circumstances (e.g. notifying Google, Meta or TikTok about a purchase).

>[!NOTE]
>Reminder: A Property contains all the extensions, data elements and rules needed to decide what to forward and where to

1. In the left rail click on Event Forwarding
2. Then click on New Property

![](assets/k7JN8MLoMC2Etju1-MWzS_create-a-new-event-forwarding-property.png "Create a new event forwarding property")

3\. Update the property name using the following formula: `Event Forward Property SB + [sandbox number]`. Your final name would look something this then:  **Event Forward Property SB01**

4\. Click **Save **when done

![](assets/4J7C0ObhL864VrcW9Y52Y_name-your-event-forwarding-property.png)

##

# Install Extension

1. Click on the Event Forwarding Property you just created

![](assets/RrKFiZYz4ZMPtRucKXK0a_open-your-event-property.png "Open your event property")



2\. You should see a screen like below.  Click on **Extensions**.

![](assets/Tll5SU_jqDF19-1UFH4mp_you-should-no-see-a-screen-like-below-click-on-extensions.png)



3\. Install the extension Adobe Cloud Connector by doing the following:

1. Click on **Catalog **in the top nav
2. Click on the **Adobe Cloud Connector** card
3. In the right rail click on the **Install **button

![](assets/cSDjWqWyT9ss3ctkxGUNv_install-adobe-cloud-connector-extension.png)



After clicking install you should see the extension show under the Installed extensions for your property as shown below

![](assets/i2q46bSaoeqEPM1NMJvDy_fully-installed-extension.png "Fully installed extension")

##

# Create Data Element

>[!NOTE]
>A Data Element references the incoming event and can parse it into multiple individual components if needed

1. In the left rail click on **Data Elements**



![](assets/h56zTjtJ97y_PgvTpfsHh_navigate-to-data-elements.png "Navigate to data elements")



2\. Click on the **Create New Data Element** button

![](assets/Cip9X6-PMjLIeFGD3KpUg_create-new-data-element.png "Create New Data Element")



3\. Configure the new data element with the following information:

| Element Type      | Value to Configure |
| ----------------- | ------------------ |
| Name              | Data Object        |
| Extension         | Core               |
| Data Element Type | Custom Code        |

![](assets/Plz9989MckNpE8iZj9g2Y_step-1-of-data-element-config.png "Step 1 of data element config")



4\. Click on the button **Open Editor** to add the following custom code:

![](assets/e-loRuF2wx-eNZixSibpf_open-the-editor.png "Open the editor")



5\. Add custom code to the editor like so and save it

```none
var xdm = arc?.event || '';
return xdm;
```

![](assets/G_tJG-hd2g4ScvIP2RYKA_custom-code.png "Custom code")

>[!NOTE]
>This is grabbing the whole xdm object without doing any translations to the payload.  If needed we could parse out each individual pieces within the XDM object (e.g. page name, purchase amount), into one data element per field.  The reason for doing this might be if there is transformation of the structure to a different structure





6\. Click the **Save **button to save your data element.

![](assets/7EyVaXb-1Rh8g5QElpx46_click-the-save-button-to-save-your-data-elemen.png)



When done you should see the following screen confirming your data element has been added:

![](assets/qmVY2I441cXhBlVl174du_data-element-saved-to-property.png)

#

# Create Rules

>[!NOTE]
>A Rule contains:
>
>1. Conditions on what to forward 
>2. Actions that can transform the payload and define where to send it



1. In the left rail click on **Rules**

![](assets/fu-NB2g0dUtGeLf3MuAag_click-on-rules-in-the-left-rail.png)



2\. Then click on **Create New Rule**

![](assets/mijcmke51JNGaCShplPMv_create-a-new-rule.png)



3\. Update the rule name using the following formula: `"EF Rule SB" + [your sandbox number]` (i.e. EF Rule SB01. You can find your sandbox number in the top right of your browser window as shown below\...

![](assets/VD2t7zWQoJ_9WxgiCpB_3_image.png)

4\. Click **Save **when done

>[!NOTE]
>Make sure your rule name follows the formula pattern of "EF Rule

![](assets/FA-CkRxTIGR_Z4fD1KSWQ_add-name-to-rule.png "Add name to rule")



5\. Add an Action to your rule by click on the (+) sign to add a new action

![](assets/DiTGVvpE4CoNzoikmLyNv_add-an-action.png "Add an action")

##

## **Get Webhook URL (to use in action)**

>[!NOTE]
>We are going to use a webhook here so we can see if the data has arrived at the Destination we are sending to. In a real world scenario, we would log into that destination instead and use their tools to see what has arrived.



1. Open the following link in a new tab in your browser -> [https://webhook.site](https://webhook.site/)
2. Copy the unique URL you see and save it somewhere safe

![](assets/N2tCOnITCH4RfYeQ8gSdd_webhooksite-copy-your-unique-url.png)



3\. Configure your action with the following information:

| Setting     | Value                                                                                                                                                               |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Extension   | Adobe Cloud Connector                                                                                                                                               |
| Action Type | Make Fetch Call                                                                                                                                                     |
| Method      | Post                                                                                                                                                                |
| URL         | Use the same webhook URL you used when setting up your streaming destination.  You can find it by opening a new tab in the and navigating to Destinations -> Browse |
| Body        | Raw                                                                                                                                                                 |
| Body Data   | \{ "data": \{ "event": "\{\{Data Object}}" } }                                                                                                                      |

>[!NOTE]
>The \{\{Data Object}} referenced here is the Data Element we created earlier. Here the requirement by the downstream system was it wanted to wrap the event in a data object with an event object. You could put any formatting here.
>
>If we had split \{\{Data Object}} into multiple fields (e.g. page name, purchase, etc.), we could transform the JSON structure placing each field in the desired spot, giving us more control over matching the destination.





When you are done validate your screen looks similar to below and then click on **Keep Changes**

![](assets/04_kG5VJwRLos0xPJxTw9_configure-the-action.png "Configure the action")



4\. When done you should see your action added to your rule. Click **Save **to continue.

![](assets/9KrFJGCYfwo_k6UcA8XcZ_save-your-rule.png "Save your rule")

>[!WARNING]
>When we send an Experience Event, we are sending the Event, not the Profile, nor any of its attributes, including any Audience Qualifications (even if it is an Edge Audience).
>
>This happens for speed purposes.



##

# Publish the Changes

1. In the left rail click on **Publishing Flow**

![](assets/9KAVTxQk4W28iyCGGWsXE_navigate-to-the-publishing-flow.png "Navigate to the Publishing Flow")



2\. Click on the button **Add Library**

![](assets/yGg8fTMq1rzdv7JIQngwq_add-library.png "Add library")



3\. Configure the library with the following information:

- Name -> **EF Library**
- Environment -> **Development**
- Click on **Add All Changed Resources**


When done your screen should look similar to the below screenshot.  If everything looks good click on the **Save & Build to Development **button

![](assets/GGZB5FXdY7XjEDIRNwxAs_configure-the-library-and-save-and-build.png)



4\. You should then see the development build go green stating its ready to use

![](assets/3r5_sp9W2tJwMjepSuOtk_you-shou.png)

