---
title: Browse schemas
description: Learn how to browse relational schemas and view entity relationship diagrams in Adobe Experience Platform to understand schema relationships used in campaigns.
doc-type: article
solution: Experience Platform
exl-id: ac0e6743-4a83-4a8b-9bc6-f012b636312e
---

# Browse schemas

## Objective

In the next set of steps you will navigate the UI to view the Schemas and their relationships.  This is important to familiarize with the schemas and relationships available when you are building your campaign.

## View schemas

The Connection 5G relational data model has already been built for you. You can see the schemas for yourself by navigating to the **Schemas -> Browse** page in the UI.

In the search box enter `dep-rel` to see all the schemas.

![Search results showing all dep-rel relational schemas](assets/browse-schemas-search-results.png)

>[!NOTE]
>
>Note the type of all the schemas is *Relational*



## View relationship diagram

With relational XDM schemas you can easily view the entity relationship diagram (ERD) by selecting any schema and clicking on the View relationship diagram button.  

Do the following:

1. Click on the **Relationships** tab and then click on the **View relationship diagram** button

![Relationships tab with the View relationship diagram button](assets/browse-schemas-relationships-tab.png)



2. Click **Select Schemas**
3. From the pop-up, select `dep-rel: Customer Account` and then click **Confirm**

![Select Schemas popup with dep-rel: Customer Account chosen](assets/browse-schemas-select-schema-popup.png)



4. On the ERD click the **3 dots** and select **Show related entities**

![Show related entities option in the ERD context menu](assets/browse-schemas-show-related-entities.png)



5. View the ERD with all tables directly related to dep-rel: Customer Account. Optionally you can download the ERD as a PNG file.

![Entity relationship diagram showing tables related to Customer Account](assets/browse-schemas-erd-diagram.png)

>[!TIP]
>
>Pretty cool eh?!

## Recap

You have now seen how easy it is to navigate the Schema and Relationships UI.  You can select a specific schema(s) and navigate to see the relationships to help understand and use the data in campaign orchestration.

You can read more [here](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/data-management/get-started-schemas) if you are interested.
