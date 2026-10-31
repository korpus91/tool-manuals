# SkellyTracker | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

GitHub API and raw files checked 2026-10-14 (repo metadata, releases, branch comparisons), PyPI/npm metadata, and freemocap uv.lock at v2.0.0-alpha.25 for pinned commits. Added the At a glance section (role in the app, links, pinned version, install note).

2026-08-26

skellytracker/core/ package structure and __init__.py's beartype_this_package() call, confirmed directly; the Tracker/Session/DetectionStage architecture claims cross-checked against tracker/tracker.py

2026-08-24

SkellyTracker source read directly (core package, README, CLAUDE.md, the pyproject config); FreeMoCap integration verified against FreeMoCap/core/tracking and FreeMoCap/core/pipeline in the FreeMoCap clone

More about how these docs are written

# SkellyTracker

SkellyTracker is the single-camera image tracking backend for FreeMoCap. It turns raw images into named 2D keypoints and bounding boxes. It wraps several independent computer-vision tools behind one consistent API built around a Tracker → Session → Detector pipeline, implemented in the skellytracker/core/ package. Part of the FreeMoCap polyrepo's pantheon tier.

It serves two distinct jobs for the pipeline:

- Human pose estimation, MediaPipe (pose/hands/face) or RTMPose + YOLOX produce whole-body keypoints per frame.

- Calibration marker detection, ArUco and ChArUco board detection produce the corner observations FreeMoCap's multi-camera calibration solves against.

Everything operates on single images or batches of images. SkellyTracker knows nothing about cameras, synchronization, recording, or 3D math. SkellyCam supplies frames, and FreeMoCap triangulates the output. Package-wide runtime type checking is enabled via beartype_this_package() in skellytracker/__init__.py.

## At a glance​

In the FreeMoCap app. Finds the body in every camera frame. Each time FreeMoCap processes a recording, SkellyTracker spots the person, locates their joints (with RTMPose or MediaPipe), and detects the ChArUco board during calibration. Choosing a tracker in the app picks which SkellyTracker detector runs. See choose a tracking model.

Codefreemocap/skellytracker

IssuesOpen issues

Version in FreeMoCap alpha.256310005 on main

InstallFreeMoCap installs it from GitHub. The PyPI package is an older, separate release; for the current code use uv add git+https://github.com/freemocap/skellytracker

LicenseAGPL-3.0

## Contents​

- Architecture

- Data model

- Built-in detectors

- Temporal processing

- Multi-person tracking

- Video IO, annotation, and demos

- Install extras and hardware

- How FreeMoCap uses SkellyTracker

- Repository pointers

- At a glance

- Contents
