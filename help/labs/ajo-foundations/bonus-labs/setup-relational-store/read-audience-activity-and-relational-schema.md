---
title: Read audience activity and Relational schema
description: Read audience activity and Relational schema
doc-type: article
exl-id: 293d6a9f-5dfd-49fa-b46d-ead2e3b9cc1b
---

This lab will cover using Relational schema with the Read audience activity. Orchestrated Campaign uses the  Relational schema for all the activities. When using the Read audience, which reads the audience from AEP, a corresponding Entity (Target Dimension) has to be configured to reconcile the audience with the Campaign Target Dimension. 

# Configure Read audience activity

1. In the left hand rail, click on **Campaigns**

![](assets/VcJhv83IcbJLFOToqA4K--20251208-061706.png)

2. Click on **Create campaign**

![](assets/XDzXpoJVQ8UAPUFjUIKcm-20251208-042622.png)

3. Select **Orchestration - Marketing**  and click on **Confirm**

![](assets/rXDETbHLsGn6XAwz5L6Xp-20251208-042621.png)

4. Provide Campaign details:
   Name: **OC-RSL-ReadAudience-Test**
   Description: **RSL-Read Audience Test**
   ****
   and click on **Save**

![](assets/N-T0yLrWhzPfXaExvYLcK-20251211-184647.png)

5. Wait for the confirmation message

![](assets/aSfx_-DKKZPW1wgMC0_Zl-20251212-181517.png)

6. Click on the **+** inside the canvas to open the options menu and then select **Read audience** from the **Targeting activities**

![](assets/rxBhUmbXGsN4vDC4QDT01-20251211-184647.png)

7. In the **Read audienc**e details pane, click on the Search icon for **Audience**

![](assets/ZYzdri3dPsQHa1FU_fGUG-20251211-184647.png)

8. Select the **dep: Basic Plan Members** audience with Profile Count of **9**

![](assets/nuWj7_RThP7mtGzLLso2f-20251212-062205.png)

9. Next click on the drop down for **Entity** and select the `oc_mdl_customer - customer_id `for Campaign Target Dimension

![](assets/1nWNIZTcW6I2CiGWOTFZ4-20251212-062205.png)

>[!NOTE]
>Other attributes can also be extracted from the AEP Profile for use in the canvas, using the **Add attribute **button. But for this lab, extra attributes are not required so that step is skipped.

10. The settings for the **Read Audience** activity are filled in. Click on **Start** to run the campaign in **Test mode**

![](assets/jL-gNnLT5ur1hCeVuFJkI-20251212-062204.png)

11. The test execution starts and the results are displayed when completed. Click on the **Result** node

![](assets/ioGGmzkXFxsRm7rCRtOfK-20251212-062204.png)

12. In the details pane of the **Result** node, click on the **Preview results** button to see the results

![](assets/F-4h4s0fSLghxZUneJfsz-20251212-062204.png)

13. Notice that **2** profiles from the **Read audience** do not have a corresponding matching **Target dimension** from the relational schema. And since Orchestrated Campaign works off the Relational schema, the unmatched `customer_id` from the **Read audience** will be dropped and only the matched ones (**4** in this case), will be usable in subsequent activites that leverages relational data in the campaign.

![](assets/TVxRSLKjbZFYFQLbi8xol-20251212-062204.png)

14. Click on **Stop** to stop the **Test mode** of the campaign

![](assets/DVIzOWo3JOCYBpR5_j8Hd-20251212-062205.png)

15. Click on the **+** at the end of the flow and add **Split** from the **Targeting activities**

![](assets/n2x2K6sMHB_VxsogFB5SE-20251212-062205.png)

17. In the details pane of the **Split** activity, expand the first split called **Subset**

![](assets/oL3kah5NXgyNLOV76MQ0L-20251212-062205.png)

18. Rename it to "**Upgrade True**" and click on **Create filter **to set the filter condition

![](assets/N3XY25j8NTcjDKEmaNiPs-20251212-062205.png)

19. In the **Create filte**r pane, click on **Add condition**

![](assets/ukjuh4Lh_0QAIHTwu9nIW-20251212-062205.png)

20. Since no other attributes were extracted from the AEP Profile, <font color="#EF4444">the only AEP Profile attribute available (reason ?)</font> here is the `customer_id`. However, since there are matching Targeting dimension from the relational schema, all of the columns from the Relational schema are available for setting up the filter condition. Expand the **Targeting dimension** by clicking on  **>** 

![](assets/05hAGBctUhahoW0JLmavw-20251212-062205.png)

21. Select `upgradepref` from the list and click on **Confirm**

![](assets/RthE_U73niTWgKbLUyNii-20251212-062204.png)

22. Since `upgradepref` is of Boolean type, for the **Custom condition**, select **True** from the drop down. Click on **Confirm** to exit

![](assets/KdADvlKEMR0PEJU2t2HyX-20251212-184829.png)

23. Back in the details pane of the **Split** activity, the settings for the first Split are complete. Click on **Add segment** to the second split

![](assets/D8famGeIedBMyP5dOMiMm-20251212-062204.png)

24. Rename it to "**Upgrade False**" and click on **Create filter **to set the filter condition

![](assets/ku5TSY2_JvMhxonpoOr08-20251212-062204.png)

25. In the **Create filte**r pane, click on **Add condition**

![](assets/BCTZxVZgvDguWe2Je3IbN-20251212-062204.png)

26. Expand the **Targeting dimension** by clicking on  **>**

![](assets/W1b44oV0_4Y0geQHePMQa-20251212-062204.png)

27. Select `upgradepref` from the list and click on **Confirm**

![](assets/WICZ1bXJdGx9SJjBXnrzq-20251212-062204.png)

28. For the **Custom condition**, select **False** from the drop down. Click on **Confirm** to exit

![](assets/KsiJRg-_GYNdTrNlBmYWn-20251212-185337.png)

29. Back in the details pane of the **Split** activity, the settings for the two Splits are complete. Click on **Start** to run the campaign in **Test mode**

![](assets/mwuekRVgeDzPHVZ9CLLkY-20251212-062204.png)

30. The test execution starts and the results are displayed when completed. As mentioned above, the activities in the campaign works off the Relational schema. And since only 4 matching targeting dimension were found in the Relational schema, the same count is observed in the Split operation (**3**  and **1**) as well.  Click on **Stop** to stop the **Test mode** of the campaign

![](assets/OvSMv1RYtld_-wHvmbjCA-20251212-062205.png)

>[!NOTE]
>While the Read audience showed 6 profiles, when it was joined with the Relational schema, via the Campaign Target Dimension, only a total of 4 profiles matched. These 4 matched customer ids are available for use in the following activities. Out of the 4 customer id matches, 3 customer ids had `upgradepref` set to **true** and 1 had it to **false**, which was evident via the Split flows.

>[!TIP]
>Congratulations, this completes the lab on using the Read Audience activity with Relational schema.

# Reference

[https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/design-campaigns/read-audience](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/design-campaigns/read-audience)

