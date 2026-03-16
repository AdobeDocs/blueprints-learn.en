---
title: Healthcare Use Cases
description: "Discover how healthcare organizations use Adobe Experience Platform to improve patient engagement, streamline care coordination, and drive better health outcomes."
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
---

# Healthcare Use Cases

Healthcare organizations use Adobe Experience Platform to build unified patient profiles and deliver personalized, timely communications across every touchpoint. By connecting clinical, behavioral, and preference data in one place, care teams can engage patients more effectively while maintaining the highest standards of privacy and compliance.

## Appointment Reminder Automation

Send personalized appointment reminders through email, text message, and push notifications based on each patient's communication preferences and appointment type. Automated reminders reduce missed appointments and keep schedules running smoothly, freeing staff to focus on patient care.

### Business impact

Organizations that implement automated appointment reminders typically see a 30 to 40 percent improvement in appointment show rates and a significant reduction in costly no-shows.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. Appointment creation and update events from the scheduling system serve as natural triggers for timely, relevant reminder messages.

### Technical considerations

- Ensure all patient contact information and appointment details are transmitted and stored in compliance with HIPAA requirements, using appropriate data usage labels to restrict unauthorized access.
- Integrate with the electronic health records scheduling system to capture appointment creation, cancellation, and rescheduling events in real time.
- Apply consent management policies so that reminders are only sent through channels the patient has explicitly opted into.
- Configure suppression rules to prevent duplicate or excessive reminders when appointments are rescheduled in quick succession.


## Medication Adherence Campaigns

Send personalized reminders and educational content to help patients stay on track with their medication schedules and treatment plans. Tailored messaging based on medication type, dosing schedule, and patient history drives better adherence and improved health outcomes.

### Business impact

Personalized medication adherence campaigns typically drive a 20 to 30 percent improvement in adherence rates, leading to measurably better health outcomes and fewer hospital readmissions.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. Medication adherence requires a sustained, multi-touch approach with escalating reminders, educational touchpoints, and follow-up check-ins over the course of a treatment plan.

### Technical considerations

- Apply strict data usage labels to all protected health information related to medication and diagnosis data to prevent unauthorized downstream activation.
- Integrate with pharmacy and electronic health records systems to receive prescription fill and refill data that trigger journey steps.
- Implement robust consent management to ensure patients have agreed to receive medication-related communications and can withdraw consent at any time.
- Design journey logic to detect non-engagement patterns and escalate to care team notifications when a patient may be at risk of non-adherence.


## Preventive Care Reminders

Proactively remind patients about recommended preventive care such as vaccinations, screenings, and annual check-ups based on their age, medical history, and risk factors. Timely preventive care reminders help close gaps in care and improve overall population health.

### Business impact

Proactive preventive care outreach typically results in a 25 to 35 percent increase in preventive care completion rates, contributing to improved population health and reduced long-term treatment costs.

### How to implement

Use the [Batch Outbound Message Activation](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) pattern. Preventive care reminders are best delivered through scheduled batch campaigns that evaluate patient eligibility against clinical guidelines on a regular cadence.

### Technical considerations

- Build audience segments using clinical guideline criteria (age, gender, family history, prior screening dates) while applying data usage labels to all protected health information used in segmentation.
- Coordinate with clinical teams to ensure reminder content aligns with current evidence-based preventive care guidelines and organizational protocols.
- Implement frequency capping to avoid overwhelming patients who qualify for multiple preventive care recommendations simultaneously.
- Maintain an audit trail of all preventive care communications sent for regulatory reporting and quality measure documentation.


## Post-Visit Follow-Up Campaigns

Automatically send post-visit surveys, care instructions, and follow-up appointment reminders based on the type of visit and each patient's specific needs. Timely follow-up improves patient satisfaction and ensures continuity of care after every encounter.

### Business impact

Automated post-visit follow-up campaigns typically achieve a 40 to 50 percent improvement in survey response rates and measurably higher patient satisfaction scores.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. Visit completion events from the electronic health records system provide a natural, timely trigger for follow-up communications tailored to the encounter type.

### Technical considerations

