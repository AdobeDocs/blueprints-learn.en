---
title: Model Standard Objects
description: Create an Individual Profile schema in the UI and add and trim standard field groups like Demographic Details and Consent and Preferences.
doc-type: article
solution: Experience Platform
exl-id: ea516c0b-3644-483c-a167-0264cc795449
---

# Model Standard Objects

## Navigate to Schemas

1. Click on the **Schemas** tab in the left rail 

![Screenshot 2024 08 21 at 115837 am.png "Navigate to schema's using the left rail"](assets/dp4dF6p7wXRlQA-5wCAaS_screenshot-2024-08-21-at-115837-am.png "Navigate to schema's using the left rail")



2\. In the top navigation you'll see options to browse existing schemas as well as view Field Groups and Data Types that are currently in the XDM registry. 

![LxxLyKc0x1oi JMI9DL6pU0d7i mpjkn68 20241015 163104.png "Browse Schemas Top Nav"](assets/n-ADAXZy_lxxLyKc0x1oi-JMI9DL6pU0d7i_mpjkn68-20241015-163104.png "Browse Schemas Top Nav")

>[!NOTE]
>
>You'll notice there are already schemas that are pre-created in your sandbox. These include schemas that were pre-created as part of this bootcamp (they are prefixed with `dep`), as well as system generated schemas for both Adobe Real-Time CDP and Adobe Journey Optimizer.


## Create Individual Profile Schema

1. Start by clicking **Create schema**

![LxxLyKc0x1oi L10hklwjy4DGNKr0wxCTi 20241023 192024.png "Create Schema"](assets/n-ADAXZy_lxxLyKc0x1oi-L10hklwjy4DGNKr0wxCTi-20241023-192024.png "Create Schema")



2\. Select **Manual**

![LxxLyKc0x1oi MFI xwK2zsS9VlpyaI3bb 20241015 171452.png "Select Manual"](assets/n-ADAXZy_lxxLyKc0x1oi-MFI_xwK2zsS9VlpyaI3bb-20241015-171452.png "Select Manual")

   

3\. Select **Individual Profile**

![LxxLyKc0x1oi DTjcQHkahuJAj5qJNfxSU 20241015 171621.png "Select the Individual ProfileClass"](assets/n-ADAXZy_lxxLyKc0x1oi-DTjcQHkahuJAj5qJNfxSU-20241015-171621.png "Select the Individual ProfileClass")


## Name Your Schema

The XDM Individual Profile class-based schemas allow you to collect attributes about an individual that will be stitched to the profile. The class itself contains fields that are not editable such as *modifiedByBatchID*, *PersonID, *etc.

1. Give your schema a name and description.
   - **Schema Display Name** --> *Customer Account – \[Your Initials]*
   - **Description** --> This schema collects identities, plan information, demographic details, and contact details of an individual.
1. Save your schema using the **Finish** button on the top right.

![LxxLyKc0x1oi gtXbXC9YmkNoXPg8zZRpK 20241016 221431.png "Name your schema, add a description and save"](assets/n-ADAXZy_lxxLyKc0x1oi-gtXbXC9YmkNoXPg8zZRpK-20241016-221431.png "Name your schema, add a description and save")

## Add Demographic Details Field Group

There are many field groups that exist as standard XDM in Adobe Experience Platform for you to add to your schema and customize. 

1. Click the **+ (add)** on the left rail in the field group section.

![LxxLyKc0x1oi bw8fF S9zPaMNjlVx0QYV 20241016 221520.png "Add a field group"](assets/n-ADAXZy_lxxLyKc0x1oi-bw8fF-S9zPaMNjlVx0QYV-20241016-221520.png "Add a field group")

   

2\. Search for **Demographic Details**, or find it by browsing the list. 

- When you find the field group click on the magnify class to the right of the field group to view it's structure.  This is a useful way to preview what you are about to add to your schema without actually adding it.
- Close the preview when done reviewing



![Click the magnify glass to preview the field group s structure.png "Click the magnify glass to preview the Field Group's structure"](assets/KJQ055zCSdfqVr7v6Ukrw_click-the-magnify-glass-to-preview-the-field-group-s-structure.png "Click the magnify glass to preview the Field Group's structure")

![H7CY02IqWCtDJ2cAp image](assets/model-standard-objects-2.png)



