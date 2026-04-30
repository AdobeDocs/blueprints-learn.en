# Blueprint Audit & Recommendations

This audit applies the [evaluation rubric](rubric.md) to every document under the
"Architecture Diagrams and Blueprints" section of [TOC.md](../help/blueprints/TOC.md) (lines 76–133), and
recommends whether each blueprint should become a use case **Pattern**, an architecture
**Diagram**, both (**Split**), or be flagged as a **Duplicate** of an existing pattern.

This is an audit only — no content has been moved. The migration backlog (Batch A–D actions)
will be drafted as a separate follow-on plan once recommendations are reviewed.

## Summary

**Total documents audited:** 43

| Recommendation | Count | Action |
| --- | --- | --- |
| Pattern | 8 | Author a new use case pattern; trim original to a diagram. |
| Duplicate | 9 | Existing pattern covers the scope; simplify blueprint to a diagram and cross-link. |
| Split | 2 | Extract pattern content; reduce original to a diagram; cross-link both. |
| Diagram | 16 | Keep as architecture diagram; trim narrative if needed. |
| Navigation | 8 | Section landing page (overview.md or links-only); revisit after migrations land. |

### Control-group calibration

All 6 `experience-platform/` files scored Pattern=0, Diagram=3 → unanimously **Diagram**.
The rubric is calibrated; results from the other sub-areas can be trusted as scored.

### New use case pattern category: B2B Activation & Marketing

A new category `use-case-patterns/b2b/` (display label **B2B Activation & Marketing**, TOC anchor
proposed `{#b2b-patterns}`) will house all B2B-specific patterns. The label mirrors the existing
"B2B activation & marketing" subsection in the architecture-diagrams area of [TOC.md](../help/blueprints/TOC.md),
giving readers visual symmetry between the two sections.

When fully populated, the category will contain **7 patterns**:

| Origin | Action | Target path |
| --- | --- | --- |
| `use-case-patterns/audience-building-activation/b2b-audience-activation.md` | **Relocate** existing pattern | `use-case-patterns/b2b/account-audience-activation.md` |
| `use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md` | **Relocate** existing pattern | `use-case-patterns/b2b/buying-group-marketing.md` |
| `use-case-patterns/analysis/b2b-analytics.md` | **Relocate** existing pattern | `use-case-patterns/b2b/account-analytics.md` |
| `b2b/b2b-journeys-with-marketo.md` | **Author new** (audit Pattern row) | `use-case-patterns/b2b/marketo-data-journeys.md` |
| `b2b/ajo-b2b-paid-media-controller.md` | **Author new** (audit Pattern row) | `use-case-patterns/b2b/paid-media-orchestration.md` |
| `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | **Author new** | `use-case-patterns/b2b/campaign-intake-and-creation.md` |
| `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | **Author new** | `use-case-patterns/b2b/campaign-review-and-approval.md` |

> **Initial transition state — writer-coordination gate.** The existing "B2B activation & marketing"
> subsection in the architecture-diagrams area of [TOC.md](../help/blueprints/TOC.md) (lines 95–106) **stays intact
> during the transition**. Each blueprint conversion and existing-pattern relocation requires
> sign-off from the owning writer before content is migrated. The new `b2b/` use case pattern
> section coexists with the existing blueprint section while migrations happen page by page, with
> cross-links between them.

When the relocations and new patterns have all landed:

- [TOC.md](../help/blueprints/TOC.md) `Use Case Patterns` section will gain a `B2B Activation & Marketing{#b2b-patterns}`
  subsection (placement TBD with the writer).
- [use-case-patterns/overview.md](../help/blueprints/use-case-patterns/overview.md) will gain a B2B category table.
- The relocated patterns will be removed from `audience-building-activation`,
  `campaign-management-orchestration`, and `analysis` overview tables; their old URLs are kept
  alive via redirects in [migration-redirects.csv](migration-redirects.csv).

