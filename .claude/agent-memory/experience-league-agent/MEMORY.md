# Experience League Agent Memory

## Key Reference Files in This Repo
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/metadata.md` — repo-level metadata defaults
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/help/blueprints/TOC.md` — guide-level metadata
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/.cursor/skills/blueprint-document-reference/reference.md` — blueprint authoring patterns

## Metadata Rules (See metadata-fields.md for full reference)
- Article front matter REQUIRED: `title`, `description`, `exl-id`
- Article front matter STRONGLY RECOMMENDED: `solution`
- `exl-id` must be a valid UUID; delete/leave blank when copying files (auto-assigned by system)
- `description` should begin "Learn how to..." or "Learn about..." per Adobe guidelines
- `title` max ~60 characters for SEO; use `[!DNL ProductName]` for product names in title
- `solution` values are case-sensitive and must match approved enum (see metadata-fields.md)
- `thumbnail: null` or `thumbnail:` (blank) are both used; empty is acceptable
- `kt:` is a legacy field (knowledge article JIRA number); still seen in this repo; blank is acceptable
- TOC files use: `user-guide-title`, `breadcrumb-title`, `user-guide-description`, `product`, `mini-toc-levels`, `role`
- Repo-level `metadata.md` uses: `cloud`, `solution`, `product`, `type`, `doc-type`, `mini-toc-levels`, `git-repo`, `index`

## Common Patterns in This Repo (blueprints-learn.en)
- Most blueprint files have: `title`, `description`, `solution`, `exl-id`
- Some older files also include: `kt`, `thumbnail`
- Some files use `version` (Campaign v8 blueprints)
- Overview pages use `doc-type: overview-page`
- `solution` often contains multiple comma-separated values: e.g. `Real-Time Customer Data Platform, Campaign`
- Files WITHOUT `solution` still pass validation if `exl-id` is present

## Adobe Markdown Extensions Used in This Repo
- `>[!NOTE]`, `>[!TIP]`, `>[!IMPORTANT]`, `>[!WARNING]`, `>[!CAUTION]`
- `>[!BEGINTABS]` / `>[!TAB Name]` / `>[!ENDTABS]` for tabbed content
- `[!DNL ProductName]` — Do Not Localize tags for product names
- `[!UICONTROL Label]` — UI control references
- `{zoomable="yes"}` — image zoom attribute
- `{width="1000"}` — image width attribute
- `{target="_blank"}` — external link target

## Detailed References
- Full metadata field reference: `metadata-fields.md`
- Authoring guide crawled: https://experienceleague.adobe.com/en/docs/authoring-guide-exl/using/home (Feb 2026)
