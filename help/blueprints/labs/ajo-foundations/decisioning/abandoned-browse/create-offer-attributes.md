---
hold: true
title: Create Offer Attributes
description: Create Offer Attributes
doc-type: article

solution: Experience Platform
exl-id: 00326a7c-8139-46f5-85bd-5ea1f63f29cf
---

# Objective

In this section, you'll add custom XDM fields to the standard Offer XDM schema. These custom fields can be used in ranking, sorting, and eligibility criteria. They can also be data that is returned to the requesting device.  

## Create Custom Device Parent Object

1. Expand the **Decisioning** menu item in the left rail if necessary and click **Catalogs.**
1. By default, the 'Offers' page is shown. Click the **Edit schema** button in the upper-right corner.

![Navigate to edit offers schema](assets/create-offer-attributes-3.png)

>[!TIP]
>
>The resulting page is the standard XDM Schema editor. Just as XDM is used to define the data structure of datasets, XDM is used here to define the attributes of an offer. 

>[!NOTE]
>
>The 'Personalized Offer Items - Experience Decisioning' schema is a system-generated standard schema that applies to all offers. However, one can add to this schema to meet unique business needs, which is what you'll do in this section.
>
>Additionally, going through the offers page is a shortcut for getting to this schema. You could also navigate to it via the Schema menu in the left rail.

1. Click the **+** icon to the right of the root level of the schema, and using the now visible 'Field Properties' menu in the right rail, fill in the following fields with the provided values:
   -  Field name:  **device**
   -  Display name: **Device**
   - Type dropdown: **Object**
   - Assign to Field Group (type this value in): **Offer Details**

>[!NOTE]
>
>The Assign to Field Group appears to be a dropdown, but it also accepts direct text input; therefore, enter the text 'Offer Details'. When you type it in, you'll see an 'Offer Details (New)' item appear as well. Any new attribute has to be assigned to a field group, so in this step, you're effectively creating a new field group called Offer Details.

1. Ensure that all of the properties have been filled out like the screenshot below:

![Create Device Schema](assets/create-offer-attributes-1.png)

1. Once you've verified that all the fields are correct, click the blue **Apply** button at the bottom of the 'Field properties' menu (right rail) to see your changes applied to the schema:

![Device schema created](assets/create-offer-attributes-4.png)

>[!TIP]
>
>Just like normal XDM, the custom attributes are grouped under a namespace specific to the IMS organization, namely the imsorg tenant ID or 'dep' in this case. You'll also see that the new 'Offer Details' field group is now listed in the 'Composition' pane, left of the schema.

>[!WARNING]
>
>Note that these changes are NOT saved....they are just 'Applied.' If you were to navigate away from the page without saving, you would lose your work. Finish out the steps in this section before navigating away. 

## Create Custom Device Attributes

Now that the Device XDM object has been created, you can move on to creating device-specific fields. 

1. Click the **+** icon to the right of the new **device** object that you just created, and using the 'Field Properties' menu in the right rail, fill in the following fields with the provided values:
   -  Field name:  **make**
   -  Display name: **Make**
   - Type dropdown: **String**
   - Assign to Field Group: **Offer Details **(should already be selected)
   - Once you've verified that all the fields are correct, click the blue **Apply** button to see your changes applied to the schema
1. Repeat the previous steps to add two additional attributes for **Model** and **Tier**. Use the same naming pattern, type, and field group. When finished, the schema should look like this:

![Full offers schema validation](assets/create-offer-attributes-2.png)

1. With all of the new XDM fields/attributes created, click **Save** in the upper right corner and you will receive a green "Schema Successfully Saved" message at the bottom of the screen. You've now completed the steps in this section. 

>[!WARNING]
>
>The schema that you just updated applies to ALL offers, including all future offers. Great care should be taken when adding attributes to this schema. In our example use case of a telecom company that sells cell phones, the device make, model, and tier attributes will likely be widely used for many offers and for years to come, so it makes sense to add them. When thinking about which attributes are necessary for an offer, avoid adding attributes that are unique to a specific campaign. Over months or years, this schema can get bloated and cause issues when creating offers. You'll see how this applies in the section where you will create offers.  

## Recap

You’ve successfully updated the standard offers schema with reusable custom fields that will be leveraged in later parts of the lab when creating and evaluating offers.
