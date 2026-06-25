---
title: Model Custom Objects
description: Model Custom Objects
doc-type: article
exl-id: 8c39b226-05f3-458a-b023-c59221a6713a
---

# Adding Custom Fields

As discussed in the lecture, there are no standard out of the box field groups or data types that model the Customer Account custom fields.  The below fields currently are considered custom and must be modeled within the XDM schema.

- \_\<tenant-name>.account.createDate
- \_\<tenant-name>.account.endDate
- \_\<tenant-name>.account.acqSource
- \_\<tenant-name>.plan.planID
- \_\<tenant-name>.plan.name
- \_\<tenant-name>.customerID

>[!NOTE]
>Note the \<tenant-name> will be specific to the environment you are working in



# Account Object Creation

1. Add a new field by clicking the **+ (add)** button at the top of your schema

![](assets/pgslWRDmjJ9ZwQgaymLb6_add-a-custom-field-to-your-schema.png)

>[!NOTE]
>Notice the right rail opens with some fields for you to fill out

 

2\. Create the account object by utilizing the below details. When done click the **Apply **button in the right rail to see the change in the schema workspace

| Field Name | Display Name | Type     | Assign to a New Field Group                                                                                                   |
| ---------- | ------------ | -------- | ----------------------------------------------------------------------------------------------------------------------------- |
| *account*  | *Account*    | *Object* | *Customer Account Details - \[Your Initials] *<br />*(you’ll need to type this in and select the dropdown or hit enter)* |

>[!WARNING]
>Your field names need to follow a specific casing. The reason is because we have already pre-created the same schema you are building. If your casing is off, it will cause a conflict with the field paths from the pre-existing schema in your sandbox

![](assets/qaM2eAV0vOinxJYBeKVvu_adding-the-account-object.png "Adding the account object")

>[!NOTE]
>Notice the custom field you created automatically is placed under a tenant namespace, denoted by `_devbc`in the screenshot. Your tenant namespace may be different. Tenant namespaces are used to differentiate custom objects from Adobe standard ones and ensure future additions/updates to Adobe standards do not conflict with custom create ones.

>[!NOTE]
>Notice that your new custom field group appears in the left rail under the `Field groups` without a lock icon.  This denotes its a custom created field group.

>[!WARNING]
>You cannot save your schema at this point. If you do an error will occur because you cannot create an empty object in JSON schema as it does not describe what its contents are


 

3\. Add the following fields show below under the Account object you just created.

| Field Name   | Display Name  | Type       |
| ------------ | ------------- | ---------- |
| *createDate* | *Create Date* | *DateTime* |
| *endDate*    | *End Date*    | *DateTime* |

>[!NOTE]
>You'll notice while adding the new fields the **Assign to **option is already filled in and references the field group you used for the account object.



4\. When done your schemas account object should look like below. **Save **your schema!



![Customer Account Schema with account object and child fields added](assets/yS-U6AJJ5e59_RNB2xVhT_customer-account-schema-with-account-object-and-child-fields-added.png)

 

5\. Add one more custom field to the account object. Click the  **+ (add)** button next to the account object.  You will create the following field:

| Field Name  | Display Name      | Type     | Enumerations                            |
| ----------- | ----------------- | -------- | --------------------------------------- |
| *acqSource* | *Acquired Source* | S*tring* | *web :: Web*<br />*inStore :: In Store* |

For this field we want to standardize the values so we will use the **Enum & Suggested values** option within the fields properties. Select **Enum **radio button to add validation for this field at ingestion, as well as friendly labels. Add the enum values as shown below:

- *web :: Web*
- *inStore :: In Store*



![Enum values for Acquisition Source field](assets/ijhlDIXR50hV4xkD09ajV_enum-values-for-acquisition-source-field.png)

>[!NOTE]
>The goal of Enum & Suggested values is make segmentation easier for the end user. Enums enforce validation at time of data ingestion whereas Suggested values do not. To learn more about this feature you can read more in the documentation here -> [https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/fields/enum.html?lang=en#enums-and-suggested-values](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/fields/enum.html?lang=en#enums-and-suggested-values)

 

6\. When done click the **Apply **button to add the new field to the schema.

7\.  **Save **your schema

>[!TIP]
>You have successfully created your first custom object and fields within the XDM schema registry!



# Plan Object Creation

Repeat the steps you performed above and add the **Plan **object and associated fields. All new fields should be added under the Customer Account Details - \[your initials] field group.

Use the metadata in the below table to create the plan object and its associated fields.

| Field Name | Display Name   | Type     | Enum & Suggested Values                                                               |
| ---------- | -------------- | -------- | ------------------------------------------------------------------------------------- |
| *plan*     | *Plan Details* | *Object* | -                                                                                     |
| *planID*   | *Plan ID*      | *String* | -                                                                                     |
| *name*     | *Plan Name*    | *String* | Enum <br />*basic :: Basic *<br />*ultimate :: Ultimate *<br />*pro :: Pro* |
| type       | Type           | String   | -                                                                                     |

>[!WARNING]
>Ensure that you are adding the new fields you create to the Customer Account Details - \[your initials] field group.  A quick way to ensure they are auto-added to that field group is to select the field group in the left rail before adding a custom field.
>
>
>
![](assets/TkHbqFVcmIr3hBMbbuFWJ_ensure-that-you-are-adding-the-new-fieldds.png)
>
>



When done validate your schema matches the below screenshot. If it looks good **Save **your schema



![Customer Account schema with plan object and child fields added](assets/Zot1l5H5nP9lisRK7Dmh4_customer-account-schema-with-plan-object-and-child-fields-added.png)

>[!TIP]
>Nice!  You added your own custom object and fields with no help!



# **Customer ID Field Creation**

Adding the **customerID **field as this field is critical because it will serve as the primary identity for the schema as well as a general field to hold data in.

Perform the same steps as you have done previously and utilize the table below for referencing the metadata for the field.

| Field Name   | Display Name  | Type     | Field Group                                   |
| ------------ | ------------- | -------- | --------------------------------------------- |
| *customerID* | *Customer ID* | *String* | *Customer Account Details - \[Your Initials]* |

>[!NOTE]
>The `customerID`could be put anywhere in the schema from a hierarchical perspective. In this lab we've chosen to keep it at the root and not nested within one of the custom objects you previously created.  This is where data architecture has opinions 
>
>😄



Your final result should look like the screenshot below when you are complete

![Customer Account schema with customerId field added](assets/tMtdEzbWNTwqE1z0DLAhj_customer-account-schema-with-customerid-field-added.png)



# Final Schema Result



![](assets/_9i_fEemrUwm44IXGMVf9_final-schema-with-custom-objects.jpeg "Final schema with custom objects")

>[!TIP]
>You have built your first XDM schema! In the next section you will configure the schema for use with the Real-Time Customer Profile.

