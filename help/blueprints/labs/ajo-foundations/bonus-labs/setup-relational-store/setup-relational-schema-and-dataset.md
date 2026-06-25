---
title: Setup Relational Schema and Dataset
description: Setup Relational Schema and Dataset
doc-type: article
solution: Experience Platform
exl-id: 4dd1d41c-aaeb-4505-bba3-29887aedbc03
---

This lab covers Relational schema and dataset creation along with loading data for use in Orchestrated Campaigns. The DDL approach will be used for schema and dataset creation.

# 1 - Prerequisite

Download the two files required for the lab to the local work station

1. DDL:

>[!NOTE]
>
>Download **OC_MDL_Customer.ddl** from your lab administrator.

1. CSV:

>[!NOTE]
>
>Download **OC_MDL_CustomerData.csv** from your lab administrator.



## 2 - Relational Schema and Dataset using DDL

1. In the AEP UI, navigate to Schemas on the left rail

![JTooP0Nmz3vqfa  20251203 153745](assets/o4AQg_JTooP0Nmz3vqfa--20251203-153745.png)

1. Click on **Create schema** and select **Relational**

![IBWtYlXtSFL61GhNHowN5 20251203 153745](assets/IBWtYlXtSFL61GhNHowN5-20251203-153745.png)

1. Select **Upload DDL file** option, click on the **Choose files** button to use the DDL file downloaded in the Prerequsite section. 


![CVLi u3M4XwZZNZNj4Uxg 20251203 153745](assets/CVLi-u3M4XwZZNZNj4Uxg-20251203-153745.png)

![QPJELbormxEthc2ayqHIo 20251203 184023](assets/qPJELbormxEthc2ayqHIo-20251203-184023.png)

1. Click on **Next**

![7I3lTY70Xk9mNS9PFtANe 20251214 031341](assets/7I3lTY70Xk9mNS9PFtANe-20251214-031341.png)

1. Mark the fields used as Identity and Versioning. In this case, the `customer_id` and the `lastmodified` columns will be used for this respectively. 

![YLBanRjsqI3GTnN9vtscC 20251203 184023](assets/yLBanRjsqI3GTnN9vtscC-20251203-184023.png)

1. For `customer_id`, from the drop down select `customerID` as Identity 

![R 20251203 184023](assets/H9J6OwAAVhoXMSB2Tpv_R-20251203-184023.png)

![78XTXMB99m6lFzqJutbtj 20251203 184023](assets/78XTXMB99m6lFzqJutbtj-20251203-184023.png)

1. For `lastmodified` row, select the `Versioning` option

![KggqVs 20251203 184023](assets/-ijURmg7caHRSl_kggqVs-20251203-184023.png)

1. Click on **Done**

![97Y4Pss0cKlyM 20251203 184941](assets/mG-VEBR_97Y4Pss0cKlyM-20251203-184941.png)

1. The visual representation of the schema is presented, click on **Save**

![MeM4yPSRmvivePsrF38B3 20251204 180401](assets/meM4yPSRmvivePsrF38B3-20251204-180401.png)

1.  The dialog confirming the start of the DDL processing is presented, click on **Open jobs** button to view the progress

![M9CEsReT1V5fjH5OcDyUl 20251204 180402](assets/m9CEsReT1V5fjH5OcDyUl-20251204-180402.png)

1. Refresh the page. The entire DDL processing steps can be traced here and goes through four steps of :
    1\) Validation 
    2\) Schema creation 
    3\) Dataset creation 
    4\) Dataset enablement for Orchestrated Campaigns

![1HF7HzG 07WEMVESqwnDB 20251204 180402](assets/1HF7HzG-07WEMVESqwnDB-20251204-180402.png)

![20251204 180402](assets/Lvd3Ir8Z5V-1L5co8Mtk_-20251204-180402.png)

![OTmGj0G9Gk21A786Y9cO 20251204 180402](assets/-OTmGj0G9Gk21A786Y9cO-20251204-180402.png)

