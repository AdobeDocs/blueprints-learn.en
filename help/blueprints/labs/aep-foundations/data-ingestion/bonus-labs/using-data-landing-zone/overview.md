---
title: Using Data Landing Zone
description: Using Data Landing Zone
doc-type: overview-page
solution: Experience Platform
exl-id: d61bef25-7039-450d-a8e7-01bb12e8df7c
---

# Pre-requisite

If you haven't downloaded Azure Storage Explorer do so now as its a requirement for this lab.  You can find the download at the link below:

[Download Azure Storage Explorer](https://azure.microsoft.com/en-us/blog/microsoft-azure-data-lake-storage-adls-in-storage-explorer-public-preview/)

1. Install the application
1. On 1st launch accept the End user License Agreement

![End user license agreement screen.png "End User License Agreement screen"](assets/rT5YtfnGtfBojx3BQ9sFo_end-user-license-agreement-screen.png "End-User License Agreement screen")


## Configure Azure Storage Explorer with Experience Platform 

1. Open Azure Storage Explorer and click on the **Select Resource icon **and then select **ADLS Gen 2 Container or directory**

![Choose the resource as shown above](assets/choose-the-resource-as-shown-above.png)



2\. Select **Shared access signature URL (SAS) **and click **Next**

![Choose the sas url option as the mode of connection.png "Choose the SAS URL option as the mode of connection"](assets/rZAMQkVlythnjbt8d6TvE_choose-the-sas-url-option-as-the-mode-of-connection.png "Choose the SAS URL option as the mode of connection")



3\. Enter the Display name as **Data Landing Zone**

>[!NOTE]
>
>You cannot continue at this step until you provide the SAS URL.  You will get this from the Experience Platform which you will see in the next step.

![IfzxEsIUJ1z1 Vaq0 name the connection.png "Name the connection"](assets/D84_ifzxEsIUJ1z1_Vaq0_name-the-connection.png "Name the connection")



4\. Go to Adobe Experience Platform and perform the navigate to the Data Landing zone by doing the following:

- Navigate to **Sources -> Catalog**
- Select **Cloud Storage **under the sources
- Next locate the **Data Landing Zone** card
- Click on the Data Landing Zone Card and then click **View Credentials **on the right rail

![LxxLyKc0x1oi JqCymPDJfxfQrCz7YwkDW 20241025 020415.png "Access Data Landing Zone Source Card in Adobe Experience Platform"](assets/n-ADAXZy_lxxLyKc0x1oi-JqCymPDJfxfQrCz7YwkDW-20241025-020415.png "Access Data Landing Zone Source Card in Adobe Experience Platform")



5\. Copy the **SASUri** from the modal that displays.

Navigate back to Azure Storage Explorer and paste the **SASUri value** into the **Blob container or directory SAS URL** you left blank from the previous step

![K copy the.png "Copy the SAS URL credentials from Adobe Experience Platform and copy it onto Azure Storage Explorer"](assets/wVoRej68xvZv5Sm7g68_k_copy-the.png "Copy the SAS URL credentials from Adobe Experience Platform and copy it onto Azure Storage Explorer")



6\. Click **Next **to continue

![KCGVSqbCGrw0 copy sas url credentials into the sas url section in connection info.png "Copy SAS URL credentials into the SAS URL section in connection info"](assets/DuFA2rMn_kCGVSqbCGrw0_copy-sas-url-credentials-into-the-sas-url-section-in-connection-info.png "Copy SAS URL credentials into the SAS URL section in connection info")



7\. On the Summary screen click **Connect**

![Y9qs3O connect screen.png "Connect screen"](assets/H5E6vkWiawIvTF_y9qs3O_connect-screen.png "Connect screen")



You should now see a screen that looks like below

![UVRldu H79PE898a successfully connected account](assets/successfully-connected-account.png)

>[!NOTE]
>
>Congratulations!  You've successfully configured Azure Storage Explorer

