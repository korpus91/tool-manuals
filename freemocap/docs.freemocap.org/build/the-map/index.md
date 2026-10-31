# The polyrepo map | FreeMoCapCameras and videoSingle-camera image tracking3D reconstruction and kinematic modelingBlender scene generation and animation export

Skip to main content

This page is in flux. polyrepo map section for FreeMoCap core is a work in progress for version alpha. It's expected to stabilize by beta.
AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

DataFlowDiagram component (edge/order/terminal-output logic derived from consumes/produces), src/plugins/repos-data and docusaurus.config.ts wiring, data/repos.yml tier/consumes/produces values for all 9 repos, the four linked routes (/developers, /build/data-contracts, /build/repo-directory, /build/architecture), and the freemocap-composes-every-shown-repo claim against pyproject.toml at pinned tag v2.0.0-alpha.21

2026-08-24

generated live from data/repos.yml's consumes/produces fields, not hand-written

More about how these docs are written

# The polyrepo map

The developer docs homepage shows the polyrepo grouped by tier: one core app, a pantheon of pipeline-stage repos below it, and a floating set of utility repos any of them can depend on. This page shows the same repos organized a different way: by data contract, which repo's output is another repo's input, and what that data is actually called.

The diagram below isn't hand-drawn. It's built at page-load time straight from data/repos.yml's own consumes and produces fields, so if a repo's data contract changes, this page changes with it automatically the next time the site builds. Nobody edits this page directly; edit repos.yml instead.

Not consumed by another repo in the polyrepo (terminal outputs): reconstructed_points (from SkellyForge), blend_scene (from SkellyBlender).

Reading it left to right, each arrow is one named data artifact, produced by the repo on its left and consumed by the repo on its right. A repo with nothing pointing into it is a source (nothing upstream in the polyrepo feeds it); a repo whose output nothing else consumes is either a terminal output (the pipeline's actual end product) or a value only the freemocap app itself consumes directly, not another repo.

Two things this diagram deliberately leaves out, both shown instead on the developers homepage: the utility tier (SkellyLogs, SkellyPings, SkellyDocs, SkellySync), since none of them appear in any consumes/produces list, they're infrastructure the pipeline repos use internally, not stages in this data chain; and freemocap itself, which composes every repo shown here but doesn't produce or consume a named artifact of its own in repos.yml, it's the thing the chain runs inside of, not a link in it.

For the full field-by-field contract (which repo produces what, and who consumes it), see Data contracts between components. For the complete repo listing including the utility tier, see All repositories.

← Architecture overview
