---
title: Create Property
description: Create Property
doc-type: article
solution: Experience Platform
exl-id: eabd5f75-7706-4c96-982e-2512509bdc55
---

We want to forward an Experience Event out to usually to a third party (but doesn't have to be). This is usually used when a copy of an Event is needed in real time to notify a third party under specific circumstances (e.g. notifying Google, Meta or TikTok about a purchase).

>[!NOTE]
>
>Reminder: A Property contains all the extensions, data elements and rules needed to decide what to forward and where to

1. In the left rail click on Event Forwarding
1. Then click on New Property

![Create a new event forwarding property.png "Create a new event forwarding property"](assets/k7JN8MLoMC2Etju1-MWzS_create-a-new-event-forwarding-property.png "Create a new event forwarding property")

3\. Update the property name using the following formula: `Event Forward Property SB + [sandbox number]`. Your final name would look something this then:  **Event Forward Property SB01**

4\. Click **Save **when done

![Name your event forwarding property](assets/name-your-event-forwarding-property.png)

# Install Extension

1. Click on the Event Forwarding Property you just created

![Open your event property.png "Open your event property"](assets/RrKFiZYz4ZMPtRucKXK0a_open-your-event-property.png "Open your event property")



2\. You should see a screen like below.  Click on **Extensions**.

![JqDF19 1UFH4mp you should no see a screen like below click on extensions](assets/you-should-no-see-a-screen-like-below-click-on-extensions.png)



3\. Install the extension Adobe Cloud Connector by doing the following:

1. Click on **Catalog **in the top nav
1. Click on the **Adobe Cloud Connector** card
1. In the right rail click on the **Install **button

![Install adobe cloud connector extension](assets/install-adobe-cloud-connector-extension.png)



After clicking install you should see the extension show under the Installed extensions for your property as shown below

![Fully installed extension.png "Fully installed extension"](assets/i2q46bSaoeqEPM1NMJvDy_fully-installed-extension.png "Fully installed extension")

## Create Data Element

>[!NOTE]
>
>A Data Element references the incoming event and can parse it into multiple individual components if needed

1. In the left rail click on **Data Elements**



![PgvTpfsHh navigate to data elements.png "Navigate to data elements"](assets/h56zTjtJ97y_PgvTpfsHh_navigate-to-data-elements.png "Navigate to data elements")



2\. Click on the **Create New Data Element** button

![Create new data element.png "Create New Data Element"](assets/Cip9X6-PMjLIeFGD3KpUg_create-new-data-element.png "Create New Data Element")



3\. Configure the new data element with the following information:

| Element Type      | Value to Configure |
| ----------------- | ------------------ |
| Name              | Data Object        |
| Extension         | Core               |
| Data Element Type | Custom Code        |

![Step 1 of data element config.png "Step 1 of data element config"](assets/Plz9989MckNpE8iZj9g2Y_step-1-of-data-element-config.png "Step 1 of data element config")



4\. Click on the button **Open Editor** to add the following custom code:

![Open the editor.png "Open the editor"](assets/e-loRuF2wx-eNZixSibpf_open-the-editor.png "Open the editor")



5\. Add custom code to the editor like so and save it

```none
var xdm = arc?.event || '';
return xdm;
```

![TJG hd2g4ScvIP2RYKA custom code.png "Custom code"](assets/G_tJG-hd2g4ScvIP2RYKA_custom-code.png "Custom code")

>[!NOTE]
>
>This is grabbing the whole xdm object without doing any translations to the payload.  If needed we could parse out each individual pieces within the XDM object (e.g. page name, purchase amount), into one data element per field.  The reason for doing this might be if there is transformation of the structure to a different structure





6\. Click the **Save **button to save your data element.

![Click the save button to save your data elemen](assets/click-the-save-button-to-save-your-data-elemen.png)



When done you should see the following screen confirming your data element has been added:

![Data element saved to property](assets/data-element-saved-to-property.png)


## Create Rules

>[!NOTE]
>
>A Rule contains:
>
>1. Conditions on what to forward 
>2. Actions that can transform the payload and define where to send it



1. In the left rail click on **Rules**

![Click on rules in the left rail](assets/click-on-rules-in-the-left-rail.png)



2\. Then click on **Create New Rule**

![Create a new rule](assets/create-a-new-rule.png)



3\. Update the rule name using the following formula: `"EF Rule SB" + [your sandbox number]` (i.e. EF Rule SB01. You can find your sandbox number in the top right of your browser window as shown below\...

![9WxgiCpB 3 image](assets/create-property-1.png)

4\. Click **Save **when done

>[!NOTE]
>
>Make sure your rule name follows the formula pattern of "EF Rule

![Z4fD1KSWQ add name to rule.png "Add name to rule"](assets/FA-CkRxTIGR_Z4fD1KSWQ_add-name-to-rule.png "Add name to rule")



5\. Add an Action to your rule by click on the (+) sign to add a new action

![Add an action.png "Add an action"](assets/DiTGVvpE4CoNzoikmLyNv_add-an-action.png "Add an action")

## **Get Webhook URL (to use in action)**

>[!NOTE]
>
>We are going to use a webhook here so we can see if the data has arrived at the Destination we are sending to. In a real world scenario, we would log into that destination instead and use their tools to see what has arrived.



1. Open the following link in a new tab in your browser -> [https://webhook.site](https://webhook.site/)
1. Copy the unique URL you see and save it somewhere safe

![Webhooksite copy your unique url](assets/webhooksite-copy-your-unique-url.png)



3\. Configure your action with the following information:

| Setting     | Value                                                                                                                                                               |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Extension   | Adobe Cloud Connector                                                                                                                                               |
| Action Type | Make Fetch Call                                                                                                                                                     |
| Method      | Post                                                                                                                                                                |
| URL         | Use the same webhook URL you used when setting up your streaming destination.  You can find it by opening a new tab in the and navigating to Destinations -> Browse |
| Body        | Raw                                                                                                                                                                 |
| Body Data   | \{ "data": \{ "event": "\{\{Data Object\}\}" } }                                                                                                                      |

>[!NOTE]
>
>The \{\{Data Object\}\} referenced here is the Data Element we created earlier. Here the requirement by the downstream system was it wanted to wrap the event in a data object with an event object. You could put any formatting here.
>
>If we had split \{\{Data Object\}\} into multiple fields (e.g. page name, purchase, etc.), we could transform the JSON structure placing each field in the desired spot, giving us more control over matching the destination.





When you are done validate your screen looks similar to below and then click on **Keep Changes**

![KG5VJwRLos0xPJxTw9 configure the action.png "Configure the action"](assets/04_kG5VJwRLos0xPJxTw9_configure-the-action.png "Configure the action")



4\. When done you should see your action added to your rule. Click **Save **to continue.

![K6UcA8XcZ save your rule.png "Save your rule"](assets/9KrFJGCYfwo_k6UcA8XcZ_save-your-rule.png "Save your rule")

>[!WARNING]
>
>When we send an Experience Event, we are sending the Event, not the Profile, nor any of its attributes, including any Audience Qualifications (even if it is an Edge Audience).
>
>This happens for speed purposes.



## Publish the Changes

1. In the left rail click on **Publishing Flow**

![Navigate to the publishing flow.png "Navigate to the Publishing Flow"](assets/9KAVTxQk4W28iyCGGWsXE_navigate-to-the-publishing-flow.png "Navigate to the Publishing Flow")



2\. Click on the button **Add Library**

![Add library.png "Add library"](assets/yGg8fTMq1rzdv7JIQngwq_add-library.png "Add library")



3\. Configure the library with the following information:

- Name -> **EF Library**
- Environment -> **Development**
- Click on **Add All Changed Resources**


When done your screen should look similar to the below screenshot.  If everything looks good click on the **Save & Build to Development **button

![Configure the library and save and build](assets/configure-the-library-and-save-and-build.png)



4\. You should then see the development build go green stating its ready to use

![Sp9W2tJwMjepSuOtk you shou](assets/you-shou.png)

