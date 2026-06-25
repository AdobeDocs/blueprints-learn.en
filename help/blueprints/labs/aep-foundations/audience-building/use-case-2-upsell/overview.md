---
title: Use Case #2 - Upsell
description: Use Case #2 - Upsell
doc-type: overview-page
exl-id: d0268de8-87eb-4dd9-b699-99d42716f20c
---

# Overview

<iframe title="Adobe Video Publishing Cloud Player" width="640" height="360" src="https://video.tv.adobe.com/v/3459487/" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen scrolling="no"></iframe>



**Use Case Definition**

Find all customers who have a total billing data usage in the last 6 months >140GB, a rolling 6 month avg. monthly data usage of >=20GB and they do not have an ultimate phone plan. 

Activate into Facebook / Google and Direct Mail channels. 

Direct Mail Personalization fields:

- First Name → used for greeting
- Mailing Address → used for mailing
- Plan Name → used for mailing statement (e.g. "Eric, upgrade to an ultimate plan today!")



# Analysis Tasks

Analyze the above and write down:

1. What fields you think are needed to address this use case?
2. Does the evaluation method need to be Streaming?
3. What do we need to keep in mind with Billing data?
4. What other information would you like to know? 

Remember: When we get requirements from the business stakeholders, they tend to be incomplete, use another terminology, and make assumptions without knowing it. It is your job to bring as much of that to the surface and guide them to something that can be done. 



# Approach

For this use case we are going to evaluate two options:

- Option #1 (Use Audience to Aggregate) 
  - This will have the Audience do the aggregation
    - Billing data usage Sum >140GB (last 6 months)
    - Billing data usage Avg >20GB (last 6 months)
    - Billing Data Usage High But No Ultimate Plan
- Option #2 (Use Pre-Aggregates)
  - This will utilize aggregation that was done before putting the data on Profile
    - Billing Data Usage High But No Ultimate Plan (Agg)

