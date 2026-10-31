# Developer documentation | FreeMoCapFreeMoCapSkellyCamSkellyTrackerSkellyForgeSkellyBlenderSkellyLogsSkellyPingsSkellyDocsSkellySync

Skip to main content

# FreeMoCap

Developer documentation for the FreeMoCap project.

FreeMoCap is a polyrepo where freemocap/freemocap is the application, which composes a set of independent libraries rather than containing them. Each one owns a stage of the pipeline: SkellyCam produces synchronized frame packages, SkellyTracker turns those into keypoint observations, SkellyForge turns those into reconstructed points and kinematic models, and SkellyBlender turns those into an animated scene. These are organized into a core layer for the application, a pantheon of supporting repos in parallel below that, and a suite of utility repos that support the whole pipeline, as shown in the tree diagram below. Support repositories in the pantheon layer communicate through the data contract, while utility repos are infrastructure handling logging, docs tooling, telemetry, sync, etc. from which any part of the pipeline can draw.

Sort of like this.
Like the Defender of the Universe, the head and body are the primary core, but it does not function without the arms and legs. Splitting a codebase this way trades a single build for independent, freely-releasable pieces, at the cost of needing an explicit way (like the tiers and data contracts above) to track which versions of each actually work together.

In practice, each entry in FreeMoCap's own repo map connects to a specific git tag instead of a branch, so a change merged into one repo can't break the others until someone deliberately moves the pin forward. This allows a manifest to decide what's actually compatible rather than memory.

Architecture docsFull repository directoryGitHub organization
