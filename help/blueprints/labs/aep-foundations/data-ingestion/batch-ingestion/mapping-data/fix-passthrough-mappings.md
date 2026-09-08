---
hold: true
title: Fix Passthrough Mappings
description: Fix Passthrough Mappings
doc-type: article

solution: Experience Platform
exl-id: b06cc091-661e-4ff4-b6e5-f16bc5128b6b
---

# Drop Specific Mappings

Some of the source data that you have will need to handled using calculated fields.  To address these lets drop these from the mappings to and re-validate the mappings.

1. Drop the following source data from the mappings:
   - birth\_date
   - source
   - sms\_optin
1. Re-validate the mappings by clicking on the validate button

![Re validate mappings using the validate button.png "Re validate mappings using the validate button"](assets/3jtwSfa5SDlyVDiYJasg__re-validate-mappings-using-the-validate-button.png "Re-validate mappings using the validate button")

>[!NOTE]
>
>After clicking the Validate you may still have errors present



## Wrong Mapping Examples

While AI/ML recommendations are helpful they are sometimes wrong.  If you inspect your recommendations you may find these type of errors that you need to fix

>[!NOTE]
>
>Below are some examples of invalid mappings that you may see in your own sandbox. You may also see others errors.

## Duplicate Mappings

In this scenario you will see that the AI/ML recommender mapped two different source fields to the same target field **person.name.lastName**



![JS lxJiI fqVvFexXvh3 personnamelastname is mapped to twice in this mapping.png "person.name.lastName is mapped to twice in this mapping"](assets/_jS-lxJiI_fqVvFexXvh3_personnamelastname-is-mapped-to-twice-in-this-mapping.png "person.name.lastName is mapped to twice in this mapping")

![Plan nam](assets/plan-nam.png)



## Bad Mappings

This mapping looks right but upon closer inspection **email **is not the same as **emailFormat**

![Email seems to be mapped correctly but is incorrect as per requirements.png "email seems to be mapped correctly but is incorrect as per requirements"](assets/RfWELh4y6RWlYqzs5N1sW_email-seems-to-be-mapped-correctly-but-is-incorrect-as-per-requirements.png "email seems to be mapped correctly but is incorrect as per requirements")

And this one where **email\_optin **is incorrectly mapping to the wrong consent object

![Email op.png "email optin seems to be mapped correctly but is incorrect as per requirements"](assets/WtXdsgFemj1REbMSd1Nf5_email-op.png "email_optin seems to be mapped correctly but is incorrect as per requirements")



## Fixing Passthrough Mappings

To fix passthrough mappings that are incorrectly pointing to the wrong target field you will need to perform the following steps.

**Example Only**

1. Start with an invalid mapping and click on the target field box. For example, in the mapping below, the field **person.name.lastname **is not mapped correctly and is mapped to **planName**
1. In the target schema that options to the right choose the appropriate target field and select the name field **\_devbc.plan.name**
1. The target field should now be updated in the target field box
1. After you fix each such error, you should press the **Validate **button so that you can make sure you are reducing these kinds of errors and not introducing new ones. 



![QOlgUB work you.png "Work your way through the mapping and fixing the mapping errors"](assets/n2zZLVICZHekRJ_qOlgUB_work-you.png "Work your way through the mapping and fixing the mapping errors")



![Choose t.png "Choose the right target field and verify that it matches the passthrough requirements"](assets/Nq9dUWVzfvCJBn-g3pdLS_choose-t.png "Choose the right target field and verify that it matches the passthrough requirements")

>[!WARNING]
>
>Do not continue to the next step until you have resolved all your mapping errors



