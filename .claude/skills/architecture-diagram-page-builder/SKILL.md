---
name: architecture-diagram-page-builder
description: "Guide creation of new architecture diagram pages for the Adobe Experience Platform blueprints repository. Use this skill when adding a new top-level architecture diagram, integration architecture page, or application architecture overview. Architecture pages cover top-level AEP and application architectures and primary integration points -- not in-depth use cases (those belong in use-case-pattern-builder). Handles the full workflow: gathering page info, generating the markdown file, placing it in the correct topic folder, and updating TOC.md."
---

# Architecture Diagram Page Builder

This skill guides the creation of new architecture diagram pages for the Adobe Experience Platform blueprints repository. Architecture diagram pages provide top-level visual references for how AEP and Adobe applications fit together, the primary data flows between them, and the integration points authors need to be aware of when designing solutions.

## Scope

Architecture diagram pages are **focused, reference-style pages** -- typically 40-100 lines of markdown -- that contain:

- One or more architecture diagrams with brief explanations of each diagram's purpose
- Links to use case patterns the architecture supports (the architecture page does not duplicate that content)
- A short list of the primary data flows and integration points illustrated
- Experience League links for further reading on the application domain

They are **not** the place for in-depth use case content. KPIs, business objectives, tactical use case examples, function chains, and persona narratives belong on use case pattern pages instead -- generated via the `use-case-pattern-builder` skill. See `references/scope-guardrails.md` for the full guardrails.

## Required reading before starting

Read the following reference files for templates and rules:

- `references/diagram-template.md` -- the full markdown template with placeholder values
- `references/toc-placement.md` -- the subsection-mapping table and entry format for TOC.md
- `references/scope-guardrails.md` -- rules for what belongs on an architecture page vs. a use case pattern page

## Phase 1: Information Gathering

Interview the user to collect all required information before generating any files. Do not proceed to content generation until every required item is provided or explicitly deferred.

### Required information

1. **Page title** -- The human-readable title (e.g., `Adobe Journey Optimizer architecture diagrams`).

2. **Topic folder** -- Where the page lives. Pick exactly one based on the diagram's primary domain:
   - `experience-platform/` -- top-level AEP, multi-app, or platform-level diagrams
   - `customer-journeys/` -- AJO, Campaign, journey orchestration
   - `customer-journey-analytics/` -- CJA architectures
   - `audience-activation/` -- RTCDP, audience and profile activation
   - `b2b/` -- B2B-specific architectures

3. **Filename** -- Kebab-case, derived from the page title (e.g., `Journey Optimizer architecture` -> `journey-optimizer-architecture.md`). Confirm with the user.

4. **Page purpose** -- 1-2 sentences describing what the diagrams collectively illustrate. Used for the `description` frontmatter field and the opening paragraph.

5. **Adobe solutions** -- Comma-separated list of Adobe products central to the page. Used for the `solution` frontmatter field. Examples: `Experience Platform, Journey Optimizer, Customer Journey Analytics`.

6. **Diagrams** -- One or more diagrams. For each diagram, collect:
   - **Image filename** (e.g., `aep_data_flow.svg`). SVG preferred; PNG acceptable.
   - **Section title** -- becomes the H2 heading for the diagram (e.g., `Data flow diagram`, `Detailed architecture diagram`).
   - **Purpose explanation** -- 1-2 sentences describing what the diagram shows.
   - **Alt text** -- short accessible description.

7. **Use case patterns supported** -- 2-5 existing patterns this architecture enables.

   **Recommend candidates first.** Before asking the user to provide patterns, scan `/help/blueprints/use-case-patterns/` and propose 3-6 likely matches based on the page title, page purpose, and Adobe solutions collected above. For each suggestion, present:
   - Pattern name (with the linked path)
   - One-sentence rationale for why it fits this architecture

   Present the suggestions as a numbered shortlist and ask the user to (a) accept any, (b) reject any, and (c) add patterns you missed. Only generate suggestions that point to real files -- glob/read to confirm before suggesting. Do not hallucinate pattern names.

   For each accepted pattern, capture the category and filename. Validate each file exists at `/help/blueprints/use-case-patterns/{category}/{pattern-file}.md` before generating.

8. **Primary data flows / integration points** -- 3-7 bullets describing key flows and integration boundaries shown across the diagrams (e.g., `Real-time event ingestion from Web SDK to Edge Network`, `Profile synchronization between Experience Platform Hub and Edge`).

9. **Experience League links** -- 3-6 links to relevant Experience League documentation for further reading. Each must begin with `https://experienceleague.adobe.com/`.

   **Recommend candidates first.** Based on the Adobe solutions and page purpose, propose 4-8 plausible Experience League articles (e.g., the canonical landing or overview pages for each named solution, key integration guides, deployment references). For each suggestion, present:
   - Article title
   - URL
   - One-line rationale for why it fits the page

   Mark suggestions as **unverified** unless you've actually fetched the URL -- the user must confirm or replace each before it lands in the generated file. Ask the user to (a) accept, (b) replace any URL with a verified one they already have, and (c) add their own. Never invent URLs you have not seen; if you are uncertain, suggest the article title and let the user supply the URL.

### Optional

- **Related-content callout** -- a single link rendered as `>[!MORELIKETHIS]` block near the top of the page. Useful when there is a sibling integration or configuration guide on Experience League the reader should be aware of.

