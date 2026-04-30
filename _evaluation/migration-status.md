# Migration Status — Blueprints to Use Case Patterns

This document captures the state of the blueprint reorganization effort so it can be resumed cleanly across sessions.

**Last updated:** 2026-04-29

## Where we are right now

**Currently paused on:** `b2b/overview.md` (B2B section blueprint #1 of 10) — awaiting decision on whether to leave as-is, add a cross-reference to the new B2B Activation & Marketing patterns section, or update the table to list all blueprints + add cross-reference.

**To resume:** respond with **A** (leave as-is, recommended), **B** (add cross-reference), or **C** (update table + add cross-reference). Then continue with blueprint #2 (`b2b/b2bactivation.md`).

## Working approach

The current working pattern, agreed in this session, is:

1. **Keep blueprints alive** — no deprecation. Each blueprint stays in place as an architecture-focused page.
2. **Add cross-link TIP** to every blueprint with a related/overlapping use case pattern, immediately after the H1:

   ```
   >[!TIP]
   >This blueprint is also available as a [use case pattern](<absolute path>) under <Category>.
   ```

3. **Migrate diagrams** — if a blueprint has an architecture diagram that the related pattern lacks, add a `## Architecture` section to the pattern referencing the same SVG via absolute path. The asset stays in its original location (no file copies).
4. **Trim implementation steps** from the blueprint where covered in the pattern. Sections to remove typically include: `## Implementation steps`, `## Implementation patterns`, `## Implementation considerations`, sometimes `## Prerequisites`. Use judgment per-blueprint.
5. **Walk through one by one** — propose changes per blueprint, get user approval, then apply.

### Universal rules

- Cross-link TIP wording is consistent: `>This blueprint is also available as a [use case pattern](...) under <Category>.`
- New files (use case patterns created during migration) **do not include `exl-id`** — Adobe publication assigns these.
- Image references in newly authored files use absolute paths (`/help/blueprints/...`), not relative.
- Existing `exl-id` values on existing pages are preserved.
- Redirects in `redirects.csv` follow the format `source,dest` with `/en/docs/...` paths (no `.html`).

## Phases A–E (initial structural work) — COMPLETE

| Phase | Result |
| --- | --- |
| A | Created `B2B Activation & Marketing` use case pattern category. Relocated 3 existing patterns (`b2b-audience-activation` → `b2b/account-audience-activation`, `buying-group-based-marketing` → `b2b/buying-group-marketing`, `b2b-analytics` → `b2b/account-analytics`). 3 redirects added. |
| B | Copied 4 B2B blueprints to `use-case-patterns/b2b/` (`marketo-data-journeys`, `paid-media-orchestration`, `campaign-intake-and-creation`, `campaign-review-and-approval`). |
| C | Copied 4 non-B2B blueprints (`real-time-profile-lookup`, `data-science-profile-enrichment`, `edge-profile-access`, `campaign-v8-orchestration`). |
| D | Copied 2 Split blueprints (`audience-sharing-with-target`, `third-party-messaging`). |
| E | Added cross-link TIP to 9 Duplicate-classified blueprints. |

Use Case Patterns total after A–E: **26 patterns** across 6 categories.

## Section-by-section walkthrough (in progress)

The section walkthrough applies the cross-link / diagram-migration / impl-trim approach to each blueprint individually under user review.

### ✅ Audience & Profile Activation — 8/8 complete

| # | Blueprint | Action taken |
| --- | --- | --- |
| 1 | `audience-manager.md` | Cross-link TIP + diagram migrated to pattern (`anonymous-visitor-web-personalization`) + RTCDP impl steps removed |
| 2 | `enterprise-destinations.md` | Cross-link TIP + diagram migrated to pattern (`audience-activation-to-destinations`) |
| 3 | `advertising-activation.md` | Impl steps removed (99 → 35 lines) |
| 4 | `customer-activity.md` | Impl steps removed (51 → 40 lines) |
| 5 | `data-science.md` | Impl considerations removed (46 → 40 lines) |
| 6 | `real-time-lookup.md` | Prereqs + impl patterns/steps/considerations removed (156 → 73 lines) |
| 7 | `segment-match.md` | **No changes** (user opted to leave as-is) |
| 8 | `rtcdp-target.md` | Impl patterns + considerations removed (99 → 74 lines) |

### 🟡 B2B Activation & Marketing — 1/10 in progress

| # | Blueprint | Status |
| --- | --- | --- |
| 1 | `b2b/overview.md` | **PAUSED** — awaiting decision A/B/C (see "Where we are right now" above) |
| 2 | `b2b/b2bactivation.md` | Pending — Phase E Duplicate; cross-link added; needs review for diagram + impl trim |
| 3 | `b2b/b2b-account-activation.md` | Pending — Diagram-classified; needs cross-link to `b2b/account-audience-activation.md` + diagram migration consideration |
| 4 | `b2b/b2b-buying-group-journeys.md` | Pending — Phase E Duplicate; cross-link added; needs review |
| 5 | `b2b/b2b-journeys-with-marketo.md` | Pending — Phase B copy; pattern is a copy; needs impl-step trim |
| 6 | `b2b/ajo-b2b-paid-media-controller.md` | Pending — Phase B copy; needs impl-step trim |
| 7 | `b2b/marketo-engage-and-workfront-integration-blueprint/overview.md` | Pending — Section landing page |
| 8 | `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | Pending — Phase B copy; needs impl-step trim |
| 9 | `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | Pending — Phase B copy; needs impl-step trim |
| 10 | `b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md` | Pending — Links-only page (audit flagged as Navigation) |

### ⚪ Customer Journey Analytics — 0/5 not yet started

Files: `overview.md`, `b2b-cja.md` (Phase E Duplicate, cross-link added), `cja-rtcdp.md` (Group 2 — recommend cross-link to `customer-analytics-insight-generation`), `cja-ajo.md` (Group 2 — same), `analysis.md` (Group 3, possibly relocate to experience-platform/).

### ⚪ Customer Journeys — 0/14 not yet started

Files: `overview.md`; `journey-optimizer/` (4 files: overview, journeys [Phase E], campaigns [Phase E], 3rd-party-messaging [Phase D]); `decision-management/` (3 files: overview, edge [Phase E], hub [Phase E]); `campaign-v8/` (3 files: overview [Phase C], rtcdp-and-v8, ajo-and-v8); `campaign-v7/` (3 deprecated files).

### ⚪ Experience Platform — 0/6 not yet started

Files: `experience-cloud.md`, `platform-applications.md`, `platform-data-flow.md`, `guardrails.md`, `deployment/websdk.md`, `deployment/appsdk.md`. All scored as Diagram-only with 0 pattern signals in the audit. **Likely all "no change"** — they are foundational architecture that no use case pattern overlaps with.

## Reference files

| File | Purpose |
| --- | --- |
| [blueprint-audit.md](blueprint-audit.md) | Per-blueprint audit table (43 rows) with recommendations |
| [rubric.md](rubric.md) | Scoring rubric used to classify blueprints |
| [migration-redirects.csv](migration-redirects.csv) | Staged redirects from migration |
| [redirects.csv](../redirects.csv) | Canonical redirects file (3 rows added in Phase A) |

## Open questions still unresolved (from audit)

1. **Decision Management edge + hub** — both currently cross-link to `offer-decisioning`. Consider consolidating into a single deployment-options diagram?
2. **`journey-optimizer-journeys.md`** — flagged as uncertain duplicate of `event-triggered-messaging`; verify scope before trimming.
3. **`customer-journey-analytics/analysis.md`** — content is about Experience Platform Query Service, not CJA; consider relocating to `experience-platform/`.
4. **Campaign v7 (3 deprecated files)** — migrate, leave, or remove from TOC?
5. **`customer-success-stories.md`** — links-only page; confirm Navigation classification.
6. **TOC anchor** for new B2B section is `{#b2b-patterns}` — confirm before any production-redirect creation.

## How to resume

Open a new Claude Code session in this repo and say:

> Let's resume the blueprint migration. Read `_evaluation/migration-status.md` to pick up where we left off.

The next concrete step: respond to the `b2b/overview.md` decision (A/B/C). Then continue with blueprint #2 (`b2b/b2bactivation.md`) and proceed through the B2B section, then Customer Journey Analytics, Customer Journeys, and Experience Platform.
