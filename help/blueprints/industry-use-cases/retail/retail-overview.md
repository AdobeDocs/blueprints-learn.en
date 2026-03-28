---
title: Retail Use Cases
description: Discover how retail organizations use Adobe Experience Platform to personalize shopping experiences, recover abandoned carts, and drive customer loyalty.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: 89a5b6b5-bb71-4154-bb3b-f6dbbbef13eb
---
# Retail Use Cases

Retail organizations use Adobe Experience Platform to unify customer data from online stores, physical locations, and loyalty programs into a single view of each shopper. This foundation enables personalized shopping experiences, timely outreach that recovers lost revenue, and loyalty strategies that keep customers coming back.

## Personalized Product Recommendations

Show personalized product recommendations on homepage, category pages, and product detail pages based on browsing history, purchase history, and similar customer behavior. When shoppers see products tailored to their interests, they spend more time exploring and are far more likely to purchase.

### Business impact

Retailers see improved click-through rates and conversion rates when serving personalized recommendations instead of static product listings.

### How to implement

Use the [Behavioral Recommendation](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) pattern. This approach uses AI-driven recommendation models that continuously learn from customer interactions to surface the most relevant products for each individual. This is the right pattern when the item set is large and continuously changing and selection is driven by behavioral affinity — rather than a bounded set of offers governed by eligibility rules.

### Technical considerations

- Product catalog data must be ingested and kept current, including product attributes, images, pricing, and availability, to ensure recommendations reflect what customers can actually purchase.
- Behavioral signals such as product views, add-to-cart events, and purchases need to flow in near real time to keep recommendations fresh within a single browsing session.
- Recommendation models require a cold-start strategy for new visitors who lack browsing history, typically falling back to trending or best-selling products.
- Page load performance must be monitored carefully, as personalization calls should not add noticeable latency to the shopping experience.


## Abandoned Cart Email Recovery

Automatically send personalized email reminders to customers who abandoned their shopping cart, including the exact items left behind and relevant offers to encourage completion. Cart abandonment is one of the largest sources of lost revenue in retail, and timely follow-up can recover a significant share of those sales.

### Business impact

Effective cart recovery programs improve cart recovery rates and can generate meaningful incremental revenue depending on store volume.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. This approach responds to a real-time cart abandon event, sending a timely reminder while the purchase intent is still high. This is the right pattern when a discrete customer action is the trigger and the required response is a single, time-sensitive message — rather than a multi-step sequence or dynamic offer selection.

### Technical considerations

- Cart abandon detection requires defining a threshold for inactivity (commonly 30-60 minutes) before triggering the first reminder, avoiding messages to customers who are still actively shopping.
- Email content must dynamically pull current product images, prices, and availability from the catalog at send time, since items may sell out or change price between abandonment and delivery.
- Frequency capping rules should prevent customers from receiving multiple abandon cart emails in a short period, especially if they abandon carts frequently.
- Consent and suppression lists must be checked before sending, and customers who completed their purchase through another channel should be excluded in real time.


## Inventory-Based Urgency Campaigns

Trigger real-time alerts and campaigns when product inventory is low, creating urgency and encouraging immediate purchase. Shoppers who see that only a few items remain are motivated to act quickly rather than delay their decision.

### Business impact

Low-inventory urgency campaigns drive improved conversion for featured products while also helping reduce overstock by accelerating sell-through of slow-moving items.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. This approach responds to inventory threshold events, automatically activating urgency messaging when stock levels drop below defined limits. This is the right pattern when the trigger is a system event rather than a customer behavior, and the required communication is immediate and reactive rather than a sustained nurture sequence.

### Technical considerations

- Inventory feeds must integrate with the customer data platform in near real time so that urgency messaging reflects actual stock levels rather than stale data.
- Threshold levels should be configured per product category, since a "low stock" threshold for a high-volume commodity differs significantly from one for a luxury item.
- Messaging must be truthful and comply with consumer protection regulations; displaying false scarcity can damage brand trust and may violate advertising standards in certain markets.
- On-site messaging and email channels should be coordinated so that a customer who already purchased does not continue to receive urgency notifications for the same product.


## Cross-Sell and Upsell Recommendations

Display relevant cross-sell and upsell products at checkout, in email, and on product pages based on purchase patterns and product relationships. Suggesting complementary or premium alternatives at the right moment increases basket size without requiring customers to search for related items themselves.

### Business impact

Well-executed cross-sell and upsell strategies increase average order value and lift revenue per transaction, contributing to stronger overall basket economics.

### How to implement

Use the [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) pattern. This approach uses centralized decision logic to evaluate all available offers and select the best cross-sell or upsell option for each customer and context. This is the right pattern when offer selection must account for margin, inventory availability, and product relationship rules — business constraints that require governed decisioning logic rather than behavioral affinity ranking alone.

