---
name: Adobe Experience League Authoring Guidelines
description: Complete reference for Adobe Experience League markdown authoring rules, crawled from the official authoring guide in March 2026.
type: reference
---

# Adobe Experience League Authoring Guidelines

Source: https://experienceleague.adobe.com/en/docs/authoring-guide/using/home
Crawled: 2026-03-15

---

## 1. METADATA / FRONT MATTER

### Required Fields
| Field | Requirement | Rules |
|---|---|---|
| `title` | Required | Max 60 chars (English). Title case. No product names unless needed for clarity. System appends "| ProductName" automatically. Wrap in quotes if it contains colons or brackets. |
| `description` | Required | 150-160 chars max. Cannot be blank/null. Concepts begin "Learn about..." Tasks begin "Learn how to..." or imperative verb. |

### Optional but Frequently Used Fields
| Field | Valid Values | Notes |
|---|---|---|
| `feature` | Must match feature YAML values; title case with spaces (e.g., "Content Fragment") | 1-2 per article; displays in Topics |
| `feature-set` | Must validate against feature YAML | Parent application of feature |
| `role` | User, Developer, Leader, Admin, Architect, Data Architect, Data Engineer | Case-sensitive; displays as "Created for" |
| `level` | Beginner, Intermediate, Experienced | Defaults to Beginner if unspecified |
| `solution` | Must match solution YAML (e.g., "Campaign, Campaign Standard v7") | Multiple values allowed; used for search filtering |
| `topic` | Must match topic YAML; title case with spaces | For cross-product filtering (e.g., "Integrations") |
| `type` | Documentation, Tutorial, Troubleshooting | Repo-level; defaults to Documentation |
| `short-description` | One sentence, max 20 words | For ExL landing pages when description is too long |
| `badgePremium` | `label="Premium" type="Positive" url="..."` | Page-level badge |
| `mini-toc-levels` | 1-6 (default 2) | Controls right-nav heading display depth |
| `hidefromtoc` | true/false | Excludes from left nav but keeps URL accessible |

### Metadata Placement
- Article level: top of markdown file as YAML front matter
- TOC level: in TOC.md file
- Repo level: in metadata.md file

### Key Formatting Rules
- Wrap values containing commas or brackets in quotation marks
- Multiple values separated by commas
- Case-sensitive matching against YAML definitions
- Empty/blank tag values cause validation failure

### Deprecated Fields
seo-title, seo-description, audience, difficulty, uuid (from migration era)

---

## 2. MARKDOWN SYNTAX (ADOBE-FLAVORED)

### Text Formatting
- Bold: `**text**`
- Italic: `*text*`
- Bold + Italic: `***text***`
- Escape special characters: use backslash `\` before `# { } [ ] * + - . !`
- HTML entities: `&lt;` `&gt;` `&amp;` `&mdash;` `&ndash;`

### Headings
- Use ATX-style (`#` syntax only, never underline/setext style)
- One H1 per document (usually the page title matching metadata `title`)
- All subsequent headings H2 (`##`) or lower
- Blank lines required before and after headings (except the very first heading)
- Max 69 characters (English) / 120 characters (localized)
- Max ~5 words preferred
- Sentence case for all headings (capitalize only first word and proper nouns)
- Title case ONLY for the `title` metadata field
- No end punctuation (question marks allowed for FAQ headings)
- Custom anchor IDs: `## Title {#custom-id}` — use hyphens, not periods
- No duplicate heading anchor IDs in a document
- Avoid reserved anchor names: search, results, facets, pagination, sorting, query, searchbox, content, header, footer, main, navigation, sidebar, page, container, wrapper
- Follow every heading with at least one paragraph of body text (do not place lists/tables directly after a heading)
- Concept headings: noun/noun phrases
- Task headings: imperative verbs (NOT gerunds — "Create a segment" not "Creating a segment")
- Parallel structure across heading levels

### Lists
- Bullet (unordered): `*`, `-`, or `+` — use consistently within a document
- Ordered: `1.` for every item (auto-numbers)
- Blank lines before and after lists
- Indent nested numbered items 3 spaces; nested bullets 2 spaces
- Bullet punctuation: omit semicolons/commas/conjunctions at end; add periods only for complete sentences
- Do not add periods if all items are ≤3 words or are UI labels/headings

### Links
- External: `[text](https://url.com)`
- Relative (same level): `[text](file.md)`
- Root relative: `[text](/help/path/file.md)` — must start with `/`
- Deep links (same page): `[text](#heading-anchor)`
- Cross-doc deep links: `[text](file.md#heading-id)`
- Force new tab: `[text](url){target="_blank"}`
- Bare URLs: wrap in angle brackets `<https://example.com>` to make clickable
- Reference links: only absolute links work for reference-style links
- Do not include the same file in multiple TOC locations via relative links
- Windows users: convert backslashes to forward slashes in paths

### Images
- Basic: `![alt text](image.png "hover tooltip")`
- Resize: `{width="300"}`
- Align: `{align="center"}` or `{align="right"}`
- Zoomable: `{zoomable="yes"}` or `{modal="regular"}`
- Max file size: 100 MB (recommend under 5 MB)
- Alt text is REQUIRED for all images (for SEO and accessibility)
- Image filenames: lowercase with hyphens
- Store images in a designated assets folder

