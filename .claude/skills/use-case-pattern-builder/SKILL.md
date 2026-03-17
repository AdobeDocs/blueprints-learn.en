---
name: use-case-pattern-builder
description: Guide creation of new use case pattern content for the Adobe Experience Platform blueprints repository. Use this skill when adding a new use case pattern, creating implementation guidance content, or when the user mentions adding patterns to the blueprints site. Handles the full workflow: gathering pattern information, generating the markdown file with correct template structure, and updating all cross-reference pages (TOC.md, overview.md).
---

# Use Case Pattern Builder

This skill guides the creation of a new use case pattern for the Adobe Experience Platform blueprints repository. It handles the full workflow: gathering pattern information from the user, generating the markdown content file with the correct template structure, and updating all cross-reference pages so the new pattern is discoverable.

Before starting, read the following reference files for the complete template structure and the checklist of pages to update:

- `references/pattern-template.md` -- the full markdown template with placeholder values
- `references/pages-to-update.md` -- the checklist of pages that must be updated when adding a pattern

## Phase 1: Information Gathering

Interview the user to collect all required information before generating any files. Ask for the following, and do not proceed to content generation until every item is provided or explicitly deferred.

### Required information

1. **Pattern name** -- The human-readable title (e.g., "Event-Triggered Messaging").

2. **Category** -- Exactly one of the following:
   - `audience-building-activation`
   - `personalization`
   - `campaign-management-orchestration`
   - `analysis`
   - `conversational-experience`

3. **Primary capability description** -- A single sentence describing what this pattern does (used in the overview table and frontmatter description).

4. **Core Adobe solutions** -- The Adobe products central to this pattern. Choose from: Journey Optimizer, Real-Time Customer Data Platform, Experience Platform, Customer Journey Analytics, Brand Concierge, Journey Optimizer B2B Edition, Real-Time CDP B2B Edition, or others as appropriate.

5. **Function chain steps** -- 3-6 sequential phases that describe the pattern's execution flow, separated by `>`. Example: "Event Ingestion > Journey Entry > Condition Evaluation > Message Delivery > Reporting".

6. **Business objectives supported** -- One or more business objectives from the existing set under `/help/blueprints/business-objectives/`. Each should include the objective name, the category subfolder, and the filename. Verify that the referenced files exist before generating content.

7. **Example tactical use cases** -- 6-10 bulleted scenarios describing how this pattern can be applied across different business contexts. Each should have a bold scenario name followed by a description.

8. **KPIs** -- A table with three columns: KPI (name), Description (what it measures), Measurement (formula or approach).

9. **Implementation options** -- 2-4 implementation options. For each option, collect:
   - Option name
   - Best for (when to use this option)
   - How it works (2-4 paragraphs)
   - Key considerations (bulleted list)
   - Advantages (bulleted list)
   - Limitations (bulleted list)
   - Experience League links (URLs to relevant documentation)

### Optional but recommended

- Use case overview paragraphs (3-5 paragraphs; if not provided, draft them from the other information)
- Applications list with descriptions of each Adobe app's role
- Foundational functions table (Function, Status, What Must Be in Place, Experience League Reference)
- Supporting functions table (Function, Status, Why It Matters, Experience League Reference)
- Application functions tables (one per application, with Function, Implementation Phase, Description)
- Prerequisites checklist

If the user does not provide the optional items, generate reasonable defaults based on the pattern category, solutions, and function chain.

## Phase 2: Content Generation

Generate the pattern markdown file at the following path:

```
/help/blueprints/use-case-patterns/{category}/{kebab-case-pattern-name}.md
```

The filename must use kebab-case derived from the pattern name. For example, "Event-Triggered Messaging" becomes `event-triggered-messaging.md`.

Use the template from `references/pattern-template.md` and fill in all placeholder values with the collected information. The generated file must include every section in the template:

1. **YAML frontmatter** -- title, description, solution (comma-separated), exl-id (generate a UUID placeholder like `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx` -- the publishing team will assign the real one).

