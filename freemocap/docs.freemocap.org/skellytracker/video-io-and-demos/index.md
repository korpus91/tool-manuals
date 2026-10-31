# Video IO, annotation, and demos | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

core/io/process_video.py (process_video, process_video_list, process_folder all confirmed to exist), core/annotation/keypoint_annotator.py (confirmed to exist), and __main__.py's argparse definitions (--list, --tracker, --camera, --rotate all confirmed exact)

2026-08-24

SkellyTracker source read directly (core package, README, CLAUDE.md, the pyproject config); FreeMoCap integration verified against FreeMoCap/core/tracking and FreeMoCap/core/pipeline in the FreeMoCap clone

More about how these docs are written

# Video IO, annotation, and demos

- process_video / process_video_list / process_folder (core/io/process_video.py) run a tracker over video files and save per-video (frames, points, 3) arrays as .npy (or JSON) via DataStore. The list/folder forms open all videos simultaneously and call process_batch once per frame, a single GPU call per model per frame, suiting synchronized multi-camera recordings; they recommend creating the OnnxSession with batch_size equal to the video count.

- KeypointAnnotator (core/annotation/keypoint_annotator.py) draws any Observation given per-stage visual schemas (connections, colors, optional colored connection groups, box overlays that distinguish "detector ran" from "bbox reused"). A dedicated ChArUco annotator also exists.

- The skellytracker console script (python -m skellytracker) opens a live webcam demo: --tracker {mediapipe,rtmpose,aruco,charuco}, --camera, --rotate, --list; each detector's run_demo module exposes finer options.
