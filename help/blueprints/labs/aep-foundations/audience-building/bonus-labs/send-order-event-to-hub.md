---
hold: true
title: Send Order Event to Hub
description: Send Order Event to Hub
doc-type: article

solution: Experience Platform
exl-id: d5de39d7-7340-487a-86fa-504344daeab7
---

# Streaming to Hub vs Edge

In Use Case #1 we sent in an Event to the Edge.  There are some use cases where we may have a back end system that wants to stream in an event, but does not need to send it to the Edge.  This lab shows how to do that by streaming in an Order event to the Hub.

## Create an Order Segment (if you haven't)

Click on Audience on the left rail and create Audience button in the top right.  

![Click on](assets/LVT9qiIXxVZaVJ3UqcxOc_click-on.png)

Find and use Order Placed Event Type card and Drag that onto the canvas.

![C let s use order placed event type card and drag that onto the canvas](assets/8rycT7n9l00yXr8yi9d_C_let-s-use-order-placed-event-type-card-and-drag-that-onto-the-canvas.png)

## Update Event Rules

Make the following changes to the event rules (you may need to expand the event to see it)

1. In Last
1. 15
1. Minutes
1. Change to Streaming Evaluation

Save as **Order Event Streaming (within 15 minutes)**



![Image](assets/1h0MQ-tRlcIDtKFustwl4_image.png)

## Activate to Destination

Open the audience you just created if it is closed.

Click Activate to Destination



![K5 image](assets/4i7TVl1ONe8sIvKxbi_k5_image.png)

### Destination

Select the Streaming Destination you created earlier (Streaming DEP Webhook)



![XQnwts5CiaLLjQ  image](assets/etDXZ_XQnwts5CiaLLjQ__image.png)

### Mapping

Leave Mapping alone and click Next

![Image](assets/JafCnlfB55WIfkwUfaiPd_image.png)

Click Finish

## Open Postman

Launch postman on your computer and navigate to the following API call:

1. **Postman Left Sidebar**  --> `Collections`
1. **Collection **--> `AEP Foundations Bootcamps (labs)`
1. **Folder **--> Profile Lab
1. **API Request** --> `Create Order Event`

![W43tBv create web event api request](assets/Kjsq3C7LCIYktN_w43tBv_create-web-event-api-request.png)


## Modify API Request

To create the sample API request you need to fill in the following pieces in the body of the API request.

Start by gathering the following values:

## Find Account Streaming Endpoint

1. Navigate to **Sources **in the left rail and then click on **Accounts **in the top nav
1. Search for **dep: HTTP API \[raw]**, highlight the row and copy and save the value of the **Streaming Endpoint** somewhere you can reference later

![LxxLyKc0x1oi VT rvewysl8ABem1xFkox 20241025 024115.png "dep: HTTP API \[raw]"](assets/n-ADAXZy_lxxLyKc0x1oi-VT-rvewysl8ABem1xFkox-20241025-024115.png "dep: HTTP API \[raw]")

## ****

## **Find Dataflow ID**

1. Find the record for **dep: Orders (stream)** click on the dataflows link
1. In the right rail copy and save the **Dataflow ID** values somewhere you can reference later

>[!NOTE]
>
>Click in an empty space on the row.  DO NOT click on the blue links!

![Screenshot 2024 10 24 at 73808 pm.png "Web Dataflow and Dataset IDs"](assets/YZq5xpIpR2udKhtI8osBm_screenshot-2024-10-24-at-73808-pm.png "Web Dataflow and Dataset IDs")

## Create Final API Request

Copy the values you saved in the previous steps into the places highlight below.  

- **Red **--> `Streaming Endpoint URL`
- **Green **--> `Dataflow ID`

Your final API request should look like this when done

>[!NOTE]
>
>DO NOT EXECUTE YET!

![Tguisg final order api request](assets/W0BXKhP2HZxF1f_Tguisg_final-order-api-request.png)


## Execute the API

1. Save your API call by clicking the **Save **button
1. Execute your request by clicking the **Send **button

A successful call should result in the following response...

![Successful web event send](assets/IkJ9XpJRVvnPsxIep6jWG_successful-web-event-send.png)

###

## Validate

1. Go over to your Profile and lookup your Profile to see that the event was ingested onto Profile.  It should appear in seconds.
   1. Lookup the Profile using the email in the Order
1. Validate the Profile has qualified for the Segments (it may take a few minutes). It should appear in seconds to minutes.
   1. Order Event Streaming (within 15 minutes)
1. Check your webhook to see if the Destination has notified the webhook of a Segment "realized".  It should appear in 5-10 minutes.
1. After 15-30 minutes, you can even check your dataset with the following:
   1. Change the table name below to the one from your sandbox.  To find it, go to your dataset list and filter on "`dest`", open the dataset and copy the table name on the right rail.

```sql
SELECT * FROM profile_export_for_destination_merge_policy_xxx
WHERE extSourceSystemAudit.LASTREFERENCEDDATE >= CURRENT_DATE
AND identitymap['email'][0].ID in ('depche.mode@dep.com')
ORDER BY extSourceSystemAudit.LASTREFERENCEDDATE DESC
LIMIT 10
```

