# Filter and fill your data | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): skellyforge filter_config.py (Butterworth low-pass, cutoff 6 Hz, order 4, sampling rate 30), posthoc_mocap_task.py (sampling rate set from recording timestamps when available), recording_framerate.py (needs synchronized_videos/timestamps, so imported videos fall back to the setting), mocap-postprocess-settings.tsx labels, skeleton_from_mediapipe_observations.py (interpolate then filter).

2026-08-26

skellyforge main (post_processing filters/interpolation incl. FilterConfig and InterpolationConfig defaults, butter.py, linear_interp.py) plus freemocap clone pinned to v2.0.0-alpha.21 (skeleton_from_mediapipe_observations.py, charuco_model_from_observations.py, posthoc_mocap_task.py, triangulator.py and TriangulationConfig)

2026-08-20

not checked against a specific version

More about how these docs are written

# Filter and fill your data

After FreeMoCap works out the 3D position of each point, it cleans up the data in two steps before saving it. Knowing about them helps you read your data correctly.

## Filling gaps​

Sometimes a point can't be placed in 3D for a frame, for example when too few cameras could see it. FreeMoCap fills these short gaps by interpolating between the frames on either side. Fewer gaps means better data, so good camera placement and lighting help. See optimize your capture space.

## Smoothing​

FreeMoCap then smooths each point's path with a low-pass filter (a Butterworth filter). It removes small frame-to-frame jitter while keeping the real, slower movement.

Smoothing too much can also remove real detail from very fast movements such as jumps and punches.

## Changing the filter​

Open Mocap Settings and find Butterworth Low-Pass Filter:

SettingDefaultWhat it does

Cutoff (Hz)6Lower smooths more. Raise it for fast movements.

Order4How sharply the filter cuts off.

Sampling Rate30The recording's frame rate.

For recordings made in FreeMoCap, the sampling rate is set automatically from the recording. For imported videos, set it to your videos' frame rate yourself.
 The Butterworth Low-Pass Filter settings in Mocap Settings.FreeMoCap 2.0.0-alpha.25
To apply new settings to an existing recording, process it again. Open it in the Playback tab, click Continue to Mocap Setup, then Process Mocap.

## Next steps​

- The FreeMoCap output data model

- Accuracy, validity, and limits

- Filling gaps

- Smoothing

- Changing the filter

- Next steps
