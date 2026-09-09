---
title: Decision Item Creation
description: Learn how decision item attributes differ from eligibility settings, plus the org-level guardrail on decision items and impressions versus decision events.
doc-type: article

solution: Experience Platform
exl-id: 28752ac1-118c-41d9-af6a-9907f854df1e
---

# Decision Item Creation

## Learning Objective

By the end of this lesson, you will be able to:

- Differentiate a decision item's attributes from its eligibility settings
- State the guardrail on decision items per IMS org and why it's org-level, not sandbox-level
- Distinguish an impression from a decision event
- Differentiate decision rules from audiences by scope, timing, and the data each can access

## Materials Needed

- 12 playing cards (Jack, Queen, King from each suit) 
- 12 sticky notes, with attribute names already written on them from previous lesson

## Lecture

This is the most hands-on lesson so far — you'll attach a sticky note to each card, then pause several times to write tier, capacity, display, camera, priority, and eligibility values as each concept is introduced.

>[!VIDEO](https://video.tv.adobe.com/v/3502207/)

## Key Takeaways

- Every decision item uses the same pre-built schema: personalized offer items – experience decisioning
- Everything under the \_experience node is system-required and cannot be edited
- Custom attributes live under your org's tenant namespace and are capped at 100 per schema
- There's only one schema for every decision item — no duplicates or alternate versions
