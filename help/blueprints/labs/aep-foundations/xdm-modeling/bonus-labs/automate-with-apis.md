---
title: Automate with APIs
description: Run a Postman collection that automates creating schemas, field groups, identity and relationship descriptors, and datasets in a single run.
doc-type: article
solution: Experience Platform
exl-id: a490f93f-19da-4de3-81c8-4569c49c5354
---

# Automate with APIs

## Introduction

To see how you can automate deployments using APIs you execute a folder of APIs that creates the following objects:

- Customer Account and Plan \[Lookup] schema(s)
- Field groups that compose the schemas above
- Identity descriptors required for profile
- Relationship and reference descriptors required for creating the relationships between Customer Account and Plan \[Lookup]
- Two datasets matching each schema created



## Execute the folder

1. In Postman navigate to the **Automation with APIs** folder within the **XDM Schema Lab** folder

   ![Automation with APIs folder within the XDM Schema Lab folder in Postman](assets/automate-with-apis-postman-automation-folder.png)



1. Click on the **Automation with APIs** folder and in the workspace click on the **Run** button

   >[!NOTE]
   >
   >The run button is in the upper right of your Postman workspace

   ![Run button in the upper right of the Postman workspace for the Automation with APIs folder](assets/automate-with-apis-click-folder-run-button.png "Click on the folder Run")



1. A new window appears that shows all the API calls in the folder. Set the **Delay** to **500ms** and then click on the **Run** button.

   ![Execute Automation dialog with Delay set to 500ms before clicking Run](assets/automate-with-apis-execute-automation-dialog.png "Execute automation")



1. You see the API calls start to execute in order, and when complete you see 32 passed tests.

   ![Successful automation run with 32 passed tests](assets/automate-with-apis-successful-automation-32-passed-tests.png "Successful Automation")



1. Go to the Experience Platform UI and you see two schemas and two datasets created and enabled for profile with the prefix of **postman:**

![Two schemas created and enabled for profile with the postman: prefix](assets/automate-with-apis-schemas-created-in-ui.png "Automation Schemas")



![Two datasets created with the postman: prefix matching the automated schemas](assets/automate-with-apis-datasets-created-in-ui.png "Automation Datasets")

>[!SUCCESS]
>
>Congratulations!  You automated the deployment of identity namespaces, field groups, schemas, identity/relationship descriptors and enabled a schema for profile and generated a dataset utilizing the schema
