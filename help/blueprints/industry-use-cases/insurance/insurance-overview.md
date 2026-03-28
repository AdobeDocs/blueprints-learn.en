---
title: Insurance Use Cases
description: Discover how insurance organizations use Adobe Experience Platform to personalize policy management, improve claims experiences, and drive customer retention.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: a082598f-555b-49a4-b201-a55bee793959
---
# Insurance Use Cases

Insurance organizations use Adobe Experience Platform to unify policyholder data across policy management, claims, and engagement systems to deliver personalized communications at every stage of the customer relationship. By connecting behavioral signals with policy and claims information, insurers can proactively engage customers with relevant offers, timely service updates, and meaningful support that drives retention and lifetime value.

## Policy Renewal Campaigns

Send personalized policy renewal reminders and offers based on each customer's policy history, claims record, and coverage preferences. Timely, relevant renewal outreach reduces policy lapse rates and strengthens long-term customer relationships by making it easy for policyholders to understand their options and take action.

### Business impact

Organizations that implement personalized policy renewal campaigns see improved renewal rates, directly reducing customer churn and protecting recurring premium revenue.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. This approach builds a timed renewal sequence that progresses from initial notice through escalating reminders and, if needed, a final urgency message, adapting the cadence and offer based on whether the policyholder has engaged with earlier touches. This is the right pattern when the timing is driven by a contract date rather than a discrete customer event, and the business intent requires a sequenced, multi-message flow over 30 or more days with conditional branching based on engagement — event-triggered messaging handles reactive responses to discrete events but cannot accommodate the calendar-based scheduling logic or escalation dependencies required for a renewal campaign.

### Technical considerations

- Integrate with the policy management system to receive renewal date events and current policy details, ensuring messages reflect accurate coverage and premium information.
- Apply data governance labels to all personally identifiable and financial policy data to comply with state insurance regulations and data privacy requirements.
- Configure suppression rules to prevent renewal messages from being sent to policyholders who have already renewed or who have active claims that may affect their renewal terms.
- Coordinate timing with agent or broker assignments so that direct-to-customer messages align with any outreach the assigned agent may also be conducting.


## Cross-Sell Product Recommendations

Recommend additional insurance products such as life, home, or auto coverage based on each customer's existing policies, life stage, and risk profile. Personalized product recommendations help policyholders discover coverage gaps and build a more complete protection portfolio.

### Business impact

Personalized cross-sell recommendations drive improved cross-sell conversion rates, increasing policies per household and overall customer lifetime value.

### How to implement

Use the [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) pattern. Real-time decisioning evaluates each customer's existing coverage, life stage, and behavioral signals to select the most relevant product recommendation from the available catalog. This is the right pattern when product selection must account for eligibility rules, underwriting guidelines, and regulatory suitability requirements — constraints that require governed decisioning logic rather than behavioral affinity ranking alone.

### Technical considerations

- Integrate policy data from all product lines into a unified customer profile so the decisioning engine has a complete view of existing coverage when selecting recommendations.
- Configure eligibility rules within the decisioning model to exclude products that a customer already holds or that conflict with underwriting guidelines for their risk profile.
- Engage your legal and compliance teams to validate that product recommendation eligibility rules align with applicable state insurance marketing and suitability requirements before go-live.
- Coordinate decisioning output with the agent portal so that recommended products are visible to assigned agents who may be having direct conversations with the customer.


## Claims Process Personalization

Personalize claims process communications, status updates, and support resources based on the type of claim, customer preferences, and claims history. A transparent, well-communicated claims experience reduces anxiety during stressful moments and builds lasting trust with policyholders.

### Business impact

Personalized claims communications achieve improved claims satisfaction scores, reducing complaints and strengthening the likelihood of policy renewal after a claim.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. The claims process is a multi-stage experience with distinct phases — filing, investigation, adjustment, and settlement — that each require tailored communications and adaptive timing. This is the right pattern when the use case requires a sequenced, multi-message flow over days with conditional branching based on claims status events — a single triggered message cannot accommodate the dependency logic between sequential claims phases.

### Technical considerations