### Code Blocks
- Inline: backticks `` `code` ``
- Use for: filenames, URLs, user-defined terms, commands
- Fenced code blocks: triple backticks with language identifier
  ```
  ```javascript
  code here
  ```
  ```
- Options: `{line-numbers="true"}`, `{start-line="7"}`, `{highlight="11-13, 16"}`
- Always include a language identifier in fenced code blocks

### Tables
- Separator row requires at least 3 hyphens per column: `|---|---|---|`
- Alignment: left `|---|`, center `|:---:|`, right `|---:|`
- Escape literal pipes: `\|` or use `&vert;`
- HTML tables allowed; use `<table style="table-layout:auto">` or `table-layout:fixed`
- HTML table alignment: `<td align="left|center|right">`
- Avoid Markdown syntax inside HTML tables (e.g., `[!NOTE]` does not work in HTML tables)
- Remove borders: `<tr style="border: 0;">`
- Markdown table layout option: add `{style="table-layout:auto"}` after table with blank lines
- Avoid very wide/tall tables due to horizontal scrollbar visibility issues

---

## 3. SPECIAL ADOBE SYNTAX EXTENSIONS

### Callouts / Admonitions
```
>[!NOTE]
>
>Text here.

>[!TIP]
>
>Text here.

>[!IMPORTANT]
>
>Text here.

>[!WARNING]
>
>Text here.

>[!CAUTION]
>
>Text here.

>[!ADMIN]
>[!AVAILABILITY]
>[!PREREQUISITES]
>[!INFO]
>[!ERROR]
>[!SUCCESS]
```
- CRITICAL: No space between `>` and `[!` — use `>[!NOTE]` NOT `> [!NOTE]`
- Add blank line between `>[!NOTE]` and the body text line

### Tabs
```
>[!BEGINTABS]

>[!TAB iOS]
Content here

>[!TAB Android]
Content here

>[!ENDTABS]
```

### Collapsible Sections (Accordions)
```
+++Click to expand
Content inside
+++
```
Note: Nested collapsible sections are NOT supported.

### Shade Boxes
```
>[!BEGINSHADEBOX "Optional Title"]
Content here
>[!ENDSHADEBOX]
```

### Videos
```
>[!VIDEO](https://video.tv.adobe.com/v/ID/?quality=12&learn=on)
```
Add `{transcript=true}` for transcripts.

### More Like This
```
>[!MORELIKETHIS]
>* [Article 1](url)
>* [Article 2](url)
```

### Contextual Help
```
>[!CONTEXTUALHELP]
>id="..."
>title="..."
>abstract="..."
>additional-url="..."
```

### Badges (Inline)
```
[!BADGE Label]{type=Informative url="https://example.com" tooltip="text"}
```
Types: `Informative` (blue), `Positive` (green), `Negative` (red), `Neutral` (gray), `Caution` (yellow)

### Text Highlighting (Preview)
```html
<span class="preview">highlighted text</span>
```

### Includes and Snippets
- Include entire file: `{{$include /help/_includes/legal-blurb.md}}`
- Snippet (no headings): `{{snippet-id}}`
- Store reusable files in `help > _includes/` folder
- Snippets stored in `help > _includes/snippets.md`
- Includes can have headings; snippets CANNOT
- Only works within the same repository (not cross-repo)
- Escape `{{` or `}}` characters in non-referencing files

### DNL (Do Not Localize) Tag
- `[!DNL ProductName]` — wraps product/brand names that should not be translated
- Use on first or prominent mention within a page

### UICONTROL Tag
- `[!UICONTROL Button Label]` — wraps UI element text (buttons, menus, field names)
- Ensures UI strings pull from product databases rather than machine translation
- No apostrophes, quotes, or punctuation within UICONTROL tags
- Use bold formatting for UI elements referenced in steps

### Unsupported Features
- Task lists (checkboxes)
- Emoji
- Horizontal rules
- Nested collapsible sections

---

## 4. FILE NAMING & FOLDER STRUCTURE

### File Naming Rules
- Lowercase filenames with hyphens only
- No uppercase, underscores, periods, or spaces
- Descriptive, SEO-friendly names (e.g., `calculated-metric-overview.md` not `cmo.md`)
- Avoid numbers in filenames; use descriptive words
- Avoid reserved/conflicting names: `metadata.md`, `search.md`
- Renaming live files requires redirect management (URL changes)

### Folder Structure
- Directory/folder names do NOT affect URLs (only repo names and filenames affect URLs)
- TOC.md controls the navigation hierarchy, not Git folder location
- Store images/assets in a designated assets folder
- Reusable includes stored in `help/_includes/`
- Snippets stored in `help/_includes/snippets.md`

