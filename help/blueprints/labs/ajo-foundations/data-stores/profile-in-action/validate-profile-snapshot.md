---
title: Validate Profile Snapshot
description: Validate Profile Snapshot
doc-type: article
solution: Experience Platform
exl-id: 1e7befcf-d952-47a2-86d9-33ef71eec57a
---

# Learning Objective

Confirm that the profile does not yet appear in the Profile Snapshot dataset.

## Use the Profile Snapshot dataset

1. In the left nav under the Data Management section click on **Datasets** and then click on the **Browse tab **found on the top rail

![HIN4jxLqEgIZCnbv8I lI 20260127 215248](assets/validate-profile-snapshot-4.png)

1. In the **search box** type `profile`, then **click on the row **with title "Profile-Snapshot...".   and in the right rail **copy the table name** and paste it somewhere you can reference in the next step.

>[!WARNING]
>
>You may have to clear any filters if you don't see the "Profile-Snapshot..." dataset.



![C3FEbl2Yj94iKHcBcK0RN 20260127 215905](assets/validate-profile-snapshot-2.png)

1. Navigate back to the Query editor and copy & paste the below SQL into the editor

```sql
select
  identityMap,
  segmentID,
  segmentMembershipUps[segmentID] ['lastQualificationTime'],
  segmentMembershipUps[segmentID] ['status'],
  current_timestamp
from
  (
    select
      identityMap,
      explode (map_keys (segmentMembership['ups'])) as segmentID,
      segmentMembership['ups'] as segmentMembershipUps
    from
   
    where
      map_keys (segmentMembership['ups']) is not null
    limit 100
  )
  --where identityMap['email'][0].id = 'henry.creel@emailsim.io'
  limit 50
```

1. Update the table name and email address as outlined below:
   - **Table name:**  on line 14 copy & paste the table name you have for the Profile Snapshot table between the `from`and `where`
   - **Email address:**  for now, on line 19 type in the same email address you used to send in your Web Event (we used henry.creel\@emailsim.io, unless you changed it).
     - At the moment, we have commented this out (leave it that way). When the query runs, look for henry, you will not find it.

![FLuAXb a7CgvkGA1WxnP1 20260127 220848](assets/validate-profile-snapshot-3.png)

1. **Run **the query by clicking on the arrow in the top left
1. The Results should be as below (but if you look for henry, you will not find him)

![QBJV33I3p0ddfWiWk5Ft 20260615 110951](assets/validate-profile-snapshot-1.png)

>[!NOTE]
>
>**Why no results for Henry? **
>
>**Reminder**: The Profile Snapshot is a **reflection **or snapshot of what existed in Profile at a **specific point in time**. The job is run **daily **and is used for downstream purposes like AJO. Since we just streamed in this data, the Profile Snapshot does not yet have it.  It will tomorrow.

## Recap

Understand that snapshot datasets update on a scheduled batch process rather than immediately.
