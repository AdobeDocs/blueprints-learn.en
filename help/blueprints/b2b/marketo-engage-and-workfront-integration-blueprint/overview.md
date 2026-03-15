---
title: Marketo Engage and Workfront integration blueprint overview
description: Overview - Marketo Engage and Workfront integration blueprint overview
exl-id: c1da95d0-0649-4e69-aade-3ddcb89d2d31
---
# Marketo Engage and Workfront integration blueprint overview {#overview}

## Achieve faster time-to-market with Marketo Engage and Workfront {#achieve-faster-time-to-market-with-marketo-engage-and-workfront}

The job of marketing continues to grow with new channels and more ways to personalize communications every day. Marketing teams need ways to continue to automate and evolve to support changing marketing demands around the world.

**"ROI has always been the real goal. Revenue is great, but not at any cost- especially today." - CMO, Business Services Industry**

Organizations that are achieving higher ROI while growing their revenues are doing so by streamlining their campaign development process, optimizing their campaign execution velocity and improving oversight across the entire marketing function.

If your organization is looking to accomplish similar goals outlined below, this document will be useful to you:

* Scale campaign operations to support cross-functional marketing teams
* Faster time to market with streamlined campaign request process
* Establish a system of record to increase visibility across campaign stakeholders
* Review and approve campaign assets (images, email copy)

Campaign operation teams need systems that allow them to efficiently and effectively plan and execute marketing campaigns. Whether it's an email, webinar, event, paid media, nurture or content syndication, marketing teams need a central solution to organize campaign contributors, deliverables, and execution.

By integrating multi-channel marketing activation system (Marketo Engage) with the marketing planning and system of record (Workfront) you can increase campaign velocity and provide better visibility to stakeholders.

With Workfront Fusion, marketing operations teams can largely eliminate manual and error-prone steps involved in translating a marketing brief to a campaign. Workfront Fusion offers an out of the box integration layer between Workfront and Marketo Engage that allows for flexibility and efficiency in developing workflows between systems. You can learn more about how to set up the integration and what actions can be taken to automate workflows [here](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/fusion-apps-and-modules/marketo-modules.html){target="_blank"}.

## Campaign planning to execution - automation use cases {#campaign-planning-to-execution-automation-use-cases}

* Support marketing operations teams by automating the creation of campaigns in Marketo Engage through intake requests in Workfront
* Share drafts of emails and landing pages created in Marketo Engage to Workfront to get final review and approval from cross-functional stakeholders
* Share campaign results from Marketo Engage to Workfront to democratize access to campaign metrics

Below you can see a workflow diagram of the campaign development process in the case of an email blast request. Additionally, you can see how Workfront Fusion can play a role between Workfront and Marketo Engage to drive workflow and process automation across the campaign development cycle.

![Campaign planning to execution - automation use cases](assets/overview-1.png){zoomable="yes"}

Take note of the different phases in the campaign development process.

1. Intake and Create: the request for campaign is made and the campaign assets are programmatically assembled.

1. Review and Approve: once the campaign is assembled it's time for stakeholders to review and sign-off on campaign assets such as emails and landing pages.

1. Report and Audit: share campaign results to Workfront to provide greater visibility to cross-functional stakeholders.

>[!NOTE]
>
>In the example above, Workfront is managing and planning work efforts throughout the lifecycle of the Marketo Engage Program. That said, Workfront's flexibility can extend to managing all your marketing team's efforts. This includes account-based marketing, marketing content supply chains, agency management, digital and social campaign management, and sales enablement programs.

## Understanding how marketing initiatives are represented in Workfront {#understanding-how-marketing-initiatives-are-represented-in-workfront}

Adobe Workfront enables organizations to manage work to drive more efficient execution. Within Workfront there is a hierarchy of objects that provide a framework for planning, resource management, and collaboration across various teams.

Understanding how to map your business process to these objects will be important to understanding the relationship between Workfront and Marketo Engage.

![Understanding how marketing initiatives are represented in Workfront](assets/overview-2.png){zoomable="yes"}

### Portfolio hierarchy defined {#portfolio-hierarchy-defined}

<table> 
  <tr> 
   <td><b>Object</b></td>
   <td><b>Definition</b></td>
  </tr>
  <tr> 
   <td>Portfolio</td>
   <td>You can use Portfolios and Programs in Workfront to organize Projects. Through organizing Projects, you can compare similar Projects and determine where resources will be best spent.<br /><br />
   (e.g., A Portfolio is created for a business unit within a company focused on selling services and/or products.)</td>
  </tr>
  <tr>
   <td>Program</td>
   <td>You can use Workfront Programs to organize Projects. Through organizing Projects, you can compare similar Projects and determine where resources will be best spent.<br /><br />
   (e.g., A marketing strategy with a high-level objective, such as raising awareness and driving demand for a new product launch.)</td>
  </tr>
  <tr>
   <td>Project</td>
   <td>Workfront Projects are a collection of work items that need to be completed to accomplish a specific goal, deliverable, product, etc.<br /><br />
   (e.g., A marketing tactic such as an email blast, a nurture campaign, a webinar, or an in-person event. A single Project can also be more complex by encompassing multiple tactics such as an email, a display ad, a landing page, and a downloadable whitepaper that are all meant to drive the same outcome.)</td>
  </tr>
  <tr>
   <td>Task</td>
   <td>Workfront Tasks are planned work items that may be part of a Project or initiative. Tasks are assigned to users or teams to complete.<br /><br />
   (e.g., A task to build audience segment or create email draft might be task associated with a Project to develop a Marketo Engage Email Program.)</td>
  </tr>
  <tr>
   <td>Issue</td>
   <td>Issues are unplanned work items in Workfront. They may be problems that occur during a Project, or they may be requests that are submitted through a request queue.<br /><br />
   (e.g., An issue is filed because the email banner image has the wrong dimensions.)</td>
  </tr>
  <tr>
   <td>Document</td>
   <td>Documents can be traditional documents like word documents or presentations. They can also be image files. Workfront allows for asset proofing through comments and annotations on documents and images, to enable collaboration amongst teams.<br /><br />
   (e.g., An email header image that needs to be reviewed.)</td>
  </tr>
  <tr>
   <td>Update</td>
   <td>Includes comments and audit logs to track work and facilitate collaboration in Workfront.<br /><br />
   (e.g., Audit log of new image version.)</td>
  </tr>
  </tbody>
