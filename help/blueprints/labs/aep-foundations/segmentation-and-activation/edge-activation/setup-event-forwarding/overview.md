---
hold: true
title: Setup Event Forwarding
description: Setup Event Forwarding
doc-type: overview-page
solution: Experience Platform
exl-id: da3d1c7f-3642-4de7-a297-fc36d09e7336
---

Event Forwarding sits on the Edge and allows us to create a set of rules and light transformations to send events to any endpoint.

At this step we are going to forward all events that we send into the Edge to a webhook. The webhook will act as a proxy for a third party and allow us to see what is happening.

To configure this, we will set up:

- A Property that contains all the extensions, data elements and rules needed to decide what to forward and where
  - A Data Element to reference the incoming event or parse it into multiple individual components if needed 
  - A Rule to add any Conditions on what to forward, transform the payload and where to send it
- A Datastream that configures which services that will utilize it (e.g. Event Forwarding & AEP)
  - Data sent to these Datastreams can then take action according to the service configured (e.g. forward an event and send data to a Dataset)