2. **Opening section** -- `# {Pattern name}` heading followed by an introductory paragraph and the "Use this guide to understand..." sentence.

3. **Use case overview** -- 3-5 paragraphs describing the pattern scope, when it applies, what it does and does not do, and who the typical stakeholders are.

4. **Key business objectives** -- Each objective as a linked heading with a brief description and a KPIs summary row.

5. **Example tactical use cases** -- Bulleted list of 6-10 scenarios.

6. **Key performance indicators** -- Table with KPI, Description, Measurement columns.

7. **Use case pattern** -- Description paragraph and the function chain.

8. **Applications** -- List of Adobe applications with `[!DNL ...]` formatting and descriptions.

9. **Foundational functions** -- Table with columns: Foundational Function, Status, What Must Be in Place, Experience League Reference. Status values: Required, Assumed in Place, Not Applicable.

10. **Supporting functions** -- Table with columns: Supporting Function, Status, Why It Matters, Experience League Reference. Status values: Recommended, Included, Not Applicable.

11. **Application functions** -- One table per application with columns: Function, Implementation Phase, Description.

12. **Prerequisites** -- Checklist using `- [ ]` syntax.

13. **Implementation options** -- 2-4 detailed options, each with Best for, How it works, Key considerations, Advantages, Limitations, and Experience League links.

14. **Option comparison** -- Summary comparison table at the end.

## Phase 3: Cross-Reference Updates

After generating the pattern file, update the following files. Read `references/pages-to-update.md` for the detailed checklist.

### TOC.md

**File:** `/help/blueprints/TOC.md`

Add a new entry under the correct category section. The categories map to these TOC sections:

| Category slug | TOC section heading |
| --- | --- |
| `audience-building-activation` | `+ Audience Building & Activation{#audience-building-activation}` |
| `personalization` | `+ Personalization{#personalization-patterns}` |
| `campaign-management-orchestration` | `+ Campaign Management & Orchestration{#campaign-orchestration-patterns}` |
| `analysis` | `+ Analysis{#analysis-patterns}` |
| `conversational-experience` | `+ Conversational Experience{#conversational-experience-patterns}` |

The entry format is:

```
    + [{{Pattern Title}}](/help/blueprints/use-case-patterns/{{category}}/{{filename}}.md)
```

Add the new entry after the last existing entry in the matching section. Preserve the exact indentation (four spaces before the `+`).

### Overview page

**File:** `/help/blueprints/use-case-patterns/overview.md`

Add a new row to the correct category table. The format is:

```
| [{{Pattern Title}}]({{category}}/{{filename}}.md) | {{Primary capability description}} | [!DNL {{Solution1}}], [!DNL {{Solution2}}] |
```

Add the new row after the last existing row in the matching category table.

## Phase 4: Validation

After all files are created and updated, verify the following:

1. **Business objective links** -- Every business objective link in the pattern file points to an existing file under `/help/blueprints/business-objectives/`. Use glob or read to confirm each target file exists.

2. **TOC entry placement** -- The new TOC entry is inside the correct category section and uses the correct indentation and path format.

3. **Overview table row** -- The new overview row is in the correct category table and follows the same column format as existing rows.

4. **File naming** -- The pattern filename uses kebab-case and matches the path referenced in both TOC.md and overview.md.

5. **Frontmatter completeness** -- The pattern file includes title, description, solution, and exl-id in its YAML frontmatter.

6. **Experience League links** -- Spot-check that any Experience League URLs are plausible (start with `https://experienceleague.adobe.com/`).

Report any validation failures to the user and fix them before considering the task complete.

## Notes

- Always use `[!DNL ...]` syntax for Adobe product names in tables and body text, following the convention of existing pattern files.
- The `exl-id` in frontmatter should be a placeholder UUID. The publishing pipeline assigns the real value.
- If the user wants to create multiple patterns at once, repeat Phases 2-4 for each pattern but gather all information in Phase 1.
- If a new category is needed that does not exist in the list above, warn the user that TOC.md and overview.md will need new sections created, and handle that as a separate step.
