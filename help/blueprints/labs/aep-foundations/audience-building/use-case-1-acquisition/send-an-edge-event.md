---
title: Send an Edge Event
description: Send an Edge Event
doc-type: article
solution: Experience Platform
exl-id: 465d09da-e30f-404c-8778-5df06e5a199f
---

Now that everything is configured, we can send in an event to the Edge to see it all work. To do this we will use Postman to send a Web Event to the Datastream we created. This will send in an event **with no OAuth Token** to simulate a page view coming in from the web to the Edge.  Ensure you have Postman open on your machine to perform this lab.

>[!NOTE]
>
>Because we are not passing in an authenticated token, we will not get back any attributes.

# Lab Expectations

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



## Navigate to the Call

1. **Postman Left Sidebar**  -> Collections
1. **Collection **-> AEP Foundations Bootcamps (Labs)
1. **Folder **-> Profile Lab
1. **API Request** -> Create Web Event Edge (No Auth)

![Navigate to the postman call](assets/navigate-to-the-postman-call.png)

## Modify API Request

If you have already done this, you can skip down to Execute the API.

Before you can execute the API request you need to add some additional pieces of information to the request. Start by gathering the following values:

## **Gather the Datastream ID**

1. In the left rail click on **Datastreams **(under the Data Collection heading)
1. Select your Datastream and copy the **Datastream ID** value

![Gather datastream id](assets/gather-datastream-id.png)

## Update Postman Query Param

1. In the request itself click on **Params**
1. Update the **Value **with the datastream ID from the previous step
1. Click the **Save **button to save your update

![Update datastreamid](assets/update-datastreamid.png)



Change email to your email

![O5DCKlW6oIADaE change email to your email](assets/change-email-to-your-email.png)

## Execute the API

Execute your request by clicking the **Send **button. 

![Successful response from edge](assets/successful-response-from-edge.png)



What you should see coming back in the response are these core things:

- A 200 OK response means the data was successfully sent and accepted by the Edge Network
- In the payload response you should also see the following:
  - the destinationId of the Custom Personalization destination you setup
  - the alias name of that destination (yours was called customPersonalization)
  - any of the segments the profile qualified for that exist on the edge

>[!NOTE]
>
>Any streaming and batch segments will not show until they are evaluated at the hub first

>[!NOTE]
>
>If you were sending to server.adobedc.net using a bearer token you would also see the attribute you configured in the Custom Personalization Destination

###

## Errors You Might Encounter

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

## Validate Event Forwarding

On webhook.site you should immediately see the same payload body you sent via your Postman request appear. 

![On webho](assets/on-webho.png)

>[!NOTE]
>
>Notice the payload has added the geo lookup information you asked for when you setup the datastream you used in your edge setup

## Lookup the Profile

In Adobe Experience Platform lookup the profile you just sent in from the event you just sent into the Edge Network.  Navigate to Profiles -> Browse to perform the lookup using the following information:

- Merge policy -> Default Time-based
- Identity Namespace -> Email
- Identity Value -> edge-email\@dep.com



1. Click **View **to lookup up the profile
1. Click on the **Profile ID** to open the profile

![Lookup profile](assets/lookup-profile.png)



3\. Click on **Events **in the top nav and you can see the event you just sent in

![View the profile event](assets/view-the-profile-event.png)



4\. Validate the Profile has qualified for the Audiences by reviewing the Audience Membership tab in the top nav.  You should see the following:

- Any Event Edge (within last 15 minutes)
- Any Event Streaming (within the last hour)
- From use case #1 you should also see the audiences of:
  - Visited iPhone 14 Page but Not Owns/Ordered it
  - Visited iPhone 14 Page

![Visited iphone 14 page](assets/visited-iphone-14-page.png)

## **Validate Streaming Destination Activation**

Check your webhook to see if the streaming destination you configured has activated any segments.  They should appear in \~5 minutes.

![Validate streaming destination activation](assets/validate-streaming-destination-activation.png)

>[!NOTE]
>
>Streaming Destinations may send another segment qualification payload if the two identities have not linked yet.

If ECID and email have not yet linked, a few minutes after that, another payload may appear with the same values except identityMap will now how two identities (email & ecid)

Over time you should begin to receive more payloads out to the webhook for "exited" status.

![Webhook streaming destination 22exited 22](assets/webhook-streaming-destination-22exited-22.png)

## How to Interpret all the Checks

1. Check for 200 response in Postman (properly formatted payload)
1. Check if the webhook has the event (properly configured Event Forwarding)
1. Check if the Profile has the events (properly configured AEP Service, event received and processed event on the Hub)
1. Check if the Profile has two identities (Identity Graph has linked on the Hub)
1. Check if the Profile qualified for the audiences (properly defined audience)
1. Check if the webhook received the Streaming Audiences (properly configured HTTP API Destination)
1. Check if Postman response includes segments (properly configured Custom Personalization Destination)
1. Check if Data Lake has log of sending (properly configured and sent Audience Qualification and Streaming Destination). See Below.

## Data Lake "Log" of Destinations

After at least 60 minutes you can even check your dataset has the event you sent. To do so perform the following query using Query Service.

Change the table name below to the one from your sandbox. To find it, go to your dataset list and filter on "`dest`", open the dataset and copy the table name on the right rail.

```sql
SELECT * FROM profile_export_for_destination_merge_policy_xxx
WHERE extSourceSystemAudit.LASTREFERENCEDDATE >= CURRENT_DATE
AND identitymap['email'][0].ID in ('edge-email@dep.com')
ORDER BY extSourceSystemAudit.LASTREFERENCEDDATE DESC
LIMIT 10
```

