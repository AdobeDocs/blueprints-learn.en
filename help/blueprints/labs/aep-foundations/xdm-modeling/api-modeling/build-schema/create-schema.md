---
hold: true
title: Create Schema
description: Create Schema
doc-type: article

solution: Experience Platform
exl-id: 78ebc5b8-d088-48e9-857f-87085a87a280
---

# **Modify the Body of API**

>[!CAUTION]
>
>**Do not execute the call...yet**

1. Click on the `Step 4 - Create Customer Account Schema` API call in the `XDM Schema Lab -> Create Schema` folder.

![Click on the step 4 create customer account schema](assets/H-GtAst5TJj95cUiscUTi_click-on-the-step-4-create-customer-account-schema.png)



2\. Open the body of the call and view the structure of how a schema is defined. Remember a schema is always composed of only one (1) class and one or more field groups.

3\. Populate the `title` and `description` fields in the body of the schema with the following:

- Title -> `Sample Customer Schema - <your sandbox number>`
- Description -> `Sample Customer Schema - <your sandbox number>`

4\. Populate the `$ref` fields with the `$id's` you saved from the previous lab sections you completed: [Create Custom Field Groups](./create-custom-field-groups.md)  and [Get Profile Class](./get-profile-class.md). You should have $id's for each of the following items:

- Class -> XDM Individual Profile
- Field Group -> Demographic Details
- Field Group -> Personal Contact Details
- Field Group -> Consent and Preference Details
- Field Group (custom) -> Customer Account Details

![Empty schema api body.png "Empty Schema API Body"](assets/3e-XAFlOXmYeqVnkq6FJ5_empty-schema-api-body.png "Empty Schema API Body")



4\. Review your final body and ensure it looks similar to this

![Example of final body payload.png "Example of final body payload"](assets/4yeNJ82ALNZFtL7Obi3w4_example-of-final-body-payload.png "Example of final body payload")

>[!NOTE]
>
>The order of the `$ref's` do not matter nor does the location of the `title` and `description` within the body. 



## Execute the API

1. Save your modifications to the API request before continuing.
1. Execute the API by clicking the `Send` button

A successful response for creating the schema should result in a `201 Created` status and should look like image below

>[!WARNING]
>
>Do not execute the request again if successful

![Sample response from executing the step 4 api.png "Sample response from executing the Step 4 API"](assets/KIkCUWK7VWbN4jN7bP-wy_sample-response-from-executing-the-step-4-api.png "Sample response from executing the Step 4 API")

#

## Locate and Save the Schema $id

1. After you execute the API request copy the `$id` and `meta:altId` from the response
1. Save the values somewhere so that you can reuse them later

>[!WARNING]
>
>Do not continue until you have saved the `$id` and `$meta:altId` somewhere.  They will be required in future lab steps

>[!NOTE]
>
>**Congratulations! You have just created a schema using only the API's**