- Integrate with the claims management system to receive real-time status change events that advance the customer through the appropriate journey stage.
- Design journey branching logic that adapts messaging tone and content based on claim type, such as auto collision versus property damage versus liability claims.
- Implement suppression rules during active claims investigations to prevent marketing or cross-sell messages from reaching customers at sensitive moments.
- Ensure all claims-related data flowing into the customer profile is labeled with appropriate data governance restrictions to prevent its use outside of service communications.


## Risk Assessment and Prevention

Provide personalized risk assessment information and prevention tips based on each customer's policy type, geographic location, and specific risk factors. Proactive risk education helps policyholders reduce their exposure to loss, benefiting both the customer and the insurer.

### Business impact

Personalized risk prevention outreach drives improved prevention engagement, contributing to reduced claim frequency and improved customer satisfaction.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. Risk prevention education is most effective as a sustained, multi-touch journey that delivers relevant guidance over time and adapts based on customer engagement and seasonal risk factors. This is the right pattern when the journey must deliver content over extended periods with seasonal timing adjustments and engagement-based branching — event-triggered messaging cannot handle predictive scheduling or the multi-step cadence needed for sustained education.

### Technical considerations

- Integrate with third-party risk data providers for weather, geographic hazard, and property risk information that enrich customer profiles with location-specific risk scores.
- Design seasonal journey logic that delivers relevant prevention content ahead of high-risk periods, such as hurricane season preparation for coastal policyholders or winter weather tips for cold-climate customers.
- Apply data governance labels to distinguish risk assessment data used for customer education from data used in actuarial underwriting decisions.
- Coordinate risk prevention content with the policyholder's specific coverage so that recommendations are relevant to the perils their policy actually covers.


## Policy Change Notifications

Send personalized notifications about policy changes, coverage updates, and new options based on each customer's specific policy and communication preferences. Clear, timely notifications keep policyholders informed and reduce confusion about their coverage status.

### Business impact

Personalized policy change notifications achieve improved notification acknowledgment rates, reducing customer service inquiries and improving overall policyholder understanding.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. Policy change events from the administration system serve as natural triggers for immediate, relevant notifications through each customer's preferred channel. This is the right pattern when the trigger is a system event (policy change) rather than customer behavior, and the required communication is immediate and reactive rather than a sustained nurture sequence.

### Technical considerations

- Integrate with the policy administration system to capture endorsement, amendment, and renewal change events in real time, ensuring notifications reflect the most current policy state.
- Work with your legal team to confirm that policy change notifications meet applicable state-mandated timing, language, and delivery channel requirements before activating automated communications.
- Configure channel priority logic based on the urgency and type of change — for example, coverage reductions may warrant more immediate channels than informational updates.
- Maintain a delivery audit trail for all policy change notifications to support regulatory compliance documentation and dispute resolution.


## Quote Abandonment Recovery

Re-engage customers who started but did not complete an insurance quote with personalized follow-up messages and tailored offers. Timely recovery outreach brings prospective customers back to the quoting process and addresses common barriers to completion.

### Business impact

Quote abandonment recovery campaigns drive improved quote completion rates, converting more prospects into policyholders and reducing customer acquisition costs.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. Quote abandonment is a behavioral event that triggers timely follow-up while the prospect's interest and intent are still fresh. This is the right pattern when a discrete customer behavior (abandonment) is the trigger and the required response is time-sensitive re-engagement — rather than a multi-step nurture sequence or complex offer decisioning.

### Technical considerations

- Integrate with the online quoting platform to capture abandonment events along with the quote details the customer had already provided, enabling personalized re-engagement.
- Configure timing rules that balance urgency with respectfulness — initial follow-up within hours, with a limited number of subsequent reminders over the following days.
- Apply consent and privacy rules to ensure follow-up is only sent to prospects who have opted in to marketing communications, particularly for customers who have not yet established a policy relationship.
- Include deep links that return the prospect directly to their saved quote rather than requiring them to restart the process from the beginning.


## Discount and Savings Opportunities

Identify and communicate personalized discount opportunities — such as bundling, safe driver, loyalty, and paperless billing discounts — based on each customer's profile and behavior. Proactive savings communications demonstrate value and strengthen the price-value relationship.

