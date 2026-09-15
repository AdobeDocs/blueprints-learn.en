# Use Case Pattern Template

This file contains the complete markdown template for a use case pattern page. Replace all `{{placeholder}}` values with actual content when generating a new pattern.

---

## Template

````markdown
---
title: {{Pattern Title}}
description: {{One-sentence description of what this pattern teaches}}
solution: {{Comma-separated Adobe solutions}}
exl-id: {{generate-uuid-placeholder}}
---
# {{Pattern title}}

This guide provides an overview of {{pattern name}} using {{solutions with [!DNL ...] formatting}}. It is designed for solution architects, marketing technologists, and implementation engineers who need to {{primary capability description}}.

## Use case pattern

**{{Pattern Name}}**

{{One-two sentence description of what the pattern does and enables.}}

**Execution plan:** {{Step 1}} > {{Step 2}} > {{Step 3}} > {{Step 4}} > {{Step 5}}

## Use case overview

{{Paragraph 1: Define the pattern. What does it do? How does it differ from related patterns? Provide a clear, specific definition.}}

{{Paragraph 2: Describe the typical trigger or starting condition. When does this pattern apply? What event, schedule, or condition initiates it?}}

{{Paragraph 3: Describe what the pattern delivers. What is the end result for the customer or business? What channels or touchpoints does it affect?}}

{{Paragraph 4: Clarify scope boundaries. What does this pattern NOT cover? What adjacent patterns handle those needs? Reference other patterns by name if relevant.}}

{{Paragraph 5 (optional): Identify typical stakeholders and teams involved in implementation. Who owns what?}}

## Key business objectives

The following business objectives are supported by this use case pattern.

**[{{Objective Name}}](../../business-objectives/{{category}}/{{objective-file}}.md)**

{{Brief description of how this pattern supports the objective -- 1-2 sentences.}}

| KPIs |
| --- |
| {{KPI1}}, {{KPI2}}, {{KPI3}} |

{{Repeat the above block for each supported business objective.}}

## Example tactical use cases

The following scenarios illustrate how {{pattern name}} can be applied across different business contexts.

- **{{Scenario name}}** -- {{Description of the scenario and how it uses this pattern}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
{{Include 6-10 scenarios total}}

## Key performance indicators

| KPI | Description | Measurement |
| --- | --- | --- |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |

## Applications

The following Adobe applications are used in this use case pattern.

- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}
- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}
- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}

## Related documentation

The following resources provide additional detail on the capabilities used in this pattern. Group the reference links to primary Experience League documents under descriptive subheadings.

### {{Topic group}}

- [{{Link text}}]({{URL}})
- [{{Link text}}]({{URL}})

### {{Topic group}}

- [{{Link text}}]({{URL}})
- [{{Link text}}]({{URL}})
````

---

## Notes on using this template

- **YAML frontmatter:** The `exl-id` should be a placeholder UUID (e.g., `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`). The publishing pipeline assigns the real value.
- **Section order:** The `Use case pattern` section comes immediately after the opening introduction, before `Use case overview`. It gives readers a crisp, one-line definition and the high-level execution plan up front.
- **Adobe product names:** Always use `[!DNL ...]` syntax for Adobe product names in body text and tables (e.g., `[!DNL Journey Optimizer]`). This is an Experience League convention that prevents translation of product names.
- **Business objective links:** Use relative paths from the pattern file to the business objectives directory: `../../business-objectives/{{category}}/{{filename}}.md`.
- **Kebab-case filenames:** The pattern filename must be kebab-case derived from the pattern title. Example: "Event-Triggered Messaging" becomes `event-triggered-messaging.md`.
- **Execution plan:** Use ` > ` (space, greater-than, space) as the separator between steps. Keep the label exactly `**Execution plan:**`.
- **Related documentation:** Group reference links under descriptive `###` subheadings (e.g., by application or capability area). These are the Experience League references for the applications and capabilities used in the pattern.
- **Architecture (optional):** If a pattern benefits from a reference architecture diagram, an optional `## Architecture` section may be placed between `Applications` and `Related documentation`.
- **Scope:** This template intentionally excludes detailed implementation sections (foundational/supporting/application capabilities, prerequisites, implementation options, and phased implementation steps). Those details live in Experience League documentation linked from `Related documentation`.