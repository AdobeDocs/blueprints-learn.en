---
title: Deployment Instructions
description: Use the DEP CLI to deploy the AJO Architectural Foundations lab pack's schemas, datasets, dataflows, and sample data to your sandbox.
doc-type: article

solution: Experience Platform
exl-id: 3d6e9a1c-7b2f-4e8a-9d0c-1f5a8b6c2e3d
---

>[!WARNING]
>
>This is only required if you're working through the labs at your own pace. If you're in a live training course or event, your sandbox has already been deployed for you.

The AJO Architectural Foundations lab pack is deployed to your sandbox using the DEP CLI, a command-line tool that creates the schemas, datasets, dataflows, and sample data you'll use throughout the labs — covering both the profile store and the AJO relational store used for orchestrated campaigns.

## What gets deployed

**Profile track**

- Identity namespaces (customerID, planID, productID)
- Standard XDM field groups, descriptors, and schemas enabled for profile
- Catalog datasets enabled for profile
- Merge policies and audiences
- Profile data for three sample datasets: Depeche Mode (traits + events), Stranger Things (traits), and Decisioning (traits)

**Relational track**

- The customerID identity namespace
- 11 relational XDM schemas with primary key, foreign key, and version descriptors
- 11 datasets enabled for AJO orchestrated campaigns
- 11 dataflows loading data from the Data Landing Zone

>[!NOTE]
>
>End-to-end deployment takes about 2 hours 23 minutes. The profile and relational tracks run in parallel, and most of the time is unattended wait time that the CLI enforces automatically.

## Prerequisites

- **License Entitlements.** Administrative privileges for an IMS Org with Real-Time CDP (w/streaming segmentation) and Adobe Journey Optimizer (w/Orchestrated Campaigns)
- **Access Rights.** An Experience Platform role with all permissions on the target sandbox including the API credential you created from [Developer Console Setup](developer-console-setup.md).
- **Developer Console credentials.** A project that includes both Adobe Experience Platform API and Adobe Journey Optimizer API's. If you don't have these yet, follow [Developer Console Setup](developer-console-setup.md) first
- **A sandbox.** Empty, of type `dev` and in a "Ready" state for at least 120 minutes before you start deployment
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
1. Open the file and fill in the following fields using the values from [Developer Console Setup](developer-console-setup.md):

| **Field**       | **Value**                                                                                                                                                                                                                                                           |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `API_KEY`       | Client ID                                                                                                                                                                                                                                                           |
| `CLIENT_SECRET` | Client Secret                                                                                                                                                                                                                                                       |
| `IMS_ORG`       | Organization ID                                                                                                                                                                                                                                                     |
| `SCOPES`        | Must include both Experience Platform API and Adobe Journey Optimizer API scopes<br />*(e.g. cjm.suppression\_service.client.delete, cjm.suppression\_service.client.all, openid, session, AdobeID, read\_organizations, additional\_info.projectedProductContext)* |
| `SANDBOX_NAME`  | The sandbox you're targeting — must be empty and of type `dev`                                                                                                                                                                                                      |

1. Save and close the file

>[!NOTE]
>
>You'll be prompted for this file's name each time you run a CLI command, so you can reuse it across every step below.

## 3. Run the AJO Architectural Foundations menu

From the main menu, select **AJO arch foundations**. There are six steps split across two tracks.

### Profile track (run in order)

>[!WARNING]
>
>The sandbox must have been in a "Ready" state for at least 60 minutes before you run Step 1.

| **Step**                | **What it does**                                                                          | **Before you run it**           |
| ------------------------ | ------------------------------------------------------------------------------------------- | ---------------------------------- |
| 1. Create profile base  | Deploys identity namespaces, schemas, datasets, merge policies, and audiences             | Sandbox "Ready" for 60+ minutes |
| 2. Load profile data    | Creates dataflows and streams Depeche Mode, Stranger Things, and Decisioning profile data | Wait 60+ minutes after Step 1   |
| 3. Check profile health | Validates that all profile data loaded correctly                                          | Wait 15+ minutes after Step 2   |

Step 1 takes about 2 minutes, Step 2 about 6 minutes.

>[!NOTE]
>
>Step 2 is safe to re-run if something fails — it overwrites existing traits and skips duplicate events.

### Relational track

>[!WARNING]
>
>The sandbox must have been in a "Ready" state for at least 120 minutes before you run Step 4 or Step 6.

| **Step**                         | **What it does**                                                             | **Before you run it**                           |
| ----------------------------------- | -------------------------------------------------------------------------------- | ---------------------------------------------------- |
| 4. Create relational base        | Creates the customerID namespace and relational schemas/descriptors/datasets | Sandbox "Ready" for 120+ minutes                |
| 5. Load relational data          | Uploads 11 CSV files and creates the dataflows that load them                | Runs right after Step 4 — no manual wait needed |
| 6. Deploy relational base & data | Combines Steps 4 and 5 into a single ~5-minute run                          | Sandbox "Ready" for 120+ minutes                |

>[!NOTE]
>
>Use Step 6 instead of running Steps 4 and 5 separately — it does the same thing in one pass with the propagation wait handled for you.

>[!WARNING]
>
>All wait times above are checked automatically by the CLI. If you run a step too early, it will block and tell you how long to wait.

## Troubleshooting

>[!WARNING]
>
>**Profile health check fails with missing events.** Some profile data hasn't finished propagating yet. Wait another 15 minutes and re-run Check profile health. If it still fails, re-run Load profile data, wait 15 minutes, and check again.

>[!WARNING]
>
>**Relational data load fails partway through.** Each API call retries up to 3 times. If it still fails, cleanup removes the source connections, target connections, and dataflows it created so you can re-run Step 5 (or Step 6) cleanly. Mapping sets can't be deleted through the API and may be left behind — this doesn't affect redeployment.

**Something else looks wrong.** As a last resort, you can reset the sandbox from the CLI's Sandbox management menu and redeploy from Step 1.

>[!CAUTION]
>
>Resetting a sandbox is destructive. The CLI will ask you to type the sandbox name to confirm before proceeding.
