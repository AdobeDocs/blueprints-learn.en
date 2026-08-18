---
title: Import API Collection
description: Import API Collection
doc-type: article
solution: Experience Platform
exl-id: 7562c7f1-0d60-4a3a-8bce-fa42bda08962
---

# Objective

In this step you will be importing the API collection which contains all the various requests you will need to make throughout the bootcamp.  This API requests in this file are reliant on the environment file you just imported.



## Import Request Collection

1. Download the **AJO Bootcamp (Labs).postman\_collection.json** file:

Download File — [AJO Bootcamp (Labs).postman_collection.json](assets/ajo-bootcamp-labs.postman_collection.json)

1. Like before, click on the **Import** button.
1. Paste the local URL of the **AJO Bootcamp (Labs).postman\_collection.json **file into the import modal text box or drop it into the import dialog box.  This should trigger an automatic import.
1. After the import process is complete, click on **Collections** in the left navbar, expand the **AJO Bootcamp (Labs)** folder, and you should see the newly imported collection

![verify postman collection import](assets/B76krD3RvzFUPjCnZFhki-20260107-210108.png)

>[!TIP]
>
>Congratulations!  You have successfully imported the bootcamp's Postman Collection



## **Validate Environment Variables**

The collection you imported contains all the necessary API calls you will need for labs throughout the bootcamp.  Each lab is organized into a specific folder with its own set of requests.  

Details about each folder can be found below:

- **Profile & Journey Labs** - Contains a set of requests for sending in a Web Event and a event that simulates and shipping confirmation event.
- **Decisioning Labs** - Contains requests for 3 visitors that mimic the top and bottom page calls that would typically be found on a AEP Web SDK- tagged site.

To ensure that the environment and collection are functioning correctly together, please follow these steps. 

1. If necessary, click on **Collections** in the left rail and then expand the **Profiles & Journey** **Labs** folder. 
1. Click on the **Create Web Event** request, and you should see that environment variables are **red**

![Saf2u44lB7bq2OHqBj9 F 20260107 215911.png "Verify postman environment variables are red"](assets/saf2u44lB7bq2OHqBj9-F-20260107-215911.png "Verify postman environment variables are red")

1. Click on the **Environment Dropdown **in the upper-right corner and choose the **AJO Bootcamp** environment.

![Select correct Postman environment](assets/XDAeTkNxNeHjMFWrufkXh-20260108-062217.png)

1. With the proper environment selected, you should see that the EDGE\_REGION variable now turns a lighter blue color. This indicates that the variable now has a value for the selected environment. The DATASTREAM\_CONFIG variable will stay red because you haven't created the datastream yet, so you don't have a value for that environment variable yet. Hovering over the EDGE\_REGION will show you what the value of the environment value is.

![EpMYLd0EA6K8yVlvSv37E 20260108 062937.png "Verify Postman enviroment works with collection"](assets/EpMYLd0EA6K8yVlvSv37E-20260108-062937.png "Verify Postman enviroment works with collection")

## Recap

You should now have the Environment and Collection files imported and know how to use them.
