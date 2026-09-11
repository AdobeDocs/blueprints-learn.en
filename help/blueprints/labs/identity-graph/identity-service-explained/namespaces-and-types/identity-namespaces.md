---
title: Identity Namespaces
description: Learn how identity namespaces pair with identity values to distinguish and properly process identities within the Identity Graph.
doc-type: article
solution: Experience Platform
exl-id: 74b3e855-fd2d-496b-b7b6-5b11daa2fa5a
---

# Data vs. Identities

If you look at the graphic, you see two rows and two columns of data. Assume for the moment that each row represents a single profile containing two identities.

If you were asked to identify which column contains CRM identities vs. Loyalty identities how would you do this? Would you assume that values starting with C mean CRM and those starting with L mean Loyalty? Do you want to assume the identities of a person?

![EuinytR8HbLOW7GYeYwAP 20260312 211035](assets/euinytR8HbLOW7GYeYwAP-20260312-211035.png)



## Introducing Identity Namespaces! 

A fully qualified identity in Identity Service includes both an identity namespace and identity value. 

Simply put, an identity namespaces provides additional context about the identity value to ensure its properly distinguished from other identities at the time of processing into the Identity Graph.

![PQEuUvPWbF  20260312 211034](assets/dwc1fel1J_PQEuUvPWbF--20260312-211034.png)

