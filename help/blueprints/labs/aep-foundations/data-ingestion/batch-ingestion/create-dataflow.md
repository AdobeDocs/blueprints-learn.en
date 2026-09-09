---
title: Create Dataflow
description: Configure a batch source dataflow with a new dataset, enable Profile and partial ingestion, and upload a sample Customer Account CSV file.
doc-type: article
solution: Experience Platform
exl-id: 70145966-d6c0-4741-8216-903de0d61e1d
---

# Create Dataflow

## Navigate to Sources

1. In Adobe Experience Platform UI navigate to the following location:  
   **Sources** -> **Catalog** -> **Local system**
1. Next click on **Add Data** button for the **Local File upload** card

![LxxLyKc0x1oi TszWAFWg87ho6qADimcJ6 20241025 025702.png "Access the Data Landing Zone"](assets/n-ADAXZy_lxxLyKc0x1oi-TszWAFWg87ho6qADimcJ6-20241025-025702.png "Access the Data Landing Zone")



## Setup the Dataflow

1. In the Dataflow detail screen, choose **New dataset**. 
1. Name the output dataset as **Customer Account - \<Your Initials>**
1. Select the **dep: Customer Account** schema from the dropdown list.
1. Turn ON the **Profile dataset** toggle box.
   (If you do not turn this on, the Profile Store will not be able to monitor for new data entering this dataset and hence will not ingest this data into Profile)
1. Turn ON the **Enable partial ingestion**.
   (If you do not turn this on, the whole ingestion may fail if just one of the records has an error)
1. Set the Dataflow name as **Customer Account Batch – \<Your Initials>** 
1. Turn on all the alerts **Sources Dataflow Start/Success/Failure**

![Data flow details.png "Data Flow Details"](assets/m5EDAfE2qxpKR2LyFgXjF_data-flow-details.png "Data Flow Details")

>[!NOTE]
>
>**Enabling partial ingestion** specifies the number of errors (**INGEST** and **DCVS**) as a percentage of the total number of records that can fail before the entire dataflow is declared a failure.

>[!CAUTION]
>
>Ensure you have **enabled the** dataset for both profile and partial ingestion before proceeding!

8\. If everything looks good click the **Next** button in the upper right corner of the screen to continue to the next step.



## Upload Sample File

1. Download the sample files from the [Sample Files](../sample-files.md) for use with this lab
1. Drag 'n drop and/or upload the **Lab\_Customer\_Account.csv** file in the UI.  When done your screen should look like below.

![Accessin.png "Accessing the Azure Storage Explorer files within Adobe Experience Platform"](assets/pjFHpQeQwNQh8gy0MndQG_accessin.png "Accessing the Azure Storage Explorer files within Adobe Experience Platform")

3\. In the preview pane, look at the following attributes and note the following things:

- **sms\_optIn** is a consent field has several missing values (shown in preview as - )
- **account\_create\_date** does not have the proper date format. It has string values along with date and time values in one string.
- **account\_end\_date** has the proper date format.



![HTLIJBLldAMbQtkm9tMS sms optin.png "sms optin"](assets/_HTLIJBLldAMbQtkm9tMS_sms-optin.png "sms_optin")



![Account create date account end date.png "account create date & account end date"](assets/lqxT3mFETK6s9VE11tpPr_account-create-date-account-end-date.png "account_create_date & account_end_date")

>[!NOTE]
>
>You will need to deal with the missing values, dates and improperly formatted fields in the mapping steps later in this lab

4\. Click the **Next** button in the upper right corner of the screen to continue to the next step
