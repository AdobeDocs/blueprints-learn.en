---
hold: true
title: Use Case #1 - Acquisition
description: Use Case #1 - Acquisition
doc-type: overview-page

solution: Experience Platform
exl-id: a85b1eb1-88f4-41b2-acce-2e34dbe6aff8
---

# Overview

>[!VIDEO](https://video.tv.adobe.com/v/3459402/?quality=12&learn=on)



**Use Case Definition**

Activate all profiles who have visited an iPhone 14 product page and no order exists for an iPhone 14 or do not have an active iPhone 14.



## Analysis Tasks

Analyze the above and write down:

1. What fields you think are needed to address this use case?
1. Does the evaluation method need to be Streaming?
1. What are the ramifications of Streaming when Events being used in the Audience come in at different times?
1. How do we know what “active” means?
1. What other information would you like to know? 

**Remember**: When we get requirements from the business stakeholders, they tend to be incomplete, use another terminology and make assumptions without knowing it. It is your job to bring as much of that to the surface and guide them to something that can be done. 



## Approach

For this use case we are going to break it down into multiple Audiences:

1. No Order exists iPhone/Pixel
1. No Active iPhone/Pixel
1. Visited iPhone/Pixel & No Order exists iPhone/Pixel & No Active iPhone/Pixel

