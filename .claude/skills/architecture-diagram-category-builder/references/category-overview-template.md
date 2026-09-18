# Category overview.md template

Every category folder under `help/blueprints/architecture-diagrams/` needs an `overview.md` that looks like the other five. Use this exact structure.

## Frontmatter

```yaml
---
title: {Category Label}
description: {One-sentence summary of what this category covers.}
solution: {Primary Adobe solution(s), comma-separated}
doc-type: overview-page
---
```

Do not include `exl-id`, `product_v2`, `feature_v2`, `role_v2`, `topic_v2`, `TQID`, `kt`, or `thumbnail` on a new page -- the publishing pipeline auto-populates these.

## Body

```markdown
# {Category Label}

{1-3 paragraph intro describing what this category of diagrams covers and why it matters.}

| Diagram | Description |
| --- | --- |
| [{Page title}]({filename}.md) | {One-sentence description of the page} |
| [{Page title}]({filename}.md) | {One-sentence description of the page} |
```

Rules:

- List every page in the category, in the same order they appear in TOC.md.
- Link targets are relative filenames (no `/help/blueprints/...` prefix), since the overview lives alongside its sibling pages.
- Descriptions are one sentence, no trailing period required if it reads like a label.
- If a category has a natural sub-grouping (e.g. "Deprecated diagrams" under Customer journeys), add a `## {Sub-group name}` heading followed by its own two-column table in the same format -- do not mix diagram thumbnails or extra columns into the table.
- Do not embed `<img>` diagram thumbnails in this table. Keep it to two columns: `Diagram` (link) and `Description` (text). Thumbnails belong on the individual content pages, not the category overview.
- Do not use nested `<ul><li>` HTML inside table cells. Plain text only.

## Example (Customer Insights)

```markdown
---
title: Customer Insights
description: Unify and analyze data and customer behaviors from across the customer journey
solution: Customer Journey Analytics
doc-type: overview-page
---
# Customer Insights

Customer Journey Analytics shows how brands can unify customer data and behavior from various interaction channels and sources to create a journey-based view of all customer interactions.

| Diagram | Description |
| --- | --- |
| [Adobe Customer Journey Analytics](cja.md) | Core Customer Journey Analytics architecture, including B2B and audience-sharing derivations |
| [Adobe Customer Journey Analytics & Adobe Journey Optimizer integration](cja-ajo-integration.md) | Campaign and journey insights integration between Customer Journey Analytics and Journey Optimizer |
```
