---
title: Review and approve blueprint
description: Review and approve blueprint - Marketo Engage and Workfront integration blueprint
exl-id: a446faab-7db4-42a2-b4b9-395725c49c9f
---
# Review and approve blueprint {#review-and-approve-blueprint}

Making sure marketing assets and campaigns meet the expectations and standards of a business extends beyond delivering the right content and messaging to the right audience. Organizations also bear the responsibility of upholding internal policies, industry regulations, and even legal prerequisites when embarking on new marketing initiatives. By incorporating reviewal and approval steps into their campaign development process, marketing teams can ensure that content and messaging is accurate and in compliance with their industry standards, particularly for industries like finance, healthcare, and pharmaceuticals. 

With Workfront and Marketo Engage, marketing teams have the opportunity to have a tightly connected system for marketing, with messaging that's accurate and in compliance.  

## Unlock Proofing and Advanced Approvals for Marketo Engage with Workfront {#unlock-proofing-and-advanced-approvals}

When we think about building marketing campaigns, we must consider that multiple systems support the different steps involved, including: planning, building, reviewing, feedback, approval, and executing. With Workfront and Marketo Engage, teams have all the tools necessary to take them through the end-to-end process of planning and launching a new marketing campaign. Additionally, teams can further streamline their review and approval process to increase campaign development speed while ensuring that accuracy and compliance are held to the highest standard.  

### Review and Approve use cases unlocked with Marketo Engage and Workfront {#review-and-approve-use-cases-unlocked-with-marketo-engage-and-workfront}

* Eliminate disparate feedback and increase collaboration in a centralized place by utilizing Workfront's annotation and commenting capabilities on Marketo Engage assets.  

* Centralize your approvals by triggering them in Marketo Engage from Workfront approval workflows.  

* Support and streamline complex approval workflows of marketing assets by utilizing Workfront's advanced approval capabilities with Marketo Engage assets.

* Democratize access of marketing drafts by programmatically pulling Marketo assets into Workfront to be reviewed by multiple stakeholders.

* Track changes and create a paper trail by centralizing all review and proofing work for Marketo Engage assets in Workfront.  

## Planning Your Proof and Approval Workflow {#planning-your-proof-and-approval-workflow}

Before setting up the proof and approval integration between Marketo Engage and Workfront, consider the following aspects: 

* What assets will need to be reviewed and approved? 
* Who will need to be the approver?  
* Will there need to be multiple approvers before a marketing asset can go live? 
* At what point in the campaign development process will marketing assets be assembled and ready to be reviewed?  

Answering these questions will help you get a baseline for what your approval flow will look like and how to begin thinking about configuring your Workfront instance.  

## Building a Proof and Approval Workflow Between Marketo Engage and Workfront {#building-a-proof-and-approval-workflow}

To streamline the proof and approval process between Workfront and Marketo Engage, you can integrate the two solutions using Workfront Fusion. Workfront Fusion provides a workflow interface for triggering actions and passing information between your Workfront and Marketo Engage instances.  

To do this, consider the steps below as part of the process for an integrated review and approval experience.

1. Configure your Workfront Project with a Ready for Review task. 
1. Trigger your Marketo Engage email to sync to Workfront with a task status change. 
1. Convert your Marketo Engage email file to reviewable Proof in Workfront.
1. Use Workfront proofing to collaborate via comments and annotations.
1. Approve the Workfront Proof to trigger asset approval in Marketo Engage, then mark the task as complete.

### Configure a Workfront project with a Ready for Review task {#configure-a-workfront-project-with-a-ready-for-review-task}

