---
title: Data Analysis and Intelligence Blueprint
description: Use Adobe [!DNL Experience Platform] (AEM) to perform exploratory query and analysis of the data that exists in the data lake.
solution: Experience Platform
kt: 7207
thumbnail: 
exl-id: a972ea56-d1c8-45da-9044-ed31222a2441

---
# Data analysis and intelligence blueprint

Data analysis and intelligence comprises the ability within [!DNL Experience Platform] to perform exploratory query and analysis of the data that exists in the data lake.

[!DNL Experience Platform]'s [!UICONTROL Query Service] allows SQL queries to be performed on the data.

[!DNL Experience Platform] allows connections with third-party SQL clients, interfaces, and Business Intelligence (BI) tools to directly connect to, access and query the data within [!DNL Experience Platform], using the [!DNL PostgreSQL] protocol.

## Use cases

* Interactive query and aggregation of data
* Row and column access to ingested data for exploration and validation
* Dashboarding and visualization of data via Business Intelligence tooling

Additional common use cases for the query service are outlined here [Query Service Use Cases](https://experienceleague.adobe.com/docs/experience-platform/query/use-cases/abandoned-browse.html)

## Applications

* Adobe [!DNL Experience Platform]

## Architecture

<img src="assets/data_exploration.svg" alt="Reference architecture for the Enterprise Data Exploration and Reporting Blueprint" style="width:90%; border:1px solid #4a4a4a" />

## Guardrails

Refer to the Query Service Product Documentation for details on best practices and guardrails.
[Query Service Guidance](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html)

## Implementation steps

1. [Create schemas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) for data to be ingested.
1. [Create datasets](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) for data to be ingested.
1. [Ingest data](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) into [!DNL Experience Platform].
1.  Confirm that data is available to [[!UICONTROL Query Service]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/queries/explore-data.html?lang=en).
1.  [Connect Business Intelligence tools and SQL clients to [!UICONTROL Query Service]](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html) for visualization, data query, and exploration.

## Related documentation

* [Adobe [!DNL Experience Platform] Intelligence product description](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [[!UICONTROL Query Service] documentation](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en)
