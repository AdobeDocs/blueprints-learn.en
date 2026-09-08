---
title: Create a New Dataflow
description: Create a batch source dataflow against an existing dataset and import mappings from a prior dataflow to speed up setup.
doc-type: article
solution: Experience Platform
exl-id: 6f26f742-27e8-445a-8005-21d4e59dc3d0
---

# Navigate to Sources

1. In Adobe Experience Platform UI navigate to the following location:  
   **Sources** -> **Catalog** -> **Local system**
1. Next click on **Add Data** button for the **Local File upload** card

![LxxLyKc0x1oi c 0wx4m qfkm5  KeN4eN 20241025 031040.png "Access the Data Landing Zone"](assets/n-ADAXZy_lxxLyKc0x1oi-c-0wx4m_qfkm5--KeN4eN-20241025-031040.png "Access the Data Landing Zone")



## Setup the Dataflow

1. In the Dataflow detail screen, choose **Existing dataset**. 
1. Use the dataset you created previously with the name **Customer Account - \<Your Initials>**
1. Ensure you have the **Profile dataset** toggle turned ON.
   (If you do not turn this on, the Profile Store will not be able to monitor for new data entering this dataset and hence will not ingest this data into Profile)
1. Ensure you have the **Enable partial ingestion **toggle turned ON
   (If you do not turn this on, the whole ingestion may fail if just one of the records has an error)
1. Set the Dataflow name as **Customer Account Batch v2 – \<Your Initials>** 
1. Turn on all the alerts **Sources Dataflow Start/Success/Failure**
1. If everything looks good click the **Next** button in the upper right corner of the screen to continue to the next step.

![HpxC data flow details.png "Data Flow Details"](assets/YKDn-MNkWPqhb5Zw_HpxC_data-flow-details.png "Data Flow Details")



## Upload Sample File

1. Drag 'n drop and/or upload the **Lab\_Customer\_Account.csv **file in the UI.  When done your screen should look like below.

![Accessin.png "Accessing the Azure Storage Explorer files within Adobe Experience Platform"](assets/zBBQkjxL8ZaedOs0DVDNm_accessin.png "Accessing the Azure Storage Explorer files within Adobe Experience Platform")



## Import Mappings

On the mapping screen instead of setting up all your mappings again you can import the ones you previous created.

1. Click on the **Import mapping** button
1. Select the dataflow that has the mapping you previously created



![Import mapping button.png "Import mapping button"](assets/-csMePssFD5AlM6nL863s_import-mapping-button.png "Import mapping button")



![Select dataflow to import mapping from.png "Select dataflow to import mapping from"](assets/zwWP7A73WOyEISaAi4IWj_select-dataflow-to-import-mapping-from.png "Select dataflow to import mapping from")

>[!NOTE]
>
>Importing mappings are a handy way to re-use mappings from other dataflows to reduce the amount mapping work you need to perform

