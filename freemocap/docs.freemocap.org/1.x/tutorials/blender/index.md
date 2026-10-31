# Open your recording in Blender | FreeMoCap

Skip to main content

This is documentation for FreeMoCap 1.x (legacy), which is no longer actively maintained.

For up-to-date documentation, see the latest version (2.0 (alpha)).

Version: 1.x (legacy)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-20

freemocap-docs architecture docs (v2.0.0-alpha.21, not yet re-checked against the running app)

More about how these docs are written

# Open your recording in Blender

FreeMoCap can export a processed recording straight into Blender: a full 3D scene with a skeleton mesh, the camera positions from your calibration, and lighting already set up.

MediaPipe only, for now

Blender export currently works with MediaPipe mocap data only. RTMPose 3D data doesn't have a working Blender export yet.

## Before you start​

You'll need:

- Blender installed. FreeMoCap detects it automatically, or you can point it at your Blender install manually.

- A processed recording, meaning the mocap pipeline has already run and produced the required .npy files in that recording's output_data/ folder (see Find and read your output). You can't export a recording that hasn't been processed yet.

Nothing else to install: the Blender addon that builds the scene is handled automatically. It's injected into Blender at export time rather than installed into Blender's own preferences, so there's no separate addon-install step to do yourself.

## Exporting​

From the recording you want to export, click Export to Blender. FreeMoCap detects your Blender install, runs the export, and writes a .blend file into that recording's folder. You can have it open automatically in Blender's GUI when it's done, or open the .blend file yourself later.

## What actually ends up in the scene​

ElementComes from

Skeleton meshBody keypoints, connected into a skeleton

Hand meshesLeft and right hand keypoints

Face meshFace keypoints

Center of massThe whole-body center of mass trajectory

Camera frustumsYour calibration, showing where each camera actually was

Ground planeYour calibration's ground-plane alignment (Z = 0)

LightingA default three-point lighting setup

## If something goes wrong​

"Blender not detected." Install Blender from blender.org, or set the path to your install manually.

Export fails, citing missing files. The recording hasn't been fully processed yet, not every required .npy file exists. Run the mocap processing pipeline on it first.

The addon fails to load. It's injected at export time rather than installed into Blender's preferences, so this usually means the freemocap_blender_addon package itself isn't available in your Python environment, not a Blender-side problem.

## Next steps​

- Find and read your output

- The FreeMoCap output data model

- Choose a tracking model

- Before you start

- Exporting

- What actually ends up in the scene

- If something goes wrong

- Next steps
