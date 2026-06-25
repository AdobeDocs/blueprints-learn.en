---
hold: true
title: Data Verification
description: Data Verification
doc-type: article

solution: Experience Platform
exl-id: 77226236-7caa-4ebd-9ab9-59ef1662f5fc
---

This lab will cover validation and verification of data ingested in the previous section.

>[!WARNING]
>
>After data has been ingested into the dataset, it takes about 15 minutes for data to be synced to the relational store. 

# 1 - Verification of data in datalake

1. In the AEP UI, navigate to Datasets on the left rail

![Mpu1uVf0sZxtw9BIc1ZFJ 20251205 184336](assets/Mpu1uVf0sZxtw9BIc1ZFJ-20251205-184336.png)

1. Search for `oc_mdl_customer` in the search box and click on the dataset

![Btk3hkCZVkIQgnGLAryb 20251205 184602](assets/-btk3hkCZVkIQgnGLAryb-20251205-184602.png)

1. View the dataset details providing details on the records and time ingested. Click on **Preview dataset**

![DhV8bSPCNWHaMsB Hu0k8 20251205 184336](assets/dhV8bSPCNWHaMsB-Hu0k8-20251205-184336.png)

1. A preview of the data ingested into this dataset is shown along with the fields in the left pane

![Xn2U1P3V5rIBokslS6QMx 20251205 184336](assets/xn2U1P3V5rIBokslS6QMx-20251205-184336.png)

>[!TIP]
>
>The local file loaded in the previous lab has been successfully ingested into the dataset and resides in the datalake.

>[!WARNING]
>
>It takes about 15 minutes for data to be synced to the relational store. The next section will cover data verification in the relational store.

## 2 - Verification of data in relational store

1. Click on the **Apps** icon and select **Jour****ney Optimizer**

![JD1tF2Z4pP2Cv6LMiwpZ7 20251205 221558](assets/jD1tF2Z4pP2Cv6LMiwpZ7-20251205-221558.png)

1. Click on **Campaigns**

![VcJhv83IcbJLFOToqA4K  20251208 061706](assets/VcJhv83IcbJLFOToqA4K--20251208-061706.png)

1. Click on **Create campaign**

![XDzXpoJVQ8UAPUFjUIKcm 20251208 042622](assets/XDzXpoJVQ8UAPUFjUIKcm-20251208-042622.png)

1. Select **Orchestration - Marketing**  and click on **Confirm**

![RXDETbHLsGn6XAwz5L6Xp 20251208 042621](assets/rXDETbHLsGn6XAwz5L6Xp-20251208-042621.png)

1. Provide Campaign details:
   Name: **OC-RSL-MDL-Campaign-01**
   Description: **Relational Verification and Message Delivery Test**
   and click on **Save**

![N5GHoRv22n 20251209 182445](assets/JjiycCwwnH_N5GHoRv22n-20251209-182445.png)

1. Wait for the confirmation message

![QQvf 7FOMGj38ous6lceS 20251209 182446](assets/qQvf-7FOMGj38ous6lceS-20251209-182446.png)

1. Click on the **+** within the canvas to open the options menu and then select **Build audience **from the **Targeting activities**

![G98p8VciVBywGhEzTlvML 20251208 042621](assets/G98p8VciVBywGhEzTlvML-20251208-042621.png)

1. The **Build audience** activity opens the details pane on the right, click on the Search icon to select the **Targeting dimension**. The primary key from the relational schema `oc_mdl_customer` created earlier will be used

![HL52zcFCwAxdNMQWCBX53 20251208 061707](assets/hL52zcFCwAxdNMQWCBX53-20251208-061707.png)

1. Search for the `oc_mdl_customer`Schema, select it and click on **Confirm**
10.

![VQ 20251208 061707](assets/3ZI9jS4msWInrXwko5_VQ-20251208-061707.png)

1. The `oc_mdl_customer`is selected, next click on **Create audience **button

![DZsekGfzcjK8NWvSQyqar 20251208 061707](assets/dZsekGfzcjK8NWvSQyqar-20251208-061707.png)

