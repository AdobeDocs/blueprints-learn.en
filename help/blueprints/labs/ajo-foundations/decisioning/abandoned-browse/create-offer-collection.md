---
title: Create Offer Collection
description: Create Offer Collection
doc-type: article
solution: Experience Platform
exl-id: 0a54f4dc-2112-474a-8383-9dd1497c3c74
---

# Objective

Now that your offers have been created, they need to be organized into a collection. A collection has one or more offer items, and an offer item can be in more than one collection. 

## Create the iPhone Offer Collection

1. If necessary, expand **Decisioning** in the left rail, then click **Catalogs**. You will see the four offers you created in the previous section.
1. Click on **Collections** just left of the offer name

![Navigate to Collections](assets/create-offer-collection-3.png)

1. Click the blue **Create collection** to create the new collection.
1. Name the collection **iPhone 17 Collection**
1. In the 'Collection rules' section, click on the text box that contains the text ***Click to create a decision item. ***Once clicked on, the options for creating the rule will appear.

![Initial collection validation](assets/create-offer-collection-2.png)

1. Click the **Select attrib****ute **button, then navigate through the offer item schema by clicking on **Device > Make**. Click **Save, **and you'll see that the 'Make' attribute is now in the decision rule.

![Select attribute demonstration](assets/create-offer-collection-4.png)

>[!NOTE]
>
>Notice that the options available to you are the same configurable fields you used when creating the offer items. Since a collection is a grouping of offer items, it makes sense that the rules to group them depend on their attributes. 

1. Leave the 'Equals' operator in place and enter the text **iPhone** in the value field, and you should see that the number of items changes to 4, indicating that all of your offer items meet that criteria

![Verify 4 offers are in the collection](assets/create-offer-collection-1.png)

>[!NOTE]
>
>You can also click the **Preview Collection** button and see the offer items that meet the criteria.

1. With all four of the offer items selected, click the blue **Create** button, and you'll be taken to a page that shows your newly created collection.

![Complete Collection validation](assets/create-offer-collection-5.png)

>[!NOTE]
>
>A collection is more than just a means of organization. In the steps ahead, you'll see that in Decisioning, we apply selection logic to a collection of offers. Thinking about an enterprise-sized implementation, it's not hard to picture how many offers would be created over the years of use. In order to determine which offers a selection strategy should apply to brings to light just how important proper collection management is. 
>
>In this case, a collection with just "iPhone" as the criteria would bring in too many offers after a few years of iPhone releases. We could have used additional criteria like 'Make equals 17' or used AEP Tags to tag offers for a specific campaign. But for simplicity, we're using this simple logic to create a collection.

## Recap

You have now created an offer collection that groups together the offer items you previously built. You added all the iPhone 17 offers into a collection and defined a rule based on offer attributes (like device make) so that only relevant offers belong to this collection.
