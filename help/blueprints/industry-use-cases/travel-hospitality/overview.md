---
title: Travel & Hospitality Use Cases
description: "Discover how travel and hospitality organizations use Adobe Experience Platform to personalize booking experiences, recover abandoned reservations, and build guest loyalty."
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
---

# Travel & Hospitality Use Cases

Travel and hospitality organizations use Adobe Experience Platform to bring together guest data from booking engines, loyalty programs, property management systems, and digital touchpoints into a single view of each traveler. This unified foundation powers personalized experiences that inspire bookings, recover abandoned reservations, and build the kind of guest loyalty that drives repeat visits.

## Personalized Homepage for New Visitors

Show personalized cruise, hotel, and destination recommendations on the homepage based on the visitor's geographic location and browsing behavior. First-time visitors who see relevant travel options immediately are far more likely to explore further and begin the booking process.

### Business impact

Personalizing the homepage for new visitors typically drives a 15-20% increase in conversion rate by presenting travel options that match the visitor's location and interests rather than generic content.

### How to implement

Use the [Anonymous Visitor Web Personalization](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md) pattern. This approach delivers tailored content to visitors who have not yet identified themselves, using available signals such as geolocation, device type, and referral source to personalize the experience from the very first page.

### Technical considerations

- Geolocation data must be resolved accurately at the edge to serve region-appropriate destinations, currencies, and departure ports without adding latency to the homepage load.
- Personalization rules should account for seasonal travel trends by region, surfacing warm-weather destinations to visitors in cold climates during winter months, for example.
- Fallback content strategies are essential for visitors whose location cannot be determined or who arrive through anonymizing services.
- Integration with the reservation system's availability feed ensures that featured properties and itineraries are actually bookable, preventing frustration from promoting sold-out options.

---

## Cart Abandonment Recovery Journey

Automatically detect when a customer abandons their booking cart and trigger a multi-step email journey with personalized offers to encourage completion. Abandoned reservations represent one of the largest revenue leaks in travel and hospitality, and timely follow-up while the travel intent is still fresh recovers a meaningful share of those bookings.

### Business impact

Effective booking recovery programs achieve a 25-35% cart recovery rate and can generate an additional $50,000 to $200,000 in monthly revenue depending on booking volume and average trip value.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. This approach responds to a real-time cart abandon event, sending a timely reminder while the customer's travel intent is still high.

### Technical considerations

- Cart abandon detection thresholds should account for the longer consideration cycles typical in travel purchases; a 2-4 hour delay before the first reminder is often more appropriate than the 30-60 minutes used in retail.
- Email content must dynamically pull current pricing, room or cabin availability, and imagery from the reservation system at send time, since travel inventory and rates change frequently.
- Personalized incentives such as complimentary upgrades or resort credits should be managed through business rules that account for margin, seasonality, and the customer's loyalty tier.
- Suppression logic must exclude customers who completed their booking through another channel, such as a call center or travel agent, to avoid irrelevant follow-up messages.

---

## High-Intent Visitor Targeting

Identify visitors with high purchase intent using AI-powered propensity scoring and target them with personalized offers and content. Recognizing which visitors are most likely to book allows the organization to focus its most compelling offers and sales outreach on the travelers who are closest to making a decision.

### Business impact

Targeting high-intent visitors with personalized offers drives a 30-40% increase in conversion for these segments, concentrating marketing investment where it delivers the greatest return.

### How to implement

Use the [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) pattern. This approach uses real-time profile data and behavioral signals to personalize the web experience for identified visitors, delivering tailored content and offers that match their level of purchase readiness.

### Technical considerations

- Propensity models must be trained on travel-specific intent signals such as date searches, pricing page views, room comparison activity, and repeat visits to the same destination within a short window.
- High-intent interventions, such as live chat prompts or limited-time offers, should appear at natural decision points in the booking flow rather than disrupting the browsing experience.
- The scoring model should distinguish between research intent and booking intent, since travelers often research months before they are ready to purchase.
- [!DNL Real-Time Customer Data Platform] computed attributes can aggregate behavioral signals across sessions to maintain an up-to-date intent score for each visitor.

---

## Post-Booking Upsell Campaigns

After a customer completes a booking, automatically trigger upsell campaigns for cabin upgrades, shore excursions, dining packages, and other ancillaries. The period between booking and travel is when guests are most excited about their upcoming trip and most receptive to enhancing their experience.

### Business impact

Post-booking upsell campaigns typically increase average order value by $200-$500 and lift ancillary revenue by 15-25%, turning a single booking into a significantly more valuable transaction.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. This multi-step journey guides booked customers through a timed sequence of upsell opportunities, adapting the offers based on what the guest has already purchased and their engagement with earlier messages.

### Technical considerations

- The journey must integrate with the reservation system to know exactly what the guest has booked, what upgrades are available for their specific itinerary, and current pricing for each ancillary option.
- Upsell timing should be staggered strategically; cabin upgrades may be offered shortly after booking, while excursions and dining packages perform better as the travel date approaches.
- Inventory and availability for ancillary products must be checked at the time of offer presentation, since excursion capacity and upgrade availability change continuously.
- [!DNL Journey Optimizer] personalization should account for the number of travelers in the booking, recommending family-appropriate excursions for family bookings and couples-oriented experiences for two-person reservations.

