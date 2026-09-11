---
hold: true
title: Fixing errors
description: Fix a calculated field expression for a date formatting error, then confirm success using the Sources, Identities, and Profiles monitoring metrics.
doc-type: article
solution: Experience Platform
exl-id: 7a3d0c15-4d58-497e-bfa5-9421d5d2eea7
---

# Fixing errors

## Fix birth day and month

1. Click on the arrow icon next to the calculated field populating the **person.birthDayAndMonth** XDM field

![Calculated field expression editor for the birthDayAndMonth fix](assets/fixing-errors-update-the-calculated-expression.png)

1. Update the expression using the below calculated field code and click **Preview**

```none
concat(date_part("mm", date(birth_Date, "M/d/yyyy")).toString(),"-", date_part("dd", date(birth_Date, "M/d/yyyy")).toString())
```

>[!NOTE]
>
>Data should appear as 2 digit month and 2 digit day (i.e. April 27 shown as 04-27). The `mm` and the `dd` parameters add 0 padding.

1. If everything looks good **Save** the calculated field

1. Then click **Finish** to execute the dataflow ingestion.



## Validate ingestion

After a few minutes the dataflow run should run and you should see success!

![Dataflow run status showing a successful Customer Account ingestion](assets/fixing-errors-successful-customer-account-ingestion.png "Successful Customer Account ingestion")



## Monitoring screen

1. Navigate to the monitoring screen by clicking the left rail on the **Monitoring** icon under the **Data Management** section.
1. Click on the **Sources** card and then scroll on the bottom bar to see the details for your dataflow run. Note the following:
   - **Records received:** 20 records were received from the source for processing
   - **Records ingested:** 20 records were ingested into the Data Lake after the mapping and the data processing. 
   - **Records failed:** You should see a 0 here. This represents the total number of INGEST and DCVS errors. It excludes the MAPPER warnings. 
   - **Ingestion rate:** This is the ratio of records ingested to the records received. 100% of the records received were successfully processed

![Sources card on the monitoring screen showing records received, ingested, and failed](assets/fixing-errors-sources-ingestion-metrics.png "Sources ingestion metrics")

>[!NOTE]
>
>With partial data ingestion enabled the **Ingested Rate** for a specific dataflow run can be \<100% up to the threshold you've set as part of the dataflow details. Also, be aware that 100% success will be reported for dataflow runs where no data was ingested.

>[!NOTE]
>
>Note that records cannot be lost.
>
>**Records received** = **Records ingested** + **Records failed**
>
>**Ingestion rate = Records ingested / Records received**
>
>**Partial ingestion threshold = Records failed / Records received**



## Identities

Click on the **Identities** card and then scroll on the bottom bar to see the granular details for your dataflow run. Note the following on the Identity Service

- **Records received:** 20 records were received by the *Identity Store* as it was monitoring for new batches i.e. dataset was marked for Profile.
- **Records ingested:** 20 records were ingested (i.e. processed for identity information)
- **Records skipped:** None as we did not have single identity records or records with now new identity relationships.
- **Success rate (only available in the card):** This is the ratio of the records received to records ingested.
- **Identities Added:** 40 identities (20 each for CustomerID and 20 for email address) were added to the overall identity graph for the Real-Time Customer Profile
- **Graphs Created:** 20 unique graphs were created based on the records it processed (i.e. relationships found in each row of data)
- **Graphs Updated:** This would tell you if identities got added to a graph. 

![Identities card on the monitoring screen showing identity graph metrics](assets/fixing-errors-identity-service-ingestion-metrics.png "Identity Service ingestion metrics")



## Profiles

Click on the **Profiles** card and then scroll on the bottom bar to see the details for your dataflow run. Note the following on the Profile Service:

- **Records received:** 20 records were received by the Profile store for processing
- **Records failed:** None of the records failed. But if they had failed, then you know that it was an ingestion into Profile issue.
- **Profile fragments created:** 20 profile fragments were created
- **Profile fragments updated:** 20 overall profile fragments were touched
- **Success rate:** This is 100%. This is the ratio of records failed to records received.

>[!NOTE]
>
>Observe that **Records skipped** metric is not available for Profile.

![Profiles card on the monitoring screen showing profile fragment metrics](assets/fixing-errors-profile-service-ingestion-metrics.png "Profile Service ingestion metrics")

>[!NOTE]
>
>Note that there is the Destination card and it has metrics that looks similar to what we explored in this lab. These metrics will only make sense once you activate an audience or a dataset.
