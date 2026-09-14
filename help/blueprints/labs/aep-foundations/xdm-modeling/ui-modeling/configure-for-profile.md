---
title: Configure for profile
description: Mark primary and person identity fields, build a schema relationship, enable a schema for Real-Time Customer Profile, and review the profile union schema.
doc-type: article
solution: Experience Platform
exl-id: 52cfc0d2-ba8c-4f81-9e03-c5c2c5e276b7
---

# Configure for profile

## Overview

To utilize a schema for the Real-Time Customer Profile, you first need to ensure it's configured appropriately. This step means taking what you identified during the LID lab as primary/person identities, relationship identities, etc. and ensuring those configurations are made to each schema. When everything is done, you enable a schema for use with profile.

Looking at the XDM on paper Connection 5G ERD, you see the following information about the Customer Account schema.  This is the work that remains to utilize the schema within the Real-Time Customer Profile.



![Connection 5G XDM on Paper Customer Account schema and its associated lookup table](assets/configure-for-profile-connection-5g-erd-customer-account-schema.jpeg "Connection 5G XDM on Paper Customer Account schema and its associated lookup table")


## Mark the primary identity field

Every schema requires a primary identity field if it's to be used with the Real-Time Customer Profile. To mark a field as a primary identity, follow the steps below.

1. Open the **Customer Account** schema you created
1. Select the **\_\<tenant-name>.customerID** field by clicking on the field in the schema
1. In the right rail check both the **Identity** and **Primary identity** checkboxes
1. Select the **customerID** namespace from the dropdown
1. When done click the **Apply** button in the right rail and then **Save** your changes. 

![Marking the customerID field as a Primary Identity](assets/configure-for-profile-mark-customerid-as-primary-identity.png "Marking _dxp.customerID as a Primary Identity")

>[!NOTE]
>
>Validate that a thumbprint shows on your field after you click apply like below
>
>![Thumbprint icon shown on the field after marking it as an identity](assets/configure-for-profile-identity-thumbprint-icon.png)
>
>

>[!NOTE]
>
>Also note that in the left rail you now see the following items. Identities (primary or non-primary) appear here, and **primary** identities are also marked as required fields.
>
>
>
>![Identities section in the left rail showing primary and non-primary identity fields](assets/configure-for-profile-identities-list-in-left-rail.png)



## Mark the person identity field(s)

Every schema can **optionally contain** other person identity fields. This rule applies to any schema used with the Real-Time Customer Profile. To mark a field as a person identity, perform the following actions on the Customer Account schema you created previously.

1. Select the **personalEmail.address** field
1. Check the **Identity** checkbox found in the right rail
1. Select the **Email** identity namespace from the dropdown
1. **Apply & Save** your changes

![Marking the personalEmail.address field as an identity](assets/configure-for-profile-mark-personal-email-as-identity.png "Marking the personalEmail.address as an identity")

>[!NOTE]
>
>Validate that a thumbprint shows on your field after you click apply



## Create the schema relationship

To relate the Plan schema to the Customer Account schema as outlined in the ERD, you need to define a relationship. To create a schema relationship between the Customer Account and Plan (lookup) schemas, follow the steps below.

### Add relationship

1. Select the **planID** field within the Plan object as shown below
1. In the right rail click on the **Add relationship** icon

![Add relationship icon selected on the planID field](assets/configure-for-profile-add-relationship-to-planid-field.png "Add relationship to the planID field")



### Define relationship

1. In the Type select box select the **One-to-one** option
1. In the Reference schema select box choose the schema named **dep: Plan \[Lookup]** (this schema was pre-created for you)
1. Click **Apply** and **Save**

![Defining a one-to-one relationship to the dep: Plan [Lookup] schema](assets/configure-for-profile-define-one-to-one-relationship.png)



### Confirm relationship

When you are done you should see the relationship you created display as seen in the screenshot below.

![Confirmation that the relationship between Customer Account and Plan schemas was created](assets/configure-for-profile-relationship-created-confirmation.png "Relationship created")



## Configure schema for profile

The Real-Time Customer Profile merges data from disparate sources to construct a complete view of each individual customer. If you want the data captured by a schema to participate in this process, you must configure the schema for use in Profile. To do so you need to perform the following steps:



1. Open your newly created **Customer Account - \[your initials]** schema
1. Click on the title of your schema from within the left rail
1. Configure your schema for profile by toggling **ON** the Profile toggle in the right rail
1. In the modal that appears click on the **Enable** button
1. Don't forget to **Save** your schema when you are done!

![Profile toggle enabled in the right rail for the Customer Account schema](assets/configure-for-profile-schema-profile-toggle.png "Schema Profile Toggle")

![Enable button in the modal that appears after toggling the Profile switch](assets/configure-for-profile-enable-profile-modal.png)

>[!SUCCESS]
>
>Congratulations!  You just created a schema to use with the Real-Time Customer Profile.



## Review the profile union schema

As mentioned previously the power of XDM + the Real-Time Customer Profile is the ability to assemble a variety of fragments of an individual and their behaviors together.  This aggregation is referred to as the "Union View" of the customer.  In the steps below, you preview what this union looks like for each XDM class that is configured for the Real-Time Customer Profile

1. Navigate to **Profiles** in the left rail
1. Select the **Union Schema** tab on the top menu
1. Select the **XDM Individual Profile** class from the dropdown

Browse the XDM Individual Profile class and then take a few moments to review other classes such as XDM ExperienceEvent or Plan classes.

![Profile Union Schema view for the XDM Individual Profile class](assets/configure-for-profile-profile-union-schema-view.png "Profile Union Schema View")

>[!NOTE]
>
>Notice the schema shown is an aggregate merged view of all profile-enabled schemas in your sandbox. Similar fields within the hierarchal XDM structure merge together, whereas fields with different names and/or hierarchies are added to the overall view.

>[!NOTE]
>
>Only the XDM Individual Profile-based class performs merges between similarly named fields.
