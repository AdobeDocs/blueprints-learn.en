# TOC.md placement reference

When the skill generates a new architecture diagram page, it must add an entry to `/help/blueprints/TOC.md` so the page is discoverable in site navigation. This document defines exactly where and how that entry goes.

## Parent section

All architecture diagram pages live under the top-level `+ Architecture Diagrams and Blueprints{#architecture-diagrams}` section in TOC.md. Within that section, several subsections group pages by topic.

## Subsection mapping

Pick the subsection that matches the new page's topic folder:

| Topic folder | TOC subsection heading |
| --- | --- |
| `experience-platform/` | `+ Architecture overviews{#architecture-overview}` |
| `experience-platform/deployment/` | `+ Deployment{#deployment}` (a sub-subsection nested inside `Architecture overviews`) |
| `audience-activation/` | `+ Audience & Profile Activation{#audience-activation}` |
| `b2b/` | `+ B2B activation & marketing{#b2b-activation}` |
| `customer-journey-analytics/` | `+ Customer Journey Analytics{#customer-journey-analytics}` |
| `customer-journeys/` | `+ Customer journeys{#customer-journeys}` |

If the user proposes a topic folder that is not in this table, treat that as a new top-level subsection and pause -- ask the user to confirm whether to create it. Do not silently invent a new subsection.

## Entry format

```
    + [{Page title}](/help/blueprints/{topic-folder}/{filename}.md)
```

Rules:

- **Indentation:** exactly four spaces, then `+ `. The TOC parser depends on this; tabs or different spacing will break navigation.
- **Link text:** the page title, matching the `title` frontmatter exactly. Use `[!DNL ...]` only if existing siblings in the same subsection use it -- match the local convention.
- **Link target:** absolute path beginning with `/help/blueprints/`. Always include the `.md` extension.
- **Position:** append as the last entry in the matching subsection unless the user specifies a different position. Preserve the existing order of all sibling entries.

## Nested subsections

`+ Architecture overviews{#architecture-overview}` contains a nested `+ Deployment{#deployment}` block for SDK pages. If the new page lives under `experience-platform/deployment/`, place the entry inside `Deployment` with **six** spaces of indent:

```
      + [{Page title}](/help/blueprints/experience-platform/deployment/{filename}.md)
```

Other subsections (`Audience & Profile Activation`, `B2B activation & marketing`, etc.) may also contain nested groupings -- inspect the section before placing the entry. If a nested grouping is present and the new page belongs in it, indent two additional spaces; otherwise place the entry at the subsection's top level.

## Worked examples

### Example 1 -- top-level AEP page

- Topic folder: `experience-platform/`
- Filename: `mix-modeler-integration.md`
- Page title: `Adobe Mix Modeler integration with Experience Platform`

Entry:

```
    + [Adobe Mix Modeler integration with Experience Platform](/help/blueprints/experience-platform/mix-modeler-integration.md)
```

Placed under `+ Architecture overviews{#architecture-overview}`.

### Example 2 -- AJO journey architecture

- Topic folder: `customer-journeys/`
- Filename: `cross-channel-journey-architecture.md`
- Page title: `Cross-channel journey architecture`

Entry:

```
    + [Cross-channel journey architecture](/help/blueprints/customer-journeys/cross-channel-journey-architecture.md)
```

Placed under `+ Customer journeys{#customer-journeys}`.

### Example 3 -- Deployment SDK page

- Topic folder: `experience-platform/deployment/`
- Filename: `mobile-sdk-architecture.md`
- Page title: `Mobile SDK deployment architecture`

Entry (note the six-space indent):

```
      + [Mobile SDK deployment architecture](/help/blueprints/experience-platform/deployment/mobile-sdk-architecture.md)
```

Placed under `+ Deployment{#deployment}` inside `+ Architecture overviews{#architecture-overview}`.

## Verification

After editing TOC.md, re-read the affected subsection and confirm:

1. The new entry uses exactly four spaces of indent (or six if nested under `Deployment`).
2. The link target matches the file path on disk -- including the `.md` extension.
3. The entry is grouped within the correct subsection -- not floating between subsections.
4. No existing entries were reordered or modified.
