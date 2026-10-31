# Export to Blender | FreeMoCap

Skip to main content

This is documentation for FreeMoCap 1.x (legacy), which is no longer actively maintained.

For up-to-date documentation, see the latest version (2.0 (alpha)).

Version: 1.x (legacy)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-21

freemocap-docs guides/blender-export.mdx (v2.0.0-alpha.21, not yet re-checked against the running app)

More about how these docs are written

# Export to Blender

Quick reference for Blender export. For the full walkthrough, see open your recording in Blender.

MediaPipe only, for now

RTMPose 3D data doesn't have a working Blender export yet.

## What gets exported​

ElementSource

Skeleton meshBody keypoints

Hand meshesLeft and right hand keypoints

Face meshFace keypoints

Center of massWhole-body center of mass trajectory

Camera frustumsYour calibration

Ground planeYour calibration's ground-plane alignment (Z = 0)

LightingDefault three-point setup

## Troubleshooting​

Blender not detected. Install from blender.org, or set the path manually.

Export fails, missing files. The recording isn't fully processed, not every required .npy file exists yet. Run mocap processing first, see process a recording after the fact.

Addon fails to load. The addon is injected at export time, not installed into Blender's own preferences, so this usually means freemocap_blender_addon isn't available in your Python environment rather than a Blender-side issue.

## Next steps​

- Open your recording in Blender

- Process a recording after the fact

- Find and read your output

- What gets exported

- Troubleshooting

- Next steps