3. **Check** the checkbox next to the field group and then click the **Add field groups** button

![CI7x59vlID select the demographic details field group to add it to your schema.png "Select the Demographic Details field group to add it to your schema"](assets/VilL6gza4x_cI7x59vlID_select-the-demographic-details-field-group-to-add-it-to-your-schema.png "Select the Demographic Details field group to add it to your schema")


## Add Other Standard Field Groups

You need to add additional standard field groups to your schema. Repeat the previous steps to add the two additional field groups to your schema:

- Personal Contact Details
- Consent and Preference Details

When you are done your schema should look like the below image when done. Be sure to click the **Save** button and save your work!

![LxxLyKc0x1oi QRbFFB75AEpQm68tKUWAG 20241016 221613.png "Final schema after saving "](assets/n-ADAXZy_lxxLyKc0x1oi-QRbFFB75AEpQm68tKUWAG-20241016-221613.png "Final schema after saving ")

>[!NOTE]
>
>Notice that that the field groups you selected and added now appear in your schema and display in the left rail. Note that not all the fields in each field group you added is necessarily needed.  We will remove the extraneous fields in the next step.

>[!WARNING]
>
>Be sure to save your schema before continuing!


## Customize Standard Field Groups

### Demographic Details Field Group

The Demographic Details field group brought in many fields, but based on your schema design from the LID methodology, you only need the following fields:

- person.name.firstName
- person.name.lastName
- person.birthDayAndMonth
- person.birthYear

To remove fields from any Adobe standard field group you can utilize the **Manage related fields** option. Manage related fields allows you to remove standard fields from your schema, so you are only left with the fields you need.

1. Select the **person** object in your schema
1. Click on the **Manage related fields** in the right rail

![LxxLyKc0x1oi J5leT3fIRHIRRYH8wb2gO 20241016 221734.png "Manage related fields for the person object as part of the Demographic Details field group"](assets/n-ADAXZy_lxxLyKc0x1oi-J5leT3fIRHIRRYH8wb2gO-20241016-221734.png "Manage related fields for the person object as part of the Demographic Details field group")

   

3\. Expand the person object by clicking the chevron to the left of person and expand the full name object by clicking the chevron to the left of the name object. Keep only the following fields:

- person.name.firstName
- person.name.lastName
- person.birthDayAndMonth
- person.birthYear

When you are done click the **Confirm** button in the upper right corner.

![Manage related fields of the demographic details person object.png "Manage related fields of the Demographic Details person object"](assets/BqBDS5LFZEx1TUrB7kFXp_manage-related-fields-of-the-demographic-details-person-object.png "Manage related fields of the Demographic Details person object")

>[!NOTE]
>
>You can click the top-most checkbox for **Demographic Details** to auto-deselect all child objects and then reselect only those that you need!



4\. When done you should see the person object in your schema as shown below. If everything looks good click the **Save** button to save your schema.

![LxxLyKc0x1oi oVEbeSpd7jIJ zTTmfnpx 20241016 221837.png "Final Demographic Details field group with only necessary fields"](assets/n-ADAXZy_lxxLyKc0x1oi-oVEbeSpd7jIJ-zTTmfnpx-20241016-221837.png "Final Demographic Details field group with only necessary fields")

### Consent and Preferences Field Group

Let's perform the same set of steps as you did previously but this time for the Consent and Preferences field group.

1. Click on the **Consent and Preferences** field group name in the left rail to highlight its fields in your schema.
1. Select the **consents** object and then use the **Manage related fields** process to remove fields not needed from the consent object. Keep only the following fields:

- consents.marketing.email.val
- consents.marketing.sms.val

>[!NOTE]
>
>Ensure that you have the toggle turned off for **Show display names for fields** in the upper right corner of the schema workspace
>
>![Image](assets/model-standard-objects-1.png)



When you are done your final schema should now look like this.  Be sure to click **Save** before continuing on.

![LxxLyKc0x1oi 3gMYIMGDD73oDZrBJuhvW 20241016 222219.png "Managed related fields for the Consent and Preferences field group"](assets/n-ADAXZy_lxxLyKc0x1oi-3gMYIMGDD73oDZrBJuhvW-20241016-222219.png "Managed related fields for the Consent and Preferences field group")

>[!TIP]
>
>You are now finished with adding standard components to your schema. Great job! Let’s move on to building some custom attributes for your schema.