### Technical considerations

- Product relationship data, including "frequently bought together" associations and upgrade paths, must be maintained and regularly refreshed to reflect current purchasing patterns.
- Offer ranking logic should account for margin, relevance, and inventory levels so that the most profitable and available options surface first.
- Cross-sell recommendations at checkout must load quickly and not disrupt the purchase flow; slow or intrusive suggestions can actually reduce conversion.
- [!DNL Journey Optimizer] decision rules should include fallback offers so that every eligible customer receives a recommendation, even when the top-ranked option is unavailable.


## New Customer Welcome Series

Automate a multi-email welcome series for new customers with personalized product recommendations, brand storytelling, and special offers. The first few interactions after a customer joins shape their long-term relationship with the brand, making this series one of the highest-impact programs a retailer can run.

### Business impact

A well-designed welcome series drives strong engagement among new customers and meaningfully improves lifetime value by building brand affinity early.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. This multi-touch nurture journey guides new customers through a sequence of brand introduction, product discovery, and incentive messages, adapting based on their engagement. This is the right pattern when the use case requires a sequenced, multi-message flow over days with conditional branching based on engagement events — a single triggered message cannot accommodate the dependency logic between steps.

### Technical considerations

- The journey entry trigger must reliably capture new customer creation events from all registration sources, including web, mobile app, in-store point-of-sale, and third-party marketplaces.
- Wait steps between emails should be configured based on engagement data; customers who open and click may receive the next message sooner, while less engaged customers benefit from more spacing.
- Product recommendations within welcome emails should reflect what the customer browsed or purchased during their first visit, not generic best-sellers.
- Customers who make a purchase during the welcome series should branch into a post-purchase flow rather than continuing to receive acquisition-focused messaging.


## Price Drop Alerts

Notify customers via email or push notification when products in their wishlist or previously viewed items drop in price. Shoppers who showed interest but did not purchase are highly responsive to price reductions, making this one of the most efficient ways to convert consideration into sales.

### Business impact

Price drop alerts generate improved conversion rates among recipients and measurably increase customer satisfaction by helping shoppers feel they are getting the best value.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. This approach responds to product price change events, matching them against customer interest signals to deliver timely notifications. This is the right pattern when the trigger is a catalog system event and the delivery window is time-sensitive — a sustained journey would be too slow, and no multi-step follow-up is needed beyond the initial notification.

### Technical considerations

- Price change detection requires comparing current prices against previous values in the product catalog feed, and only triggering alerts for meaningful reductions rather than minor fluctuations.
- Customer interest signals (wishlist additions, product page views, time spent on product pages) must be stored and matched efficiently against potentially thousands of daily price changes.
- Notifications should include the original price, new price, and savings amount to clearly communicate the value; vague "price reduced" messages underperform specific savings callouts.
- [!DNL Real-Time Customer Data Platform] segments for price-sensitive shoppers can be used to prioritize alert delivery and tailor the messaging tone.


## Replenishment Reminders

Send automated reminders to customers for products they purchase regularly, such as subscription items and consumables, to encourage repeat purchases before they run out. Proactive reminders reduce the chance that customers switch to a competitor simply because they forgot to reorder.

### Business impact

Replenishment reminder programs drive improved repeat purchase rates and improve customer retention by making it effortless for shoppers to restock the products they rely on.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. This recurring scheduled journey uses purchase frequency predictions to send reminders at the optimal time before a customer is likely to need a refill. This is the right pattern when there is no discrete triggering event and timing must be calculated from purchase frequency models that recalibrate dynamically — event-triggered messaging cannot handle predictive scheduling or timing adjustments when customers reorder early or late.

### Technical considerations

- Purchase frequency calculation must account for varying consumption rates across product categories; a reminder for coffee should arrive on a different cadence than one for cleaning supplies.
- The journey should adjust its timing dynamically when a customer reorders earlier or later than predicted, recalibrating the next reminder based on updated purchase data.
- Reminders should include a direct reorder link or one-click repurchase option to minimize friction and maximize conversion from the notification.
- Customers who have already reordered through another channel (in-store, subscription service) must be suppressed to avoid sending irrelevant reminders.


## Personalized Category Pages

Dynamically personalize category pages to show the most relevant products first based on each customer's preferences, past purchases, and browsing behavior. When shoppers see products aligned with their tastes at the top of the page, they discover what they want faster and convert at higher rates.

### Business impact

Personalized category pages drive improved category page engagement and meaningfully improve product discovery, particularly for retailers with large catalogs.

### How to implement

