---
title: Environment file
description: Import the Postman environment file and populate its developer project and sandbox variables needed for the bootcamp's API calls.
doc-type: article
solution: Experience Platform
exl-id: 1461fac5-0714-44d4-b5c8-949df6bcff83
---

# Environment file

## Postman environment file

Download File — [AEP Bootcamp.postman_environment.json](assets/aep-bootcamp.postman_environment.json)



## Import environment file

1. Open the `Environment File` from above in your browser by clicking on the file
1. Copy the URL of the file to your clipboard
1. Launch Postman on your local machine and click on the `Import` button within your workspace
1. Paste the URL of the `Environment File` into the import modal text box on the overlay.  This should trigger an automatic import

![Clicking the Import button in the Postman workspace to import the environment file](assets/environment-file-click-import-button.png "Import Button")



![Pasting the environment file URL into the Postman import modal text box](assets/environment-file-import-modal-paste-url.png "Import Button Overlay")



Once imported, you can validate your environment file exists by clicking on the `Environments` tab in the left sidebar.  You should see something similar to below.

![AEP Bootcamp environment listed under the Postman Environments tab after import](assets/environment-file-aep-bootcamp-environment-listed.png "AEP Bootcamp Environment")



## Environment variables

Before you can make any API calls you need to update a few of the variables in the environment file you just imported.  These variables are referenced in the API calls so be sure they are correctly filled in.  The variables are broken into two groups:

- **Developer Project Values** -> these are the default variables generated from the Developer Project that were created in the Adobe Developer Console
- **Other Values** -> these are custom created variables that are typically created by a user to work with the various Experience Platform APIs

>[!NOTE]
>
>These values come from the OAuth Server-to-Server credential you created in [Developer Console Setup](../sandbox-setup/developer-console-setup.md#collect-your-values)



### Update developer project values

1. Click on the `Environments` tab in the left sidebar of Postman
1. Next click on the `AEP Bootcamp` environment file
1. Update the `current values` for the below listed variables:
   - CLIENT\_SECRET
   - CLIENT\_ID (also called API KEY)
   - TECHNICAL\_ACCOUNT\_ID
   - IMS\_ORG

When done your environment file should look similar to this:

![Environment file after updating CLIENT_SECRET, CLIENT_ID, TECHNICAL_ACCOUNT_ID, and IMS_ORG values](assets/environment-file-with-developer-project-values.png "Environment File with Developer Project values")

### Update other values

The only other values that need to be updated are the `SANDBOX_NAME` variable and the `TENANT_NAME` variable.

- `SANDBOX_NAME` - tells Adobe Experience Platform what sandbox to execute against
- `TENANT_NAME` - used to pre-populate the tenant name in specific XDM calls

>[!NOTE]
>
>If you're working through these labs at your own pace (rather than a live training event with a sandbox-assignment.pdf), you can find both values while logged into your sandbox from the Adobe Experience Platform UI URL, for example:
>
>`https://experience.adobe.com/#/@dep/sname:prod/platform/home`
>
>- `SANDBOX_NAME` is the value after `sname:` — in this example, `prod`
>- `TENANT_NAME` is the value after the `@` symbol, prefixed with an underscore — in this example, `_dep`

1. Update the `current values` for the below listed variables:
   - SANDBOX\_NAME
   - TENANT\_NAME
1. Save your updates by clicking the `Save` button in the top right of the environment workspace

When you are done your environment file should look like this:

![Environment file after updating the SANDBOX_NAME and TENANT_NAME values](assets/environment-file-with-sandbox-name-and-tenant-name.png "Environment File with SANDBOX_NAME")

>[!TIP]
>
>Congratulations! You have completed your Postman Environment configuration
