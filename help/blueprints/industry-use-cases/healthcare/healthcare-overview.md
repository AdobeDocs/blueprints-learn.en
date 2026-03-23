---
title: Healthcare Use Cases
description: Discover how healthcare organizations use Adobe Experience Platform to improve patient engagement, streamline care coordination, and drive better health outcomes.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: 8da82711-a783-488d-a0ed-070b33ecbbc4
---
# Healthcare Use Cases

Healthcare organizations use Adobe Experience Platform to build unified patient profiles and deliver personalized, timely communications across every touchpoint. By connecting clinical, behavioral, and preference data in one place, care teams can engage patients more effectively while maintaining the highest standards of privacy and compliance.

>[!IMPORTANT]
>Healthcare use cases involve protected health information (PHI) subject to HIPAA and other applicable regulations. Before implementing any of these patterns, ensure that [!DNL Adobe Experience Platform] is provisioned as a HIPAA-eligible service and that a Business Associate Agreement (BAA) is in place with Adobe. The technical considerations in each section highlight key compliance requirements but are not exhaustive. Work with your legal, compliance, and security teams to validate your implementation against all applicable regulatory requirements.

## Appointment Reminder Automation

Send personalized appointment reminders through email, text message, and push notifications based on each patient's communication preferences and appointment type. Automated reminders reduce missed appointments and keep schedules running smoothly, freeing staff to focus on patient care.

### Business impact

Organizations that implement automated appointment reminders see measurable improvements in appointment show rates and a meaningful reduction in costly no-shows.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. Appointment creation and update events from the scheduling system serve as natural triggers for timely, relevant reminder messages. This is the right pattern when a discrete appointment event is the trigger and the required response is a single, time-sensitive notification — rather than a sustained engagement sequence, since patients need immediate confirmation without follow-up steps.

### Technical considerations

- Ensure all patient contact information and appointment details are transmitted and stored in compliance with HIPAA requirements, using appropriate data usage labels to restrict unauthorized access.
- Integrate with the electronic health records scheduling system to capture appointment creation, cancellation, and rescheduling events in real time.
- Apply consent management policies so that reminders are only sent through channels the patient has explicitly opted into.
- Configure suppression rules to prevent duplicate or excessive reminders when appointments are rescheduled in quick succession.


## Medication Adherence Campaigns

Send personalized reminders and educational content to help patients stay on track with their medication schedules and treatment plans. Tailored messaging based on medication type, dosing schedule, and patient history drives better adherence and improved health outcomes.

### Business impact

Personalized medication adherence campaigns help drive improvements in adherence rates, leading to better health outcomes and fewer hospital readmissions.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. Medication adherence requires a sustained, multi-touch approach with escalating reminders, educational touchpoints, and follow-up check-ins over the course of a treatment plan. This is the right pattern because medication management requires a sequenced, multi-message flow over days or weeks with conditional branching based on refill events and engagement signals — a single triggered message cannot accommodate the dependency logic between educational steps and escalation paths.

### Technical considerations

- Apply strict data usage labels to all protected health information related to medication and diagnosis data to prevent unauthorized downstream activation.
- Integrate with pharmacy and electronic health records systems to receive prescription fill and refill data that trigger journey steps.
- Implement robust consent management to ensure patients have agreed to receive medication-related communications and can withdraw consent at any time.
- Design journey logic to detect non-engagement patterns and escalate to care team notifications when a patient may be at risk of non-adherence.


## Preventive Care Reminders

Proactively remind patients about recommended preventive care such as vaccinations, screenings, and annual check-ups based on their age, medical history, and risk factors. Timely preventive care reminders help close gaps in care and improve overall population health.

### Business impact

Proactive preventive care outreach results in improved preventive care completion rates, contributing to better population health and reduced long-term treatment costs.

### How to implement

Use the [Batch Outbound Message Activation](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) pattern. Preventive care reminders are best delivered through scheduled batch campaigns that evaluate patient eligibility against clinical guidelines on a regular cadence. This is the right pattern when the audience is pre-defined by clinical guideline criteria, delivery timing is scheduled on a regular cadence rather than event-driven, and no real-time branching or decisioning is required.

