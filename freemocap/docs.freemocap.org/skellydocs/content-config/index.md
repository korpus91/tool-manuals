# The content config and landing page | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

skellydocs/src/types.ts (SkellyDocsConfig, HeroConfig, CoreFeature, GuaranteesConfig) and src/theme/IndexPage.tsx (HeroSection/FeaturesSection/GuaranteesSection exports, children prop, numbered customization-levels comment); every field in the table matches the type definitions verbatim

2026-08-24

SkellyDocs source read directly (package at 0.3.17, main); consumer usage verified in this site's package.json, Docusaurus config, custom.css, and fetched SkellyCam docs

More about how these docs are written

# The content config and landing page

A consuming repo describes its landing page in a typed content.config.tsx implementing SkellyDocsConfig:

FieldTypeNotes

heroHeroConfigtitle, accentedSuffix (rendered in the accent color), subtitle, tagline, logoSrc, parentProject (name/url, auto-linkified wherever it appears in subtitle), optional ctaButtons

featuresCoreFeature[]Each has id, icon, title, description, summary (ReactNode shown on the card), issues (LinkedIssue[]), and docPath (the card links to /docs/<docPath>)

guaranteesstring[]Legacy plain-string list

guaranteeIssuesLinkedIssue[]Legacy issues attached to the guarantees section

guaranteesConfigoptional overrideReplaces the guarantees section's title, items, and issues wholesale; takes precedence over the two legacy fields

hideSectionsoptionalArray of "hero" | "features" | "guarantees" to drop from the default layout

projectBoardUrloptionalAdds a "View full project board" link on the roadmap page

IndexPage supports three levels of customization, per its own docstring: set config fields (including the overrides preceding); pass children to replace the default section layout entirely; or skip IndexPage and import HeroSection/FeaturesSection/GuaranteesSection directly to reorder or interleave sections. Cards render their issues through LinkedIssues, and feature-card links assume the standard routeBasePath: 'docs' layout.
