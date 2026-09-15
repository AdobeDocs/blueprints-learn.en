---
title: Edge Activation
description: Learn how Edge, streaming, and batch activation speeds differ, and preview the lab steps for creating an edge segment and configuring event forwarding.
doc-type: overview-page
solution: Experience Platform
exl-id: 9ecadff9-3838-4cd4-93b1-7c23a232f84c
---

# Edge Activation

## Activation speed recap

Adobe has three speeds of activation meant to address different needs:

1. Edge
1. Streaming
1. Batch

We will go through how to activate using the Adobe Edge with Event Forwarding, Edge Audiences and Edge Personalization. We will then show how to use Streaming Destinations from the Hub to both the Edge and to an external destination.

>[!IMPORTANT]
>
>Complete [Postman setup](../../setup.md) before starting this lab. You also need access to [webhook.site](https://webhook.site/) to capture the event sent to the external destination.

>[!NOTE]
>
>We will not be covering Batch Activation in this lab. Batch Activation can be scheduled at different intervals and the timing makes it hard to showcase in a lab environment without having at least 3-24 hours.



## What the lab will cover

- Create Edge Segment
- Configure Event Forwarding
- Send in an Edge Event
- This triggers
  - Edge Segment to qualify
  - Event Forwarding on Edge to send to webhook
