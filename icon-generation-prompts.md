# Icon Generation Prompts for Missing Use Cases

46 use cases across 7 industries need icons generated. For each prompt generate at 1024x1024 pixels, and save as PNG to the path listed.

## Design Style Reference

All existing icons follow a consistent visual language. New icons MUST match:

- **Style:** Minimal flat design icon — simple geometric shapes and recognizable symbols
- **Color palette:** Only 2-3 colors on a white background:
  - **Blue** rgb(13, 65, 149) — primary color for main objects
  - **Light gray** rgb(174, 174, 174) — secondary color for supporting objects
  - **White** #FFFFFF — background
- **Composition:** 2-3 recognizable objects arranged together (e.g., envelope + cart + arrow, phone + checkmark + arrow), centered composition
- **Shape treatment:** Simple geometric shapes, clean edges, bold simplified solid fills
- **Absolutely no text, letters, or words** of any kind
- **No gradients, no 3D effects**
- **Professional look** suitable for display at small sizes like 96x96 pixels

**Prompt preamble (included with every prompt below):**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels.

---

## Retail (3 icons needed)

Existing icons for style reference: icon-abandoned-cart (cart + envelope + arrow), icon-price-drop (envelope + dollar pin with down arrow), icon-welcome-series (person + envelope + gear), icon-replenishment (bottle + bell + envelope with checkmark), icon-cross-sell-upsell (browser window + shopping bags + arrows)

### Out-of-Stock Notifications

- **Filename:** `icon-out-of-stock.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/retail/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue product box with a light gray notification bell above it and a blue envelope with a checkmark beside it, representing a back-in-stock product notification.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/retail/icon-out-of-stock.png" alt="Out-of-Stock Notifications" width="40">
```

---

### Social Proof Personalization

- **Filename:** `icon-social-proof.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/retail/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue speech bubble with a star rating inside it, a light gray person silhouette beside it, and a small blue thumbs-up icon, representing customer reviews and social proof personalization.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/retail/icon-social-proof.png" alt="Social Proof Personalization" width="40">
```

---

### VIP Customer Exclusive Offers

- **Filename:** `icon-vip-offers.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/retail/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue crown symbol above a light gray gift box with a ribbon, and a small blue star badge beside it, representing VIP exclusive offers for premium customers.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/retail/icon-vip-offers.png" alt="VIP Customer Exclusive Offers" width="40">
```

---

## Financial Services (7 icons needed)

Existing icons for style reference: icon-lead-nurturing (profile card + arrows + envelope with dollar), icon-churn-prevention (cart + eye + megaphone with circular arrow), icon-account-dashboard (browser window + chart bars + person), icon-life-stage (timeline with milestone markers)

### Transaction-Based Alerts and Recommendations

- **Filename:** `icon-transaction-alerts.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/financial-services/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue credit card with a light gray notification bell above it and a small blue lightning bolt symbol, representing real-time transaction alerts and recommendations.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/financial-services/icon-transaction-alerts.png" alt="Transaction Alerts" width="40">
```

---

### Credit Card Application Abandonment Recovery

- **Filename:** `icon-credit-card-abandonment.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/financial-services/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue credit card with a light gray curved return arrow wrapping around it and a blue envelope beside it, representing re-engagement of abandoned credit card applications.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/financial-services/icon-credit-card-abandonment.png" alt="Credit Card Application Abandonment" width="40">
```

---

### Fraud Alert Personalization

- **Filename:** `icon-fraud-alert.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/financial-services/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue shield with a white exclamation mark inside it, a light gray lock icon beside it, and a small blue bell, representing fraud alert personalization and security notifications.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/financial-services/icon-fraud-alert.png" alt="Fraud Alert" width="40">
```

---

### Investment Portfolio Recommendations

- **Filename:** `icon-investment-portfolio.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/financial-services/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue pie chart divided into segments, a light gray upward-trending arrow beside it, and a small blue person silhouette, representing personalized investment portfolio recommendations.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/financial-services/icon-investment-portfolio.png" alt="Investment Portfolio" width="40">
```

---

### Mortgage Pre-Approval Campaigns

- **Filename:** `icon-mortgage-preapproval.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/financial-services/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue house silhouette with a light gray checkmark badge overlapping it and a blue document with lines beside it, representing mortgage pre-approval campaigns.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/financial-services/icon-mortgage-preapproval.png" alt="Mortgage Pre-Approval" width="40">
```

---

### Loyalty Program Engagement

- **Filename:** `icon-loyalty-program.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/financial-services/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue card with a white star on it, a light gray bar chart showing ascending tiers beside it, and a small blue person silhouette, representing loyalty program engagement and rewards tiers.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/financial-services/icon-loyalty-program.png" alt="Loyalty Program" width="40">
```

