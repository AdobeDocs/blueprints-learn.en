---
title: Read an Audience
description: Read an Audience
doc-type: article
exl-id: f825efe9-4349-4195-a017-c956c15df946
---

# Objective

In the next set of steps you will create a campaign to read an audience from AEP and use  it along with the Profile Target Dimension created earlier. Use the Split activity to split the data based on a condition. Finally test the campaign to understand how these audiences work when used with the Relational schema.

# Read Audience

This lab covers using the Read audience activity in conjunction with the Relational schema for enrichment.

Orchestrated Campaign uses the  Relational schema for all the activities. When using the Read audience activity, which reads the audience from AEP, a corresponding Entity (Target Dimension) should be configured to reconcile the audience with the Campaign Target Dimension. 

# Create a Campaign

1. In the left side rail, click on **Campaigns**

![Navigate to Campaigns](assets/VcJhv83IcbJLFOToqA4K--20251208-061706.png)

2. Click on **Create campaign**

![Create campaign](assets/XDzXpoJVQ8UAPUFjUIKcm-20251208-042622.png)

3. Select **Orchestration - Marketing**  and click on **Confirm**

![Select Orchestration - Marketing](assets/rXDETbHLsGn6XAwz5L6Xp-20251208-042621.png)

4. Provide Campaign details as follows and then click the **Save button**
   - Name: **OC-RSL-ReadAudience-Test**
   - Description: **RSL-Read Audience Test**

![Campaign settings](assets/N-T0yLrWhzPfXaExvYLcK-20251211-184647.png)

5. Wait for the confirmation message

![Campaign settings updated](assets/aSfx_-DKKZPW1wgMC0_Zl-20251212-181517.png)



# Add Read Audience Activity

1. Click on the **+** inside the canvas to open the options menu and then select **Read audience** from the **Targeting activities**

![Read Audience](assets/rxBhUmbXGsN4vDC4QDT01-20251211-184647.png)

2. In the **Read audienc**e details pane, click on the Search icon for **Audience**

![Specify audience](assets/ZYzdri3dPsQHa1FU_fGUG-20251211-184647.png)

3. Select the **dep: Basic Plan Members** audience with Profile Count of **9 **and click on **Add audience**

![Select dep: Basic Plan Members audience](assets/8WzDMKxQMfI-0mhWlGBby-20260111-021739.png)

4. Next click on the drop down for **Entity** and select the `dep-rel: Customer Account - customer_id` Campaign Target Dimension

![Specify Entity/Target Dimension](assets/MoSyNpSZbJ6B2nQjcZOAD-20260111-021739.png)

>[!NOTE]
>Other attributes can also be extracted from the AEP Profile for use in the canvas using the **Add attribute **button. But for this lab, extra attributes are not required, so that step is skipped.



# Test the Campaign

1. The settings for the **Read Audience** activity are filled in. Click on **Start** to run the campaign in **Test mode**

![Start campaign in Test mode](assets/6nvSWgpbZWkO6ylCuLuJ0-20260111-021739.png)

>[!NOTE]
>This will take a few minutes to run.
>
>Test mode permits the execution of the campaign to verify and monitor its behavior along with the results from each activity. The activities get executed sequentially through to the end of the canvas.



2. The test execution starts and the results are displayed when completed. Click on the **Result** node and then Preview results to see the execution results

![Review test results](assets/gc6VaOcFO60KOfdNFTqnn-20260111-021739.png)

3. Notice that **2** (out of 9) profiles from the **Read audience** do not have a corresponding matching **Target dimension** from the relational schema (i.e. they exist in the Profile store but not the relational store). And since Orchestrated Campaign works off the Relational schema, the unmatched `customer_id` (**2**) from the **Read audience** will be dropped and only the *matching* ones, **7** in this case, will be usable in subsequent activites that leverages **relational data** in the campaign

![Missing Target Dimension](assets/-34lyVsIDUh5u-hQXMYKe-20260111-021740.png)

>[!NOTE]
>In the following steps, we will attempt to use the relational data and confirm the above statement of unmatched `customer_id` getting dropped.

4. Click on **Stop** to stop the **Test mode** of the campaign

![Stop test mode](assets/lpF21653znspLOIi2h-OT-20260113-224440.png)

5. Click on the **+** at the end of the flow and add **Split** from the **Targeting activities**

![Add Split](assets/5JId8U2ATOcc4pVLaMWde-20260113-224440.png)

