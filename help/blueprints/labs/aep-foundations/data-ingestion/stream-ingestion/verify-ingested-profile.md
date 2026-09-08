---
title: Verify Ingested Profile
description: Verify Ingested Profile
doc-type: article
solution: Experience Platform
exl-id: d45d6baf-9597-4419-b838-03156ce8cc83
---

# Streaming Validation

Validating streaming data within the Adobe Experience Platform requires a few different steps.  Remember that streaming data can write to multiple databases depending on the dataset's configuration.

| Storage        | Latency                                                                    | Description                                                            |
| -------------- | -------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Data Lake      | \~up to 60 minutes                                                         | The final resting place for all streaming data                         |
| Profile Store  | \~1 min on avg. but up to \~15min                                          | Only processes data when the underlying dataset is enabled for profile |
| Identity Store | \~1 min avg. \~10 min micro-batches for net new identity relationships | Only processes data when the underlying dataset is enabled for profile |

Depending on what you trying to validate you may have to go to a few different places as you can see from above.  In this scenario, you wrote the data to the profile (as you had enabled the dataset for the profile) so you will want to check the Profile Store to see if the profile is there.



## Look Up Your Profile

1. In the UI navigate to the **Profiles -> Browse**
1. Enter the following values into the Identity namespace and Identity value input boxes:
   - **Identity namespace** -> `customerID`
   - **Identity value** -> `202208240125`
1. Click the **View** button to lookup your profile
1. Click on the **Profile ID** link in the returned row to view your profile

![REiI53URbvx screenshot 2024 10 24 at 64233 pm.png "Browse Profile screen"](assets/OL-s0RYUP_rEiI53URbvx_screenshot-2024-10-24-at-64233-pm.png "Browse Profile screen")

Please take a look at your profile and validate it matches what you streamed in. Pretty cool huh!

![Screenshot 2024 10 24 at 64329 pm](assets/screenshot-2024-10-24-at-64329-pm.png)

>[!NOTE]
>
>Given the \~10min latency on net new identity relationship stitching, had you tried to look up your profile using the email namespace you would not have seen a response.  
>
>Using the customerId namespace instead (which is the primary identity) ensured you could look up the profile immediately.  
>
>Remember that profile only knows about the primary identities 😄

