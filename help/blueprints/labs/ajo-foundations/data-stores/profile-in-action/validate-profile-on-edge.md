---
hold: true
title: Validate Profile on Edge
description: Validate Profile on Edge
doc-type: article

solution: Experience Platform
exl-id: f82ceba7-6916-49ff-8776-2d0238560df8
---

# Learning Objective

Confirm that the profile does not exist on the Edge network profile store.

## Validate Profile on Edge 

1. Click on the **Attributes **tab and the ***Edge ***radio button to see the Edge Profile

![Haz0UYeW1zeZ3imcMyvVe 20251120 025352](assets/haz0UYeW1zeZ3imcMyvVe-20251120-025352.png)

>[!NOTE]
>
>It is possible you may see a "stripped down" version of the profile that consists of only the identities depending on how much time has passed.



1. Click on the Audience Membership tab.  It will be **blank**.

![DLDIDx 20251120 025608](assets/u2S-VLbyqe13et_DLDIDx-20251120-025608.png)

>[!NOTE]
>
>**Why no Edge Membership?**
>
>Shouldn't we have seen **dep: Any Event Edge (within the hour) **qualify?
>
>Even though we have an audience that has an Edge evaluation, that audience does not exist on the Edge because we have no reason for it out there... yet.  
>
>If we were to use that audience (e.g. Decisioning or Destinations), then the audience rules will be pushed to the Edge and next time an event is streamed into the Edge, it will evaluate that audience.
>
>Also, we didn't turn on Edge Segmentation Services.



## Recap

The profile does not exist on the Edge (yet)
