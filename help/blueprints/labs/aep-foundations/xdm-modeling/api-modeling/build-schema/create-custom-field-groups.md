---
hold: true
title: Create Custom Field Groups
description: Create Custom Field Groups
doc-type: article
solution: Experience Platform
exl-id: d3262db9-7c0b-476a-843f-1a2c224ee792
---

# Field Group Structure

A field group is always composed of the following fields. You will see this in the request in the next step.

| Required Values             | Description                                                                                                                                                                                    |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| title                       | The name of the field group you wish to create within the schema registry. Note the name MUST BE UNIQUE.                                                                                       |
| description                 | A short description about the purpose of the field group                                                                                                                                       |
| type                        | Always an object                                                                                                                                                                               |
| meta\:intendedToExtend      | Defines what classes the field group can be used with. Classes are always referenced by their `$id` value                                                                                      |
| allOf                       | Describes the resources that be included in the field group. For custom defined fields the path is always `#/defintions/customFields`                                                          |
| definitions.customFields... | This is the default JSON schema structure required to create custom field groups. It must match the `allOf` from above                                                                         |
| \<TENANT\_NAME>             | The tenant name (i.e. unique name) is created during the provisioning process. This ensures that any customizations made do not conflict with existing or future Adobe schema registry changes |



## Create Customer Account Details Field Group

1. Click on the request `Step 2 - Create Customer Account Details Field Group` API call in the X`DM Schema Lab -> Create Schema` Folder



![Step 2 create customer account details field group.png "Step 2   Create Customer Account Details Field Group"](assets/tYs9Qb2oGMD1y7dre2qti_step-2-create-customer-account-details-field-group.png "Step 2 - Create Customer Account Details Field Group")



Review the body of the request before executing. Notice that the required fields mentioned in the Field Group Structure section appear like so:

![Field group structure.png "Field Group Structure"](assets/JunXRjZEj6VjNnbxqMMGN_field-group-structure.png "Field Group Structure")



![Image.png "Field Group Structure allOf"](assets/KheXEhm58SN9sqK2SoEWl_image.png "Field Group Structure allOf")

>[!NOTE]
>
>Notice how in the image on the right above the `allOf` references the path of "/definitions/customFields".  That must match the structure defined in the schema (image on the left) as it tells the XDM system where to locate custom created objects.
>
>![Notice how in the image](assets/Dd1Qd1xfqGgX3ixQxmzhN_notice-how-in-the-image.png)



Also notice how each specific field from the mapping sheet is substantiated within the XDM JSON structure. 



![Plan dot notation to xdm json.png "Plan Dot Notation to XDM JSON"](assets/xq7x73qvAhSgn4Q8gyPGD_plan-dot-notation-to-xdm-json.png "Plan Dot Notation to XDM JSON")



![MUq lfv f4oH account customer id dot notation to xdm.png "Account & Customer ID Dot Notation to XDM"](assets/OE6ta7H0_mUq-lfv-f4oH_account-customer-id-dot-notation-to-xdm.png "Account & Customer ID Dot Notation to XDM")



2\. Update the `title` and `description` for the field group using the following format: `Customer Account Details - Sandbox <your number here>`



![Field group title description example.png "Field Group Title & Description Example"](assets/U6X0D63-U7DQuVdwgis4t_field-group-title-description-example.png "Field Group Title & Description Example")



3\. Execute by clicking the `Send` button.  You should see a response similar to the screenshot below.

4\. Copy the `$id` value of your newly created Customer Account Details field group. 

![W Kc0bsy9B2TC step 2 create custom field group success.png "Step 2   Create Custom Field Group Success"](assets/hso24TH_W-Kc0bsy9B2TC_step-2-create-custom-field-group-success.png "Step 2 - Create Custom Field Group Success")

>[!WARNING]
>
>Do not continue until you have saved the `$id` somewhere.  It will be required later to create the Customer Account schema
>
>

