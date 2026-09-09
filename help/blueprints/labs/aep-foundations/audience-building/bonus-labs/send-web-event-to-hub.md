---
title: Send Web Event to Hub
description: Learn how to send a web event directly to the Hub using Postman and validate that it reaches the profile and qualifies for streaming segments.
doc-type: article
solution: Experience Platform
exl-id: a8343499-b4d5-4540-8fe1-7497bc20e437
---

# Open Postman

Launch postman on your computer and navigate to the following API call:

1. **Postman Left Sidebar**  --> `Collections`
1. **Collection** --> `AEP Foundations Bootcamps (labs)`
1. **Folder** --> Profile Lab
1. **API Request** --> `Create Web Event`

![Create web event api request](assets/create-web-event-api-request-2.png)


## Modify API Request

To create the sample API request you need to fill in the following pieces in the body of the API request.

Start by gathering the following values:



## Find Account Streaming Endpoint

1. Navigate to **Sources** in the left rail and then click on **Accounts** in the top nav
1. Search for **dep: HTTP API \[raw]**, highlight the row and copy and save the value of the **Streaming Endpoint** somewhere you can reference later

![LxxLyKc0x1oi VT rvewysl8ABem1xFkox 20241025 024115.png "dep: HTTP API \[raw]"](assets/n-ADAXZy_lxxLyKc0x1oi-VT-rvewysl8ABem1xFkox-20241025-024115.png "dep: HTTP API \[raw]")

###

## **Find Web Dataflow ID**

1. Click into the **HTTP API \[raw]** Account
1. Find and Select the dataflow row called **dep: Web (stream)**
1. In the right rail copy and save the **Dataflow ID** values somewhere you can reference later

>[!NOTE]
>
>Click in an empty space on the row.  DO NOT click on the blue links!

![LxxLyKc0x1oi pRZ4Hwpscm O OGuzxNgV 20241025 024319.png "Web Dataflow ID"](assets/n-ADAXZy_lxxLyKc0x1oi-pRZ4Hwpscm_O_OGuzxNgV-20241025-024319.png "Web Dataflow ID")

###

## Create Final API Request

Copy the values you saved in the previous steps into the places highlight below.  

- **Red** --> `Streaming Endpoint URL`
- **Green** --> `Dataflow ID`

Your final API request should look like this when done

>[!NOTE]
>
>DO NOT EXECUTE YET!

![Final web api request](assets/final-web-api-request.png)

###

## Execute the API

1. Save your API call by clicking the **Save** button
1. Execute your request by clicking the **Send** button

A successful call should result in the following response...

![Successful web event send](assets/successful-web-event-send-2.png)

###

## Validate

1. Go over to your Profile and lookup your Profile to see that the event was ingested onto Profile.  It should appear in seconds.
   1. Use the email in your call to lookup the Profile
1. Depending on how long it was since you last sent in an evant, you may not qualify for new Segments. Otherwise you may see these or others:
   1. Any Event Edge (within 15 minutes)
      1. Remember: all audiences saved with an Edge evaluation also are evaluated on the Hub when streaming data comes in
   2. dep: Any Event Streaming (within the hour)
1. You may not see anything appear at your webhook if you have no new Segments.  
1. Event Forwarding won't send anything.
   1. Why? This event went to the Hub, not the Edge, thus, the event will not appear as an something for Event Forward to send, nor in Assurance.
1. After at least 30 minutes, you can even check your dataset with the following:
   1. Change the table name below to the one from your sandbox.  To find it, go to your dataset list and filter on "`dest`", open the dataset and copy the table name on the right rail.

```sql
SELECT * FROM profile_export_for_destination_merge_policy_xxx
WHERE extSourceSystemAudit.LASTREFERENCEDDATE >= CURRENT_DATE
AND identitymap['email'][0].ID in ('depche.mode@dep.com')
ORDER BY extSourceSystemAudit.LASTREFERENCEDDATE DESC
LIMIT 10
```
