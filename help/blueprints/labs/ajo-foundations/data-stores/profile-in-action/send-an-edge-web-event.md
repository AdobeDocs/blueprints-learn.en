---
title: Send an Edge web event
description: Learn how to send a simulated web event to the Adobe Edge Network via a Postman API call using your datastream ID.
doc-type: article
solution: Experience Platform
exl-id: 0823bcf7-35d9-492e-ad8d-3e8327f77dd8
---

# Send an Edge web event

## Learning objective

Send a simulated web event to the Adobe Edge Network using the API.

To simulate a web page being loaded and sent to the AEP Edge, you send in a Postman call to the Datastream you created.

This sends in an event with no OAuth Token.  Ensure you have Postman open on your machine to perform this lab.

>[!NOTE]
>
>Because you are not passing in an authenticated token, you don't get back any attributes.

## Lab expectations

1. Experience Event to hit the Edge
1. Datastream configuration
1. Datastream configuration to use AEP Service
   1. Edge Audience to run
   2. Send Event to the Hub
1. Postman Response to include Edge Audience (but no attributes)
1. Profile Store to receive event and add an Event Profile Fragment
1. Identity Store to add a relationship
1. Dataset to receive data and store in Data Lake



## Update Postman environment variable

Before you can execute the API request you need to add the datastream ID to the Postman variable environment. Start by gathering the following values:

### Gather the Datastream ID

1. You should already have the **Datastream ID**

>[!NOTE]
>
>**If you lost the Datastream ID**
>
>1. In the left rail click on **Datastreams** (under the Data Collection heading)
>2. Select your Datastream and copy the **Datastream ID** value
>
>![Datastreams list showing the Datastream ID to copy](assets/send-an-edge-web-event-gather-datastream-id.png)



### Navigate to the call

1. **Postman Left Sidebar** -> `Collections`
1. **Collection** -> `AJO Bootcamp (Labs)`
1. **Folder** -> `Profile & Journey Labs`
1. **API Request** -> `Create Web Event`

![Postman sidebar navigating to the Create Web Event request](assets/send-an-edge-web-event-postman-create-web-event-request.png)

### Update DATASTREAM\_CONFIG variable

1. Click on **Variables in Request** in the top right

![Variables in Request option in the Postman toolbar](assets/send-an-edge-web-event-click-variables-in-request.png)

2. Update the **DATASTREAM_CONFIG** **Value** with the **datastream ID** from the first step on the page.

![DATASTREAM_CONFIG variable updated with the datastream ID](assets/send-an-edge-web-event-update-datastream-config-variable.png)

3. **Save** your update (ctrl+s or command+s)
4. Click the '**X**' in the upper right corner of the environment sidebar to close the sidebar

![Closing the Postman environment sidebar after saving](assets/send-an-edge-web-event-close-environment-sidebar.png)

5. The **Create Web Event** request is now ready to send since all of the variables are now blue and have a value in the environment.

![Create Web Event request with all variables populated](assets/send-an-edge-web-event-request-ready-to-send.png)

## Execute the API

Execute your request by clicking the **Send** button.

Response looks something like this: 

![Example 200 OK response from the Create Web Event request](assets/send-an-edge-web-event-api-response-example.png)

What you see coming back in the response are these core things:

- A 200 OK response means the data was successfully sent and accepted by the Edge Network

## Recap

The event has been successfully sent to and accepted by the Edge Network
