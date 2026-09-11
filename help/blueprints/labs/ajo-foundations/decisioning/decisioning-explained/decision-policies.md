---
hold: true
title: Decision policies
description: Learn how decision policies apply selection strategies to a delivery channel and how individual versus grouped combination methods change offer order.
doc-type: article

solution: Experience Platform
exl-id: 21dc67fd-76ac-4b82-ae78-be024c7bfc55
---

# Decision policies

## Learning objective

By the end of this lesson, you will be able to:

- Explain what a decision policy configures and where it's applied
- Define a decision package and what it comprises
- Differentiate the individual and grouped methods of combining multiple selection strategies
- Explain how frequency capping interacts with the number of decision items a policy returns

## Materials needed

- 12 playing cards (Jack, Queen, King from each suit) 
- 13 sticky notes
  - 12 filled with both attribute name and values from previous lessons
  - One new sticky note to track the requests

## Lecture

This is the longest and most involved simulate in the course. You'll simulate live decision policy behavior — making repeated "requests," tracking impressions against frequency caps, and watching cards drop out and get replaced — then apply everything to a real business scenario comparing individual vs. grouped selection strategy combination.

>[!VIDEO](https://video.tv.adobe.com/v/3502211/)

## Key takeaways

- A decision policy applies selection strategies to an actual AJO delivery channel, configured on a channel node in a journey or a campaign's channel section
- A policy can use none, one, or many selection strategies; with none, it returns items by original priority score, filtered by item-level eligibility
- A decision policy plus its delivery channel together are called a decision package — the configuration that lives on the hub or edge
- With individual combination, each strategy's collection is ordered separately, then the lists are stacked; with grouped, all items are ordered together into one list and duplicates use the higher of their two scores
- The same inputs can produce dramatically different final orders depending on individual vs. grouped
- Frequency capping directly limits how many items are available to return, so plan enough uncapped fallback items to fill every slot
