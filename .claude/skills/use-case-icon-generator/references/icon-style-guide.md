# Use Case Icon Style Guide

## Overview

Use case icons serve as visual identifiers in the use case catalog table. They must be immediately recognizable at 40px display width while maintaining quality at their native 1024x1024 resolution.

## Technical Specifications

| Property | Value |
| --- | --- |
| Dimensions | 1024 x 1024 pixels |
| Format | PNG (8-bit RGB or RGBA) |
| File size | 900KB - 1.4MB typical |
| Display size | 40px width in catalog tables |
| Naming | `icon-{kebab-case-name}.png` |
| Storage path | `/help/blueprints/industry-use-cases/assets/use-case-icons/{industry}/` |

## Visual Style Guidelines

### Composition
- **Single central subject** — Each icon should feature one clear visual metaphor that represents the use case concept
- **Centered composition** — The main subject should be centered with balanced whitespace
- **No text** — Text is illegible at 40px; rely entirely on visual metaphor
- **No complex scenes** — Avoid multi-element compositions, backgrounds with many objects, or narrative scenes
- **Bold silhouettes** — The icon's shape should be recognizable even as a tiny silhouette

### Color & Tone
- **Clean, modern palette** — Use professional, corporate-appropriate colors
- **Industry cohesion** — Icons within the same industry should feel like they belong together
- **High contrast** — Ensure the main subject stands out clearly from the background
- **Avoid neon or overly saturated colors** — Keep the palette refined and professional

### Style
- **Modern and professional** — Clean lines, polished finish
- **Consistent rendering** — All icons should appear to come from the same design system
- **3D or flat is acceptable** — But be consistent within an industry vertical
- **Avoid photorealism** — Illustrated or rendered style preferred for consistency
- **No brand logos or trademarked imagery** — Use generic visual metaphors

### Small-Size Legibility Test
Before finalizing, mentally scale the image to 40px:
- Can you identify the main subject?
- Is there enough contrast between foreground and background?
- Are there any fine details that would turn into visual noise?
- Does the shape read clearly without color (in case of accessibility)?

## Visual Metaphor Examples by Industry

### Retail
| Use Case | Visual Metaphor |
| --- | --- |
| Abandoned Cart | Shopping cart with items |
| Product Recommendations | Gift box or curated products |
| Cross-Sell Upsell | Connected shopping items |
| Welcome Series | Welcome card or gift |
| Price Drop | Price tag with down arrow |

### Automotive
| Use Case | Visual Metaphor |
| --- | --- |
| Service Reminders | Wrench or service calendar |
| Vehicle Purchase | Car with keys |
| Trade-In | Car exchange arrows |
| Connected Car | Car with digital connection |

### Healthcare
| Use Case | Visual Metaphor |
| --- | --- |
| Appointment Reminder | Calendar with stethoscope |
| Medication Adherence | Pill bottle or prescription |
| Preventive Care | Shield with health symbol |

### Financial Services
| Use Case | Visual Metaphor |
| --- | --- |
| Lead Nurturing | Growth chart or seedling |
| Churn Prevention | Shield or retention symbol |
| Life Stage | Life milestones timeline |

### B2B
| Use Case | Visual Metaphor |
| --- | --- |
| ABM | Target with building |
| Lead Scoring | Scoring gauge or thermometer |
| Contract Renewal | Document with refresh symbol |

### Travel & Hospitality
| Use Case | Visual Metaphor |
| --- | --- |
| Cart Abandonment | Suitcase or booking |
| Loyalty Program | Loyalty card or star badge |
| Booking Reminders | Calendar with plane/hotel |

### Insurance
| Use Case | Visual Metaphor |
| --- | --- |
| Policy Renewal | Document with renewal arrows |
| Claims Process | Clipboard with checkmark |
| Cross-Sell | Connected policy documents |

### Media & Entertainment
| Use Case | Visual Metaphor |
| --- | --- |
| New Content | Play button or spotlight |
| Content Recommendations | Curated playlist or starred content |
| Subscription Churn | Broken subscription card |

### Telecommunications
| Use Case | Visual Metaphor |
| --- | --- |
| Plan Optimization | Signal bars with gear |
| Device Upgrade | Phone with up arrow |
| Churn Prevention | Shield with signal |

## Image Generation Prompt Template

Use this template as a starting point, customizing the subject and details for each use case:

```
A clean, modern icon illustration of {visual metaphor} representing {use case concept}. Professional corporate design style with bold shapes and clean lines. Single centered subject on a {solid/gradient} background. High contrast, vibrant but refined color palette. No text, no fine details, no complex backgrounds. The icon must be clearly recognizable when scaled down to 40 pixels. Square format, 1024x1024 pixels.
```

### Prompt Customization Tips

- **Be specific about the subject** — "A bright red shopping cart with two colorful gift boxes inside" is better than "a shopping cart"
- **Specify background treatment** — "on a soft blue gradient background" or "on a clean white background with subtle shadow"
- **Mention lighting** — "soft studio lighting" or "gentle ambient glow" helps achieve consistency
- **Add style modifiers** — "minimalist", "geometric", "isometric", or "flat design" to steer the aesthetic
- **Include negative prompts if supported** — "no text, no watermarks, no borders, no photorealistic elements"

## Existing Icon Inventory

### By Industry

**Retail (9 icons):**
icon-abandoned-cart, icon-inventory-urgency, icon-price-drop, icon-product-recommendations, icon-category-pages, icon-welcome-series, icon-replenishment, icon-post-purchase, icon-cross-sell-upsell

**Automotive (12 icons):**
icon-service-reminders, icon-recall-notifications, icon-test-drive, icon-model-launch, icon-trade-in, icon-parts-accessories, icon-warranty, icon-connected-car, icon-dealer-network, icon-vehicle-purchase, icon-financing, icon-owner-loyalty

**Financial Services (6 icons):**
icon-lead-nurturing, icon-account-dashboard, icon-product-recommendation, icon-churn-prevention, icon-life-stage

**Healthcare (4 icons):**
icon-appointment-reminder, icon-post-visit, icon-preventive-care, icon-medication-adherence

**Insurance (3 icons):**
icon-policy-renewal, icon-claims-process, icon-cross-sell

**Media & Entertainment (3 icons):**
icon-new-content, icon-content-recommendations, icon-subscription-churn

**Telecommunications (3 icons):**
icon-plan-optimization, icon-device-upgrade, icon-churn-prevention

**Travel & Hospitality (12 icons):**
icon-cart-abandonment, icon-booking-reminders, icon-seasonal-campaigns, icon-personalized-homepage, icon-high-intent, icon-post-booking-upsell, icon-win-back, icon-dynamic-itinerary, icon-recently-browsed, icon-group-booking, icon-exit-intent, icon-loyalty-program

**B2B (11 icons):**
icon-webinar-demo, icon-abm, icon-lead-scoring, icon-content-personalization, icon-event-registration, icon-trial-conversion, icon-customer-onboarding, icon-competitive-replacement, icon-case-study, icon-contract-renewal, icon-upsell-expansion
