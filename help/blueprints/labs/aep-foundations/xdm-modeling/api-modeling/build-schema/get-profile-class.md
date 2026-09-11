---
title: Get Profile Class
description: Call the global schema registry API to retrieve and save the $id of the XDM Individual Profile class for use in a custom schema.
doc-type: article
solution: Experience Platform
exl-id: d87c21a2-dad4-4666-b917-cdf8e16058d4
---

# Get Profile Class

## Execute step 3 - Get Profile Class

1. Click on the `Step 3 - Get Profile Class` request in the `XDM API Lab -> Create Schema` folder
1. Execute by clicking the `Send` button

![Step 3 - Get Profile Class API request](assets/get-profile-class-step-3-api-request.jpeg "Step 3 - Get Profile Class API Request")

>[!NOTE]
>
>Notice that in the GET request the `global` path:  .../schemaregistry/**global**/classes. Remember that using `global` tells the schema registry that we only want to return Adobe standard XDM objects


## Locate and save the Class $id

After you execute the API request perform the following steps to locate and save the `$id` for the XDM Individual Profile class.

1. Search for the `XDM Individual Profile` class in the response
1. Copy the `$id` for the `XDM Individual Profile` class and save it somewhere you can reference later.

![XDM Individual Profile class located in the API response](assets/get-profile-class-xdm-individual-profile-class.png "XDM Individual Profile Class")

>[!WARNING]
>
>Do not continue until you have saved the `$id` somewhere.  It will be required later to create the Customer Account schema