Use the [Behavioral Recommendation](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) pattern. This approach uses selection strategies and ranking models to reorder products on category pages based on each visitor's profile and real-time behavior. This is the right pattern when the task is ranking a large, open product set using behavioral affinity signals — offer decisioning is not appropriate here because there are no eligibility rules or business constraints limiting which products appear.

### Technical considerations

- Product ranking must execute quickly enough to avoid perceived page load delays; server-side personalization or edge-based decisioning is often required for category pages with hundreds of products.
- The personalization logic should blend individual preferences with merchandising rules, ensuring that promoted products, new arrivals, and seasonal items still receive appropriate visibility.
- A/B testing infrastructure should be in place to measure the revenue impact of personalized sorting versus default merchandising rules on an ongoing basis.
- [!DNL Experience Platform] Web SDK implementation must capture category page interactions (scroll depth, product clicks, filter usage) to continuously refine the ranking models.


## Post-Purchase Follow-Up Campaigns

Send post-purchase emails with product care tips, related product suggestions, review requests, and loyalty program information. The period immediately after a purchase is when customers are most engaged with the brand, making it an ideal window to deepen the relationship and encourage future activity.

### Business impact

Effective post-purchase campaigns increase review submission rates and drive improved repeat purchase rates, turning one-time buyers into loyal customers.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern. This multi-step post-purchase flow uses branching logic to tailor follow-up messages based on product type, customer segment, and engagement with earlier emails in the series. This is the right pattern because the follow-up spans multiple days, depends on fulfillment status events, and branches based on product category and return events — a single triggered message cannot support the conditional logic required across the full post-purchase timeline.

### Technical considerations

- The journey must account for order fulfillment status; care tips and review requests should only send after the product has been delivered, not immediately after purchase.
- Product-specific content (care instructions, usage guides, accessory suggestions) requires a content mapping system that associates each product category with relevant follow-up materials.
- Review request timing should be optimized based on the product category; electronics may need a longer usage period before a meaningful review, while apparel can be reviewed shortly after delivery.
- Customers who initiate a return or exchange should be automatically removed from the standard post-purchase flow and redirected to a service recovery path.


## VIP Customer Exclusive Offers

Identify high-value customers and provide exclusive offers, early access to sales, and personalized shopping experiences that reward their loyalty. Retaining top-tier customers is far more cost-effective than acquiring new ones, and exclusive treatment strengthens the emotional connection that keeps them spending.

### Business impact

VIP programs generate strong engagement from top-tier customers and measurably improve customer lifetime value by reducing churn among the most profitable segment.

### How to implement