- Integrate with the electronic health records system to receive visit discharge events that include visit type, provider, and relevant care instructions without exposing full clinical notes.
- Apply data usage labels to any care instruction content to ensure protected health information is only shared through secure, patient-authorized channels.
- Configure timing rules that account for visit type — for example, post-surgical follow-ups may require different timing than routine check-up surveys.
- Include secure links to the patient portal for survey completion and appointment scheduling rather than collecting health information through unsecured channels.


## Chronic Disease Management Programs

Personalize chronic disease management communications, educational content, and monitoring reminders based on each patient's specific condition and treatment plan. Sustained, relevant engagement helps patients take an active role in managing their health over time.

### Business impact

Personalized chronic disease management programs typically see a 30 to 40 percent increase in program engagement rates, leading to improved disease management outcomes and reduced emergency care utilization.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. Chronic disease management is inherently a long-running, multi-touchpoint experience that requires adaptive messaging based on patient engagement and health milestones.

### Technical considerations

- Design journey branching logic that adapts based on condition-specific metrics (for example, blood glucose trends for diabetes management or blood pressure readings for hypertension programs).
- Implement strict data governance with [!DNL Adobe Experience Platform] data usage labels to classify and protect condition-specific health data throughout the journey.
- Integrate with remote patient monitoring devices and patient-reported outcome systems to feed real-time health data into journey decision points.
- Build care team escalation paths within the journey so that non-engagement or concerning health trends trigger alerts to the appropriate clinical staff.


## New Patient Onboarding Journey

Automate a multi-step onboarding journey for new patients that includes welcome information, patient portal access instructions, and appointment scheduling guidance. A smooth onboarding experience sets the tone for an engaged, long-term patient relationship.

### Business impact

Automated new patient onboarding journeys typically drive a 50 to 60 percent improvement in portal activation rates and significantly higher early patient engagement.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. Patient onboarding is a naturally sequential, multi-step process where each communication builds on the previous one and adapts based on whether the patient has completed key actions.

### Technical considerations

- Integrate with the patient registration system to trigger the onboarding journey immediately upon new patient record creation, ensuring a timely first impression.
- Use identity resolution to merge any pre-existing records (for example, from a website visit or appointment request) with the new patient profile to avoid duplicate communications.
- Ensure portal activation links and credentials are delivered through secure, HIPAA-compliant channels and expire after a defined period.
- Design the journey to detect portal activation and form completion events so that subsequent steps adapt rather than repeating information the patient has already acted on.


## Personalized Health Content Delivery

Deliver personalized health education content, wellness tips, and resources tailored to each patient's conditions, interests, and health goals. Relevant content builds trust, improves health literacy, and empowers patients to make informed decisions about their care.

### Business impact

Personalized health content delivery typically achieves a 35 to 45 percent increase in content engagement rates, leading to measurably improved patient education and health literacy.

### How to implement

