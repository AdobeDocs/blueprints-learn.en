---
title: Setup
description: Complete the sandbox deployment and Postman configuration steps required before starting the AJO Foundations labs.
doc-type: article

solution: Experience Platform
exl-id: 7c1a9e3d-5b8f-4a2e-9c6d-3f7b0e4a8c2d
---

# Setup

Before you start the AJO Foundations labs, complete the setup steps below. Which steps you need depend on how you're taking this bootcamp.

## Sandbox setup

>[!NOTE]
>
>If you're in a live training course or event, your sandbox has already been deployed for you — skip this section and go straight to Postman setup below.

If you don't already have a working sandbox with the lab assets deployed, complete the following steps:

- [Developer Console setup](sandbox-setup/developer-console-setup.md)
- [Deployment instructions](sandbox-setup/deployment-instructions.md)

## Postman setup

Postman is required for the labs in this course, regardless of how your sandbox was provisioned. Complete the following before continuing:

- [Postman installation](postman-setup/postman-installation.md)
- [Import environment file](postman-setup/import-environment-file.md)
- [Import API collection](postman-setup/import-api-collection.md)

## Channel prerequisites

Two labs later in this bootcamp depend on external accounts that only self-paced learners need to arrange — if you're in a live training course or event, these are already provisioned for you.

### Delegated subdomain

The [Configure email channels](data-stores/configure-email-channels/overview.md) lab — and everything that depends on it ([Message delivery in action](orchestrated-campaigns/message-delivery-in-action/overview.md), [Post-purchase excitement](journeys/post-purchase-excitement/overview.md), and [AJO Brands](content-authoring-with-ai/overview.md)) — requires a subdomain delegated to Adobe for sending email. If you don't already have a domain, register one with any domain registrar (for example, Namecheap), then follow Adobe's [subdomain delegation instructions](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/delegate-subdomains/delegate-subdomain) to delegate a subdomain of it (e.g. `email.yourdomain.com`) to Adobe.

>[!NOTE]
>
>Subdomain delegation can take time to propagate. Start this well before you plan to reach the Configure email channels lab.

### SMS credentials

The [Flagship phone launch](orchestrated-campaigns/flagship-phone-launch/overview.md) lab configures an SMS channel through Twilio. No messages are actually sent, but you need working credentials to complete the configuration. The simplest option is a free [Twilio trial account](https://www.twilio.com/try-twilio) — see Twilio's [getting started guide](https://www.twilio.com/docs/usage/tutorials/how-to-use-your-free-trial-account) for how to sign up and find your Account SID and Auth Token.
