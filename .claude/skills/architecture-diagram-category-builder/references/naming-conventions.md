# Naming conventions: Architecture Diagrams and Blueprints

This document is the source of truth for how categories under `+ Architecture Diagrams and Blueprints{#architecture-diagrams}` are named. Both the `architecture-diagram-category-builder` skill (new categories) and the `architecture-diagram-page-builder` skill (new pages within existing categories) must follow these rules.

## The rule

**Folder name = TOC anchor slug = kebab-case of the full TOC label.** All three must match exactly, with no abbreviation or truncation.

| TOC label | Anchor | Folder |
| --- | --- | --- |
| Architecture overviews | `#architecture-overviews` | `architecture-overviews/` |
| Audience & Profile Activation | `#audience-profile-activation` | `audience-profile-activation/` |
| B2B activation & marketing | `#b2b-activation-marketing` | `b2b-activation-marketing/` |
| Customer Insights | `#customer-insights` | `customer-insights/` |
| Customer journeys | `#customer-journeys` | `customer-journeys/` |

This is the current, corrected state of all five categories (as of 2026-09-16). Earlier in this repo's history some of these were abbreviated (`architecture-overview`, `audience-activation`, `b2b-activation`) -- that inconsistency has been fixed. Do not reintroduce abbreviated folder/anchor names for new or existing categories.

## Why this matters

- **Predictability.** A contributor (human or agent) should be able to guess the folder path from the TOC label, and vice versa, without opening TOC.md.
- **Safe automation.** Skills and scripts that generate paths from labels (or labels from paths) only work reliably when the mapping is exact and mechanical (kebab-case, no abbreviation).
- **Redirect hygiene.** Every rename requires new entries in `redirects.csv`. Keeping names stable and fully descriptive from the start avoids repeated rename churn.

## How to derive a slug from a label

1. Lowercase the label.
2. Drop `&` entirely and join the surrounding words with a hyphen (e.g. `Audience & Profile Activation` -> `audience-profile-activation`).
3. Replace spaces with hyphens.
4. Strip punctuation other than hyphens.
5. Do not abbreviate, truncate, or drop words from the label (no `b2b-activation` for "B2B activation & marketing" -- use `b2b-activation-marketing`).

## Required per-category assets

Every category folder directly under `help/blueprints/architecture-diagrams/` must contain:

1. **`overview.md`** -- a landing page for the category. See `./category-overview-template.md` for the required structure. Every category overview page must look the same: intro paragraph(s), then a single `| Diagram | Description |` table listing every page in the category (in TOC order). Do not use nested `<ul><li>` cells, embedded diagram images, or a third column -- match the existing five categories exactly.
2. **`assets/`** -- folder for diagram images, even if empty at creation time (create it once the first diagram is added).

## TOC.md requirements

- The category's `+ [Overview](/help/blueprints/architecture-diagrams/{folder}/overview.md)` entry is always the **first** entry under the category heading, before any content pages.
- The category heading and its anchor go immediately under `+ Architecture Diagrams and Blueprints{#architecture-diagrams}`, at the same 2-space indent level as the other five categories.
- Content pages are indented 4 spaces (`+` prefixed with four leading spaces). Nested sub-groupings (e.g. RTCDP grouping under Audience & Profile Activation) are indented 6 spaces.

## Landing page requirements

`help/blueprints/architecture-diagrams/overview.md` (the top-level Architecture Diagrams and Blueprints landing page) must have exactly one card per category, in TOC order. Each card:

- Links to the category's `overview.md` (not a content page).
- Uses a representative diagram image from that category's `assets/` folder as the thumbnail, styled with the standard card CSS (`background-color:#ffffff; border:1px solid #d3d3d3;` plus the shared sizing/padding rules already in the file).
- Includes the category name (bold/strong) and a one-sentence description matching the category overview's intro.

When the number of categories is a multiple of 3, the table renders as clean full rows (3-column, `table-layout:fixed`, `width:33%` per cell). If it isn't a multiple of 3, add one empty `<td>` per missing slot in the last row (do not leave the table ragged/unstyled).
