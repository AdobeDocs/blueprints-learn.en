---
title: Build an Audience
description: Learn how to use the Build Audience activity to target Basic plan members from a relational schema and verify the resulting row counts.
doc-type: article
solution: Experience Platform
exl-id: 7576e64b-d99a-4864-b877-f4ae77e1d7bd
---

# Build an Audience

## Objective

In the next set of steps you will build an audience from the relational schema by selecting the right Targeting dimension and setting the appropriate conditions. You will also use the refresh option to check the expected number of row counts.

## Build Audience

1. Once the campaign is rendered, click on the **+** within the canvas to open the options menu and then select **Build audience** from the **Targeting activities**

![Build Audience](assets/build-an-audience-5.png)

2. The **Build audience** activity opens the details pane on the right, click on the Search icon to select the **Targeting dimension**. 

![Select Targeting dimension](assets/build-an-audience-4.png)

3. Select `dep-rel: Customer Account` from the list and click on **Confirm**

![Select dep-rel: Customer Account schema](assets/build-an-audience-2.png)

4. Once the **Targeting dimension** is configured, click on Create audience to start the process of building the audience from the relational schema

![Create audience](assets/build-an-audience-9.png)

5. The Create audience details pane opens, click on **Add condition** 

![Add condition](assets/build-an-audience-3.png)

6. Scroll down and expand the `dep-rel: Plan Lookup` by clicking on the **>** next to it

![Expand Plan Lookup](assets/build-an-audience-8.png)

7.  Select `dep-rel: Plan Name` and click on **Confirm**

![Select Plan Name](assets/build-an-audience-6.png)

8. In the Custom condition panel, leave the operator as "equal to" and for Value, select Basic from the drop down.

![Plan Name equals Basic](assets/build-an-audience-7.png)

>[!NOTE]
>
>Notice that all the distinct values available for the selected column show up in the drop down, making it easy to create the custom conditions.



9. With the Custom condition configure, click on the Refresh icon to calculate and view the count. There are two locations to help with calculating the results

![Calculate expected row counts](assets/build-an-audience-10.png)

>[!NOTE]
>
>The Refresh operation evaluates the condition against the relational data and displays the expected results. This operation typically just takes a few seconds and is extremely useful for fine-tuning the criteria and ensuring it meets expectations. 



10. The counts (**38**) indicate the number of rows in the relational store that match the specified condition. Click on **Confirm** to exit the **Create audience** pane

![Confirm](assets/build-an-audience-1.png)

>[!NOTE]
>
>There are options under the Rule properties section to get more details. Click on **View results** to see the actual results returned. Use the **Code view** option to see the query being executed. 

## Recap

You have now seen how easy use the Build Audience activity in the campaign by choosing the right Target dimension from the relational schema. You then added a condition to  refine the audience building criteria and used the refresh option to check the expected number of rows. 

You can read more [here](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/design-campaigns/build-audience) if you are interested.
