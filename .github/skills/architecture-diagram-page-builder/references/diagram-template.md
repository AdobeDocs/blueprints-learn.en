# Architecture diagram page template

This is the full markdown template for an architecture diagram page. Replace every `{placeholder}` with the value collected during Phase 1 of the skill workflow. Remove any optional section that does not apply (e.g., the `>[!MORELIKETHIS]` block) -- do not leave empty placeholders in the generated file.

---

```markdown
---
title: {Page title}
description: {1-2 sentence page purpose, used for search snippets and previews}
solution: {Comma-separated Adobe solutions, e.g. Experience Platform, Journey Optimizer, Customer Journey Analytics}
---
# {Page title}

{Opening paragraph -- 1-2 sentences describing what the diagrams collectively illustrate. Frame the page as a top-level architecture reference, not a use case walkthrough.}

>[!MORELIKETHIS]
>
>[{Related-content link text}]({Related-content URL}).

## {Diagram 1 section title}

{1-2 sentence explanation of what the diagram shows and why it matters.}

<img src="assets/{filename-1}" alt="{Alt text for diagram 1}" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## {Diagram 2 section title}

{1-2 sentence explanation.}

<img src="assets/{filename-2}" alt="{Alt text for diagram 2}" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Primary data flows and integration points

- {Flow or integration 1 -- e.g., "Real-time event ingestion from [!DNL Web SDK] to [!DNL Edge Network]"}
- {Flow or integration 2 -- e.g., "Profile sync between [!DNL Experience Platform] Hub and Edge"}
- {Flow or integration 3}
- {Flow or integration 4}
- {Flow or integration 5}

## Use case patterns supported

The architecture above supports the following use case patterns:

- [{Pattern 1 name}](/help/blueprints/use-case-patterns/{category}/{pattern-1-file}.md) -- {1-line note on why this architecture enables the pattern}
- [{Pattern 2 name}](/help/blueprints/use-case-patterns/{category}/{pattern-2-file}.md) -- {1-line note}
- [{Pattern 3 name}](/help/blueprints/use-case-patterns/{category}/{pattern-3-file}.md) -- {1-line note}

## Further reading

- [{Article 1 title}]({Experience League URL 1})
- [{Article 2 title}]({Experience League URL 2})
- [{Article 3 title}]({Experience League URL 3})
```

---

## Frontmatter rules

- **Required fields:** `title`, `description`, `solution`.
- **Forbidden fields** (auto-assigned at publish time): `exl-id`, `product_v2`, `feature_v2`, `role_v2`, `topic_v2`, `TQID`, `kt`, `thumbnail`. Do not include these in newly authored files.

## Body conventions

- **One H1** -- the page title. Match the `title` frontmatter exactly.
- **One H2 per diagram.** No H3 inside diagram sections; keep them to a 1-2 sentence intro plus the image.
- **`<img>` embed** -- the inline style and `class="modal-image"` are required. They drive the Experience League modal-zoom interaction.
- **Image path** -- always `assets/{filename}` (relative to the page's topic folder). Do not use absolute paths.
- **Adobe product names** -- wrap in `[!DNL ...]` in body text and bullets. Example: `[!DNL Real-Time CDP]`, `[!DNL Journey Optimizer]`, `[!DNL Experience Platform]`.
- **Use case pattern links** -- always use the absolute `/help/blueprints/use-case-patterns/{category}/{file}.md` form so the link resolves from any page that may transclude this content.
- **Experience League links** -- absolute URLs starting with `https://experienceleague.adobe.com/`. Prefer the canonical doc URL over a localized variant.

## Section ordering

Keep the order consistent across all architecture pages so readers can scan predictably:

1. Frontmatter
2. H1 + opening paragraph
3. (Optional) `>[!MORELIKETHIS]` callout
4. One H2 per diagram (in user-specified order)
5. `## Use case patterns supported`
6. `## Primary data flows and integration points`
7. `## Further reading`

## Length expectations

40-100 lines of markdown is typical. If the page exceeds 150 lines, the content has likely drifted into use-case-pattern territory -- re-check `scope-guardrails.md` and consider splitting.
