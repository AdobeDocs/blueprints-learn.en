# Migration Status â€” Blueprints to Use Case Patterns

This document captures the state of the blueprint reorganization effort so it can be resumed cleanly across sessions.

**Last updated:** 2026-09-24

## Where we are right now

The B2B section is no longer paused. Its published architecture scope is now limited to the audience/profile and account-activation pages, with retired pages redirected to the category overview.

**Current status:** The B2B architecture cleanup is complete. The audience/profile and account-activation pages remain in the architecture-diagrams category; the other B2B architecture pages were retired and redirected to the category overview.

## Working approach

> The working approach below is historical; the B2B section has since been dispositioned as recorded above.

The current working pattern, agreed in this session, is:

1. **Keep blueprints alive** â€” no deprecation. Each blueprint stays in place as an architecture-focused page.
2. **Add cross-link TIP** to every blueprint with a related/overlapping use case pattern, immediately after the H1:

   ```
   >[!TIP]
   >This blueprint is also available as a [use case pattern](<absolute path>) under <Category>.
   ```

3. **Migrate diagrams** â€” if a blueprint has an architecture diagram that the related pattern lacks, add a `## Architecture` section to the pattern referencing the same SVG via absolute path. The asset stays in its original location (no file copies).
4. **Trim implementation steps** from the blueprint where covered in the pattern. Sections to remove typically include: `## Implementation steps`, `## Implementation patterns`, `## Implementation considerations`, sometimes `## Prerequisites`. Use judgment per-blueprint.
5. **Walk through one by one** â€” propose changes per blueprint, get user approval, then apply.

### Universal rules

- Cross-link TIP wording is consistent: `>This blueprint is also available as a [use case pattern](...) under <Category>.`
- New files (use case patterns created during migration) **do not include `exl-id`** â€” Adobe publication assigns these.
- Image references in newly authored files use absolute paths (`/help/blueprints/...`), not relative.
- Existing `exl-id` values on existing pages are preserved.
- Redirects in `redirects.csv` follow the format `source,dest` with `/en/docs/...` paths (no `.html`).

## Phases Aâ€“E (initial structural work) â€” COMPLETE

| Phase | Result |
| --- | --- |
| A | Created `B2B Activation & Marketing` use case pattern category. Relocated 3 existing patterns (`b2b-audience-activation` â†’ `b2b/account-audience-activation`, `buying-group-based-marketing` â†’ `b2b/buying-group-marketing`, `b2b-analytics` â†’ `b2b/account-analytics`). 3 redirects added. |
| B | Copied 4 B2B blueprints to `use-case-patterns/b2b/` (`marketo-data-journeys`, `paid-media-orchestration`, `campaign-intake-and-creation`, `campaign-review-and-approval`). |
| C | Copied 4 non-B2B blueprints (`real-time-profile-lookup`, `data-science-profile-enrichment`, `edge-profile-access`, `campaign-v8-orchestration`). |
| D | Copied 2 Split blueprints (`audience-sharing-with-target`, `third-party-messaging`). |
| E | Added cross-link TIP to 9 Duplicate-classified blueprints. |

Use Case Patterns total after Aâ€“E: **26 patterns** across 6 categories.

## Section-by-section walkthrough (in progress)

The section walkthrough applies the cross-link / diagram-migration / impl-trim approach to each blueprint individually under user review.

### âœ… Audience & Profile Activation â€” 8/8 complete

| # | Blueprint | Action taken |
| --- | --- | --- |
| 1 | `audience-manager.md` | Cross-link TIP + diagram migrated to pattern (`anonymous-visitor-web-personalization`) + RTCDP impl steps removed |
| 2 | `enterprise-destinations.md` | Cross-link TIP + diagram migrated to pattern (`audience-activation-to-destinations`) |
| 3 | `advertising-activation.md` | Impl steps removed (99 â†’ 35 lines) |
| 4 | `customer-activity.md` | Impl steps removed (51 â†’ 40 lines) |
| 5 | `data-science.md` | Impl considerations removed (46 â†’ 40 lines) |
| 6 | `real-time-lookup.md` | Prereqs + impl patterns/steps/considerations removed (156 â†’ 73 lines) |
| 7 | `segment-match.md` | **No changes** (user opted to leave as-is) |
| 8 | `rtcdp-target.md` | Impl patterns + considerations removed (99 â†’ 74 lines) |

