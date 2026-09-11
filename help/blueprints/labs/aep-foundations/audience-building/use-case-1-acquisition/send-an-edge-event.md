---
title: Send an Edge event
description: Send an unauthenticated web event to the Edge via Postman and trace it through event forwarding, profile ingestion, audience qualification, and destination activation.
doc-type: article
solution: Experience Platform
exl-id: 465d09da-e30f-404c-8778-5df06e5a199f
---

# Send an Edge event

Now that everything is configured, send in an event to the Edge to see it all work. To do this, use Postman to send a Web Event to the Datastream you created. This sends in an event **with no OAuth Token** to simulate a page view coming in from the web to the Edge.  Ensure you have Postman open on your machine to perform this lab.

>[!NOTE]
>
>Because you are not passing in an authenticated token, you don't get back any attributes.

## Lab expectations

1. Experience Event to hit the Edge
1. Datastream configuration to use Event Forwarding Service
1. Event Forwarding to send the Event to the webhook
1. Datastream configuration to use AEP Service
   1. Edge Audience to run
   2. Send Event to the Hub
1. Postman Response to include Edge Audience (but no attributes)
1. Profile Store to receive event and add an Event Profile Fragment
1. Identity Store to add a relationship
1. Dataset to receive data and store in Data Lake
1. Streaming Audiences to evaluate and store results on Profile on Hub
1. Custom Personalization Destinations to send any Streaming Audiences "entries" back to Edge
1. HTTP API Destinations to send any Streaming Audiences "entries" to the webhook
1. Eventually HTTP API Destinations to send any Streaming Audiences "exits" to the webhook
1. Eventually Custom Personalization Destinations to send any Streaming Audiences "exits" to the Edge



## Navigate to the call

1. **Postman Left Sidebar**  -> Collections
1. **Collection** -> AEP Foundations Bootcamps (Labs)
1. **Folder** -> Profile Lab
1. **API Request** -> Create Web Event Edge (No Auth)

![Open the Create Web Event Edge (No Auth) request in Postman](assets/send-an-edge-event-navigate-to-the-postman-call.png)

## Modify API request

If you have already done this, you can skip down to Execute the API.

Before you can execute the API request you need to add some additional pieces of information to the request. Start by gathering the following values:

## Gather the datastream ID

1. In the left rail click on **Datastreams** (under the Data Collection heading)
1. Select your Datastream and copy the **Datastream ID** value

![Copy the Datastream ID value](assets/send-an-edge-event-gather-datastream-id.png)

## Update Postman query param

1. In the request itself click on **Params**
1. Update the **Value** with the datastream ID from the previous step
1. Click the **Save** button to save your update
1. Change email to your email

![Update the Params value with the datastream ID and click Save](assets/send-an-edge-event-update-datastreamid.png)

![Change the email value in the request body to your own email](assets/send-an-edge-event-change-email-to-your-email.png)

## Execute the API

Execute your request by clicking the **Send** button. 

![Successful 200 OK response returned from the Edge Network](assets/send-an-edge-event-successful-response-from-edge.png)



What you should see coming back in the response are these core things:

- A 200 OK response means the data was successfully sent and accepted by the Edge Network
- In the payload response you should also see the following:
  - the destinationId of the Custom Personalization destination you set up
  - the alias name of that destination (yours was called customPersonalization)
  - any of the segments the profile qualified for that exist on the edge

>[!NOTE]
>
>Any streaming and batch segments don't show until they are evaluated at the hub first

>[!NOTE]
>
>If you were sending to server.adobedc.net using a bearer token you would also see the attribute you configured in the Custom Personalization Destination

## Errors you might encounter

Below is an example of an error you may encounter. This means the edge segmentation evaluation is not yet available to evaluate the data being sent into the edge network.

```none
"errors": [
        {
            "type": "https://ns.adobe.com/aep/errors/EXEG-0203-502",
            "status": 502,
            "title": "The service call has failed.",
            "detail": "An error occurred while calling the 'com.adobe.experience_platform.edge_segmentation' service for this request. Try again.",
            "report": {
                "eventIndex": 0
            }
        }
    ]
```

## Validate event forwarding

On webhook.site you should immediately see the same payload body you sent via your Postman request appear. 

![Payload appears on webhook.site after event forwarding](assets/send-an-edge-event-payload-appears-on-webhook-site.png)

>[!NOTE]
>
>Notice the payload has added the geo lookup information you asked for when you set up the datastream you used in your edge setup

## Look up the Profile

In Adobe Experience Platform look up the profile you just sent in from the event you just sent into the Edge Network.  Navigate to Profiles -> Browse to perform the lookup using the following information:

- Merge policy -> Default Time-based
- Identity Namespace -> Email
- Identity Value -> edge-email\@dep.com



1. Click **View** to look up the profile
1. Click on the **Profile ID** to open the profile

   ![Look up the profile and click the Profile ID to open it](assets/send-an-edge-event-lookup-profile.png)



3. Click on **Events** in the top nav and you can see the event you just sent in

   ![View the event in the Events tab of the profile](assets/send-an-edge-event-view-the-profile-event.png)



4. Validate the Profile has qualified for the Audiences by reviewing the Audience Membership tab in the top nav.  You should see the following:

- Any Event Edge (within last 15 minutes)
- Any Event Streaming (within the last hour)
- From use case #1 you should also see the audiences of:
  - Visited iPhone 14 Page but Not Owns/Ordered it
  - Visited iPhone 14 Page

![Profile qualified for the Visited iPhone 14 Page audiences](assets/send-an-edge-event-visited-iphone-14-page.png)

## Validate streaming destination activation

Check your webhook to see if the streaming destination you configured has activated any segments.  They should appear in \~5 minutes.

![Validate the streaming destination activated segments on the webhook](assets/send-an-edge-event-validate-streaming-destination-activation.png)

>[!NOTE]
>
>Streaming Destinations may send another segment qualification payload if the two identities have not linked yet.

If ECID and email have not yet linked, a few minutes after that, another payload may appear with the same values except identityMap will now have two identities (email & ecid)

Over time you should begin to receive more payloads out to the webhook for "exited" status.

![Webhook payload showing an "exited" status for the streaming destination](assets/send-an-edge-event-webhook-exited-status-payload.png)

## How to interpret all the checks

1. Check for 200 response in Postman (properly formatted payload)
1. Check if the webhook has the event (properly configured Event Forwarding)
1. Check if the Profile has the events (properly configured AEP Service, event received and processed event on the Hub)
1. Check if the Profile has two identities (Identity Graph has linked on the Hub)
1. Check if the Profile qualified for the audiences (properly defined audience)
1. Check if the webhook received the Streaming Audiences (properly configured HTTP API Destination)
1. Check if Postman response includes segments (properly configured Custom Personalization Destination)
1. Check if Data Lake has log of sending (properly configured and sent Audience Qualification and Streaming Destination). See Below.

## Data Lake "Log" of destinations

After at least 60 minutes you can even check your dataset has the event you sent. To do so perform the following query using Query Service.

Change the table name below to the one from your sandbox. To find it, go to your dataset list and filter on "`dest`", open the dataset and copy the table name on the right rail.

```sql
SELECT * FROM profile_export_for_destination_merge_policy_xxx
WHERE extSourceSystemAudit.LASTREFERENCEDDATE >= CURRENT_DATE
AND identitymap['email'][0].ID in ('edge-email@dep.com')
ORDER BY extSourceSystemAudit.LASTREFERENCEDDATE DESC
LIMIT 10
```
