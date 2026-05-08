# Pages to Update When Adding a Use Case Pattern

When a new use case pattern is created, the following pages must be updated to ensure the pattern is discoverable and correctly linked.

## Required Updates

### 1. TOC.md
- **File:** `/help/blueprints/TOC.md`
- **Action:** Add a new entry under the correct category section
- **Format:** `    + [{{Pattern Title}}](/help/blueprints/use-case-patterns/{{category}}/{{filename}}.md)`
- **Location by category:**
  - Audience Building & Activation: after line ~47 (after existing entries in that section)
  - Personalization: after line ~52
  - Campaign Management & Orchestration: after line ~58
  - Analysis: after line ~61
  - Conversational Experience: after line ~63

#### Category-to-TOC mapping

| Category slug | TOC section heading | Anchor |
| --- | --- | --- |
| `audience-building-activation` | `+ Audience Building & Activation` | `{#audience-building-activation}` |
| `personalization` | `+ Personalization` | `{#personalization-patterns}` |
| `campaign-management-orchestration` | `+ Campaign Management & Orchestration` | `{#campaign-orchestration-patterns}` |
| `analysis` | `+ Analysis` | `{#analysis-patterns}` |
| `conversational-experience` | `+ Conversational Experience` | `{#conversational-experience-patterns}` |

#### Indentation rules

- Category headings use two spaces + `+` (e.g., `  + Personalization{#personalization-patterns}`)
- Pattern entries use four spaces + `+` (e.g., `    + [Pattern Title](path)`)

### 2. Use Case Patterns Overview
- **File:** `/help/blueprints/use-case-patterns/overview.md`
- **Action:** Add a new row to the correct category table
- **Format:** `| [{{Pattern Title}}]({{category}}/{{filename}}.md) | {{Primary capability description}} | [!DNL {{Solution1}}], [!DNL {{Solution2}}] |`
- **Categories in overview:**
  - Audience building & activation (line ~18)
  - Personalization (line ~29)
  - Campaign management & orchestration (line ~40)
  - Analysis (line ~52)
  - Conversational experience (line ~61)

#### Row format example

```
| [Event-Triggered Messaging](campaign-management-orchestration/event-triggered-messaging.md) | Listen for a real-time behavioral or system event, then deliver a contextual message to the triggering profile | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
```

## Validation Checklist

- [ ] Pattern markdown file created in correct category directory
- [ ] Frontmatter includes title, description, solution, and exl-id
- [ ] TOC.md entry added under correct category
- [ ] Overview.md table row added under correct category
- [ ] All business objective links point to existing files
- [ ] File uses kebab-case naming convention
- [ ] All Experience League links are valid URLs
- [ ] Adobe product names use `[!DNL ...]` syntax
- [ ] Function chain uses ` > ` separator format
- [ ] Pattern file includes all required sections (see pattern-template.md)
