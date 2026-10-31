# Connect and configure cameras | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): CameraSettingsModal.tsx (Rotate, Resolution, Exposure; no framerate, focus or white balance controls), SettingsModal.tsx and menu-builder.ts (File > Settings, Include virtual cameras when detecting devices; alpha.24 release notes), skellycam opencv_apply_config.py (Linux forced auto-exposure). Rewritten; fixed garbled text from an earlier automated style pass. Camera table carried over, not re-tested.

2026-08-25

freemocap-docs docs/guides/camera-setup.mdx plus live code: freemocap-ui camera config tree and calibration settings, skellycam camera_config.py and opencv_apply_config.py, skellytracker charuco_board_definition.py, freemocap shared/charuco

2026-08-21

freemocap-docs guides/camera-setup.mdx (v2.0.0-alpha.21, not yet re-checked against the running app)

More about how these docs are written

# Connect and configure cameras

For placement, lighting and background, see optimize your capture space and record with multiple cameras.

## Which cameras work​

Most USB webcams work. These are commonly used:

CameraResolutionFPSNotes

Logitech C9201080p / 720p30 / 60Widely used, reliable

Logitech C9221080p / 720p30 / 60Like the C920, better in low light

Logitech Brio4K / 1080p30 / 60Higher resolution, wider view

Elgato Cam Link1080p60Connects a DSLR or mirrorless camera over HDMI

FreeMoCap doesn't look for virtual cameras (like OBS Virtual Camera) by default. To use one, turn on Include virtual cameras when detecting devices under File > Settings > Cameras.

## USB bandwidth​

Each camera uses a lot of USB bandwidth. When there isn't enough, you get dropped frames or cameras disconnecting, with no clear error.

- Plug cameras straight into the computer, not into a hub.

- Spread cameras across different USB controllers if you can.

- Use USB 3 ports where possible.

- Lower the resolution to fit more cameras.

## Camera settings​

Expand a camera's row in the camera panel to change:

SettingRecommendation

RotateMatch how the camera is mounted

Resolution720p is a good balance of quality and bandwidth

ExposureManual, kept fixed. See setting exposure

Keep exposure fixed. If it changes during a recording, tracking and calibration can drift. Cameras on Linux always use automatic exposure.

FreeMoCap has no settings for frame rate, focus, or white balance. Cameras run at their own default frame rate. If your camera can lock focus and white balance, do it with the camera's own software before recording.

## Synchronization​

FreeMoCap keeps the cameras in step in software. Every camera captures the same number of frames, and each frame gets a timestamp. For the best sync, use cameras with a steady frame rate and keep recordings under about 30 minutes.

## Next steps​

- Calibrate your cameras

- Get a calibration you can trust

- Which cameras work

- USB bandwidth

- Camera settings

- Synchronization

- Next steps
