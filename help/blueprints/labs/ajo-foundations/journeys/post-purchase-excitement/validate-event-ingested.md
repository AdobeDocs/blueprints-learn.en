---
hold: true
title: Validate Event Ingested
description: Validate Event Ingested
doc-type: article

solution: Experience Platform
exl-id: c04397dd-8b5c-48a8-82b5-78188b8374f1
---

# Learning Objective

Confirm that the event was successfully ingested into Adobe Experience Platform.

## Validate Event in Profile

1. Go over to your **Profiles** and lookup your Profile to see that the event was ingested onto Profile.  It should appear in seconds.
   - **Identity namespace** -> `email`
   - **Identity value** -> `henry.creel@emailsim.io`
1. Click on **Events **tab. Look for `orders.shipped` event.

![PpKXqvI9HUjWc 20251118 002104](assets/validate-event-ingested-3.png)

>[!WARNING]
>
>Did you get any **message.feedback** events.  These are from Journeys and usually indicate a failure or exclusion.  Click on them and look at the `reason`.
>
>Some examples you might run into in production might be:
>
>- EmailNoAddressFoundInProfile (you tried to send an email to a profile that didn't have an email)
>- EmailNoConsent (you tried to send an email to a profile that had consent set to no.



1. Validate the Profile has qualified for the **Audiences** (it may take a few minutes).
   - Any Event Edge (within 15 minutes)
   - Any Event Streaming (within 15 minutes)

![NIpWSijjwrCP8n9yT7qb 20251118 002155](assets/validate-event-ingested-2.png)



## Try with Your Own Email

Now that you have validated the Profile got in, let's send in some Order Shipped Events using your own email.

1. Go back to Postman, find the **Ship Order Event**
1. click on the **Body **& change the **email address** to yours.  

![J6R uupsRQFa3cVlQi4aq 20251111 230837](assets/validate-event-ingested-1.png)

1. **Save **and hit **Send**.  
1. Go back to steps 1-3 and validate using your email address. 

## **Recap**

The event appears in the Profile store and the Profile is now part of Audiences that were  looking for the event.
