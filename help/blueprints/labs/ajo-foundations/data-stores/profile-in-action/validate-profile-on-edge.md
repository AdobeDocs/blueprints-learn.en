---
title: Validate Profile on Edge
description: Learn how to check the Edge profile store and Audience Membership tab to confirm a profile's status on the Edge network.
doc-type: article
solution: Experience Platform
exl-id: f82ceba7-6916-49ff-8776-2d0238560df8
---

# Validate Profile on Edge

## Learning objective

Confirm that the profile does not exist on the Edge network profile store.

## Check the Edge Profile

1. Click on the **Attributes** tab and the **Edge** radio button to see the Edge Profile

   ![Edge Profile shown on the Attributes tab](assets/validate-profile-on-edge-attributes-tab.png)

   >[!NOTE]
   >
   >It is possible you may see a "stripped down" version of the profile that consists of only the identities depending on how much time has passed.



2. Click on the Audience Membership tab.  It will be **blank**.

![Empty Audience Membership tab on the Edge profile](assets/validate-profile-on-edge-empty-audience-membership-tab.png)

>[!NOTE]
>
>**Why no Edge Membership?**
>
>Shouldn't we have seen **dep: Any Event Edge (within the hour)** qualify?
>
>Even though we have an audience that has an Edge evaluation, that audience does not exist on the Edge because we have no reason for it out there... yet.  
>
>If we were to use that audience (e.g. Decisioning or Destinations), then the audience rules will be pushed to the Edge and next time an event is streamed into the Edge, it will evaluate that audience.
>
>Also, we didn't turn on Edge Segmentation Services.



## Recap

The profile does not exist on the Edge (yet)
