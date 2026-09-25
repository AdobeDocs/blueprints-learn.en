---
name: architecture-diagram-category-builder
description: "Guide creation of a brand-new top-level category (subsection) under Architecture Diagrams and Blueprints in the Adobe Experience Platform blueprints repository. Use this skill when a proposed architecture diagram doesn't fit any of the existing categories (Architecture overviews, Audience & Profile Activation, B2B activation & marketing, Customer Insights, Customer journeys) and a new one is needed. Handles the full workflow: confirming a new category is actually warranted, enforcing folder/anchor naming conventions, creating the folder structure and overview.md landing page, adding the TOC.md subsection, and updating the architecture-diagrams landing page card grid. For adding a page to an *existing* category, use architecture-diagram-page-builder instead."
---

# Architecture Diagram Category Builder

This skill guides the creation of a new top-level category under `+ Architecture Diagrams and Blueprints{#architecture-diagrams}` in `/help/blueprints/TOC.md`. A category is a folder like `customer-insights/` or `b2b-activation-marketing/` -- a group of related architecture diagram pages with its own `overview.md` landing page and its own TOC subsection.

**This is a rare operation.** There are five categories today. Adding a sixth should only happen when a genuinely new domain of architecture content doesn't fit any existing one -- not as a shortcut to avoid organizing a page under an existing category.

## Required reading before starting

- `./references/naming-conventions.md` -- the folder/anchor/label naming rule and why it matters. Read this fully; it is the single source of truth for how categories must be named.
- `./references/category-overview-template.md` -- the exact structure required for the new category's `overview.md`.
- If you haven't already, also skim `../architecture-diagram-page-builder/SKILL.md` -- once the category exists, individual pages within it are added using that skill, not this one.

## Phase 1: Confirm a new category is actually needed

Before doing anything else, list the five existing categories and their scope to the user:

| Category | Folder | Scope |
| --- | --- | --- |
| Architecture overviews | `architecture-overviews/` | Top-level Experience Cloud / Experience Platform architecture, guardrails, deployment SDKs |
| Audience & Profile Activation | `audience-profile-activation/` | Audience/profile building and activation via Real-Time CDP, Audience Manager |
| B2B activation & marketing | `b2b-activation-marketing/` | Account-based activation, buying-group journeys, Marketo/Workfront |
| Customer Insights | `customer-insights/` | Customer Journey Analytics and its integrations |
| Customer journeys | `customer-journeys/` | Journey Optimizer, Decision Management, Campaign v7/v8 |

Ask the user to confirm the proposed content doesn't fit any of these. If it's a close fit (e.g., a new B2B diagram, a new personalization diagram), redirect to `architecture-diagram-page-builder` for that existing category instead of creating a new one. Only proceed to Phase 2 if the user confirms a genuinely new category is warranted.

## Phase 2: Gather category information

Use a question form to collect, in one round:

1. **Category label** -- the full, human-readable TOC label (e.g. "Commerce Architecture", not an abbreviation). Present 2-3 suggested phrasings plus "Other".
2. **One-sentence description** -- what this category covers, for the `overview.md` frontmatter and landing-page card.
3. **Primary Adobe solution(s)** -- for frontmatter `solution` field.
4. **Initial pages** -- does the user already have 1+ pages ready to place in this category, or is this just scaffolding the category for pages to follow later?

Derive the folder name and anchor from the category label using the slug rule in `./references/naming-conventions.md` (lowercase, drop `&`, hyphenate, no abbreviation). Show the user the derived folder/anchor and confirm before proceeding -- this is the one detail that's expensive to fix later.

## Phase 3: Create the folder structure

```
help/blueprints/architecture-diagrams/{new-folder}/
help/blueprints/architecture-diagrams/{new-folder}/assets/
help/blueprints/architecture-diagrams/{new-folder}/overview.md
```

