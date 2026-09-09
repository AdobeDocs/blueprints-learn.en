---
title: View Schema
description: View a schema's identity descriptors via the UI and API, and compare Accept header options for resolved versus unresolved schema responses.
doc-type: article
solution: Experience Platform
exl-id: 44eedb82-259f-4f7f-84fe-acc2b42376eb
---

# **View via the UI**

1. Open your browser and navigate back to the `Schema -> Browse`section.
1. Search for the schema `Sample Customer Schema - <your sandbox number>`
1. Notice that the identities are added to the schema

![LxxLyKc0x1oi aKjUnWfVu4aH XNWPHeqL 20241023 215737.png "Schema UI View with Identities"](assets/n-ADAXZy_lxxLyKc0x1oi-aKjUnWfVu4aH-XNWPHeqL-20241023-215737.png "Schema UI View with Identities")


## **View via the API**

1. Select the `Step 3 - Get Customer Account Schema and it's descriptors`API by clicking on it.

![Step 3 get customer account schema w descriptors.png "Step 3   Get Customer Account Schema w/descriptors"](assets/axYZV1HEwOElFJlQh8tEK_step-3-get-customer-account-schema-w-descriptors.png "Step 3 - Get Customer Account Schema w/descriptors")



2\. In the URL of the request replace the `<replace me>` with the `$meta:altId` you saved from the previous section (Create Your Schema) to the end of the call like shown below

![Final step 5 request.png "Final Step 5 Request"](assets/3L1FD7W2l5jNj7-tTMqv3_final-step-5-request.png "Final Step 5 Request")



3\. Save the edits you've made the request

4\. Execute the request by clicking the `Send` button

You should now see a `200 OK` response and you should be able to browse the schema you created through the lens of the XDM JSON structure

![QOy8p4Ky body of the api response.png "Body of the API resposne"](assets/bgHLqZYdQytK_QOy8p4Ky_body-of-the-api-response.png "Body of the API resposne")



Browse further down in the API response to see the identity descriptors you created

![NsMS56rO descriptors displayed in api response.png "Descriptors displayed in API response"](assets/uIIStkniOpho_NsMS56rO_descriptors-displayed-in-api-response.png "Descriptors displayed in API response")


## Accept Headers

Note the **Accept** header used in the request. This header tells the XDM schema registry to return the schema's `$ref's` unresolved (i.e. show the bare minimum amount of information) along with its associated descriptors in the API response.  Adobe provides other **Accept** headers you can utilize to get various degrees of detail about the schema.

![Step 3 get customer account schema accept header.png "Step 3   Get Customer Account Schema Accept Header"](assets/2JiVHkUVdDRcIr8YZ2L0t_step-3-get-customer-account-schema-accept-header.png "Step 3 - Get Customer Account Schema Accept Header")

>[!NOTE]
>
>You can read more about the various Accept headers here ->  [Experience League Schema API Endpoint](https://experienceleague.adobe.com/docs/experience-platform/xdm/api/schemas.html?lang=en#lookup)



To see this in action lets change the **Accept** header to tell the schema registry to respond with all the `$ref `and `allOff` fully resolved (i.e. exploded out) and any associated descriptors

1. Update the `Accept` header value to the following:
   `application/vnd.adobe.xed-full-desc+json; version=1`
1. Save your request using the `Save` button
1. Execute your request using the `Send` button

You should see a response now that looks like this:

![Es4OYrPdatSRSIRL0 fully exploded schema showing all properties.png "Fully exploded schema showing all properties"](assets/JRM_es4OYrPdatSRSIRL0_fully-exploded-schema-showing-all-properties.png "Fully exploded schema showing all properties")

>[!NOTE]
>
>Notice how all the properties of the schema are now fully displayed in the respone whereas in the previous call you only were shown the `$ref` values of the schema (i.e. what field groups it was referencing) and nothing was fully resolved down to each individual field/property.

>[!NOTE]
>
>This is important to understand because when working with APIs you do not always need the fully resolved response if all you are doing is getting the `$id` of the schema or simply checking its composition

