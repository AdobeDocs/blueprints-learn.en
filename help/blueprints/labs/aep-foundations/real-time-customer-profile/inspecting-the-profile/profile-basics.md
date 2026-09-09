---
title: Profile Basics
description: Explore the profile union schema, look up a profile in the UI, and inspect its attributes, identity map, and identity graph relationships.
doc-type: article
solution: Experience Platform
exl-id: 5be38b40-47ef-42ce-8829-39fa09394716
---

# Profile Union Schema

Remember that the view of any Real-Time Customer Profile is built using the schema's you defined and enabled for the profile. This is what Adobe refers to as the Union Schema of the profile.

You can see the Union Schema of the profile by doing the following:

1. Click on **Profiles** in the left rail 
1. Click on **Union Schema** in the top nav

![LxxLyKc0x1oi qkk7x9qYLauRcyynYFt39 20241017 193248.png "Profile Union View"](assets/n-ADAXZy_lxxLyKc0x1oi-qkk7x9qYLauRcyynYFt39-20241017-193248.png "Profile Union View")

>[!NOTE]
>
>Remember that profile creates a union view for every XDM class. You utilize this view to see what schema's contributed to what class, the identities within each class and any relationships.

Review the Union Schema for the XDM Individual Profile class and expand out the tenant namespace. You should see a number of items here that came from various schemas you defined the **LID Methodology** and **XDM Modeling Labs.**

![LxxLyKc0x1oi MxPrIGEZ3ZqdQTysq 3EW 20241017 193926.png "Profile Union Schema view of tenant objects "](assets/n-ADAXZy_lxxLyKc0x1oi-MxPrIGEZ3ZqdQTysq_3EW-20241017-193926.png "Profile Union Schema view of tenant objects ")

Click on the **account** object and notice what appears in the right rail of the screen. You can now see the details around object, what schema(s) and dataset(s) contributed to its formation and other relevant information.

![Profile union schema account object details.png "Profile Union Schema account object details"](assets/TpYFSpH93E4tPQHBD82IF_profile-union-schema-account-object-details.png "Profile Union Schema account object details")

>[!NOTE]
>
>The union schema is a great tool for understanding why certain elements exist within a profile and where they came from. 
>
>Keep in mind that the Union Schema is observable meaning profile will only show fields that contain data when viewing an actual Real-Time Customer Profile


## Profile Lookup

1. Click on **Profiles** in the left rail and then in the top navigation select **Browse**
1. Select the Identity namespace of **Email**
1. Enter the Identity value of **depeche.mode\@dep.com**
1. Click on the **View** button to lookup the profile
1. Click on the **link** to the profile to see the profile's details

