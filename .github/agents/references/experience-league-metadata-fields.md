# Adobe Experience League — Approved Metadata Fields Reference

*Sourced from Adobe ExL Authoring Guide (crawled Feb 2026) + repo analysis of blueprints-learn.en*

---

## Metadata Hierarchy

Metadata cascades in this order (article overrides TOC, TOC overrides repo):
1. Article front matter (highest priority)
2. TOC.md in the user guide
3. metadata.md at repo root (lowest priority)

---

## Article-Level Fields

### REQUIRED

| Field | Description | Format / Constraints |
|-------|-------------|----------------------|
| `title` | SEO page title. Appears in search results. | Max ~60 chars; title case; use `[!DNL Product]` for product names; do NOT duplicate H1 exactly unless intended |
| `description` | Meta description for search engines and ExL recommendations. | 150–160 chars; ideally begins "Learn how to..." or "Learn about..."; validation fails if missing/null |
| `exl-id` | System-assigned unique identifier. Used for content tracking. | UUID format (e.g. `70573eb9-cd69-4fe6-b2ae-dae81665a308`); **delete when copying a file** — it will be auto-assigned; never duplicate across files |

### STRONGLY RECOMMENDED

| Field | Description | Valid Values |
|-------|-------------|--------------|
| `solution` | Adobe product(s) the article covers. Used for ExL search/filtering and content recommendations. | Comma-separated; case-sensitive; must match approved enum (see Valid Solution Values below) |

### OPTIONAL — COMMON

| Field | Description | Valid Values / Notes |
|-------|-------------|----------------------|
| `kt` | Legacy knowledge-article JIRA number. Used for analytics tracking. | Integer (e.g. `7207`); blank acceptable; `null` acceptable |
| `thumbnail` | Thumbnail image reference for recommendations/analytics. | Filename string or `null` or blank |
| `version` | Product version filter. Primarily used for AEM and Campaign blueprints. | E.g. `Campaign v8`, `Campaign v8 Client Console`; must match version.yml |
| `doc-type` | Content classification used in repo/analytics. | `blueprint`, `overview-page`, `Video`, `Tutorial`, `Troubleshooting` (lowercase preferred) |
| `feature` | Topic tags shown as "Topics" on ExL pages. | 1–2 per article; title case; must match feature.yml; comma-separated |
| `feature-set` | Parent application for feature validation. | Must match feature.yml values |
| `role` | Target audience role. Shown as "Created for" on ExL. | `Admin`, `Architect`, `Data Architect`, `Data Engineer`, `Developer`, `Leader`, `User` |
| `level` | User experience level. Shown as "Created for" on ExL. | `Beginner`, `Intermediate`, `Experienced` (title case) |
| `topic` | Cross-product topics for search/filtering. | Title case; must match topic.yml; comma-separated |
| `type` | Guide classification. | `Documentation` (default), `Tutorial`, `Troubleshooting` |
| `last-substantial-update` | Surfaces content in "What's new" widgets. | Format: `YYYY-MM-DD` |
| `hide` | Excludes page from all search and recommendations; also sets index to no. | `yes` or `no` |
| `hidefromtoc` | Removes from TOC navigation but page is still accessible via direct link. | `yes` or `no` |
| `index` | Controls whether page appears in external search/sitemap. | `yes`/`no` or `y`/`n`; default: `no` (indexed) |
| `recommendations` | Controls "More help on this feature" widget behavior. | `noDisplay` (prevents widget display), `noCatalog` (excludes from recommendations pool) |
| `internal` | Marks page as Adobe internal-only. Prevents internal link flagging. | `yes` |
| `short-description` | Condensed description for ExL landing pages. Uses `description` if omitted. | One sentence; max ~20 words |
| `activity` | Page usage classification. | `understand`, `implement`, `troubleshoot` (lowercase) |
| `sub-product` | Product subcomponent. Work with solution teams for valid enums. | Lowercase; e.g. `search`, `assets`, `sites` |
| `team` | Team assignment for analytics. | E.g. `TM` |
| `landing-page-name` | Links to landing page for breadcrumb. | E.g. `experience-manager` |
| `landing-page-breadcrumb-title` | Breadcrumb text for landing page link. | E.g. `AEM` |
| `auto-video-transcripts` | Enables video transcripts by default. | `true` |
| `badgeType` | Badge for content status. | Varies; e.g. `informative`, `positive` |
| `badgePremium` | Premium badge indicator. | Per Adobe badge spec |
| `badgeLabel` | Badge label text. | Short string |
| `source-git-url` | Source repository URL. | Full GitHub URL |
| `cloud` | Cloud category override at article level. | Title case; must match cloud.yml |