### ðŸŸ¡ B2B Activation & Marketing â€” 1/10 in progress

| # | Blueprint | Status |
| --- | --- | --- |
| 1 | `b2b/overview.md` | Completed - B2B category overview updated |
| 2 | `b2b/b2bactivation.md` | Retired - replaced by the architecture-diagrams audience/profile page |
| 3 | `b2b/b2b-account-activation.md` | Retained - migrated to the architecture-diagrams B2B category |
| 4 | `b2b/b2b-buying-group-journeys.md` | Retired |
| 5 | `b2b/b2b-journeys-with-marketo.md` | Retired |
| 6 | `b2b/ajo-b2b-paid-media-controller.md` | Retired |
| 7 | `b2b/marketo-engage-and-workfront-integration-blueprint/overview.md` | Retired |
| 8 | `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | Retired |
| 9 | `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | Retired |
| 10 | `b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md` | Retired |

### âšª Customer Journey Analytics â€” 0/5 not yet started

Files: `overview.md`, `b2b-cja.md` (Phase E Duplicate, cross-link added), `cja-rtcdp.md` (Group 2 â€” recommend cross-link to `customer-analytics-insight-generation`), `cja-ajo.md` (Group 2 â€” same), `analysis.md` (Group 3, possibly relocate to experience-platform/).

### âšª Customer Journeys â€” retirement cleanup complete; retained-page migration pending

Files: `overview.md`; `journey-optimizer/` (4 files: overview, journeys [Phase E], campaigns [Phase E], 3rd-party-messaging [Phase D]); `campaign-v8/` (3 files: overview [Phase C], rtcdp-and-v8, ajo-and-v8). `decision-management/` and `campaign-v7/` are fully retired; their historical entries remain in the audit and their URLs redirect to the approved overview pages.

### âšª Experience Platform â€” 0/6 not yet started

Files: `experience-cloud.md`, `platform-applications.md`, `platform-data-flow.md`, `guardrails.md`, `deployment/websdk.md`, `deployment/appsdk.md`. All scored as Diagram-only with 0 pattern signals in the audit. **Likely all "no change"** â€” they are foundational architecture that no use case pattern overlaps with.

The Decision Management and Campaign v7 retirement decisions are complete. Their related open questions
are historical only and should not block the remaining migration work.

## Reference files

| File | Purpose |
| --- | --- |
| [blueprint-audit.md](blueprint-audit.md) | Per-blueprint audit table (43 rows) with recommendations |
| [rubric.md](rubric.md) | Scoring rubric used to classify blueprints |
| [migration-redirects.csv](migration-redirects.csv) | Staged redirects from migration |
| [redirects.csv](../redirects.csv) | Canonical redirects file (3 rows added in Phase A) |

## Open questions still unresolved (from audit)

2. **`journey-optimizer-journeys.md`** â€” flagged as uncertain duplicate of `event-triggered-messaging`; verify scope before trimming.
3. **`customer-journey-analytics/analysis.md`** â€” content is about Experience Platform Query Service, not CJA; consider relocating to `experience-platform/`.
4. **`customer-success-stories.md`** â€” links-only page; confirm Navigation classification.
5. Historical TOC-anchor question superseded by the completed B2B architecture disposition.

## How to resume

Open a new Claude Code session in this repo and say:

> Let's resume the blueprint migration. Read `_evaluation/migration-status.md` to pick up where we left off.

The B2B architecture cleanup is complete. Continue with the next planned architecture category after validation.
