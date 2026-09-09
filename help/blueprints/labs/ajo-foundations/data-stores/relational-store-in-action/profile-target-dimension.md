---
title: Profile Target Dimension
description: Learn how to label a relational schema field as an identity and create a Profile Target Dimension to join the Real-Time Customer Profile with the Relational Store.
doc-type: article
solution: Experience Platform
exl-id: bfc71051-e471-4d5c-a9a7-bb6805a5acb1
---

# Objective

In the next set of steps you will navigate the UI to view the Schema and setup the Identity. Next, you will setup the Profile Target Dimension, which is the entity type the campaign is targeting and reconciling with the AEP Profile for delivery.

## Why This is Important

The Profile Target Dimension is used to tell Adobe Journey Optimizer how data between the Real-Time Customer Profile and Relational Store can be joined. The ingredients of this configuration are as follows:

- A relational schema
- A single field from the relational schema
- An identity namespace associated to that field

>[!CAUTION]
>
>Without this configuration in place no reading or sharing of audiences can happen nor can any messages be sent out of Orchestrated Campaigns

## Label the Identity

1. Click on the **Apps** icon and select **Journey Optimizer**

![Navigate to Journey Optimizer](assets/profile-target-dimension-8.png)

2. Click on **Schemas** under the Data Management menu and make sure you have the **Browse** tab selected.
3. Search for the schema called `dep-rel: Customer Account`

![Search for schema dep-rel: Customer Account](assets/profile-target-dimension-9.png)

4. Open the schema by clicking on its name and then click on the field **customer\_id**

![Select schema field customer_id](assets/profile-target-dimension-2.png)

5. In the right rail locate the checkbox named **Identity**, **check the box** and choose the Identity namespace titled **customerID**

![Choose the identity namespace customerID](assets/profile-target-dimension-5.png)

6. Click the **Save** button to save your schema. A confirmation message will show up
7. Click on **Cancel** button or the **Schemas** in the left hand rail to exit the schema UI

>[!CAUTION]
>
>If you do not save the schema after adding the identity label the next set of configuration steps will not work

>[!NOTE]
>
>After Save, it takes a few minutes (under 5 mins), before it shows up on the Profile Target Dimension drop down in the next step.

## Create the Profile Target Dimension 

1. Click on **Configurations** under **Administration**

![Configurations](assets/profile-target-dimension-7.png)

2. Select **Profile Target Dimension** and click on **Manage**

![Profile Target Dimension](assets/profile-target-dimension-10.png)

3. The Profile Target Dimension pane opens, click on **Create**

![Create](assets/profile-target-dimension-4.png)

4. Select the schema `dep-rel: Customer Account` from the drop-down.

>[!NOTE]
>
>It might take a few minutes for the schema to appear in this screen after marking the identity. Refresh the page and repeat the previous two steps until the schema appears.

![Create Profile Target Dimension](assets/profile-target-dimension-3.png)

5. For the **Identity value** select `/customer_id`

![Select Identity value](assets/profile-target-dimension-1.png)

>[!NOTE]
>
>A relational schema can have many fields labeled with identities hence this being a list box.



6. Click the **Save** button to create the Profile Target Dimension. You should then see the record appear.

![Profile Target Dimension saved](assets/profile-target-dimension-6.png)

>[!NOTE]
>
>The name of the record created is a concatination of the schema name *(dep-rel: Customer Account)* and the field labeled with the identity *(customer\_id)*

>[!TIP]
>
>Congratulations! this concludes the Profile Target Dimension creation step in the lab.

## Recap

You have now seen how easy it is to navigate the Schema, mark an attribute as an Identity and create  the Profile Target Dimension.

You can read more [here](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/data-configuration/target-dimension) if you are interested.