---

## TOC.md Fields

| Field | Description | Notes |
|-------|-------------|-------|
| `user-guide-title` | Guide name displayed in ExL breadcrumbs and landing pages. | Required for TOC files |
| `breadcrumb-title` | Shorter guide name for breadcrumbs when user-guide-title is too long. | Optional |
| `user-guide-description` | Guide summary for ExL landing page. | One sentence; max ~20 words recommended |
| `product` | Analytics tracking for the guide. Single value only. | Must match product.yml (see Valid Product Values) |
| `mini-toc-levels` | Number of heading levels shown in right-nav mini-TOC. | Integer 1–6; default 2 |
| `role` | Default audience role for the guide. | Same values as article `role`; comma-separated |
| `index` | Whether guide is indexed. | `yes`/`no` |

---

## Repo-Level metadata.md Fields

| Field | Notes |
|-------|-------|
| `cloud` | Default cloud category for all articles in repo |
| `solution` | Default solution for all articles |
| `product` | Default product for analytics tracking |
| `type` | Default guide type |
| `doc-type` | Default doc type |
| `mini-toc-levels` | Default mini-TOC levels |
| `git-repo` | GitHub repo URL; enables "Edit this page" and "Log issue" buttons |
| `index` | Default index setting |

---

## Valid Solution Values (Case-Sensitive)

Common values used in this repo:
- `Experience Platform`
- `Real-Time Customer Data Platform`
- `Journey Optimizer`
- `Journey Optimizer B2B Edition`
- `Customer Journey Analytics`
- `Campaign`
- `Campaign v8`
- `Campaign Classic v7`
- `Campaign Standard`
- `Audience Manager`
- `Target`
- `Analytics`
- `Data Collection`
- `Commerce`
- `Marketo Engage`
- `Experience Cloud`
- `Journey Orchestration`

Multiple values: comma-separated, e.g. `Real-Time Customer Data Platform, Campaign`

---

## Valid Product Values (for `product` field — analytics tracking)

See system prompt for full list. Key values:
- `adobe experience platform` / `experience platform` / `aem`
- `adobe analytics` / `analytics` / `aa`
- `adobe journey optimizer` / `journey optimizer` / `jo`
- `adobe customer journey analytics` / `customer journey analytics` / `cja`
- `adobe real time customer data platform` / `real time cdp` / `rtcdp`
- `adobe marketo` / `marketo` / `amk`
- `adobe campaign` / `campaign` / `ac`
- `adobe target` / `target` / `at`

---

## Valid Role Values

- `Admin`
- `Architect`
- `Data Architect`
- `Data Engineer`
- `Developer`
- `Leader`
- `User`

---

## Key Validation Rules

1. Never leave `exl-id` with the same UUID in a copied file — delete it and let the system assign a new one.
2. Blank/null `thumbnail` and `kt` are acceptable; these are legacy fields.
3. `solution` values must exactly match the approved enum — case-sensitive.
4. `description` validation fails if missing or null; always provide a meaningful value.
5. Wrap `title` values in quotes if they contain colons, brackets, or leading special characters.
6. Multiple `solution` values are comma-separated within a single string value.
7. `product` is single-value only (for analytics tracking); do not use comma-separated values.
8. To request new enum values, file a UGP JIRA ticket with "Content Tagging" component.