### Technical considerations

- Build audience segments using clinical guideline criteria (age, gender, family history, prior screening dates) while applying data usage labels to all protected health information used in segmentation.
- Coordinate with clinical teams to ensure reminder content aligns with current evidence-based preventive care guidelines and organizational protocols.
- Implement frequency capping to avoid overwhelming patients who qualify for multiple preventive care recommendations simultaneously.
- Maintain an audit trail of all preventive care communications sent for regulatory reporting and quality measure documentation.


## Post-Visit Follow-Up Campaigns

Automatically send post-visit surveys, care instructions, and follow-up appointment reminders based on the type of visit and each patient's specific needs. Timely follow-up improves patient satisfaction and ensures continuity of care after every encounter.

### Business impact

Automated post-visit follow-up campaigns achieve improved survey response rates and higher patient satisfaction scores.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. Visit completion events from the electronic health records system provide a natural, timely trigger for follow-up communications tailored to the encounter type. This is the right pattern when a discrete visit completion event is the trigger and the required response is immediate follow-up tailored to encounter type — rather than a multi-step sequence, since each visit generates its own independent follow-up need.

### Technical considerations

- Integrate with the electronic health records system to receive visit discharge events that include visit type, provider, and relevant care instructions without exposing full clinical notes.
- Apply data usage labels to any care instruction content to ensure protected health information is only shared through secure, patient-authorized channels.
- Configure timing rules that account for visit type — for example, post-surgical follow-ups may require different timing than routine check-up surveys.
- Include secure links to the patient portal for survey completion and appointment scheduling rather than collecting health information through unsecured channels.


## Chronic Disease Management Programs

Personalize chronic disease management communications, educational content, and monitoring reminders based on each patient's specific condition and treatment plan. Sustained, relevant engagement helps patients take an active role in managing their health over time.

### Business impact

Personalized chronic disease management programs see increased program engagement rates, leading to improved disease management outcomes and reduced emergency care utilization.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. Chronic disease management is inherently a long-running, multi-touchpoint experience that requires adaptive messaging based on patient engagement and health milestones. This is the right pattern because chronic disease management requires adaptive messaging over an extended period with conditional branching based on clinical metrics and engagement patterns — event-triggered messaging cannot handle the ongoing, dynamic re-evaluation needed to adjust interventions based on evolving health data.

### Technical considerations

- Design journey branching logic that adapts based on condition-specific metrics (for example, blood glucose trends for diabetes management or blood pressure readings for hypertension programs).
- Implement strict data governance with [!DNL Adobe Experience Platform] data usage labels to classify and protect condition-specific health data throughout the journey.
- Integrate with remote patient monitoring devices and patient-reported outcome systems to feed real-time health data into journey decision points.
- Build care team escalation paths within the journey so that non-engagement or concerning health trends trigger alerts to the appropriate clinical staff.


## New Patient Onboarding Journey

Automate a multi-step onboarding journey for new patients that includes welcome information, patient portal access instructions, and appointment scheduling guidance. A smooth onboarding experience sets the tone for an engaged, long-term patient relationship.

### Business impact

Automated new patient onboarding journeys help drive improvements in portal activation rates and stronger early patient engagement.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. Patient onboarding is a naturally sequential, multi-step process where each communication builds on the previous one and adapts based on whether the patient has completed key actions. This is the right pattern because onboarding requires a sequenced, dependent flow over multiple days with branching based on patient actions (portal activation, form completion) — a single message or batch approach cannot accommodate the interdependencies between steps or adapt to progressive completion.

### Technical considerations

- Integrate with the patient registration system to trigger the onboarding journey immediately upon new patient record creation, ensuring a timely first impression.
- Use identity resolution to merge any pre-existing records (for example, from a website visit or appointment request) with the new patient profile to avoid duplicate communications.
- Ensure portal activation links and credentials are delivered through secure, HIPAA-compliant channels and expire after a defined period.
- Design the journey to detect portal activation and form completion events so that subsequent steps adapt rather than repeating information the patient has already acted on.


