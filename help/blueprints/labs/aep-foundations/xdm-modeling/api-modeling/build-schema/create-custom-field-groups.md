---
title: Create Custom Field Groups
description: Use the schema registry API to create a custom Customer Account Details field group and save its $id for use in a later schema.
doc-type: article
solution: Experience Platform
exl-id: d3262db9-7c0b-476a-843f-1a2c224ee792
---

# Create Custom Field Groups

## Field group structure

A field group is always composed of the following fields. You will see this in the request in the next step.

| Required Values             | Description                                                                                                                                                                                    |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| title                       | The name of the field group you wish to create within the schema registry. Note the name MUST BE UNIQUE.                                                                                       |
| description                 | A short description about the purpose of the field group                                                                                                                                       |
| type                        | Always an object                                                                                                                                                                               |
| meta\:intendedToExtend      | Defines what classes the field group can be used with. Classes are always referenced by their `$id` value                                                                                      |
| allOf                       | Describes the resources that can be included in the field group. For custom defined fields the path is always `#/definitions/customFields`                                                     |
| definitions.customFields... | This is the default JSON schema structure required to create custom field groups. It must match the `allOf` from above                                                                         |
| \<TENANT\_NAME>             | The tenant name (i.e. unique name) is created during the provisioning process. This ensures that any customizations made do not conflict with existing or future Adobe schema registry changes |



## Create Customer Account Details field group

1. Click on the request `Step 2 - Create Customer Account Details Field Group` API call in the `XDM Schema Lab -> Create Schema` folder



![Step 2 - Create Customer Account Details Field Group API request](assets/create-custom-field-groups-step-2-field-group-request.png "Step 2 - Create Customer Account Details Field Group")



Review the body of the request before executing. Notice that the required fields mentioned in the Field Group Structure section appear like so:

![Required fields of a custom field group as shown in the request body](assets/create-custom-field-groups-field-group-structure.png "Field Group Structure")



![The allOf property referencing the custom field definitions path](assets/create-custom-field-groups-field-group-structure-allof.png "Field Group Structure allOf")

>[!NOTE]
>
>Notice how in the image on the right above the `allOf` references the path of "/definitions/customFields".  That must match the structure defined in the schema (image on the left) as it tells the XDM system where to locate custom created objects.
>
>![Comparison highlighting how the allOf path must match the custom field definitions path](assets/create-custom-field-groups-allof-path-highlighted.png)



Also notice how each specific field from the mapping sheet is substantiated within the XDM JSON structure. 



![Mapping sheet plan dot notation converted to XDM JSON structure](assets/create-custom-field-groups-plan-dot-notation-to-xdm-json.png "Plan Dot Notation to XDM JSON")



![Mapping sheet account and customer ID dot notation converted to XDM](assets/create-custom-field-groups-account-customer-id-dot-notation-to-xdm.png "Account & Customer ID Dot Notation to XDM")



2. Update the `title` and `description` for the field group using the following format: `Customer Account Details - Sandbox <your number here>`



   ![Example title and description filled in for the custom field group](assets/create-custom-field-groups-field-group-title-description-example.png "Field Group Title & Description Example")



3. Execute by clicking the `Send` button.  You should see a response similar to the screenshot below.

4. Copy the `$id` value of your newly created Customer Account Details field group. 

![Successful API response after creating the custom field group](assets/create-custom-field-groups-step-2-create-custom-field-group-success.png "Step 2 - Create Custom Field Group Success")

>[!WARNING]
>
>Do not continue until you have saved the `$id` somewhere.  It will be required later to create the Customer Account schema
>
>
