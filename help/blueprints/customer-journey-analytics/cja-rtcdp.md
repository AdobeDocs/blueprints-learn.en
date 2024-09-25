---
title: Customer Journey Analytics with Real-time Customer Data Platform blueprint
description: Unify and analyze data and customer behaviors from across the customer journey in Customer Journey Analytics, publish audience from CJA to RTCDP
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 9e1ba723-63f2-4622-ba67-f2a315c3ba0c
---
# Customer Journey Analytics with Real-time Customer Data Platform blueprint

Create and publish audiences identified in Customer Journey Analytics (CJA) to Real-time Customer Profile in Adobe Experience Platform for customer targeting and personalization. Ideal for creating audiences using historical data or more refined audiences from granular filtering and computed fields in Customer Journey Analytics.

## Customer Journey Analytics audience publishing guide

See the following documentation for guidance on implementation and configuration on publication of audiences from Customer Journey Analytics to Real-time Customer Data Platform. [Documentation](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html)

## Architecture for Customer Journey Analytics blueprints

![Architecture diagram](assets/CJA.svg){zoomable="yes"}

## Guardrail diagram for Customer Journey Analytics blueprints

* For detailed guardrails and end to end latencies refer to the [deployment guardrails document](../experience-platform/deployment/guardrails.md)

![Guardrail diagram](../experience-platform/deployment/assets/CJA_guardrails.svg){zoomable="yes"}

## Frequently asked questions

* If a corresponding profile does not exist in RTCDP that CJA sent, will a new profile be created, or are audiences only recorded from CJA for profiles that are already present? Yes, a new profile will be created. As a result if your RTCDP implementation is for known customers only, the CJA audience rules should be written to filter for only profiles with known identities. This will ensure that the RTCDP Profile count does not increase from anonymous profiles if not desired.

* What identities does CJA send over? CJA sends over whichever identities were configured as the "person ID" during CJA configuration.

* What is set as the primary identity? Whatever identity the user selected when they set up CJA as the primary "person" ID.

* Does the identity service process the CJA messages as well? i.e. can CJA add identities to a profile identity graph through audience sharing? No, identity service does not process the CJA messages.