---
title: View schema
description: View a schema's identity descriptors via the UI and API, and compare Accept header options for resolved versus unresolved schema responses.
doc-type: article
solution: Experience Platform
exl-id: 44eedb82-259f-4f7f-84fe-acc2b42376eb
---

# View schema

## View via the UI

1. Open your browser and navigate back to the `Schema -> Browse` section.
1. Search for the **Customer Account** schema
1. Notice that the identities are added to the schema

![Schema browse view showing identities added to the schema](assets/view-schema-schema-ui-with-identities.png "Schema UI View with Identities")


## View via the API

1. Select the `Step 3 - Get Customer Account Schema and its descriptors` API by clicking on it.

![Step 3 - Get Customer Account Schema w/descriptors API request](assets/view-schema-step-3-get-customer-account-schema-w-descriptors.png "Step 3 - Get Customer Account Schema w/descriptors")



1. In the URL of the request replace the `<replace me>` with the `$meta:altId` you saved from the previous section (Create Your Schema) to the end of the call like shown below

![Final Step 5 request with altId appended to the URL](assets/view-schema-final-step-5-request.png "Final Step 5 Request")



1. Save the edits you've made the request

1. Execute the request by clicking the `Send` button

You should now see a `200 OK` response and you should be able to browse the schema you created through the lens of the XDM JSON structure

![Body of the API response showing the schema's XDM JSON structure](assets/view-schema-body-of-the-api-response.png "Body of the API response")



Browse further down in the API response to see the identity descriptors you created

![Identity descriptors displayed in the API response](assets/view-schema-descriptors-displayed-in-api-response.png "Descriptors displayed in API response")


## Accept headers

Note the **Accept** header used in the request. This header tells the XDM schema registry to return the schema's `$refs` unresolved (i.e. show the bare minimum amount of information) along with its associated descriptors in the API response.  Adobe provides other **Accept** headers you can utilize to get various degrees of detail about the schema.

![Accept header field in the Step 3 Get Customer Account Schema request](assets/view-schema-accept-header.png "Step 3 - Get Customer Account Schema Accept Header")

>[!NOTE]
>
>You can read more about the various Accept headers here ->  [Experience League Schema API Endpoint](https://experienceleague.adobe.com/docs/experience-platform/xdm/api/schemas.html?lang=en#lookup)



To see this in action, change the **Accept** header to tell the schema registry to respond with all the `$ref` and `allOf` fully resolved (i.e. exploded out) and any associated descriptors

1. Update the `Accept` header value to the following:
   `application/vnd.adobe.xed-full-desc+json; version=1`
1. Save your request using the `Save` button
1. Execute your request using the `Send` button

You should see a response now that looks like this:

![Fully exploded schema response showing all resolved properties](assets/view-schema-fully-exploded-schema-showing-all-properties.png "Fully exploded schema showing all properties")

>[!NOTE]
>
>Notice how all the properties of the schema are now fully displayed in the response whereas in the previous call you only were shown the `$ref` values of the schema (i.e. what field groups it was referencing) and nothing was fully resolved down to each individual field/property.

>[!NOTE]
>
>This is important to understand because when working with APIs you do not always need the fully resolved response if all you are doing is getting the `$id` of the schema or simply checking its composition
