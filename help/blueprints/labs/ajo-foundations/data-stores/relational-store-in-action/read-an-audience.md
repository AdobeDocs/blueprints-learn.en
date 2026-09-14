---
title: Read an audience
description: Learn how to use the Read Audience activity with a Profile Target Dimension in an Orchestrated Campaign and test how unmatched profiles are dropped when reconciling relational data.
doc-type: article
solution: Experience Platform
exl-id: f825efe9-4349-4195-a017-c956c15df946
---

# Read an audience

## Objective

In the next set of steps you will create a campaign to read an audience from AEP and use it along with the Profile Target Dimension created earlier. Use the Split activity to split the data based on a condition. Finally test the campaign to understand how these audiences work when used with the Relational schema.

## Read audience

This lab covers using the Read audience activity in conjunction with the Relational schema for enrichment.

Orchestrated Campaign uses the Relational schema for all the activities. When using the Read audience activity, which reads the audience from AEP, a corresponding Entity (Target Dimension) should be configured to reconcile the audience with the Campaign Target Dimension. 

## Create a campaign

1. In the left side rail, click on **Campaigns**

   ![Left rail navigation to Campaigns](assets/read-an-audience-navigate-to-campaigns.png)

2. Click on **Create campaign**

   ![Create campaign button](assets/read-an-audience-create-campaign-button.png)

3. Select **Orchestration - Marketing**  and click on **Confirm**

   ![Orchestration - Marketing campaign type selection](assets/read-an-audience-select-orchestration-marketing.png)

4. Provide Campaign details as follows and then click the **Save button**
   - Name: **OC-RSL-ReadAudience-Test**
   - Description: **RSL-Read Audience Test**

   ![Campaign settings form with name and description fields](assets/read-an-audience-campaign-settings-form.png)

5. Wait for the confirmation message

![Confirmation message after saving campaign settings](assets/read-an-audience-campaign-settings-confirmation.png)



## Add Read audience activity

1. Click on the **+** inside the canvas to open the options menu and then select **Read audience** from the **Targeting activities**

   ![Targeting activities menu with Read audience selected](assets/read-an-audience-add-read-audience-activity.png)

2. In the **Read audience** details pane, click on the Search icon for **Audience**

   ![Read audience details pane with the Audience search icon](assets/read-an-audience-search-audience-icon.png)

3. Select the **dep: Basic Plan Members** audience with Profile Count of **9** and click on **Add audience**

   ![dep: Basic Plan Members audience selected with Profile Count of 9](assets/read-an-audience-select-basic-plan-members-audience.png)

4. Next click on the drop down for **Entity** and select the `dep-rel: Customer Account - customer_id` Campaign Target Dimension

![Entity drop-down with the Customer Account Target Dimension selected](assets/read-an-audience-select-entity-target-dimension.png)

>[!NOTE]
>
>Other attributes can also be extracted from the AEP Profile for use in the canvas using the **Add attribute** button. But for this lab, extra attributes are not required, so that step is skipped.



## Test the campaign

1. The settings for the **Read Audience** activity are filled in. Click on **Start** to run the campaign in **Test mode**

   ![Start button to run the campaign in Test mode](assets/read-an-audience-start-test-mode.png)

   >[!NOTE]
   >
   >This takes a few minutes to run.
   >
   >Test mode permits the execution of the campaign to verify and monitor its behavior along with the results from each activity. The activities get executed sequentially through to the end of the canvas.



2. The test execution starts and the results are displayed when completed. Click on the **Result** node and then Preview results to see the execution results

   ![Result node with the Preview results option](assets/read-an-audience-preview-test-results.png)

3. Notice that **2** (out of 9) profiles from the **Read audience** do not have a corresponding matching **Target dimension** from the relational schema (i.e. they exist in the Profile store but not the relational store). And since Orchestrated Campaign works off the Relational schema, the unmatched `customer_id` (**2**) from the **Read audience** is dropped and only the *matching* ones, **7** in this case, are usable in subsequent activities that leverage **relational data** in the campaign

   ![Preview results showing profiles missing a matching Target Dimension](assets/read-an-audience-missing-target-dimension.png)

   >[!NOTE]
   >
   >The following steps use the relational data to confirm the above statement of unmatched `customer_id` getting dropped.

4. Click on **Stop** to stop the **Test mode** of the campaign

   ![Stop button to end campaign Test mode](assets/read-an-audience-stop-test-mode.png)