Use [project templates](https://experienceleague.adobe.com/docs/workfront/using/manage-work/projects/create-and-manage-project-templates/project-template-overview.html){target="_blank"} to capture most of the repeatable processes, information, and settings associated with the projects in your organization. You can define tasks, queue topics, create custom forms, and attach documents in your template. 

In your project template in Workfront, include tasks for reviewing assets that are part of your marketing campaign. Additionally, you can add an approval process to handle single approvals, or more complex multi-level approvals.  

If you want to launch a new email campaign, you should have a project template that includes a task to review the email, as well as an approval process for ensuring the email is approved by the right stakeholder before it can be sent out.   

![tasks screen](assets/review-and-approve-blueprint-1.png){zoomable="yes"}

### Trigger your Marketo Engage email to sync to Workfront with task status change {#trigger-your-marketo-engage-email-to-sync-to-workfront}

As part of your review process, you'll want to be able to sync emails to your Workfront project once they're ready for review by your marketing team. To do this, we recommend setting up a Ready to Review task with a [task status](https://experienceleague.adobe.com/docs/workfront/using/manage-work/projects/update-work-on-a-project/update-task-status.html){target="_blank"} that signifies when the email is ready to be reviewed. In our example, we added a Review Marketo Email status to our task that can be selected when the email draft is ready to be reviewed by stakeholders.

With this status in place in your Workfront project, you can configure your Workfront Fusion scenario to listen for the Ready to Review task to update to "Review Marketo Email." Once updated, your scenario can retrieve the Marketo Engage email as an HTML file, zip it up, and save a copy of it in the Workfront project documents to be reviewed.  

![ready for review screen](assets/review-and-approve-blueprint-2.png){zoomable="yes"}

### Convert your Marketo Engage email to reviewable Proof in Workfront {#convert-your-marketo-engage-email-to-reviewable-proof-in-workfront}

Once your Ready for Review task is moved to the "Review Marketo Email" status and the Marketo Engage email is saved in Workfront, you can configure your Workfront Fusion scenario to convert the email into a Workfront Proof.

### Use Workfront proofing to collaborate via comments and annotations {#use-workfront-proofing-to-collaborate}

[Workfront's proofing](https://experienceleague.adobe.com/docs/workfront/using/review-and-approve-work/proofing/proofing-overview/proofing-basics.html){target="_blank"} capabilities allow your marketing team to take a new asset, such as an image or an email, and collaborate via comments and annotation. Once a proof is ready to go live, decision-makers can approve the asset from the proofing tool.

![convert email screen](assets/review-and-approve-blueprint-3.png){zoomable="yes"}

### Approve Workfront Proof and trigger asset approval in Marketo Engage, mark task as complete {#approve-workfront-proof-and-trigger-asset-approval-in-marketo-engage}

Workfront Fusion can detect when the email has been approved by stakeholders and send a request to Marketo Engage to approve the email inside Marketo.  

With the email reviewed/approved by the right team members, the email is ready to go live in Marketo Engage!

## Fusion Scenario Templates {#fusion-scenario-templates}

To help streamline your development of Review and Approve workflows in your own Workfront and Marketo Engage instance, we've built out Fusion Templates that will help you get started with the integration. You can utilize these templates by searching "Marketo" in the Public Templates section of Fusion and downloading them to your instance.  

### Review an email Proof of your Marketo Engage email draft in Workfront {#review-an-email-proof-of-your-marketo-engage-email-draft-in-workfront}

The fusion scenario below will take you through the first half of the review and approve flow, in which the email draft can be pulled from Marketo Engage and saved to Workfront as a Proof. Once saved as a Proof to the Workfront project documents, it can be reviewed by marketing stakeholders, commented on, and annotated as part of the review process.

![fusion scenario review and approve flow](assets/review-and-approve-blueprint-4.png){zoomable="yes"}

### Approve an email in Workfront that triggers the approval of the asset in Marketo Engage {#approve-an-email-in-workfront-that-triggers-approval}

The fusion scenario below can be used to detect when a Proof in Workfront has been approved, and route that approval to Marketo Engage to update the email draft so that it's live and ready to be used in a Marketo Engage program.

![fusion scenario proof approval](assets/review-and-approve-blueprint-5.png){zoomable="yes"}

Together, these two scenarios can be used to create a two-way path for pulling marketing assets from Marketo Engage into Workfront's robust review and approve workflows, and push approvals back to Marketo Engage from Workfront.