---

## Win-Back Campaigns for Lapsed Customers

Identify customers who have not booked in twelve or more months and engage them with personalized win-back offers and content based on their past travel preferences. Re-engaging lapsed guests is significantly more cost-effective than acquiring entirely new customers, and past travelers already have brand familiarity that lowers the barrier to rebooking.

### Business impact

Well-targeted win-back campaigns achieve a 10-15% reactivation rate among lapsed customers, recovering revenue from guests who might otherwise never return.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. This multi-step journey re-engages lapsed customers with a progressive series of messages that evolve from inspiration to incentive based on the customer's response.

### Technical considerations

- Lapsed customer segmentation should account for typical booking frequency in the travel category; a customer who books annually should not be flagged as lapsed after only six months of inactivity.
- Win-back content should reference the customer's past travel preferences, such as preferred destinations, cabin types, or travel seasons, to demonstrate that the brand remembers and values them.
- Offers should escalate across the journey, starting with inspirational content and progressing to monetary incentives only if earlier messages do not generate engagement.
- Customer records must be checked against the reservation system for any bookings made through offline channels such as travel agents or call centers to avoid sending win-back messages to customers who are actually active.

---

## Dynamic Itinerary Recommendations

Show personalized cruise itineraries and destinations based on the customer's past bookings, browsing history, and stated preferences. When travelers see itineraries tailored to their interests and travel style, they engage more deeply with the planning experience and move toward booking more quickly.

### Business impact

Personalized itinerary recommendations drive a 20-30% increase in engagement with itinerary pages, helping customers find the right trip faster and reducing the drop-off that occurs when travelers feel overwhelmed by too many options.

### How to implement

Use the [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) pattern. This approach personalizes website content for identified visitors, using their profile data and behavioral history to surface the most relevant itineraries and destinations.

### Technical considerations

- Itinerary recommendation logic must incorporate sailing or stay dates, departure ports, and duration preferences alongside destination interest to present options that are both appealing and practical for the customer.
- Integration with the central reservation system ensures that recommended itineraries have available inventory and reflect current pricing, preventing frustration from promoting sold-out sailings or fully booked properties.
- Seasonal factors should heavily influence recommendations; customers who previously booked summer Mediterranean cruises should see similar seasonal options rather than off-season alternatives.
- [!DNL Experience Platform] profile merge policies must correctly unify browsing behavior from multiple devices so that research conducted on mobile is reflected in desktop recommendations.

---

## Recently Browsed Products on Homepage

Display recently viewed cruises, hotels, or destinations on the homepage to remind visitors of their interest and encourage return visits. Travelers often research across multiple sessions before booking, and surfacing their previous interests eliminates the friction of starting their search over each time they return.

### Business impact

Showing recently browsed travel products on the homepage increases return visit engagement by 15-20%, helping customers pick up where they left off and shortening the path to booking.

### How to implement

Use the [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) pattern. This approach uses the visitor's stored profile data to render previously viewed items on the homepage, creating continuity across browsing sessions.

### Technical considerations

- Recently viewed data must persist across devices and sessions using identity resolution, so that a customer who browses on their phone sees the same items when they return on a desktop.
- Displayed items should show current pricing and availability status, with clear indicators if a previously viewed option is no longer available or if the price has changed since the last visit.
- The recency window for displayed items should be tuned to travel booking cycles; showing a cruise viewed three months ago may still be relevant, unlike a retail product viewed that long ago.
- Privacy considerations require that recently viewed content be tied to the customer's consent status, and an option to clear browsing history should be easily accessible.

---

## Exit Intent Modal with Targeted Offers

When a visitor shows exit intent, display a personalized modal with relevant offers based on their browsing behavior during the session. Catching a departing visitor with a compelling, contextually relevant offer provides one final opportunity to convert interest into a booking before they leave.

### Business impact

Exit intent modals with personalized travel offers recover a 5-10% conversion rate among visitors who would otherwise leave without booking, capturing revenue that would be entirely lost.

### How to implement

Use the [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) pattern. This approach uses centralized decision logic to evaluate all available offers and select the most relevant one for the departing visitor based on their session behavior and profile data.

### Technical considerations

- Exit intent detection on travel booking sites must account for multi-tab browsing behavior, since travelers frequently open multiple itineraries or properties in separate tabs without actually intending to leave.
- Offer selection should reflect what the visitor browsed during their session, presenting a discount on the specific destination or property they explored rather than a generic promotion.
- Modal frequency should be strictly limited to prevent visitors from seeing the same offer on every visit, which erodes the urgency and perceived exclusivity of the promotion.
- [!DNL Journey Optimizer] offer eligibility rules should consider the visitor's loyalty tier and booking history to present appropriately valued incentives, offering premium guests meaningful perks rather than small discounts.

