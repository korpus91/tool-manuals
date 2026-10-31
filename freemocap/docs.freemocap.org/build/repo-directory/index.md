# All repositories | FreeMoCap

Skip to main content

This page is in flux. repo directory section for FreeMoCap core is a work in progress for version alpha. It's expected to stabilize by beta.
AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

data/repos.yml's 9-repo list, tiers, routes, and GitHub URLs cross-checked against the 9 polyrepo clones; RepoDirectory, PolyrepoTree, and DataContractsTable components, the repos-data-plugin, and the stub/external docs-instance wiring in docusaurus.config.ts; the-map.md and data-contracts.md confirmed to leave out the utility tier

2026-08-24

generated live from data/repos.yml, not hand-written

More about how these docs are written

# All repositories

Every repository in the FreeMoCap polyrepo, grouped by tier, generated live from data/repos.yml at page-load time. This is the complete list, including the utility tier that the polyrepo map and data contracts pages leave out because those two are specifically about the data-flow pipeline, not the whole org.

## Core

RepoResponsibilityDomainDocsSource

💀✨ FreeMoCapPipelines. Composes the sub-skellies into one application.Anything that requires nodes from multiple sub-skelliesdocsGitHub

## Pantheon

RepoResponsibilityDomainDocsSource

💀📸 SkellyCamCameras and videoCamera device interaction, empirical measurement, raw imagesdocsGitHub

💀🔭 SkellyTrackerSingle-camera image trackingImage analysis, computer vision, convolutional neural networksdocsGitHub

💀🛠️ SkellyForge3D reconstruction and kinematic modelingMulti-camera aggregation, 3D geometry, signal processingdocsGitHub

💀🎬 SkellyBlenderBlender scene generation and animation export3D animation, .blend / .fbx / .bvh / .gltf outputdocsGitHub

## Utility

RepoResponsibilityDomainDocsSource

💀📜 SkellyLogsShared logging configuration and websocket log transportLoggingdocsGitHub

💀📡 SkellyPingsTelemetry and diagnosticsInstrumentationdocsGitHub

💀📖 SkellyDocsShared Docusaurus theme and CLI for every FreeMoCap docs siteDocumentation toolingdocsGitHub

💀🔄 SkellySyncSynchronizes videos of the same event, by audio cross-correlation or a brightness flashSynchronizationdocsGitHub

A repo without a "docs" link here doesn't have its own documentation site plugged into this build yet; its GitHub link still works, and its box on the developer docs homepage at /developers points at whatever page this build serves for that repo in the meantime.

← Architecture overview
