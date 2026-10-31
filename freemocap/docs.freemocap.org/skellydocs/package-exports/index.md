# What the package exports | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

skellydocs main re-read: full src/index.ts export list, all 12 shared types in src/types.ts, every theme component source (IndexPage with HeroSection/FeaturesSection/GuaranteesSection, RoadmapPage, RoadmapContent, RoadmapEntry, Tip, LinkedIssues, AiGeneratedBanner, CoreFeatureHeader, collectLinkedUrls), package.json version 0.3.17 and its css subpath exports map, plus consumption verified in this site's docusaurus.config.ts and external/skellycam/content.config.tsx

2026-08-24

SkellyDocs source read directly (package at 0.3.17, main); consumer usage verified in this site's package.json, Docusaurus config, custom.css, and fetched SkellyCam docs

More about how these docs are written

# What the package exports

The entry point (src/index.ts) re-exports everything below plus the shared TypeScript types.

ExportKindPurpose

IndexPageComponentFull landing page: hero, feature cards, guarantees

HeroSection, FeaturesSection, GuaranteesSectionComponentsThe individual landing-page sections, for compose-it-yourself layouts

RoadmapPageComponent/roadmap route wrapper around RoadmapContent

RoadmapContentComponentThe roadmap dashboard: fetch, cache, filter, search, sort, grid/list views

RoadmapEntryComponentA single roadmap card

TipComponentInline tooltip, CSS-only hover or two-stage progressive disclosure

LinkedIssuesComponentCollapsible list of GitHub issues/PRs with badges, enriched live

AiGeneratedBannerComponentCollapsible AI-content disclaimer banner

CoreFeatureHeaderComponentSummary-plus-linked-issues block for feature doc pages

collectLinkedUrlsFunctionExtracts every unique issue/PR URL from a content config

./css/custom.css, ./css/theme.module.cssCSSDesign tokens and component styles, exported from source
