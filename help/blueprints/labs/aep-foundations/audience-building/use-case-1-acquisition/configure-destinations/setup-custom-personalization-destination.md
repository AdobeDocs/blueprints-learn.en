---
hold: true
title: Setup Custom Personalization Destination
description: Setup Custom Personalization Destination
doc-type: article

solution: Experience Platform
exl-id: 46073f7c-00f4-4a4f-9fa3-8827ef15ec4a
---

Using a [Custom Personalization Destination](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) is a way to make audiences available on the Edge for use by a third party, usually using the Network Server API, to use for Personalizing.

This lab configures the Custom Personalization Destination so that we can send Profile Attributes to the Edge.



# Browse Destination Catalog

>[!NOTE]
>
>For personalizing using Adobe Target, we would use the [Adobe Target Destination.](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-target-v2) The behavior is identical to Custom Personalization.

1. In the left rail click on **Destinations**
1. In the top rail click on **Catalog**
1. Next select the category of **Personalization**
1. In the middle of the screen you should see the destination titled **Custom Personalization with Attributes. **Click the **Set up** button on that card.

![PDFpcMRYTDKx5WatQ37KL 20251126 155614.png "Browse destination catalog for Custom Personalization destination"](assets/pDFpcMRYTDKx5WatQ37KL-20251126-155614.png "Browse destination catalog for Custom Personalization destination")



## Configure Destination

## Setup Account

Name your account `DEP Labs Custom PZN` and then click the **Connect to destionation button**

![Create PZN account](assets/M-4_n8wFBuIVQoamgcX78-20251202-151555.png)



## Add Destination Details

Fill in the following Destination details:

1. Name -> **Edge Destination**
1. Integration Alias -> **edgeAlias**
1. Datastream ID -> *select the datastream name you created previously*
1. When done click the **Next **button

![K6ssA7rSRDSQ0QTi0h827 20251202 152043.png "Fill in destination details"](assets/k6ssA7rSRDSQ0QTi0h827-20251202-152043.png "Fill in destination details")

>[!CAUTION]
>
>Once you click Next you cannot change the **Name **or **Integration alias**.  These things will appear later on in the Edge Network responses



## Select Governance Policy

Select **Onsite Personalization** and then click the **Create **button

![1qXmv 5VJ8sQO5o F 20251202 152724.png "Select governance policy"](assets/ePk_1qXmv-5VJ8sQO5o_F-20251202-152724.png "Select governance policy")

>[!NOTE]
>
>While this set is optional its highly encourage that any destination you create has a governance policy assigned to avoid erronously activating profiles



When done you should see this screen noting your success!

![72FA5coONQt 20251202 153115.png "Successful PZN destination creation"](assets/vZp41fJ3X_72FA5coONQt-20251202-153115.png "Successful PZN destination creation")



## Activate Destination

## Select Audiences

Select the destination you just created by click on the row to highlight it and then click the **Next **button

![Q6HStXiyBFeZfO9njuXO  20251202 153325.png "Select PZN destination"](assets/q6HStXiyBFeZfO9njuXO--20251202-153325.png "Select PZN destination")



Select **All Audiences** and click **Next**

![BVDjpTU7fB3HxE7nGUVHA 20251202 160029.png "Select PZN Audiences"](assets/BVDjpTU7fB3HxE7nGUVHA-20251202-160029.png "Select PZN Audiences")



## Mapping

Add a **new mapping** as follows:

| Source Field           | Target Field |
| ---------------------- | ------------ |
| \_tenantName.plan.name | Plan Name    |

>[!WARNING]
>
>Remember to replace **\_tenantName** with your tenant name

>[!NOTE]
>
>The Target Field allows for providing a friendly name that may be different than the XDM name



When done your screen should like the below image.  You can then click the Next **button**

![Uge7zDALhElTgjs4kmSje 20251202 161742.png "Create PZN Mapping"](assets/uge7zDALhElTgjs4kmSje-20251202-161742.png "Create PZN Mapping")

>[!NOTE]
>
>Since profile attributes may contain sensitive data, all [Edge Network Server API ](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)calls must be made in an authenticated context in order to retrieve the attribute once it is on the Edge.


## Review

On the final screen you can review the details of your configuration and then click the Finish button.

![97dq54NjiTnWvqUKZgg78 20251202 162224.png "Review and Publish PZN Destination"](assets/97dq54NjiTnWvqUKZgg78-20251202-162224.png "Review and Publish PZN Destination")

>[!NOTE]
>
>This is the point where [Automatic Enforcement](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/auto-enforcement) will check against your [Data Usage Policies](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/policies/overview) It will check your Marketing Actions with the Rules you created and raise any errors.



