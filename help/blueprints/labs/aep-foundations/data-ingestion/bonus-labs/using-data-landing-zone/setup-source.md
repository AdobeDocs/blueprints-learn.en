---
title: Set up the source
description: Upload a sample Customer Account file to the Data Landing Zone and configure a new cloud storage source dataflow.
doc-type: article
solution: Experience Platform
exl-id: 1c80e71b-19a7-45e9-9961-d72b3f03ecae
---

# Set up the source

## Upload sample file

You need to upload a sample data file to your Data Landing Zone via Azure Storage Explorer so that you can use it during the lab.  To do so, do the following:

1. Download the [Sample Files](../../sample-files.md) 
1. Drag 'n drop and/or upload the **Lab\_Customer\_Account.csv** file to the Data Landing Zone you saved from the previous step.

When uploaded your screen should look like the below screenshot. 

>[!WARNING]
>
>Make sure you do not upload the file into the *project* folder. It contains preloaded data that you don't use in our labs.

![Data Landing Zone file browser showing the uploaded Lab_Customer_Account.csv file, not the project folder](assets/setup-source-make-sure-you-do-not-upload-the-file.png)

## Navigate to Sources

1. Go to Adobe Experience Platform and navigate to: **Sources** -> **Catalog** -> **Cloud storage**
1. Click on **Setup** / **Add Data** for the Data Landing Zone

![Setup or Add data action for the Data Landing Zone cloud storage source](assets/setup-source-add-data-landing-zone-source.png "Access the Data Landing Zone")

>[!NOTE]
>
>If at least one connection exists for that source, you see **Add data** as the default action. If no connections exist for that source, you see **Setup** as the default action

## Preview the file

1. Select the **Lab\_Customer\_Account.csv**

![Selecting the Lab_Customer_Account.csv file to preview in Azure Storage Explorer](assets/setup-source-select-lab-customer-account-csv.png "Accessing the Azure Storage Explorer files within Adobe Experience Platform")

1. In the preview pane, look at the following attributes and observe the following:

- **sms\_optIn** is a consent field that has several missing values (shown in preview as - )
- **account\_create\_date** does not have the proper date format. It has string values along with date and time values in one string.
- **account\_end\_date** has the proper date format.



![sms_optIn field with several missing values shown in the file preview](assets/setup-source-sms-optin-missing-values.png "sms_optin")



![account_create_date and account_end_date fields shown in the file preview](assets/setup-source-account-create-date-account-end-date.png "account_create_date & account_end_date")

>[!NOTE]
>
>You will need to deal with the missing values, dates and improperly formatted fields in the mapping steps later in this lab

1. Click **Next** in the upper right corner of the screen to continue to the next step



## Set up the dataflow

1. In the Dataflow detail screen, choose **New dataset**. 
1. Name the output dataset as **Customer Account - \<Your Initials>**
1. Select the **dep: Customer Account** schema from the dropdown list.
1. Turn on the **Profile dataset** toggle box.
   (If you do not turn this on, the Profile Store is not able to monitor for new data entering this dataset and hence does not ingest this data into Profile)
1. Turn on the **Enable partial ingestion**.
   (If you do not turn this on, the ingestion may fail if one of the records has errors)
1. Set the Dataflow name as **Customer Account Batch Ingestion – \<Your Initials>** 
1. Turn on all the alerts **Sources Dataflow Start/Success/Failure**

![Dataflow detail screen with new dataset, profile toggle, and partial ingestion settings configured](assets/setup-source-dataflow-detail-screen-settings.png "Data Flow Details")

>[!CAUTION]
>
> Ensure you have **enabled the** dataset for both profile and partial ingestion.

Click **Next** in the upper right corner of the screen to continue to the next step.

>[!NOTE]
>
>**Enable partial ingestion** specifies the number of errors (**INGEST** and **DCVS**) as a percentage of the total number of records that can fail before the entire dataflow is declared a failure.
