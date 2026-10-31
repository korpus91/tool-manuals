# Open your recording in Blender | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): BlenderSection.tsx and mocap-blender-settings.tsx (Select Blender executable, Export to Blender after mocap processing, Auto-open .blend file, Process Recording with Blender, MediaPipe-only gating), blender_export_config.py (FBX/BVH into 3d_models, T-pose/A-pose, foot locking, hand range of motion), blender_router.py /export (detector now detected, so the alpha.21 manual-export bug is fixed; alpha.24 release notes agree), mocap_task_config.py defaults. Rewritten; not checked against a real export.

2026-08-26

freemocap-ui BlenderSection.tsx, blender-thunks.ts, server-urls.ts, and api/http/blender/blender_router.py + core/blender/export_to_blender.py at v2.0.0-alpha.21: found the manual export button's real label and a real bug (blenderExport always omits the required detector argument, confirmed against the endpoint's own signature)

2026-08-20

freemocap-docs architecture docs (v2.0.0-alpha.21, not yet re-checked against the running app)

More about how these docs are written

# Open your recording in Blender

FreeMoCap can turn a processed recording into a Blender scene with an animated skeleton. It also saves the animation as FBX and BVH files you can use in other 3D software.

MediaPipe only, for now

Blender export only works with recordings processed with the MediaPipe tracker. Choose it under Mocap Settings > Detector before you record or process.

## Before you start​

Install Blender. FreeMoCap finds it automatically. If it doesn't, click Select Blender executable in the Blender settings and choose your Blender app.

## Export automatically​

With Export to Blender after mocap processing turned on (it's on by default), FreeMoCap makes the Blender scene every time it finishes processing a MediaPipe recording. With Auto-open .blend file in Blender when done on, the scene opens in Blender straight away.
 The exported scene in Blender, with the skeleton, the ground plane and the camera videos.FreeMoCap 2.0.0-alpha.25

## Export a recording you already processed​

Open the recording in the Playback tab and click Continue to Mocap Setup. In the Blender settings, click Process Recording with Blender.

## Export options​

In the Blender settings you can choose:

- The files to make (FBX, BVH, or both). They're saved in the recording's 3d_models folder.

- The skeleton's rest pose: T-pose or A-pose.

- Apply Foot Locking, to stop feet sliding on the floor.

- Limit Hand Markers Range of Motion, to keep fingers from bending unnaturally.

 The Blender settings in Mocap Settings.FreeMoCap 2.0.0-alpha.25

## Where the files go​

The .blend file is saved in the recording's folder, named after the recording. See find and read your output.

## If something goes wrong​

- Blender isn't found: install Blender, or click Select Blender executable and choose it.

- The export option is greyed out: the recording used RTMPose. Switch Detector to MediaPipe and process it again.

- Export fails: make sure the recording finished processing first.

## Next steps​

- Find and read your output

- Choose a tracking model

- Before you start

- Export automatically

- Export a recording you already processed

- Export options

- Where the files go

- If something goes wrong

- Next steps