Generate `overview.md` using `./references/category-overview-template.md`. If the user has initial pages ready, list them in the table now (using `architecture-diagram-page-builder` to generate those page files themselves -- this skill only creates the category scaffold and its overview page, not individual diagram pages). If no pages exist yet, the table may be empty or omitted until the first page is added -- note this to the user rather than inventing placeholder rows.

The `assets/` folder can be empty at creation time; it exists so the first diagram page added to the category has somewhere to put its images.

## Phase 4: Add the TOC.md subsection

Insert the new category as a top-level entry under `+ Architecture Diagrams and Blueprints{#architecture-diagrams}`, positioned after the last existing category unless the user specifies otherwise:

```
  + {Category Label}{#{folder-slug}}
    + [Overview](/help/blueprints/architecture-diagrams/{new-folder}/overview.md)
    + [{Page title}](/help/blueprints/architecture-diagrams/{new-folder}/{filename}.md)
```

Rules:

- 2-space indent for the category heading, matching the other five.
- The anchor `{#{folder-slug}}` must exactly equal the folder name (see naming-conventions.md).
- `+ [Overview]` is always the first entry, at 4-space indent, before any content pages.
- Preserve the existing order and content of all other TOC.md entries -- only insert, never reorder or rewrite unrelated sections.

## Phase 5: Update the Architecture Diagrams and Blueprints landing page

Add a new card to `help/blueprints/architecture-diagrams/overview.md`, in the same `<table style="table-layout:fixed; width:100%;">` grid used by the other five cards. The new card:

- Links to `{new-folder}/overview.md`.
- Uses a representative diagram thumbnail from `{new-folder}/assets/` (or a neutral placeholder note if no diagram exists yet -- flag this to the user rather than inventing an image path).
- Uses the exact same inline style block as the existing cards (`width:100%; height:160px; object-fit:contain; background-color:#ffffff; border:1px solid #d3d3d3; padding:10px; box-sizing:border-box;` on the image, `min-height:100px;` on the text div).

**Recompute the grid layout.** The existing five cards fill a 3-column grid (two rows, one trailing empty cell). Adding a sixth card fills that empty cell exactly -- no layout change needed. If this is the 7th, 8th, etc. category, add a new `<tr>` with the new card(s) and pad any remaining empty cells in that row with blank `<td style="width:33%; ...;"></td>` elements so the row doesn't render ragged.

## Phase 6: Validation

Confirm and report to the user:

1. **Naming consistency** -- folder name, TOC anchor, and category label slug are identical (per naming-conventions.md).
2. **overview.md structure** -- matches `category-overview-template.md` (intro + two-column `Diagram | Description` table, no embedded images or nested lists in the table).
3. **TOC.md placement** -- new subsection sits under Architecture Diagrams and Blueprints, `+ [Overview]` is first, indentation is correct, no other entries were altered.
4. **Landing page card** -- added in the correct grid position, uses the standard card styling, links to the new `overview.md`.
5. **Redirects** -- if this category consolidates or renames content that previously lived elsewhere (rare for a brand-new category, but check), add entries to `redirects.csv` following the existing `source,dest` format used for prior architecture-diagrams renames.

Fix any validation issues before considering the task complete.

## Notes

- If the user later renames a category (label, folder, or anchor), that's a rename operation, not a new-category operation -- follow the naming-conventions.md rule for the new name, update every internal link (TOC.md, both overview pages, sibling relative links, skill docs), and add redirect entries. Treat it the same way category renames have been handled previously in this repo: `git mv` the folder, then a repo-wide search-and-replace of the old path forms, never a blind global string replace that could collide with unrelated external URLs (e.g. `experienceleague.adobe.com/docs/experience-platform/...` product doc links).
- Keep this skill and `architecture-diagram-page-builder` in sync: if the subsection-mapping table in `architecture-diagram-page-builder`'s `references/toc-placement.md` doesn't yet list the new category, add it there too.
