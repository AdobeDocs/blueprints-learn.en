---
title: Test Journey (cloned with children)
description: Test Journey (cloned with children)
doc-type: article
exl-id: 7545158e-015d-4015-a7b9-8e0121eca591
---

# Learning Objective

Use the journey testing tools to verify that the event trigger and journey logic are configured correctly.

# Test the Journey

1. Click on **Journeys **on the left rail and the **Browse tab** if you don't see a list of Journeys
2. Click on your **Journey **to open it
3. Click on **Alerts **& ensure no errors (warnings are ok)

![](assets/dvImaqds_ZYn2cnZa6-L1-20251113-200640.png)

>[!NOTE]
>**What is CJMMAS - 2001-200**
>
>Indicates the opt-out link is missing in an email variant

4. Click on the **Simulate **and on the left side, select **Test Mode**

![](assets/wnyV5WyS3iyKIvOILMzRU-20260615-104621.png)



>[!NOTE]
>It might take a minute to get ready. During that time the Trigger an Event button will not be available.



5. Click **Trigger an Event **and fill out these properties:
   - **Event Type**: `orders.shipped`
   - **Personal Email**: `henry.creel@emailsim.io`
   - **Order ID**: `123`
6. Click **Send **(note, it takes a few seconds to respond after clicking send)

![](assets/SvyzYc4SMYffxKat90AuF-20251113-201239.png)

>[!CAUTION]
>**Note**: Some students get errors and need to send this a few times. You may have to do this **multiple **times.
>
>**Sometimes **the first Send gives an error of:
>
>**Inlet does not exist (Reference id: 3216a850-c40d-11f0-8fa5-73d1522cc9a2)**
>
>If you get an error, Click** Trigger an Event**, then **send **again.  You may have to do this **multiple times**.



7. Under **Results **-> Click **Show Log **on left side

![](assets/T83sahcgABemDM7PnACDD-20251113-201517.png)

>[!WARNING]
>Some students who received errors sometimes receive different logs that look more like the below. This is not a blocker, go ahead and move on to the next step:
>
>\{
>  "instances": \[]
>}



You should see something like this in the log:

>[!NOTE]
>We are looking for the key fields we used
>
>...
>      "**actionsHistory**": \{
>        "8919055f-1b00-4a43-8bd6-c8af894474b2": \{
>          "**eta**": "11/27/2025",
>          "**tracking\_number**": "091204404",
>          "jo\_status\_code": "http\_200"
>        }
>      },
>      "**transitionsHistory**": \{
>        "orderShipped (1158856989)": \{
>          "**eventType**": "**orders.shipped**",
>          "\_id": "joTestModeEvent\_5abbfdcd-561d-45a7-ba42-d0640539831a",
>          "\_dep": \{
>            "**personalEmail**": "henry.creel\@emailsim.io"
>          },
>          "order": \{
>            "**orderID**": "123"
>          },
>          "timestamp": "2025-11-17T23:30:49.576289372Z",
>          "\_experience": \{
>            "campaign": \{
>              "orchestration": \{
>                "eventID": "0afa45de34b6217707c9eea915cbe0b0384ab970bcd26122f4ece977fd9040af"
>              }
>            }
>          }
>        },
>        "\{GetShippingDetails (a03d4b8d-e734-4717-a7f8-e3fa2a848723\_8919055f-1b00-4a43-8bd6-c8af894474b2)} -> \{Email (40ef8272-871d-4eb5-b1e3-825a8ea1bbdf)} (df153ea0-e105-3467-9590-a2351c6f83b2)": \{},
>        "\{Email (40ef8272-871d-4eb5-b1e3-825a8ea1bbdf)} -> \{End (250b03fb-da4d-4e79-a424-25d540bd4f1d)} (2880ab91-cc84-3961-bfe5-2e652085001b)": \{}
>      }
>    }
>  ]
>}



8. **Close **the Browser **tab**
9. **Close Test Mode** in the top right

![](assets/niqxGZjRWMi7MDiQul5hw-20251117-235338.png)

10. Click on **Publish **the Journey in the top right

![](assets/rqfeWFQA4yR0J8CvPxu5o-20251118-001155.png)

11. **Close **the **Journey **by clicking \<- arrow in the top left

![](assets/zxaTyocb4irBpx9COCJRk-20251117-235355.png)

Next we will send a real Order Shipped Event into AEP

# Recap

The journey has passed configuration validation and is ready to receive events
