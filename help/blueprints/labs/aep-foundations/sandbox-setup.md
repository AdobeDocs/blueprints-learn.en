---
hold: true
title: Sandbox Setup
description: Sandbox Setup
doc-type: article

solution: Experience Platform
exl-id: 7f400886-7ddf-4b6b-8ca0-3e417857f963
---

>[!NOTE]
>
>This is only required if you are looking to do this on at your own pace. If you are in a training course or event this will have been already done for you :)



# Lab Assets Deployed

Listed below are all the assets that are deployed as part of the *deploy.json* package.

- Identity Namespaces (4)
- Schema Registry
  - Classes (1)
  - Field Groups (13)
  - Schemas (10)
    - Identity Descriptors (12)
    - Relationship/Reference Descriptors (6)
    - Friendly Name Descriptors (3)
- Catalog Datasets (10)
- Flow Service
  - Source --> HTTP API (1)
    - Dataflows (10) --> all using mapping sets
- Profile Store ([depeche.mode@dep.com](mailto:depeche.mode@dep.com))
  - 3 contributing trait-based datasets (3 records)
  - 7 contributing event-based datasets (43 events)
  - 4 lookup datasets | 22 records
- Profile Merge Policies (2)
  - default merge policy --> system generated
  - dep: No Stitch
- Audiences (1)
  - Any Event Streaming (within the hour)



>[!CAUTION]
>
>Event data spans up to 6 months in arrears based on the date of the deployment. The date is dynamically generated as part of the deployment scripts.  The AEP enviornment you deploy in must be part of a commercial license as non-commerical environments have strict data retention requirements that are not supported with this deployment.



## Files to Download

You will need to download the following files to your local machine to install the lab assets to your individual sandbox.

- Download File — [env.json](assets/env.json)
- Download File — [deploy.json](assets/deploy.json)
- Download File — [health.json](assets/health.json)



## Installing via Newman CLI

## Pre-requisite Software

- [Node.js ](https://nodejs.org/en/download/package-manager/)installed
- [Postman Newman](https://learning.postman.com/docs/collections/using-newman-cli/installing-running-newman/) installed
- Downloaded deployment files



## Installation Instructions

1. Install Newman
1. Download the following files from the repository:
   - env.json --> postman environment file
   - deploy.json --> postman deployment collection
   - health.json --> postman health collection
1. Configure you `env.json` file with the appropriate Developer Console Project credentials and save it.
1. Execute the deployment collection in newman using the following command:

```bash
newman run deploy.json -e env.json --delay-request 750 --bail failure --timeout-script 4800000
```

1. When it completes wait 15mins and then execute the `health.json` collection

```bash
newman run health.json -e env.json --delay-request 750 --bail failure
```



>[!WARNING]
>
>There is a 1hr delay in the deployment execution to ensure that the control plane has had time to fully populate before data is introduced.  If you see failures with data missing you will need to try to manually resend it in or can brute force a sandbox reset and retry deployment.



>[!TIP]
>
>A successful health check run will result in a totalFound count matching the totalExpected count.  This should be 137.



