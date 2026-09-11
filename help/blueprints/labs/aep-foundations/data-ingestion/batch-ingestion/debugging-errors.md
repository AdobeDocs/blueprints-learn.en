---
title: Debugging errors
description: Use preview error diagnostics to investigate a failed dataflow run and distinguish INGEST format errors from MAPPER conversion warnings.
doc-type: article
solution: Experience Platform
exl-id: beee191b-a860-494c-873f-ab2e407ffbf5
---

# Debugging errors

## Preview error diagnostics

After a few minutes, you should notice that the **Status** shows a failure. Drill into the failure details to see what caused the failure.  

1. Click on **Dataflow Run Start** date
1. Click on the **Preview error diagnostics** to see the specific details on each row that fail

![Dataflow run status showing a failure](assets/debugging-errors-dataflow-run-failure.png "Dataflow run failure")

![Preview error diagnostics link on the dataflow run details screen](assets/debugging-errors-preview-error-diagnostics-link.png "Preview error diagnosis")



The screen you now see shows you a bunch of details about what the error codes mean with the full error message and the row that failed.

![Error diagnostics detail screen showing error codes, messages, and the failed row](assets/debugging-errors-error-diagnostics-detail-screen.png "Error diagnosis preview")

>[!NOTE]
>
>Scroll to the right side to see the source data associated with this error code



## Understanding error types

### INGEST-XXXX-XXX error

This error occurs because **person.birthDayAndMonth** is expected in the format of a two digit month plus a two digit day (i.e. April 27 should be formatted as 04-27)

```none
The value (9-27) does not conform to the specified
regex pattern: [0-1][0-9]-[0-9][0-9] in field: 
person.birthDayAndMonth of type: String
```

>[!CAUTION]
>
>Note that person.birthDayAndMonth is not a required field but non-conformance to regular expression is treated by the system as a "data corruption problem" and is a serious error.  



### MAPPER-XXXX-XXX error

This error occurs because the source field of **createDate** has string values of `Created on 2022-04-22T19:34:17Z`. This value cannot be converted into a date automatically because of the text at the beginning: `Created on`. A calculated field must be used to cleanse the data. 

```none
Error transforming data for destination path 
_dep.account.createDate. Details: Unable to convert 
Created on 2023-09-24T10:19:58Z to schema type DATE_TIME
```

> [!NOTE]
>
>This error is not a serious one as this leads to only warnings during mapping. The dataflow run does not fail because of this, so this lab does not fix this error.
