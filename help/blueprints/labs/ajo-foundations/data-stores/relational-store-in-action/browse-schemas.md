---
title: Browse Schemas
description: Browse Schemas
doc-type: article
solution: Experience Platform
exl-id: ac0e6743-4a83-4a8b-9bc6-f012b636312e
---

# Objective

In the next set of steps you will navigate the UI to view the Schemas and their relationships.  This is important to familiarize with the schemas and relationships available when you are building your campaign.

## View Schemas

The Connection 5G relational data model has already been built for you. You can see the schemas for yourself by navigating to the **Schemas -> Browse** page in the UI.

In the search box enter `dep-rel` to see all the schemas.

![Relational Schemas](assets/browse-schemas-5.png)

>[!NOTE]
>
>Note the type of all the schemas is *Relational*



## View Relationships Diagram

With relational XDM schemas you can easily view the entity relationship diagram (ERD) by seleting any schema and clicking on the View relationalships digram button.  

Do the following:

1. Click on the **Relationships **tab and then click on the **View relationship diagram** button

![View relationships diagram](assets/browse-schemas-3.png)



1. Click **Select Schemas**
1. From the pop-up, select `dep-rel: Customer Account` and then click **Confirm**

![Select dep-rel: Customer Account schema](assets/browse-schemas-1.png)



1. On the ERD click the **3 dots** and select **Show related entities**

![Show related entities](assets/browse-schemas-2.png)



1. View the ERD with all tables directly related to dep-rel: Customer Account. Optionally you can download the ERD as a PNG file.

![View ERD diagram](assets/browse-schemas-4.png)

>[!TIP]
>
>Pretty cool eh?!

## Recap

You have now seen how easy it is to navigate the Schema and Relationships UI.  You can select a specific schema(s) and navigate to see the relationships to help understand and use the data in campaign orchestration.

You can read more [here](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/data-management/get-started-schemas) if you are interested.
