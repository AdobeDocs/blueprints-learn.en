---
hold: true
title: Set up the source
description: Upload a historical orders JSON file to the Data Landing Zone and configure a new dataflow targeting the Orders schema.
doc-type: article
solution: Experience Platform
exl-id: 046d50ad-687e-4cdb-a8b1-3c55ab39b68e
---

# Set up the source

## Upload sample file

You need to upload a sample data file to your Data Landing Zone via Azure Storage Explorer so that you can use it during the lab.  To do so, do the following:

1. Download the [Sample Files](../../../sample-files.md) 
1. Drag 'n drop and/or upload the **Lab\_Historical\_Orders.json** file to the Data Landing Zone you saved from above.



When uploaded, your screen should look like the screenshot below.

![Lab_Historical_Orders.json file uploaded to the Data Landing Zone](assets/setup-source-lab-historical-orders-json-uploaded-to-dlz.png "Lab_Historical_Orders.json uploaded to DLZ")

## Navigate to Sources

1. Go to Adobe Experience Platform and navigate to: **Sources** -> **Catalog** -> **Cloud storage**
1. Click on **Setup** / **Add Data** for the Data Landing Zone

![Navigating to Sources > Catalog > Cloud storage to set up the Data Landing Zone](assets/setup-source-navigate-to-data-landing-zone-source.png "Sources - Data Landing Zone")

>[!NOTE]
>
>You see **Add data** as the default action if you've already set up a connection from the previous Batch Ingestion lab



## Preview the file

1. Select the **Lab\_Historical\_Orders.json** file and preview its contents
1. Click **Next** in the upper right corner of the screen to continue to the next step

![Selecting and previewing the Lab_Historical_Orders.json file contents](assets/setup-source-select-and-preview-lab-historical-orders.png "Select & Preview the Lab_Historical_Orders.json file")

## Set up the dataflow

1. In the Dataflow detail screen, choose **New dataset**
1. Name the output dataset as **Orders - YourNameHere**
1. Select the schema name **dep: Orders**
1. Turn on the **Profile dataset** toggle box
   (If you do not turn this on, the Profile Store is not able to monitor for new data entering this dataset and hence does not ingest this data into Profile)
1. Turn on the **Enable partial ingestion**
   (If you do not turn this on, the ingestion may fail if one of the records has errors)
1. Set the Dataflow name as **Orders – Backfill – YourNameHere**
1. Turn on all the alerts **Sources Dataflow Start/Success/Failure** 

![Dataflow details screen configured for the Orders dataset](assets/setup-source-dataflow-details-for-orders.png "Dataflow details for Orders")

>[!CAUTION]
>
>Ensure you have **enabled** your dataset for both profile and partial ingestion.

Click **Next** in the upper right corner of the screen to continue to the next step
