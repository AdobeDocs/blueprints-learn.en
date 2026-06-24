---
title: Setup Relational Schema and Dataset
description: Setup Relational Schema and Dataset
doc-type: article
exl-id: 4dd1d41c-aaeb-4505-bba3-29887aedbc03
---

This lab covers Relational schema and dataset creation along with loading data for use in Orchestrated Campaigns. The DDL approach will be used for schema and dataset creation.

# 1 - Prerequisite

Download the two files required for the lab to the local work station

1. DDL:

>[!NOTE]
>Download **OC_MDL_Customer.ddl** from your lab administrator.

2. CSV:

>[!NOTE]
>Download **OC_MDL_CustomerData.csv** from your lab administrator.



# 2 - Relational Schema and Dataset using DDL

1. In the AEP UI, navigate to Schemas on the left rail

![](assets/o4AQg_JTooP0Nmz3vqfa--20251203-153745.png)

2. Click on **Create schema** and select **Relational**

![](assets/IBWtYlXtSFL61GhNHowN5-20251203-153745.png)

3. Select **Upload DDL file** option, click on the **Choose files** button to use the DDL file downloaded in the Prerequsite section. 


![](assets/CVLi-u3M4XwZZNZNj4Uxg-20251203-153745.png)

![](assets/qPJELbormxEthc2ayqHIo-20251203-184023.png)

4. Click on **Next**

![](assets/7I3lTY70Xk9mNS9PFtANe-20251214-031341.png)

5. Mark the fields used as Identity and Versioning. In this case, the `customer_id` and the `lastmodified` columns will be used for this respectively. 

![](assets/yLBanRjsqI3GTnN9vtscC-20251203-184023.png)

6. For `customer_id`, from the drop down select `customerID` as Identity 

![](assets/H9J6OwAAVhoXMSB2Tpv_R-20251203-184023.png)

![](assets/78XTXMB99m6lFzqJutbtj-20251203-184023.png)

7. For `lastmodified` row, select the `Versioning` option

![](assets/-ijURmg7caHRSl_kggqVs-20251203-184023.png)

8. Click on **Done**

![](assets/mG-VEBR_97Y4Pss0cKlyM-20251203-184941.png)

9. The visual representation of the schema is presented, click on **Save**

![](assets/meM4yPSRmvivePsrF38B3-20251204-180401.png)

10.  The dialog confirming the start of the DDL processing is presented, click on **Open jobs** button to view the progress

![](assets/m9CEsReT1V5fjH5OcDyUl-20251204-180402.png)

11. Refresh the page. The entire DDL processing steps can be traced here and goes through four steps of :
    1\) Validation 
    2\) Schema creation 
    3\) Dataset creation 
    4\) Dataset enablement for Orchestrated Campaigns

![](assets/1HF7HzG-07WEMVESqwnDB-20251204-180402.png)

![](assets/Lvd3Ir8Z5V-1L5co8Mtk_-20251204-180402.png)

![](assets/-OTmGj0G9Gk21A786Y9cO-20251204-180402.png)

![](assets/j8C_C8ukOW6G3pZGqK1OI-20251204-180402.png)

:::Paragraph{indent="2"}
The DDL processing is complete and the schema and dataset has been created successfully.
:::



1. Navigate to **Dataset** section on the left rail 

![](assets/ed-1h47bn1LNk7rQuBKX1-20251204-182145.png)

:::Paragraph{indent="2"}
Search for the `oc_mdl_customer` dataset just created in the above step
:::

![](assets/e_NkCsL-Y14z3mSOgPxUO-20251204-182145.png)

:::Paragraph{indent="2"}
View the dataset details and also that it is enabled for Orchestrated Campaign
:::

![](assets/6CqeR3Pa5gFrWiGgHJnFY-20251204-182145.png)

>[!TIP]
>Using the DDL approach, the schema, dataset have been successfully created and the dataset has also been enabled for **Orchestrated Campaigns**.

# 3 - Data ingestion

Data will be ingested into the dataset created above using the AEP UI and the local CSV file downloaded earlied in the Prerequsite section

1. Navigate to **Workflows** on the left side rail and then to **Map CSV to XDM** **schema**

![](assets/ESpo75AuzBAjdSCwxjxSA-20251204-202719.png)

2. Click on **Launch**

![](assets/5IXH1iEZsN6Us3Fp3rLLK-20251204-202719.png)

3. Toggle **Enable change data capture** to view the list of datasets related to Relational schemas. Select the `oc_mdl_customer` dataset created earlier from the drop down and click on **Next** 

![](assets/X9OUff8okdJ53yYvVONpE-20251204-202719.png)

4. Click on Choose files to upload local file (use the CSV file downloaded in the Prerequsite section)

![](assets/e6r5SD2PSZXnGnnwfaBcv-20251204-202719.png)

