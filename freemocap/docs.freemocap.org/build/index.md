# Build with FreeMoCap | FreeMoCap

Skip to main content

This page is in flux. Build section for FreeMoCap core is a work in progress for version alpha. It's expected to stabilize by beta.
AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

hub pass: every link target resolved against the local site tree (build-docs/* files, src/pages/developers.tsx, sidebars/build.ts, the build docs instance in docusaurus.config.ts, and the repos.yml generation claims behind the-map/data-contracts/repo-directory); the Design proposals blurb re-checked against the centroidal-kinematics proposal sources and the real implementation in polyrepo-clones/freemocap (core/kinematics/, freemocap/tests/kinematics/, freemocap-ui/src/components/viewport3d/) at v2.0.0-alpha.21

2026-08-24

none, this page is a hub linking to already-written pages, not sourced content itself

More about how these docs are written

# Build with FreeMoCap

Developer documentation for the freemocap core repository: how the app is put together, how it fits into the wider polyrepo, and how to build, test, and contribute to it. If you're looking for a specific sibling repo's own documentation (SkellyCam, SkellyTracker, and so on), start at the developer docs homepage instead, this section is specifically about the freemocap app itself.

## Architecture​

- Architecture overview: the FastAPI backend, the React/Electron frontend, and how they connect. Start here.

- backend architecture: pub/sub, the websocket server, calibration, and triangulation.

- frontend architecture: providers, routing, state management, and styling.

- Follow one recording end to end: realtime and posthoc pipeline topology, from camera to frontend, or video to disk.

- The polyrepo map: the data-contract pipeline across repos, generated from data/repos.yml.

- Data contracts between components: the reference table behind that map.

- All repositories: every repo in the polyrepo, including the utility tier.

## Contributing​

- Contributing to FreeMoCap

- Contributing to the docs

- Python code style

- Building and packaging

- Testing

## Design proposals​

- Design proposals: in-progress design work, part of which has already landed in the current code; the linked page tracks exactly what is built versus still proposed.

- Architecture

- Contributing

- Design proposals
