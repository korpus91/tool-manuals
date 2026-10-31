# Multi-person tracking | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

core/temporal_processing/multi_person_config.py: iou_weight=0.5, keypoint_weight=0.5, max_age=10, min_hits=3 all confirmed exact

2026-08-24

SkellyTracker source read directly (core package, README, CLAUDE.md, the pyproject config); FreeMoCap integration verified against FreeMoCap/core/tracking and FreeMoCap/core/pipeline in the FreeMoCap clone

More about how these docs are written

# Multi-person tracking

MultiPersonTracker (core/tracker/multi_person_tracker.py) extends the same stage machinery to several people: the root stage's object detector runs every frame to propose candidates, candidates are matched to existing PersonTrackStates by Hungarian assignment on a cost blending bbox IoU and keypoint displacement (MultiPersonTrackingConfig: weights 0.5/0.5, max_age 10, min_hits 3), and matched detections are finalized with each track's own accumulated temporal state. Unmatched detections spawn new tracks; unmatched tracks age out.

FreeMoCap does not use this today, its configs cap detections to one crop per camera, with an in-source comment explaining that a fixed batch size prevents intermittent GPU OOMs from spurious detections.
