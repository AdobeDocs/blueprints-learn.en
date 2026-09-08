---
title: Configure Mapping
description: Configure Mapping
doc-type: article
solution: Experience Platform
exl-id: c05792af-5eab-4e62-a26e-a54478a988a8
---

>[!CAUTION]
>
>Only follow this section if you successfully completed the Batch Ingestion lab.  Otherwise follow the [Mapping Data](../batch-ingestion/mapping-data/overview.md) steps found in the Batch Ingestion lab.

# Import Mapping Set

If you completed the Batch Ingestion lab you can re-use the mapping set you created there 😄🎉

Perform the following steps:

1. Click on the **Import Mapping** button on the mapping screen

![Import mapping button](assets/import-mapping-button.png)



2\. Choose the datalfow you created in the Batch Ingestion section and select it.  It should be named like **Customer Account Batch v2 - \<your initials>.**

![Choose t](assets/choose-t.png)



After import you are going to see errors appear.  This is because the date format used for the birth\_date field in the sample file has changed.

- Batch Sample file used -> mm/dd/yyyy
- Stream Sample file used -> yyyy-mm-dd

The calculated fields that use **date **functions will need to be updated to account for the change in the date format used. 

![Mapping after the import](assets/mapping-after-the-import.png)



## Update Calculated Fields

Update each calculated field by simply clicking on the arrow icon next to each calculated field and then validate your mappings

![OQ arrow to click to edit the formula for the calculated fields](assets/arrow-to-click-to-edit-the-formula-for-the-calculated-fields.png)

| Target Field            | New Calculated Field                                                                                                                |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| person.birthYear        | date\_part("yyyy",date(birth\_Date,"yyyy-M-d"))                                                                                     |
| person.birthDayAndMonth | concat(date\_part("mm", date(birth\_Date, "yyyy-M-d")).toString(), "-", date\_part("dd", date(birth\_Date, "yyyy-M-d")).toString()) |

