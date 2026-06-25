---
hold: true
title: Get Profile Class
description: Get Profile Class
doc-type: article

solution: Experience Platform
exl-id: d87c21a2-dad4-4666-b917-cdf8e16058d4
---

# Execute Step 3 - Get Profile Class

1. Click on the `Step 3 - Get Profile Class` request in the `XDM API Lab -> Create Schema` folder
1. Execute by clicking the `Send` button

![B9g7 step 3 get profile class api request.jpeg "Step 3   Get Profile Class API Request"](assets/liFeetB8YVlttuHO_b9g7_step-3-get-profile-class-api-request.jpeg "Step 3 - Get Profile Class API Request")

>[!NOTE]
>
>Notice that in the GET request the `global` path:  .../schemaregistry/**global**/classes. Remember that when using `global` this tells the schema registry we only want to return Adobe standard XDM objects


## Locate and Save the Classes $id 

After you execute the API request perform the following steps to locate and save the `$id` for the XDM Individual Profile class.

1. Search for the `XDM Individual Profile` class in the response
1. Copy the `$id` for the `XDM Individual Profile` class and save it somewhere you can reference later.

![Xdm individual profile class.png "XDM Individual Profile Class"](assets/mKLJKZdVyUCdspPQKmUXd_xdm-individual-profile-class.png "XDM Individual Profile Class")

>[!WARNING]
>
>Do not continue until you have saved the `$id` somewhere.  It will be required later to create the Customer Account schema