---

### Personalized Financial Education Content

- **Filename:** `icon-financial-education.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/financial-services/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue open book with a light gray dollar sign above it and a small blue graduation cap, representing personalized financial education content delivery.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/financial-services/icon-financial-education.png" alt="Financial Education" width="40">
```

---

## Healthcare (8 icons needed)

Existing icons for style reference: icon-appointment-reminder (calendar with checkmark + gear + envelope + speech bubble), icon-medication-adherence (pill bottle + capsule + tablet + speech bubble with clock), icon-post-visit (clipboard + person + arrow), icon-preventive-care (shield + heart + stethoscope)

### Lab Results Notification

- **Filename:** `icon-lab-results.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/healthcare/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue test tube with liquid inside it, a light gray envelope beside it, and a small blue bell notification icon, representing lab results notification to patients.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/healthcare/icon-lab-results.png" alt="Lab Results" width="40">
```

---

### Insurance Coverage Verification

- **Filename:** `icon-insurance-coverage.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/healthcare/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue ID card with a white cross symbol on it, a light gray checkmark badge overlapping the corner, and a small blue calendar icon, representing insurance coverage verification before appointments.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/healthcare/icon-insurance-coverage.png" alt="Insurance Coverage" width="40">
```

---

### Telehealth Appointment Reminders

- **Filename:** `icon-telehealth.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/healthcare/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue laptop screen with a white video camera icon on it, a light gray clock beside it, and a small blue medical cross symbol, representing telehealth appointment reminders.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/healthcare/icon-telehealth.png" alt="Telehealth" width="40">
```

---

### Chronic Disease Management Programs

- **Filename:** `icon-chronic-disease.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/healthcare/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue heart with a white pulse/heartbeat line through it, a light gray clipboard beside it, and a small blue circular arrow representing ongoing monitoring, representing chronic disease management programs.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/healthcare/icon-chronic-disease.png" alt="Chronic Disease Management" width="40">
```

---

### New Patient Onboarding Journey

- **Filename:** `icon-patient-onboarding.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/healthcare/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue person silhouette with a light gray clipboard with checklist items beside it and a small blue forward arrow, representing new patient onboarding journey.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/healthcare/icon-patient-onboarding.png" alt="Patient Onboarding" width="40">
```

---

### Wellness Program Engagement

- **Filename:** `icon-wellness-program.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/healthcare/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue leaf or apple inside a circle, a light gray trophy or star badge beside it, and a small blue person silhouette, representing wellness program engagement and health rewards.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/healthcare/icon-wellness-program.png" alt="Wellness Program" width="40">
```

---

### Care Team Coordination

- **Filename:** `icon-care-team.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/healthcare/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. Two blue person silhouettes connected by light gray bidirectional arrows, with a small blue medical cross symbol between them, representing care team coordination and collaborative patient care.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/healthcare/icon-care-team.png" alt="Care Team" width="40">
```

---

### Personalized Health Content Delivery

- **Filename:** `icon-health-content.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/healthcare/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue tablet or screen displaying a white medical cross, a light gray document with lines beside it, and a small blue person silhouette, representing personalized health content delivery.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/healthcare/icon-health-content.png" alt="Health Content" width="40">
```

---

## Insurance (9 icons needed)

Existing icons for style reference: icon-policy-renewal (clipboard with checklist + megaphone + circular arrow), icon-claims-process (document + magnifying glass + checkmark), icon-cross-sell (document + arrow + second document + star)

### Policy Change Notifications

- **Filename:** `icon-policy-change.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/insurance/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue document with white lines on it, a light gray pencil or edit symbol overlapping the corner, and a small blue bell notification icon, representing policy change notifications.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/insurance/icon-policy-change.png" alt="Policy Change" width="40">
```

---

### Quote Abandonment Recovery

- **Filename:** `icon-quote-abandonment.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/insurance/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue document with a white dollar sign on it, a light gray curved return arrow wrapping around it, and a small blue envelope, representing abandoned insurance quote recovery.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/insurance/icon-quote-abandonment.png" alt="Quote Abandonment" width="40">
```

---

### Claims Fraud Prevention

- **Filename:** `icon-claims-fraud.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/insurance/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue magnifying glass examining a light gray document, with a small blue warning triangle with an exclamation mark, representing claims fraud detection and prevention.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/insurance/icon-claims-fraud.png" alt="Claims Fraud" width="40">
```

---

### Catastrophic Event Response

- **Filename:** `icon-catastrophic-event.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/insurance/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue shield with a white lightning bolt inside it, a light gray megaphone beside it, and a small blue house silhouette, representing proactive catastrophic event response and customer communication during disasters.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/insurance/icon-catastrophic-event.png" alt="Catastrophic Event" width="40">
```