### Business impact

Personalized discount and savings communications drive improved discount utilization rates, improving customer satisfaction and reducing price-driven churn.

### How to implement

Use the [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) pattern. Real-time decisioning evaluates each customer's eligibility for available discounts and selects the most impactful savings opportunity to present at the right moment. This is the right pattern when discount selection must account for stacking limitations, regulatory restrictions, and accurate actuarial calculations — constraints that require governed decisioning logic rather than simple eligibility checks alone.

### Technical considerations

- Integrate with the policy rating and billing systems to calculate accurate discount eligibility and potential savings amounts for each customer in real time.
- Configure decisioning rules that account for discount stacking limitations and ensure communicated savings amounts are actuarially accurate and approved by the pricing team.
- Apply state-specific regulatory rules to discount communications, as certain states have restrictions on how insurance discounts can be marketed and applied.
- Track discount adoption outcomes to continuously refine the decisioning model and prioritize the savings messages that resonate most with different customer segments.


## Claims Fraud Prevention

Use intelligent fraud detection to identify suspicious claims patterns and personalize investigation communications while maintaining customer trust. Effective fraud prevention protects honest policyholders by keeping premiums fair and ensuring legitimate claims are processed quickly.

### Business impact

Intelligent claims fraud prevention programs achieve improved fraud detection rates, reducing fraudulent payouts and lowering overall claims costs.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. Fraud risk scoring events trigger appropriate investigation communications and process adjustments in real time, ensuring that flagged claims receive immediate attention. This is the right pattern when a system-derived event (fraud risk score) is the trigger and the required action is immediate internal process adjustment with careful customer communication — rather than a multi-step journey or decisioning scenario.

### Technical considerations

- Integrate fraud risk scores from the claims analytics system into the customer profile while applying strict data governance labels to prevent fraud investigation data from appearing in customer-facing communications.
- Design communication paths that maintain a professional, respectful tone for customers whose claims are under review, preserving the relationship regardless of investigation outcome.
- Implement role-based access controls to ensure fraud indicators are only visible to authorized investigation teams and are never surfaced in standard agent or customer service views.
- Coordinate with the [!DNL Adobe Experience Platform] identity resolution service to detect patterns across related profiles, such as shared addresses or phone numbers linked to multiple suspicious claims.


## Wellness and Prevention Programs

Personalize wellness program communications, participation reminders, and reward notifications for health and life insurance customers based on their goals and engagement level. Active wellness programs improve policyholder health outcomes and build a stronger, more engaged customer base.

### Business impact

Personalized wellness and prevention program communications drive improved program participation rates, contributing to better health outcomes and reduced claims frequency.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. Wellness programs are sustained engagement experiences with milestones, challenges, and rewards that require adaptive orchestration based on each participant's activity and progress. This is the right pattern when the use case requires a long-term, multi-message flow with engagement-based branching and adaptive timing adjustments — event-triggered messaging cannot handle the complex milestone logic or the need to adjust communication cadence based on sustained activity tracking.

### Technical considerations

- Integrate with wearable device and health application data feeds using [!DNL Adobe Experience Platform] streaming ingestion, applying clear data governance labels to distinguish wellness data from underwriting or claims data.
- Implement separate consent mechanisms for wellness data collection to ensure participants understand how their health activity data is used and can opt out without affecting their policy.
- Design journey logic that adjusts program intensity and communication frequency based on each participant's engagement level to prevent fatigue and encourage sustained participation.
- Engage your legal and compliance teams to review wellness incentive structures and premium discount programs for compliance with applicable state insurance regulations before launch.


## Agent and Broker Coordination

Enable personalized communication and coordination between customers and their assigned agents or brokers based on policy needs, service history, and preferences. Better coordination creates a seamless experience where customers feel supported by a knowledgeable advisor who understands their full relationship.

### Business impact

Effective agent and broker coordination communications result in improved agent engagement, leading to stronger customer relationships and higher retention driven by trusted advisory interactions.

### How to implement

