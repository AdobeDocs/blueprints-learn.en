---
title: Validate Event on Data Lake
description: Validate Event on Data Lake
doc-type: article
solution: Experience Platform
exl-id: 14445089-aa3c-4cce-9d33-80032b6f9868
---

# Learning Objective

Verify that the web event was written to the Experience Platform Data Lake.

## Validate Event

>[!WARNING]
>
>Eventually the data will appear in the Data Lake.  **This could take up to 60 minutes**.  We know the dataset is enabled for profile and thus the event will create a profile fragement.
>
>You can find and query the Web dataset.

1. Go to **Queries **and **Create Query**

![NBZzK2rgWOnAsq8e1BVqo 20251027 224300](assets/NBZzK2rgWOnAsq8e1BVqo-20251027-224300.png)

1. Copy this SQL and paste it into your query

```sql
SELECT identityMap['email'][0].id, * FROM dep_web
where identityMap['email'][0].id = 'henry.creel@emailsim.io'
```

1. **Run **Query

>[!WARNING]
>
>**Remember**: Eventually the data will appear in the Data Lake.  **This could take up to 60 minutes**.
>
>You do not need to wait for it to appear. Feel free to come back to this step and check later.



![GWmv8Krk7SCvP9VFbFgDD 20251120 030733](assets/GWmv8Krk7SCvP9VFbFgDD-20251120-030733.png)

## Recap

The event record appears in the appropriate dataset.