---

### Agent and Broker Coordination

- **Filename:** `icon-agent-coordination.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/insurance/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue person silhouette on the left, a light gray person silhouette on the right, connected by blue bidirectional arrows between them, with a small blue envelope below, representing agent and broker coordination with customers.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/insurance/icon-agent-coordination.png" alt="Agent Coordination" width="40">
```

---

### Risk Assessment and Prevention

- **Filename:** `icon-risk-assessment.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/insurance/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue semicircular gauge meter with a white needle, a light gray shield with a checkmark beside it, and a small blue clipboard, representing risk assessment and prevention.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/insurance/icon-risk-assessment.png" alt="Risk Assessment" width="40">
```

---

### Wellness and Prevention Programs

- **Filename:** `icon-wellness-prevention.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/insurance/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue heart with a white cross inside it, a light gray person silhouette in an active pose beside it, and a small blue star badge, representing wellness and prevention programs for insurance customers.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/insurance/icon-wellness-prevention.png" alt="Wellness Prevention" width="40">
```

---

### Life Stage-Based Product Offers

- **Filename:** `icon-life-stage.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/insurance/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue winding path with three light gray milestone circle markers along it, and a small blue document with a checkmark at the end, representing life stage transitions and personalized insurance product offers.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/insurance/icon-life-stage.png" alt="Life Stage" width="40">
```

---

### Discount and Savings Opportunities

- **Filename:** `icon-discount-savings.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/insurance/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue price tag with a white percentage symbol on it, a light gray piggy bank beside it, and a small blue downward arrow, representing personalized discount and savings opportunities.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/insurance/icon-discount-savings.png" alt="Discount Savings" width="40">
```

---

## Media & Entertainment (9 icons needed)

Existing icons for style reference: icon-new-content (clapperboard + bell), icon-content-recommendations (browser window with grid + star + person), icon-subscription-churn (broken card + warning triangle)

### Watchlist and Favorites Reminders

- **Filename:** `icon-watchlist-reminders.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/media-entertainment/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue bookmark or flag icon, a light gray clock beside it, and a small blue play button triangle, representing watchlist and favorites reminders for unwatched content.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/media-entertainment/icon-watchlist-reminders.png" alt="Watchlist Reminders" width="40">
```

---

### Live Event Viewing Reminders

- **Filename:** `icon-live-event.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/media-entertainment/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue broadcast/antenna tower emitting light gray signal waves, a small blue calendar icon beside it, and a light gray bell, representing live event viewing reminders.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/media-entertainment/icon-live-event.png" alt="Live Event" width="40">
```

---

### Content Completion Campaigns

- **Filename:** `icon-content-completion.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/media-entertainment/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue circular progress ring three-quarters complete, a white play button triangle in the center, and a small light gray forward arrow, representing content completion reminders for unfinished shows.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/media-entertainment/icon-content-completion.png" alt="Content Completion" width="40">
```

---

### Personalized Homepage Experience

- **Filename:** `icon-personalized-homepage.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/media-entertainment/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue browser window frame with light gray content tile grid inside it, one tile highlighted in blue, and a small light gray person silhouette beside it, representing a dynamically personalized homepage experience.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/media-entertainment/icon-personalized-homepage.png" alt="Personalized Homepage" width="40">
```

---

### Personalized Playlist Generation

- **Filename:** `icon-playlist-generation.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/media-entertainment/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue music note, a light gray list or stacked horizontal lines beside it, and a small blue sparkle or magic wand icon, representing automatically generated personalized playlists.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/media-entertainment/icon-playlist-generation.png" alt="Playlist Generation" width="40">
```

---

### Free Trial Conversion Campaigns

- **Filename:** `icon-trial-conversion.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/media-entertainment/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue hourglass, a light gray upward arrow beside it, and a small blue star or checkmark badge, representing converting free trial users to paid subscribers.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/media-entertainment/icon-trial-conversion.png" alt="Trial Conversion" width="40">
```

---

### Cross-Platform Content Sync

- **Filename:** `icon-cross-platform-sync.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/media-entertainment/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue smartphone on the left and a blue laptop on the right, connected by light gray circular sync arrows between them, representing seamless cross-platform content synchronization.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/media-entertainment/icon-cross-platform-sync.png" alt="Cross-Platform Sync" width="40">
```

---

### Social Sharing Personalization

- **Filename:** `icon-social-sharing.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/media-entertainment/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue share network symbol (three dots connected by lines), a light gray speech bubble beside it, and a small blue person silhouette, representing personalized social sharing prompts.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/media-entertainment/icon-social-sharing.png" alt="Social Sharing" width="40">
```

