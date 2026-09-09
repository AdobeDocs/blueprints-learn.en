---
title: Decision Item XDM
description: Learn the pre-built XDM schema every decision item shares and how custom attributes are nested under a tenant namespace.
doc-type: article

solution: Experience Platform
exl-id: c42503a2-24e7-4a5d-98bf-38c16fe69733
---

# Decision Item XDM

## Learning Objective

By the end of this lesson, you will be able to:

- Identify the pre-built XDM schema used for every decision item
- Explain where custom attributes live within the schema and the cap that applies to them
- Recognize how nesting attributes under a parent object supports reuse

## Materials Needed

- pad of at least 12 sticky notes (more in case you make mistakes)

## Lecture

Partway through the video, you'll pause to write four attribute names across the top of your 12 sticky notes — you'll fill in the actual values in the next lesson.

>[!VIDEO](https://video.tv.adobe.com/v/3502206/)

## Key Takeaways

- Every decision item uses the same pre-built schema: personalized offer items – experience decisioning
- Everything under the \_experience node is system-required and cannot be edited
- Custom attributes live under your org's tenant namespace and are capped at 100 per schema
- There's only one schema for every decision item — no duplicates or alternate versions
