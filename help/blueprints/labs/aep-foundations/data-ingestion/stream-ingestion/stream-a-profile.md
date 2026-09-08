---
hold: true
title: Stream a Profile
description: Stream a Profile
doc-type: article

solution: Experience Platform
exl-id: 937d153c-9230-4f5a-a397-6c177a3ea890
---

# API Overview

It's important to understand the structure of the API when streaming data into the Adobe Experience Platform in raw form so you can easily re-create it regardless of what dataflow you create.  Below is an example of the basic structure of the call using cURL

**Sample Request (raw data)**

```curl
curl --location '' \
--header 'Content-Type: application/json' \
--header 'x-adobe-flow-id:  <dataflow-id>;' \
--header 'Authorization: Bearer XXX;' \
--data '{
    "customer_id": "202208240125",
    "firstName": "",
    "lastName": "",
    "email": "",
    "createDate": "1660096899",
    "modifyDate": "2022-08-09T22:01:40Z",
    "birth_Date": "1991-06-12",
    "mobile_phone": "888-888-8888",
    "email_optIn": "y",
    "sms_optIn": "n",
    "shipping_street_address": "1901 W Madison St",
    "shipping_city": "Chicago",
    "shipping_state": "IL",
    "shipping_zip_code": "60612",
    "billing_street_address": "1901 W Madison St",
    "billing_city": "Chicago",
    "billing_state": "IL",
    "billing_zip_code": "60612",
    "plan_id": "m1",
    "plan_name": "basic",
    "account_create_date": "Created on 2022-04-20T22:19:03Z",
    "account_end_date": "2022-01-20T13:15:32Z",
    "source": "inStore"
}'
```



A few important elements to note in the request above:

| Key Elements                | Required | Description                                                                                                                                                                                 |
| --------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Request URL (i.e. location) | -        | This is the URL of the HTTP API source account you created that the streaming data will point to. **It is always of type POST**                                                             |
| Header 'Content-Type'       | *        | Always set to `application/json` as the data you are sending in is in JSON format                                                                                                           |
| Header 'x-adobe-flow-id'    | -        | Set to the dataflow id created from the source connector                                                                                                                                    |
| Header 'Authorization'      | *        | Optional value but highly encouraged for security reason. This is the same `access_token` you generated during the [Postman Setup](../../postman-setup/environment-file.md)  labs |
| Body Content                | -        | Contains the actual data you want to send into the Adobe Experience Platform                                                                                                                |

>[!NOTE]
>
>Body Content should always be in JSON format and match the sample payload provided during the design of the dataflow



## Gather Required Values

Before you can stream in data you need to gather a few of the required values listed above (i.e. specifically the streaming endpoint URL and body content 'header' values). 

Perform the following steps:

1. Copy the **Streaming endpoint** value and save it to your local machine (assuming you haven't navigated away from the previous sections step). If you did navigate away, you can find it under Sources->Accounts.

>[!NOTE]
>
>If you did navigate away you can get to this page by doing the following:
>
>- Click on **Sources** in the left rail
>- Ensure you are on **Accounts** tab and click on the account you created titled **Streaming Ingestion - \<Your Initials>**

>[!NOTE]
>
>If you do not see this value ensure you do not have the dataflow row selected by click on the row.  DO NOT CLICK ON THE BLUE LINKS

![Streaming endpoint url is available as a url on the right](assets/streaming-endpoint-url-is-available-as-a-url-on-the-right.png)



2\. Select the dataflow row by clicking anywhere on it avoiding the blue links. Copy the **Dataflow ID** and save it somewhere safe

![Dataflow details right rail with api usage details](assets/dataflow-details-right-rail-with-api-usage-details.png)



## Update Your API Request

Switch over to your Postman application and update the Create Customer Account request with the information you just gathered.

1. Open Postman and navigate to the **Data Ingestion Lab -> Create Customer Account** API request and open it

![Create customer account api request](assets/create-customer-account-api-request.png)



2\. Copy and paste the **Streaming endpoint **value you saved previously into the request's URL

![Create customer account streaming endpoint url](assets/create-customer-account-streaming-endpoint-url.png)



3\. Copy and paste the Dataflow ID value you saved previously into **x-adobe-flow-id** header value

![Copy paste x adobe flow id](assets/copy-paste-x-adobe-flow-id.png)



4\. In the body of the request update the following attributes like so:

- **firstName **-> Your First Name
- **lastName **-> Your Last Name
- **email **-> Your Email Address
- **birth Date**-> YYYY-MM-DD

**5. Save** your request

6\. Click on the **Send** button to execute the request to stream in your Customer Account Profile

![Final create customer account request](assets/final-create-customer-account-request.png)



7\. You should receive a `200 OK` response indicating it was successfully received by the Adobe Experience Platform

Sample 200 OK Response

```none
{
    "inletId": "57e8b639020de08147888c2ce2046f2f4d36f622ee22b7313a565ab3a4ecee54",
    "xactionId": "1688068236344:7186:152",
    "flowId": "7d1d1a20-3df2-43fb-8bd8-2856bb3ea6a4",
    "receivedTimeMs": 1688068236344
}
```

>[!NOTE]
>
>Note the **xactionId **in the response.  If an error ever occurs where you do not see a record ingested this should always be provided as part of a customer support ticket as its a tracer bullet used by our support teams to debug any environment issues

>[!TIP]
>
>Congratulations!  You've successfully streamed in a profile record into the Adobe Experience Platform

