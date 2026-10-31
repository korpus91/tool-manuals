# Recording folder structure | FreeMoCap

Skip to main content

This is documentation for FreeMoCap 1.x (legacy), which is no longer actively maintained.

For up-to-date documentation, see the latest version (2.0 (alpha)).

Version: 1.x (legacy)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-21

freemocap-docs architecture docs (v2.0.0-alpha.21, not yet re-checked against the running app)

More about how these docs are written

# Recording folder structure

For the narrative version of this page, see find and read your output.

## Layout​

```

~/freemocap_data/recordings/{recording_name}/

├── synchronized_videos/

│   └── camera_{n}.mp4

├── annotated_videos/

│   └── camera_{n}_annotated.mp4

├── output_data/

│   ├── *.npy

│   ├── *.csv

│   └── *.parquet

├── logs/

├── {recording_name}_camera_calibration.toml

├── {recording_name}_recording_info.json

└── {recording_name}.blend            # only if exported

```

A videos/synchronized/, videos/annotated/, output/ layout is the migration target in the codebase; both layouts validate today, but the names above are what a current recording actually produces.

## Defaults​

PathPurpose

~/freemocap_data/Root for all FreeMoCap data

~/freemocap_data/recordings/All recordings

~/freemocap_data/recordings/freemocap_test_data/Bundled test recording

~/freemocap_data/logs_info_and_settings/logs/Application logs

~/freemocap_data/calibrations/last_successful_camera_calibration.tomlMost recent calibration

## File purposes​

File/folderContains

synchronized_videos/Raw, time-aligned per-camera footage

annotated_videos/Same footage with detected keypoints drawn on top

output_data/*.npyPer-tracker, per-region 3D arrays, see array shapes and units

output_data/*.parquetThe same data in tidy long format, see the output data model

{name}_camera_calibration.tomlCamera intrinsics/extrinsics used for this recording

{name}_recording_info.jsonCamera settings at record time, and whether this was tagged calibration or mocap

{name}.blendBlender scene, present only after export

- Layout

- Defaults

- File purposes
