---
title: Modify Schema - JSON Patch
description: Use a JSON PATCH API call to add a new field to an existing tenant field group and see the change reflected in the schema.
doc-type: article
solution: Experience Platform
exl-id: c0313594-d998-4525-a0a4-d9d844bed5ef
---

# Modify Schema - JSON Patch

## Overview

Assume for a minute that after building the schema you need to come back and add an additional field to the `plan` object called `planDescription` because either you forgot to add it at time of creation or it was a request that came in months later.  To perform this task you can simply perform a `PATCH` operation which updates the schema with the new field.

You can learn more about JSON PATCH at the links below, but for the purposes of this lab, assume you have some concept of how this works 😄

- [https://jsonpatch.com/](https://jsonpatch.com/)
- [Experience League API Fundamentals](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-fundamentals.html?lang=en#json-patch)

![Diagram of patching a missing planDescription field into an existing schema](assets/modify-schema-json-patch-patching-missing-plan-description-field.png "Patching in a Missing Field Plan Description")

>[!NOTE]
>
>Remember the following points:
>
>- A schema is composed of one (1) class and one (1) or more field groups
>- You cannot add new fields directly to a schema without first adding to a field group. This ensures re-usability of a field across any schema that utilizes that field group.



To add a new field to a schema you need to perform the following operations in order.  This is what you do in the following lab steps.

- Identify the field group where you would like to add the new property
- Construct a JSON PATCH call to update the field group
- Execute the JSON PATCH call to update the Field group (which the schema will inherit)



## Locate & identify the field group to update

1. Select the `Step 1 - Get Tenant Field groups` API call located in the `XDM Schema Lab -> Customize Schema` folder 
1. Execute the request by clicking the `Send` button

   ![Step 1 - Get Tenant Field Groups API request](assets/modify-schema-json-patch-step-1-get-tenant-field-groups.png "Step 1 - Get Tenant Field Groups")

   >[!NOTE]
   >
   >Remember that you created the `plan` object within a custom field group. Custom created objects in the XDM schema registry are referred to as "tenant" hence the API call utilizing the `/schemaregistry/tenant/mixins/` path.



1. In the response search for the schema ID for the custom field group you created previously titled `Customer Account Details - Sandbox <your number here> `

1. Copy the `$meta:altId` and save it somewhere safe as you will need it for the next step

![Locating the custom Customer Account Details field group in the API response](assets/modify-schema-json-patch-search-field-group-response.jpeg "Search the response for the Customer Account Details Field Group")

>[!CAUTION]
>
>Ensure you select the right field group to copy!  There is one that is named similarly called `dep: Customer Account Details` that you should **not** use

>[!WARNING]
>
>Do not continue until you have saved the `$meta:altId `somewhere.  It will be required in future lab steps



## Look up the field group by $meta\:altId

1. Select the `Step 2 - Fetch path for the object to be modified` API call in the `XDM Schema Lab -> Customize Schema` folder
1. In the URL of the request replace the `<replace me>` with the `$meta:altId` you saved from the previous section step to the end of the call like shown below
1. Save the edits you've made to the request
1. Execute the request by clicking the `Send` button

![Step 2 - Fetch path for the object to be modified API call](assets/modify-schema-json-patch-step-2-fetch-object-path.jpeg "Step 2 - Fetch path for the object to be modified steps")



Review the response and note the JSON pointer path for the **plan** object is constructed using each of the properties highlighted below.

![Highlighted properties composing the JSON pointer path to the plan object](assets/modify-schema-json-patch-customer-account-details-path-to-the-plan-object.png "Customer Account Details Path to the Plan object")



The fully composed path looks like what you see below.  Copy this path and save somewhere for reference

```none
/definitions/customFields/properties/_devbc/properties/plan/properties
```

>[!NOTE]
>
>Remember to update the tenant name above (\_devbc) with the your own



## PATCH the field group

### JSON PATCH API body sample

```none
[
    {
        "op": "",
        "path": "",
        "value": {
            "title": "",
            "type": "",
            "description": ""
        }
    }
]
```

- **op (Operation)** -> this provides the instruction for what action the PATCH should perform
- **Path** -> this is the path you want to create, update or delete (i.e. this is the JSON pointer to the location of the new field)
- **Value** -> this is an optional field and only used when creating or replacing an existing field



### Execute the API request

1. Click on the `Step 3 - Modify Tenant Field group` API call in the `XDM Schema Lab -> Customize Schema` folder

   ![Step 3 - Modify Tenant Field Group API call](assets/modify-schema-json-patch-step-3-modify-tenant-field-group.png "Step 3 - Modify Tenant Field Group")



2. Update the body of the request with the following information

   - **op** ->` add`
   - **path** -> `path from previous step +`` the new field name`
   - **value** ->
     - **title** -> `Plan Description`
     - **type** -> `string`
     - **description** -> `High-level details about the plan`

   When you are done your API request should look something like this

   ![Completed JSON PATCH request body adding the planDescription field](assets/modify-schema-json-patch-step-3-final-call-example.png "Step 3 - Final Call Example")

   >[!WARNING]
   >
   >Make sure you include the new field name, **planDescription,** in your path



3. If everything looks good `Save` your call

4. `Execute` the call to perform the PATCH

You should see a `200 OK `response and should now see the `planDescription` field in your field group like so:

![200 OK response after successfully patching the field group with planDescription](assets/modify-schema-json-patch-step-3-200-ok-successful-patch.png "Step 3 - 200 OK Successful PATCH")

>[!SUCCESS]
>
>Congratulations! You have successfully updated a field group/schema using JSON PATCH



## View the change in the UI

Browse your Schema through the UI and have a look at your newly added field.  Pretty cool huh?

![Plan Description field visible in the schema after JSON Patch in the Experience Platform UI](assets/modify-schema-json-patch-plan-description-added-to-field-group.png "Plan Description added to the Customer Account Details - Sandbox \<your number> field group. Modify Schema JSON")
