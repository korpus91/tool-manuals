# Testing | FreeMoCap

Skip to main content

This page is in flux. Testing section for FreeMoCap core is a work in progress for version alpha. It's expected to stabilize by beta.
Human-checked documentationchecked against source

This page is adapted from real, human-written FreeMoCap documentation. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

freemocap v2.0.0-alpha.21: freemocap-ui/electron/main/services/menu-builder.ts and src/hooks/useMenuActions.ts (Data > Load Test Data action, freemocap_test_data recording name, 7x5/58mm board config), freemocap/tests/pipelines/conftest.py (test recording contents, canonical path, auto-download URL and cache), MocapPanel.tsx, BlenderSection.tsx and RecordingBrowser.tsx/ImportVideosModal.tsx (current button labels, posthoc stage toggles, MediaPipe-only Blender export)

2026-08-19

v1 (ported, not yet re-checked against v2)

More about how these docs are written

# Testing steps for FreeMoCap

These steps are primarily made to test:

- Starting a brand new recording from scratch and making sure it works

- Reprocessing an existing recording and making sure it works

- Running the pipeline from all the different stages to make sure that file loading and processing works as intended

## 1. Single camera recording​

- Record and process a single camera recording in full (meaning you get a Blender output)

- Note: Blender export currently only supports MediaPipe output. Switch the detector to MediaPipe in the Motion Capture panel before processing if you want the .blend file.

## 2. Sample/test data​

- In the desktop app, use Data > Load Test Data in the menu bar. This loads the freemocap_test_data recording (3 synchronized videos, 222 frames, filmed with a 7x5 ChArUco board with 58mm squares) and applies the matching board configuration, then process it in full

- The test recording is looked for at ~/freemocap_data/recordings/freemocap_test_data. It is not bundled with the installer; if it is missing, running the end-to-end pipeline test suite once (uv run poe test-pipelines) downloads it automatically from a FreeMoCap/skellysamples GitHub release and caches it

- The longer freemocap_sample_data recording (roughly 1100 frames, the same recording at full length rather than downsampled) has no download source, so it only works if it is already on disk next to the test data

## 3. Record and run a multi-camera recording​

- Record a calibration

- Make a multi-camera recording

- Process the recording in full

## 4. Load in an existing session​

- Use this to test the pipeline in different stages, to ensure you can run it from any point in the pipeline

- Bonus points if you load an existing session that was processed with a previous version of FreeMoCap, to make sure there are no version-related conflicts when it comes to processing

- Load the session by entering or browsing to its folder in the Motion Capture panel's recording path field, and check that it loaded correctly (check the Recording ID and the status panel)

- Re-run the recording with the Process Selected Recording button

- Exercise the pipeline stage toggles in the Motion Capture panel (2D tracking, 3D triangulation, filtering) to check the stages behave as expected on an already-processed session

- Test the export with the Blender section of the Motion Capture panel (Process Recording with Blender, or enable Export to Blender after mocap processing before running)

## 5. Import video​

- Import any set of videos (can just use existing ones from a synchronized recording) via the Import Videos button in the playback view, and run in full

For the automated test suite (pytest backend tests, frontend tests, and the end-to-end pipeline tests used preceding), see TESTING.md at the root of the FreeMoCap repository.

- 1. Single camera recording

- 2. Sample/test data

- 3. Record and run a multi-camera recording

- 4. Load in an existing session

- 5. Import video