![](assets/8e26i5nWr7HoM4FM6ysFW-20251204-202719.png)

5. Once the file is loaded, view/verify the data and click on **Next**

![](assets/dmSe8fbp-nuCpYZRaQ_5m-20251205-182914.png)

6. The auto-mapping performs the CSV fields to the Schema fields mapping

>[!WARNING]
>It has been observed that sometimes the mapping could be incorrect. This can be fixed by manually adding the correct mappings and validating them. The following steps will help fix that.
>
>If mappings are all correct and no errors are encountered, please move to the next step.

![](assets/VBALOSsCA_CkrT9k55ziZ-20251204-202719.png)

:::Paragraph{indent="2"}
Delete the incorrect mappings:
:::

:::Paragraph{indent="2"}

:::

![](assets/16H10rmdG9rQcbReMPaqT-20251204-202718.png)

:::Paragraph{indent="2"}
Once the mappings are deleted, click on on **Validate**
:::

![](assets/aWNE2RARnsVdV3vBMgDmw-20251204-202718.png)

:::Paragraph{indent="2"}
The UI will complain of missing mappings, which needs to be manually added
:::

![](assets/8BLRgEe9qM6q3Bp248RIM-20251204-202718.png)

:::Paragraph{indent="2"}
Click on **New field ****type** and select **Add new field**
:::

![](assets/iRBxq-gVTi68zFjkDlnwY-20251204-202718.png)

:::Paragraph{indent="2"}
Choose the `upgradePref` from the Source Schema (CSV) mapping and click on **Select**
:::

![](assets/U8om5Nmn_vUFGEdpkBMAU-20251204-202718.png)

:::Paragraph{indent="2"}
Click on the **Map target field** under **TARGET FIELDS**
:::

:::Paragraph{indent="2"}

:::

![](assets/fmYdNjYKuaa1iukxRnMiQ-20251204-202718.png)

:::Paragraph{indent="2"}
Select `upgradepref` attribute from the Schema structure
:::

![](assets/eZZBroJNIcfaxkBmXflF9-20251204-202718.png)

:::Paragraph{indent="2"}
The input field `upgradePref` has been mapped to `upgradepref` attribute from the Schema. 
:::

:::Paragraph{indent="2"}
Map the remaining field. Click on **New field type** and select **Add new field** to add
:::

![](assets/iRBxq-gVTi68zFjkDlnwY-20251204-202718.png)

:::Paragraph{indent="2"}
Choose the `LastModDate` from the Source Schema (CSV) mapping and click on **Select**
:::

![](assets/Fw8sYAfGneHo4TS34L-ld-20251204-202718.png)

:::Paragraph{indent="2"}
Click on the **Map target field** under **TARGET FIELDS**
:::

![](assets/yn0KQzlMUhM_uxTbJWIip-20251204-202718.png)

:::Paragraph{indent="2"}
Select `lastmodified` attribute from the Schema structure
:::

![](assets/ax09YukxngGs9pwBisyvt-20251204-202718.png)

:::Paragraph{indent="2"}
Confirm all the mappings and click on **Validate** to remove all mapping errors
:::

![](assets/hROEPsZk2X5cLEhx1-ty0-20251204-202718.png)

7. If errors have been cleared, click on **Finish** to start the ingestion process

![](assets/4GXNeyCX8oUM7_c_S-_O4-20251204-202718.png)

8. Once the ingestion process is initiated, refresh the Dataflow activity page for the dataset to see the details. Once completed, the dataflow status is updated to **Success** 

![](assets/Lm_HiJuYSkH2QiRaTiqHf-20251204-202719.png)

>[!TIP]
>Congratulations! the schema and the corresponding dataset have been created and data has been successfully ingested into the dataset.

# Bonus: Graphical view of the schema and relationships

As new Relational schemas get created and relationships defined, the AEP UI provides an option to have a graphical view of these schemas and their relationships:

1. In the AEP UI, navigate to Schemas on the left rail

![](assets/o4AQg_JTooP0Nmz3vqfa--20251203-153745.png)

2. Click on the Relationships tab

![](assets/s-9wMAZzkFOj8mD4lwXGU-20251208-175255.png)

3. Click on **View relationships diagram**

![](assets/KNsfTzY120aCWdU-aezSo-20251208-175605.png)

4. Click on **Select Schemas**

![](assets/9XlycUi3-XGq3J1IpyIaZ-20251208-175605.png)

5. Select few/all of the schemas and click on **Confirm**

![](assets/_7Rlt3dAyftDel0XkACSI-20251208-175605.png)

6. The graphical view of the Schema relationships are renderred. Click on **Back** to exit

![](assets/uSKqgJm_aGFIDZP6A_xdN-20251208-175255.png)

>[!TIP]
>Congratulations! this concludes the Relational Schema+Dataset setup step in the lab.