### Identified duplicates (9)

The blueprint scope is already covered by an existing use case pattern. Migration action is
**simplify to architecture diagram + cross-link**.

| Blueprint | Existing pattern |
| --- | --- |
| `audience-activation/advertising-activation.md` | `use-case-patterns/audience-building-activation/audience-activation-to-destinations.md` |
| `audience-activation/segment-match.md` | `use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md` |
| `b2b/b2bactivation.md` | `use-case-patterns/audience-building-activation/b2b-audience-activation.md` |
| `b2b/b2b-buying-group-journeys.md` | `use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md` |
| `customer-journey-analytics/b2b-cja.md` | `use-case-patterns/analysis/b2b-analytics.md` |
| `customer-journeys/journey-optimizer/journey-optimizer-journeys.md` | `use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md` |
| `customer-journeys/journey-optimizer/journey-optimizer-campaigns.md` | `use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md` |
| `customer-journeys/decision-management/decision-management-edge.md` | `use-case-patterns/personalization/offer-decisioning.md` |
| `customer-journeys/decision-management/decision-management-hub.md` | `use-case-patterns/personalization/offer-decisioning.md` |

> Note: `decision-management-edge.md` and `decision-management-hub.md` both map to the same
> existing `offer-decisioning.md` pattern. Consider consolidating both blueprints into a single
> deployment-options diagram, or augmenting the existing pattern with edge-vs-hub deployment
> variants. Flag for writer review.

### Patterns to author (8 new + 2 from Splits = 10 total)

| Source blueprint | Proposed category | Proposed pattern title |
| --- | --- | --- |
| `audience-activation/customer-activity.md` | audience-building-activation | Real-Time Profile Lookup for Support and Sales |
| `audience-activation/data-science.md` | audience-building-activation | Data Science Model Ingestion for Profile Enrichment |
| `audience-activation/real-time-lookup.md` | personalization | Edge Profile Access for Web/Mobile Personalization |
| `b2b/b2b-journeys-with-marketo.md` | **b2b** (new) | B2B Account Journeys with Marketo Data Integration |
| `b2b/ajo-b2b-paid-media-controller.md` | **b2b** (new) | B2B Paid Media Orchestration via Waterfall Split-Path Logic |
| `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | **b2b** (new) | Campaign Request Intake & Automated Program Creation |
| `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | **b2b** (new) | Campaign Asset Review & Approval Workflow |
| `customer-journeys/campaign-v8/campaign-v8-overview.md` | campaign-management-orchestration | Campaign v8 Batch Orchestration and Transactional Messaging |
| `audience-activation/rtcdp-target.md` *(Split)* | personalization | Real-time Audience Sharing with Adobe Target |
| `customer-journeys/journey-optimizer/3rd-party-messaging.md` *(Split)* | campaign-management-orchestration | 3rd-party Messaging Integration with Journey Optimizer |

### Proposed new pattern category

- **`b2b/`** (display label **B2B Activation & Marketing**) — see the dedicated section above. The
  Marketo + Workfront patterns (`intake-and-create`, `review-and-approve-blueprint`) are routed
  here rather than to a separate `marketing-resource-management` category, since they represent
  B2B marketing operations in practice. The new category aggregates 7 patterns total: 3 relocated
  from existing categories and 4 newly authored from blueprints.

### Migration redirects

Every URL change introduced by this migration adds a row to the canonical
[`redirects.csv`](../redirects.csv) at repo root (format: `source,dest`). Confirmed
redirects are staged in [migration-redirects.csv](migration-redirects.csv) and merged into the
canonical file as each corresponding move actually happens.

**Confirmed (3 entries, staged):** Existing pattern relocations to `b2b/`. See
[migration-redirects.csv](migration-redirects.csv).

