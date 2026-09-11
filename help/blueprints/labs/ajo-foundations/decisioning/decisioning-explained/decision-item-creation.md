---
hold: true
title: Decision item creation
description: Learn how decision item attributes differ from eligibility settings, plus the org-level guardrail on decision items and impressions versus decision events.
doc-type: article

solution: Experience Platform
exl-id: 28752ac1-118c-41d9-af6a-9907f854df1e
---

# Decision item creation

## Learning objective

By the end of this lesson, you will be able to:

- Differentiate a decision item's attributes from its eligibility settings
- State the guardrail on decision items per IMS org and why it's org-level, not sandbox-level
- Distinguish an impression from a decision event
- Differentiate decision rules from audiences by scope, timing, and the data each can access

## Materials needed

- 12 playing cards (Jack, Queen, King from each suit) 
- 12 sticky notes, with attribute names already written on them from previous lesson

## Lecture

This is the most hands-on lesson so far — you'll attach a sticky note to each card, then pause several times to write tier, capacity, display, camera, priority, and eligibility values as each concept is introduced.

>[!VIDEO](https://video.tv.adobe.com/v/3502207/)

## Key takeaways

- A decision item has two halves: attributes (name, description, custom attributes, tags, priority) and eligibility (dates, decision rule inclusion, audience inclusion, capping)
- A customer can have up to 10,000 decision items — that limit is per IMS org, not per sandbox
- Higher priority scores are returned first
- A decision rule is an if/true conditional scoped to a single campaign or journey, evaluated at decision time, and can use decision item attributes; an audience is a broader group of profiles, evaluated at batch/streaming/edge speed, and cannot access decision item attributes
- Use a decision rule instead of an audience when eligibility depends on the decision item's own attributes
- A decision item can carry more than one capping trigger (impressions, clicks, decision events, custom events) at once
- An impression counts when the item is actually viewed at the edge; a decision event counts every time decisioning evaluates and returns a response, seen or not
- Capping resets daily, weekly, or monthly at midnight GMT — not local time