## Personalized Health Content Delivery

Deliver personalized health education content, wellness tips, and resources tailored to each patient's conditions, interests, and health goals. Relevant content builds trust, improves health literacy, and empowers patients to make informed decisions about their care.

### Business impact

Personalized health content delivery achieves higher content engagement rates, leading to improved patient education and health literacy.

### How to implement

Use the [Cross-Channel Journey with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pattern. Health content delivery benefits from real-time decisioning that selects the most relevant content for each patient based on their conditions, preferences, and past engagement, delivered through their preferred channel. This is the right pattern when content selection must account for patient conditions, consent preferences, and channel preferences while preventing duplicate or fatiguing delivery — multi-step orchestration alone does not provide the real-time decisioning layer needed to match dynamic content inventory to individual patient needs.

### Technical considerations

- Apply content classification and data usage labels to all health education materials to ensure condition-specific content is only delivered to patients who have consented to receive health information on that topic.
- Integrate the decisioning engine with a content repository that is regularly reviewed and approved by clinical teams to ensure medical accuracy.
- Implement content fatigue rules to avoid over-delivering content on a single topic and to balance educational material across a patient's various health needs.
- Track content engagement signals (opens, clicks, time spent) to continuously refine content relevance without collecting or storing additional protected health information.


## Lab Results Notification

Notify patients when lab results are available through their preferred communication channel with personalized, secure messaging. Prompt notification encourages patients to review results quickly and follow up with their care team when needed.

### Business impact

Automated lab results notifications help drive higher result viewing rates, improving patient communication and enabling faster clinical follow-up when results require action.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. Lab result availability is a discrete event that calls for an immediate, single notification through the patient's preferred channel. This is the right pattern when a discrete lab result event is the trigger and the required response is a single, immediate notification — rather than a multi-message sequence, since patients need a prompt alert to check their portal without additional follow-up communications.

### Technical considerations

- Never include actual lab result values in notification messages — only notify the patient that results are available and direct them to the secure patient portal for details.
- Integrate with the laboratory information system to receive result-ready events while applying strict data usage labels to prevent any clinical data from flowing into marketing channels.
- Implement provider-hold logic so that notifications are only sent after the ordering physician has reviewed and released the results for patient viewing.
- Ensure all notification links point to authenticated, encrypted patient portal sessions that meet HIPAA security requirements.


## Insurance Coverage Verification

Proactively verify and communicate insurance coverage information to patients before their appointments to reduce billing surprises and improve the overall patient experience. Clear, upfront coverage communication builds trust and reduces post-visit billing disputes.

### Business impact

Proactive insurance coverage verification results in improved pre-visit coverage confirmation rates and a meaningful reduction in billing disputes and patient complaints.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. Appointment scheduling events serve as the trigger to initiate coverage verification and communicate results to the patient before the visit. This is the right pattern when a discrete appointment scheduling event is the trigger and the required response is a single, time-sensitive notification about coverage — rather than a multi-step engagement sequence, since the patient needs one clear message before their appointment.

### Technical considerations

- Integrate with insurance eligibility verification systems to retrieve real-time coverage status without storing full insurance claim data in the customer data platform.
- Apply data usage labels to all financial and insurance information to restrict its use to billing-related communications only.
- Configure message timing to allow sufficient lead time before the appointment for patients to resolve any coverage issues or contact their insurance provider.
- Include clear instructions and contact information for the billing department so patients can ask questions or provide updated insurance details before their visit.


## Telehealth Appointment Reminders

Send personalized reminders for telehealth appointments that include connection instructions, preparation tips, and technical support information. Effective telehealth reminders reduce missed virtual visits and help patients feel confident using digital care tools.

### Business impact

Personalized telehealth appointment reminders help drive improvements in virtual visit show rates and accelerate overall telehealth adoption across the patient population.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. Telehealth appointment scheduling events provide a natural trigger for timely reminders that include connection details and preparation guidance. This is the right pattern when a discrete telehealth appointment event is the trigger and the required response is a single, immediate reminder with technical guidance — rather than a multi-step sequence, since patients need clear pre-appointment instructions without subsequent follow-up messaging.

### Technical considerations

- Include platform-specific connection instructions (desktop versus mobile) based on the patient's known device preferences or past telehealth session data.
- Ensure all telehealth connection links and session identifiers are delivered through encrypted, HIPAA-compliant channels and expire after the scheduled appointment window.
- Integrate with the telehealth platform to detect when a patient has successfully connected so that secondary reminder messages can be suppressed.
- Provide a fallback path to technical support contact information for patients who have not connected within a defined window before the appointment start time.


## Wellness Program Engagement

Personalize wellness program communications, challenges, and rewards based on each patient's health goals, activity level, and preferences. Engaging wellness programs motivate patients to adopt healthier habits and maintain long-term well-being.

### Business impact

Personalized wellness program engagement campaigns achieve increased program participation rates, contributing to improved health outcomes and stronger patient loyalty.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. Wellness programs are sustained engagement experiences with multiple milestones, challenges, and reward touchpoints that require adaptive orchestration based on patient participation and progress. This is the right pattern because wellness programs require a sequenced, multi-message flow over an extended period with conditional branching based on participation milestones and engagement patterns — event-triggered messaging cannot handle the sustained, adaptive orchestration needed to adjust challenges and rewards based on ongoing progress tracking.

### Technical considerations

- Integrate with wearable device and fitness application data feeds while applying clear data usage labels to distinguish wellness data from clinical health data subject to stricter regulatory requirements.
- Implement consent management that allows patients to grant and revoke permission for wellness data collection independently from their clinical communication preferences.
- Design journey logic that adjusts challenge difficulty and communication frequency based on each patient's engagement patterns to avoid discouragement or fatigue.
- Ensure reward and incentive tracking complies with applicable healthcare regulations around patient inducements and anti-kickback requirements.


## Care Team Coordination

Enable personalized communication and coordination between patients and their care team members based on the care plan and individual preferences. Better coordination leads to more seamless care transitions and improved outcomes for patients with complex care needs.

### Business impact

Effective care team coordination communications result in improved care team engagement and better care coordination outcomes across multi-provider care plans.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. Care team coordination involves multiple stakeholders and ongoing communication flows that must adapt based on care plan milestones, patient status changes, and provider actions. This is the right pattern because care coordination requires adaptive, multi-step messaging flows that branch based on care plan milestones and provider actions across multiple stakeholders — a single message or simpler pattern cannot accommodate the complex interdependencies and role-based message routing needed across clinical teams.

### Technical considerations

- Implement role-based access controls and data usage labels to ensure that each care team member only receives patient information relevant to their role in the care plan.
- Integrate with care management and electronic health records systems to receive care plan updates, referral completions, and transition-of-care events that trigger coordination messages.
- Design separate communication paths for patient-facing and provider-facing messages, ensuring that clinical terminology is used appropriately for providers while patient messages remain clear and accessible.
- Maintain a complete audit trail of all care coordination communications for compliance with care continuity regulations and accreditation requirements.


## Patient Journey Funnel and Care Gap Analysis

Map the end-to-end patient journey from initial web research through appointment scheduling, care delivery, and follow-up to identify where patients disengage and which populations have gaps in recommended preventive or chronic care. Health systems that lack cross-channel journey visibility cannot distinguish between scheduling friction and patient disengagement — limiting their ability to improve access and close care gaps at scale.

### Business impact

Understanding where patients drop out of care pathways and which member segments have the highest concentration of care gaps enables care management and marketing teams to focus outreach resources on the populations and friction points that will yield the greatest improvement in care adherence.

### How to implement

Use the [Customer Analytics & Insight Generation](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) pattern. This approach connects web and portal behavioral data, appointment system records, and care claims data to Customer Journey Analytics, where fallout analysis measures drop-off at each scheduling or care step and cohort analysis identifies which member segments have the lowest care adherence rates. This is the right pattern when the goal is insight generation and population-level analysis — understanding where journeys break down and who is most at risk — rather than triggering outreach or activating a suppression list.

### Technical considerations

- Appointment and claims data from clinical systems must be mapped to HIPAA-compliant XDM schemas before ingestion into AEP, and data use labels must be applied to restrict access to protected health information within CJA data views.
- Patient or member identifiers across the web portal, scheduling system, and EHR must be resolved to a consistent person ID in the CJA connection to produce a coherent cross-system journey view without duplicating individuals.
- Care gap analysis requires look-up datasets that encode clinical guideline definitions — such as recommended screening intervals by age and condition — so that CJA derived fields can flag members who have not completed recommended care within the guideline window.
- Scheduling funnel analysis should capture both completed and abandoned scheduling sessions, including exit points in multi-step scheduling flows, so that friction points are visible at the step level rather than as aggregate drop-off rates.


## Patient Portal Content Personalization

Personalize the authenticated patient portal experience by surfacing the most relevant health content, tools, and resources based on each patient's in-session browsing behavior and engagement history. A portal that adapts to what a patient is actively researching — rather than presenting the same static experience to every visitor — makes it easier for patients to find what they need and encourages deeper engagement with available health resources.

### Business impact

Personalizing the patient portal experience based on engagement behavior drives improved content discovery and self-service completion rates, helping patients navigate their care more confidently without requiring care team intervention.

### How to implement

Use the [Behavioral Recommendation](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) pattern. In-session behavioral signals from the authenticated portal — including content page views, health tool usage, FAQ topic engagement, and appointment scheduling activity — train a recommendation model that surfaces the most relevant resources for each patient based on what they are actively exploring, without requiring clinical data as an input. This is the right pattern when personalization is driven by implicit behavioral signals within an authenticated session and the goal is relevance ranking of a content and resource catalog — rather than governed eligibility decisioning, which is more appropriate when clinical criteria must gate what a patient sees.

### Technical considerations

- Limit behavioral signals used for recommendations to portal interaction data — content views, tool usage, and navigation patterns — and implement data use labels that prevent any inferred health interests from flowing outside the authenticated portal session or into marketing channels.
- Implement a clinically reviewed content library as the recommendation pool so that the model can only surface pre-approved health education materials, ensuring every recommended resource has been validated for accuracy before deployment.
- Ensure the recommendation system meets HIPAA technical safeguard requirements for the authenticated portal environment, including session timeout controls and audit logging of which content was presented to each patient and when.
- Provide patients with visible controls to clear their portal browsing history and opt out of behavioral personalization, maintaining transparency and trust in how their engagement data is used within the portal experience.

## Patient Engagement & Appointment Reminders

Send personalized appointment reminders, health tips, and follow-up care communications through compliant, consent-aware multi-channel journeys. Automated, personalized appointment reminders reduce no-show rates while ensuring communications comply with healthcare privacy regulations and patient consent preferences.

### Business impact

Healthcare organizations with automated appointment reminder programs see meaningful reductions in no-show and late-cancellation rates, improving provider schedule utilization and patient health outcomes through better appointment adherence.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern to respond to appointment scheduling events with timely, personalized reminders timed at optimal intervals before the appointment date. This is the right pattern when the communication is triggered by a specific patient interaction event and the response is a time-sensitive, individualized message — rather than a multi-week nurture sequence or complex offer selection.

### Technical considerations

- All patient communications must comply with applicable healthcare privacy regulations; messaging content must avoid including protected health information beyond what is strictly necessary for the communication.
- Consent management must be enforced at the channel level — patients who have not opted into SMS reminders must not receive texts, even when SMS would be the most effective reminder channel for their demographic.
- Integration with the scheduling system must deliver appointment events in near real time to enable reminder timing that is accurate to the actual appointment schedule, including same-day reschedules and cancellations.
- Multi-channel reminder sequences must include suppression logic so that patients who confirm their appointment do not continue to receive reminder messages for that appointment.
