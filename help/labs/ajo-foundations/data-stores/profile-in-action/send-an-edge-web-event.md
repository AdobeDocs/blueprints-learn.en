---
title: Send an Edge Web Event
description: Send an Edge Web Event
doc-type: article
exl-id: 0823bcf7-35d9-492e-ad8d-3e8327f77dd8
---

# Learning Objective

Send a simulated web event to the Adobe Edge Network using the API.

To simulate a web page being loaded and sent to the AEP Edge, we are going to send in a Postman call to the Datastream we created.

This will send in an event with no OAuth Token.  Ensure you have Postman open on your machine to perform this lab.

>[!NOTE]
>Because we are not passing in an authenticated token, we will not get back any attributes.

# Lab Expectations

1. Experience Event to hit the Edge
2. Datastream configuration
3. Datastream configuration to use AEP Service
   1. Edge Audience to run
   2. Send Event to the Hub
4. Postman Response to include Edge Audience (but no attributes)
5. Profile Store to receive event and add an Event Profile Fragment
6. Identity Store to add a relationship
7. Dataset to receive data and store in Data Lake



# Update Postman Environment Variable

Before you can execute the API request you need to add the datastream ID to the Postman variable environment. Start by gathering the following values:

## **Gather the Datastream ID**

1. You should already have the **Datastream ID**

>[!NOTE]
>**If you lost the Datastream ID**
>
>1. In the left rail click on **Datastreams **(under the Data Collection heading)
>2. Select your Datastream and copy the **Datastream ID** value
>
>![](assets/Z9_4G6rGvHEqMAe6IJyPU_gather-datastream-id.png)



## Navigate to the Call

1. **Postman Left Sidebar**  -> `Collections`
2. **Collection **-> `AJO Bootcamp (Labs)`
3. **Folder **-> `Profile & Journey Labs`
4. **API Request** -> `Create Web Event`

![](assets/RrRQ0BaywIDeyyb6nPMSd-20260108-070718.png)

## Update DATASTREAM\_CONFIG variable. 

1. Click on **Variables in Request** in the top right

![](assets/r--mIJFGTDonPts4qLZwl-20251216-182201.png)

2. Update the **DATASTREAM \_CONFIG ****Value **with the **datastream ID **from the first step on the page.

![](assets/cA_qMJeuG-rjBzd0dNPql-20260108-065751.png)

3. **Save **your update (ctrl+s or command+s)
4. Click the '**X**' in the upper right corner of the environment sidebar to close the sidebar

![](assets/wuin7IF-swFawTfHrnlYi-20260108-070102.png)

5. The **Create Web Event** request should now be ready to send since all of the variables are now blue and have a value in the environment.

![](assets/C7ZuN0vvpqlYwTRnk3We0-20260108-070358.png)

## Execute the API

Execute your request by clicking the **Send **button.

Response will look something like this: 

![](assets/_5JHa_s-xtuwZKH2auy2Z_image.png)

What you should see coming back in the response are these core things:

- A 200 OK response means the data was successfully sent and accepted by the Edge Network

# Recap

The event has been successfully sent to and accepted by the Edge Network