Use the [Cross-Channel Journey with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pattern. Health content delivery benefits from real-time decisioning that selects the most relevant content for each patient based on their conditions, preferences, and past engagement, delivered through their preferred channel.

### Technical considerations

- Apply content classification and data usage labels to all health education materials to ensure condition-specific content is only delivered to patients who have consented to receive health information on that topic.
- Integrate the decisioning engine with a content repository that is regularly reviewed and approved by clinical teams to ensure medical accuracy.
- Implement content fatigue rules to avoid over-delivering content on a single topic and to balance educational material across a patient's various health needs.
- Track content engagement signals (opens, clicks, time spent) to continuously refine content relevance without collecting or storing additional protected health information.


## Lab Results Notification

Notify patients when lab results are available through their preferred communication channel with personalized, secure messaging. Prompt notification encourages patients to review results quickly and follow up with their care team when needed.

### Business impact

Automated lab results notifications typically drive a 60 to 70 percent increase in result viewing rates, improving patient communication and enabling faster clinical follow-up when results require action.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. Lab result availability is a discrete event that calls for an immediate, single notification through the patient's preferred channel.

### Technical considerations

- Never include actual lab result values in notification messages — only notify the patient that results are available and direct them to the secure patient portal for details.
- Integrate with the laboratory information system to receive result-ready events while applying strict data usage labels to prevent any clinical data from flowing into marketing channels.
- Implement provider-hold logic so that notifications are only sent after the ordering physician has reviewed and released the results for patient viewing.
- Ensure all notification links point to authenticated, encrypted patient portal sessions that meet HIPAA security requirements.


## Insurance Coverage Verification

Proactively verify and communicate insurance coverage information to patients before their appointments to reduce billing surprises and improve the overall patient experience. Clear, upfront coverage communication builds trust and reduces post-visit billing disputes.

### Business impact

Proactive insurance coverage verification typically results in a 25 to 35 percent improvement in pre-visit coverage confirmation rates and a meaningful reduction in billing disputes and patient complaints.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. Appointment scheduling events serve as the trigger to initiate coverage verification and communicate results to the patient before the visit.

### Technical considerations

- Integrate with insurance eligibility verification systems to retrieve real-time coverage status without storing full insurance claim data in the customer data platform.
- Apply data usage labels to all financial and insurance information to restrict its use to billing-related communications only.
- Configure message timing to allow sufficient lead time before the appointment for patients to resolve any coverage issues or contact their insurance provider.
- Include clear instructions and contact information for the billing department so patients can ask questions or provide updated insurance details before their visit.


## Telehealth Appointment Reminders

Send personalized reminders for telehealth appointments that include connection instructions, preparation tips, and technical support information. Effective telehealth reminders reduce missed virtual visits and help patients feel confident using digital care tools.

### Business impact

Personalized telehealth appointment reminders typically drive a 40 to 50 percent improvement in virtual visit show rates and accelerate overall telehealth adoption across the patient population.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. Telehealth appointment scheduling events provide a natural trigger for timely reminders that include connection details and preparation guidance.

### Technical considerations

- Include platform-specific connection instructions (desktop versus mobile) based on the patient's known device preferences or past telehealth session data.
- Ensure all telehealth connection links and session identifiers are delivered through encrypted, HIPAA-compliant channels and expire after the scheduled appointment window.
- Integrate with the telehealth platform to detect when a patient has successfully connected so that secondary reminder messages can be suppressed.
- Provide a fallback path to technical support contact information for patients who have not connected within a defined window before the appointment start time.


## Wellness Program Engagement

Personalize wellness program communications, challenges, and rewards based on each patient's health goals, activity level, and preferences. Engaging wellness programs motivate patients to adopt healthier habits and maintain long-term well-being.

### Business impact

Personalized wellness program engagement campaigns typically achieve a 30 to 40 percent increase in program participation rates, contributing to improved health outcomes and stronger patient loyalty.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. Wellness programs are sustained engagement experiences with multiple milestones, challenges, and reward touchpoints that require adaptive orchestration based on patient participation and progress.

### Technical considerations

- Integrate with wearable device and fitness application data feeds while applying clear data usage labels to distinguish wellness data from clinical health data subject to stricter regulatory requirements.
- Implement consent management that allows patients to grant and revoke permission for wellness data collection independently from their clinical communication preferences.
- Design journey logic that adjusts challenge difficulty and communication frequency based on each patient's engagement patterns to avoid discouragement or fatigue.
- Ensure reward and incentive tracking complies with applicable healthcare regulations around patient inducements and anti-kickback requirements.


## Care Team Coordination

Enable personalized communication and coordination between patients and their care team members based on the care plan and individual preferences. Better coordination leads to more seamless care transitions and improved outcomes for patients with complex care needs.

### Business impact

Effective care team coordination communications typically result in a 35 to 45 percent improvement in care team engagement and measurably better care coordination outcomes across multi-provider care plans.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. Care team coordination involves multiple stakeholders and ongoing communication flows that must adapt based on care plan milestones, patient status changes, and provider actions.

### Technical considerations

- Implement role-based access controls and data usage labels to ensure that each care team member only receives patient information relevant to their role in the care plan.
- Integrate with care management and electronic health records systems to receive care plan updates, referral completions, and transition-of-care events that trigger coordination messages.
- Design separate communication paths for patient-facing and provider-facing messages, ensuring that clinical terminology is used appropriately for providers while patient messages remain clear and accessible.
- Maintain a complete audit trail of all care coordination communications for compliance with care continuity regulations and accreditation requirements.
