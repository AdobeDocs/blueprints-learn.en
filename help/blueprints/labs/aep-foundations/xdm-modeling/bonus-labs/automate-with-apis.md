---
title: Automate with API's
description: Automate with API's
doc-type: article
exl-id: a490f93f-19da-4de3-81c8-4569c49c5354
---

# Introduction

To see how you can automate deployments using API's you will execute a folder of APIs that will create the following objects:

- Customer Account and Plan \[Lookup] schema(s)
- Field groups that compose the schemas above
- Identity descriptors required for profile
- Relationship and reference descriptors required for creating the relationships between Customer Account and Plan \[Lookup]
- Two datasets matching each schema created



# Execute the Folder

1. In Postman navigate to the **Automation with APIs** folder within the** XDM Schema Lab** folder

![Automate with APIs folder](assets/n-ADAXZy_lxxLyKc0x1oi-QGfnKiMXL9JPmaW9nVIEB-20241017-190316.png)



2\. Click on the **Automation with APIs **folder and in the workspace click on the **Run **button

>[!NOTE]
>The run button is in the upper right of your Postman workspace

![](assets/k48Az7N7R7fieBX8NJ7lJ_click-on-the-folder-run.png "Click on the folder Run")



3\. A new window should appear that shows all the API calls in the folder. Set the **Delay **to **500ms **and then click on the **Run **button.

![](assets/xiCgs4_VRMmiYsVdCv6Wz_execute-automation.png "Execute automation")



4\. You will see the API calls start to execute in order and when complete you should see 32 passed tests.

![](assets/0AFXuzHE0Ok6zCsAGBWaJ_successful-automation.png "Successful Automation")



5\. Go the Experience Platform UI and you should see two schemas and two datasets created and enabled for profile with the prefix of **postman:**

![](assets/n-ADAXZy_lxxLyKc0x1oi-W_W3kPDYjFu52exXE6-bs-20241017-191330.png "Automation Schemas")



![](assets/BcqFozB78hmUiuOusmC6R_automation-datasets.png "Automation Datasets")

>[!NOTE]
>Congratulations!  You just automated the deployment of identity namespaces, field groups, schemas, identity/relationship descriptors and enabling a schema for profile and generating a dataset utilizing the schema