</table>

## Marketing initiative work management example {#marketing-initiative-work-management-example}

Let's look at how the Workfront portfolio hierarchy plays out in a real-world example.

The Zeplin Company is releasing an updated version of one of their compact utility tractor attachments called the Z11, which outperforms the previous Z10 model by offering greater durability and customization. With this they need to plan, develop, and execute their marketing strategy to drive demand and raise awareness for their new release from the tractor division of their business. This marketing strategy needs to include different marketing tactics to both raise new customer awareness and existing Z10 customer awareness.

The hierarchy below shows how the strategy, tactics, tasks, and assets map to Workfront for this marketing campaign.

![Marketing initiative work management example](assets/overview-3.png){zoomable="yes"}

## Mapping Workfront to Marketo {#mapping-workfront-to-marketo}

With Workfront as your upstream system for marketing planning and Project organization, it's important to understand how information can be shared between Marketo Engage and Workfront.

In order to have these systems work in tandem as new marketing initiatives are developed, it's important to understand how the different record types in Workfront map to record types in Marketo Engage.

### Mapping Workfront projects to Marketo Engage Programs {#mapping-workfront-projects-to-marketo-engage-programs}

Using Workfront Fusion as an integration layer, you can map your Projects in Workfront to a Program in Marketo Engage. For example, in the case above, Zeplin wants to raise awareness of the new Zeplin model. With this they create a new Program in Workfront that houses multiple marketing tactics that are represented as Projects. One tactic is an awareness email that needs to go out to existing customers of the Z10 model letting them know about the new Z11 model. In Workfront there would be a Project created to represent this email tactic with a set of tasks associated with it for creating the audience, getting creative for the email images, and assembling the email in Marketo Engage. The Project in Workfront can map to an Email Program in Marketo Engage so that information can be synced between systems.

Below you can see an example of how a Program can include multiple projects and how those Workfront Projects can map to Programs in Marketo Engage.

![Mapping Workfront projects to Marketo Engage Programs](assets/overview-4.png){zoomable="yes"}

You may want to kick-off a large marketing initiative that needs multiple Workfront Projects to be housed in a Workfront Program, or you may have a one-off request for a webinar or email that just needs a single Workfront Project created. Whatever your needs are, with Workfront, Workfront Fusion, and Marketo Engage, your team has the flexibility to integrate your campaign development process seamlessly from planning to execution.

### Mapping Workfront tasks to Marketo Engage assets {#mapping-workfront-tasks-to-marketo-engage-assets}

As you begin to map your campaign development process out in Workfront you can also think about what tasks map to work to be done in Marketo Engage and how you can capture information in Workfront, help drive more consistency, efficiency, and accuracy in the campaign development supply chain.

Workfront Projects can be templatized so that your process can be clearly defined each time you run a specific marketing tactic. For example, when executing on an email campaign there will be a standard set of tasks that need to be completed for your organization. These tasks can involve a kick-off meeting with stakeholders, getting creative assets, approving creative, building the target audience, building the email, email translation, approving the email, and sharing email campaign results with stakeholders.

Some of these tasks can map directly to work to be done in Marketo Engage. For example, the build email task in Workfront can be customized to include fields that will pass information to Marketo Engage to automate the assembly of the email. These can include things like the subject line, copy, and images in the email.

## Next steps {#next-steps}

Now that you have a foundational understanding of how Workfront and Marketo Engage can unlock new efficiencies in your campaign development supply chain, check out the following documents and resources on how to automate workflows and process between Marketo Engage and Workfront using Workfront Fusion.

### Getting started with Workfront Fusion, Workfront and Marketo Engage integration {#getting-started-with-workfront-fusion}

* [Intake and Create](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md){target="_blank"} - Campaign Development Automation with Marketo Engage and Workfront

* [Review and Approve](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md){target="_blank"}

### Managing Marketo Engage campaign names and their associated URLs {#managing-marketo-engage-campaign-names}

Standardizing your naming conventions for campaigns and URLs is a key foundation to accurate program management in Marketo Engage and helps drive a more consistent process across the campaign development lifecycle. If you're looking for tools to help with this, we recommend checking out some free open source tools from [Adobe Success Services](https://main--marketo-campaign-tools--dr-adobe.hlx.live/){target="_blank"} that allow you to create a consistent approach to creating and managing Marketo Engage campaigns and their associated URLs.

### Resources {#resources}

* [Workfront Fusion for Marketo Engage](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/fusion-apps-and-modules/marketo-modules.html){target="_blank"}

* [Workfront Fusion for Workfront](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/fusion-apps-and-modules/workfront-modules.html){target="_blank"}
