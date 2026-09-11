---
hold: true
title: Create Property
description: Create an Event Forwarding property with a data element and rule that forwards incoming experience events to a webhook endpoint.
doc-type: article
solution: Experience Platform
exl-id: eabd5f75-7706-4c96-982e-2512509bdc55
---

# Create Property

We usually want to forward an Experience Event out to a third party (though it doesn't have to be). This is usually used when a copy of an Event is needed in real time to notify a third party under specific circumstances (e.g. notifying Google, Meta or TikTok about a purchase).

>[!NOTE]
>
>Reminder: A Property contains all the extensions, data elements and rules needed to decide what to forward and where to

1. In the left rail click on Event Forwarding
2. Then click on New Property

![Event Forwarding section with the New Property button highlighted](assets/create-property-new-property-button.png "Create a new event forwarding property")

3. Update the property name using the following formula: `Event Forward Property SB + [sandbox number]`. Your final name would look something like this: **Event Forward Property SB01**

4. Click **Save** when done

![Event Forwarding property name field filled in with Save button highlighted](assets/create-property-name-property-form.png)

## Install extension

1. Click on the Event Forwarding Property you just created

![List of Event Forwarding properties with the newly created property highlighted](assets/create-property-open-new-property.png "Open your event property")



2. You should see a screen like below.  Click on **Extensions**.

![Event Forwarding property overview screen with the Extensions tab highlighted](assets/create-property-click-extensions-tab.png)



3. Install the extension Adobe Cloud Connector by doing the following:

4. Click on **Catalog** in the top nav
5. Click on the **Adobe Cloud Connector** card
6. In the right rail click on the **Install** button

![Extension Catalog with the Adobe Cloud Connector card and Install button highlighted](assets/create-property-install-cloud-connector-extension.png)



After clicking install you should see the extension show under the Installed extensions for your property as shown below

![Installed Extensions list showing the Adobe Cloud Connector extension successfully installed](assets/create-property-extension-installed-confirmation.png "Fully installed extension")

## Create data element

>[!NOTE]
>
>A Data Element references the incoming event and can parse it into multiple individual components if needed

1. In the left rail click on **Data Elements**



![Left rail navigation with the Data Elements link highlighted](assets/create-property-navigate-to-data-elements.png "Navigate to data elements")



2. Click on the **Create New Data Element** button

![Data Elements page with the Create New Data Element button highlighted](assets/create-property-create-new-data-element-button.png "Create New Data Element")



3. Configure the new data element with the following information:

| Element Type      | Value to Configure |
| ----------------- | ------------------ |
| Name              | Data Object        |
| Extension         | Core               |
| Data Element Type | Custom Code        |

![Data element configuration with Name, Extension, and Data Element Type fields set](assets/create-property-data-element-config-step-1.png "Step 1 of data element config")



4. Click on the button **Open Editor** to add the following custom code:

![Data element settings with the Open Editor button highlighted for custom code](assets/create-property-open-custom-code-editor.png "Open the editor")



5. Add custom code to the editor like so and save it

```none
var xdm = arc?.event || '';
return xdm;
```

![Custom code editor showing the script that returns the incoming XDM event object](assets/create-property-custom-code-added.png "Custom code")

>[!NOTE]
>
>This is grabbing the whole xdm object without doing any translations to the payload.  If needed we could parse out each individual pieces within the XDM object (e.g. page name, purchase amount), into one data element per field.  The reason for doing this might be if there is transformation of the structure to a different structure





6. Click the **Save** button to save your data element.

![Data element editor with the Save button highlighted](assets/create-property-save-data-element-button.png)



When done you should see the following screen confirming your data element has been added:

![Data Elements list showing the newly saved data element added to the property](assets/create-property-data-element-saved-confirmation.png)


## Create rules

>[!NOTE]
>
>A Rule contains:
>
>1. Conditions on what to forward 
>2. Actions that can transform the payload and define where to send it



1. In the left rail click on **Rules**

![Left rail navigation with the Rules link highlighted](assets/create-property-navigate-to-rules.png)



2. Then click on **Create New Rule**

![Rules page with the Create New Rule button highlighted](assets/create-property-new-rule-button.png)



3. Update the rule name using the following formula: `"EF Rule SB" + [your sandbox number]` (i.e. EF Rule SB01). You can find your sandbox number in the top right of your browser window as shown below\...

![Browser window top right corner showing the sandbox number used in the rule name](assets/create-property-sandbox-number-location.png)

4. Click **Save** when done

>[!NOTE]
>
>Make sure your rule name follows the formula pattern of `"EF Rule SB" + [sandbox number]`

![Rule name field filled in with the EF Rule sandbox naming pattern](assets/create-property-add-rule-name.png "Add name to rule")



5. Add an Action to your rule by clicking on the (+) sign to add a new action

![Rule editor with the plus icon highlighted to add a new action](assets/create-property-add-action-button.png "Add an action")

## Get webhook URL (to use in action)

>[!NOTE]
>
>This lab uses a webhook here so you can see if the data has arrived at the destination you are sending to. In a real world scenario, you would log into that destination instead and use its tools to see what has arrived.



1. Open the following link in a new tab in your browser -> [https://webhook.site](https://webhook.site/)
2. Copy the unique URL you see and save it somewhere safe

![Webhook.site page with the unique URL highlighted for copying](assets/create-property-webhooksite-copy-url.png)



3. Configure your action with the following information:

| Setting     | Value                                                                                                                                                               |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Extension   | Adobe Cloud Connector                                                                                                                                               |
| Action Type | Make Fetch Call                                                                                                                                                     |
| Method      | Post                                                                                                                                                                |
| URL         | Use the same webhook URL you used when setting up your streaming destination. You can find it by opening a new tab in the browser and navigating to Destinations -> Browse |
| Body        | Raw                                                                                                                                                                 |
| Body Data   | \{ "data": \{ "event": "\{\{Data Object\}\}" } }                                                                                                                      |

>[!NOTE]
>
>The \{\{Data Object\}\} referenced here is the Data Element you created earlier. Here the requirement by the downstream system was it wanted to wrap the event in a data object with an event object. You could put any formatting here.
>
>If we had split \{\{Data Object\}\} into multiple fields (e.g. page name, purchase, etc.), we could transform the JSON structure placing each field in the desired spot, giving us more control over matching the destination.





When you are done validate your screen looks similar to below and then click on **Keep Changes**

![Rule action configured with Adobe Cloud Connector Make Fetch Call settings and webhook URL](assets/create-property-configure-action-settings.png "Configure the action")



4. When done you should see your action added to your rule. Click **Save** to continue.

![Rule editor showing the configured action with the Save button highlighted](assets/create-property-save-rule-button.png "Save your rule")

>[!WARNING]
>
>When you send an Experience Event, you are sending the Event, not the Profile, nor any of its attributes, including any Audience Qualifications (even if it is an Edge Audience).
>
>This happens for speed purposes.



## Publish the changes

1. In the left rail click on **Publishing Flow**

![Left rail navigation with the Publishing Flow link highlighted](assets/create-property-navigate-to-publishing-flow.png "Navigate to the Publishing Flow")



2. Click on the button **Add Library**

![Publishing Flow page with the Add Library button highlighted](assets/create-property-add-library-button.png "Add library")



3. Configure the library with the following information:

- Name -> **EF Library**
- Environment -> **Development**
- Click on **Add All Changed Resources**


When done your screen should look similar to the below screenshot.  If everything looks good click on the **Save & Build to Development** button

![Library configuration with name, Development environment, and Save & Build to Development button](assets/create-property-configure-library-save-and-build.png)



4. You should then see the development build go green stating it's ready to use

![Publishing Flow showing the Development build status turned green and ready to use](assets/create-property-development-build-ready.png)
