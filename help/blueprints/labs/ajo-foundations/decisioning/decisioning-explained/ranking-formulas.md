---
hold: true
title: Ranking formulas
description: Learn how ranking formulas dynamically adjust a decision item's priority score per profile using conditional math expressions.
doc-type: article

solution: Experience Platform
exl-id: 08183f1a-8db6-43c5-8b2e-05fa3d9c0f8d
---

# Ranking formulas

## Learning objective

By the end of this lesson, you will be able to:

- Define a ranking formula and explain what it adjusts
- Explain the if/then structure of a ranking formula rule
- Explain why every ranking formula setup requires a default formula
- Determine the outcome when two decision items land on the same adjusted priority score

## Materials needed

- 12 playing cards (Jack, Queen, King from each suit) 
- 12 sticky notes, filled with both attribute name and values from previous lessons

## Lecture

This lesson has several rounds of reordering your cards by hand — first by original priority, then by two different ranking formulas applied against different sample profiles — so you can see how the same set of items reshuffles depending on who's asking.

>[!VIDEO](https://video.tv.adobe.com/v/3502209/)

## Key takeaways

- A ranking formula dynamically adjusts a decision item's priority score on a per-profile basis, based on profile attributes or the triggering experience event
- Formulas support basic math (add, subtract, multiply, divide) and can reference the decision item's original priority score as a variable
- The rule logic: if a condition about the profile or hit is true, adjust the priority for decision items that meet certain item criteria
- Every ranking formula setup needs a default formula for decision items that no adjustment rule touches
- When two decision items land on the same adjusted priority score, decisioning orders them at random
