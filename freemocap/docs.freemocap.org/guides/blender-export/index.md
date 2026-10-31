# Export to Blender | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): BlenderSection.tsx labels, MediaPipe-only gating. Troubleshooting updated for installer users; scene element table unchanged and not re-checked.

2026-08-25

polyrepo-clones/freemocap (v2.0.0-alpha.21): freemocap/core/blender/export_to_blender.py, helpers/run_blender_export.py, system/recording_status/recording_status.py, api/http/blender/blender_router.py, plus polyrepo-clones/freemocap_blender_addon main_controller.py, create_freemocap_empties.py, add_capture_cameras.py, create_lights.py

2026-08-21

freemocap-docs guides/blender-export.mdx (v2.0.0-alpha.21, not yet re-checked against the running app)

More about how these docs are written

# Export to Blender

Quick reference for Blender export. For the full walkthrough, see open your recording in Blender.

MediaPipe only, for now

Blender export only works with recordings processed with the MediaPipe tracker.

## What gets exported​

ElementSource

Skeleton meshBody keypoints

Hand meshesLeft and right hand keypoints

Face keypointsLoaded from mediapipe_face_3d_xyz.npy (one of the required input files), but not visualized in the scene

Center of massWhole-body center of mass trajectory

Camera frustumsYour calibration

Video planesYour synchronized_videos/, loaded into the scene as video planes

Ground planeA checkerboard plane at Z = 0; if your calibration didn't include groundplane alignment, the addon rotates and translates the skeleton onto the ground first

LightingNone, the export adds no light objects (it sets the viewport shading to Material Preview)

## Troubleshooting​

Blender not detected. Install it from Blender.org, or click Select Blender executable and choose it.

Export fails, missing files. The recording hasn't finished processing. Process it first; see process a recording after the fact.

## Next steps​

- Open your recording in Blender

- Process a recording after the fact

- Find and read your output

- What gets exported

- Troubleshooting

- Next steps