### TOC.md Rules
- Every article must be listed in TOC.md to render on Experience League
- H1 format: `# Guide Title {#anchor-id}` — anchor generates base URL path
- Section headings must have anchor IDs: `+ Section Name {#section-id}`
- Section headings (parent items) cannot be links themselves
- Article links: `+ [Title](path/file.md)`
- Changing section anchor IDs changes all nested article URLs (requires redirects)
- Use consistent bullet style throughout (`+`, `*`, or `-`)
- TOC metadata: `user-guide-description`, optionally `breadcrumb-title`
- `mini-toc-levels`: controls right-nav heading display (1-6, default 2)

---

## 5. CONTENT QUALITY & EDITORIAL STANDARDS

### Voice & Tone
- Active voice preferred over passive
- Present tense over future tense
- Second person ("you") for instructional content
- Sentences under 35 words
- Strong, precise verbs — avoid weak adverbs ("very," "extremely")

### Steps / Procedures
- Each step is ONE single, concise command (one sentence)
- Extra information goes on the next line (indented under the step)
- Start each step with an imperative verb
- Limit procedures to approximately 7 steps (max ~10 before breaking into subtasks)
- Place conceptual information BEFORE steps
- Place screenshots AFTER the relevant step
- Repeat page/tab names for reader orientation
- Bold UICONTROL formatting for UI elements in steps

### Interface Terminology
- **Open/Close**: applications and programs
- **Go to**: menus, tabs, or UI locations
- **Select**: text, cells, or options from lists
- **Click**: mouse actions (avoid specifying control type unless essential)
- **Dropdown menu** (not "dropdown list")

### Product Names
- Do not add product name to titles/headings unless clarity requires it
- Omit "the" before product names
- Include "Adobe" on first mention at guide level (trademark requirement)
- Drop "Adobe" in secondary mentions unless legally required
- Use DNL tags for product names to prevent mistranslation

### Emphasis & Formatting
- Bold: UI elements and keyboard actions
- Italics: Error messages, foreign words, emphasis
- Code (backticks): Filenames, URLs, user-defined terms
- No quotation marks around UI elements (use UICONTROL tag instead)

### Capitalization
- Sentence case for headings, navigation, subheadings
- Title case ONLY for `title` metadata field
- Proper nouns always capitalized

---

## 6. SEO BEST PRACTICES

- One H1 per page — must be concise, descriptive, tell users what the page is about
- Sequential heading hierarchy (h1 → h2 → h3, never skip levels)
- Include keywords in H1, body text, and metadata (not the `keywords` meta tag — Google ignores it)
- Avoid keyword stuffing (intent > frequency)
- Title: 50-60 chars max; system appends "| Adobe ProductName" automatically
- Description: 150-160 chars; should be a call to action, not a repeat of content
- Add descriptive alt text to all images
- Include video transcripts (search engines can only read text)
- Link strategically to related pages (avoid orphaned pages)
- Include structured elements: numbered lists, subheadings, code blocks
- Use tools like AnswerThePublic, Google Trends to research keywords
- Content should demonstrate E-E-A-T (Experience, Expertise, Authoritativeness, Trustworthiness)

---

## 7. LOCALIZATION

### Machine Translation First
- English source content auto-generates localized versions
- Supported languages: German, French, Japanese, Italian, Spanish, Brazilian Portuguese, Simplified Chinese, Traditional Chinese, Korean, Dutch, Swedish

### Writing for Localization
- Consistent terminology throughout
- Short sentences and active voice
- Standard English word order (subject → verb → object)
- Use relative pronouns ("that," "which")
- Avoid: humor, idioms, jargon, regional phrases, metaphors, unnecessary words

### Localization Tags
- `[!UICONTROL Label]` — ensures UI strings pull from product DB, not machine-translated
- `[!DNL ProductName]` — prevents product/brand names from being translated
- Images in a "do-not-localize" folder are excluded from localization

---

## 8. CONTENT TYPES

- **Guide**: Online collection of pages referenced in a TOC; covers official best practices
- **Tutorial**: Instructional content (video or text) for specific use cases; published in learn repos
- **Reference Guide**: Developer APIs/SDKs; typically table format; published to developer.adobe.com
- **Course**: Expert-curated collection of lessons targeting specific user roles
- **Knowledge Base Articles**: Brief, temporarily relevant troubleshooting content
- **Landing Page/Home Page**: Managed separately (SCCM)

---

## 9. COMMON VALIDATION ERRORS TO AVOID

- Missing or blank `title` or `description` metadata
- `description` not starting with "Learn about..." or "Learn how to..."
- Space between `>` and `[!` in callout syntax (`> [!NOTE]` instead of `>[!NOTE]`)
- Spaces in bold markers: `**text **` (trailing space breaks bold)
- Markdown syntax inside HTML tables (e.g., callouts don't work there)
- Duplicate heading anchor IDs in a document
- Anchor IDs containing periods (use hyphens instead)
- Using reserved anchor names (search, results, header, footer, etc.)
- `role`, `level`, `feature`, `topic` values that don't match YAML definitions
- Stacked headings with no body text between them
- H1 used more than once per document
- Skipped heading levels (e.g., H1 → H3)
- File naming with uppercase, underscores, or spaces
- Missing alt text on images
- Gerund task headings ("Creating..." instead of "Create...")