1. The Create audience details pane opens, click on **Add condition** 

![HEtK 20251208 061707](assets/1jRy7TAYQQjHNMTa_HEtK-20251208-061707.png)

1. Select the `upgradepref` column for the `oc_mdl_customer` schema and click on **Confirm**

![JfAMNM7Hv2jW 20251208 061707](assets/1EIMc1eo_JfAMNM7Hv2jW-20251208-061707.png)

1. The `upgradepref` is selected, next for **Custom condition**, select **True** from the drop down. The test is to count

![0ev nN 20251208 061707](assets/f61xPRqHtGSHPG_0ev_nN-20251208-061707.png)

1. Click on the refresh icon to calculate and view the count results. There are two locations to help with calculating the results

![NcjWrapHk58iimszxx4mC 20251208 061707](assets/NcjWrapHk58iimszxx4mC-20251208-061707.png)

1. The count (=7)  shows up for the number of rows in the relational schema that matched the `upgradepref = True` condition

![KXK8iYJ2ExJOFX24Em31B 20251209 175909](assets/KXK8iYJ2ExJOFX24Em31B-20251209-175909.png)

1. To view the results (list of primary keys) which matched the above condition, click on **View results**

![MhkaUc0rHx M1pvEF4JoX 20251209 175909](assets/MhkaUc0rHx-M1pvEF4JoX-20251209-175909.png)

1. The list of primary keys are presented, click on **Close** to close the pane

![FF7nJnSlEo3orTjY4eh9P 20251208 063650](assets/fF7nJnSlEo3orTjY4eh9P-20251208-063650.png)

1. To familiarize with the query being executed, click on Code view. Then click on **Close** to close the pane

![MYMkTFOKlDRJ UE 20251209 175909](assets/fKYvm_MYMkTFOKlDRJ_UE-20251209-175909.png)

1. Click on **Confirm** to exit the **Create audience** pane

![SFzyZ6LHTjG4A0osdnvBk 20251209 175909](assets/sFzyZ6LHTjG4A0osdnvBk-20251209-175909.png)

1. The canvas with the configured **Build audience** is presented. Click on **Start** at the top to run the campaign in **Test** **mode**

![6LQlMl1GYu6aNe4y68auz 20251208 061706](assets/6LQlMl1GYu6aNe4y68auz-20251208-061706.png)

1. The **Test mode** executes the activities and presents the results without publishing the campaign. The **Result** node confirms the expected result (=7) from the audience . Click on the Result node to view the options available

![LhsC9KGbMqXHRenwpfjS 20251209 181210](assets/-LhsC9KGbMqXHRenwpfjS-20251209-181210.png)

1. Click on **Preview results** to view the results.  Click **Close** to close the pane

![PPK1C Oqsd HSirL0CyB2 20251209 181210](assets/PPK1C-Oqsd-HSirL0CyB2-20251209-181210.png)

1. Click on **Stop** to stop the Test mode of the campaign

![T53ppxtZ7MLZKprR85vsx 20251208 064514](assets/t53ppxtZ7MLZKprR85vsx-20251208-064514.png)

1. **Save** the campaign, if not saved already (Test mode typically, auto saves the campaign). The campaign will be used again in the Message Delivery in Action Lab. Click on **Campaigns** on the left side rail or the left arrow at the top of the canvas to exit out of the campaign

![LOsTYWrUs6xvwpqNUTtsW 20251210 010359](assets/LOsTYWrUs6xvwpqNUTtsW-20251210-010359.png)

1. Click on **Campaigns** on the left side rail or the left arrow at the top of the canvas to exit out of the campaign

![VcJhv83IcbJLFOToqA4K  20251208 061706](assets/VcJhv83IcbJLFOToqA4K--20251208-061706.png)

>[!NOTE]
>
>Note: The campaign created above will be re-used in the Message Delivery in Action Lab.

>[!TIP]
>
>The verification of the data in the  relational store is complete.
>
>Congratulations! this concludes the Relational data verification step in the lab.

