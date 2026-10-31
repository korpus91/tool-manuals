# Find and read your output | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

This page is in flux. Where and how your V2 output data is laid out is a work in progress for version alpha. It's expected to stabilize by beta.
AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-20

a real recording folder produced by the installed alpha.25 app on macOS (official sample data imported, MediaPipe detector, Blender export on): the folder names, the 3d_models, output_data and saved_data contents

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): on-disk names actually written today (skellycam default_paths.py synchronized_videos/ and timestamps/, freemocap default_paths.py annotated_videos/, posthoc_mocap_task.py output_data/, skeleton save_out_* npy/csv/parquet, calibration_paths.py {name}_camera_calibration.toml and calibrations/last_successful_camera_calibration.toml, blender_export_config.py 3d_models/). recording_structure.py describes a newer target layout that nothing writes yet, so it was not used. Not checked against a real recording.

2026-08-26

freemocap v2.0.0-alpha.21 code (system/default_paths.py, system/recording_structure/recording_structure.py, core/tasks/mocap/posthoc_mocap_task.py, core/pipeline/posthoc/video_node.py, api/http/playback/playback_router.py, core/blender/export_to_blender.py), skellycam RecordingInfo.save_to_file, skellyforge Actor save_out_* methods, skellylogs configure_logging and default_paths

2026-08-20

freemocap-docs architecture docs (v2.0.0-alpha.21, not yet re-checked against the running app)

More about how these docs are written

# Find and read your output

Every recording, calibration or motion capture, gets its own folder in freemocap_data/recordings in your home folder. To jump to a recording's folder, open it in the Playback tab and click Open folder in file explorer.

## What's in a recording folder​

```

freemocap_data/recordings/

└── {recording_name}/

    ├── synchronized_videos/          # Original videos, one per camera

    │   └── timestamps/               # When each frame was captured

    ├── annotated_videos/             # Videos with the tracked points drawn on

    ├── output_data/                  # The motion capture data

    │   ├── *.npy

    │   ├── *.csv

    │   └── freemocap_data_by_frame.parquet

    ├── saved_data/                   # A second copy of the data, split by body part

    ├── 3d_models/                    # FBX and BVH files, after a Blender export

    ├── tracker_schema.json           # Which points were tracked and how they connect

    ├── {name}_camera_calibration.toml

    ├── {name}_info.json              # Camera settings used for the recording

    └── {name}.blend                  # The Blender scene, after a Blender export

```

 A processed recording's folder in Finder, after a Blender export.FreeMoCap 2.0.0-alpha.25

- synchronized_videos/ holds your original footage, lined up in time across cameras.

- annotated_videos/ holds the same footage with the tracked points drawn on top. It's the quickest way to check tracking by eye.

- output_data/ holds the motion capture data in three formats: .npy for Python, .csv for spreadsheets, and freemocap_data_by_frame.parquet, which has every point of every frame in one table. See array shapes and units for what each file holds.

- saved_data/ holds a second copy of the data, split by body part into csv/ and npy/ folders, with the trajectory names and metadata in info/. Two README files in the folder explain how it is laid out.

- {name}_camera_calibration.toml is the calibration used for this recording.

- {name}.blend and 3d_models/ appear only after a Blender export.

## Other locations​

WhatWhere, in your home folder

All recordingsfreemocap_data/recordings/

Your latest calibrationfreemocap_data/calibrations/last_successful_camera_calibration.toml

Log filesskellylogs_data/logs/

## Next steps​

- Analyze your data in Python

- The FreeMoCap output data model

- Open your recording in Blender

- What's in a recording folder

- Other locations

- Next steps
