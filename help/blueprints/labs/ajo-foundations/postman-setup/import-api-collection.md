---
title: Import API collection
description: Import the bootcamp's Postman API collection and validate that its environment variables resolve correctly against your sandbox.
doc-type: article
solution: Experience Platform
exl-id: 7562c7f1-0d60-4a3a-8bce-fa42bda08962
---

# Import API collection

## Objective

In this step, you import the API collection, which contains all the various requests you need to make throughout the bootcamp.  These API requests are reliant on the environment file you just imported.



## Import request collection

1. Download the **AJO Bootcamp (Labs).postman\_collection.json** file:

   Download File — [AJO Bootcamp (Labs).postman_collection.json](assets/ajo-bootcamp-labs.postman_collection.json)

2. As before, click on the **Import** button.
3. Paste the local URL of the **AJO Bootcamp (Labs).postman\_collection.json** file into the import modal text box or drop it into the import dialog box.  This triggers an automatic import.
4. After the import process is complete, click on **Collections** in the left navbar, expand the **AJO Bootcamp (Labs)** folder, and you see the newly imported collection

![verify postman collection import](assets/import-api-collection-verify-collection-imported.png)

>[!SUCCESS]
>
>Congratulations!  You have successfully imported the bootcamp's Postman Collection



## Validate environment variables

The collection you imported contains all the API calls you need for labs throughout the bootcamp.  Each lab is organized into a specific folder with its own set of requests.  

Details about each folder appear below:

- **Profile & Journey Labs** - Contains a set of requests for sending a Web Event and an event that simulates a shipping confirmation.
- **Decisioning Labs** - Contains requests for 3 visitors that mimic the top and bottom page calls that would typically be found on an AEP Web SDK-tagged site.

To ensure that the environment and collection are functioning correctly together, follow these steps. 

1. If necessary, click on **Collections** in the left rail and then expand the **Profile & Journey Labs** folder. 
2. Click on the **Create Web Event** request, and you see that environment variables are **red**

   ![Postman request showing environment variables highlighted in red because no environment is selected](assets/import-api-collection-environment-variables-shown-red.png "Verify postman environment variables are red")

3. Click on the **Environment Dropdown** in the upper-right corner and choose the **AJO Bootcamp** environment.

   ![Select correct Postman environment](assets/import-api-collection-select-postman-environment.png)

4. With the proper environment selected, you see that the EDGE\_REGION variable now turns a lighter blue color. This indicates that the variable now has a value for the selected environment. The DATASTREAM\_CONFIG variable stays red because you haven't created the datastream yet, so you don't have a value for that environment variable yet. Hovering over the EDGE\_REGION shows you what the value of the environment value is.

![Postman EDGE_REGION variable now populated and no longer shown in red](assets/import-api-collection-environment-works-with-collection.png "Verify Postman environment works with collection")

## Recap

You now have the Environment and Collection files imported and know how to use them.
