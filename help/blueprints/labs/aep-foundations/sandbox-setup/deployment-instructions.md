---
hold: true
title: Deployment instructions
description: Use the DEP CLI to deploy the AEP Foundations lab pack's schemas, datasets, dataflows, and sample profile data to your sandbox.
doc-type: article

solution: Experience Platform
exl-id: 9f2b6d4a-8e1c-4b7a-a3d5-6c9f0e2a4b8d
---

# Deployment instructions

> [!NOTE]
>
>This is only required if you're working through the labs at your own pace. If you're in a live training course or event, your sandbox has already been deployed for you.

The AEP Foundations lab pack is deployed to your sandbox using the DEP CLI, a command-line tool that creates the schemas, datasets, dataflows, and sample data you'll use throughout the labs.

## What gets deployed

- 4 identity namespaces
- 1 schema class, 13 field groups, 10 schemas
- 12 identity descriptors, 6 relationship/reference descriptors, 3 friendly name descriptors
- 10 catalog datasets
- 1 HTTP API source connection and 10 dataflows
- Profile data: a single Depeche Mode profile (3 trait datasets, 7 event datasets) plus 3 lookup datasets
- 2 profile merge policies and 1 audience (Any Event Streaming, within the hour)

>[!NOTE]
>
>End-to-end deployment takes about 2 hours 24 minutes, most of which is unattended wait time between steps. The CLI enforces these waits automatically, so you don't need to time anything yourself.

## Prerequisites

- **License Entitlements.** Administrative privileges for an IMS Org with Real-Time CDP (w/streaming segmentation)
- **Access Rights.** An Adobe Experience Platform role with all permissions on the target sandbox including the API credential you created from [Developer Console Setup](developer-console-setup.md).
- **Developer Console credentials.** A project that includes Adobe Experience Platform APIs. If you don't have these yet, follow [Developer Console Setup](developer-console-setup.md) first
- **A sandbox.** Empty, of type `dev` and in a "Ready" state for at least 60 minutes before you start deployment
- **Node.js.** Any recent LTS version, on Windows or Mac

## 1. Install the CLI

1. Clone or download the [dep-cli repository](https://github.com/adobe/dep-cli)
1. From the `dep-cli` directory, run `npm install`
1. Start the CLI with `npm start`

>[!NOTE]
>
>Node.js is required before you run the commands above. If you don't have Node.js installed yet, see the wiki's [Node.js Setup ](https://github.com/adobe/dep-cli/wiki/Nodejs-Setup)page first. For full install details, including screenshots and how to update an existing install, see the [Installation ](https://github.com/adobe/dep-cli/wiki/Installation)wiki page

## 2. Configure your environment file

The CLI deploys to whichever sandbox your environment file points at, so this has to be set up correctly before you run anything.

1. Copy `envFiles/sample-env.json` and give it a new name, e.g. `my-env.json`
2. Open the file and fill in the following fields using the values from [Developer Console Setup](developer-console-setup.md):

| **Field**       | **Value**                                                                                                                             |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| `API_KEY`       | Client ID                                                                                                                             |
| `CLIENT_SECRET` | Client Secret                                                                                                                         |
| `IMS_ORG`       | Organization ID                                                                                                                       |
| `SCOPES`        | Must include Experience Platform API scopes (openid, session, AdobeID, read_organizations, additional_info.projectedProductContext) |
| `SANDBOX_NAME`  | The sandbox you're targeting — must be empty and of type `dev`                                                                        |

3. Save and close the file

>[!NOTE]
>
>You're prompted for this file's name each time you run a CLI command, so you can reuse it across every step below.

## 3. Run the AEP foundations menu

From the main menu, select **AEP foundations**. There are three steps, and they have to run in order.

>[!WARNING]
>
>The sandbox must have been in a "Ready" state for at least 60 minutes before you run Step 1.

| **Step**                | **What it does**                                                              | **Before you run it**           |
| ----------------------- | ------------------------------------------------------------------------------------------ | ------------------------------- |
| 1. Create profile base  | Deploys identity namespaces, schemas, datasets, merge policies, and audiences | Sandbox "Ready" for 60+ minutes |
| 2. Load profile data    | Creates dataflows and streams profile and lookup data                         | Wait 60+ minutes after Step 1   |
| 3. Check profile health | Validates that all data loaded correctly                                      | Wait 15+ minutes after Step 2   |

Step 1 takes about 2 minutes to run, Step 2 about 6 minutes, and Step 3 is a quick validation with no wait of its own. The 60- and 15-minute gaps between steps are for AEP to finish propagating data behind the scenes — that's most of your 2-hour timeline.

> [!NOTE]
>
>The CLI checks these wait times automatically. If you run a step too early, it blocks and tells you how many minutes remain — you don't need to track the clock yourself.

>[!NOTE]
>
>Step 2 is safe to re-run if something goes wrong. It overwrites existing trait records and skips duplicate events.

## Troubleshooting

>[!WARNING]
>
>**Health check fails with missing events**. Some profile data hasn't finished propagating yet. Wait another 15 minutes and re-run Check profile health. If it still fails, re-run Load profile data, wait 15 minutes, and check again.

**Something else looks wrong.** As a last resort, you can reset the sandbox from the CLI's Sandbox management menu and redeploy from Step 1.

>[!CAUTION]
>
>Resetting a sandbox is destructive. The CLI asks you to type the sandbox name to confirm before proceeding.
