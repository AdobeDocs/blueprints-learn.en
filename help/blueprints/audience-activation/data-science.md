---
title: Custom Data Science for Profile Enrichment Blueprint
description: Learn how data science-based insights can be ingested into [!DNL Experience Platform] to enrich the Real-time Customer Profile.
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
---
# Custom data science for profile enrichment blueprint

The custom data science for profile enrichment blueprint illustrates how data can be used to train, deploy, and score models to provide machine learning insights into [!DNL Experience Platform] and the [!DNL Real-Time Customer Data Platform] from data science and machine learning tools. 

Modeled insights can be ingested into [!DNL Experience Platform] to enrich the real-time customer profile. Examples of machine learning insights include lifetime value scoring, product and category affinity, propensity to convert, or propensity to churn.

## Use cases

* Extract insight and discover patterns from customer data, train and score models from this data.
* Enrich the [!UICONTROL Real-time Customer Profile] with model driven insights and attributes for more granular personalization and optimized journeys.
* Train and Score models to determine customer insights such as customer lifetime value, propensity to convert or churn, product and content affinities, and engagement scores.

## Architecture

<img src="assets/data_science.svg" alt="Reference Architecture for the Custom Data Science for Profile Enrichment Blueprint" style="width:90%; border:1px solid #4a4a4a" />

## Guardrails

* For detailed guardrails and end to end latencies on ingesting data science results into [!DNL Experience Platform] and the Real-time Customer Profile refer to the data ingestion guardrails and latency diagram referenced in the [deployment guardrails document](../experience-platform/guardrails.md).

## Implementation considerations

* In most cases model result should be ingested as profile attributes and not experience events. The model results can be a simple attribute strings. If there are multiple model results that are to be ingested, it is recommended to use an array or map type field.
* The daily profile snapshot dataset which is a daily export of the unified profile attribute data can be leveraged to train models on profile attribute data. Profile snapshot dataset documenation can be accessed [here](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html#profile-attribute-datasets).

## Related documentation

* [Adobe [!DNL Experience Platform] Intelligence product description](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Adobe [!DNL Experience Platform] Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html)

## Related blog posts

* [Content and Commerce AI: Personalizing Your Interactions with Customers Through Content Intelligence](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [An Introductory Look at Exploratory Data Analysis on Adobe [!DNL Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe [!DNL Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)