# Repository pointers | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

core/ directory listing (annotation, config, data_primitives, detectors, io, sessions, temporal_processing, tracker, exact match) and pyproject.toml's pytest markers ("video" confirmed to exist)

2026-08-24

SkellyTracker source read directly (core package, README, CLAUDE.md, the pyproject config); FreeMoCap integration verified against FreeMoCap/core/tracking and FreeMoCap/core/pipeline in the FreeMoCap clone

More about how these docs are written

# Repository pointers

- Source layout follows the architecture preceding: skellytracker/core/{tracker,detectors,sessions,temporal_processing,data_primitives,config,io,annotation}.

- Tests: pytest skellytracker/tests (slow real-inference tests marked video; skip with -m 'not video'). Lint: ruff check skellytracker/.

- Extending: subclass KeypointDetector or ObjectDetector, register in the corresponding registry, and define the point-name/connection YAML.
