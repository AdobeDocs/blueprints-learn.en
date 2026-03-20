---
name: use-case-icon-generator
description: Generate icon specifications and image generation prompts for use case icons in the Adobe Experience Platform blueprints repository. Use this skill when creating icons for new industry use cases, when the industry-use-case-builder skill needs an icon, or when the user asks about creating or updating use case icons. Outputs a detailed image generation prompt the user can use with Midjourney, DALL-E, Adobe Firefly, or similar tools, along with the correct file naming and placement.
---

# Use Case Icon Generator

Generate detailed icon specifications and AI image generation prompts for use case icons in the blueprints repository.

## When to Use This Skill

- Creating a new use case that needs an icon
- Called by the industry-use-case-builder skill to generate an icon spec
- User asks about creating, updating, or replacing a use case icon
- User wants to generate a batch of icons for a new industry vertical

## Step 1: Collect Inputs

Gather the following information from the user or from the calling skill:

**Required:**
- **Use case name** — The human-readable name of the use case (e.g., "Abandoned Cart", "Lead Scoring")
- **Industry vertical** — One of: automotive, b2b, financial-services, healthcare, insurance, media-entertainment, retail, telecommunications, travel-hospitality
- **Brief description** — 1-2 sentences describing what the use case does

**Optional:**
- **Preferred visual metaphor or subject** — If the user has a specific idea for what the icon should depict

If any required input is missing, ask the user before proceeding.

## Step 2: Read the Style Guide

Read the file `references/icon-style-guide.md` (relative to this skill's directory) to load the complete style guide, including:

- Technical specifications
- Visual style guidelines
- Visual metaphor examples by industry
- The prompt template
- The existing icon inventory

Use the style guide to ensure consistency with existing icons.

## Step 3: Generate the Icon Specification

Produce all three parts of the icon specification:

### A. File Specification

Derive the filename and path from the use case name and industry:

- **Filename:** `icon-{kebab-case-name}.png`
  - Convert the use case name to kebab-case (lowercase, hyphens for spaces)
  - Examples: "Abandoned Cart" becomes `icon-abandoned-cart.png`, "Cross-Sell Upsell" becomes `icon-cross-sell-upsell.png`
- **Path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/{industry}/`
- **Dimensions:** 1024 x 1024 pixels
- **Format:** PNG, 8-bit RGB or RGBA
- **Target file size:** 900KB - 1.4MB

### B. Image Generation Prompt

Create a detailed, copy-ready prompt for AI image generation tools. The prompt must:

1. **Describe a clear visual metaphor** — Choose a single, strong visual metaphor that immediately communicates the use case concept. If the user provided a preferred metaphor, use it. Otherwise, select one based on the style guide examples and the use case description.

2. **Specify the artistic style** — Include these style directives:
   - Clean, modern icon illustration style
   - Professional corporate design aesthetic
   - Bold shapes and clean lines
   - Polished, rendered finish (not photorealistic)
   - Consistent with a unified design system

3. **Include technical specifications:**
   - Square format, 1024x1024 pixels
   - Single centered subject
   - Solid or subtle gradient background
   - High contrast between subject and background

4. **Enforce small-size legibility:**
   - No text or lettering of any kind
   - No fine details or intricate patterns
   - No complex backgrounds or multi-element scenes
   - Bold silhouette that reads clearly at 40px
   - Strong shape recognition even without color

5. **Guide the color palette:**
   - Professional, corporate-appropriate colors
   - Vibrant but refined (not neon or overly saturated)
   - High contrast for accessibility
   - Cohesive with other icons in the same industry vertical

Structure the prompt as a single paragraph, ready to paste into any image generation tool.

### C. Catalog Reference Snippet

Generate the HTML snippet for use in the catalog table:

```
<img src="assets/use-case-icons/{industry}/icon-{name}.png" alt="{Alt Text}" width="40">
```

Where `{Alt Text}` is the human-readable use case name.

## Step 4: List Existing Icons in the Same Industry

Check the style guide's existing icon inventory section and list all current icons for the same industry. This helps the user:
- Ensure visual consistency when generating the new icon
- Avoid duplicating an icon that already exists
- Reference existing icons as style examples

## Step 5: Present the Output

Format the output clearly with these sections:

---

### Icon Specification: {Use Case Name}

**Industry:** {Industry}

**File Details:**
- Filename: `icon-{kebab-case-name}.png`
- Path: `/help/blueprints/industry-use-cases/assets/use-case-icons/{industry}/`
- Dimensions: 1024 x 1024 pixels
- Format: PNG (8-bit RGB/RGBA)

**Image Generation Prompt:**

> {The complete, detailed prompt — formatted as a blockquote so it is easy to copy}

**Catalog HTML:**

```html
<img src="assets/use-case-icons/{industry}/icon-{name}.png" alt="{Use Case Name}" width="40">
```

**Existing Icons in {Industry}:**
- {list of existing icon names}

**Next Steps:**
1. Copy the image generation prompt above.
2. Paste it into your preferred image generation tool (Adobe Firefly, Midjourney, DALL-E, or similar).
3. Generate the image and select the best result.
4. Resize/export to exactly 1024x1024 pixels if needed.
5. Save as `{filename}` in the path shown above.
6. Verify the icon looks clear and recognizable at 40px display size.
7. Use the catalog HTML snippet when adding this use case to the catalog table.

---

## Guidelines

- **Never generate the actual image** — This skill produces the specification and prompt only. The user must use an external image generation tool.
- **One icon per use case** — Each use case gets exactly one icon.
- **Check for duplicates** — If an icon with the same or very similar name already exists in the inventory, warn the user.
- **Prioritize legibility** — When in doubt between a detailed metaphor and a simple one, always choose the simpler option that reads well at 40px.
- **Be specific in prompts** — Vague prompts produce inconsistent results. Include concrete visual details (e.g., "a shopping cart with two colorful boxes inside" rather than "a shopping concept").
- **Avoid cliches when possible** — Try to find fresh but still immediately recognizable visual metaphors. A lightbulb for every "smart" use case gets repetitive.