**Pending — added when a blueprint is *deleted* (not when reduced to diagram in place):** if a
Pattern, Split, or Duplicate row's blueprint is later removed entirely, add a redirect from the
blueprint URL to the canonical pattern URL. Default migration approach (simplify-to-diagram)
keeps the blueprint URL alive and **does not require** these redirects. Listed below for
completeness if any blueprint is fully retired:

```
# Pattern blueprints — if deleted, redirect to the new pattern URL
# (slugs are placeholders; finalize when each pattern is authored)
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/customer-activity → use-case-patterns/audience-building-activation/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/data-science → use-case-patterns/audience-building-activation/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/real-time-lookup → use-case-patterns/personalization-patterns/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2b-journeys-with-marketo → use-case-patterns/b2b-patterns/marketo-data-journeys
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/ajo-b2b-paid-media-controller → use-case-patterns/b2b-patterns/paid-media-orchestration
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/marketo-engage-and-workfront-integration-blueprint/intake-and-create → use-case-patterns/b2b-patterns/campaign-intake-and-creation
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint → use-case-patterns/b2b-patterns/campaign-review-and-approval
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/campaign-v8/campaign-v8-overview → use-case-patterns/campaign-orchestration-patterns/<new-pattern-slug>

# Duplicate blueprints — if deleted, redirect to the existing pattern URL
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/advertising-activation → use-case-patterns/audience-building-activation/audience-activation-to-destinations
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/segment-match → use-case-patterns/audience-building-activation/audience-collaboration-segment-match
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2bactivation → use-case-patterns/b2b-patterns/account-audience-activation  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2b-buying-group-journeys → use-case-patterns/b2b-patterns/buying-group-marketing  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journey-analytics/b2b-cja → use-case-patterns/b2b-patterns/account-analytics  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/journey-optimizer/journey-optimizer-journeys → use-case-patterns/campaign-orchestration-patterns/event-triggered-messaging
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/journey-optimizer/journey-optimizer-campaigns → use-case-patterns/campaign-orchestration-patterns/batch-outbound-message-activation
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/decision-management/decision-management-edge → use-case-patterns/personalization-patterns/offer-decisioning
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/decision-management/decision-management-hub → use-case-patterns/personalization-patterns/offer-decisioning

# Optional one-off — if customer-journey-analytics/analysis.md is relocated to experience-platform/
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journey-analytics/analysis → architecture-diagrams/architecture-overview/analysis
```

When converting any of the above to active redirect rows, format as comma-separated `source,dest`
with full `/en/docs/...` paths (no `.html` suffix), matching the existing pattern in
[`redirects.csv`](../redirects.csv).

### Redirect-creation policy (durable rule)

For every migration step, follow these rules:

1. **File moved or renamed** → add redirect from old URL to new URL.
2. **File deleted** (blueprint replaced; no diagram retained) → add redirect from deleted URL to
   canonical replacement URL.
3. **File simplified in place** (URL unchanged) → no redirect.
4. **TOC anchor renamed** (e.g., section heading change) → add redirects for every page under
   that anchor, since the URL changes.

### Open questions for the writer

1. **Decision Management edge vs. hub** — both map to the same existing `offer-decisioning.md`
   pattern. Consolidate to a single diagram with deployment variants, or treat as separate
   diagrams that both cross-link to the same pattern?
2. **Journey Optimizer journeys vs. event-triggered messaging** — agent flagged this duplicate
   classification as uncertain. Verify scope alignment before reducing the blueprint.
3. **`customer-journey-analytics/analysis.md`** — content is actually about Experience Platform
   Query Service, not CJA. Consider relocating to `experience-platform/` folder. (One redirect
   would be added if so — see [migration-redirects.csv](migration-redirects.csv).)
4. **Campaign v7 (deprecated)** — three deprecated v7 files were classified as Diagram /
   Navigation. Confirm whether to migrate at all, leave as-is, or remove from TOC entirely.
5. **`customer-success-stories.md`** — links-only reference page (not an `overview.md`).
   Classified as Navigation. Confirm or reclassify.
