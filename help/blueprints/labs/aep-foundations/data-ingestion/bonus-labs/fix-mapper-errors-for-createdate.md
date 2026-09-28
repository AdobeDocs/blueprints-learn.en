---
title: Fix MAPPER errors for CreateDate
description: Troubleshoot and resolve a MAPPER error caused by a badly formatted createDate value that was transforming into an empty field.
doc-type: article
solution: Experience Platform
exl-id: e3f7ef23-6fd1-4f7a-8dc7-db82445322b0
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
---

# Fix MAPPER errors for CreateDate

In this exercise, you will need to figure out how to remove the MAPPER error that we saw in the batch ingestion lab. The error needs to be fixed because even though createDate is not a required field, the records are still ingested because the badly formatted date is transformed into an empty field instead. 

![createDate value with an invalid format causing the MAPPER error](assets/fix-mapper-errors-for-createdate-invalid-format-mapper-error.png)
