# SkellyDocs | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

GitHub API and raw files checked 2026-10-14 (repo metadata, releases, branch comparisons), PyPI/npm metadata, and freemocap uv.lock at v2.0.0-alpha.25 for pinned commits. Added the At a glance section (role in the app, links, pinned version, install note).

2026-08-26

Re-checked package.json (version 0.3.17, dependencies, peerDependencies, engines, license field), LICENSE file, README, llms.txt, publish.yml, and src/bin usage of handlebars and prompts in polyrepo-clones/skellydocs; consumer claims against this site's package.json, docusaurus.config.ts, and data/repos.yml; resolved all eight contents links against stub-docs/skellydocs/

2026-08-24

SkellyDocs source read directly (package at 0.3.17, main); consumer usage verified in this site's package.json, Docusaurus config, custom.css, and fetched SkellyCam docs

More about how these docs are written

# SkellyDocs

@freemocap/skellydocs is the shared Docusaurus theme package and CLI for every FreeMoCap documentation site. Each repo's docs folder contains only content, markdown, images, and a thin config, while the React components, CSS design tokens, and site scaffolding come from this package. It is published to npm and part of the polyrepo's utility tier: infrastructure any of the pipeline repos can depend on. Licensing comes with a caveat: the repo contradicts itself right now, package.json and the README both say MIT, while the LICENSE file in the repository is the full GNU Affero General Public License v3 text, so the effective license is unresolved upstream.

Runtime dependencies are just handlebars and prompts (both used only by the CLI). Everything Docusaurus-related is a peer dependency: @docusaurus/core, @docusaurus/preset-classic, @docusaurus/theme-mermaid, @mdx-js/react, prism-react-renderer, and React 18 or 19. Building it requires Node >= 24.

Version note. This site's lock file installs 0.3.10. The latest version on npm is 0.3.16, and main is at 0.3.17, which isn't published yet.

## At a glance​

In the FreeMoCap app. Builds this docs site. It isn't part of the FreeMoCap app; it provides the shared theme and components for every FreeMoCap documentation site.

Codefreemocap/skellydocs

IssuesOpen issues

Package@freemocap/skellydocs on npm (latest published: 0.3.16)

Its own docsSkellyDocs' own docs site

Version this site uses0.3.10

LicenseUnresolved: package.json says MIT, the LICENSE file is AGPL-3.0

## Contents​

- How this site uses it

- What the package exports

- The content config and landing page

- The roadmap

- In-page components

- CSS design tokens

- The CLI

- Layout and development

- At a glance

- Contents