Use the [Cross-Channel Journey with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pattern. This approach combines journey orchestration with real-time decisioning for offer selection, ensuring each VIP customer receives the most relevant exclusive offer across every channel. This is the right pattern when the journey must coordinate delivery across channels to prevent duplicate offers and when offer selection requires eligibility rules and business constraints — multi-step orchestration alone does not provide the real-time decisioning layer needed to govern which exclusive offer each VIP receives.

### Technical considerations

- VIP segmentation criteria must be clearly defined using recency, frequency, and monetary value metrics, and segments should refresh frequently enough to capture customers who recently qualified or disqualified.
- Exclusive offers must be enforced at the point of redemption (web, app, store) to prevent non-VIP customers from accessing them, which requires integration with promotion and pricing systems.
- Channel preferences vary significantly among high-value customers; some prefer email, others respond to app notifications or direct mail, so the journey should adapt delivery channels based on past engagement.
- [!DNL Journey Optimizer] decisioning must coordinate across channels to prevent a VIP customer from receiving the same offer via email, push, and SMS simultaneously.


## Out-of-Stock Notifications

Allow customers to sign up for notifications when out-of-stock products become available, then automatically notify them via email or text message. Capturing demand for unavailable products prevents lost sales and gives customers a reason to return to the store rather than purchasing from a competitor.

### Business impact

Back-in-stock notifications achieve strong conversion rates among subscribers and meaningfully reduce lost sales for high-demand products that experience temporary stockouts.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern. This approach triggers notifications on back-in-stock events, matching inventory updates against customer notification sign-ups to deliver timely alerts. This is the right pattern because the trigger is a discrete inventory system event, delivery is time-critical (inventory may sell out again quickly), and the communication is a single notification rather than an ongoing journey.

### Technical considerations

- Inventory monitoring must detect restocking events quickly; delays of even a few hours can result in the product selling out again before notified customers have a chance to purchase.
- When a popular product is restocked in limited quantity, notifications should be staggered or prioritized by sign-up date to avoid sending alerts to more customers than the available inventory can serve.
- The notification sign-up mechanism must capture channel preference (email or text message) and comply with opt-in requirements for each channel, particularly for SMS.
- [!DNL Real-Time Customer Data Platform] profile attributes should track which products each customer is watching so that duplicate notifications are prevented if the same product restocks multiple times.


## Social Proof Personalization

Display personalized social proof, including reviews, ratings, and "customers who bought this also bought" suggestions, based on each customer's profile and preferences. Tailoring social proof to reflect the experiences of similar customers builds trust more effectively than generic ratings alone.

### Business impact

Personalized social proof increases conversion rates and improves shopper confidence, particularly for first-time buyers and higher-priced products where purchase hesitation is greatest.

### How to implement

Use the [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) pattern. This approach personalizes web content for identified visitors, selecting the most relevant reviews and social proof elements based on the customer's profile, preferences, and browsing context. This is the right pattern when personalization is driven by profile attributes and segment membership rather than a behavioral affinity model — behavioral recommendation is not appropriate here because social proof selection depends on who the customer is, not which items they have browsed.

### Technical considerations

- Review and rating data must be structured and tagged by customer attributes (such as purchase context, customer segment, and product use case) to enable meaningful filtering and personalization.
- Social proof elements should load asynchronously to avoid blocking the main product page render, since review data may come from a third-party review platform with variable response times.
- Privacy regulations require that any customer data used to match reviews to visitors is handled according to consent preferences; displaying "customers like you" content implies profiling that may require disclosure.
- [!DNL Experience Platform] audience membership can be used to select which reviews to highlight, showing outdoor enthusiasts reviews from fellow outdoor shoppers rather than generic top-rated reviews.


## AI Product Advisor

Online retailers carry thousands of SKUs across complex category hierarchies, making it difficult for shoppers to find the right product without extended browsing or abandoned searches. An AI-powered product advisor engages shoppers in natural multi-turn dialogue — asking qualifying questions about needs, preferences, and budget — then narrows the assortment to a curated set of personalized recommendations. The experience mirrors the guidance a knowledgeable in-store associate would provide, delivered at digital scale.

### Business impact

Retailers that deploy guided conversational discovery see improved conversion rates and average order value compared to unassisted browsing, while also reducing product returns through better-informed purchase decisions.

### How to implement

Use the [Brand Concierge Conversational Experience](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md) pattern. This approach deploys the Product Advisor Agent against a structured product catalog, using AEP Agent Orchestrator and real-time customer profile data to generate brand-safe, personalized product recommendations through natural dialogue. This is the right pattern when the goal is interactive, multi-turn conversational discovery driven by customer-stated needs — distinct from event-triggered messaging, which is one-directional and reactive to a specific action, and from personalized web experiences, which display recommendations passively rather than engaging customers in conversation. It requires AEP Agent Orchestrator and brand governance configuration.

### Technical considerations

- The product catalog must be structured with rich attribute data — including size, material, compatibility, availability, and pricing — because the Product Advisor Agent grounds recommendations in catalog content and cannot reliably advise on products with incomplete attributes.
- Real-time customer profile lookup via RT-CDP must be configured with edge activation so that purchase history, browsing behavior, and loyalty tier data are accessible during the live conversation without latency that would disrupt the experience.
- Brand governance guardrails must be defined to specify how the agent handles out-of-stock items, competitive product comparisons, promotional pricing claims, and prohibited topics, ensuring every response aligns with retail brand standards.
- Conversational events — including intent signals, product interactions, and recommendation acceptance — must be captured as XDM ExperienceEvents and streamed back to AEP, enriching customer profiles with product affinity data that improves future personalization across all channels.


## Cross-Channel Attribution Analysis

Measure how each marketing touchpoint — paid search, email, social, and in-store promotions — contributes to online and offline purchase conversions. Retailers who rely on last-touch attribution systematically undervalue upper-funnel channels and make budget allocation decisions based on an incomplete picture of the purchase path.

### Business impact

Retail marketing teams that move from last-touch to multi-touch attribution gain a clearer view of which channels drive purchase intent, leading to better-informed budget decisions and improved return on marketing spend.

### How to implement

Use the [Customer Analytics & Insight Generation](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) pattern. This approach connects online and offline event data — web clicks, email engagements, loyalty transactions, and point-of-sale records — to Customer Journey Analytics, where attribution models can be configured and compared across the full purchase path. This is the right pattern when the goal is measurement and insight generation across a complex, multi-channel journey — rather than activating audiences or triggering messages — and when the analysis requires Customer Journey Analytics rather than a CDP or campaign orchestration tool.

### Technical considerations

- Point-of-sale and e-commerce transaction data must share a consistent customer identifier so that in-store and online conversions can be stitched into a single cross-channel view in CJA.
- Multiple attribution models — first-touch, last-touch, linear, and time-decay — should be configured in the CJA data view so analysts can compare them side by side without rebuilding the analysis.
- Paid media impression and click data from external ad platforms must be ingested via source connectors or batch uploads to include paid channels in the attribution path alongside owned channels.
- Conversion windows and credit lookback periods need to be defined per channel type, since the relevant attribution window for a paid search click differs significantly from that of a seasonal email campaign.

## Audience Segmentation & Activation for Paid Media

Build high-value audience segments from unified customer profiles and activate them across paid media destinations such as Google Ads, Meta, and The Trade Desk for acquisition and retargeting campaigns. Unifying behavioral, transactional, and loyalty data enables more precise targeting that reduces wasted ad spend and improves campaign return on investment.

### Business impact

Retailers who activate high-quality first-party audiences see improved match rates on paid media platforms, reduced cost per acquisition, and stronger return on ad spend compared to relying on third-party segments.

### How to implement

Use the [Audience Activation to Destinations](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md) pattern to evaluate audience membership against unified profiles and publish segments to connected paid media destinations on a scheduled or streaming basis. This is the right pattern when the primary requirement is segment publication to external systems rather than orchestrated messaging or real-time decisioning.

### Technical considerations

- Identity resolution across web, mobile, and loyalty data is required to build complete customer profiles before activation — fragmented profiles reduce audience quality and match rates.
- Destination connectors must be configured for each paid media platform, with appropriate consent flags respected at the profile level to prevent non-consented data from being activated.
- Segment refresh frequency should align with campaign objectives — acquisition audiences may need daily refreshes while retargeting audiences benefit from near-real-time updates to exclude recent purchasers.
- Overlap analysis between acquisition and retention audiences helps prevent cross-contamination where existing customers receive new-customer acquisition messaging.


## Customer Suppression for Acquisition Campaigns

Suppress existing customers and recent converters from acquisition ad spend by activating exclusion audiences to paid media destinations, reducing wasted spend. Continuously syncing suppression lists ensures that paid budgets target net-new prospects rather than people who have already converted or are actively engaged.

### Business impact

Suppressing existing customers from acquisition campaigns reduces wasted paid media spend, improves cost per acquisition metrics, and prevents existing customers from receiving messaging that is irrelevant to their relationship stage.

### How to implement

Use the [Audience Activation to Destinations](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md) pattern to publish exclusion audiences — recent purchasers, active subscribers, high-value customers — to each paid media destination on a frequent schedule. This is the right pattern when the objective is segment publication for suppression rather than orchestrating a customer-facing journey.

### Technical considerations

- Suppression audiences require a clear definition of who to exclude — typically customers who purchased within the last 30-90 days, active loyalty members, and recent email converts.
- Exclusion lists must be refreshed frequently enough to exclude purchasers before ads serve; stale suppression lists cause the most brand friction in high-volume retail periods.
- Identity matching quality directly affects suppression accuracy — poor email or device ID matching will result in existing customers still seeing acquisition ads.
- Ensure that suppression audiences are separate from retention audiences so that win-back campaigns can still reach lapsed customers who should not be suppressed.


## Personalized Web Experiences for Known Visitors

Deliver personalized hero banners, product recommendations, and promotional content to authenticated website visitors based on their real-time profile, segment membership, and behavioral history. When returning customers see experiences tailored to their loyalty status, purchase history, and preferences, engagement rates and conversion improve significantly compared to generic homepage experiences.

### Business impact

Retailers who personalize for known visitors see meaningful improvement in engagement metrics including time on site, pages per session, and conversion rate, with the greatest impact among loyalty members who visit frequently.

### How to implement

Use the [Known-Visitor Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) pattern to deliver profile-driven personalized experiences at page load using real-time segment membership and profile attributes. This is the right pattern when the experience must be driven by identity-linked profile data rather than session-only signals — and when content decisions do not require complex offer ranking or business constraints.

### Technical considerations

- Authentication must occur before profile-driven personalization can activate; the website needs a mechanism to identify the visitor and resolve their ECID to a known profile.
- Real-time profile lookups must complete within the page load latency budget, typically requiring edge-deployed profile evaluation rather than server-side API calls on the critical rendering path.
- Content variations must be designed for all audience segments that will be targeted, including a default experience for visitors who don't match any personalization rule.
- Personalization decisions should be logged for analysis, enabling A/B testing of content variations and attribution of engagement improvements to specific segments.


## Anonymous Visitor Web Personalization

Personalize content for unidentified website visitors using in-session behavioral signals such as pages viewed, product categories browsed, and referral source. Since the majority of retail web traffic is anonymous, personalizing for unrecognized visitors significantly expands the reach of on-site personalization beyond the authenticated segment.

### Business impact

Retailers serving personalized experiences to anonymous visitors see improved engagement and first-visit conversion rates, with particularly strong impact on visitors arriving from specific campaign sources or browsing high-intent category pages.

### How to implement

Use the [Anonymous Visitor Web Personalization](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md) pattern to evaluate in-session behavioral signals at the edge and serve relevant content variations without requiring authentication. This is the right pattern when personalization must work immediately from the first interaction without relying on a persistent profile — particularly for acquisition traffic and visitors who have not yet logged in.

### Technical considerations

- In-session personalization relies on streaming event data collected via Edge Network; the edge evaluation rules must be deployed and tested before traffic is sent to them.
- Content variations should be designed around high-signal in-session behaviors — referral source, first page viewed, product category explored — rather than low-signal attributes that don't reliably predict intent.
- Privacy requirements must be evaluated carefully; some jurisdictions treat behavioral personalization as requiring consent even for anonymous visitors.
- Personalization rules for anonymous visitors should be simpler and faster to evaluate than known-visitor rules, as edge latency constraints are more stringent.


## Welcome Series Journey

Orchestrate a multi-step welcome journey for newly registered customers, delivering onboarding content, product education, and a first-purchase incentive across email and push channels. A well-designed welcome series sets the tone for the customer relationship and significantly increases the likelihood that a new registrant converts to their first purchase.

### Business impact

Welcome series programs drive meaningful improvements in new customer activation rates and first-purchase conversion, with the strongest impact when the series combines educational content with a timely, personalized incentive.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern to design a multi-day onboarding sequence with wait steps, channel branching based on engagement, and suppression when the first purchase goal is achieved. This is the right pattern when the use case requires a sequenced, time-spaced communication flow with conditional logic — a single triggered message is insufficient to guide a new customer through the onboarding experience.

### Technical considerations

- Journey entry should be triggered by account registration events in real time so the first welcome message arrives promptly while registration intent is high.
- The journey must include exit conditions that suppress remaining messages when a new customer completes their first purchase — continuing the welcome series after purchase undermines message relevance.
- Channel preference must be respected throughout; push notification steps require app installation and push opt-in, with email fallback for customers without opt-in.
- Personalization in the welcome series improves conversion but requires enough profile data to be meaningful — new profiles often need a fallback to bestsellers or trending products.


## Cart Abandonment Recovery

Trigger real-time email and push notifications when a customer abandons their shopping cart, with personalized product reminders and time-limited incentives to complete the purchase. Cart abandonment is among the highest-ROI use cases in retail, recovering revenue from customers who have already demonstrated strong purchase intent.

### Business impact

Well-executed cart abandonment programs recover a meaningful share of abandoned revenue, with recovery rates highest when the first message arrives within one hour of abandonment and includes the exact items left in the cart.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern to respond to the cart abandon event with an immediate triggered communication while purchase intent is still active. This is the right pattern when a discrete customer action is the trigger and the primary requirement is a timely, personalized response — rather than a multi-week nurture sequence or complex offer decisioning with business constraints.

### Technical considerations

- Cart abandon detection requires a defined inactivity threshold (typically 30-60 minutes) to avoid messaging customers who are still actively browsing or completing the checkout flow.
- Email content must dynamically render current product images, prices, and inventory status at send time, as items may sell out or change price between abandonment and message delivery.
- Suppression logic must exclude customers who completed their purchase through another channel between abandonment detection and message send.
- Frequency capping rules should prevent repeat cart abandonment messages in short windows, particularly for customers who habitually abandon carts as a browsing behavior.


## Post-Purchase Engagement Journey

Deliver post-purchase communications including order confirmation, shipping updates, cross-sell recommendations, and review requests through an orchestrated multi-step journey. The post-purchase window is one of the highest-engagement moments in the customer lifecycle, making it an ideal time to build loyalty and introduce relevant complementary products.

### Business impact

Retailers with structured post-purchase journeys see improved repeat purchase rates and customer review submission rates, contributing to both long-term loyalty and social proof that supports future acquisition.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern to orchestrate a sequence of post-purchase communications timed to key milestones: order confirmation, shipment, delivery, and post-delivery follow-up. This is the right pattern when the use case spans multiple days with multiple objectives — a single triggered message cannot accommodate the arc from transactional confirmation to loyalty building to review solicitation.

### Technical considerations

- Order management system integration is required to receive real-time purchase and shipment events; delays in event ingestion create awkward timing in post-purchase communications.
- Cross-sell recommendations in the post-purchase sequence require real-time product catalog data and recommendation model inference at message render time to reflect current inventory and pricing.
- Review request messages must comply with platform terms of service for incentivized reviews and should be timed after the customer has had sufficient time to use the product.
- Channel coordination is important — customers should not receive both email and push for the same milestone unless they have engaged with the first channel.


## Loyalty Tier Upgrade Campaign

Identify customers approaching loyalty tier thresholds and deliver targeted campaigns encouraging them to reach the next tier with personalized offers based on purchase history and preferences. When customers are within reach of a tier upgrade, targeted messaging with personalized incentives creates urgency and drives incremental purchase behavior.

### Business impact

Loyalty tier upgrade campaigns drive incremental purchase volume and improve program engagement, with the strongest impact among mid-tier members who are close to the next threshold and have shown recent purchase activity.

### How to implement

Use the [Multi-Step Orchestrated Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) pattern to build a tier proximity campaign that enters customers when they reach a defined spend threshold below their next tier level and guides them through a sequence of benefit messaging and incentive offers. This is the right pattern when the use case requires monitoring a calculated profile attribute over time and orchestrating a multi-step campaign tied to the customer's progress toward a goal.

### Technical considerations

- Loyalty platform data — points balance, tier status, tier thresholds — must be ingested and kept current in the customer profile so that tier proximity calculations are accurate.
- Tier upgrade campaigns should be suppressed for customers who have already achieved the target tier or whose loyalty status has changed since campaign entry.
- Personalized incentives in the upgrade campaign should be constrained to offers the customer is genuinely eligible for and that do not undermine the perceived value of the tier structure.
- The campaign must include clear exit conditions for customers who complete their tier upgrade mid-journey, pivoting to a congratulations message rather than continuing the persuasion sequence.


## Cross-Channel Campaign Orchestration

Orchestrate coordinated marketing campaigns across email, SMS, push, and web channels with journey branching, wait steps, and frequency capping to maximize engagement without fatigue. Coordinated cross-channel orchestration ensures that customers receive a coherent campaign experience regardless of which channel they respond to first, eliminating duplicate messaging and conflicting offers.

### Business impact

Retailers with cross-channel orchestration capabilities see higher campaign engagement and conversion rates than single-channel campaigns, while also reducing unsubscribe rates driven by channel fatigue from uncoordinated messaging.

### How to implement

Use the [Cross-Channel Journey with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) pattern to build campaigns that route customers through personalized channel sequences based on their engagement history, channel preferences, and real-time response signals. This is the right pattern when the campaign requires governed offer selection, channel preference routing, and dynamic branching based on in-journey engagement — rather than a fixed sequence sent to all campaign recipients.

### Technical considerations

- Global frequency caps must be configured across all channels to prevent customers from receiving excessive communications when multiple journeys are running simultaneously.
- Channel preference data must be current and actionable — preference profiles that are months out of date will route customers to channels they no longer engage with.
- Journey orchestration logic should handle re-entry gracefully, preventing customers from entering the same campaign twice while ensuring they are not excluded from genuinely new campaigns.
- Real-time engagement signals (email opens, link clicks, web sessions) should feed back into the journey to enable channel switching and early exit for customers who have already converted.


## Brand Concierge Conversational Experience

Deploy an AI-powered, brand-safe conversational agent across digital properties to provide personalized product guidance, site navigation help, and seamless handoff to live agents. An on-site AI concierge extends personalized service at scale, helping shoppers discover products, compare options, and complete purchases without requiring human agent intervention for common queries.

### Business impact

Retailers with AI concierge capabilities report improved self-service resolution rates, reduced inbound support volume for product and navigation questions, and higher conversion among customers who engage with conversational guidance before purchase.

### How to implement

Use the [Brand Concierge Conversational Experience](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md) pattern to deploy a governed AI agent grounded in product catalog data, brand guidelines, and real-time customer profile context. This is the right pattern when the use case requires natural language interaction over a large, dynamic product set — rather than a scripted chatbot with fixed intents or a pattern that matches a specific channel like email.

### Technical considerations

- The AI agent must be grounded in current product catalog data including descriptions, specifications, availability, and pricing to provide accurate guidance; stale product data leads to incorrect recommendations.
- Brand safety guardrails must be configured to prevent the agent from discussing competitor products, making pricing commitments that conflict with promotions, or responding to off-topic queries.
- Handoff logic to live agents requires integration with the service platform and should be triggered when the AI agent cannot resolve the customer's query after a defined number of turns.
- Profile data integration enables the agent to personalize responses based on purchase history and loyalty status, but this requires identity resolution before the conversational session begins.

## Check-in Reminder with App Download CTA

Remind guests to check-in, and encourage them to download the app in order to access information easily. Timely check-in reminders paired with app download prompts drive mobile engagement and enable richer in-venue experiences.

### Business impact

Retailers that combine check-in reminders with app download calls-to-action see increased app adoption rates and higher in-store engagement, as customers who use the mobile app tend to interact more frequently with promotions and venue content.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern to trigger a check-in reminder with app download CTA based on event attendance or reservation data. This is the right pattern when a single timely message needs to be sent in response to a known event or schedule trigger.

### Technical considerations

- Check-in reminders must be timed appropriately relative to the event or visit date to maximize engagement without being perceived as too early or too late.
- App download deep links should route to the correct app store based on the customer's device platform (iOS or Android).
- Customers who already have the app installed should receive a different message variant that skips the download CTA and focuses on check-in functionality.

## Birthday Campaigns for Fans

Target fans on their birthday with a personalized birthday message and an exclusive offer. Birthday campaigns create emotional connections with fans and drive incremental purchases through timely, personalized outreach.

### Business impact

Birthday campaigns consistently deliver above-average open and conversion rates because they arrive at a moment of personal significance, creating goodwill and encouraging fans to treat themselves with a special purchase.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern to send a personalized birthday message when the customer's birthday date arrives. This is the right pattern when a single event-driven message is sent based on a profile attribute date trigger.

### Technical considerations

- Birthday date must be captured in the customer profile and validated to avoid sending messages on incorrect dates.
- Offers should have a defined validity window (such as the birthday week) to create urgency while giving customers reasonable time to redeem.
- Fans without a birthday on file should be excluded from the campaign rather than sent a generic message.

## Birthday Campaigns for Shoppers

Target shoppers on their birthday with a personalized birthday message and an exclusive offer. Birthday campaigns build brand loyalty by acknowledging customers personally and encouraging a celebratory purchase.

### Business impact

Personalized birthday offers drive higher redemption rates than generic promotions because they align with a moment when shoppers are already inclined to make discretionary purchases for themselves.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern to trigger a birthday message and offer based on the shopper's birth date profile attribute. This is the right pattern when a single personalized message needs to be delivered on a specific calendar date tied to the customer profile.

### Technical considerations

- Birthday date must be stored as a profile attribute and should be collected during registration or loyalty sign-up.
- Offer personalization should consider the shopper's purchase history and preferences to present relevant product suggestions alongside the birthday discount.
- Duplicate suppression logic is needed for customers who appear in multiple systems to avoid sending multiple birthday messages.

## Game Day Promotion Campaigns

Target fans to buy tickets for an upcoming game with personalized promotions and offers. Game day promotions drive ticket sales by reaching the right audience with timely, event-specific messaging.

### Business impact

Targeted game day promotions improve ticket sell-through rates by reaching fans with relevant offers based on their team preferences, past attendance, and proximity to the venue.

### How to implement

Use the [Batch Outbound Message Activation](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) pattern to send promotional messages to segmented fan audiences ahead of upcoming games. This is the right pattern when a batch of personalized messages needs to be sent to a pre-built audience segment on a scheduled basis.

### Technical considerations

- Game schedule data must be integrated to trigger promotions at the right lead time before each event.
- Audience segmentation should account for team affinity, geographic proximity, and past attendance patterns to maximize relevance.
- Customers who have already purchased tickets for the promoted game should be suppressed from acquisition messaging and may instead receive upsell offers for upgrades or add-ons.

## Product Promotion Campaigns

Target shoppers to buy products during an ongoing product promotion campaign. Promotional campaigns drive revenue by connecting the right customers with timely offers aligned to active promotions.

### Business impact

Targeted product promotion campaigns outperform broad-reach promotions by focusing on shoppers most likely to convert, reducing promotional waste and improving return on marketing spend.

### How to implement

Use the [Batch Outbound Message Activation](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) pattern to send promotional messages to qualified audience segments during active campaign windows. This is the right pattern when a scheduled batch of personalized promotional messages needs to reach a defined audience during a time-bound campaign.

### Technical considerations

- Promotion start and end dates must be managed to ensure messages are only sent during the active promotion window.
- Audience segmentation should leverage purchase history, browsing behavior, and product affinity to target shoppers most likely to engage with the promoted products.
- Frequency capping should be applied to prevent promotional fatigue, especially when multiple campaigns run concurrently.

## Shopping Cart Abandon

Re-engage customers who abandon their shopping cart with personalized reminders and incentives to complete the purchase. Cart abandonment recovery is one of the highest-ROI use cases in retail marketing.

### Business impact

Cart abandonment recovery campaigns recover a meaningful percentage of otherwise lost revenue by re-engaging shoppers at the moment of highest purchase intent with personalized reminders and incentives.

### How to implement

Use the [Event-Triggered Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) pattern to trigger a recovery message when a cart abandonment event is detected. This is the right pattern when a single real-time message needs to be sent in response to a behavioral event such as leaving items in the cart without completing checkout.

### Technical considerations

- Cart abandonment detection requires a defined inactivity threshold (typically 30-60 minutes) to distinguish true abandonment from customers who are still browsing.
- Cart contents must be passed in the event payload to enable personalized product reminders in the recovery message.
- Customers who complete their purchase between the abandonment event and the message send must be suppressed to avoid irrelevant messaging.
