---
hold: true
title: API collection
description: Download and import the bootcamp's Postman API collection containing the requests used throughout the AEP Foundations labs.
doc-type: article
solution: Experience Platform
exl-id: 18d820c5-56ad-46b8-a9cf-f725555d2db3
---

# API collection

## Postman API collection file

Download File — [AEP Foundations Bootcamp (Labs).postman_collection.json](assets/aep-foundations-bootcamp-labs.postman_collection.json)



## Import API collection

1. Open the `Postman API Collection File` from above in your browser by clicking on the file
1. Copy the URL of the file to your clipboard
1. Launch Postman on your local machine and click on the `Import` button within your workspace
1. Paste the URL of the `Postman API Collection File` into the import modal text box on the overlay.  This should trigger an automatic import

![Clicking the Import button in the Postman workspace to import the API collection](assets/api-collection-click-import-button.png "Import Button")



![Pasting the API collection file URL into the Postman import modal text box](assets/api-collection-import-modal-paste-url.png "Import Button Modal Text Box")

You should now see a collection populated under the left sidebar's `Collections` tab called `AEP Foundations Bootcamp`



![AEP Foundations Bootcamp collection populated under the Postman Collections sidebar tab](assets/api-collection-imported-collection-in-sidebar.png)

## AEP Foundations Bootcamp collection overview

The API collection you imported contains all the necessary API calls you will need for labs throughout the bootcamp.  Each lab is organized into a specific folder with its own set of APIs.  Please be aware of this as you work through labs this week.

Details about each folder can be found below:

- **IMS Authenticate** - contains a single request to generate an access\_token which is required when working with any of the Adobe Experience Platform APIs
- **XDM Schema Lab** - contains a set of requests for creating the XDM components necessary for building and configuring a schema for the Real-Time Customer Profile
- **Data Ingestion Lab** - contains a set of requests for streaming data into the Experience Platform
- **Profile Lab** - contains a set of requests for viewing the Real-Time Customer Profile's traits and behaviors

>[!TIP]
>
>Congratulations!  You have successfully imported the bootcamp's Postman Collection
