---
title: Sandbox access
description: Verify your Postman environment can successfully retrieve your assigned Experience Platform sandbox before starting the labs.
doc-type: article
solution: Experience Platform
exl-id: c841e497-a695-4d3f-85e6-d653478cad1e
---

# Sandbox access

Before you continue, double check that your access is legit. Perform the following steps:

1. Open the folder titled `Check Sandbox Access` and click on the call titled `Retrieve Your Sandbox`
1. Next in the upper right corner of Postman you see an Environment drop-down box.  Be sure to select the `AEP Bootcamp` environment
1. Execute the call by clicking the `Send` button

![Postman request pane for the Retrieve Your Sandbox call before sending](assets/sandbox-access-check-sandbox-request.png "Retrieve your sandbox API call")



A successful response looks like so:

![200 OK response confirming successful retrieval of the assigned sandbox](assets/sandbox-access-successful-response.png "200 OK Successful sandbox request")

>[!NOTE]
>
>The **name** value should match the sandbox\_name variable in your postman environment

>[!TIP]
>
>Congratulations!  You are ready to start using the Experience Platform APIs
