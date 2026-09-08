---
hold: true
title: Profile & Identity API's
description: Profile & Identity API's
doc-type: article

solution: Experience Platform
exl-id: 1db55c5b-fdf8-4c63-b435-477626bb0450
---

# Profile Entity API

Knowing how to utilize the profile API's is critical when it comes to working with the Real-Time Customer Profile. It unlocks the ability for fast triage and debug while also exposing you to endless possibilities around system integrations from call centers to kiosks.

One of the most important API's is the Profile Entity API.  This API allows you to lookup an individual profile (just like you saw in the UI) but uses param's to dictate whether you want to see the attributes or events of the profile.

Below is the entire spec for the GET method for the Profile Entity API


## API Overview

`GET` https\://platform.adobe.io/data/core/ups/access/entities

## Query parameters 

**schema.name**`*` `string`

XED Schema Class name.

Example: "\_xdm.context.profile"


relatedSchema.name `string`

XED Schema Class name that the experience event is associated with. Used when looking up experience events.

Example: "\_xdm.context.profile"


entityId `string`

ID of the entity. For Native XID lookup, use **'entityId=\<XID>' **and leave** 'entityIdNS' **absent; For Id\:NS lookup, use both **'entityId' **and **'entityIdNS' **fields.

Example: "GtghAUFkdGVzdDE"


entityIdNS `string`

Identity Namespace code. Used for id\:ns lookup. If this field is used, **'entityId' **cannot be empty.

Example: "UPS1"


relatedEntityId `string`

ID of the entity that the experience events are associated with. Used when looking up experience events. For Native XID lookup, use '**relatedEntityId=\<XID>'** and leave '**relatedEntityIdNS'** absent; For Id\:NS lookup, use both '**relatedEntityId'** and '**relatedEntityIdNS'** fields.

Example: "GtghAUFkdGVzdDE"


relatedEntityIdNS `string`

Identity Namespace code of the related entity id of experience event. Used when looking up experience events. If this field is used, '**entityId' **cannot be empty.

Example: "UPS1"


fields `string`

Fields to be returned for the model object. By default, all fields will be fetched. For each field, paths are seprated by '.'. Different fields are separated by ','.

Example: "person.name.firstName,person.name.lastName"


mergePolicyId `string`

Id of the mergePolicy. MergePolicy includes information of Identity stitching and key-value xdm object merging. If not present, default merge policy will be used.

Example: "example-mergePolicy"


startTime `number`

Start time of Time range filter for experience events. Should be at millisecond granularity. Included. Default: From beginning.

Example: "1539838505"


endTime `number`

End time of Time range filter for experience events. Should be at millisecond granularity. Excluded. Default: To the end.

Example: "1539838510"


limit `number`

Number of records to return from the result. Only for time-series objects. Default: 1000

Example: 10


orderby `string`

The sort order of retrieved experience events by timestamp. Syntax: (+/-)timestsamp. Default: +timestamp

Example: "-timestamp"


property `string`

Filter by property value. Support evaluators \[=,!=,\<,>,\<=,>=]. When more than 1 property filter is provided, it will be concantenated with AND. Example: Paramter Input of

**'property=web.webPageDetails.isHomepage=false\&placeContext.localTime\<="2019-07-20" **will result in a filter of '**placeContext.geo.city!="Burns Lake" AND placeContext.localTime\<="2019-07-20"' **Date filters should be provided as a '**String' **in the format of **'yyyy-mm-dd' **Notes: URL will need to be encoded. Maximum of 3 properties is supported. Only for experience events.

Example: "web.webPageDetails.isHomepage=false"


withUISApi `boolean`

You can use UIS API to get identity map with this params equals to true


withUISCache `boolean`

You can use UIS cached records in UPS to get identity map with this params equals to true


withUISDebug `boolean`

When you are using UIS cached records in UPS to get identity map, with this params equals to true, you will get the union set of all the xids identity map

## Header parameters

x-gw-ims-org-id`*``string`

IMS Organization ID

Example: "\<replace with your ims org>"


x-api-key`*``string`

API Key

Example: "\<replace with your api key>"


Authorization`*``string`

Authorization token

Example: "Bearer \<replace with your token

>[!NOTE]
>
>You can learn more about the Profile API's and others on the [Adobe Developer ](https://developer.adobe.com/experience-platform-apis/)website

>[!WARNING]
>
>Remember all API requests are sandbox specific so its important when working with the API's that you ensure your header param in each request called `x-sandbox-name` is correctly set the appropriate sandbox.
>
>For this lab you already have the `x-sandbox-name` set in your environment file

###

## Entity Lookup (attributes)

To get a feel the Entity Lookup API you'll use the Depeche Mode profile from the previous lab.

1. Open up **Postman **and navigate to the **Profile Lab** folder
1. Click on the **Entity Lookup (attributes)** request to open it
1. Execute the call by clicking the **Send **button

