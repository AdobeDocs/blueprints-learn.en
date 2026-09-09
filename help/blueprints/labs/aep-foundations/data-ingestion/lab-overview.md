---
title: Lab Overview
description: Review the goals and syllabus for the data ingestion labs, from schema mapping and passthrough fixes to dataflow debugging and validation.
doc-type: article
solution: Experience Platform
exl-id: 04decc87-65d2-40b4-8c14-e2f7e911304d
---

# Lab Overview

## Goals

The goal of these labs is to prepare you to deal with the practical challenges of data ingestion. With this understanding, you will be able to handle, manage, and guide your team on data implementations in production. As much as the theory is fascinating, we will be spending time debugging issues as they come up and connect what we see in the tool to that of the broader concepts taught in this bootcamp. 



## What to Expect

I need your focus. Here is why: data will be the foundation of any implementation you will ever do. 

Data problems are not easy. Data is messy, incomplete, scattered and hard to bring into the system where you need it. These labs are designed to give you a taste of those scenarios.  

These next set of labs will require attention and dedication as you will be touching the innards of the system. It is not expected that you will absorb all the concepts in one go and so take the time to find your way in the lab.



## Syllabus in a Nutshell

Since you have source schemas and you have defined target schemas in XDM, you will need to connect the two schemas through mappings. Since this process requires a field by field mapping, you will need to learn some techniques that speed up the process while being aware of some common pitfalls:

- Understand passthrough mappings
- Fix AI/ML generated passthrough mappings
- Use source data preview to check any data quality issues

Once the schema mapping is set up, you will need to put your work to the test and debug errors and warnings:

- Schedule a dataflow run
- Mark a dataset for Profile
- Deal with errors arising from missing values in required fields
- Deal with errors arising from data type mismatch errors
- Deal with data ingest errors and recover from such failures
- Iteratively use test data to generate a comprehensive mapping set. 
- Verify and validate the data ingested successfully.

You will learn the above concepts with relational and non-relational data ingestion scenarios.
