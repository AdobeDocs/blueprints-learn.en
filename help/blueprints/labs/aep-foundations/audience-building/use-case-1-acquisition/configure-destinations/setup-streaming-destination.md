---
title: Setup Streaming Destination
description: Configure an HTTP API streaming destination with a webhook endpoint, governance policy, audiences, and field mappings to test segment activation.
doc-type: article
solution: Experience Platform
exl-id: c52d301f-b308-40fc-a59c-ace1c96ccd13
---

>[!NOTE]
>
>Skip to the next step you have already configured your streaming destination!

# Get Webhook URL

>[!NOTE]
>
>We are going to use a webhook here so we can see if the data has arrived at the Destination we are sending to. In a real world scenario, we would log into that destination instead and use their tools to see what has arrived.

1. Open the following link in a new tab in your browser -> [https://webhook.site](https://webhook.site/)
1. Copy the unique URL you see and save it somewhere safe

![Webhooksite copy your unique url.png "Webhook.site copy your unique URL"](assets/FZjiu3ESI1tSWn5jTMHeH_webhooksite-copy-your-unique-url.png "Webhook.site copy your unique URL")


## Configure HTTP API Destination

>[!NOTE]
>
>We are using a Streaming Destination as a proxy for sending this data to a 3rd party (e.g. Facebook). In a real world scenario, you would use a Facebook Destination in place of an HTTP API Destination to send data to Facebook.

In the Experience Platform UI navigate to the destinations catalog by doing the following

1. Click on **Destinations **in the left rail
1. Click on **Catalog **on the top rail
1. In the search box enter **http**
1. Click on the **Set up** button to configure the HTTP API destination

![LxxLyKc0x1oi RQE8bk1LfsgmlXTfh1LP8 20241025 023030.png "Navigate to the HTTP API destination and intitiate the setup"](assets/n-ADAXZy_lxxLyKc0x1oi-RQE8bk1LfsgmlXTfh1LP8-20241025-023030.png "Navigate to the HTTP API destination and intitiate the setup")

>[!NOTE]
>
>You are using the HTTP API streaming destination for the lab(s) to demonstrate how a real world streaming connector would work.

###

## Configure

1. Connection type **None**
1. Click on **Connect to destination**

![Qalu26TqOpYn connect to destination.png "Connect to destination"](assets/ceOAAC2J_qalu26TqOpYn_connect-to-destination.png "Connect to destination")

>[!NOTE]
>
>Typically we would add any authentication credentials at this stage, but none are required for this webhook.



3\. Fill in the configuration details of your destination as follows:

- **Name **-> `Streaming DEP Webhook - [Your Initials]`
- **Description **->  `[your webhook endpoint you copied above]`
- **Endpoint **-> ` [your webhook endpoint you copied above]`
- **Query Parameters** -> `leave blank`
- **Headers **-> `leave blank`
- Include segment names -> toggle on
- Include segment timestamps -> toggle on

When done ensure your configure matches what you see below.  If it looks good click the **Next **button in the upper right to continue to the next step

![LxxLyKc0x1oi 04Lph 8tmJSFqHA6LPvzY 20241021 201004](assets/setup-streaming-destination-1.png)

>[!CAUTION]
>
>The endpoint, header and query params cannot be changed in the UI once saved

###

## Define Governance

1. Select **Cross Site Targeting** from the Marketing Actions
1. When done click the **Next **button to continue to the next step

![Governance screen for destinations.png "Governance screen for destinations"](assets/c76F7Kf1wV-YD8NridS1w_governance-screen-for-destinations.png "Governance screen for destinations")

>[!NOTE]
>
>You can learn more about governance policies in Experience League
>
>[https://experienceleague.adobe.com/docs/experience-platform/data-governance/policies/overview.html?lang=en#core-actions](https://experienceleague.adobe.com/docs/experience-platform/data-governance/policies/overview.html?lang=en#core-actions)

###

## Select Audiences

1. Select all audiences
1. When done click the **Next **button to continue to the next step

![Select all audiences](assets/select-all-audiences.png)

## Add Mappings

>[!NOTE]
>
>Here we are adding a field from Profile. If that field has no data, we may see nothing passed to the Destination. Multiple updates over time across Profile and Events sometimes can cause the Destination to trigger multiple times and send multiple payloads.

1. Click on **Add new field **to add a field to the schema
1. Type **model** into the schema field input box and select the** \_dep.activeProducts\[0].model **field from the list of fields that appears
1. Change the **\[0]** to **\[\*] **in the field name.  Your final field should now show as **\_dep.activeProducts\[\*].model**
1. When done click the **Next **button to continue to the next step



![Select model field.png "Select Model Field"](assets/0A43ygDjMcBwAohd-5Hda_select-model-field.png "Select Model Field")



![Final model field.png "Final Model Field"](assets/Q2qButkM8RGukEa-ku7nS_final-model-field.png "Final Model Field")

>[!NOTE]
>
>This is mapping a field on Profile, not Experience Event. Even though we are sending profiles to a Destination based on Audience Qualification, we have to keep in mind what is happening. 
>
>1. An event comes in 
>2. Audience qualifies the Profile based on rules 
>3. Qualification is stored on the Profile 
>4. The Destination is notified the Profile has qualified 
>5. The Destination sends the Profile What this means is when Destination goes to send the Profile it no longer has awareness of the Event that triggered the Audience evaluation.

###

## Review Step

Validate your final destination looks good and then click the **Finish **button

![Destination review screen.png "Destination review screen"](assets/YrD--mkpMGlzHBmWllgx6_destination-review-screen.png "Destination review screen")

>[!NOTE]
>
>The destination is now configured and waiting for segment qualifications from all the segments added based on their evaluation speeds:
>
>- Edge
>- Stream
>- Batch

>[!NOTE]
>
>When initially setting up a Destination the following are important to remember:
>
>- It takes up to 2hrs for any backfill (existing qualified profile) to start activating
>- It takes up to 20mins for a newly added audience to start activating

