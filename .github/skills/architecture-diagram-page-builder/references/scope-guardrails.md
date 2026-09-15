# Scope guardrails: architecture page vs. use case pattern page

The blueprints site separates **architecture diagram pages** from **use case pattern pages** because they serve different reader needs. This document defines what belongs where and how to handle content that drifts across the boundary.

## The core distinction

- **Architecture diagram pages** are top-level visual references. They answer: *"How do these systems fit together? Where are the integration points? What is the shape of the data flow?"* Readers come here to orient themselves.
- **Use case pattern pages** are implementation guides. They answer: *"How do I build this capability? What functions are involved? What KPIs measure success? What are my implementation options?"* Readers come here when they have a use case and need to ship it.

## Belongs on an architecture page

| Category | Examples |
| --- | --- |
| Top-level architecture | Overview diagrams of AEP and applications, Experience Cloud marketecture, hub vs. edge topology |
| System data flow | Real-time vs. batch ingest paths, profile sync between hub and edge, lookup vs. activation flows |
| Integration points | Where AEP integrates with AJO, CJA, Target, Campaign, Marketo, Workfront; SDK boundaries; API surfaces |
| Deployment topology | Web SDK vs. Mobile SDK deployment, server-side forwarding, edge node placement |
| Application architecture | How a single application (AJO, CJA, RTCDP) is internally structured at a system level |
| Pointers to use case patterns | "This architecture supports patterns X, Y, Z" with links -- the architecture page does **not** duplicate that content |

## Does NOT belong on an architecture page

If you find yourself writing any of the following, redirect to a use case pattern page (use the `use-case-pattern-builder` skill):

| Category | Why it belongs elsewhere |
| --- | --- |
| KPIs and measurement formulas | Use case patterns measure outcomes; architecture pages don't |
| Business objectives, business impact | KBO content lives under `/help/blueprints/business-objectives/`; patterns reference it |
| Tactical use case examples | "Cart abandonment reminder", "Personalized homepage hero", etc. -- these are pattern content |
| Capabilities (`A > B > C > D`) | The capabilities construct is part of the use case pattern template |
| Persona narratives | "Maria the marketer wants to..." style scenarios belong in patterns, not architecture refs |
| Implementation options | Multi-option implementation guidance (Best for, How it works, Advantages, Limitations) is a pattern construct |
| Foundational/supporting function tables | These are pattern-page sections |
| Prerequisite checklists per use case | Patterns track these; architecture pages link to patterns instead |

## Trigger phrases to watch for

If the user provides any of these phrases when describing the new page, pause and re-check scope:

- "KPIs"
- "business impact" / "business outcomes"
- "tactical use cases" / "example scenarios"
- "capabilities"
- "implementation options"
- "best for"
- "advantages and limitations"
- "prerequisites"
- "personas" / "stakeholders"
- "measurement"

These do not automatically disqualify the page -- but they signal that the user may want a use case pattern page, not an architecture page. Confirm intent before generating.

## What to do when content drifts

1. **Identify the drift.** Point to the specific section or bullet that crossed the boundary.
2. **Offer two options to the user:**
   - Trim the section from the architecture page (most common -- keeps the architecture page focused).
   - Stop and switch to `use-case-pattern-builder` for that content (when the user actually wants a pattern page).
3. **Wait for confirmation.** Do not silently rewrite or drop content.
4. **If keeping architecture-only content**, replace the deep content with a single bullet under `## Use case patterns supported` linking to the relevant pattern (existing or to-be-created).

## Edge cases

- **Page is half architecture, half pattern.** Split into two pages -- one architecture page (this skill), one use case pattern page (the `use-case-pattern-builder` skill). Cross-link them.
- **Architecture page describes a single use case end-to-end.** That is a use case pattern, not an architecture page. Redirect to `use-case-pattern-builder`.
- **Architecture page needs to show example data flows for one specific scenario.** Acceptable if the scenario is illustrative only and the bulk of the page stays at the system-architecture level. Keep the example to one paragraph and link out to the relevant pattern for full detail.

## Quick test

Before generating, ask: *"If a reader lands on this page expecting a top-level architecture reference, will they get one -- or will they get a half-finished use case walkthrough?"* If the latter, the page belongs in `use-case-pattern-builder`.