6. In the details pane of the **Split** activity, expand the first split called **Subset**

![Update default Split segment](assets/fJ8kVoyPdwlPkmjgXolwO-20260113-224440.png)

7. Rename it to "**In Store**" and click on **Create filter **to set the filter condition

![Rename segment](assets/RfxXwGBTbEp7m9PN314S6-20260113-224440.png)

8. In the **Create filte**r pane, click on **Add condition**

![Add condition](assets/KdcNHV9eIrVxI4EOOOlGo-20260113-224440.png)

9. Since no other attributes were extracted from the AEP Profile, the only AEP Profile attribute available here is the `Customer ID`. However, columns from the relational store corresponding to the matching Target dimension are available for setting up the filter condition. Expand the **Targeting dimension** by clicking on  **>**

![Expand Targeting dimension](assets/v0Fe28Hr-UUlEJongGSP5-20260113-224440.png)

9. Select `Source` from the list and click on **Confirm**

![Select Source attribute](assets/UhXX4RmL-JGLJ4KeAg5U_-20260113-224439.png)

10. The distinct values for the Source column are available in the drop down. For the **Custom condition**, select **"In Store"** from the drop down and click on **Confirm** to exit

![Set condition](assets/rfLivscSjlArYboT5lYGN-20260113-224439.png)

11. Back in the details pane of the **Split** activity, the settings for the first Split are complete. Click on **Add segment** to the second split

![Add new segment](assets/SLNPZ84iuhqBI668K90mx-20260113-224439.png)

A new segment with the name **Result** is created

![Choose Result segment](assets/8X1IlXHgC2cmIUoF1UPvv-20260113-224440.png)

13. Rename "**Result**" to "**Not In Store**" and click on **Create filter **to set the filter condition

![Rename segment and add filter](assets/BDnOcONic3uqSEENWIXha-20260113-224439.png)

14. In the **Create filter** pane, click on **Add condition**. Follow the same approach as above, expand the **Targeting dimension** by clicking on  **>** 

![Expand Targeting dimension](assets/v0Fe28Hr-UUlEJongGSP5-20260113-224440.png)

Select `Source` from the list and click on **Confirm**

![Select Source attribute](assets/UhXX4RmL-JGLJ4KeAg5U_-20260113-224439.png)

15. For the **Custom condition**, select **"In Store"** from the drop down and for the operator select "**not equal to**". Click on **Confirm** to exit

![Set condition](assets/SiIQddR0x9Aj-VXST7eTr-20260113-224439.png)

16. Back in the details pane of the **Split** activity, the settings for the two Splits are complete. Click on **Start** to run the campaign in **Test mode**

![Start campaign in Test mode](assets/wyv5nfguyrWFljlIdu44H-20260113-224439.png)

17. The test execution begins and the results are displayed upon completion. Since  only **7** matching Target dimension were found in the Relational schema, the same count is observed post the Split operations (**7** and **0**) as well

![Verify counts](assets/8EP-J_E_pggQ6-TQsV3j0-20260113-224439.png)

18. Click on each result box and **Preview results** to view the results

![Preview results](assets/ntBHuK_k8dpB3x34D5Nd--20260113-224439.png)

19. Click on **Stop** to stop the **Test mode** of the campaign

![Stop Test mode](assets/Su9dhiEtAk5Y6BCujBJp7-20260113-224438.png)

>[!NOTE]
>While the Read audience showed **9** profiles. Since we built a filter on Source and the Source field exists in the Relational store, we had to join from the Profile store to the Relational store to check it. When it was joined with the Relational schema, via the Campaign Target Dimension, only a total of **7** profiles matched. These **7** matched customer ids are available for use in the following activities that attempts to use relational data. All of the **7** customer ids had `Source` set to **"In Store"**, which was evident via the Split flows.
>
>Hence, maintaining data consistency is critical when using AEP Profiles along with their relational counterparts for enrichment.

>[!TIP]
>Congratulations, this completes the lab on using the Read Audience activity with Relational schema.

# Recap

You have now seen how easy it is to create a Campaign, perform a Read Audience activity along with the Profile Target Dimension to leverage the relational schema. You used the Split activity to split the audience based on a condition. Finally, the test mode helped understand that it is important to have the data consistency between the Profile and the Relational schema.

You can read more [here](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/design-campaigns/read-audience) if you are interested.
