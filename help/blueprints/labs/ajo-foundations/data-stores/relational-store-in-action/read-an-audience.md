---
title: Read an Audience
description: Learn how to use the Read Audience activity with a Profile Target Dimension in an Orchestrated Campaign and test how unmatched profiles are dropped when reconciling relational data.
doc-type: article
solution: Experience Platform
exl-id: f825efe9-4349-4195-a017-c956c15df946
---

# Read an Audience

## Objective

In the next set of steps you will create a campaign to read an audience from AEP and use  it along with the Profile Target Dimension created earlier. Use the Split activity to split the data based on a condition. Finally test the campaign to understand how these audiences work when used with the Relational schema.

## Read Audience

This lab covers using the Read audience activity in conjunction with the Relational schema for enrichment.

Orchestrated Campaign uses the  Relational schema for all the activities. When using the Read audience activity, which reads the audience from AEP, a corresponding Entity (Target Dimension) should be configured to reconcile the audience with the Campaign Target Dimension. 

## Create a Campaign

1. In the left side rail, click on **Campaigns**

![Navigate to Campaigns](assets/read-an-audience-16.png)

2. Click on **Create campaign**

![Create campaign](assets/read-an-audience-17.png)

3. Select **Orchestration - Marketing**  and click on **Confirm**

![Select Orchestration - Marketing](assets/read-an-audience-24.png)

4. Provide Campaign details as follows and then click the **Save button**
   - Name: **OC-RSL-ReadAudience-Test**
   - Description: **RSL-Read Audience Test**

![Campaign settings](assets/read-an-audience-10.png)

5. Wait for the confirmation message

![Campaign settings updated](assets/read-an-audience-19.png)



## Add Read Audience Activity

1. Click on the **+** inside the canvas to open the options menu and then select **Read audience** from the **Targeting activities**

![Read Audience](assets/read-an-audience-26.png)

2. In the **Read audienc**e details pane, click on the Search icon for **Audience**

![Specify audience](assets/read-an-audience-18.png)

3. Select the **dep: Basic Plan Members** audience with Profile Count of **9** and click on **Add audience**

![Select dep: Basic Plan Members audience](assets/read-an-audience-5.png)

4. Next click on the drop down for **Entity** and select the `dep-rel: Customer Account - customer_id` Campaign Target Dimension

![Specify Entity/Target Dimension](assets/read-an-audience-9.png)

>[!NOTE]
>
>Other attributes can also be extracted from the AEP Profile for use in the canvas using the **Add attribute** button. But for this lab, extra attributes are not required, so that step is skipped.



## Test the Campaign

1. The settings for the **Read Audience** activity are filled in. Click on **Start** to run the campaign in **Test mode**

![Start campaign in Test mode](assets/read-an-audience-3.png)

>[!NOTE]
>
>This will take a few minutes to run.
>
>Test mode permits the execution of the campaign to verify and monitor its behavior along with the results from each activity. The activities get executed sequentially through to the end of the canvas.



2. The test execution starts and the results are displayed when completed. Click on the **Result** node and then Preview results to see the execution results

![Review test results](assets/read-an-audience-21.png)

3. Notice that **2** (out of 9) profiles from the **Read audience** do not have a corresponding matching **Target dimension** from the relational schema (i.e. they exist in the Profile store but not the relational store). And since Orchestrated Campaign works off the Relational schema, the unmatched `customer_id` (**2**) from the **Read audience** will be dropped and only the *matching* ones, **7** in this case, will be usable in subsequent activites that leverages **relational data** in the campaign

![Missing Target Dimension](assets/read-an-audience-1.png)

>[!NOTE]
>
>In the following steps, we will attempt to use the relational data and confirm the above statement of unmatched `customer_id` getting dropped.

4. Click on **Stop** to stop the **Test mode** of the campaign

![Stop test mode](assets/read-an-audience-22.png)

5. Click on the **+** at the end of the flow and add **Split** from the **Targeting activities**

![Add Split](assets/read-an-audience-2.png)

6. In the details pane of the **Split** activity, expand the first split called **Subset**

![Update default Split segment](assets/read-an-audience-20.png)

7. Rename it to "**In Store**" and click on **Create filter** to set the filter condition

![Rename segment](assets/read-an-audience-11.png)

8. In the **Create filte**r pane, click on **Add condition**

![Add condition](assets/read-an-audience-8.png)

9. Since no other attributes were extracted from the AEP Profile, the only AEP Profile attribute available here is the `Customer ID`. However, columns from the relational store corresponding to the matching Target dimension are available for setting up the filter condition. Expand the **Targeting dimension** by clicking on  **>**

![Expand Targeting dimension](assets/read-an-audience-27.png)

10. Select `Source` from the list and click on **Confirm**

![Select Source attribute](assets/read-an-audience-15.png)

11. The distinct values for the Source column are available in the drop down. For the **Custom condition**, select **"In Store"** from the drop down and click on **Confirm** to exit

![Set condition](assets/read-an-audience-25.png)

12. Back in the details pane of the **Split** activity, the settings for the first Split are complete. Click on **Add segment** to the second split

![Add new segment](assets/read-an-audience-12.png)

A new segment with the name **Result** is created

![Choose Result segment](assets/read-an-audience-6.png)

13. Rename "**Result**" to "**Not In Store**" and click on **Create filter** to set the filter condition

![Rename segment and add filter](assets/read-an-audience-7.png)

14. In the **Create filter** pane, click on **Add condition**. Follow the same approach as above, expand the **Targeting dimension** by clicking on  **>** 

![Expand Targeting dimension](assets/read-an-audience-27.png)

Select `Source` from the list and click on **Confirm**

![Select Source attribute](assets/read-an-audience-15.png)

15. For the **Custom condition**, select **"In Store"** from the drop down and for the operator select "**not equal to**". Click on **Confirm** to exit

![Set condition](assets/read-an-audience-13.png)

16. Back in the details pane of the **Split** activity, the settings for the two Splits are complete. Click on **Start** to run the campaign in **Test mode**

![Start campaign in Test mode](assets/read-an-audience-28.png)

17. The test execution begins and the results are displayed upon completion. Since  only **7** matching Target dimension were found in the Relational schema, the same count is observed post the Split operations (**7** and **0**) as well

![Verify counts](assets/read-an-audience-4.png)

18. Click on each result box and **Preview results** to view the results

![Preview results](assets/read-an-audience-23.png)

19. Click on **Stop** to stop the **Test mode** of the campaign

![Stop Test mode](assets/read-an-audience-14.png)

>[!NOTE]
>
>While the Read audience showed **9** profiles. Since we built a filter on Source and the Source field exists in the Relational store, we had to join from the Profile store to the Relational store to check it. When it was joined with the Relational schema, via the Campaign Target Dimension, only a total of **7** profiles matched. These **7** matched customer ids are available for use in the following activities that attempts to use relational data. All of the **7** customer ids had `Source` set to **"In Store"**, which was evident via the Split flows.
>
>Hence, maintaining data consistency is critical when using AEP Profiles along with their relational counterparts for enrichment.

>[!TIP]
>
>Congratulations, this completes the lab on using the Read Audience activity with Relational schema.

## Recap

You have now seen how easy it is to create a Campaign, perform a Read Audience activity along with the Profile Target Dimension to leverage the relational schema. You used the Split activity to split the audience based on a condition. Finally, the test mode helped understand that it is important to have the data consistency between the Profile and the Relational schema.

You can read more [here](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/design-campaigns/read-audience) if you are interested.
