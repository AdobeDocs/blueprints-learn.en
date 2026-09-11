---
title: Developer Console setup
description: Create an Adobe Developer Console project with OAuth Server-to-Server credentials for the Experience Platform and Journey Optimizer APIs used by the DEP CLI.
doc-type: article

solution: Experience Platform
exl-id: 8b8f2a3e-2f4a-4b0e-9c5a-6e0c2b7a1d4f
---

# Developer Console setup

>[!WARNING]
>
>This is only required if you're working through the labs at your own pace. If you're in a live training course or event, your sandbox has already been deployed for you.

The DEP CLI authenticates to your sandbox using OAuth Server-to-Server credentials from an Adobe Developer Console project. This page walks through creating that project. You only need to do this once — the same credentials work across both the AEP Foundations and AJO Architectural Foundations tracks, as long as you add both APIs described below.

>[!NOTE]
>
>If you already have a Developer Console project with credentials for Adobe Experience Platform (and, if needed, Adobe Journey Optimizer), skip this section and go straight to [Deployment instructions](deployment-instructions.md).

## Prerequisites

- An Adobe ID with developer access to your organization
- An Adobe Experience Platform sandbox that is empty and of type `dev`
- An Adobe Experience Platform role with all permissions granted for that sandbox (ask your system administrator if you're not sure)

## Create the project

1. Go to [Adobe Developer Console](https://developer.adobe.com/console) and sign in
1. If you have access to more than one organization, use the org switcher in the top right to select the correct one
1. Select **Create new project**
1. Rename the project to something you'll recognize later (e.g., `DEP Sandbox`)

## Add Experience Platform API

1. From the project overview, select **Add API**
1. Choose the **Adobe Experience Platform** product icon, then select **Adobe Experience Platform API**
1. Select **Next**
1. Choose **OAuth Server-to-Server** as the authentication type and select **Next**
1. Give the credential a name and select **Next**
1. Select the product profile that matches the sandbox you're using, then select **Save configured API**

## Add Adobe Journey Optimizer API

1. From the project overview, select **Add API** 
1. Choose the **Adobe Journey Optimizer** product icon and select the relevant API 
1. Select **OAuth Server-to-Server** 
1. Select the same product profile and select **Save configured API** 

>[!NOTE]
>
>Reuse the credential you created above instead of creating a new one — the CLI only needs a single set of credentials, with combined scopes.



## Collect your values

Open your credential's **OAuth Server-to-Server** overview page. You'll need four values for the CLI's environment file:

| **Dev Console value** | **Env file field**              |
| --------------------- | ------------------------------- |
| Client ID             | `API_KEY`                       |
| Client Secret         | `CLIENT_SECRET`                 |
| Organization ID       | `IMS_ORG` (ends in `@AdobeOrg`) |
| Scopes                | `SCOPES`                        |

>[!NOTE]
>
>Copy the default scopes shown on the credential page — you don't need to add anything manually. If you added both APIs above, the scopes list will include both automatically.

Keep this page open, or copy these four values somewhere safe. You'll paste them into the CLI's environment file in the next step of your track's setup guide.
