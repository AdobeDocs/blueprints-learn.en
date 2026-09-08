---
hold: true
title: Setup Souce
description: Setup Souce
doc-type: article

solution: Experience Platform
exl-id: 1c80e71b-19a7-45e9-9961-d72b3f03ecae
---

# Upload Sample File

You need to upload a sample data file to your Data Landing Zone via Azure Storage Explorer so that you can use it during the lab.  To do so do the following:

1. Download the [Sample Files](../../sample-files.md) 
1. Drag 'n drop and/or upload the **Lab\_Customer\_Account.csv **file to the Data Landing Zone you saved from the previous step.

When uploaded your screen should look like the below screenshot. 

>[!WARNING]
>
>Make sure you do not upload the file into the *project *folder. It contains preloaded data that we will not be using in our labs.

![Make sure you do not upload the file](assets/make-sure-you-do-not-upload-the-file.png)

## **Navigate to Sources**

1. Go to Adobe Experience Platform and navigate to: **Sources** -> **Catalog** -> **Cloud storage**
1. Click on **Setup** / **Add Data** for the Data Landing Zone

![LxxLyKc0x1oi gWzji9MzyidHSbL8GtmFB 20241025 020902.png "Access the Data Landing Zone"](assets/n-ADAXZy_lxxLyKc0x1oi-gWzji9MzyidHSbL8GtmFB-20241025-020902.png "Access the Data Landing Zone")

>[!NOTE]
>
>If at least one connection exists for that source, you will see **Add data** as the default action. If no connections exist for that source, you will see **Setup** as the default action

## Preview the File

1. Select the **Lab-Customer-Account.csv**

![Accessin.png "Accessing the Azure Storage Explorer files within Adobe Experience Platform"](assets/m1OnJcCHyxHJK6Ys1MJwf_accessin.png "Accessing the Azure Storage Explorer files within Adobe Experience Platform")

2\. In the preview pane, look at the following attributes and observe the following:

- **sms\_optIn** is a consent field has several missing values (shown in preview as - )
- **account\_create\_date** does not have the proper date format. It has string values along with date and time values in one string.
- **account\_end\_date** has the proper date format.



![Sms optin.png "sms optin"](assets/NdIBbtrUZKMx7kG2jiWYV_sms-optin.png "sms_optin")



![WJZNwF account create date account end date.png "account create date & account end date"](assets/UFrtOZI7jjngyX_WJZNwF_account-create-date-account-end-date.png "account_create_date & account_end_date")

>[!NOTE]
>
>You will need to deal with the missing values, dates and improperly formatted fields in the mapping steps later in this lab

3\. Click **Next** in the upper right corner of the screen to continue to the next step



## Setup the Dataflow

1. In the Dataflow detail screen, choose **New dataset**. 
1. Name the output dataset as **Customer Account - \<Your Initials>**
1. Select the **dep: Customer Account **schema from the dropdown list.
1. Turn ON the **Profile dataset** toggle box.
   (If you do not turn this on, the Profile Store will not be able to monitor for new data entering this dataset and hence will not ingest this data into Profile)
1. Turn ON the **Enable partial ingestion**.
   (If you do not turn this on, the ingestion may fail if one of the records has errors)
1. Set the Dataflow name as **Customer Account Batch Ingestion – \<Your Initials>** 
1. Turn on all the alerts **Sources Dataflow Start/Success/Failure**

![Data flow details.png "Data Flow Details"](assets/k2tDIS2EK7aFLmnvM59kM_data-flow-details.png "Data Flow Details")

>[!CAUTION]
>
> Ensure you have **enabled the **dataset for both profile and partial ingestion.

Click **Next** in the upper right corner of the screen to continue to the next step.

>[!NOTE]
>
>**Enable partial ingestion **specifies the number of errors (**INGEST** and **DCVS**) as a percentage of the total number of records that can fail before the entire dataflow is declared a failure.

