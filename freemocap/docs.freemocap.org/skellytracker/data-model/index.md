# Data model | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

core/data_primitives/keypoints.py (names/xyz/visibility fields and shapes confirmed exact, including the x,y-pixels/z-filled-by-triangulation comment) and observation.py (to_keypoints() confirmed to exist)

2026-08-24

SkellyTracker source read directly (core package, README, CLAUDE.md, the pyproject config); FreeMoCap integration verified against FreeMoCap/core/tracking and FreeMoCap/core/pipeline in the FreeMoCap clone

More about how these docs are written

# Data model

- Keypoints (core/data_primitives/keypoints.py), named points: .names tuple, .xyz (N, 3) (x,y in pixels; z filled by triangulation later), .visibility (N,) scores in 0-1. Undetected points are NaN with visibility 0. Provides name-based lookup, slicing, concatenation, confidence masking, and translation.

- BoundingBox, x1y1x2y2 plus confidence, with crop/clamp/scaling helpers.

- StageObservation / Observation (core/data_primitives/observation.py), per-frame result. observation.stages["name"].keypoints returns a stage's Keypoints; children nest under .children. Observation.to_keypoints() flattens the whole stage tree into one Keypoints with <stage>.<point> name prefixes, the docstring calls this "the form passed to FreeMoCap for triangulation."

- TrackerState (core/tracker/tracker_state.py), the explicit external temporal state: per-stage StageState holding bbox smoothing state, per-detector keypoint filter states, last keypoints, and consecutive miss/reset counters.
