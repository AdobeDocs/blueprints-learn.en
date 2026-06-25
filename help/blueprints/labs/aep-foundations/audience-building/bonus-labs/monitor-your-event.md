---
hold: true
title: Monitor Your Event
description: Monitor Your Event
doc-type: article

solution: Experience Platform
exl-id: 94b200c0-6714-4996-a266-119cc8f7f4e2
---

# Navigate to Assurance

[Adobe Experience Platform Assurance](https://experienceleague.adobe.com/en/docs/experience-platform/assurance/home) is a product from Adobe Experience Cloud to help you inspect, proof, simulate, and validate how you collect data to the Adobe Experience Platform Edge.

1. Go to Adobe Experience Platform -> Assurance -> Create Session

![Go to adobe experience platform greater assurance greater create session](assets/JhXXw8zJa8U6LH9Tqozdj_go-to-adobe-experience-platform-greater-assurance-greater-create-session.png)



2\. Click on the **Start **button

![Start](assets/cOkdH6YSAkhMvrCtvjEBe_start.png)



## Configure a Session

1. Name --> \[Sandbox] Edge Session
1. URL --> https\://www\.adobe.com
   - Note this URL would be replaced by your customer's actual site 
1. Click the Next button

![Next](assets/QnynlFfHRWLh2v26hkel__next.png)

4\. Copy the link somewhere you can reference later

5\. Click the **Done **button

![Copy link](assets/9S1Uju5MONpZh8onHWUR5_copy-link.png)



6\. Navigate to **Settings**

![LxxLyKc0x1oi gxaSyFh9sQmczCtvIBRll 20241025 193023.png "Click on settings"](assets/n-ADAXZy_lxxLyKc0x1oi-gxaSyFh9sQmczCtvIBRll-20241025-193023.png "Click on settings")



7\. Enable **Event Transactions **and **Edge Delivery **by clicking on the **+ **button, then **Done**

![GDCKe 79Aw6  done](assets/mOYnYAh0_GDCKe-79Aw6-_done.png)


Open Postman
============

Go to Postman -> Create Web Event Edge (No Auth) -> Headers

1. Add the **x-adobe-aep-validation-token** to the Headers with the link copied above from Assurance. Grab **just the ID** value after the = in the link you copied from Assurance. e.g. [https://www.adobe.com/?adb\_validation\_sessionid=](https://www.adobe.com/?adb_validation_sessionid=efa4a9ed-02d8-4647-80fa-f01a5be273d0)[`efa4a9ed-02d8-4647-80fa-f01a5be273d0`](https://www.adobe.com/?adb_validation_sessionid=efa4a9ed-02d8-4647-80fa-f01a5be273d0)
1. We would just use the [`efa4a9ed-02d8-4647-80fa-f01a5be273d0`](https://www.adobe.com/?adb_validation_sessionid=efa4a9ed-02d8-4647-80fa-f01a5be273d0)value, not the full url

![Populate the x adobe aep validation token](assets/CXGFont6YjTCwCl7M51Dt_populate-the-x-adobe-aep-validation-token.png)



2\. In Postman, save and execute the** Create Web Event Edge (No Auth)** request



## View Assurance Logs

Go back to Assurance and you should see a bunch of events showing. Filter down to just relevant event types by putting your datastream ID in the search

![Filter using search](assets/0rdMwZbJLRHIaO5HAdn5i_filter-using-search.png)



Select an event and open any messages if needed on the right rail.

![Expand messages](assets/G5MKtQVwQ6FHtz1cAF9Zq_expand-messages.png)

Event types to look for:

- hitReceived (shows the payload received by the Edge)
- evaluatingRule (if you set up SSF, shows rules being evaluated)
- firedDestinations (which destinations was this sent to)
- segmentsDiscovered (did it qualify for any edge segments)
- com.adobe.experience\_platform.edge\_segmentation/response (what segments did it respond with)

![Select each event](assets/OHNH2o7RV83SPvIGew6fv_select-each-event.png)

Explore these and see how each step is interpreted by Assurance.
