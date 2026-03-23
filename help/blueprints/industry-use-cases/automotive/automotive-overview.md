---
title: Automotive Use Cases
description: Discover how automotive organizations use Adobe Experience Platform to personalize the vehicle purchase journey, improve service retention, and build owner loyalty.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: ee83c739-0907-481d-ba3f-358af4e03c67
---
# Automotive use cases

Automotive organizations use Adobe Experience Platform to unify customer data from dealership interactions, online vehicle research, service records, and connected car systems into a single view of each owner. This foundation enables personalized experiences throughout the entire ownership lifecycle, from initial vehicle research through purchase, service, and loyalty.

## Use case summary

| Use Case | Description | Business Impact | Implementation Pattern |
| --- | --- | --- | --- |
| [Vehicle Purchase Journey Personalization](#vehicle-purchase-journey-personalization) | Personalize the vehicle purchase journey from research to purchase with relevant vehicle recommendations, financing options, and dealer information. When potential buyers receive tailored guidance at each stage, they move through the sales funnel more quickly and with greater confidence. | Improved lead-to-purchase conversion rates and stronger sales pipeline | [Cross-Channel Journey with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| [Service Appointment Reminders](#service-appointment-reminders) | Send personalized service reminders based on vehicle mileage, service history, and customer preferences. Proactive outreach keeps vehicles maintained and ensures customers return to the dealership rather than seeking third-party providers. | Improved service appointment show rates and increased service revenue | [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [Trade-In Value Campaigns](#trade-in-value-campaigns) | Proactively offer trade-in value assessments to customers who may be ready to upgrade. Reaching owners at the right point in their ownership cycle accelerates the path to a new vehicle purchase. | Improved trade-in engagement and increased new vehicle sales | [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [Parts and Accessories Recommendations](#parts-and-accessories-recommendations) | Recommend relevant parts, accessories, and upgrades based on vehicle model, ownership duration, and customer preferences. Personalized aftermarket recommendations drive incremental revenue while helping owners get more from their vehicle. | Improved parts and accessories purchase rates and increased aftermarket revenue | [Behavioral Recommendation](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| [Vehicle Recall Notifications](#vehicle-recall-notifications) | Send personalized recall notifications with service scheduling options and safety information. Timely, clear recall communications protect customer safety and demonstrate the brand's commitment to responsible ownership support. | Improved recall response rates and stronger safety compliance | [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [New Model Launch Campaigns](#new-model-launch-campaigns) | Target customers who may be interested in new model launches based on their current vehicle, preferences, and purchase history. Focused audience targeting maximizes launch impact and builds early order momentum. | Improved launch campaign engagement and increased new model interest | [Batch Outbound Message Activation](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| [Financing and Insurance Offers](#financing-and-insurance-offers) | Present personalized financing and insurance offers based on credit profile, vehicle selection, and purchase timeline. Tailored financial products remove barriers to purchase and help customers feel confident in their terms. | Improved financing acceptance rates and increased revenue per sale | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| [Test Drive Scheduling](#test-drive-scheduling) | Enable personalized test drive scheduling with dealer recommendations and vehicle availability. Making it effortless for interested buyers to get behind the wheel accelerates the path to purchase. | Improved test drive completion rates and stronger sales conversion | [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [Owner Loyalty Programs](#owner-loyalty-programs) | Coordinate loyalty communications across dealer, OEM digital, and connected car channels, applying tier-based eligibility rules to govern which owners receive exclusive offers, early vehicle access, and partner rewards. Offer arbitration prevents conflicting promotions from dealer and OEM channels reaching the same owner simultaneously. | Improved loyalty program engagement and increased repeat purchases | [Cross-Channel Journey with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| [Warranty and Extended Service Plans](#warranty-and-extended-service-plans) | Recommend warranty and extended service plans at optimal times based on vehicle age, mileage, and purchase patterns. Well-timed outreach captures revenue before factory warranties expire. | Improved extended warranty adoption rates and increased service revenue | [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [Connected Car Feature Activation](#connected-car-feature-activation) | Personalize connected car feature recommendations based on vehicle capabilities and technology preferences. Helping owners discover unused features increases satisfaction and strengthens the digital relationship. | Improved feature activation rates and better customer experience | [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [Dealer Network Coordination](#dealer-network-coordination) | Enable personalized dealer recommendations based on customer location, preferences, and dealer inventory. Connecting customers with the right dealership improves the buying and service experience. | Improved dealer engagement rates and stronger sales coordination | [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

## Technical considerations by use case

### Vehicle purchase journey personalization

- Vehicle inventory data from dealer management systems must be integrated and refreshed frequently so that recommendations reflect actual availability at nearby dealerships.
- Customer research behavior across the website, including vehicle configuration activity, comparison tool usage, and brochure downloads, must be captured to accurately identify purchase intent signals.
- Lead scoring models should account for both online engagement and offline signals such as dealership visits and phone inquiries to prioritize the highest-intent prospects.
- [!DNL Real-Time Customer Data Platform] profiles must merge anonymous web research sessions with known customer identities once a prospect registers or visits a dealership.

### Service appointment reminders

- Vehicle mileage and telematics data from connected car systems or dealer service records must flow into customer profiles to trigger reminders at the correct service intervals.
- Reminder messages should include one-click scheduling links that pre-populate the customer's vehicle information and recommended service items to minimize booking friction.
- Service history records must be integrated to avoid recommending services that were recently completed and to personalize the reminder with the specific maintenance items due.
- [!DNL Journey Optimizer] message timing should account for dealer service capacity and hours of operation to ensure customers can book appointments when they receive the reminder.

### Trade-in value campaigns

- Vehicle valuation data from third-party providers must be integrated and refreshed regularly to ensure trade-in estimates shared with customers are accurate and competitive.
- Ownership lifecycle models should consider factors such as lease expiration dates, loan payoff timelines, and average ownership duration by vehicle segment to identify the optimal outreach window.
- Campaign messaging should dynamically reference the customer's current vehicle and suggest specific upgrade options that align with their preferences and budget.
- [!DNL Experience Platform] segments should exclude customers who recently purchased a vehicle or are currently in an active service dispute to avoid poorly timed outreach.

### Parts and accessories recommendations

- Product catalog data must include vehicle compatibility information so that recommendations only show parts and accessories that fit the customer's specific vehicle year, make, and model.
- Seasonal and regional factors should influence recommendations; winter accessories should be promoted in colder climates, while performance upgrades may resonate more in regions with active enthusiast communities.
- Browsing behavior on parts and accessories pages must be captured and associated with customer profiles to refine recommendations based on expressed interest.
- [!DNL Experience Platform] Web SDK implementation should capture vehicle identification number data from authenticated sessions to ensure compatibility filtering is accurate.

### Vehicle recall notifications

- Vehicle identification number records must be accurately maintained in customer profiles so that recall notifications reach every affected owner and do not go to unaffected customers.
- Recall messaging must comply with regulatory requirements for safety notification content, timing, and delivery confirmation in each applicable market.
- Multi-channel delivery (email, text message, push notification, and physical mail) should be used to maximize reach, as safety-critical communications require higher delivery assurance than marketing messages.
- [!DNL Journey Optimizer] should track recall response status at the individual level and escalate follow-up communications for owners who have not scheduled service within a defined timeframe.

### New model launch campaigns

- Audience segments for launch campaigns should consider current vehicle model, ownership duration, past model interest signals, and demographic fit to identify the highest-propensity prospects.
- Launch content should be personalized to reference the customer's current vehicle and highlight specific improvements or features that address their likely priorities.
- Campaign timing must coordinate with embargo dates and regional launch schedules to ensure customers receive information at the appropriate time for their market.
- [!DNL Real-Time Customer Data Platform] audience activation should synchronize launch segments to advertising platforms for coordinated paid media support alongside owned-channel outreach.

### Financing and insurance offers

- Financial offer eligibility rules must be carefully configured to comply with lending regulations, ensuring that offers presented to customers are ones they can actually qualify for.
- Credit profile data integration requires secure handling and strict access controls, as financial information is subject to heightened privacy and regulatory requirements.
- Offer presentation must clearly disclose terms, rates, and conditions in compliance with consumer finance regulations in each applicable market.
- [!DNL Journey Optimizer] decisioning rules should factor in vehicle price, down payment, and loan term preferences to rank offers by relevance rather than simply by rate.

### Test drive scheduling

- Dealer inventory systems must be integrated to confirm that the specific vehicle model and trim the customer is interested in is available for test drive at the recommended dealership.
- Location-based dealer recommendations should factor in customer address, dealer ratings, and current appointment availability to suggest the most convenient option.
- Test drive confirmation and reminder messages should include directions, dealer contact information, and what to expect, reducing no-show rates.
- [!DNL Experience Platform] behavioral data should identify the optimal moment to suggest a test drive, avoiding premature outreach to early-stage researchers who are not yet ready.

### Owner loyalty programs

- Loyalty tier calculations must incorporate multiple dimensions of engagement including service visits, parts purchases, referrals, and event attendance, not just vehicle purchase history.
- Tier-based eligibility rules must be configured in [!DNL Journey Optimizer] decisioning to govern which owners qualify for exclusive offers, early access to new vehicle reveals, and partner reward redemptions, ensuring only eligible members receive each category of benefit.
- Offer arbitration logic must evaluate pending communications from both dealer and OEM channels before any message is sent, suppressing lower-priority or conflicting promotions to prevent the same owner from receiving contradictory offers simultaneously.
- Cross-channel coordination must span dealer CRM systems, OEM digital properties, connected car notification channels, and service touchpoints so that loyalty interactions are consistent regardless of where the owner engages.
- Reward fulfillment systems at dealerships and service centers must be integrated so that loyalty benefits can be redeemed seamlessly at the point of service.
- Communications should adapt based on ownership lifecycle stage, delivering different value propositions to new owners in their first year versus long-term owners approaching a potential upgrade.
- [!DNL Journey Optimizer] journey logic should detect tier changes in real time and trigger congratulatory or re-engagement messages when customers move between loyalty levels.

### Warranty and extended service plans

- Warranty expiration dates and coverage details must be accurately tracked in customer profiles to trigger outreach at the right time, typically 60-90 days before expiration.
- Vehicle mileage and usage patterns from connected car data or service records should inform plan recommendations, as high-mileage drivers benefit from different coverage than low-mileage owners.
- Plan comparison content should be clear and jargon-free, helping customers understand exactly what is covered and the value relative to potential out-of-pocket repair costs.
- [!DNL Real-Time Customer Data Platform] segments should distinguish between customers with expiring factory warranties, those with existing extended plans approaching renewal, and those with no current coverage.

### Connected car feature activation

- Connected car platform data must be integrated to identify which features are available on each vehicle and which ones the owner has already activated or used.
- Feature adoption tracking should capture activation events, usage frequency, and engagement depth to personalize the sequence and pacing of feature recommendations.
- In-vehicle notification channels should be coordinated with email and app notifications to deliver feature prompts at the most contextually relevant moment, such as suggesting navigation features when a road trip is detected.
- [!DNL Experience Platform] profiles should store vehicle technology configuration data including installed packages and software versions to ensure feature recommendations are compatible with the owner's specific vehicle.

### Dealer network coordination

- Dealer inventory feeds must be integrated and refreshed frequently to ensure that vehicle availability shown to customers accurately reflects what is on each dealer's lot.
- Customer-to-dealer assignment logic should consider proximity, dealer specialization, language preferences, and any existing dealer relationship to provide the best match.
- Lead routing rules must ensure that when a customer expresses purchase interest online, the inquiry reaches the appropriate dealer quickly with full context about the customer's research activity.
- [!DNL Experience Platform] identity resolution must handle scenarios where a customer interacts with multiple dealerships, maintaining a unified profile while respecting each dealer's view of their own customer relationships.
