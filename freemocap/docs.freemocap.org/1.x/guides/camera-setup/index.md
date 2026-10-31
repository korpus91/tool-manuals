# Connect and configure cameras | FreeMoCap

Skip to main content

This is documentation for FreeMoCap 1.x (legacy), which is no longer actively maintained.

For up-to-date documentation, see the latest version (2.0 (alpha)).

Version: 1.x (legacy)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-21

freemocap-docs guides/camera-setup.mdx (v2.0.0-alpha.21, not yet re-checked against the running app)

More about how these docs are written

# Connect and configure cameras

For the physical setup (lighting, placement, background), see optimize your capture space and record with multiple cameras. This page is about the cameras themselves and the settings that affect calibration stability.

## Supported cameras​

Any USB camera OpenCV's VideoCapture can open should work. Tested configurations:

CameraResolutionFPSNotes

Logitech C9201080p / 720p30 / 60Widely used, reliable

Logitech C9221080p / 720p30 / 60Similar to C920, better low light

Logitech Brio4K / 1080p30 / 60Higher resolution, wider field of view

Elgato Cam Link1080p60HDMI capture, for use with a DSLR or mirrorless camera

Generic USB webcamsVariableVariableMay work, quality varies

## USB bandwidth​

USB cameras use real bandwidth, and running out of it shows up as dropped frames or disconnects, not a clear error message. A few things that help:

- Use separate USB controllers when you can, not just separate ports on the same hub.

- USB 3.0 has more headroom than USB 2.0.

- Lower resolution means less bandwidth per camera, which means more cameras can share one controller.

- If cameras are dropping frames or disconnecting, that's the first thing to check, spread them across controllers before assuming something else is wrong.

## Configuration settings that matter​

Set through the Camera Config Tree in the sidebar:

SettingRecommendation

Resolution720p is a good balance of quality and bandwidth

Framerate30 FPS minimum, 60 FPS for fast movement

ExposureManual, fixed

FocusManual, fixed on the capture volume

White balanceManual, fixed

Fixed exposure and focus matter more than they might seem to. If auto-exposure changes mid-recording, the detected feature positions shift with the brightness change, and your calibration can drift as a result. This is a common, non-obvious cause of a calibration that looked fine and then didn't.

## Synchronization​

Cameras aren't hardware-genlocked, FreeMoCap synchronizes them in software by aligning frame timestamps after the fact. For the most reliable sync: use cameras that hold a consistent framerate (not variable frame rate), and keep individual recording sessions under about 30 minutes to limit how much drift can accumulate.

## Calibration board​

Calibration uses a printed ChArUco board. Print it on something rigid so it stays flat, board files are in the software's repository. The board's physical dimensions need to match whatever's configured in the calibration settings.

## Next steps​

- Why calibration matters

- Get a calibration you can trust

- Record with multiple cameras

- Supported cameras

- USB bandwidth

- Configuration settings that matter

- Synchronization

- Calibration board

- Next steps