Use the [Batch Outbound Message Activation](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) pattern. Agent coordination is best delivered through scheduled batch activations that provide agents with prioritized customer outreach lists, talking points, and recommended actions on a regular cadence. This is the right pattern when the audience is large and pre-defined, delivery timing is scheduled on a recurring basis rather than event-driven, and no real-time branching or decisioning is required.

### Technical considerations

- Integrate with the agent management system to maintain accurate agent-customer assignments and ensure communications reflect the correct relationship, especially during agent transitions.
- Design data activation to the agent portal so that agents receive a consolidated view of customer insights, upcoming renewals, and recommended actions without exposing raw behavioral data.
- Apply data governance labels to restrict which customer data elements are shared with external broker partners versus captive agents, respecting contractual and regulatory data sharing boundaries.
- Implement feedback loops from agent interactions back into the customer profile so that insights from in-person or phone conversations enrich the unified view and improve future personalization.


## Catastrophic Event Response

Proactively communicate with customers in affected areas during natural disasters or catastrophic events with personalized support information, claims filing guidance, and emergency resources. Rapid, empathetic outreach during a crisis demonstrates the insurer's commitment to being there when customers need it most.

### Business impact

Proactive catastrophic event response communications achieve improved customer communication rates during events, accelerating claims filing and strengthening long-term customer trust and loyalty.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. Catastrophic event declarations serve as high-priority triggers for immediate, personalized outreach to all policyholders in the affected geographic area. This is the right pattern when a high-priority external event is the trigger and the required response is immediate, broad geographic outreach with time-critical information — rather than individual customer behavior patterns or complex sequencing.

### Technical considerations

- Integrate with catastrophe monitoring services and government disaster declaration feeds to trigger communications rapidly when events are declared for specific geographic areas.
- Build geographic audience segments using policyholder address data and property location information to accurately identify customers in the affected area without over-communicating to unaffected customers.
- Configure high-priority message routing that overrides standard frequency capping and suppression rules to ensure critical safety and claims information reaches customers immediately.
- Pre-build message templates and journey configurations for common catastrophic event types so that communications can be activated within hours of an event declaration rather than requiring content creation during the crisis.


## Policyholder Portal Content Personalization

Personalize the authenticated self-service portal and mobile app experience for policyholders by surfacing the most relevant coverage information, tools, and resources based on their browsing behavior, policy portfolio, and recent service interactions. A portal that adapts to each policyholder's current context reduces friction and makes it easier for customers to find what they need when they need it.

### Business impact

Personalizing the policyholder portal experience drives measurable improvements in self-service task completion and digital engagement, reducing inbound contact center volume and strengthening customer satisfaction with the digital channel.

### How to implement

Use the [Behavioral Recommendation](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) pattern. Behavioral signals from authenticated portal sessions — coverage calculator usage, policy document views, claims status checks, and FAQ topic engagement — train a recommendation model that dynamically surfaces the most relevant content and tools for each policyholder's current context. This is the right pattern when personalization is driven by implicit behavioral signals within an authenticated session and the goal is relevance ranking of a content or resource catalog — rather than Offer Decisioning, which requires governed eligibility and actuarial approval before presenting a product offer, or Cross-Channel with Decisioning, which is more appropriate when coordinating a product offer across multiple channels.

### Technical considerations

- Apply data governance labels to behavioral signals collected in the policyholder portal to distinguish engagement analytics from regulated insurance data, and restrict any signals derived from claims history from flowing into personalization models without explicit actuarial and compliance review.
- Integrate the behavioral model with the policy management system to ensure that content and tool recommendations reflect each policyholder's active policy portfolio — surfacing auto coverage tools for auto policyholders and property resources for homeowners — without exposing raw policy data to the recommendation model beyond product-line classification.
- Implement state-specific compliance controls to ensure that behavioral personalization does not constitute an insurance recommendation or marketing solicitation under applicable state regulations, particularly when behavioral signals could imply coverage gap detection.
- Coordinate portal personalization signals with the agent portal so that agents serving policyholders who have shown strong self-service research behavior receive a consolidated view of the customer's digital engagement alongside their service history.
