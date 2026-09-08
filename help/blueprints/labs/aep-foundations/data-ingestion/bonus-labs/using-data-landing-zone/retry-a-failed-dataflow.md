---
title: Retry a Failed Dataflow
description: Retry a failed dataflow run so the source data is reprocessed against updated mapping rules in a new dataflow.
doc-type: article
solution: Experience Platform
exl-id: 83ecf037-e524-4887-b833-5ed96af40419
---

To retry a workflow, do the following:

1. Navigate to **Sources -> Dataflows -> \[Name of Dataflow] -> \[Failed Run]**
1. Highlight the dataflow run that failed to bring up the right rail.
1. Click on** Retry**. The retry will take the copy of the data associated with the failed run and will now apply the new mapping rules to it

![Retry a failed dataflow](assets/retry-a-failed-dataflow.png)

>[!NOTE]
>
>Note that when you retry a failed dataflow a new dataflow is created and executed. It will appear at the top of the list of dataflows