5. Click on the **+** at the end of the flow and add **Split** from the **Targeting activities**

   ![Targeting activities menu with Split selected](assets/read-an-audience-add-split-activity.png)

6. In the details pane of the **Split** activity, expand the first split called **Subset**

   ![Split activity details pane with the Subset segment expanded](assets/read-an-audience-expand-subset-split.png)

7. Rename it to "**In Store**" and click on **Create filter** to set the filter condition

   ![Segment renamed to In Store with the Create filter option](assets/read-an-audience-rename-in-store-segment.png)

8. In the **Create filte**r pane, click on **Add condition**

   ![Create filter pane with the Add condition button](assets/read-an-audience-add-condition-button.png)

9. Since no other attributes were extracted from the AEP Profile, the only AEP Profile attribute available here is the `Customer ID`. However, columns from the relational store corresponding to the matching Target dimension are available for setting up the filter condition. Expand the **Targeting dimension** by clicking on  **>**

   ![Targeting dimension expanded to show relational store columns](assets/read-an-audience-expand-targeting-dimension.png)

10. Select `Source` from the list and click on **Confirm**

   ![Source attribute selected from the Targeting dimension columns](assets/read-an-audience-select-source-attribute.png)

11. The distinct values for the Source column are available in the drop down. For the **Custom condition**, select **"In Store"** from the drop down and click on **Confirm** to exit

   ![Custom condition set to In Store](assets/read-an-audience-set-in-store-condition.png)

12. Back in the details pane of the **Split** activity, the settings for the first Split are complete. Click on **Add segment** to the second split

   ![Add segment button in the Split activity details pane](assets/read-an-audience-add-segment-button.png)

   A new segment with the name **Result** is created

   ![New segment named Result](assets/read-an-audience-new-result-segment.png)

13. Rename "**Result**" to "**Not In Store**" and click on **Create filter** to set the filter condition

   ![Segment renamed to Not In Store with the filter option](assets/read-an-audience-rename-not-in-store-segment.png)

14. In the **Create filter** pane, click on **Add condition**. Follow the same approach as above, expand the **Targeting dimension** by clicking on **>**, then select `Source` from the list and click on **Confirm**

   ![Targeting dimension expanded to show relational store columns](assets/read-an-audience-expand-targeting-dimension.png)

   ![Source attribute selected from the Targeting dimension columns](assets/read-an-audience-select-source-attribute.png)

15. For the **Custom condition**, select **"In Store"** from the drop down and for the operator select "**not equal to**". Click on **Confirm** to exit

   ![Custom condition set to not equal to In Store](assets/read-an-audience-set-not-in-store-condition.png)

16. Back in the details pane of the **Split** activity, the settings for the two Splits are complete. Click on **Start** to run the campaign in **Test mode**

   ![Start button to run the campaign in Test mode after configuring the Split](assets/read-an-audience-start-test-mode-second-run.png)

17. The test execution begins and the results are displayed upon completion. Since  only **7** matching Target dimension were found in the Relational schema, the same count is observed post the Split operations (**7** and **0**) as well

   ![Split activity results showing counts of 7 and 0](assets/read-an-audience-verify-split-counts.png)

18. Click on each result box and **Preview results** to view the results

   ![Preview results option for each Split result box](assets/read-an-audience-preview-split-results.png)

19. Click on **Stop** to stop the **Test mode** of the campaign

![Stop button to end the final Test mode run](assets/read-an-audience-stop-test-mode-final.png)

>[!NOTE]
>
>The Read audience showed **9** profiles. Because you built a filter on Source, and the Source field exists in the Relational store, you had to join the Profile store with the Relational store to check it. When joined with the Relational schema via the Campaign Target Dimension, only a total of **7** profiles matched. These **7** matched customer ids are available for use in the following activities that attempt to use relational data. All of the **7** customer ids had `Source` set to **"In Store"**, which was evident via the Split flows.
>
>Hence, maintaining data consistency is critical when using AEP Profiles along with their relational counterparts for enrichment.

>[!SUCCESS]
>
>Congratulations, this completes the lab on using the Read Audience activity with Relational schema.

## Recap

You have now seen how easy it is to create a Campaign, perform a Read Audience activity along with the Profile Target Dimension to use the relational schema. You used the Split activity to split the audience based on a condition. Finally, the test mode helped understand that it is important to have the data consistency between the Profile and the Relational schema.

You can read more [here](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/design-campaigns/read-audience) if you are interested.