If the user does not provide all required items, ask for the missing ones before proceeding. Do not fabricate diagrams, patterns, or links.

## Phase 2: Scope Check

Before generating, re-read the user's diagram descriptions, data-flow bullets, and any draft prose. Apply the guardrails from `references/scope-guardrails.md`.

If any of the following appears in the planned content, warn the user and offer to redirect that section to a use case pattern page (or trim it from the architecture page):

- KPIs or measurement formulas
- Business objectives or business impact narratives
- Tactical use case examples (specific personalization scenarios, campaign examples, etc.)
- Function chains (`A > B > C > D` style)
- Persona-driven storytelling

If the planned content stays within architecture-page scope (top-level architecture, system data flow, integration points, deployment topology, edge vs. hub), confirm with the user and proceed to Phase 3.

## Phase 3: Content Generation

Generate the page at:

```
/help/blueprints/{topic-folder}/{kebab-filename}.md
```

Use `references/diagram-template.md` as the source template. Fill in all placeholder values with the collected information. The generated file must include:

1. **YAML frontmatter** -- `title`, `description`, `solution` only.
   - **Do NOT include `exl-id`** -- the publishing pipeline auto-assigns it.
   - **Do NOT include** `product_v2`, `feature_v2`, `role_v2`, `topic_v2`, `TQID`, `kt`, or `thumbnail` -- these are also auto-populated.

2. **H1 heading** -- the page title.

3. **Opening paragraph** -- 1-2 sentences derived from the page-purpose input.

4. **Optional `>[!MORELIKETHIS]` block** -- only if the user provided a related-content link.

5. **One H2 section per diagram** -- in the order the user provided them. Each section contains:
   - The section title as the H2 heading
   - 1-2 sentences explaining the diagram's purpose
   - The image embed using the standard convention:

     ```html
     <img src="assets/{filename}" alt="{Alt Text}" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />
     ```

6. **`## Use case patterns supported`** -- bulleted list. Each bullet:

   ```
   - [{Pattern name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) -- {1-line note on why this architecture enables the pattern}
   ```

7. **`## Primary data flows and integration points`** -- bulleted list of 3-7 flow/integration items.

8. **`## Further reading`** -- bulleted list of Experience League links:

   ```
   - [{Article title}]({Experience League URL})
   ```

Use `[!DNL ...]` syntax for Adobe product names in body text and bullets, matching the convention of existing pages.

## Phase 4: Cross-reference updates

Update **`/help/blueprints/TOC.md`** to add the new page to navigation. This is the only cross-reference page to update.

Read `references/toc-placement.md` for the full subsection-mapping table and rules. Summary:

| Topic folder | TOC subsection |
| --- | --- |
| `experience-platform/` | `+ Architecture overviews{#architecture-overview}` |
| `experience-platform/deployment/` | `+ Deployment{#deployment}` (sub-subsection of Architecture overviews) |
| `audience-activation/` | `+ Audience & Profile Activation{#audience-activation}` |
| `b2b/` | `+ B2B activation & marketing{#b2b-activation}` |
| `customer-journey-analytics/` | `+ Customer Journey Analytics{#customer-journey-analytics}` |
| `customer-journeys/` | `+ Customer journeys{#customer-journeys}` |

Entry format (4-space indent + `+`):

```
    + [{Page title}](/help/blueprints/{topic-folder}/{filename}.md)
```

Append the new entry as the last item in the matching subsection unless the user specifies a different position. Preserve the exact 4-space indentation -- TOC parsing depends on it.

## Phase 5: Validation

After all files are created and updated, verify the following and report any failures to the user:

1. **Image asset existence** -- For each diagram, check that `/help/blueprints/{topic-folder}/assets/{filename}` exists. **Warn** if missing; do not block (the user may be authoring in parallel with diagram design). Surface a clear list of missing files so the user knows what to add.

2. **Use case pattern links** -- Every pattern link in the file points to an existing markdown file under `/help/blueprints/use-case-patterns/`. Use `Read` or glob to confirm each target exists.

3. **Experience League links** -- Spot-check that every URL in the `## Further reading` section starts with `https://experienceleague.adobe.com/`.

4. **TOC entry placement** -- The new entry is inside the correct subsection, uses 4-space indentation, and the path matches the generated file location exactly.

5. **File naming** -- The page filename is kebab-case and matches the path referenced in TOC.md.

6. **Frontmatter completeness** -- The page includes `title`, `description`, and `solution`. It must **not** include `exl-id`, `product_v2`, `feature_v2`, `role_v2`, `topic_v2`, `TQID`, `kt`, or `thumbnail`.

Fix any validation issues before considering the task complete.

## Notes

- Always use `[!DNL ...]` syntax for Adobe product names in body text and bullets, following the convention of existing pages.
- Architecture diagrams are typically SVG (preferred for crispness and scaling) but PNG is acceptable for raster-source artwork.
- The `<img>` embed inline-styling string (`border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;`) and `class="modal-image"` are required -- they enable the Experience League modal-zoom interaction.
- If the user is creating a page for a brand-new topic folder that does not exist yet, warn them that TOC.md needs a new top-level subsection under `+ Architecture Diagrams and Blueprints{#architecture-diagrams}`. Handle that as a separate step with the user's explicit approval.
- If the architecture diagram extensively documents a *single use case end-to-end* (with KPIs, business objectives, function chain), redirect the user to `use-case-pattern-builder` -- that is not an architecture page.
