---
hold: true
title: Create a new dataflow
description: Create a batch source dataflow against an existing dataset and import mappings from a prior dataflow to speed up setup.
doc-type: article
solution: Experience Platform
exl-id: 6f26f742-27e8-445a-8005-21d4e59dc3d0
---

# Create a new dataflow

## Navigate to Sources

1. In Adobe Experience Platform UI navigate to the following location:  
   **Sources** -> **Catalog** -> **Local system**
1. Next click on **Add Data** button for the **Local File upload** card

![Add Data button for the Local File upload card in the Sources catalog](assets/create-a-new-dataflow-local-file-upload-add-data.png "Access the Data Landing Zone")



## Set up the dataflow

1. In the Dataflow detail screen, choose **Existing dataset**. 
1. Use the dataset you created previously with the name **Customer Account - \<Your Initials>**
1. Ensure you have the **Profile dataset** toggle turned ON.
   (If you do not turn this on, the Profile Store will not be able to monitor for new data entering this dataset and hence will not ingest this data into Profile)
1. Ensure you have the **Enable partial ingestion** toggle turned ON
   (If you do not turn this on, the whole ingestion may fail if just one of the records has an error)
1. Set the Dataflow name as **Customer Account Batch v2 – \<Your Initials>** 
1. Turn on all the alerts **Sources Dataflow Start/Success/Failure**
1. If everything looks good click the **Next** button in the upper right corner of the screen to continue to the next step.

![Dataflow detail screen configured with the existing dataset for the second dataflow](assets/create-a-new-dataflow-existing-dataset-flow-details.png "Data Flow Details")



## Upload sample file

1. Drag 'n drop and/or upload the **Lab\_Customer\_Account.csv** file in the UI.  When done your screen should look like below.

![Preview of the uploaded Customer Account CSV file for the second dataflow](assets/create-a-new-dataflow-uploaded-csv-preview.png "Accessing the Azure Storage Explorer files within Adobe Experience Platform")



## Import mappings

On the mapping screen instead of setting up all your mappings again you can import the ones you previous created.

1. Click on the **Import mapping** button
1. Select the dataflow that has the mapping you previously created



![Import mapping button on the mapping screen](assets/create-a-new-dataflow-import-mapping-button.png "Import mapping button")



![Dialog for selecting the dataflow to import mapping from](assets/create-a-new-dataflow-select-dataflow-to-import-mapping-from.png "Select dataflow to import mapping from")

>[!NOTE]
>
>Importing mappings is a handy way to reuse mappings from other dataflows and reduce the amount of mapping work you need to perform
