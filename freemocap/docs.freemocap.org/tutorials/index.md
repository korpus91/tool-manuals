# Tutorials | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-09-21

prose cleanup, replaced a mid-paragraph colon with two sentences per explicit instruction; heading colons (Tier 1: the basics, etc.) left as-is, that's the same title-colon-subtitle pattern as the sidebar's own tier labels, not the sentence-level tic being corrected

2026-09-21

src/data/sitePages.ts's tutorialTiers; Tier 3's two entries point to real pages (/tutorials/specialization-tracks, /tutorials/skelly-university) rather than the homepage's `/#advanced` anchor, which was explicitly rejected in favor of standalone explainer pages

2026-09-20

src/data/sitePages.ts's tutorialTiers, added back a non-tutorial Tier 3: Advanced pointing at the homepage's Advanced section (src/pages/index.tsx) and Skelly University; specialization track descriptions cross-checked against that section's Technology/Science/Art PathGroups

2026-09-19

src/data/sitePages.ts's tutorialTiers, merged to two tiers to match the homepage Intermediate tile grid (src/pages/index.tsx); page list, order, and titles cross-checked against that array

2026-08-26

Cross-checked the three tiers against tutorialTiers in src/data/sitePages.ts (navbar flyout and footer) and sidebars/sharedDocsTree.ts (sidebar TOC); verified all 14 child pages exist under docs/tutorials/ with titles matching their link text and no slug overrides; confirmed the /tutorials/ and /concepts/ routes resolve via docusaurus.config.ts routeBasePath settings

2026-08-21

not checked against a specific version

More about how these docs are written

# Tutorials

Three tiers, roughly in order. Tier 1 gets you from nothing to a working multi-camera recording. Tier 2 is everything past that. It covers a trustworthy calibration, choosing a tracker, cleaning your data, and going further with the data or the pipeline itself. Tier 3 isn't more tutorials. It's where they stop and FreeMoCap splits into three specialization tracks.

## Tier 1: the basics​

- Choose and set up your cameras

- Record with one camera

- Calibrate your cameras

- Record with multiple cameras

- Find and read your output

- Open your recording in Blender

## Tier 2: past the basics​

- Get a calibration you can trust

- Set the ground plane

- Choose a tracking model

- Filter and fill your data

- Optimize your capture space

- Analyze your data in Python

- Build a custom pipeline

- Process many recordings at once

## Tier 3: advanced​

- Specialization tracks

- Skelly University

If you want to go past tutorials and tracks into the codebase itself, see the Developer Docs.

If you'd rather understand why any of this works the way it does, that's what concepts is for.

- Tier 1: the basics

- Tier 2: past the basics

- Tier 3: advanced
