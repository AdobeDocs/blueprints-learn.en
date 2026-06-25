---
title: Fix MAPPER Errors for CreateDate
description: Fix MAPPER Errors for CreateDate
doc-type: article
solution: Experience Platform
exl-id: e3f7ef23-6fd1-4f7a-8dc7-db82445322b0
---

In this exercise, you will need to figure out how to remove the MAPPER error that we saw in the batch ingestion lab. The error needs to be fixed because even though createDate is not a required field, the records are being ingested in by transforming this badly formatted date into an empty field. 

![Createdate format has an issue that is causing the mapper error](assets/1j1anUX1zntMpBxPU57c2_createdate-format-has-an-issue-that-is-causing-the-mapper-error.png)

