---
hold: true
title: Setup Source
description: Setup Source
doc-type: article

solution: Experience Platform
exl-id: 046d50ad-687e-4cdb-a8b1-3c55ab39b68e
---

# **Upload Sample File**

You need to upload a sample data file to your Data Landing Zone via Azure Storage Explorer so that you can use it during the lab.  To do so do the following:

1. Download the [Sample Files](../../../sample-files.md) 
1. Drag 'n drop and/or upload the **Lab\_Historical\_Orders.json **file to the Data Landing Zone you saved from above.



When uploaded your screen should look like the below screenshot

![Lab historical ordersjson uploaded to dlz.png "Lab Historical Orders.json uploaded to DLZ"](assets/pY-OFVPYjQaPKJxqRwuFh_lab-historical-ordersjson-uploaded-to-dlz.png "Lab_Historical_Orders.json uploaded to DLZ")

## Navigate to Sources

1. Go to Adobe Experience Platform and navigate to: **Sources** -> **Catalog** -> **Cloud storage**
1. Click on **Setup** / **Add Data** for the Data Landing Zone

![LxxLyKc0x1oi MxTYbowbaFGcpeaAkRnTS 20241025 021247.png "Sources   Data Landing Zone"](assets/n-ADAXZy_lxxLyKc0x1oi-MxTYbowbaFGcpeaAkRnTS-20241025-021247.png "Sources - Data Landing Zone")

>[!NOTE]
>
>You will see **Add data** as the default action if you've already setup a connection from the previous Batch Ingestion lab



## Preview the File

1. Select the **Lab\_Historical\_Orders.json **file and preview its contents
1. Click **Next** in the upper right corner of the screen to continue to the next step

![Select and preview the lab historical orders.png "Select & Preview the Lab Historical Orders.json file"](assets/YlaOXmjTZGeyeWDUAaTAT_select-and-preview-the-lab-historical-orders.png "Select & Preview the Lab_Historical_Orders.json file")

## Setup the Dataflow

1. In the Dataflow detail screen, choose **New dataset**
1. Name the output dataset as **Orders - YourNameHere**
1. Select the schema name **dep: Orders**
1. Turn ON the **Profile dataset** toggle box
   (If you do not turn this on, the Profile Store will not be able to monitor for new data entering this dataset and hence will not ingest this data into Profile)
1. Turn ON the **Enable partial ingestion**
   (If you do not turn this on, the ingestion may fail if one of the records has errors)
1. Set the Dataflow name as **Orders – Backfill – YourNameHere**
1. Turn on all the alerts **Sources Dataflow Start/Success/Failure** 

![OjZj1uGhBsSyTQQN dataflow details for orders.png "Dataflow details for Orders"](assets/dVjB_ojZj1uGhBsSyTQQN_dataflow-details-for-orders.png "Dataflow details for Orders")

>[!CAUTION]
>
>Ensure you have **enabled **your dataset for both profile and partial ingestion.

Click **Next** in the upper right corner of the screen to continue to the next step
