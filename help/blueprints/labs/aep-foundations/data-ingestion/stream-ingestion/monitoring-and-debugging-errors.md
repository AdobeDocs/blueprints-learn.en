---
title: Monitoring and debugging errors
description: Use the Streaming End-to-End monitoring dashboard to identify and interpret INGEST, DCVS, and MAPPER errors in a streaming dataflow.
doc-type: article
solution: Experience Platform
exl-id: 268abf15-14ac-45e3-8cd7-8d180ee5b1e3
---

# Monitoring and debugging errors

>[!NOTE]
>
>Monitoring streaming ingestion happens at the dataflow level which means when you are viewing it within the UI you are viewing the data lake.  This means you see batches show up (the micro-batches processing off of the streaming pipeline) roughly every 60mins.  So if you do not see your data in the Real-Time Customer Profile, you have to wait for up to 60 minutes to diagnose the issue. 



## View monitoring dashboard

1. Navigate to **Monitoring->Streaming End-to-End** and locate your **Dataflow**:

   ![Locating the streaming dataflow in the Monitoring section](assets/monitoring-and-debugging-errors-locate-your-dataflow-in-monitoring.png "Locate your dataflow in Monitoring")



1. You may want to preview the **dashboard** tab to see pipeline metrics pertaining to batch ingestion workflows. 

![Dashboard tab showing metrics across all batch ingestion workflows](assets/monitoring-and-debugging-errors-dashboard-tab-metrics.png "Dashboard tab shows metrics across all batch ingestion workflows")

>[!NOTE]
>
>This monitoring screen allows you to see the status of your various dataflow runs.  Note the various metrics available to you in the top panel.  These metrics can be extremely useful for understanding the health of your data pipeline within the Experience Platform



## Debugging errors 

1. If your dataflow had errors because you did not follow instructions, you see the following.

   ![Failures reported for a streaming dataflow with mapping errors](assets/monitoring-and-debugging-errors-failures-reported.png "Failures reported")



1. If you click on the Failures, you obtain the following screen:

   ![Error diagnostics screen showing INGEST, DCVS, and MAPPER error details](assets/monitoring-and-debugging-errors-preview-error-diagnostics.png "Preview error diagnostics")

   >[!NOTE]
   >
   >A successful micro-batch may take longer than 15 minutes as it may need time to write the records to the data lake.



1. Analyze the error message, identify the **source/target fields,** and look for the code:

   - **INGEST XXXX** - This is a serious error either due to data corruption or formatting issues i.e. not following a regex format. 
   - **DCVS XXXX** -  This error is seen with `required` fields. If the values do not exist or are mapped incorrectly (not within the enum list), these rows are skipped.
   - **MAPPER XXXX** - These are warnings and no rows are skipped. But the values may have been "nullified" - so you should check to make sure that they do not impact downstream activities. 

1. To recover from the errors, you need to go to **Sources->Dataflows->Dataflow Name->Update dataflow** and fix your mappings. 

> [!NOTE]
>
>You need to re-upload the JSON sample file by first deleting it and adding it back again so that the mapper is now refreshed with a new copy for validation.

![Navigating to Sources > Dataflows > Dataflow Name > Update dataflow to fix mappings](assets/monitoring-and-debugging-errors-update-dataflow-navigation.png "Click Update dataflow")
