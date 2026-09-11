---
title: Stream an order event
description: Practice building an HTTP API streaming dataflow to send a sample order event and link it to an existing customer profile.
doc-type: article
solution: Experience Platform
exl-id: 558c21d1-f9b7-489b-9153-5f10d0b8448a
---

# Stream an order event

## Prerequisites

1. You have downloaded the [Sample Files](../sample-files.md) and see the file named --> **Lab\_Single\_Order\_sample.json**
1. You have successfully completed the [Using Data Landing Zone](./using-data-landing-zone/overview.md) lab and have a valid mapping set to import

## Challenge

Perform the following set of tasks just as you did in the previous lab. 

1. Create a new account using the HTTP API source connector
1. Set up a dataflow using the new account to stream data into your own Customer Orders dataset
1. Re-use the mapping set from the [Using Data Landing Zone](./using-data-landing-zone/overview.md) lab
1. In Postman populate the **Create Order Event** with the necessary information to successfully stream in the data and attach it to your previously created Customer Account record
1. Verify the Order is linked to your profile

>[!TIP]
>
>Good luck and may the Adobe Experience Platform gods be with you!
