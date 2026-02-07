---
name: blueprint-document-reference
description: Reference for creating and editing Adobe Digital Experience Blueprint documents. Use when creating new blueprints, adding blueprint pages, or when the user asks about blueprint structure, sections, templates, or referencing Adobe Experience League.
---

# Blueprint Document Reference

Use this skill when creating or editing blueprint documents in this repository. Blueprints are repeatable implementations that address established business problems and include architecture diagrams, technical considerations, and links to Adobe Experience League documentation.

## When to Apply

- Creating a new blueprint document or blueprint overview page
- Adding or restructuring sections in an existing blueprint
- Linking to or citing Adobe Experience League documentation
- Aligning new content with blueprint conventions (frontmatter, headings, diagrams)

## Quick Reference

1. **Document purpose**: Blueprints provide system and data flow architecture to show how Adobe Experience Platform and applications are integrated. They are visual and technical, not marketing.
2. **Sections**: Use the standard sections from the template; omit only when not applicable (see [reference.md](reference.md)).
3. **Experience League**: Prefer linking to Experience League for product docs, APIs, guardrails, and tutorials. Use full URLs; see [reference.md](reference.md) for URL patterns and formatting.
4. **Repo structure**: Blueprints live under `help/blueprints/`. Update `help/blueprints/TOC.md` when adding or moving blueprint pages.

## Document Template

Every blueprint page should follow this structure. Include only sections that apply.

```markdown
---
title: [Short descriptive title]
description: "[One sentence: what this blueprint shows and why it matters.]"
solution: [Product name, e.g. Real-Time Customer Data Platform, Journey Optimizer]
exl-id: [UUID - leave blank if new, this will be auto-generated as part of the Experience League publishing flow]
---
# [H1 - same as title or expanded]

[1–3 paragraphs: what the blueprint covers, key capabilities, and who it’s for.]

## Applications

* [Product 1]
* [Product 2]

## Use cases

* [Use case 1]
* [Use case 2]

## Prerequisites

[Bullets or short paragraphs: required products, config, or setup.]

## Architecture Diagram

<img src="[path to SVG/image]" alt="[Descriptive alt]" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## Guardrails

[Link to Experience League guardrails and any blueprint-specific limits.]

## Implementation patterns

[Optional: named patterns with bullets.]

## Implementation steps

1. [Step with link to Experience League where relevant]
2. ...

## Implementation considerations

[Optional: identity, performance, security, etc.]

## Related documentation

[Grouped links to Experience League: product docs, APIs, tutorials.]
```

For overview or hub pages, use a shorter structure: intro, use cases (or tabs), architecture image, scenario/pattern table, prerequisites, guardrails, related documentation. See existing overviews in `help/blueprints/` for examples.

## Frontmatter

| Field | Required | Notes |
|-------|----------|--------|
| `title` | Yes | Short; use `[!DNL Product Name]` for product names per Adobe style |
| `description` | Yes | One sentence; used in search and cards |
| `solution` | Yes | Primary product (e.g. Real-Time Customer Data Platform, Journey Optimizer) |
| `exl-id` | Yes | UUID; leave blank for new pages |
| `doc-type` | For overviews | Use `overview-page` for main blueprint overview pages |
| `kt` | Optional | Knowledge base article ID if linked |

## Referencing Adobe Experience League

- **When to link**: Link to Experience League for product documentation, API references, guardrails, tutorials, and configuration steps. Do not duplicate long procedures; summarize and link.
- **URL format**: Use full URLs. Prefer `https://experienceleague.adobe.com/docs/...` or `https://experienceleague.adobe.com/en/docs/...`. For developer docs, `https://developer.adobe.com/...` is also valid.
- **Link text**: Use descriptive text (e.g. "[Create schemas](url)" not "Click here"). For product names in link text, use `[!DNL Product Name]` when appropriate.
- **Related documentation section**: End blueprints with a "Related documentation" section grouping links by category (e.g. Destination configurations, SDK documentation, Profile and segmentation, Tutorials).

For detailed URL patterns, link grouping, and examples, see [reference.md](reference.md).

## Checklist Before Submitting

- [ ] Frontmatter has `title`, `description`, `solution`, `exl-id`
- [ ] H1 matches or appropriately expands the title
- [ ] Architecture diagram present and alt text descriptive
- [ ] Implementation steps link to Experience League where procedures live
- [ ] Guardrails section links to official Experience League guardrail docs
- [ ] Related documentation section includes relevant Experience League links
- [ ] New or moved pages are reflected in `help/blueprints/TOC.md`

## Additional Resources

- Full template and section notes: [reference.md](reference.md)
- Existing blueprints: `help/blueprints/` (e.g. `audience-activation/real-time-lookup.md`, `customer-journeys/journey-optimizer/journey-optimizer-overview.md`)
- TOC and navigation: `help/blueprints/TOC.md`
