---
hold: true
title: Validate Journey
description: Validate Journey
doc-type: article

solution: Experience Platform
exl-id: 2e6e73e5-6bd8-4dde-ba06-29b67f927131
---

# Learning Objective

Verify that the journey was triggered and executed as expected.  Verify reports show metrics updated as expected.

## Checking Your Journey

1. Go to your Order Shipped Journey, open it if you closed it
1. You should see at least 2 Profile Entered

![Iwa42eUkpVbVCNYzyI4jK 20251224 002013](assets/validate-journey-2.png)

1. Click **View Report **->** Last 24 hours** in the top right.
1. By default, you should be in the **Journey **tab (on the left rail)
   - You should see some enters and exits (count will depend on how many events you sent in, any testing, any errors, etc.)

![VClBq 20251118 002624](assets/validate-journey-1.png)

If everything went through clean you should have (scroll down to check):

**Journey's statistics**

3 Entered Profiles (Henry, You and the Testing we did)

You can click the toggle at the top to **exclude test events** if you want and you will see these numbers change

3 Exited Profiles (Henry, You and the Testing we did)

**Actions executed and errors**

6 Actions (3 Email, 3 GetShippingDetails)

**Actions error reasons**

0 Errors (hopefully)

**Events**

3 Events (orderShipped)

3 External Events

1. Click on the **Email **tab (on the left rail)
   - **Email - Sending Performance**
     - You should see some values for **Delivered **and **Sent **(count will depend on how many events you sent in, any errors, etc.)
     - Hopefully, you have no errors (unless you ran into some problems earlier)
   - **Email - Statistics**
     - Email - 3 targeted, sent, delivered

![MOGtLfhTriQ u5UwoTNYQ 20251118 002651](assets/validate-journey-3.png)

1. Go check your **email inbox** and see if you got the email (it should look similar to this below)
   - *,*your order has shipped ETA: *10/17/2026* Tracking Number: *051009364*

>[!CAUTION]
>
>Check your Spam folder for AJO Campaigns [ajo-campaigns@email.dep-labs.com](mailto:ajo-campaigns@email.dep-labs.com)

>[!NOTE]
>
>**Why is first name missing?**
>
>We changed the Email node to look at the Event Context for the email address.  But the first name in the personalization is pulling from \{\{profile.person.name.firstName\}\}.  
>
>When you look up your profile for your email, do you have a firstName?



1. *After 30-60 minutes*, you can even check your dataset in the data lake with the following: **Queries **-> **Create Query** -> **Copy/Paste SQL** -> **Run**

>[!NOTE]
>
>**Note**: The order shipped event was streamed in, so while it updated profile quickly, it will take a while before the data lake is updated.

```sql
SELECT * FROM dep_orders
WHERE timestamp >= CURRENT_DATE
LIMIT 10
```

![Xqv654TpraIH1PHv0dFgW 20251118 195218](assets/validate-journey-4.png)

## Bonus (check Step Events)

>[!NOTE]
>
>Step Events records whenever a profile starts a journey and every step in the journey. Note: it may take a few minutes to record these events into the dataset.



1. While in Query Service, you can view what the step events dataset is capturing by running this SQL. Copy the below SQL and paste into a query.

```sql
select timestamp,
  identityMap,
  _experience.journeyOrchestration.stepevents.journeyVersionName,
  _experience.journeyOrchestration.stepevents.NodeName,
  _experience.journeyOrchestration.stepevents.*
  from journey_step_events
limit 50
```

Results will have over 100 columns and gives you an idea of what Step Events records.

>[!NOTE]
>
>Curious about what each field means, check out the AJO Schema Dictionary and change the drop down to the Journey Step Events schema: [https://experienceleague.adobe.com/tools/ajo-schemas/schema-dictionary.html?lang=en](https://experienceleague.adobe.com/tools/ajo-schemas/schema-dictionary.html?lang=en)



## Recap

The journey instance appears in journey reporting or logs and the configured action is executed
