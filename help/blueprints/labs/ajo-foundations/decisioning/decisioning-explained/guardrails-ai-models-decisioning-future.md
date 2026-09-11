---
hold: true
title: Guardrails, AI Models, and the future of Decisioning
description: Learn the key decisioning guardrails, how AI ranking models differ from formulas, and how decisioning's building blocks connect end to end.
doc-type: article

solution: Experience Platform
exl-id: 90902f6e-ba3c-4852-ab82-ad852698b227
---

# Guardrails, AI Models, and the future of Decisioning

## Learning objective

By the end of this lesson, you will be able to:

- Recall the two guardrails most commonly encountered in practice
- Differentiate auto-optimization from personalized optimization AI models
- Explain how decisioning extends beyond the legacy ODE product
- Summarize how the eight building blocks fit together end to end

## Lecture

The below video covers the two most common decisioning guardrails, how AI ranking models differ from manual ranking formulas, how decisioning extends beyond the legacy Offer Decisioning Engine, and a recap of how the eight building blocks connect end to end.

>[!VIDEO](https://video.tv.adobe.com/v/3502212/)

## Key takeaways

- The two most commonly hit guardrails: 10,000 decision items per IMS org (not per sandbox), and 100 custom attributes per schema; check product documentation for current numbers, as these are subject to change
- AI models can be used within ranking formulas; auto-optimization is non-personalized and optimizes on global performance, while personalized optimization serves items toward specific business goals per profile
- Model scores computed outside AEP can be brought in as profile attributes and used in eligibility rules or ranking formulas
- Decisioning goes beyond the legacy Offer Decisioning Engine: it uses XDM for reusability, delivers JSON to headless applications, and separates the decision item from the treatment
- Decisioning can condition journey pathing and entry priority on a decisioning response
- End to end: decision item XDM defines attributes → decision item creation assigns values and eligibility → collections group items → ranking formulas adjust priority per profile → selection strategies rank and filter a collection → decision policies apply strategies to a channel → decision packages live on the hub or edge
