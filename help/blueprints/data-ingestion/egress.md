---
title: Data Access and Export blueprint
description: Learn about the methods by which data can be accessed and exported from Adobe Experience Platform and applications.
product: adobe experience platform
solution: Experience Platform, Journey Optimizer, Real-Time Customer Data Platform, Data Collection
exl-id: 2ca51a29-2db2-468f-8688-fc8bc061b47b
---
# Data access and export blueprint

The data access and export blueprint outlines all the possible methods whereby data can be accessed or exported from [!DNL Experience Platform] and applications.

The blueprint is broken up into two categories for data access from [!DNL Experience Platform] and applications. 

The first includes approaches for egressing data from [!DNL Experience Platform] and applications. This would be considered a _push_ type method of data egress. 

The second includes approaches for access data from [!DNL Experience Platform] and applications. This would be considered a _pull_ type method of data access.

Data access approaches:

* [Real-time Customer Profile Access API](#rtcp-profile-access-api)
* [Data Access API](#data-access-api)
* [Query Service](#query-service)

Data export approaches:

* [Client Side Tags](#client-side-tags-extensions)
* [Event Forwarding](#event-forwarding)
* [Real-time Customer Data Platform Destinations](#RTCDP-destinations)
* [Journey Optimizer Custom Actions](#jo-custom-actions)

## Data access and export overview architecture

<img src="../experience-platform/assets/aep_data_flow.svg" alt="Reference architecture for the Data Preparation and Ingestion Blueprint" style="width:90%; border:1px solid #4a4a4a; margin-bottom: 15px;" class="modal-image" />

## Data access and export methods

<table cellspacing="0" class="Table" style="border-collapse:collapse; width:1133px">
<tbody>
<tr>
<td colspan="4" style="background-color:#308fff; border-bottom:4px solid white; border-left:1px solid white; border-right:1px solid white; border-top:1px solid white; height:39px; vertical-align:top; width:1133px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><strong><span style="color:black">Streaming Destinations</span></strong></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Method</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Common Use Cases</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Protocols</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Considerations</span></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en" style="color:#0563c1; text-decoration:underline">Event Forwarding</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Forwarding of raw data collected from Adobe SDKs for analysis and collection to enterprise systems</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Light weight tagging for 3<sup>rd</sup> party data collection through extensions</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST API</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Low level raw events</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">No aggregation or prior record context added</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/destination-types.html?lang=en#:~:text=containing%20profile%20exports.-,Streaming%20segment%20export%20destinations,-Segment%20export%20destinations" style="color:#0563c1; text-decoration:underline">RTCDP &ndash; Streaming Segment Exports</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Activate audiences from RTCDP to marketing and advertising, systems..</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST API</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Aggregated data representing audience membership</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">No activation of raw experience event data</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/destination-types.html?lang=en#:~:text=file%2Dbased)%20destinations-,Streaming%20profile%20export%20destinations%20(enterprise%20destinations),-IMPORTANT" style="color:#0563c1; text-decoration:underline">RTCDP &ndash; Profile Export Destinations</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Leverage RTCDP rich behavioral profiles and audiences to enhance consumer experiences and marketing.</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Activate audiences and profile attributes from RTCDP to marketing and advertising, systems that operate on audiences and profile attributes. </span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Activate AEP profiles to Email Service Providers, lead nurturing and CRM systems.</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST API</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Aggregated data representing audience membership and profile record attributes</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">No activation of raw experience event data</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/custom-personalization.html?lang=en" style="color:#0563c1; text-decoration:underline">RTCDP - Personalization Destinations</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Access the Real-time Customer Profile in browser and client side experiences to enrich client side personalization. </span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Requires deployment of WebSDK</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/destination-sdk/overview.html?lang=en" style="color:#0563c1; text-decoration:underline">RTCDP - Destination SDK</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Configure a customized destination card in the RTCDP destinations.</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Supports file and streaming type destinations</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">CSV</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Allows partners and brands to configure custom destination cards</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=en" style="color:#0563c1; text-decoration:underline">RTCDP - Profile Lookup Hub API</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Access profile to enrich consumer experiences for agent assisted experiences such as support or sales agent interactions.</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Pull</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST API</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Hub lookup ideal for &gt;500ms+ use cases only</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:27px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">RTCDP - Profile Lookup Edge API</span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:27px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Access profile on the edge to enrich consumer experiences for real-time &lt;200ms experiences such as personalization or offer decisions on web and mobile.</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:27px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Pull</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST API</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:27px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">For real-time experiences and server to server integrations</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions.html?lang=en" style="color:#0563c1; text-decoration:underline">Journey Optimizer Custom Actions</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Activation of 1:1 journey events and triggers to notify an external system. Cart abandons, application abandons, registrations.</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST API</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Single event activation for a given profile. Not for aggregation or bulk operations</span></span></span></li>
</ul>
</td>
</tr>
</tbody>
</table>

<p>&nbsp;</p>

<table cellspacing="0" class="Table" style="border-collapse:collapse; width:1132px">
<tbody>
<tr>
<td colspan="4" style="background-color:#308fff; border-bottom:4px solid white; border-left:1px solid white; border-right:1px solid white; border-top:1px solid white; height:39px; vertical-align:top; width:1132px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><strong><span style="color:black">Batch Destinations</span></strong></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:245px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Method</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:462px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Common Use Cases</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Protocols</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:281px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Considerations</span></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:245px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/data-access/api.html?lang=en" style="color:#0563c1; text-decoration:underline">Data Access API</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:462px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Access to raw data for data science and ML workflows outside of Experience Platform.</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Pull</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST API</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Parquet files</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:281px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Requires development processes to access and process parquet files into usable datasets</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:245px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en" style="color:#0563c1; text-decoration:underline">Query Service</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:462px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Persist query results of datasets, for aggregated insight and reporting. </span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Pull</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">PostgreSQL </span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">SQL Client</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:281px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Aggregate data only. 10 minute query limit.</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:245px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/export-datasets.html?lang=en" style="color:#0563c1; text-decoration:underline">Dataset Export</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:462px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Export Experience Platform event data for access in external reporting, analysis, and data science tools. </span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Export of aggregated profile insights and audience membership for external reporting, analysis, and data science tools. </span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST API </span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">CSV</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:281px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Subset of datasets are supported as outlined in the product documentation.</span></span></span></li>
</ul>
</td>
</tr>
</tbody>
</table>



## Approaches for Data Access

### Real-time Customer Profile Access API {#rtcp-profile-access-api}

Customers can access single unified profiles from the Real-time Customer Profile store including all profile identities, audience memberships, attributes and experience events using the Real-time Customer Profile Access API.

Refer to the [Real-time Customer Profile Access API](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=en) documentation for additional information.

#### Use cases

* Lookup a single profile to add context to agent customer interaction such as a support interactions through chat and call center, or a sales interaction at the point of sale.
* Allow added context to a personalization descision made by an external system, for example a web personalization system or a offer decision system.

#### Considerations

* Real-time Customer Profile [guardrails](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) apply.
* Designed for single profile lookup at a time. Not used for bulk profile access or download of the entire profile population for the use of analysis or data science. 
* Profile lookup response time adhears to the profile guardrails. Real-time low latency requirements - for example for same page personalization requirements should utilize the Edge Profile from the to [Adobe Target Connection](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en) or the [Custom Personalization Connection](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/custom-personalization.html?lang=en) for real-time profile access for in browser and in app personalization.

### Data Access API {#data-access-api}

Using the data access API customers can directly access the raw dataset files that are stored in the Experience Platform data lake.

* For additional details on using the data access API please refer to the [documentation](https://experienceleague.adobe.com/docs/experience-platform/data-access/home.html?lang=en).

#### Use cases

* Pull raw and processed data files from Experience Platform for storage and evaluation in enterprise environments.

#### Considerations 

* As data is accessed in a batch asynchronous fashion the access to the data will be inherently latent as compared to streaming data egress approaches such as utlitizing Tags, Event Forwarding, or RTCDP Destinations.
* Data files when processed into Experience Platform are stored as collections of files in batches and are compressed and stored in parquet format. As such when accessing and downloading the files to a different environment they must be systematically accessed by their batch and file as oppossed to an entire dataset and any operations on the data must account for the files being compressed in parquet format. 

### Query Service {#query-service}

Using the experience platform Query Service customers can query datasets within Experience Platform and persist the results of the query. A SQL Client can be utilized to query and persist the query response in the desired storage destination that the SQL client can support. The Query Service UI can be used to store the SQL result in a target dataset in the Experience Platform or the results can be saved to the local machine.

* For additional details on connectin to SQL clients to persist SQL results from Experience Platform Query Service see the following [documentation](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=en).

#### Use cases

* Query raw data from the Experience Platform datasets and persist the query results.
* Query the profile snapshot dataset to extract insights on the Real-time Customer Profile. [Documentation](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=en#profile-attribute-datasets). 
* Store query results into a separate dataset for access or into a profile enabled dataset which can later be egressed through RTCDP and other Experience Cloud applications which access the Real-time Customer Profile. 

#### Considerations

* As data is queried in a batch asynchronous fashion the access to the data will be inherently latent as compared to streaming data egress approaches such as utlitizing Tags, Event Forwarding, or RTCDP Destinations.
* Only data that is available in the Experience Platform data lake can be queried using the Query Service. The Real-time Customer Profile store, the identity graph, Customer Journey Analytics can not be directly queried using the Query Service. Only when datasets are exported to the data lake can these datasets be queried, as in the example of the profile snapshot dataset.
* Note that guardrails for the number of query results and the query timeout apply as outlined in the [Query Services guardrails](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=en) documentation.

## Approaches for Data Export

### Client-side tag extensions {#client-side-tags-extensions}

Extensions can be deployed using Adobe's Tags solution. Once an extension is deployed data requests are deployed directly on a client browser or application and a request can be invoked to send data and requests to the desired destination.

Refer to the [Tags Overview](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en) documentation for additional information.

#### Use cases

* Collect raw streaming information directly from client side environments using tagging.

#### Considerations

* No direct access to any server side information such as the Experience Platform Real-time Customer Profile and audience memberships. 
* Adding additional data collection tags to the page may increase page load times.
* Ability to set up rules to only request data when certain criteria are met. 
* Data is collected directly from the client, limiting the types of transformations and enrichment that can be performed prior to collecting the data.

### Event forwarding {#event-forwarding}

Data collection requests are collected directly to Adobe's [!DNL Edge Network]. From the [!DNL Edge Network] requests to external RESTful endpoints can ba configured to forward these requests on to the external destination. 

Refer to the following [Event Forwarding](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en) documentation for additional information.

#### Use cases

* Collect raw streaming information directly from client side environments to a enterprise endpoint using Adobe's server side event forwarding.

#### Considerations

* To use Event Forwarding, data must be sent to the [!DNL Edge Network] using the Web SDK or MobileSDK.
* Event forwarding approach reduces the page load time and weight due to additional tags being added on the page.
* No enrichment from the edge profile or other data sources is currently supported. 
* Limited data filtering and simple mapping transformations are supported.

### Real-time Customer Data Platform destinations {#RTCDP-destinations}

Profile attribute data and audience membership data can be activated to enterprise and advertising destinations. This means the data egressed must be ingested into the Experience Platform Real-time Customer Profile. 

Refer to the [Real-time Customer Data Platform Destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=en) documentation for additional information.

#### Use cases

* Activate profile attibute information including audience membership to a internal enterprise data stores, analytsis tools, email systems, or support systems.
* Activate profile audience membership to a external advertising vender to target and personalize content to the profile. 

#### Considerations

* Profile attributes and audience memberships can be activated. Raw experience events can not currently be activated as part of RTCDP Destinations. 
* Activations happen in streaming or batch depending on the nature of the segment evalution and the nature of the ingestion protocal that the destination accepts.

### Journey Optimizer custom actions {#jo-custom-actions}

Using Journey Optimizer customers can invoke a custom action from the journey canvas to send a payload or message to a external API endpoint that is configured. An action can be configured to any service from any provider that can be called through a REST API with a JSON-formatted payload. This payload can include event information, profile attributes and prior event data, transformations and enrichments that are configured in the journey.

Refer to the [Journey Optimizer custom actions](https://experienceleague.adobe.com/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions.html?lang=en) documentation for additional information.

#### Use cases

* Activation events from Experience Platform and Journey Optimizer that include additional information from the Real-time Customer Profile.
* Notify external systems when a customer has reached a specific point of a journey. 

#### Considerations

* Guardrails on the throughput supported by [Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=en) and enrichments supported by the [Real-time Customer Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) apply.
* Custom actions can be performed in a streaming one by one fashion for each event or profile in a journey. Bulk operations or bulk data egress in the form of files or aggregated requests across customer journeys can not be performed. 
* Streaming access to Real-time Customer Profile attributes and experience events which can be included in the activation payload.
* Event data can be filtered and simple mapping transformations applied before sending events to external destinations.
