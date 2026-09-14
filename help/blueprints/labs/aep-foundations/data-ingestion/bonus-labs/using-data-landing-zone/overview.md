---
title: Using Data Landing Zone
description: Install and configure Azure Storage Explorer with a SAS URL to connect to the Adobe Experience Platform Data Landing Zone.
doc-type: overview-page
solution: Experience Platform
exl-id: d61bef25-7039-450d-a8e7-01bb12e8df7c
---

# Using Data Landing Zone

## Prerequisites

If you haven't downloaded Azure Storage Explorer do so now as it's a requirement for this lab.  You can find the download at the link below:

[Download Azure Storage Explorer](https://azure.microsoft.com/en-us/blog/microsoft-azure-data-lake-storage-adls-in-storage-explorer-public-preview/)

1. Install the application
1. On first launch accept the End User License Agreement

![End User License Agreement screen in Azure Storage Explorer](assets/overview-end-user-license-agreement-screen.png "End-User License Agreement screen")


## Configure Azure Storage Explorer with Experience Platform 

1. Open Azure Storage Explorer and click on the **Select Resource icon** and then select **ADLS Gen 2 Container or directory**

   ![Selecting ADLS Gen2 Container or directory as the resource in Azure Storage Explorer](assets/overview-choose-the-resource-as-shown-above.png)



1. Select **Shared access signature URL (SAS)** and click **Next**

   ![Choosing the SAS URL option as the mode of connection](assets/overview-choose-the-sas-url-option-as-the-mode-of-connection.png "Choose the SAS URL option as the mode of connection")



1. Enter the Display name as **Data Landing Zone**

   >[!NOTE]
   >
   >You cannot continue at this step until you provide the SAS URL.  You get this from the Experience Platform, which you see in the next step.

   ![Naming the connection Data Landing Zone](assets/overview-name-the-connection.png "Name the connection")



1. Go to Adobe Experience Platform and perform the navigate to the Data Landing zone by doing the following:

   - Navigate to **Sources -> Catalog**
   - Select **Cloud Storage** under the sources
   - Next locate the **Data Landing Zone** card
   - Click on the Data Landing Zone Card and then click **View Credentials** on the right rail

   ![Data Landing Zone source card with View Credentials option in Adobe Experience Platform](assets/overview-data-landing-zone-view-credentials.png "Access Data Landing Zone Source Card in Adobe Experience Platform")



1. Copy the **SASUri** from the modal that displays.

   Navigate back to Azure Storage Explorer and paste the **SASUri value** into the **Blob container or directory SAS URL** you left blank from the previous step

   ![Copying the SASUri value from Experience Platform into Azure Storage Explorer](assets/overview-copy-sas-uri-into-azure-storage-explorer.png "Copy the SAS URL credentials from Adobe Experience Platform and copy it onto Azure Storage Explorer")



1. Click **Next** to continue

   ![Copying SAS URL credentials into the SAS URL section of the connection info](assets/overview-copy-sas-url-into-connection-info.png "Copy SAS URL credentials into the SAS URL section in connection info")



1. On the Summary screen click **Connect**

![Summary screen with Connect button](assets/overview-connect-screen.png "Connect screen")



You should now see a screen that looks like below

![Azure Storage Explorer showing the successfully connected Data Landing Zone account](assets/overview-successfully-connected-account.png)

>[!SUCCESS]
>
>Congratulations!  You've successfully configured Azure Storage Explorer