6. **B2B section TOC anchor** — proposed `{#b2b-patterns}`. Other patterns subsections use
   `-patterns` suffix (`{#personalization-patterns}`, `{#analysis-patterns}`,
   `{#campaign-orchestration-patterns}`). Confirm or pick another anchor before authoring redirects.
7. **B2B section placement in TOC** — proposed under `+ Use Case Patterns{#use-case-patterns}`.
   Order among siblings (Audience Building & Activation, Personalization, Campaign Management
   & Orchestration, Analysis, B2B Activation & Marketing, Conversational Experience) is the
   writer's call.
8. **Owning-writer coordination** — each blueprint conversion and existing-pattern relocation
   needs writer sign-off before content moves. The audit table is the target state, not a
   sequencing plan; sequencing happens in a follow-on migration plan after coordination.

## Audit table

| path | title | summary | dominant_type | recommendation | proposed_pattern_category | proposed_pattern_title | proposed_diagram_title | duplicate_of | pattern_score | diagram_score | notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| help/blueprints/experience-platform/experience-cloud.md | Adobe Experience Cloud architecture diagrams | Enterprise architecture showing how Experience Cloud applications and services integrate on the AEP foundation. | Diagram | Diagram |  |  | Experience Cloud Architecture Overview |  | 0 | 3 | Override 3 (no business objective). Three complementary diagrams (marketecture, integration, enterprise landscape). Control group: as expected. |
| help/blueprints/experience-platform/platform-applications.md | Adobe Experience Platform and applications architecture diagrams | Architecture diagrams showing how Experience Platform relates to other Experience Cloud applications. | Diagram | Diagram |  |  | AEP and Applications Architecture |  | 0 | 3 | Override 3. Two overview/detailed diagrams; no implementation guidance. Cross-links to integrations-learn docs. Control group: as expected. |
| help/blueprints/experience-platform/platform-data-flow.md | Adobe Experience Platform data flow architecture diagrams | Data flow architecture diagram showing ingestion and egress paths in and out of Experience Platform. | Diagram | Diagram |  |  | AEP Data Flow Architecture |  | 0 | 3 | Override 3. Single data flow diagram with reference to data collection docs. Pure architecture artifact. Control group: as expected. |
| help/blueprints/experience-platform/guardrails.md | Experience Platform and Application Guardrails | System constraints, performance expectations, and latency guardrails for AEP and applications. | Diagram | Diagram |  |  | AEP and Applications Guardrails and Latencies |  | 0 | 3 | Override 3. Latency diagram plus reference tables. Architect-oriented (edge vs hub). Constraints documentation, not how-to. Control group: as expected. |
| help/blueprints/experience-platform/deployment/websdk.md | Experience Platform Web SDK & Edge Network architecture diagram | Web SDK and Edge Network deployment architecture showing data collection flows. | Diagram | Diagram |  |  | Web SDK and Edge Network Deployment |  | 0 | 3 | Override 3. Two diagrams (flow and sequence). References tutorials but no in-document how-to. Architect-focused. Control group: as expected. |
| help/blueprints/experience-platform/deployment/appsdk.md | Application-specific SDK Deployment architecture diagram | Application-specific SDK integration paths and data collection architecture diagram. | Diagram | Diagram |  |  | Application-specific SDK Deployment |  | 0 | 3 | Override 3. Single deployment diagram with minimal narrative. Pure architecture artifact. Control group: as expected. |
| help/blueprints/audience-activation/advertising-activation.md | Audience Activation to Social and Advertising Destinations | Activate audiences to Facebook and Google ad networks via RTCDP with identity configuration and destination setup. | Pattern | Duplicate |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md | 4 | 1 | Existing pattern covers this scope. Duplicate override. Action: simplify to pure diagram and cross-link. |
| help/blueprints/audience-activation/audience-manager.md | Device Based - Anonymous Audience Targeting with Audience Manager | Anonymous audience activation using Audience Manager or RTCDP for device-based targeting across channels. | Diagram | Diagram |  |  | Anonymous Device-Based Audience Targeting |  | 1 | 2 | Minimal narrative. Architecture diagram present, system topology shown. No business objective framing; deployment SDKs and hub/edge concepts. |
| help/blueprints/audience-activation/customer-activity.md | Real-time Profile Access for Support and Sales Scenarios | Enable support and sales agents real-time customer context via profile lookup API. | Pattern | Pattern | audience-building-activation | Real-Time Profile Lookup for Support and Sales |  |  | 3 | 1 | Frames business outcome (agent context). Has prerequisites checklist; implementation steps >30 lines. Unique use case: hub profile access (not edge personalization). Distinct from existing personalization patterns. |
| help/blueprints/audience-activation/data-science.md | Custom Data Science for Profile Enrichment Blueprint | Ingest machine learning model scores into RTCDP to enrich profiles for personalization and segmentation. | Pattern | Pattern | audience-building-activation | Data Science Model Ingestion for Profile Enrichment |  |  | 3 | 1 | Frames business outcome (enrichment for personalization). Has use cases and considerations; implementation considerations >30 lines. Focus on data science workflows, not messaging/activation. |
| help/blueprints/audience-activation/enterprise-destinations.md | Audience and Profile Activation to Enterprise Destinations | Stream or batch profile and audience changes to cloud storage and enterprise apps for sales, support, analytics. | Diagram | Diagram |  |  | Enterprise Audience and Profile Activation |  | 1 | 2 | No business objective framing. Sparse implementation guidance. Architecture diagram + system topology for cloud storage/enterprise apps. Visual-dominant. |
| help/blueprints/audience-activation/real-time-lookup.md | Real-time Edge Profile Access for Web and Mobile Personalization | Access unified profile at the edge in milliseconds for real-time web and mobile personalization. | Pattern | Pattern | personalization | Edge Profile Access for Web/Mobile Personalization |  |  | 5 | 2 | Strong business framing (low-latency personalization). Two implementation patterns (Web SDK vs. Edge API). Extensive prerequisites and steps (>30 lines). KPIs implied (latency, throughput). |
| help/blueprints/audience-activation/rtcdp-target.md | Known Customer Personalization with Target | Share RTCDP audiences and profiles with Adobe Target for known-visitor web and mobile personalization. | Mixed | Split | personalization | Real-time Audience Sharing with Adobe Target | Target Integration Architecture | help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md | 3 | 2 | Overlaps with existing known-visitor pattern but narrower scope (Target only). Three integration patterns. Architecture diagrams + edge deployment considered. Pattern content + diagram both substantial → Split. |
| help/blueprints/audience-activation/segment-match.md | Audience Collaboration with Segment Match | Enable secure partner audience collaboration via Segment Match with privacy controls. | Pattern | Duplicate |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md | 4 | 1 | Existing pattern covers this exactly. Duplicate override. Unique content to preserve in diagram: detailed RBAC/consent/governance config and programmatic ad workflow. |
| help/blueprints/b2b/overview.md | B2B Analytics, Activation, and Marketing blueprints | Navigation page listing B2B analytics, audience activation, buying group, Marketo, and Workfront blueprints. | Navigation | Navigation |  |  |  |  |  |  | Override 1: file named overview.md. Excluded from migration. |
| help/blueprints/b2b/b2bactivation.md | B2B Audience and Profile Activation blueprint | Activate account-based B2B audiences across web, email, and advertising channels using account and profile data. | Pattern | Duplicate |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md | 3 | 1 | Override 2: equivalent pattern exists. Blueprint is narrower architecture-focused subset. |
| help/blueprints/b2b/b2b-account-activation.md | B2B Account Activation to Advertising Destinations and File Destinations | Target B2B accounts via LinkedIn and cloud storage destinations using account audience creation and activation. | Diagram | Diagram |  |  | B2B Account Audience Activation |  | 1 | 2 | Minimal business framing, no KPIs, minimal narrative. Architecture diagram present; LinkedIn/cloud-storage topology described. Keep as diagram. |
| help/blueprints/b2b/b2b-buying-group-journeys.md | Buying Group-based Marketing and Journey Management Blueprint | Design account journeys that qualify leads into buying groups with defined roles and solution interests. | Pattern | Duplicate |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md | 5 | 2 | Override 2: equivalent pattern exists. Blueprint has rich pattern content but the existing pattern is more comprehensive. |
| help/blueprints/b2b/b2b-journeys-with-marketo.md | B2B Journeys using Marketo Data blueprint | Deploy Journey Optimizer B2B Edition with Marketo data for orchestrating buying group journeys and account engagement. | Pattern | Pattern | b2b | B2B Account Journeys with Marketo Data Integration |  |  | 4 | 1 | Strong business framing. KPIs listed; multiple implementation options; extensive considerations (>30 lines). Differentiated from existing pattern by Marketo data integration depth (XDM config, identity stitching, field blocking). Routes to new b2b/ category. |
| help/blueprints/b2b/ajo-b2b-paid-media-controller.md | AJO B2B - Account Journey Orchestration - Paid Media Controller | Orchestrate B2B paid media campaigns using waterfall logic to assign accounts to campaigns and activate to destinations. | Pattern | Pattern | b2b | B2B Paid Media Orchestration via Waterfall Split-Path Logic |  |  | 4 | 2 | Strong business framing. Explicit KPIs; multiple implementation options; prerequisites; >30 lines narrative. Distinct from existing buying-group pattern (focuses on paid media prioritization, not nurture). Routes to new b2b/ category. |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md | Marketo Engage and Workfront integration blueprint overview | Overview of campaign planning to execution automation using Marketo Engage and Workfront with Fusion. | Navigation | Navigation |  |  |  |  |  |  | Override 1: file named overview.md. Excluded from migration. |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md | Intake and Create blueprint | Automate B2B marketing campaign request intake to creation using Workfront forms and Marketo Engage program templating. | Pattern | Pattern | b2b | Campaign Request Intake & Automated Program Creation |  |  | 4 | 1 | Strong business framing on campaign velocity. Implicit KPIs (errors/rework reduction); workflow steps >30 lines; readiness checklist. Routes to new b2b/ category (Marketo+Workfront ops are predominantly B2B). |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md | Review and approve blueprint | Integrate Workfront proofing and approval workflows with Marketo Engage email assets using Fusion automation. | Pattern | Pattern | b2b | Campaign Asset Review & Approval Workflow |  |  | 3 | 2 | Strong business framing on compliance and accuracy; implicit KPIs (approval velocity); narrative >30 lines; workflow planning section. Routes to new b2b/ category. |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md | Customer success stories | Links to customer case studies and webinars showcasing Marketo and Workfront integration outcomes. | Navigation | Navigation |  |  |  |  |  |  | Minimal content (6 hyperlinks). No business framing, KPIs, architecture, or narrative. Treated as Navigation. Writer should confirm. |
| help/blueprints/customer-journey-analytics/overview.md | Customer Journey Analytics blueprints | Unify and analyze customer data and behavior from various channels to create journey-based views. | Navigation | Navigation |  |  |  |  |  |  | Override 1: overview.md. TOC-style landing page. Excluded from migration. |
| help/blueprints/customer-journey-analytics/b2b-cja.md | B2B Customer Journey Analytics blueprint | Account-based CJA reporting and analysis for B2B organizations using account as primary data model. | Pattern | Duplicate |  |  |  | help/blueprints/use-case-patterns/analysis/b2b-analytics.md | 4 | 2 | Override 2: equivalent pattern covers B2B account-level analytics with CJA B2B Edition. Action: simplify to diagram, cross-link. |
| help/blueprints/customer-journey-analytics/cja-rtcdp.md | Customer Journey Analytics with Real-time Customer Data Platform blueprint | Create and publish audiences from CJA to RTCDP for targeting and personalization. | Diagram | Diagram |  |  | CJA-to-RTCDP audience publishing integration |  | 1 | 3 | Strong architecture focus (system-to-system integration, deployment shape). Minimal narrative. Unique content: CJA audience publishing latency guardrails. |
| help/blueprints/customer-journey-analytics/cja-ajo.md | Customer Journey Analytics with Journey Optimizer blueprint | Analyze AJO delivery and interaction data in CJA; publish CJA audiences to AJO. | Diagram | Diagram |  |  | CJA-to-AJO integration and analysis |  | 1 | 3 | Strong architecture focus. Minimal narrative. Unique content: bidirectional CJA-AJO data sharing pattern. |
| help/blueprints/customer-journey-analytics/analysis.md | Data Analysis and Intelligence Blueprint | Use Experience Platform Query Service for exploratory analysis of data lake data. | Diagram | Diagram |  |  | Experience Platform Query Service and BI tool integration |  | 1 | 3 | Covers Query Service, NOT CJA-specific. May be misplaced in CJA folder; consider relocating to experience-platform/. Strong architect audience (PostgreSQL, BI tooling). |
| help/blueprints/customer-journeys/overview.md | Customer Journey blueprints | Modern marketing platforms supporting event-driven journeys and brand-initiated campaigns across channels. | Navigation | Navigation |  |  |  |  |  |  | Override 1: overview.md. TOC for journey subcategories; describes Journey Optimizer and Campaign positioning. |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md | Journey Optimizer Blueprints | Event-driven 1:1 profile orchestration and audience-based brand communications across channels. | Navigation | Navigation |  |  |  |  |  |  | Override 1: overview.md. Landing page with use case tabs and integration patterns. |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-journeys.md | Journey Optimizer - Triggered Messaging and Adobe Experience Platform Blueprint | Real-time event-driven workflows delivering personalized multi-step experiences based on customer behaviors. | Pattern | Duplicate |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md | 4 | 2 | Override 2 with caveat: agent flagged as likely duplicate but uncertain. Verify scope alignment before reducing. Architecture considerations may be unique (profile freshness, segment qualification timing) and worth preserving in diagram. |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-campaigns.md | Journey Optimizer - Campaign Orchestration | Scheduled audience-based multi-step communications across outbound channels: email, SMS, push, direct mail. | Pattern | Duplicate |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md | 3 | 2 | Override 2: equivalent pattern. Multiple architecture diagrams; preserve as diagram. Unique content: relational database/audience portal/skinny profile architecture details. |
| help/blueprints/customer-journeys/journey-optimizer/3rd-party-messaging.md | Journey Optimizer - 3rd-party Messaging blueprint | Demonstrates Journey Optimizer integration with third-party messaging systems for orchestrated communications. | Mixed | Split | campaign-management-orchestration | 3rd-party Messaging Integration with Journey Optimizer | 3rd-party messaging architecture |  | 2 | 2 | Tied scores → Split. Diagram (system-to-system topology) plus pattern content (implementation steps, integration constraints: bearer auth, no static IPs, rate limits). Worth preserving both. |
| help/blueprints/customer-journeys/decision-management/decision-management-overview.md | Decision Management blueprints | Deliver personalized offers across customer journeys via centralized offer library and decision engine. | Navigation | Navigation |  |  |  |  |  |  | Override 1: overview.md. Describes Decision Management components and edge vs. hub deployment approaches. |
| help/blueprints/customer-journeys/decision-management/decision-management-edge.md | Decision Management on the Edge blueprint | Deliver personalized offers in real-time web and mobile experiences with sub-second latency on the edge network. | Mixed | Duplicate |  |  |  | help/blueprints/use-case-patterns/personalization/offer-decisioning.md | 2 | 3 | Override 2: maps to offer-decisioning. Edge deployment variant — consider consolidating with hub blueprint into a single deployment-options diagram. |
| help/blueprints/customer-journeys/decision-management/decision-management-hub.md | Decision Management on the Hub blueprint | Deliver personalized offers across channels including kiosks, agent-assisted experiences, and outbound deliveries. | Mixed | Duplicate |  |  |  | help/blueprints/use-case-patterns/personalization/offer-decisioning.md | 2 | 3 | Override 2: maps to offer-decisioning. Hub deployment variant — consider consolidating with edge blueprint into a single deployment-options diagram. |
| help/blueprints/customer-journeys/campaign-v8/campaign-v8-overview.md | Campaign v8 Blueprint, Campaign & Platform | Next-generation batch campaign management platform with ETL, segmentation, and transactional messaging capabilities. | Pattern | Pattern | campaign-management-orchestration | Campaign v8 Batch Orchestration and Transactional Messaging | Campaign v8 architecture deployment models |  | 4 | 3 | Distinct technical approach (Campaign v8 native, not AJO). Multiple architecture diagrams; business framing; KPIs implicit in guardrails (20M msg/hr batch, 1M/hr real-time). No equivalent in existing pattern catalog. Note: scores qualify as Split too — propose Pattern but writer may want diagram retained. |
| help/blueprints/customer-journeys/campaign-v8/rtcdp-and-campaign-v8.md | Real-Time CDP with Adobe Campaign v8 integration pattern | Showcases RTCDP audience and profile integration with Campaign v8 for personalized conversations. | Diagram | Diagram |  |  | RTCDP - Campaign v8 audience and profile exchange |  | 1 | 2 | Integration connector blueprint, not standalone use case. Diagram + brief prerequisites/guardrails. Architect-oriented. |
| help/blueprints/customer-journeys/campaign-v8/ajo-and-campaign-v8.md | Journey Optimizer with Adobe Campaign v8 blueprint | Demonstrates AJO orchestration with Campaign v8 transactional messaging for 1:1 experiences. | Diagram | Diagram |  |  | Journey Optimizer - Campaign v8 transactional messaging integration |  | 1 | 2 | Integration connector. Diagram + implementation steps + technical constraints (4,000 msg/5min throttle, event-initiated only). Cross-link to AJO and Campaign v8 patterns. |
| help/blueprints/customer-journeys/campaign-v7/campaign-v7-overview.md | Campaign v7 blueprint | Deprecated: batch-based messaging, onboarding, re-marketing, direct mail, simple transactional messaging. | Navigation | Navigation |  |  |  |  |  |  | DEPRECATED PRODUCT (frontmatter links to v8). Minimal content (architecture diagram only). Do not migrate. |
| help/blueprints/customer-journeys/campaign-v7/rtcdp-and-campaign-v7.md | Real-Time CDP with Campaign v7 and Campaign Standard integration pattern | Showcases RTCDP and Real-Time Customer Profile integration with Campaign v7/Standard for personalized conversations. | Diagram | Diagram |  |  | RTCDP - Campaign v7/Standard audience and profile exchange |  | 1 | 2 | DEPRECATED. Integration connector. Diagram + comprehensive implementation steps. Do not migrate to new pattern; leave as-is. |
| help/blueprints/customer-journeys/campaign-v7/ajo-and-campaign-v7.md | Journey Optimizer with Adobe Campaign v7 blueprint | Demonstrates AJO orchestration with Campaign v7 transactional messaging for 1:1 experiences. | Diagram | Diagram |  |  | Journey Optimizer - Campaign v7 transactional messaging integration |  | 1 | 2 | DEPRECATED. Integration connector. Diagram + implementation steps + constraints. Do not migrate; leave as-is. |