![LxxLyKc0x1oi  k AbBvi5cOvsBM8ZaWpm 20241017 200615.png "Profile Viewer (Browse](assets/n-ADAXZy_lxxLyKc0x1oi-_k-AbBvi5cOvsBM8ZaWpm-20241017-200615.png "Profile Viewer (Browse)")



You should see this now!

![LxxLyKc0x1oi dKdxPtp4qU nqTvA57hde 20241017 201202.png "Depeche Mode profile details"](assets/n-ADAXZy_lxxLyKc0x1oi-dKdxPtp4qU_nqTvA57hde-20241017-201202.png "Depeche Mode profile details")

Take a minute to explore the profile, Depeche Mode, by looking at each tab in the top nav. These are the tabs that you will use:

- Detail - displays customize cards that show various aspects for the given profile
- Attributes - displays all the associated attributes for the given profile coming from the union schema
- Events - displays all the associated events for the given profile coming from the union schema
- Audience Membership - displays the audiences that the profile is currently a member of

## View Attributes

Navigate to the **Attributes** tab and click **View JSON**

![LxxLyKc0x1oi Da2kw9BmD5pri1y8C5fGD 20241017 202102.png "Depeche Mode attributes"](assets/n-ADAXZy_lxxLyKc0x1oi-Da2kw9BmD5pri1y8C5fGD-20241017-202102.png "Depeche Mode attributes")

Let’s see how fields show up that came from the Field Groups you added to the Customer Account Schema. 

- Look for the parent node titled **entity**
- Note the child object **billingAddress** (this came from Personal Contact Details Field Group)

```json
"billingAddress": {
  "postalCode": "11355",
  "city": "New York City",
  "state": "NY",
  "street1": "108 Ruskin Terrace"
}
```

Compare this to what the Profile Union Schema has and you should lightbulb on what obserable means 😄

```json
"billingAddress": {
    "_repo": {
        "createDate": "datetime",
        "modifyDate": "datetime",
    },
    "_schema": {
        "description": "string",
        "elevation": "double",
        "latitude": "double",
        "longitude": "double"
    },
    "_id": "string",
    "city": "string",
    "country": "string",
    "countryCode": "string",
    "createdByBatchID": "string",
    "dmaID": "integer",
    "label": "string",
    "lastVerifiedDate": "date",
    "modifiedByBatchID": "string",
    "msaID": "string",
    "postOfficeBox": "string",
    "postalCode": "string",
    "primary": "boolean"
    "region": "string",
    "repositoryCreatedBy": "string",
    "repositoryLastModifiedBy": "string",
    "state": "string",
    "stateProvince": "string",
    "status": "string",
    "statusReason": "string"
    "street1": "string",
    "street2": "string",
    "street3": "string",
    "street4": "string"
}
```

>[!NOTE]
>
>Observable schema literally means to only show the fields where data exists and hide the fields that do not contain data.  Very different then traditional relational database!



Next look for **consents** object (this came from Consent and Preference Details field group)

```json
"consents":{
   "marketing":{
      "sms":{
         "val":"y"
      },
      "email":{
         "val":"y"
      }
   }
}
```



Scroll down to tenant namespace, **\_devbc**, and look for **plan** object (this came from a custom created field group named 'dep: Plan Details')

```json
"plan": {
    "planID": "m3",
    "type": "mobile",
    "name": "pro"
}
```



Notice the **aggregates** object you defined to for the upsell use case. Those fields are also under the tenant namespace \_devbc. They came from a different schema (dep: Customer Aggregates) and a custom field group (dep: Aggregates)

```json
"aggregates":{
   "rollingSixMonthAvgMonthlyDataUsage":30,
   "rollingSixMonthTotalDataUsage":200
}
```

## View Identity Map

You can also see a profile's associated identities as they are stored within a map based object named **identityMap.** Look for **identityMap** near the bottom of the JSON document. 

This is a representation of all the identities you have passed in regardless if you used the identityMap field or marked a field using an identity Descriptor.

```json
"identityMap": {
  "ecid": [{
          "id": "34537751351243145301122536487445728054"
      },
      {
          "id": "66385443304271800137026604878870723316"
      },
      {
          "id": "34537751351243145301122536483456723542"
      }
  ],
  "email": [{
          "id": "dave.gahan@dep.com"
      },
      {
          "id": "depeche.mode@dep.com"
      }
  ],
  "customerid": [{
      "id": "266242885"
  }],
  "gaid": [{
          "id": "266242-9013"
      },
      {
          "id": "266242-9012"
      }
  ]
}
```

>[!NOTE]
>
>Note there is no reference to the concept of “primary identity" within the identityMap. The reason for is two-fold:
>
>1. The identityMap you see in profile attributes is created for each profile utilizing the Identity Service's graph\*
>2. The Identity Graph only cares about relationships between identities. Each identity is treated the same. A is related to B and it does not matter if it was via a primary identity, person identity, etc.
>
>*\*If no identity graph is used the identityMap is composed of only the identity requested in the lookup*

>[!NOTE]
>
>When you built the customer account schema you only had one email field marked as an identity (i.e. personalEmail.address). Did you notice though the identityMap has two email addresses!
>
>What is going on? 
>
>- Identity Graph is constantly recording new relationships and the values within those relationships as data flows into its service
>- Profile's behavior is to overwrite existing field values with new values as data is ingested into its service
>- When you flag a field with an identity descriptor it is still a field for Profile



## Identity Graph

Navigate back to the **Detail** tab in the top nav and click on the **View Identity graph** link found at the bottom of the **Linked identities** card

![LxxLyKc0x1oi f6FcL1H4RJTGi194ghRgD 20241017 202332.png "View Identity Graph"](assets/n-ADAXZy_lxxLyKc0x1oi-f6FcL1H4RJTGi194ghRgD-20241017-202332.png "View Identity Graph")

You should now see this screen.

![Identity graph view of depech mode profile.png "Identity Graph view of Depech Mode profile"](assets/8-PW56xho50xtvQ4trr55_identity-graph-view-of-depech-mode-profile.png "Identity Graph view of Depech Mode profile")

The view above is the Identity Graph of the Depeche Mode profile and is broken up into a three (3) key areas:

**Identity Graph Visualizer** - shows the identities and their associated relationships within the profiles identity cluster

**Identity Graph Details** - provides specific details around the overall identity graph namespaces, values and data sources that created all the relationships seen within the Identity Graph Visualizer

**Selected Identity Details** - displays detailed information on the selected identity along with the last five (5) batches where that identity was processed in a relationship

>[!NOTE]
>
>The identity graph viewer displays both the relationships between all the identities as well information around the last time the identity relationship was seen and from what dataset



Lets view the identity graph of Depeche Mode using the customerID identity instead.  Perform the following actions:

1. Copy and save the **customerID** somewhere.
1. Change the namespace value in the Identity namespace box to **customerID**
1. Paste in the **customerID** value you saved from the previous step
1. Click the **View** button to see the identity graph that contains this identity using the new identity value

![Identity graph view of.png "Identity Graph View of Identity Graph View of "](assets/CAoR0JPVtw5hL5qR3TIe2_identity-graph-view-of.png "Identity Graph View of Identity Graph View of ")

>[!NOTE]
>
>Notice how you see the exact same identity graph! Any identity you use from this graph will always result in the same result



## Changing Identities

Go back to the Profile Viewer and lookup Depeche Mode using the customerID now

1. Change the Identity namespace to **customerID**
1. Update the Identity value using the customerID value you saved in the last section
1. Click the **View** button

![LxxLyKc0x1oi X7PNE3BFiKC9NNb5x 0VR 20241017 203302.png "Lookup Depeche Mode using customerID"](assets/n-ADAXZy_lxxLyKc0x1oi-X7PNE3BFiKC9NNb5x-0VR-20241017-203302.png "Lookup Depeche Mode using customerID")



You should see the same profile you just viewed previously!

![LxxLyKc0x1oi Dg2H11yDR5UbeyAydVo7x 20241017 204630.png "Depeche Mode profile details"](assets/n-ADAXZy_lxxLyKc0x1oi-Dg2H11yDR5UbeyAydVo7x-20241017-204630.png "Depeche Mode profile details")

>[!NOTE]
>
>The identity graph ensures that any identity you use results in the same profile when assembling the various profile fragments