![3AYLtWMu profile entity lookup attributes api.png "Profile Entity Lookup (attributes](assets/lV7mJTqL9wBN_3AYLtWMu_profile-entity-lookup-attributes-api.png "Profile Entity Lookup (attributes) API")

A successful request should respond with a `200 OK` and you should see a result that contains all the attributes for the Depeche Mode profile.

![Ur7P0oenhGc2 successful profile entity attributes api response.png "Successful Profile Entity (attributes](assets/Gogu7oCC_Ur7P0oenhGc2_successful-profile-entity-attributes-api-response.png "Successful Profile Entity (attributes) API Response")

>[!NOTE]
>
>By default if no merge policy is specified in a profile entity request it uses the default merge policy in the sandbox

With the Entity API there are a number of query parameters that you can utilize to change the what is returned in response.  

1. In the Entity Lookup (attributes) request click on the **Params **option for the request
1. Check the box next to **Key **named **fields**
1. Execute the request by clicking the **Send **button

![Profile entity lookup attributes with filter enabled](assets/profile-entity-lookup-attributes-with-filter-enabled.png)

>[!NOTE]
>
>Notice there is also a parameter for specifying the `mergePolicyId`.  You can find the value for this utilizing other API's or looking up the ID using the UI.

A successful request should respond with a `200 OK` and you should see only the fields specified in the param filter you just enabled:  First Name, Last Name and an array of Active Products.

![Successf.png "Successful Profile Entity Lookup (attributes](assets/a8YtaW9-H7Ohxku-jR6Ew_successf.png "Successful Profile Entity Lookup (attributes) API Response with filter enabled")

>[!NOTE]
>
>Congratulations!  You've successfully looked up a profile's attributes utilizing the Profile Entity API

###

## **Entity Lookup (events)**

To lookup the events of a profile you use the same exact Profile Entity API.  The only difference is you have to tell the profile service that you want to change which class type use in the response.

1. Click on the **Entity Lookup (events)** request to open it
1. Execute the call by clicking the **Send **button

![Profile entity lookup events](assets/profile-entity-lookup-events.png)

A successful request should respond with a` 200 OK` and you should see a result that contains all the events for the Depeche Mode profile.



![LLZG3u2wYuw046kQ successful profile entity lookup events api response.png "Successful Profile Entity Lookup (events](assets/Fsmu_LLZG3u2wYuw046kQ_successful-profile-entity-lookup-events-api-response.png "Successful Profile Entity Lookup (events) API Response")

Just like when looking up profile attributes the Entity API has even more query parameters that can be utilized to change the what is returned in response.

You can try a few of them by turning enabling them in the Params section and executing the request.  Try it out and see how it works!

![LbDoa5Tnv27Y8diQW profile entity lookup for experience events.png "Profile Entity Lookup for Experience Events"](assets/-1k_LbDoa5Tnv27Y8diQW_profile-entity-lookup-for-experience-events.png "Profile Entity Lookup for Experience Events")

**Sample Query Param Definitions**

| Key           | Value                           | Description                                                                                                                                               |
| ------------- | ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| mergePolicyId | \<blank>                        | If provided you can switch the merge policy used to perform the lookup. For the lab leaving it blank means it will use the sandboxes default merge policy |
| fields        | eventType,timestamp,identityMap | Only displays these fields from each event regardless if the field specificed has a value                                                                 |
| property      | eventType="order.placed"        | Filters down the events of the profile to only those that are of type "order.placed"                                                                      |
| orderby       | +timestamp                      | Sorts the events in descending order                                                                                                                      |
| limit         | 5                               | Only shows 5 events in the response                                                                                                                       |

>[!NOTE]
>
>You can learn more about all the Query Parameter options here -> [https://developer.adobe.com/experience-platform-apis/references/profile/#tag/Entities/operation/retrieveEntity](https://developer.adobe.com/experience-platform-apis/references/profile/#tag/Entities/operation/retrieveEntity)



## Identity Service Cluster API

At some point you may have a question about what identities are part of a specific profiles identity cluster within the identity graph.  This API allows you to pass a single identity namespace/value and in response you'll receive the full identity cluster for that profile.

Try it yourself:

1. Click on the **List Linked Identities **request to open it
1. Execute the call by clicking the **Send **button

>[!NOTE]
>
>Note the parameters in the request are the identity namespace and id (i.e. value)



![List linked identities api.png "List Linked Identities API"](assets/Xls-UKprd9UcF0GRhQ701_list-linked-identities-api.png "List Linked Identities API")

A successful response should look like the below screenshot



![GCE1tBuGkhecfU you ll n](assets/you-ll-n.png)

>[!NOTE]
>
>You'll notice the response contains all the identities of the profile Depeche Mode