![C8ukOW6G3pZGqK1OI 20251204 180402](assets/j8C_C8ukOW6G3pZGqK1OI-20251204-180402.png)

The DDL processing is complete and the schema and dataset has been created successfully.



1. Navigate to **Dataset** section on the left rail 

![Ed 1h47bn1LNk7rQuBKX1 20251204 182145](assets/ed-1h47bn1LNk7rQuBKX1-20251204-182145.png)

Search for the `oc_mdl_customer` dataset just created in the above step

![NkCsL Y14z3mSOgPxUO 20251204 182145](assets/e_NkCsL-Y14z3mSOgPxUO-20251204-182145.png)

View the dataset details and also that it is enabled for Orchestrated Campaign

![6CqeR3Pa5gFrWiGgHJnFY 20251204 182145](assets/6CqeR3Pa5gFrWiGgHJnFY-20251204-182145.png)

>[!TIP]
>
>Using the DDL approach, the schema, dataset have been successfully created and the dataset has also been enabled for **Orchestrated Campaigns**.

## 3 - Data ingestion

Data will be ingested into the dataset created above using the AEP UI and the local CSV file downloaded earlied in the Prerequsite section

1. Navigate to **Workflows** on the left side rail and then to **Map CSV to XDM** **schema**

![ESpo75AuzBAjdSCwxjxSA 20251204 202719](assets/ESpo75AuzBAjdSCwxjxSA-20251204-202719.png)

1. Click on **Launch**

![5IXH1iEZsN6Us3Fp3rLLK 20251204 202719](assets/5IXH1iEZsN6Us3Fp3rLLK-20251204-202719.png)

1. Toggle **Enable change data capture** to view the list of datasets related to Relational schemas. Select the `oc_mdl_customer` dataset created earlier from the drop down and click on **Next** 

![X9OUff8okdJ53yYvVONpE 20251204 202719](assets/X9OUff8okdJ53yYvVONpE-20251204-202719.png)

1. Click on Choose files to upload local file (use the CSV file downloaded in the Prerequsite section)

![E6r5SD2PSZXnGnnwfaBcv 20251204 202719](assets/e6r5SD2PSZXnGnnwfaBcv-20251204-202719.png)

![8e26i5nWr7HoM4FM6ysFW 20251204 202719](assets/8e26i5nWr7HoM4FM6ysFW-20251204-202719.png)

1. Once the file is loaded, view/verify the data and click on **Next**

![5m 20251205 182914](assets/dmSe8fbp-nuCpYZRaQ_5m-20251205-182914.png)

1. The auto-mapping performs the CSV fields to the Schema fields mapping

>[!WARNING]
>
>It has been observed that sometimes the mapping could be incorrect. This can be fixed by manually adding the correct mappings and validating them. The following steps will help fix that.
>
>If mappings are all correct and no errors are encountered, please move to the next step.

![CkrT9k55ziZ 20251204 202719](assets/VBALOSsCA_CkrT9k55ziZ-20251204-202719.png)

Delete the incorrect mappings:



![16H10rmdG9rQcbReMPaqT 20251204 202718](assets/16H10rmdG9rQcbReMPaqT-20251204-202718.png)

Once the mappings are deleted, click on on **Validate**

![AWNE2RARnsVdV3vBMgDmw 20251204 202718](assets/aWNE2RARnsVdV3vBMgDmw-20251204-202718.png)

The UI will complain of missing mappings, which needs to be manually added

![8BLRgEe9qM6q3Bp248RIM 20251204 202718](assets/8BLRgEe9qM6q3Bp248RIM-20251204-202718.png)

Click on **New field ****type** and select **Add new field**

![IRBxq gVTi68zFjkDlnwY 20251204 202718](assets/iRBxq-gVTi68zFjkDlnwY-20251204-202718.png)

