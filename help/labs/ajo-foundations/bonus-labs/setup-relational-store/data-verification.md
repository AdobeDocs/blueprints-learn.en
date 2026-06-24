---
title: Data Verification
description: Data Verification
doc-type: article
exl-id: 77226236-7caa-4ebd-9ab9-59ef1662f5fc
---

This lab will cover validation and verification of data ingested in the previous section.

>[!WARNING]
>After data has been ingested into the dataset, it takes about 15 minutes for data to be synced to the relational store. 

# 1 - Verification of data in datalake

1. In the AEP UI, navigate to Datasets on the left rail

![](assets/Mpu1uVf0sZxtw9BIc1ZFJ-20251205-184336.png)

2. Search for `oc_mdl_customer` in the search box and click on the dataset

![](assets/-btk3hkCZVkIQgnGLAryb-20251205-184602.png)

3. View the dataset details providing details on the records and time ingested. Click on **Preview dataset**

![](assets/dhV8bSPCNWHaMsB-Hu0k8-20251205-184336.png)

4. A preview of the data ingested into this dataset is shown along with the fields in the left pane

![](assets/xn2U1P3V5rIBokslS6QMx-20251205-184336.png)

>[!TIP]
>The local file loaded in the previous lab has been successfully ingested into the dataset and resides in the datalake.

>[!WARNING]
>It takes about 15 minutes for data to be synced to the relational store. The next section will cover data verification in the relational store.

# 2 - Verification of data in relational store

1. Click on the **Apps** icon and select **Jour****ney Optimizer**

![](assets/jD1tF2Z4pP2Cv6LMiwpZ7-20251205-221558.png)

2. Click on **Campaigns**

![](assets/VcJhv83IcbJLFOToqA4K--20251208-061706.png)

3. Click on **Create campaign**

![](assets/XDzXpoJVQ8UAPUFjUIKcm-20251208-042622.png)

4. Select **Orchestration - Marketing**  and click on **Confirm**

![](assets/rXDETbHLsGn6XAwz5L6Xp-20251208-042621.png)

5. Provide Campaign details:
   Name: **OC-RSL-MDL-Campaign-01**
   Description: **Relational Verification and Message Delivery Test**
   ****
   and click on **Save**

![](assets/JjiycCwwnH_N5GHoRv22n-20251209-182445.png)

6. Wait for the confirmation message

![](assets/qQvf-7FOMGj38ous6lceS-20251209-182446.png)

7. Click on the **+** within the canvas to open the options menu and then select **Build audience **from the **Targeting activities**

![](assets/G98p8VciVBywGhEzTlvML-20251208-042621.png)

8. The **Build audience** activity opens the details pane on the right, click on the Search icon to select the **Targeting dimension**. The primary key from the relational schema `oc_mdl_customer` created earlier will be used

![](assets/hL52zcFCwAxdNMQWCBX53-20251208-061707.png)

9. Search for the `oc_mdl_customer`Schema, select it and click on **Confirm**
10.

![](assets/3ZI9jS4msWInrXwko5_VQ-20251208-061707.png)

11. The `oc_mdl_customer`is selected, next click on **Create audience **button

![](assets/dZsekGfzcjK8NWvSQyqar-20251208-061707.png)

12. The Create audience details pane opens, click on **Add condition** 

![](assets/1jRy7TAYQQjHNMTa_HEtK-20251208-061707.png)

13. Select the `upgradepref` column for the `oc_mdl_customer` schema and click on **Confirm**

![](assets/1EIMc1eo_JfAMNM7Hv2jW-20251208-061707.png)

14. The `upgradepref` is selected, next for **Custom condition**, select **True** from the drop down. The test is to count

![](assets/f61xPRqHtGSHPG_0ev_nN-20251208-061707.png)

15. Click on the refresh icon to calculate and view the count results. There are two locations to help with calculating the results

![](assets/NcjWrapHk58iimszxx4mC-20251208-061707.png)

16. The count (=7)  shows up for the number of rows in the relational schema that matched the `upgradepref = True` condition

![](assets/KXK8iYJ2ExJOFX24Em31B-20251209-175909.png)

17. To view the results (list of primary keys) which matched the above condition, click on **View results**

![](assets/MhkaUc0rHx-M1pvEF4JoX-20251209-175909.png)

18. The list of primary keys are presented, click on **Close** to close the pane

![](assets/fF7nJnSlEo3orTjY4eh9P-20251208-063650.png)

19. To familiarize with the query being executed, click on Code view. Then click on **Close** to close the pane

![](assets/fKYvm_MYMkTFOKlDRJ_UE-20251209-175909.png)

20. Click on **Confirm** to exit the **Create audience** pane

![](assets/sFzyZ6LHTjG4A0osdnvBk-20251209-175909.png)

21. The canvas with the configured **Build audience** is presented. Click on **Start** at the top to run the campaign in **Test** **mode**

![](assets/6LQlMl1GYu6aNe4y68auz-20251208-061706.png)

22. The **Test mode** executes the activities and presents the results without publishing the campaign. The **Result** node confirms the expected result (=7) from the audience . Click on the Result node to view the options available

![](assets/-LhsC9KGbMqXHRenwpfjS-20251209-181210.png)

23. Click on **Preview results** to view the results.  Click **Close** to close the pane

![](assets/PPK1C-Oqsd-HSirL0CyB2-20251209-181210.png)

24. Click on **Stop** to stop the Test mode of the campaign

![](assets/t53ppxtZ7MLZKprR85vsx-20251208-064514.png)

25. **Save** the campaign, if not saved already (Test mode typically, auto saves the campaign). The campaign will be used again in the Message Delivery in Action Lab. Click on **Campaigns** on the left side rail or the left arrow at the top of the canvas to exit out of the campaign

![](assets/LOsTYWrUs6xvwpqNUTtsW-20251210-010359.png)

26. Click on **Campaigns** on the left side rail or the left arrow at the top of the canvas to exit out of the campaign

![](assets/VcJhv83IcbJLFOToqA4K--20251208-061706.png)

>[!NOTE]
>Note: The campaign created above will be re-used in the Message Delivery in Action Lab.

>[!TIP]
>The verification of the data in the  relational store is complete.
>
>Congratulations! this concludes the Relational data verification step in the lab.

