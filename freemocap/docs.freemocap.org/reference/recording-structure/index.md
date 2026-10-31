# Recording folder structure | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

This page is in flux. The V2 output folder and file layout is a work in progress for version alpha. It's expected to stabilize by beta.
AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): skellylogs default_paths.py (logs in ~/skellylogs_data/logs, confirmed on the installed app; freemocap's own get_log_file_path() has no callers), useMenuActions.ts and download_sample_data.py (test data isn't bundled), blender_export_config.py (3d_models/). Fixed the log path, removed the bundled-test-data row and the migration note.

2026-08-25

freemocap v2.0.0-alpha.21 source (system/default_paths.py, system/recording_structure/recording_structure.py, api/http/mocap/mocap_router.py, core/tasks/mocap/posthoc_mocap_task.py, core/pipeline/posthoc/video_group_helper.py, core/tasks/calibration/shared/calibration_save.py), skellycam RecordingInfo and parse_video_filename, skellyforge Actor.save_out_all_data_parquet

2026-08-21

freemocap-docs architecture docs (v2.0.0-alpha.21, not yet re-checked against the running app)

More about how these docs are written

# Recording folder structure

For the narrative version of this page, see find and read your output.

## Layout​

```

~/freemocap_data/recordings/{recording_name}/

├── synchronized_videos/

│   ├── {recording_name}.id-{camera_id}.idx-{camera_index}.mp4

│   └── timestamps/

├── annotated_videos/

│   └── {video_name}_annotated.mp4

├── output_data/

│   ├── *.npy

│   ├── *.csv

│   └── *.parquet

├── 3d_models/                      # FBX/BVH, only if exported

├── tracker_schema.json

├── {recording_name}_camera_calibration.toml

├── {recording_name}_info.json

└── {recording_name}.blend            # only if exported

```

Videos recorded by FreeMoCap itself follow the {name}.id-{camera_id}.idx-{camera_index} pattern preceding; imported footage with other names (for example camera_0.mp4) is assigned cameras by filename heuristics instead.

## Defaults​

PathPurpose

~/freemocap_data/Root for all FreeMoCap data

~/freemocap_data/recordings/All recordings

~/skellylogs_data/logs/App logs

~/freemocap_data/calibrations/last_successful_camera_calibration.tomlMost recent calibration

Note that the base folder can be overridden with the FREEMOCAP_BASE_FOLDER environment variable, which the desktop shell sets when you pick a different data location.

## File purposes​

File/folderContains

synchronized_videos/Raw, time-aligned per-camera footage, plus capture-time timestamp CSVs under timestamps/

annotated_videos/Same footage with detected keypoints drawn on top, one {video_name}_annotated.mp4 per camera

output_data/*.npyPer-tracker, per-region 3D arrays, see array shapes and units

output_data/*.parquetAll trajectories combined into one tidy long-format file, freemocap_data_by_frame.parquet, see the output data model

tracker_schema.jsonkeypoint names and connections for the tracker that produced the data

{name}_camera_calibration.tomlCamera intrinsics/extrinsics used for this recording

{name}_info.jsonCamera settings at record time (resolution, exposure, framerate, rotation), plus the recording name, a UUID, and the start timestamp

{name}.blendBlender scene, present only after export

3d_models/FBX and BVH files, present only after export

- Layout

- Defaults

- File purposes