Choose the `upgradePref` from the Source Schema (CSV) mapping and click on **Select**

![VUFGEdpkBMAU 20251204 202718](assets/U8om5Nmn_vUFGEdpkBMAU-20251204-202718.png)

Click on the **Map target field** under **TARGET FIELDS**



![FmYdNjYKuaa1iukxRnMiQ 20251204 202718](assets/fmYdNjYKuaa1iukxRnMiQ-20251204-202718.png)

Select `upgradepref` attribute from the Schema structure

![EZZBroJNIcfaxkBmXflF9 20251204 202718](assets/eZZBroJNIcfaxkBmXflF9-20251204-202718.png)

The input field `upgradePref` has been mapped to `upgradepref` attribute from the Schema. 

Map the remaining field. Click on **New field type** and select **Add new field** to add

![IRBxq gVTi68zFjkDlnwY 20251204 202718](assets/iRBxq-gVTi68zFjkDlnwY-20251204-202718.png)

Choose the `LastModDate` from the Source Schema (CSV) mapping and click on **Select**

![Fw8sYAfGneHo4TS34L ld 20251204 202718](assets/Fw8sYAfGneHo4TS34L-ld-20251204-202718.png)

Click on the **Map target field** under **TARGET FIELDS**

![UxTbJWIip 20251204 202718](assets/yn0KQzlMUhM_uxTbJWIip-20251204-202718.png)

Select `lastmodified` attribute from the Schema structure

![Ax09YukxngGs9pwBisyvt 20251204 202718](assets/ax09YukxngGs9pwBisyvt-20251204-202718.png)

Confirm all the mappings and click on **Validate** to remove all mapping errors

![HROEPsZk2X5cLEhx1 ty0 20251204 202718](assets/hROEPsZk2X5cLEhx1-ty0-20251204-202718.png)

1. If errors have been cleared, click on **Finish** to start the ingestion process

![C S  O4 20251204 202718](assets/4GXNeyCX8oUM7_c_S-_O4-20251204-202718.png)

1. Once the ingestion process is initiated, refresh the Dataflow activity page for the dataset to see the details. Once completed, the dataflow status is updated to **Success** 

![HiJuYSkH2QiRaTiqHf 20251204 202719](assets/Lm_HiJuYSkH2QiRaTiqHf-20251204-202719.png)

>[!TIP]
>
>Congratulations! the schema and the corresponding dataset have been created and data has been successfully ingested into the dataset.

## Bonus: Graphical view of the schema and relationships

As new Relational schemas get created and relationships defined, the AEP UI provides an option to have a graphical view of these schemas and their relationships:

1. In the AEP UI, navigate to Schemas on the left rail

![JTooP0Nmz3vqfa  20251203 153745](assets/o4AQg_JTooP0Nmz3vqfa--20251203-153745.png)

1. Click on the Relationships tab

![S 9wMAZzkFOj8mD4lwXGU 20251208 175255](assets/s-9wMAZzkFOj8mD4lwXGU-20251208-175255.png)

1. Click on **View relationships diagram**

![KNsfTzY120aCWdU aezSo 20251208 175605](assets/KNsfTzY120aCWdU-aezSo-20251208-175605.png)

1. Click on **Select Schemas**

![9XlycUi3 XGq3J1IpyIaZ 20251208 175605](assets/9XlycUi3-XGq3J1IpyIaZ-20251208-175605.png)

1. Select few/all of the schemas and click on **Confirm**

![7Rlt3dAyftDel0XkACSI 20251208 175605](assets/_7Rlt3dAyftDel0XkACSI-20251208-175605.png)

1. The graphical view of the Schema relationships are renderred. Click on **Back** to exit

![AGFIDZP6A xdN 20251208 175255](assets/uSKqgJm_aGFIDZP6A_xdN-20251208-175255.png)

>[!TIP]
>
>Congratulations! this concludes the Relational Schema+Dataset setup step in the lab.

