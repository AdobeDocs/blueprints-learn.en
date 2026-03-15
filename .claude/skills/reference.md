# Blueprint Document Reference — Detailed Guide

## Document Types

| Type | Purpose | Location / Example |
|------|---------|--------------------|
| **Overview / hub** | Introduces a product or area; links to scenario blueprints | e.g. `overview.md`, `journey-optimizer-overview.md` |
| **Scenario blueprint** | Single use case: architecture, steps, guardrails | e.g. `real-time-lookup.md`, `journey-optimizer-journeys.md` |
| **TOC** | Navigation; do not use as content template | `help/blueprints/TOC.md` |

---

## Full Section Reference

### Title and description (frontmatter)

- **title**: Short, specific. Use `[!DNL Product Name]` for product names (e.g. `[!DNL Journey Optimizer]`).
- **description**: One sentence. Describe what the blueprint shows and the outcome (e.g. "Real-time Customer Profile access at the edge for web and mobile personalization.").

### Body sections

| Section | When to include | Content guidance |
|---------|-----------------|-------------------|
| **Applications** | Always for scenario blueprints | Bullet list of Adobe products/solutions involved (e.g. Real-time Customer Data Platform, Data Collection). |
| **Use cases** | Always | Bullet list of business/technical use cases this blueprint supports. |
| **Prerequisites** | When setup is required | Products, subdomains, SDKs, config that must be in place. Link to Experience League for setup steps. |
| **Architecture Diagram** | Always | Single primary diagram (SVG preferred). Use consistent styling: `style="width:90%; border:1px solid #4a4a4a" class="modal-image"`. Provide meaningful `alt` text. |
| **Guardrails** | Always when product has guardrails | Link to official Experience League guardrail pages. Add blueprint-specific limits (e.g. TTL, rate limits) as bullets. |
| **Implementation patterns** | When multiple approaches exist | Name each pattern (e.g. "Pattern 1: Audience membership-based with Web SDK"); use bullets for when to use and trade-offs. |
| **Implementation steps** | For scenario blueprints with a defined path | Numbered list. Each step: action + link to Experience League where the procedure lives. Do not copy full procedures. |
| **Implementation considerations** | When there are important caveats | Subsections (e.g. Identity considerations, Attribute-based personalization). Bullets or short paragraphs; link out for depth. |
| **Related documentation** | Always | Grouped links to Experience League (and optionally developer.adobe.com). See "Experience League link groups" below. |

### Overview/hub pages

- Start with 1–2 paragraphs on the product/area and what the blueprints cover.
- **Use cases**: Can use `>[!BEGINTABS]` / `>[!TAB ...]` / `>[!ENDTABS]` for multiple categories.
- **Architecture**: One main diagram.
- **Blueprint Scenarios** or **Integration Patterns**: Table with scenario name, short description, and link to the scenario blueprint.
- **Prerequisites**, **Guardrails**, **Related documentation**: Same as above; keep concise.

---

## Adobe Experience League — Agent Directions

### When to reference Experience League

- **Product documentation**: How a product works, UI flows, concepts.
- **APIs**: Endpoints, parameters, examples (Experience Platform, Edge, etc.).
- **Guardrails**: Official guardrail pages for the product or service.
- **Tutorials**: Step-by-step guides (e.g. create schemas, activate destinations).
- **Configuration**: Datastreams, destinations, merge policies, identities, etc.

Do not paste long procedures from Experience League into the blueprint. Summarize and link.

### URL patterns

| Content type | Base URL | Example path |
|--------------|----------|--------------|
| Experience Platform docs | `https://experienceleague.adobe.com/docs/experience-platform/` | `.../profile/home.html`, `.../destinations/catalog/...` |
| Experience League (en) | `https://experienceleague.adobe.com/en/docs/` | Same structure as above with `/en/`. |
| Journey Optimizer | `https://experienceleague.adobe.com/docs/journey-optimizer/` | `.../using/get-started/guardrails.html` |
| Web SDK | `https://experienceleague.adobe.com/docs/experience-platform/web-sdk/` | `.../home.html`, `.../commands/command-responses.html` |
| Edge Network Server API | `https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/` | `.../overview.html`, `.../guardrails.html` |
| Mobile SDK | `https://developer.adobe.com/client-sdks/` | `.../home/`, `.../edge/adobe-journey-optimizer-decisioning/` |
| Tags | `https://experienceleague.adobe.com/docs/experience-platform/tags/` | `.../home.html` |
| Platform tutorials | `https://experienceleague.adobe.com/docs/platform-learn/tutorials/` | `.../profiles/create-merge-policies.html` |

Use the canonical path that matches the current Experience League site (prefer `/en/docs/` when the English path is known).

### Link formatting in markdown

- **Descriptive link text**: `[Create schemas](https://experienceleague.adobe.com/...)` not "click here".
- **Product names in text**: Use `[!DNL Product Name]` per Adobe style (e.g. `[!DNL Real-time Customer Profile]`).
- **External links**: Add `{target="_blank"}` only when the template or pipeline requires it (check existing blueprints in repo).

### Related documentation — suggested groups

Use these groups when they apply:

1. **Destination configurations** (for activation/edge personalization blueprints)
2. **SDK documentation** (Web SDK, Mobile SDK, Edge Network Server API, Tags)
3. **Profile and segmentation** (Real-time Customer Profile, merge policies, segmentation)
4. **Tutorials** (platform-learn or product-specific step-by-step guides)
5. **Product documentation** (main product doc home or key subsections)
6. **Guardrails** (if not already in Guardrails section)

Example:

```markdown
## Related documentation

### Destination configurations
* [Custom Personalization Connection](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization)
* [Activate audiences to edge personalization destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)

### SDK documentation
* [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html)
* [Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html)

### Profile and segmentation
* [Real-time Customer Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)
* [Profile Guardrails](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
```

---

## Repo and TOC

- **Blueprint content path**: `help/blueprints/` (with subfolders by area, e.g. `audience-activation/`, `customer-journeys/journey-optimizer/`).
- **Assets**: Co-locate with the blueprint (e.g. `assets/`, `images/`) or in a shared folder (e.g. `experience-platform/assets/`).
- **TOC**: Edit `help/blueprints/TOC.md` when adding, renaming, or moving blueprint pages. Preserve frontmatter (`user-guide-title`, `breadcrumb-title`, `user-guide-description`, `product`, `mini-toc-levels`, `role`) and the `+` hierarchy.

---

## Example references in this repo

- **Scenario blueprint (long form)**: `help/blueprints/audience-activation/real-time-lookup.md`
- **Overview/hub with tabs and tables**: `help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md`
- **Guardrails-focused**: `help/blueprints/experience-platform/guardrails.md`
- **Navigation**: `help/blueprints/TOC.md`, `help/blueprints/overview.md`

Use these as patterns for section order, frontmatter, diagram placement, and Experience League link usage.
