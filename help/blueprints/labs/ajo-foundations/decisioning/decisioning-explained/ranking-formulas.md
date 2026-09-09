---
title: Ranking Formulas
description: Learn how ranking formulas dynamically adjust a decision item's priority score per profile using conditional math expressions.
doc-type: article

solution: Experience Platform
exl-id: 08183f1a-8db6-43c5-8b2e-05fa3d9c0f8d
---

# Ranking Formulas

## Learning Objective

By the end of this lesson, you will be able to:

- A collection is a group of decision items that share a relationship — a campaign, similar features, or any other connection
- Decision items can be grouped by any attribute or by metadata tags, using logical operators (and/or) that depend on the attribute's data type
- A collection can have up to 500 decision items
- A single decision item can belong to more than one collection at once

## Materials Needed

- 12 playing cards (Jack, Queen, King from each suit) 
- 12 sticky notes, filled with both attribute name and values from previous lessons

## Lecture

This lesson has several rounds of reordering your cards by hand — first by original priority, then by two different ranking formulas applied against different sample profiles — so you can see how the same set of items reshuffles depending on who's asking.

>[!VIDEO](https://video.tv.adobe.com/v/3502209/)

## Key Takeaways

- A ranking formula dynamically adjusts a decision item's priority score on a per-profile basis, based on profile attributes or the triggering experience event
- Formulas support basic math (add, subtract, multiply, divide) and can reference the decision item's original priority score as a variable
- The rule logic: if a condition about the profile or hit is true, adjust the priority for decision items that meet certain item criteria
- Every ranking formula setup needs a default formula for decision items that no adjustment rule touches
- When two decision items land on the same adjusted priority score, decisioning orders them at random
