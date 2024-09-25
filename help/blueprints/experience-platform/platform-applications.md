---
title: Experience Platform (AEP) and applications architecture diagrams
description: View architecture diagrams that show how Adobe Experience Platform (AEP) relates to other Experience Cloud applications and application services.
solution: Experience Platform, Campaign, Analytics, Target, Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
kt: 7199
thumbnail:
exl-id: 9b12cd7a-5e5f-443a-91a1-44273cdabc2d
---
# Adobe Experience Platform and applications architecture diagrams

These architecture diagrams show how Experience Platform (AEP) relates to other Experience Cloud applications and application services.

>[!MORELIKETHIS]
>
>[Integration Configurations for Experience Cloud Applications Integrations](https://experienceleague.adobe.com/docs/integrations-learn/experience-cloud/overview.html?lang=en).


## Architecture diagram

This architecture diagram shows how Adobe Experience Platform relates to Adobe Experience Cloud applications and application services.

<img src="assets/aep+apps.svg" alt="Experience Platform & Applications" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Overview diagram

<img src="assets/aep+apps_overview.svg" alt="Experience Platform & Applications" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Detailed architecture diagram

<img src="assets/aep+apps_detailed.svg" alt="Experience Platform & Applications" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

>[!VIDEO](https://video.tv.adobe.com/v/32456/?quality=12&learn=on)

## AEP and Experience Cloud application integrations

<table class="relative-table wrapped" style="width: 100%;">
<colgroup>
<col style="width: 16.0202%;" />
<col style="width: 29.3423%;" />
<col style="width: 33.5582%;" />
<col style="width: 21.0793%;" />
</colgroup>
<tbody>
<tr>
<th>Application</th>
<th>Experience Platform to Application</th>
<th>Application to Experience Platform</th>
<th>Related Blueprints</th>
</tr>
<tr>
<td colspan="1">Ad Cloud</td>
<td colspan="1">
<ul>
<li>Audiences defined in Real-time Customer Data Platform can be shared to Ad Cloud for targeting via Audience Manager.</li>
</ul>
</td>
<td colspan="1">
<ul>
<li>No current integration</li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=en">Anonymous Audience Activation</a></li>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html">Known Customer Activation</a></li>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-applications.html">Activation with Experience Platform and Applications</a></li>
</ul>
</td>
</tr>
<tr>
<td>Analytics</td>
<td>
<ul>
<li>Data collected via the Web/Mobile SDK can be forwarded to Adobe Analytics.</li>
</ul>
</td>
<td>
<ul>
<li>Data collected by Analytics can be sent to Experience Platform data lake and profile store.&nbsp;<a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=en">Analytics Data Connector</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-data-flow.html?lang=en">Experience Platform Data flows</a></li>
</ul>
</td>
</tr>
<tr>
<td>Audience Manager</td>
<td>
<ul>
<li>Audiences defined in Real-time Customer Data Platform can be shared to Audience Manager for activation to 3rd party cookie destinations.</li>
</ul>
</td>
<td>
<ul>
<li>Data collected and evaluated along with audience membership from Audience Manager can be shared to Experience Platform data lake and profile store.&nbsp;<a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=en">Audience Manager Source Connector</a></li>
</ul>
</td>
<td>
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=en">Anonymous Audience Activation</a></li>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html">Known Customer Activation</a></li>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Activation with Experience Platform and Applications</a></li>
</ul>
</td>
</tr>
<tr>
<td colspan="1">Campaign Classic</td>
<td colspan="1">
<ul>
<li>Audiences defined in Real-time Customer Data Platform can be shared to Campaign Classic as the audience to initiate campaigns.</li>
</ul>
</td>
<td colspan="1">
<ul>
<li>Interaction and campaign data collected by Campaign can be ingested to Experience Platform as a data source for further use in audience building via Real-time Customer Data Platform and analysis via Customer Journey Analytics and Experience Platform Query Service.</li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/overview.html?lang=en">Customer Journeys</a></li>
</ul>
</td>
</tr>
<tr>
<td colspan="1">Campaign Standard</td>
<td colspan="1">
<ul>
<li>Audiences defined in Real-time Customer Data Platform can be shared to Campaign Standard as the audience to initiate campaigns.</li>
</ul>
</td>
<td colspan="1">
<ul>
<li>Interaction and campaign data collected by Campaign can be ingested to Experience Platform as a data source for further use in audience building via Real-time Customer Data Platform and analysis via Customer Journey Analytics and Experience Platform Query Service.</li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/overview.html">Customer Journeys</a></li>
</ul>
</td>
</tr>
<tr>
<td colspan="1">Customer Journey Analytics</td>
<td colspan="1">
<ul>
<li>Data collected and ingested into Experience Platform data lake is made available for processing into Customer Journey Analytics.&nbsp;</li>
<li>Profile and audience data from Real-time Customer Data Platform can be ingested into CJA. <a href="https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/ingest-aep-segments.html?lang=en">RTCDP to CJA integration</a>.
</li>
</ul>
</ul>
</td>
<td colspan="1">
<ul>
<li>Build audiences in Customer Journey Analtyics and share the audience results to Real-time Customer Data Platform. <a href="https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=en">CJA Audience Publishing</a></li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journey-analytics/overview.html?lang=en">Customer Journey Analytics</a></li>
</ul>
</td>
</tr>
<tr>
<td colspan="1">Experience Manager</td>
<td colspan="1">
<ul>
<li>The Experience Platform profile can be directly accessed server side to power personalized experiences delivered through Experience Manager. Note that personalization activities are most commonly delivered via Experience Manager through the Target integration.&nbsp;</li>
</ul>
</td>
<td colspan="1">
<ul>
<li>No current integration, behaviors and interactions performed on Experience Manager sites are collected directly via the Experience Platform Web and Mobile SDK.</li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html?lang=en">Known Customer Activation</a></li>
</ul>
</td>
</tr>
<tr>
<td colspan="1">Journey Optimizer</td>
<td colspan="1">
<ul>
<li>Data events and profiles ingested into Experience Platform are made available to Journey Optimizer to initiate and power journeys in Journey Optimizer.</li>
</ul>
</td>
<td colspan="1">
<ul>
<li>Interaction and campaign data produced by Journey Optimizer is collected into Experience Platform for further&nbsp;use in audience building via Real-time Customer Data Platform and analysis via Customer Journey Analytics, and Experience Platform Query Service.</li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer.html?lang=en">Journey Optimizer</a></li>
</ul>
</td>
</tr>
<tr>
<td colspan="1">Adobe Commerce</td>
<td colspan="1">
<ul>
<li>Profiles and audiences built in Real-time Customer Data Platform can be made available for personalization in Adobe Commerce. </li>
</ul>
</td>
<td colspan="1">
<ul>
<li>Data native to Adobe Commerce can be sent to Experience Platform via a Adobe Commerce source connector.&nbsp;</li>
</ul>
</td>
<td colspan="1">No current integration</td>
</tr>
<tr>
<td colspan="1">Marketo</td>
<td colspan="1">
<ul>
<li>Audiences defined in Real-time Customer Data Platform can be shared to Marketo as the audience to initiate Marketo campaigns and update Marketo objects.</li>
</ul>
</td>
<td colspan="1">
<ul>
<li>Marketo accounts, contacts, and opportunity data, along with Interaction and campaign data produced by Marketo is ingested into Experience Platform for further&nbsp;use in audience building via B2B-CDP and analysis via Customer Journey Analytics, and Experience Platform Query Service.&nbsp;<a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=en">Marketo Engage Connector</a></li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=en">B2B Activation Blueprint</a></li>
</ul>
</td>
</tr>
<tr>
<td colspan="1">Real-Time CDP</td>
<td colspan="1">
<ul>
<li>Data ingested and collected into Experience Platform is the data source for assembling real-time customer profiles that power the Real-time Customer Data Platform.</li>
</ul>
</td>
<td colspan="1">
<ul>
<li>Audience and Profile metrics are sent to the Experience Platform data lake to power profile insight reporting dashboards.</li>
<li>The Audience and Profile data in the data lake can be used for further insights via Query Service&nbsp;and Customer Journey Analytics.</li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html?lang=en">Known Customer Activation</a></li>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Activation with Experience Platform and Applications</a></li>
</ul>
</td>
</tr>
<tr>
<td colspan="1">Target</td>
<td colspan="1">
<ul>
<li>Audiences and Profile Attributes defined in Real-time Customer Data Platform can be shared to Target and used in personalization and targeting experiences delivered by Target.</li>
</ul>
</td>
<td colspan="1">
<ul>
<li>Data collected for Target experiences and interactions can be collected to Experience Platform via the Experience Platform Web/Mobile SDK. This data can be used in audience building via the Real-time Customer Data Platform and for analysis via Customer Journey Analytics, and Experience Platform Query Service.</li>
</ul>
</td>
<td colspan="1">
<ul>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html?lang=en">Known Customer Activation</a></li>
<li><a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Activation with Experience Platform and Applications</a></li>
</ul>
</td>
</tr>
</tbody>
</table>