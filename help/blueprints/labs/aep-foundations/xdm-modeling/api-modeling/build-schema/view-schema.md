---
title: View Schema
description: View a newly created customer schema in both the Experience Platform UI and via a Get Schema API call.
doc-type: article
solution: Experience Platform
exl-id: 29302546-46dc-4c97-8fd8-deab6977635c
---

# View Schema

## View via the UI

1. Open your browser and navigate back to the `Schema -> Browse` section.

>[!NOTE]
>
>Refresh the UI to see it, since you just created it and need to re-query the schema registry

2. Search for the schema `Sample Customer Schema - <your sandbox number>`

3. Notice that the required class and the associated field groups are added to the schema

![Sample Customer Schema displayed in the Experience Platform UI with its class and field groups](assets/view-schema-ui-view-of-sample-customer-schema.png "UI View of the Sample Customer Schema")


## View via the API

1. Select the `Step 5 - Get Customer Account Schema` API by clicking on it.
1. In the URL of the request replace the `<replace me>` with the `$meta:altId` you saved from the previous section (Create Your Schema) to the end of the call like shown below
1. Save the edits you've made to the request
1. Execute the request by clicking the `Send` button

![Step 5 - Get Customer Account Schema API call](assets/view-schema-step-5-get-customer-account-schema.jpeg "Step 5 - Get Customer Account Schema")



Example of your final request after adding the `$meta:altId`

![Step 5 request with the meta:altId appended to the URL](assets/view-schema-final-step-5-request.png "Final Step 5 Request")



If you received a `200 OK` response you should be able to browse the schema you created just through the lens the XDM JSON structure

![200 OK response showing the full Sample Customer Account schema JSON](assets/view-schema-sample-customer-account-schema.png "Sample Customer Account Schema")
