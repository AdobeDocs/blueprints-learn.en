---
hold: true
title: Validate event on Data Lake
description: Learn how to query the Data Lake to verify that a streamed web event was written to the correct dataset.
doc-type: article
solution: Experience Platform
exl-id: 14445089-aa3c-4cce-9d33-80032b6f9868
---

# Validate event on Data Lake

## Learning objective

Verify that the web event was written to the Experience Platform Data Lake.

## Validate event

> [!NOTE]
>
>Eventually the data will appear in the Data Lake.  **This could take up to 60 minutes**.  We know the dataset is enabled for profile and thus the event will create a profile fragment.
>
>You can find and query the Web dataset.

1. Go to **Queries** and **Create Query**

![Create Query screen in the Queries section](assets/validate-event-on-data-lake-create-query.png)

2. Copy this SQL and paste it into your query

```sql
SELECT identityMap['email'][0].id, * FROM dep_web
where identityMap['email'][0].id = 'henry.creel@emailsim.io'
```

3. **Run** Query

> [!NOTE]
>
>**Remember**: Eventually the data will appear in the Data Lake.  **This could take up to 60 minutes**.
>
>You do not need to wait for it to appear. Feel free to come back to this step and check later.



![Query results showing the streamed web event in the data lake](assets/validate-event-on-data-lake-query-results.png)

## Recap

The event record appears in the appropriate dataset.
