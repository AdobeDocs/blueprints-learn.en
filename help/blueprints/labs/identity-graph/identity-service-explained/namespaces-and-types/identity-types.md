---
title: Identity types
description: Learn the difference between person and non-person identity types and how each determines whether an identity is processed into the Identity Graph.
doc-type: article
solution: Experience Platform
exl-id: 3aa69c7f-0dcc-443e-bf82-3cf699b7e4e4
---

# Two Types of Identities

In order to differentiate whether an identity participates in the creation of a person-based identity graph, all identity namespaces have identity types. There are two categories of identity types:

- **Person Types** - utilized by the identity graph at processing time
- **Non-Person Types** - ignored by the identity graph at processing time



## Person Types

These identity types tell identity service to process the identity records into the identity graph when two or more exist within a single record of data.

- **Cookie ID** - used specifically for web browsers
- **Individual Cross-Device ID** - catch all bucket used to identify a person (i.e. CRM ID, Loyalty ID, etc.)
- **Hardware Device ID** - used specifically for hardware devices like mobile phones, tablets, set-top boxes, etc. Examples are IDFA (Apple), GAID (Android) and RIDA (Roku's) to name a few.
- **Email** - email address of a person
- **Phone Number** - phone number of a person

## Non-Person Types

These identity types tell identity service to ignore processing the identities into the identity graph

- **Non-people Identifier** - represent identities that are not describing a person such as Product SKU or Household ID (typically used for lookup tables within the Real-Time Customer Profile)
- **Partner ID** - provided by data partners that may or may not represent people

>[!NOTE]
>
>Identity Service will only process identities when two or more exist within a row of data and the identity types are person-based. The Identity Graph's purpose is to store deterministic relationships about a person.



