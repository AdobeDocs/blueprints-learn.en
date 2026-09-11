---
title: Configure mapping
description: Import the mapping set from the batch ingestion lab and update calculated date fields to match the streaming source's date format.
doc-type: article
solution: Experience Platform
exl-id: c05792af-5eab-4e62-a26e-a54478a988a8
---

# Configure mapping

>[!NOTE]
>
>Only follow this section if you successfully completed the Batch Ingestion lab.  Otherwise follow the [Mapping Data](../batch-ingestion/mapping-data/overview.md) steps found in the Batch Ingestion lab.

## Import mapping set

If you completed the Batch Ingestion lab you can re-use the mapping set you created there 😄🎉

Perform the following steps:

1. Click on the **Import Mapping** button on the mapping screen

   ![Import Mapping button on the mapping screen](assets/configure-mapping-import-mapping-button.png)



1. Choose the dataflow you created in the Batch Ingestion section and select it.  It should be named like **Customer Account Batch v2 - \<your initials>.**

![Choosing the Batch Ingestion dataflow to import its mapping set from](assets/configure-mapping-choose-batch-ingestion-dataflow.png)



After import you are going to see errors appear.  This is because the date format used for the birth\_Date field in the sample file has changed.

- Batch Sample file used -> mm/dd/yyyy
- Stream Sample file used -> yyyy-mm-dd

The calculated fields that use **date** functions will need to be updated to account for the change in the date format used. 

![Mapping errors shown after importing the batch ingestion mapping set](assets/configure-mapping-mapping-after-the-import.png)



## Update calculated fields

Update each calculated field by simply clicking on the arrow icon next to each calculated field and then validate your mappings

![Arrow icon to click for editing the formula of a calculated field](assets/configure-mapping-arrow-to-edit-calculated-field-formula.png)

| Target Field            | New Calculated Field                                                                                                                |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| person.birthYear        | date\_part("yyyy",date(birth\_Date,"yyyy-M-d"))                                                                                     |
| person.birthDayAndMonth | concat(date\_part("mm", date(birth\_Date, "yyyy-M-d")).toString(), "-", date\_part("dd", date(birth\_Date, "yyyy-M-d")).toString()) |
