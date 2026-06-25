---
hold: true
title: Validate Profile on Hub
description: Validate Profile on Hub
doc-type: article

solution: Experience Platform
exl-id: f1c8b1ac-e57c-48c6-aa91-5c83f79ce7e3
---

# Learning Objective

Verify that the event resulted in a profile update and segment qualification in Real-Time Profile on the Hub.

## Lookup the Profile on Hub

In Adobe Experience Platform lookup the profile you just sent in from the event you just sent into the Edge Network.  

1. Navigate to **Customer **-> **Profiles **-> **Browse **to perform the lookup using the following information:
   - **Merge policy** -> `Default Timebased`
   - **Identity Namespace** -> `Email`
   - **Identity Value** ->  `henry.creel@emailsim.io`
1. Click **View **to lookup up the profile

![YhLnKD84tNVUxSLTan2bG 20251223 172059](assets/yhLnKD84tNVUxSLTan2bG-20251223-172059.png)



## Validate Profile on Hub

1. Click on the **Profile ID** to open the profile
1. Click on the **Attributes **tab first and the ***Hub ***radio button to see the **Hub Profile**

![IJ iro 20251107 005528](assets/woTrja2xouGiFi_IJ-iro-20251107-005528.png)


## Validate Events

1. Click on **Events **in the top nav and you can see the event you just sent in

![ZH1XaOgtwuC 20251222 222838](assets/i10MOG8a9_zH1XaOgtwuC-20251222-222838.png)

## Validate Segments

### Via JSON

1. Click on the **Attributes **header and View **JSON**

![2jS2liqd8p8Bb yRTLTfn 20251111 223239](assets/2jS2liqd8p8Bb-yRTLTfn-20251111-223239.png)

1. Find **segmentMembership**.  It should look like this (your IDs will be different)

```json
  "segmentMembership": {
    "ups": {
      "ce0b8386-ef2a-4244-8ad0-1a72d6494181": {
        "status": "realized",
        "lastQualificationTime": "2025-12-15T23:11:49Z"
      },
      "8ce516fe-920a-4f9d-b92b-0403890a8491": {
        "status": "realized",
        "lastQualificationTime": "2025-12-12T15:01:01Z"
      }
    }
```

>[!NOTE]
>
>**How to read segmentMembership?**
>
>[https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/segmentation)
>
>**ups: **This is the map key for different kinds of audiences supported by AEP.  The ups key contains audiences created by the Rule Builder.  Other auidences will be contained in other keys (e.g. AAM).
>
>**lastQualificationTime    **A timestamp of the last time this profile qualified for the segment
>
>**status    
**
>*realized*: The profile qualifies for the segment.
>*exited*: The profile is exiting the segment as part of the current request.
>
>

### Via UI

1. An easier way to validate the Profile has qualified for the Audiences is by looking at the **Audience Membership** tab (you should see at least these):
   - dep: Any Event Streaming (within the hour)
   - dep: Any Event Edge (within the hour)

![QyX j 20251120 025018](assets/sKN3WoWhsJzIOwW_QyX_j-20251120-025018.png)

>[!NOTE]
>
>**Why no Batch Audience?**
>
>You should not see **dep: Any Event Batch (within the day) **qualified for since we streamed in data and batch evaluation happens once a day.

## Recap

A profile exists on the Hub and is qualified for the expected audience.
