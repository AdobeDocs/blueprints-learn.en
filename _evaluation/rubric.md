# Blueprint Evaluation Rubric

This rubric is applied to every document under the "Architecture Diagrams and Blueprints" section
of [TOC.md](../TOC.md) (lines 76–133) to recommend whether each blueprint should become a
**Use Case Pattern**, an **Architecture Diagram**, both (**Split**), or be flagged as a
**Duplicate** of an existing pattern.

The output of applying this rubric is [blueprint-audit.md](blueprint-audit.md).

## Definitions

- **Use Case Pattern** — a document describing a specific business or technical objective and
  outlining possible implementation approaches and considerations to achieve that objective.
  Canonical shape: `.claude/skills/use-case-pattern-builder/references/pattern-template.md`.
- **Architecture Diagram** — a visual diagram representing the functionality of a system, the
  integrations, and data flows. Minimal narrative; the diagram is the artifact.
  Canonical example: [platform-data-flow.md](../experience-platform/platform-data-flow.md).

## Scoring

Each blueprint is read end-to-end and scored against eight binary signals. Each signal contributes
+1 to either the Pattern score or the Diagram score.

### Pattern signals (each = +1 Pattern)

1. **Business objective framing** — frames revenue, retention, acquisition, lead generation, cost
   reduction, customer experience, or similar business outcome.
2. **KPIs or success metrics** — explicitly names metrics, conversion rates, match rates, ROI, or
   similar outcome measures.
3. **Multiple implementation options or maturity tiers** — presents Option A / Option B, basic vs.
   advanced, or comparable alternatives the reader chooses between.
4. **Prerequisites or readiness checklist** — lists what must be in place before implementing.
5. **Narrative implementation steps > ~30 lines** — substantive how-to-implement guidance, not
   just a brief overview.

### Diagram signals (each = +1 Diagram)

6. **Architecture/data-flow image present** — `.svg`, `.png`, or `.jpg` showing system topology,
   data flow, or integration arrows.
7. **System-to-system integration topology, deployment shape, or guardrails** — describes how
   components connect, where data lives, deployment models (edge vs. hub), or capacity limits.
8. **Audience is solution architects** — framing uses deployment, SDK, edge, hub, or similar
   architect-oriented terminology rather than marketer-oriented framing (campaigns, journeys,
   audiences).

## Recommendation logic

Apply override rules first. If no override fires, derive the recommendation from the scores.

### Override rules (highest priority)

1. **File is named `overview.md`** → recommendation = `Navigation`. Excluded from migration; the
   page is a TOC-style landing page that will be revised after child files settle.
2. **An equivalent pattern already exists in `help/blueprints/use-case-patterns/`** →
   recommendation = `Duplicate`. The migration action is to simplify the blueprint to a pure
   architecture diagram and add a "See use case pattern" cross-link to the existing pattern.
   Record the existing pattern path in the `duplicate_of` column.
3. **File is in `experience-platform/` and has no business objective signal (#1)** → default to
   `Diagram` regardless of other scores. This folder is the architecture-overview tier.

### Score-based recommendation (when no override fires)

| Pattern score | Diagram score | Recommendation | Reasoning |
| --- | --- | --- | --- |
| ≥ 3 | ≤ 1 | `Pattern` | Strong pattern signals, weak diagram signals → migrate to pattern. |
| ≤ 1 | ≥ 2 | `Diagram` | Weak pattern signals, dominant visual/topology focus → keep as diagram. |
| ≥ 3 | ≥ 2 | `Split` | Both rich pattern content and a meaningful diagram → extract pattern, reduce original to diagram, cross-link. |
| 2 | 2 | `Split` | Tie at moderate strength → split. |
| 2 | ≤ 1 | `Pattern` | Pattern leaning, no significant diagram value. |
| ≤ 1 | ≤ 1 | `Diagram` | Thin overall — likely an existing minimal architecture page. |

## How to apply the rubric

For each blueprint markdown file in scope:

1. Read the full file end-to-end.
2. Mark each of the eight signals present/absent.
3. Apply override rules in order. If one fires, that is the recommendation.
4. Otherwise, compute Pattern score and Diagram score and look up the recommendation.
5. For `Pattern` and `Split` recommendations, propose:
   - `proposed_pattern_category` — one of:
     `audience-building-activation`, `personalization`, `campaign-management-orchestration`,
     `analysis`, `conversational-experience`, or a new category labeled `(new) <name>`.
   - `proposed_pattern_title` — a short, action-oriented title following the existing pattern
     naming style.
6. For `Diagram` and `Split` recommendations, propose:
   - `proposed_diagram_title` — typically the existing title trimmed of business framing.
7. Capture any duplicates found by comparing the blueprint's scope to the existing pattern catalog
   in `duplicate_of`.
8. Record open questions, unique technical content worth preserving, or migration risk in `notes`.

## Existing use case pattern catalog (for duplicate detection)

| Category | Patterns |
| --- | --- |
| audience-building-activation | audience-activation-to-destinations, audience-collaboration-segment-match, b2b-audience-activation, event-forwarding |
| personalization | anonymous-visitor-web-personalization, known-visitor-web-app-personalization, offer-decisioning, behavioral-recommendation |
| campaign-management-orchestration | batch-outbound-message-activation, event-triggered-messaging, multi-step-orchestrated-journey, cross-channel-journey-with-decisioning, buying-group-based-marketing |
| analysis | customer-analytics-insight-generation, b2b-analytics |
| conversational-experience | brand-concierge-conversational-experience |