---

## Loyalty Program Personalization

Personalize the website experience, offers, and communications based on the customer's loyalty tier, point balance, and engagement history. Loyalty members who see their status reflected across every touchpoint feel recognized and valued, which strengthens their commitment to the brand and encourages tier advancement.

### Business impact

Tier-based personalization drives a 25-35% increase in engagement from loyalty members, deepening the relationship and accelerating the earning and redemption behaviors that sustain long-term revenue.

### How to implement

Use the [Cross-Channel Journey with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pattern. This approach combines journey orchestration with real-time decisioning to deliver the right offer through the right channel for each loyalty member, adapting to their tier, preferences, and recent activity.

### Technical considerations

- Loyalty program data, including tier status, point balances, and earning history, must be ingested and kept current to ensure that website personalization and offers reflect the customer's actual standing.
- Tier-specific benefits such as early access to bookings, complimentary upgrades, and exclusive pricing must be enforced at the point of redemption, requiring tight integration with the reservation and pricing systems.
- Point balance changes from bookings, stays, and partner transactions should trigger recalculation of personalization rules in near real time, so that a customer who just earned enough points for a reward sees that option immediately.
- [!DNL Real-Time Customer Data Platform] audiences should be structured around loyalty tiers and key engagement milestones such as approaching the next tier or at risk of tier demotion.

---

## Multi-Channel Booking Reminders

Send personalized booking reminders via email, text message, and push notifications to customers who have started but not completed their reservations. Travelers frequently begin the booking process and get interrupted, and reaching them across their preferred channels with a reminder and their saved trip details brings them back to complete the reservation.

### Business impact

Multi-channel booking reminders improve booking completion rates by 20-30%, recovering significant revenue from customers who intended to book but were sidetracked before finishing.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. This approach triggers reminders automatically when an incomplete booking event is detected, delivering timely messages across the customer's preferred channels.

### Technical considerations

- Channel selection logic should respect customer communication preferences and optimize delivery based on past engagement patterns, sending push notifications to customers who respond well to mobile and email to those who prefer it.
- Reminder content must include a deep link that returns the customer directly to their saved booking with all selections intact, eliminating the friction of re-entering travel dates, room preferences, and guest details.
- Timing and frequency rules should coordinate across channels to avoid overwhelming the customer; an email and a push notification about the same booking should be spaced appropriately rather than sent simultaneously.
- Integration with the property management or central reservation system must verify that the originally selected room type, rate, and dates are still available before sending the reminder, updating the message if availability has changed.

---

## Seasonal Campaign Personalization

Personalize campaigns and offers based on seasonal preferences, past seasonal bookings, and current seasonal trends. Travelers are highly influenced by seasons, and campaigns that align with their demonstrated seasonal interests and current travel trends are far more compelling than generic promotions.

### Business impact

Seasonally personalized campaigns lift seasonal booking conversion by 15-25%, ensuring that marketing investment is concentrated on the destinations and travel products most likely to resonate with each customer.

### How to implement

Use the [Batch Outbound Message Activation](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) pattern. This approach delivers personalized seasonal campaign messages to large audiences on a scheduled basis, segmenting customers by their seasonal travel patterns and preferences.

### Technical considerations

- Customer seasonal preference profiles should be built from historical booking data, identifying patterns such as consistent summer beach vacations or winter ski trips to inform campaign targeting.
- Campaign scheduling must account for travel industry lead times; summer vacation campaigns should launch in early spring when families are planning, not in June when most bookings are already made.
- Pricing and availability feeds for seasonal inventory must be integrated so that promoted deals reflect real-time rates and actual room or cabin availability during the featured travel periods.
- [!DNL Experience Platform] audiences should combine seasonal preference data with recency indicators to prioritize customers who are in their typical planning window for the upcoming season.

---

## Group Booking Recommendations

Identify customers who frequently book group travel and proactively recommend group packages, family-friendly options, or multi-room bookings. Group bookings represent significantly higher revenue per transaction, and customers with a demonstrated pattern of group travel respond well to curated options that simplify the planning process.

### Business impact

Proactive group booking recommendations increase average order value by $1,000-$3,000 per booking, capturing the full value of group travel transactions that might otherwise be split across multiple individual reservations.

### How to implement

Use the [Behavioral Recommendation](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) pattern. This approach uses AI-driven models that learn from customer booking patterns and behavior to recommend the most relevant group travel options for each customer.

### Technical considerations

- Group travel identification requires analyzing booking history for patterns such as multi-room reservations, bookings with multiple passengers, and coordinated bookings made close together for the same dates and destination.
- Group package pricing must be pulled from the reservation system dynamically, since group rates often differ from individual rates and may require minimum party sizes or advance booking windows.
- Recommendation content should address the unique needs of group organizers, including information about group dining options, meeting spaces, block booking discounts, and group excursion availability.
- [!DNL Real-Time Customer Data Platform] profile enrichment should flag customers as group travel organizers based on their booking patterns, enabling targeted campaigns during peak group planning periods such as family reunion season or corporate retreat windows.
