---
title: Schedule Dataflow
description: Schedule Dataflow
doc-type: article
solution: Experience Platform
exl-id: 9865b1eb-0d98-4cae-a928-69ea897607ca
---

In the** Scheduling **step

1. Set the **Frequency** to Minute. 
1. Set the **Interval **to 15 i.e. 15 minutes. 
1. Turn the **Backfill **option on. 

>[!NOTE]
>
>Observe that the **Start time **is in UTC. 
>
>Coordinated Universal Time (UTC) is a global time standard that is used as a reference point for timekeeping worldwide. For a globally distributed team, it provides a common reference for various regions and countries, making it easier to coordinate activities and schedule events across different time zones.
>
>In different parts of the AEP UI, you will see UTC time as the basis of the time scheduling. UTC time is 1 hour behind London time. If you are unsure about the UTC time, simply google "utc time now".

>[!NOTE]
>
>In practice, the **Backfill **option will do a one-time backfill of all the files and subsequent runs will take new files. 

![Scheduling dataflow run.png "Scheduling Dataflow Run"](assets/cZzN2Y9EjzGxqBu9ApqhR_scheduling-dataflow-run.png "Scheduling Dataflow Run")

Review the data flow and click **Finish.**

![Review final dataflow.png "Review final dataflow"](assets/446tbhFUXFtJkijBoFHo3_review-final-dataflow.png "Review final dataflow")

>[!CAUTION]
>
>If you choose the** Run once **option for your dataflow, you will not be able to edit this schedule or update the dataflow later. However, you can run the dataflow on demand i.e. run again if you need to ingest new data.

After you click** Finish**, you will be brought back to the **Dataflows** screen. It should takes a few minutes to create the Dataflow. Notice that Last Dataflow Run Status indicates **No runs**. The first run should kick in a couple of minutes. 

![LxxLyKc0x1oi j WC X0IPG15it9HEbl1R 20241025 032327.png "Dataflows sources screen"](assets/n-ADAXZy_lxxLyKc0x1oi-j-WC_X0IPG15it9HEbl1R-20241025-032327.png "Dataflows sources screen")

>[!CAUTION]
>
>You need to refresh the page continuously to see the status update as the backend does not push updates out to the UI.

>[!NOTE]
>
>If you turned on all the alerts you'll receive an alert in your browser in the upper right corner of your browser when the flow starts running and successfully completes or fails

