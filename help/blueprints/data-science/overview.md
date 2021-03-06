---
title: Custom Data Science for Profile Enrichment Blueprint
description: This blueprint shows how Adobe Experience Platform's Data Science Workspace can use data within Experience Platform to train, deploy, and score models to provide machine learning insights from the data.
solution: Experience Platform, Data Collection
kt: 7203
---

# Custom Data Science for Profile Enrichment Blueprint

This Blueprint shows how the data in Adobe Experience Platform is used by Data Science Workspace to train, deploy, and score models to provide machine learning insights. These models can directly output to a dataset enabled for Real-time Customer Profile. Examples of machine learning insights include lifetime value, product and category affinity, propensity to convert, or propensity to churn. 

## Use Cases

* Extract insight and discover patterns from customer data in Experience Platform. Train and score models from this data.
* Enrich the Real-time Customer Profile with model driven insights and attributes for more granular personalization and optimized journey optimization.
Train and Score models to determine customer insights such as customer lifetime value, propensity to convert or churn, product and content affinities, and engagement scores. 

## Scenarios

| Scenario | Scenario Description | Experience Cloud Applications |
|---|---|---|
|Exploratory Data Science | <ul><li>Discover signals, completeness, correctness of data</li><li>Discover new insights using data science tooling</li></ul> | <ul><li>Experience Platform Intelligence</li></ul> |
|Profile enrichment with AI/ML<br> - batch | <ul><li>Discover, author, train, deploy, score, and operationalize models.</li><li>Push model prediction to profile or to data lake for batch-based activation.</li></ul> | <ul><li>Experience Platform Intelligence</li></ul> |

## Architecture

<img src="assets/datascience.svg" alt="Reference Architecture for the Custom Data Science for Profile Enrichment Blueprint" style="border:1px solid #4a4a4a" />

## Implementation Steps

1. Create schemas and datasets
1. Ingest data into Experience Platform
1. Create a DSW notebook
1. Choose a language - support for Python and PySpark
1. Author model in notebook
1. Train the model
1. Score the model to generate predictions with the target data
1. Enable the model results dataset for profile, if pushing model results to the Real-time Customer Profile

## Related Documentation

* [Adobe Experience Platform Intelligence product description](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Data Science Workspace documentation](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=en)
* [Data Science Workspace tutorials](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/understanding-data-science-workspace.html)

## Related Blog Posts

* [Simplifying the Data Science Lifecycle with Adobe Platform Experience](https://medium.com/adobetech/simplifying-the-data-science-lifecycle-with-adobe-platform-experience-8ea4f056d82f)
* [Content and Commerce AI: Personalizing Your Interactions with Customers Through Content Intelligence](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [Gaining a Deeper Understanding of Churn Using Data Science Workspace](https://medium.com/adobetech/gaining-a-deeper-understanding-of-churn-using-data-science-workspace-18a2190e0cf3)
* [Understanding Data Science In Adobe Experience Platform](https://medium.com/adobetech/understanding-data-science-in-adobe-experience-platform-5bce5a17b42)
* [An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [Modeling XDM Data for Data Science at Scale on Adobe Experience Platform](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7)
* [Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe Experience Platform](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)
* [Reimagining Jupyter Notebooks for Enterprise Scale](https://medium.com/adobetech/reimagining-jupyter-notebooks-for-enterprise-scale-8bc6340d504a)
* [Accelerate Intelligent Insights with Adobe Experience Platform Data Science Workspace](https://medium.com/adobetech/accelerate-intelligent-insights-with-adobe-experience-platform-data-science-workspace-89538bacbbea)
* [A Preview of Time Series Forecasting with Adobe Experience Platform](https://medium.com/adobetech/preview-of-time-series-forecasting-with-adobe-experience-platform-38a2fc778e89)
* [Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)


