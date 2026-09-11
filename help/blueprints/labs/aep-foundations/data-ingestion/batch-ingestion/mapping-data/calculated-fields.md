---
title: Calculated fields
description: Create calculated field expressions to backfill missing SMS consent values and split a birth date into day, month, and year fields.
doc-type: article
solution: Experience Platform
exl-id: ea5d006b-11c5-439c-af01-bc00b919851f
---

# Calculated fields

## Overview

The sms\_optIn field is a required field in the Customer Account schema. The issue is that sms\_optIn field in our streaming source can send *null* values, so a calculated field is needed to address that; otherwise these records are skipped from ingestion, which is a loss. 

![The consents.marketing.sms.val field as shown in the target schema](assets/calculated-fields-consents-marketing-sms-val-schema-field.png "consents.marketing.sms.val field as shown in the schema")



## Create calculated field

1. Create a calculated field by clicking **New field type** icon and then select **Add Calculated Field**. For all missing values, consent is assumed to be not given and is marked as **"n"**. Note that calculated fields appear in the left column as the transformation via calculated field is the input to this new mapping. 

![New field type icon menu with Add Calculated Field option selected](assets/calculated-fields-add-a-calculated-field.png "Add a calculated field")



1. In the Create Calculated field dialog box add the following expression and then click **Preview**

```none
iif(sms_optIn == null or sms_optIn == "", 'n', sms_optIn)
```

![Create Calculated Field dialog with the sms_optIn expression and Preview result](assets/calculated-fields-sms-optin-calculated-field.png "sms_optIn calculated field")



1. You should see a green checkmark in the top right corner of the black box indicating the validity of the expression and the data Preview should only show **“n”** or **“y”** as values. If everything looks good click **Save**.



## Map to target

A new field is added to the mapping screen but with an unmapped target field path.

![New sms_optin calculated field added to the mapping screen with an unmapped target field](assets/calculated-fields-sms-optin-unmapped.png "sms_optin unmapped")

1. Click on the **Map target field** for the new calculated field you created
1. In the right pane, you now see the target schema panel open. Type **sms** into the search box
1. Select the **val** field

![Target schema panel with the sms.val field selected for the calculated field mapping](assets/calculated-fields-map-calculated-field-to-target-xdm-field.png)



Your final mapping should look like this:

![Final mapping screen with the sms_optin calculated field mapped to the target schema](assets/calculated-fields-final-mapping-screen.png)



1. Validate your mapping to ensure it looks good

![Validate button confirming the sms_optin mapping is valid](assets/calculated-fields-validate-mappings.png)

>[!NOTE]
>
>Any rows without a valid SMS value are rejected during ingestion. If partial ingestion is not enabled, the ingestion failure with this row fails the ingestion of the entire batch or file in our case. With partial ingestion enabled, the rows with required fields with missing values are rejected but other rows are ingested.



## Handling birthdays

There is a requirement to separate out the birth day, month and year into separate fields so that some of them may not be used in downstream activities. You need to create two calculated fields to resolve this.

### Create mapping for birth day and month

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



1. Click preview and you should see the following result. If everything looks good click **Save**

![Preview result of the birth day and month calculated field expression](assets/calculated-fields-birth-day-month-preview.png)



1. Map the calculated field to **person.birthDayAndMonth**

1. Validate your mapping



### Create mapping for birth year

1. Create a new calculated field to capture the birth year of the profile using the code below

```none
date_part("yyyy",date(birth_Date,"M/d/yyyy"))
```

1. Map the calculated field to the target location of **person.birthYear**

1. Validate your mapping

>[!NOTE]
>
>Observe that the dates are in **MM/DD/YYYY** format but **birth\_Date** data in the sample is coming as either single or double digits for the day and month. For the **date** function to work, you have to specify the input format of the data such as **M/d/yyyy** so that you can account for 1 to 2 digits for the month and day. Without this date input format specification, the validation of these mappings fails.
