---
title: AJO B2B Paid Media Controller
description: Priority of campaigns and activation of accounts to Paid Media destinations
solution: Journey Optimizer B2B Edition
exl-id: a4f4982f-2b56-4ce2-9c16-abdf627f97de
---
# AJO B2B - Account Journey Orchestration - Paid Media Controller

## Overview

Marketing teams running B2B paid media at scale face a recurring problem: **accounts end up in multiple campaigns at once** (persona, category awareness, solution-led, pursuit), which dilutes messaging, causes audience fatigue, and forces manual list work—uploads, exclusions, and suppression—across LinkedIn Account Match (Account Destination). Without **waterfall prioritization** and **automated campaign assignment**, there is no single place to decide which account gets which message, and operations do not scale.

The **Paid Media Controller** is a perfect solution in addressing this problem. It uses **Adobe Journey Optimizer B2B Edition (AJO B2B)** and **Adobe Experience Platform (AEP)** together: one **account journey** reads a qualified-account audience from Real-Time CDP, applies **split-path (waterfall) logic** to assign each account to exactly one campaign tier, and **activates each path directly** to paid media destinations (**e.g., LinkedIn Matched Audiences**)—with no manual list handoffs. The outcome is precision control, less overlap, and a repeatable pattern for multichannel B2B paid media orchestration.

## Use Case: A marketer's story: Why a controller matters

*Maya leads paid media for a global B2B brand. Her team runs dozens of campaigns—foundational awareness, category intent (Journey, Data, Content), solution-led programs, persona campaigns, and must-win pursuits. She has a problem.*

**The problem:** The same accounts show up in multiple campaigns. A high-intent Journey account is also in a broad awareness list; a pursuit account still gets persona ads. List uploads and exclusions are manual. Every time sales updates a "must-win" list or a new persona campaign launches, her team re-exports audiences, reconciles overlaps in spreadsheets, and re-uploads to LinkedIn and other platforms. It's slow, error-prone, and doesn't scale.

**What she wants:** One place where every qualified account is evaluated once, assigned to the *most relevant* campaign using clear priority rules (waterfall), and sent to the right paid media destination—automatically. No manual list handoffs. When data or strategy changes, the system re-evaluates and moves accounts between campaigns without her team touching lists.

**Adobe's answer:** With **AJO B2B and AEP working together**, Maya can run a single **Paid Media Controller** journey: AEP and Real-Time CDP hold the data and one master "qualified accounts" audience; AJO B2B runs an account journey that uses **split-path logic** (waterfall) to route each account into the right tier—e.g., Targeted Pursuits → Solution-Led → Persona → Category Awareness → Foundational Awareness—and **Activate to Destination** sends each path to the right LinkedIn (or other) campaign. One journey, one source of truth, no manual list exports. That's the Paid Media Controller pattern—and it's how Adobe enables precision and scale for B2B paid media.

## Why it matters for B2B enterprises:

Organizations that adopt this pattern can eliminate manual suppression and exclusion logic entirely (e.g., 100% of overlap resolution handled in the journey), scale to **tens of thousands of accounts** through a single controller, and maintain a **single source of truth** for which account goes to which campaign. The system **automatically adapts** as campaign focus, target audiences, and sales goals change, without re-exporting lists or re-uploading to each platform. For any B2B enterprise running multiple paid media campaigns, the Paid Media Controller pattern delivers the clarity, control, and automation that manual list workflows cannot.

The following KPIs align well with measuring success:

- **Awareness:** Are target accounts seeing the right ads and moving to the right campaigns at a higher rate?
- **Engagement:** Are engagement and conversion better when overlap is removed?
- **Efficiency:** How much has manual list work (uploads, exclusions, suppression) decreased?
- **Cost:** How does cost per acquired account or opportunity change with automated orchestration?

## Paid Media Journey orchestration

A common use case, and the focus of this blueprint, is **B2B paid media Journey orchestration**: ensuring every qualified account is assigned to exactly one campaign tier and activated to the correct paid media destination, without overlap or manual handoffs.

The controller journey **reads** a qualified-account audience (built in Real-Time CDP from AEP data), **evaluates** each account through split-path (waterfall) conditions—e.g., pursuit → solution-led → persona → category intent → foundational—and **activates** each path to the corresponding destination (e.g., LinkedIn Matched Audiences for each campaign).

**Account-focused solution:** The focus of the Paid Media Controller is **accounts** and their **campaign assignment**. The technical setup supports the data and audiences that represent qualified accounts and their attributes (e.g., intent, segment, persona), which is required for successful account-level segmentation and journey-based orchestration.

## Requirements

The account-focused solution requires the following applications and services:

