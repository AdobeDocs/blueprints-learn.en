---
hold: true
title: Fix passthrough mappings
description: Identify and correct incorrect AI/ML passthrough mappings, such as duplicate or mismatched target field assignments, before validating.
doc-type: article
solution: Experience Platform
exl-id: b06cc091-661e-4ff4-b6e5-f16bc5128b6b
---

# Fix passthrough mappings

## Drop specific mappings

Some of the source data that you have needs to be handled using calculated fields.  To address these, drop them from the mappings and re-validate the mappings.

1. Drop the following source data from the mappings:
   - birth\_date
   - source
   - sms\_optIn
1. Re-validate the mappings by clicking on the validate button

![Validate button used to re-validate mappings after dropping fields](assets/fix-passthrough-mappings-re-validate-mappings-using-validate-button.png "Re-validate mappings using the validate button")

>[!NOTE]
>
>After clicking the Validate you may still have errors present



## Wrong mapping examples

While AI/ML recommendations are helpful they are sometimes wrong.  If you inspect your recommendations you may find these type of errors that you need to fix

>[!NOTE]
>
>Below are some examples of invalid mappings that you may see in your own sandbox. You may also see others errors.

## Duplicate mappings

In this scenario you see that the AI/ML recommender mapped two different source fields to the same target field **person.name.lastName**



![Two different source fields mapped to the same target field person.name.lastName](assets/fix-passthrough-mappings-person-lastname-mapped-twice.png "person.name.lastName is mapped to twice in this mapping")

![Duplicate passthrough mapping example involving the plan_name field](assets/fix-passthrough-mappings-plan-name-duplicate-mapping.png)



## Bad mappings

This mapping looks right but upon closer inspection **email** is not the same as **emailFormat**

![Mapping where email is incorrectly mapped instead of emailFormat](assets/fix-passthrough-mappings-email-mapped-incorrectly.png "email seems to be mapped correctly but is incorrect as per requirements")

And this one where **email\_optIn** is incorrectly mapping to the wrong consent object

![email_optIn incorrectly mapped to the wrong consent object](assets/fix-passthrough-mappings-email-optin-wrong-consent-object.png "email_optIn seems to be mapped correctly but is incorrect as per requirements")



## Fixing passthrough mappings

To fix passthrough mappings that are incorrectly pointing to the wrong target field, perform the following steps.

### Example

1. Start with an invalid mapping and click on the target field box. For example, in the mapping below, the field **person.name.lastName** is not mapped correctly and is mapped to **planName**
1. In the target schema panel that opens on the right, choose the appropriate target field and select **\_devbc.plan.name**
1. The target field should now be updated in the target field box
1. After you fix each such error, you should press the **Validate** button so that you can make sure you are reducing these kinds of errors and not introducing new ones. 



![Working through the mapping list to fix each mapping error](assets/fix-passthrough-mappings-work-through-mapping-errors.png "Work your way through the mapping and fixing the mapping errors")



![Target schema panel for selecting the correct field to fix a passthrough mapping](assets/fix-passthrough-mappings-choose-correct-target-field.png "Choose the right target field and verify that it matches the passthrough requirements")

>[!WARNING]
>
>Do not continue to the next step until you have resolved all your mapping errors
