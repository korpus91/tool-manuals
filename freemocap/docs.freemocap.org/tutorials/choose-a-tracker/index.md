# Choose a tracking model | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): mocap_task_config.py and mocap-slice.ts (detector rtmpose default; rtmpose 'more accurate', mediapipe 'faster, CPU-friendly'), mocap-detector-settings.tsx (RTMPose/MediaPipe only; Default/High Res/Fast and Heavy/Full/Lite), BlenderSection.tsx (MediaPipe-only export). The old page said MediaPipe was the default and listed trackers the app doesn't offer. Validation findings carried over from /concepts/accuracy-and-limits.

2026-08-26

skellytracker/core/detectors/detector_base_classes.py (confirmed a real, current extensible detector interface exists) and skellyforge/pipelines/dlc_pipeline.py (confirmed dead code, broken imports, already tracked in CODE-BUGS-FOUND.md)

2026-08-20

not checked against a specific version

More about how these docs are written

# Choose a tracking model

The tracker finds your body's joints in each video frame. FreeMoCap offers two. Choose one under Mocap Settings > Detector.

RTMPose (default)MediaPipe

AccuracyHigherLower

SpeedSlower, much faster with a GPUFaster, runs well on any processor

Blender exportNot yetYes

OptionsDefault, High Res, or Fast modelHeavy, Full, or Lite model

Use RTMPose for the most accurate data, unless you need Blender.

Use MediaPipe if you want a Blender scene, or if processing is too slow on your computer.
 With RTMPose selected, choose a Default, High Res or Fast model.FreeMoCap 2.0.0-alpha.25 With MediaPipe selected, choose a Heavy, Full or Lite pose model.FreeMoCap 2.0.0-alpha.25

## Matching the tracker to your task​

From FreeMoCap's validation studies (details in accuracy, validity, and limits):

- Walking and gait: RTMPose was the most consistent.

- Balance and standing still: MediaPipe's built-in smoothing made it better at picking up small amounts of sway.

- Fast movements: MediaPipe's smoothing can make it lag behind quick motion, so prefer RTMPose.

## When neither tracker works​

Standard trackers can fail on bodies they weren't trained on, such as a person with a prosthetic limb. A custom-trained model can work in these cases; see image tracking and pose models.

## Next steps​

- Set up GPU acceleration

- Image tracking and pose models

- Matching the tracker to your task

- When neither tracker works

- Next steps
