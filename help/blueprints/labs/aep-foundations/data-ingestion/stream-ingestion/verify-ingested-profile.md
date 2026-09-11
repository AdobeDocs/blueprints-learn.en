---
title: Verify ingested profile
description: Look up a streamed profile in the Profiles browser using its primary identity namespace to confirm successful ingestion.
doc-type: article
solution: Experience Platform
exl-id: d45d6baf-9597-4419-b838-03156ce8cc83
---

# Verify ingested profile

## Streaming validation

Validating streaming data within the Adobe Experience Platform requires a few different steps.  Remember that streaming data can write to multiple databases depending on the dataset's configuration.

| Storage        | Latency                                                                    | Description                                                            |
| -------------- | -------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Data Lake      | \~up to 60 minutes                                                         | The final resting place for all streaming data                         |
| Profile Store  | \~1 min on avg. but up to \~15min                                          | Only processes data when the underlying dataset is enabled for profile |
| Identity Store | \~1 min avg. \~10 min micro-batches for net new identity relationships | Only processes data when the underlying dataset is enabled for profile |

Depending on what you are trying to validate you may have to go to a few different places as you can see from above.  In this scenario, you wrote the data to the profile (as you had enabled the dataset for the profile) so check the Profile Store to see if the profile is there.



## Look up your profile

1. In the UI navigate to the **Profiles -> Browse**
1. Enter the following values into the Identity namespace and Identity value input boxes:
   - **Identity namespace** -> `customerID`
   - **Identity value** -> `202208240125`
1. Click the **View** button to look up your profile
1. Click on the **Profile ID** link in the returned row to view your profile

![Browse Profile screen showing the returned profile row after searching by customerID](assets/verify-ingested-profile-browse-profile-screen.png "Browse Profile screen")

Please take a look at your profile and validate it matches what you streamed in. Pretty cool huh!

![Profile detail view matching the streamed Customer Account record](assets/verify-ingested-profile-profile-detail-view.png)

>[!NOTE]
>
>Given the \~10min latency on net new identity relationship stitching, had you tried to look up your profile using the email namespace you would not have seen a response.  
>
>Using the customerID namespace instead (which is the primary identity) ensured you could look up the profile immediately.  
>
>Remember that the profile only knows about the primary identities 😄
