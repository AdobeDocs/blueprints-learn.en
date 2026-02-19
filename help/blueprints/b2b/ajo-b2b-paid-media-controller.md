# Paid Media Controller Blueprint

## Overview

Marketing teams running B2B paid media at scale face a recurring
problem: **accounts end up in multiple campaigns at once** (persona,
category awareness, solution-led, pursuit), which dilutes messaging,
causes audience fatigue, and forces manual list work---uploads,
exclusions, and suppression---across LinkedIn Account Match (Account
Destination). Without **waterfall prioritization** and **automated
campaign assignment**, there is no single place to decide which account
gets which message, and operations do not scale.

The **Paid Media Controller** addresses this problem using **Adobe
Journey Optimizer B2B Edition (AJO B2B)** and **Adobe Experience
Platform (AEP)** together. One **account journey** reads a
qualified-account audience from Real-Time CDP, applies **split-path
(waterfall) logic** to assign each account to exactly one campaign tier,
and **activates each path directly** to paid media destinations (e.g.,
LinkedIn Matched Audiences)---with no manual list handoffs.

The outcome is precision control, less overlap, and a repeatable pattern
for multichannel B2B paid media orchestration.

------------------------------------------------------------------------

## Use Case: A Marketer's Story --- Why a Controller Matters

*Maya leads paid media for a global B2B brand. Her team runs dozens of
campaigns---foundational awareness, category intent (Journey, Data,
Content), solution-led programs, persona campaigns, and must-win
pursuits. She has a problem.*

### The Problem

The same accounts show up in multiple campaigns. A high-intent Journey
account is also in a broad awareness list; a pursuit account still gets
persona ads. List uploads and exclusions are manual. Every time sales
updates a "must-win" list or a new persona campaign launches, her team
re-exports audiences, reconciles overlaps in spreadsheets, and
re-uploads to LinkedIn and other platforms.

It's slow, error-prone, and doesn't scale.

### What She Wants

One place where every qualified account is evaluated once, assigned to
the *most relevant* campaign using clear priority rules (waterfall), and
sent to the right paid media destination---automatically.

No manual list handoffs.

When data or strategy changes, the system re-evaluates and moves
accounts between campaigns without her team touching lists.

### Adobe's Answer

With **AJO B2B and AEP working together**, Maya can run a single **Paid
Media Controller** journey:

-   AEP and Real-Time CDP hold the data and one master "qualified
    accounts" audience
-   AJO B2B runs an account journey
-   **Split-path logic (waterfall)** routes each account into the right
    tier:
    -   Targeted Pursuits\
    -   Solution-Led\
    -   Persona\
    -   Category Awareness\
    -   Foundational Awareness\
-   **Activate to Destination** sends each path to the correct LinkedIn
    (or other) campaign

One journey. One source of truth. No manual list exports.

------------------------------------------------------------------------

## Why It Matters for B2B Enterprises

Organizations that adopt this pattern can:

-   Eliminate manual suppression and exclusion logic\
-   Scale to tens of thousands of accounts\
-   Maintain a single source of truth for campaign assignment\
-   Automatically adapt as campaign focus and sales goals change\
-   Avoid re-exporting lists or re-uploading to each platform

### KPIs to Measure Success

-   **Awareness:** Are target accounts seeing the right ads and moving
    appropriately?\
-   **Engagement:** Are engagement and conversion rates better when
    overlap is removed?\
-   **Efficiency:** How much has manual list work decreased?\
-   **Cost:** How does cost per acquired account or opportunity change?

------------------------------------------------------------------------

## Architecture (High-Level Flow)

1.  **Data & Audiences**\
    AEP holds profiles and events. Real-Time CDP builds account
    audiences (e.g., "Paid Media Eligible Accounts").

2.  **Orchestration**\
    AJO B2B journey: Read audience → Split path (waterfall) → Activate
    to Destination.

3.  **Destinations**\
    LinkedIn Matched Audiences and other paid media platforms receive
    account-level activation.

------------------------------------------------------------------------

## Summary

The **Paid Media Controller** blueprint demonstrates how **AJO B2B and
AEP** provide a single, automated system for campaign assignment and
paid media activation:

-   One master audience\
-   One journey\
-   Waterfall split logic\
-   Direct activation to destinations\
-   No manual list handoffs

It establishes a scalable and repeatable model for multichannel B2B paid
media orchestration.
