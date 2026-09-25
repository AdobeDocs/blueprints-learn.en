# TOC.md placement reference

When the skill generates a new architecture diagram page, it must add an entry to `/help/blueprints/TOC.md` so the page is discoverable in site navigation. This document defines exactly where and how that entry goes.

## Parent section

All architecture diagram pages live under the top-level `+ Architecture Diagrams and Blueprints{#architecture-diagrams}` section in TOC.md. Within that section, several subsections group pages by topic.

Folder names, TOC anchors, and TOC labels for these subsections must follow the naming rule in `../../architecture-diagram-category-builder/references/naming-conventions.md` -- see that file if a new category is ever needed (use the `architecture-diagram-category-builder` skill for that, not this one).

## Subsection mapping

Pick the subsection that matches the new page's topic folder:

| Topic folder | TOC subsection heading |
| --- | --- |
| `architecture-diagrams/architecture-overviews/` | `+ Architecture overviews{#architecture-overviews}` |
| `architecture-diagrams/audience-profile-activation/` | `+ Audience & Profile Activation{#audience-profile-activation}` |
| `architecture-diagrams/b2b-activation-marketing/` | `+ B2B activation & marketing{#b2b-activation-marketing}` |
| `architecture-diagrams/customer-insights/` | `+ Customer Insights{#customer-insights}` |
| `architecture-diagrams/customer-journeys/` | `+ Customer journeys{#customer-journeys}` |

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

`+ Architecture overviews{#architecture-overviews}` has no nested groupings -- all pages under `architecture-diagrams/architecture-overviews/` (including SDK deployment pages, e.g. `websdk.md`, `appsdk.md`) sit at the same four-space indent level. Other subsections (`Audience & Profile Activation`, `B2B activation & marketing`, etc.) may still contain nested groupings -- inspect the section before placing the entry. If a nested grouping is present and the new page belongs in it, indent two additional spaces; otherwise place the entry at the subsection's top level.

## Worked examples

### Example 1 -- top-level AEP page

- Topic folder: `architecture-diagrams/architecture-overviews/`
- Filename: `mix-modeler-integration.md`
- Page title: `Adobe Mix Modeler integration with Experience Platform`

Entry:

```
    + [Adobe Mix Modeler integration with Experience Platform](/help/blueprints/architecture-diagrams/architecture-overviews/mix-modeler-integration.md)
```

Placed under `+ Architecture overviews{#architecture-overviews}`.

### Example 2 -- AJO journey architecture

- Topic folder: `architecture-diagrams/customer-journeys/`
- Filename: `cross-channel-journey-architecture.md`
- Page title: `Cross-channel journey architecture`

Entry:

```
    + [Cross-channel journey architecture](/help/blueprints/architecture-diagrams/customer-journeys/cross-channel-journey-architecture.md)
```

Placed under `+ Customer journeys{#customer-journeys}`.

### Example 3 -- SDK deployment page

- Topic folder: `architecture-diagrams/architecture-overviews/`
- Filename: `mobile-sdk-architecture.md`
- Page title: `Mobile SDK deployment architecture`

Entry (same four-space indent as other Architecture overviews pages):

```
    + [Mobile SDK deployment architecture](/help/blueprints/architecture-diagrams/architecture-overviews/mobile-sdk-architecture.md)
```

Placed under `+ Architecture overviews{#architecture-overviews}`.

## Verification

After editing TOC.md, re-read the affected subsection and confirm:

1. The new entry uses exactly four spaces of indent (or six if nested under a subsection-specific grouping, e.g. `Audience & Profile Activation`'s RTCDP grouping).
2. The link target matches the file path on disk -- including the `.md` extension.
3. The entry is grouped within the correct subsection -- not floating between subsections.
4. No existing entries were reordered or modified.
