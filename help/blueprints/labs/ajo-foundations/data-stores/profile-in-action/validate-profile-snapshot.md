---
hold: true
title: Validate Profile Snapshot
description: Learn how to query the Profile Snapshot dataset and understand why a newly streamed profile update doesn't appear until the next daily batch job.
doc-type: article
solution: Experience Platform
exl-id: 1e7befcf-d952-47a2-86d9-33ef71eec57a
---

# Validate Profile Snapshot

## Learning objective

Confirm that the profile does not yet appear in the Profile Snapshot dataset.

## Use the Profile Snapshot dataset

1. In the left nav under the Data Management section click on **Datasets** and then click on the **Browse tab** found on the top rail

![Datasets Browse tab in the Data Management section](assets/validate-profile-snapshot-datasets-browse-tab.png)

2. In the **search box** type `profile`, then **click on the row** with title "Profile-Snapshot...".   and in the right rail **copy the table name** and paste it somewhere you can reference in the next step.

> [!NOTE]
>
>You may have to clear any filters if you don't see the "Profile-Snapshot..." dataset.



![Search results for the Profile-Snapshot dataset](assets/validate-profile-snapshot-dataset-search.png)

3. Navigate back to the Query editor and copy & paste the below SQL into the editor

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

4. Update the table name and email address as outlined below:
   - **Table name:**  on line 14 copy & paste the table name you have for the Profile Snapshot table between the `from` and `where`
   - **Email address:**  for now, on line 19 type in the same email address you used to send in your Web Event (we used henry.creel\@emailsim.io, unless you changed it).
     - At the moment, we have commented this out (leave it that way). When the query runs and you look for henry, you don't find him.

![Query editor with the Profile Snapshot table name and email address to update](assets/validate-profile-snapshot-update-query-table-name.png)

5. **Run** the query by clicking on the arrow in the top left
6. The Results are as below (but if you look for henry, you don't find him)

![Query results showing no match for the streamed profile in the snapshot](assets/validate-profile-snapshot-query-results-no-match.png)

>[!NOTE]
>
>**Why no results for Henry?**
>
>**Reminder**: The Profile Snapshot is a **reflection** or snapshot of what existed in Profile at a **specific point in time**. The job is run **daily** and is used for downstream purposes like AJO. Since you just streamed in this data, the Profile Snapshot does not yet have it.  It will tomorrow.

## Recap

Understand that snapshot datasets update on a scheduled batch process rather than immediately.