- **Adobe Journey Optimizer B2B Edition** — Account journeys, split-path (waterfall) logic, Activate to Destination.
- **Adobe Real-time Customer Data Platform (RTCDP) B2B Edition** — Account profiles, account audiences (e.g., qualified accounts for paid media).

## Architecture

High-level flow:

1. **Data & audiences** — AEP holds profiles and events; Real-Time CDP B2B builds account audiences (e.g., "Paid Media Eligible Accounts") used as the journey entry audience.
2. **Orchestration** — AJO B2B account journey: **Read audience** (qualified accounts) → **Split path** (waterfall: e.g., Pursuit → Solution-Led → Persona → Category → Foundational) → **Activate to Destination** (per path to LinkedIn or other paid media).
3. **Destinations** — Paid media channels (e.g., LinkedIn Matched Audiences) receive account-level activation from each journey path; no manual list uploads.

## Architecture Diagram

<img src="assets/ajo-b2b-paid-media-activation-architecture.svg" alt="AJO B2B Paid Media Controller Architecture" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## Data Modelling in B2B AEP

With any data-driven orchestration, schema design is important. Account and person profiles in AEP/RTCDP must include the attributes used in **split-path conditions** (e.g., pursuit flag, solution interest, persona, intent category, engagement score). B2B schemas (XDM Business Account, XDM Individual Profile, relational) should represent your hierarchy and data sources. For details, see [RTCDP B2B schemas](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) and [AJO B2B documentation](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/home).

**Note:** Split-path logic in the journey uses profile and, where supported, relational data; ensure the fields you need for waterfall logic are available in the journey.

### Guardrails

- **Journey Optimizer B2B Edition** — See the [product description](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer-b2b.html) for journey limits, node limits, and destination support.
- **Real-Time CDP** — See [RTCDP guardrails](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/guardrails/overview) for segmentation and activation limits.

## Implementation

The following steps give guidance for implementing the Paid Media Controller with AJO B2B and AEP.

### Pre-requisite steps

1. **Define account audiences and Data Model in Real-Time CDP B2B.**

   Create the **qualified-account audience** (e.g., "Paid Media Eligible Accounts") that will enter the controller journey. Use Segment Builder and the account/person attributes that define eligibility (e.g., geography, segment, MQA status). This audience is the single entry point for the journey.

2. **Define campaign hierarchy and split logic.**

   Document the waterfall order (e.g., Pursuit → Solution-Led → Persona → Category → Foundational) and the conditions for each path (which attributes or audiences qualify an account). Ensure conditions are **mutually exclusive in order** (top-down): an account should match at most one path, the first one that evaluates true.

3. **Configure destinations.**

   Set up paid media destinations (e.g., LinkedIn Matched Audiences) in AEP/RTCDP and ensure they are available for activation from AJO B2B. Map account identifiers and any required attributes for each destination.

### Paid Media Controller configuration

1. **Create the controller journey in AJO B2B.**

   - **Read audience:** Select the qualified-account audience from Real-Time CDP.
   - **Split path:** Create a path for each paid media audiences, starting with Path 1 as your top priority and proceeding in priority order. For each path, add attributes to set the criteria for qualification (e.g., “in Pursuit audience,” “solution interest = X,” “persona = Y,” “intent category = Z”). Accounts evaluate through the split path node a in waterfall fashion, qualifying for the first path that they meet criteria for.
   - **Activate to Destination:** For each path, add an Activate to Destination node to the correct LinkedIn (or other) campaign/destination.

2. **Validate mutual exclusivity.**

   - Confirm that each account enters only one path (the first matching condition).
   - Verify activation: accounts appear in the right destination and are excluded from lower-priority campaigns as intended.

## Implementation Diagram

<img src="assets/ajo-b2b-paid-media-controller-canvas.svg" alt="AJO B2B Paid Media Controller Canvas" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

### Audience activation

1. **Activate to LinkedIn (and other destinations).**

   Use "Activate to Destination" in the journey to send each path to the right paid media audience. No manual list export or upload; the journey drives activation as accounts flow through paths.

2. **Monitor and tune.**

   Use journey reporting to monitor volumes per path.

## Summary

The **Paid Media Controller** blueprint shows how **AJO B2B and AEP** work together to give B2B marketers a single, automated way to assign accounts to campaigns and activate to paid media: one master audience, one journey, waterfall split logic, and direct activation to destinations—no manual list handoffs. It establishes a repeatable pattern for multichannel B2B paid media orchestration and helps reduce overlap, improve relevance, and scale operations.

## Related documentation

- [Buying Group-based Marketing and Journey Management blueprint](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/b2b-activation/b2b-buying-group-journeys) — Account and buying group journeys in AJO B2B.
- [Adobe Journey Optimizer B2B Edition](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b) — Product documentation.
- [Real-time Customer Data Platform B2B Edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) — Account audiences and activation.
