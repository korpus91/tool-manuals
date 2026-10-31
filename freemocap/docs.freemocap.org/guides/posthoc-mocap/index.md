# Process a recording after the fact | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): ImportVideosModal.tsx (Choose Video Files, Recording name, Synchronize videos on import with Audio or Brightness flash, ffmpeg requirement), check_ffmpeg.py (ffmpeg found on PATH, not bundled), ProcessMocapPanel.tsx and mocap-setup-modal.tsx (Continue to Mocap Setup, Processing Directory, Calibration, Detector, Blender, Post Processing, Process Mocap), mocap-processing-directory.tsx (re-check button), recording_framerate.py (imported videos lack timestamps). Rewritten; fixed garbled text from an earlier automated style pass; the old calibration-folder bug note dropped because calibration import now picks video files.

2026-08-25

freemocap v2.0.0-alpha.21 working tree: freemocap-ui mocap-setup-modal.tsx, mocap-processing-directory.tsx, calibration-module.tsx, mocap-detector-settings.tsx, mocap-blender-settings.tsx, mocap-triangulation-settings.tsx, mocap-postprocess-settings.tsx, ProcessMocapPanel.tsx, SidePanelContent.tsx, useMocap.ts, store/slices/mocap, freemocap api/http/mocap/mocap_router.py, core/tasks/mocap/mocap_task_config.py, posthoc_mocap_task.py, skeleton_from_mediapipe_observations.py, calibration_paths.py, core/pipeline/posthoc/video_node.py, video_group_helper.py

2026-08-21

freemocap-docs guides/posthoc-mocap.mdx (v2.0.0-alpha.21, human-authored source, not yet re-checked against the running app)

More about how these docs are written

# Process a recording after the fact

You can run motion capture on videos you already have, either a FreeMoCap recording you want to process again, or videos from your own cameras.

## Bring in your own videos​

- Open the Playback tab and click Import Videos.

- Click Choose Video Files and select one video per camera.

- Give the recording a name.

- If the videos weren't recorded in sync, FreeMoCap says the frame counts differ. Turn on Synchronize videos on import and choose how to line them up:

- Audio, if all the videos recorded the same sound.

- Brightness flash, if you flashed a light that every camera saw.

- Click Import.

 The Import Videos dialog with one video per camera chosen.FreeMoCap 2.0.0-alpha.25
Synchronizing needs FFmpeg. If FreeMoCap says FFmpeg is missing, install it and restart FreeMoCap.
 Ticking the synchronize option reveals the Audio and Brightness flash choices.FreeMoCap 2.0.0-alpha.25

## Process the recording​

- In the Playback tab, select the recording. Then click Continue to Mocap Setup.

- Under Processing Directory, check that the recording's folder is selected. If Process Mocap stays greyed out, click the re-check button next to the folder.

- Under Calibration, choose the calibration that matches the cameras used. It must come from the same cameras, in the same positions. You can use an existing calibration file, import one, or calibrate from calibration videos. A single-camera recording doesn't need one.

- Under Detector, choose a tracker. See choose a tracking model.

- Under Blender, choose whether to make a Blender scene. See open your recording in Blender.

- Click Process Mocap and keep FreeMoCap open until it finishes.

For imported videos, also set the Sampling Rate under Post Processing to your videos' frame rate. See filter and fill your data.

Results are saved in the recording's folder. See find and read your output.

Processing again replaces the earlier results. Copy anything you want to keep first.

## Troubleshooting​

- "Frame counts differ": the videos aren't in sync, or a video from another session is in the folder. Remove stray videos, or synchronize on import.

- Calibration or camera error: the calibration was made with different cameras. Use one made with the same cameras.

- The 3D skeleton looks distorted: check the annotated videos. If the 2D tracking looks right but the 3D doesn't, a camera probably moved after calibration. Calibrate again and reprocess.

- Processing stops: report a bug and include your log file from skellylogs_data/logs in your home folder.

## Next steps​

- Find and read your output

- Get a calibration you can trust

- Bring in your own videos

- Process the recording

- Troubleshooting

- Next steps
