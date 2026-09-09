---
title: Calculated Fields
description: Create calculated field expressions to backfill missing SMS consent values and split a birth date into day, month, and year fields.
doc-type: article
solution: Experience Platform
exl-id: ea5d006b-11c5-439c-af01-bc00b919851f
---

# Overview

The sms\_optin field is a required field in the Customer Account schema. The issue is that sms\_optin field in our streaming source can send *null* values and we need a calculated field to address that otherwise these records will be skipped from ingestion which is a loss. 

![Consentsmarketingsmsval field as shown in the schema.png "consents.marketing.sms.val field as shown in the schema"](assets/P-ANLbgMLxAWCGzeXbUMK_consentsmarketingsmsval-field-as-shown-in-the-schema.png "consents.marketing.sms.val field as shown in the schema")



## Create Calculated Field

1. Create a calculated field by clicking **New field type** icon and then select **Add Calculated Field**. We will assume that for all missing values, consent will be assumed to be not given and will be marked as **"n"**. Note that calculated fields will appear in the left column as the transformation via calculated field is the input to this new mapping. 

![Add a calculated field.png "Add a calculated field"](assets/7koWrpvaZYGWblVwgQQUR_add-a-calculated-field.png "Add a calculated field")



2\. In the Create Calculated field dialog box add the following expression and then click **Preview**

```none
iif(sms_optIn == null or sms_optIn == "", 'n', sms_optIn)
```

![Sms optin calculated field.png "sms optIn calculated field"](assets/JUMPPCHQhEpLrTWaRLkHl_sms-optin-calculated-field.png "sms_optIn calculated field")



3\. You should see a green checkmark in the top right corner of the black box indicating the validity of the expression and the data Preview should only show **“n”** or **“y”** as values. If everything looks good click **Save**.



## Map to Target

A new field will be added to the mapping screen but with an unmapped target field path.

![Sms optin unmapped.png "sms optin unmapped"](assets/ypkVU1U2D2Vjs8TYF5bVs_sms-optin-unmapped.png "sms_optin unmapped")

1. Click on the **Map target field** for the new calculated field you created
1. In the right pane, you will now see the target schema panel open. Type **sms** into the search box
1. Select the **val** field

![Map calculated field to target xdm field](assets/map-calculated-field-to-target-xdm-field.png)



Your final mapping should look like this:

![Image](assets/calculated-fields-1.png)



4\. Validate your mapping to ensure it looks good

![Validate mappings](assets/validate-mappings.png)

>[!NOTE]
>
>Any rows without a valid SMS value will be rejected during ingestion. If partial ingestion is not enabled, the ingestion failure with this row will fail the ingestion of the entire batch or file in our case. With partial ingestion enabled, the rows with required fields with missing values will be rejected but other rows will be ingested.



## Handling Birthdays

There is a requirement to separate out the birth day, month and year into separate fields so that that some of them may not be used in downstream activities. You will need to create two calculated fields to resolve this.

### Create Mapping for Birth Day and Month

1. Add a new calculated field to capture the profiles birth day and month
1. Use the following code for the calculated field:

>[!NOTE]
>
>Instead of just copying the code above, try to understand what is happening by executing the code pieces separately to see how it has been composed to create more complex calculated fields in a single line as multiline is not allowed. Try the following:
>
>1. `date(birth_Date,"M/d/yyyy")`
>2. `date_part("day", date(birth_Date,"M/d/yyyy")).toString()`
>3. `date_part("month", date(birth_Date,"M/d/yyyy")).toString()`
>4. `concat(date_part("month", date(birth_Date,"M/d/yyyy")).toString(),`
>   `"-", date_part("day", date(birth_Date,"M/d/yyyy")).toString())`



3\. Click preview and you should see the following result. If everything looks good click **Save**

![A7RpQDntc7VQQ dX click pr](assets/click-pr.png)



4\. Map the calculated field to **person.birthDayAndMonth**

5\. Validate your mapping



### Create Mapping for Birth Year

1. Create a new calculated field to capture the birth year of the profile using the code below

```none
date_part("yyyy",date(birth_Date,"M/d/yyyy"))
```

    2\. Map the calculated field to the target location of     **person.birthYear**

    3\. Validate your mapping

>[!NOTE]
>
>Observe that the dates are in **MM/DD/YYYY** format but **birth\_Date** data in the sample is coming as either single or double digits for the day and month. For the **date** function to work, you have to specify the input format of the data such as **M/d/yyyy** so that you can account for 1 to 2 digits for the month and day. Without this date input format specification, the validation of these mappings will fail.
