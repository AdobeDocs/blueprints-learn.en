---
title: Intake and Create blueprint
description: Intake and Create - Marketo Engage and Workfront integration blueprint
exl-id: 09679521-727c-4676-8e91-23d0b7fd54a2
---
# Intake and Create blueprint {#intake-and-create}

The number of marketing requests coming into a marketing operations team to launch new campaigns can turn a high functioning team into a revolving door of repetitive tasks, causing burnout and stagnating innovation.

By establishing a process for submitting campaign requests and automating the creation of commonly requested marketing campaigns, you can: increase the velocity of your campaigns, reduce errors, route requests to the right member of marketing operations, balance and improve resource utilization, and focus more of your marketing operations on more strategic tasks.

With Workfront and Marketo Engage, a system-to-system connection allows details from a [Workfront request form](https://experienceleague.adobe.com/docs/workfront/using/administration-and-setup/customize/custom-forms/create-or-edit-a-custom-form.html){target="_blank"} to create a Marketo Engage Program, then fill in key variables such as: subject lines, email copy, images, dates, times, event information, and more.

To achieve this integration, you'll use Workfront Fusion, a work automation layer that allows you to automate workflows between Workfront and other systems.

The workflow below shows a request for a webinar being made by a campaign manager using a Workfront request form. The details submitted in the request then trigger a program and email to be created in Marketo Engage for the webinar. Additionally, details are taken from the request form to populate the content of the email.

![Intake and Create blueprint](assets/intake-and-create-1.png){zoomable="yes"}

>[!TIP]
>
>To learn more about the different types of objects in Workfront used for organizing marketing campaign work and how it's mapped to a Marketo Engage program, check out the [Marketo and Workfront Overview](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md){target="_blank"}.

## Prepare your campaign development process for automation {#prepare-your-campaign-development-process-for-automation}

Behind every great workflow automation is a defined process that ensures teams and stakeholders are getting the most value from the automation.

**What types of marketing requests will you receive?**

Think about what types of marketing tactics you'll run such as emails, nurture, first party webinars, and events. Do you also run 3rd-party Webinars or Display Ads? Each of these requests should be considered as they may need specific input fields in the request form and will map to different program templates in Marketo Engage that will be cloned.

You'll also want to understand if you're running campaigns in multiple regions. If this is the case, you'll want to account for one Project in Workfront creating multiple programs in Marketo Engage, with each program representing different language support.

It's important to know up front what types of marketing requests you expect to receive to ensure requests can be facilitated in an automated manner.

**What information should be captured in the campaign request?**

Think about the key pieces of information that will need to be captured in your request form for each of the different tactics you run. Below are some examples of information that you can capture in a Workfront form to help automate your campaign development.

<table> 
  <tr> 
   <td><b>Marketing Tactic</b></td>
   <td><b>Information to Capture</b></td>
  </tr>
  <tr> 
   <td>Email Blast</td>
   <td>&#x2022; Email Subject<br />
&#x2022; Scheduled Date<br />
&#x2022; Email Copy<br />
&#x2022; Call to Action<br />
&#x2022; Image(s) - AEM Assets URLs can be directly referenced for use in Marketo<br />
&#x2022; Audience Qualification Criteria</td>
  </tr>
  <tr>
   <td>Webinar/Event</td>
   <td>&#x2022; Event Name<br />
&#x2022; Event Date<br />
&#x2022; Event Time<br />
&#x2022; Event City<br />
&#x2022; Event Description<br />
&#x2022; Webinar Recording Page - PageURL OnDemand<br />
&#x2022; Speaker Names<br />
&#x2022; Speaker Titles<br />
&#x2022; Speaker Images<br />
&#x2022; Emails Needed (Invite, Confirmation, Reminder, Follow-up)<br />
&#x2022; Email Header Image(s)<br />
&#x2022; Audience Qualification Criteria</td>
  </tr>
  <tr>
   <td>Nurture</td>
   <td>&#x2022; Number of emails<br />
&#x2022; Email Copy<br />
&#x2022; Email Headers<br />
&#x2022; Call to Action<br />
&#x2022; Audience Qualification Criteria</td>
  </tr>
  </tbody>
</table>

>[!NOTE]
>
>Today, programmatically building audiences through automation is limited in Marketo Engage because tokens are not supported in smart lists. This means audiences will need to either be created in Marketo Engage by a user, or if you have a predetermined audience you continuously communicate to, you can include a configured smart list as part of your program template that's cloned during the automation process.

### Establish your center of excellence {#establish-your-center-of-excellence}

If you want to automate the creation of programs, you'll need a center of excellence in Marketo Engage. A center of excellence includes templatized programs and assets to help expedite and standardize the campaign development process. For example, you might have a program template for your different campaign needs: email, nurture, in-person event, and webinar. Additionally, you may have multiple email program templates that you use for different regions or different types of email announcements.

Building out your center of excellence with program templates in Marketo Engage is one of the first steps to having a more programmatic approach to campaign execution and will act as a foundation to automating campaign requests.

Once you have a set of reusable program templates, you can further scale your efforts using automation outlined in this blueprint to drive more velocity to your campaign development.

To learn more on creating your own center of excellence, check out the [Marketo Community](https://nation.marketo.com/t5/product-blogs/marketo-master-class-center-of-excellence-with-chelsea-kiko/ba-p/243221){target="_blank"} for best practices.

### Use tokens to populate content {#use-tokens-to-populate-content}

With Marketo Engage, tokens can be used to populate content into your campaign assets. For example, after cloning an email template from your center of excellence, Workfront Fusion can take details from the campaign request in Workfront and pass them to the My Tokens in the Marketo Engage program. The token values can then be inherited directly into the email to build the email out.

![Use tokens to populate content diagram](assets/intake-and-create-2.png){zoomable="yes"}

### Populate images from AEM Assets {#populate-images-from-aem-assets}

You can further automate your email and landing page development by utilizing Marketo Engage tokens in combination with links to assets in AEM Assets. Campaign requesters can submit published image links from AEM Assets as part of the request process. Workfront Fusion can then take those links and embed them into the HTML of an email using Marketo Engage tokens.

Remember, you will need to build out your Programs and Program Templates in Marketo Engage to utilize My Tokens so that Fusion can update the token values with the information submitted in Workfront.

>[!NOTE]
>
>AEM Assets is not required to support this workflow but can allow a more streamlined process for managing campaign assets across the campaign development supply chain.

### Assemble a lookup library for all program request types {#assemble-a-lookup-library-for-all-program-request-types}

When automating the creation of new Marketo Engage programs from Workfront requests, it's important to include a step in your Workfront Fusion automation that can take information from the Workfront request and lookup the correct program templates that should be cloned in Marketo Engage.

To do this, you can import a dataset in Workfront Fusion that includes a list of all the different program templates in your Marketo Engage center of excellence.

Some basic information to include in your Program Template Lookup Library are:

<table> 
  <tr> 
   <td><b>Column</b></td>
   <td><b>Description</b></td>
  </tr>
  <tr> 
   <td>Campaign Type</td>
   <td>This could be email, webinar, nurture, event, third-party webinar, list import etc… The Campaign Type will act as a readable description for what is being requested.</td>
  </tr>
  <tr> 
   <td>Workfront Request Type</td>
   <td>This is the request type that is selected in the Workfront form, this could be the same as campaign type, like email, webinar, nurture, or event. This is used to map the input that is selected in the Workfront form to a Program Template in Marketo.</td>
  </tr>
  <tr> 
   <td>Workfront Form ID</td>
   <td>The unique ID of the Workfront request form used, to validate the write request is being mapped to the Marketo Engage Program Template.</td>
  </tr>
  <tr> 
   <td>Marketo Program ID</td>
   <td>This is the ID of the program template in Marketo Engage that maps to the request that is being made. Having this information readily available in Workfront Fusion will allow Fusion to make the request to Marketo Engage and know exactly what program to clone.</td>
  </tr>
  </tbody>
</table>

## Intake and Create automation flow {#intake-and-create-automation-flow}

Here's an example of how the workflow logic can be assembled in Fusion using prebuilt [Workfront](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/fusion-apps-and-modules/workfront-modules.html){target="_blank"} and [Marketo Engage](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/fusion-apps-and-modules/marketo-modules.html){target="_blank"} modules that enable you to deliver automation faster.

![Intake and Create automation flow](assets/intake-and-create-3.png)

## Resources {#resources}

* [Adobe Marketo Engage Modules](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/fusion-apps-and-modules/marketo-modules.html){target="_blank"}

* [Adobe Workfront Modules](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/fusion-apps-and-modules/workfront-modules.html){target="_blank"}

* [Marketo and Workfront Overview](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md){target="_blank"}
