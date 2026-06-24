---
title: Environment File
description: Environment File
doc-type: article
exl-id: 1461fac5-0714-44d4-b5c8-949df6bcff83
---

# Postman Environment File

[Download File](<assets/AEP Bootcamp.postman_environment.json>) — AEP Bootcamp.postman_environment.json



# Import Environment File

1. Open the `Environment File` from above in your browser by clicking on the file
2. Copy the URL of the file to your clipboard
3. Launch Postman on your local machine and click on the `Import` button within your workspace
4. Paste the URL of the `Environment File` into the import modal text box on the overlay.  This should trigger an automatic import

![](assets/uCY1kQDFa7lfHFWTuKtvr_import-buttonenvironmental-file.png "Import Button")



![](assets/ygbntV4Irq-weJ24YD3c1_import-button-overlayenvironmental-file.png "Import Button Overlay")



Once imported, you can validate your environment file exists by clicking on the `Environments` tab in the left sidebar.  You should see something similiar to below.

![](assets/T0-r1SaY5Q3ZCm3RxsWmZ_aep-bootcamp-environmentenvironmental-file.png "AEP Bootcamp Environment")



# Environment Variables

Before you can make any API calls you need to update a few of the variables in the environment file you just imported.  These variables are referenced in the API calls so be sure they are correctly filled in.  The variables are broken into two groups:

- **Developer Project Values** -> these are the default variables generated from the Developer Project that were created in the Adobe Developer Console
- **Other Values **-> these are custom created variables that typically created by a user to work with the various Experience Platform APIs

>[!NOTE]
>Reference the sandbox-assignment.pdf to get all the values required for your environment file



### Update Developer Project Values

1. Click on the `Environments` tab in the left sidebar of Postman
2. Next click on the `AEP Bootcamp` environment file
3. Update the `current values` for the below listed variables:
   - CLIENT\_SECRET
   - CLIENT\_ID (also called API KEY)
   - TECHNICAL\_ACCOUNT\_ID
   - IMS\_ORG

When done your environment file should look similar to this:

![](assets/wEQbeKucQCHY8m_ZlZXC6_environment-file-with-developer-project-valuesenvironmental-file.png "Environment File with Developer Project values")

###

### Update Other Values

The only other values that need to be updated are the `SANDBOX_NAME` variable and the `TENANT_NAME` variable.

- `SANDBOX_NAME` - tells Adobe Experience Platform what sandbox to execute against
- `TENANT_NAME` - used to pre-populate the tenant name in specific XDM calls

>[!NOTE]
>These values will come from your sandbox-assignment.pdf

1. Update the `current values` for the below listed variables:
   - SANDBOX\_NAME
   - TENANT\_NAME
2. Save your updates by clicking the `Save` button in the top right of the environment workspace

When you are done your environment file should look like this:

![](assets/EyshNCyi8TRJ8wRkfhVgK_environment-file-with-sandbox-nameenvironmental-file.png "Environment File with SANDBOX_NAME")

>[!TIP]
>Congratulations! You have completed your Postman Environment configuration