---

### Premium Feature Upsell

- **Filename:** `icon-premium-upsell.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/media-entertainment/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue diamond or gem shape, a light gray upward arrow beside it, and a small blue crown symbol, representing premium feature upsell opportunities.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/media-entertainment/icon-premium-upsell.png" alt="Premium Upsell" width="40">
```

---

## Telecommunications (9 icons needed)

Existing icons for style reference: icon-plan-optimization (signal bars + gear), icon-device-upgrade (smartphone + checkmark circle + upload arrow circle), icon-churn-prevention (shield + signal waves)

### Data Usage Alerts and Recommendations

- **Filename:** `icon-data-usage.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/telecommunications/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue bar chart nearly full, a light gray warning triangle beside it, and a small blue bell notification icon, representing data usage alerts when customers approach their limits.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/telecommunications/icon-data-usage.png" alt="Data Usage" width="40">
```

---

### Service Outage Notifications

- **Filename:** `icon-service-outage.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/telecommunications/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue signal tower with light gray broken or disconnected signal waves emanating from it, and a small blue warning triangle with an exclamation mark, representing service outage notifications.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/telecommunications/icon-service-outage.png" alt="Service Outage" width="40">
```

---

### Bill Payment Reminders

- **Filename:** `icon-bill-payment.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/telecommunications/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue document with a white dollar sign on it, a light gray clock beside it, and a small blue envelope, representing bill payment reminders with due date awareness.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/telecommunications/icon-bill-payment.png" alt="Bill Payment" width="40">
```

---

### 5G Upgrade Campaigns

- **Filename:** `icon-5g-upgrade.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/telecommunications/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue ascending signal bars icon, a light gray rocket or speed streak beside it, and a small blue upward arrow, representing 5G upgrade campaign offers for eligible customers.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/telecommunications/icon-5g-upgrade.png" alt="5G Upgrade" width="40">
```

---

### New Customer Onboarding Journey

- **Filename:** `icon-customer-onboarding.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/telecommunications/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue smartphone, a light gray person silhouette with a forward arrow beside it, and a small blue checklist clipboard, representing new telecommunications customer onboarding with feature tutorials.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/telecommunications/icon-customer-onboarding.png" alt="Customer Onboarding" width="40">
```

---

### Network Performance Personalization

- **Filename:** `icon-network-performance.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/telecommunications/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue speedometer or gauge icon, light gray signal bars behind it, and a small blue gear symbol, representing personalized network performance information.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/telecommunications/icon-network-performance.png" alt="Network Performance" width="40">
```

---

### Family Plan Management

- **Filename:** `icon-family-plan.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/telecommunications/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue large person silhouette with two smaller light gray person silhouettes beside it, connected under a blue arc or umbrella shape, representing family plan management for telecommunications.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/telecommunications/icon-family-plan.png" alt="Family Plan" width="40">
```

---

### Add-On Service Recommendations

- **Filename:** `icon-addon-services.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/telecommunications/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue main square block, a light gray plus symbol in a circle connected to it by a line, and a small blue arrow pointing right, representing add-on service recommendations.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/telecommunications/icon-addon-services.png" alt="Add-On Services" width="40">
```

---

### Loyalty Program Engagement

- **Filename:** `icon-loyalty-program.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/telecommunications/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue card with a white star on it, light gray signal waves emanating from the top, and a small blue person silhouette beside it, representing telecommunications loyalty program engagement and rewards.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/telecommunications/icon-loyalty-program.png" alt="Loyalty Program" width="40">
```

---

## B2B (1 icon needed)

Existing icons for style reference: icon-abm (person + document + checkmark), icon-lead-scoring (gauge + person + score), icon-customer-onboarding (person + checklist + arrow), icon-contract-renewal (document + circular arrow + checkmark)

### Customer Advocacy Programs

- **Filename:** `icon-customer-advocacy.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/b2b/`

**Prompt:**

> Minimal flat design icon, use only 2-3 colors (primarily shades of blue rgb(13, 65, 149) and light gray rgb(174, 174, 174) on a white #FFFFFF background), simple geometric shapes and recognizable symbols, absolutely no text or letters or words, no gradients, no 3D effects, centered composition, clean edges, professional look suitable for display at small sizes like 96x96 pixels. Square format, 1024x1024 pixels. A blue megaphone, a light gray person silhouette with a star badge beside it, and a small blue speech bubble with a thumbs-up inside, representing customer advocacy programs where satisfied customers provide references and testimonials.

**Catalog HTML:**

```html
<img src="assets/use-case-icons/b2b/icon-customer-advocacy.png" alt="Customer Advocacy" width="40">
```
