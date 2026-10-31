# See what you made | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): default_paths.py and skellycam default_paths.py folder names (synchronized_videos/, annotated_videos/), posthoc_mocap_task.py (output_data/), default_paths.py (freemocap_data/recordings), PlaybackPage.tsx (Open folder in file explorer), mocap_task_config.py (export_to_blender and auto_open_blend_file default true), BlenderSection.tsx (MediaPipe-only export), mocap-slice.ts (RTMPose default). Not checked against a real recording.

2026-08-25

freemocap v2.0.0-alpha.21 polyrepo clone (system/default_paths.py, core/pipeline/posthoc/video_node.py, core/blender/export_to_blender.py, core/tasks/mocap/posthoc_mocap_task.py, core/tasks/mocap/mocap_task_config.py, freemocap-ui BlenderSection.tsx), plus site link targets

2026-08-21

this site's own find-your-data.md and blender.md

More about how these docs are written

# See what you made

## Watch it back​

Open the Playback tab and select your recording. Check the tracked skeleton against your movement: points should sit on your joints and move smoothly.

## Open it in Blender​

If you recorded with the MediaPipe tracker and have Blender installed, FreeMoCap creates a Blender scene and opens it when processing finishes. If Blender doesn't open, see open your recording in Blender.

The default RTMPose tracker doesn't export to Blender yet. Its data files are still saved.

## Find the files​

Recordings are saved in the freemocap_data/recordings folder in your home folder, one folder per recording. In the Playback tab, click Open folder in file explorer to go straight there.

Inside each recording folder:

- synchronized_videos/ holds the original videos.

- annotated_videos/ holds copies with the tracked points drawn on top.

- output_data/ holds the motion capture data.

- <recording name>.blend is the Blender scene, if one was made.

See find and read your output for the full layout.

## If something looks wrong​

- Points jump around or disappear: usually lighting. See optimize your capture space.

- A multi-camera skeleton is lying down, mirrored, or the wrong size: usually calibration. See get a calibration you can trust.

A single camera can't give reliable 3D positions, however clean the tracking looks. For real 3D data, record with multiple cameras.

## Next steps​

- Where to go next

- Watch it back

- Open it in Blender

- Find the files

- If something looks wrong

- Next steps
