# Contributing to the docs | FreeMoCap

Skip to main content

This page is in flux. Docs contribution section for FreeMoCap core is a work in progress for version alpha. It's expected to stabilize by beta.
Human-checked documentationchecked against source

This page is adapted from real, human-written FreeMoCap documentation. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-27

this site's own repo (freemocap/freemocap.github.io): README.md, .github/workflows/deploy.yml triggers and CI steps, package.json scripts, docusaurus.config.ts docs instances, and data/redirects.js

2026-08-19

v1 (ported, not yet re-checked against v2)

More about how these docs are written

# Contributing to the docs

The docs are plain Markdown in the freemocap.github.io repository, built with Docusaurus. Any text editor works. Every page has an Edit this page link that opens its file on GitHub.

## Where pages live​

SectionFolder

Start, tutorials, guides, reference, aboutdocs/

Conceptsconcepts/

Build (developer docs)build-docs/

SkellyCamfetched from the skellycam repo at build time

## Make a change​

- Fork the repository (outside the FreeMoCap organization) or create a branch (inside it).

- Edit the Markdown. To preview, run npm install, npm run fetch, then npm start (Node.js 22 recommended). See Docusaurus Markdown features.

- Keep each page's frontmatter current: provenance, plus a history entry with today's date and what you checked the page against.

- Open a pull request into main. The build runs on the PR, and a broken internal link fails it.

- Once merged, the site updates by itself within a few minutes.

For the Git workflow itself, see Contributing to FreeMoCap.

## Moving or renaming a page​

Add the old URL to data/redirects.js so existing links keep working.

- Where pages live

- Make a change

- Moving or renaming a page
