# Beginner Tutorial | FreeMoCap

Skip to main content

🤖AI-generated documentation✓ curatedAI Generated
This page was drafted by an AI assistant and may contain inaccuracies. This content has been reviewed by a human curator.About content generation types

🤖
AI Generated — Page drafted entirely by AI from codebase or prompt instructions.
(e.g., docs generated from codebase analysis)
← this page

✋→🤖
AI Transformatted — Human provided raw material; AI restructured it into a different format.
(e.g., livestream → blog post, meeting notes → docs)

✋
Human Generated — Page written entirely by a human author.
(e.g., hand-written tutorial)

More info about content generation types ↗

# Beginner Tutorial

This tutorial expands on the Quick Start with more detail about camera selection, configuration, and recording.

## Selecting Cameras​

When you click Detect Cameras, SkellyCam scans for all available USB Video Class (UVC) cameras. This includes most USB webcams (e.g. Logitech C270, C920) and built-in laptop cameras. Virtual cameras (like OBS Virtual Camera) are filtered out by default.

After detection, you'll see a list of available cameras. Select the ones you want to use and click Apply to create a camera group. A live preview will appear for each selected camera.

API

Detect cameras: POST /skellycam/camera/detect — Create or update a camera group: POST /skellycam/camera/group/apply. See the API Reference for details.

## Configuring Cameras​

Screenshot coming soon

Screenshot of the Camera Config panel in the UI, showing resolution, framerate, exposure, exposure mode, and rotation settings with labels for each control.

Each camera in the group can be configured independently. The configuration panel in the UI lets you adjust the following settings:

SettingDefaultDescription

Resolution1280 x 720Capture resolution in pixels. If the camera doesn't support the requested resolution, OpenCV falls back to the nearest supported one.

FramerateCamera defaultTarget capture framerate. Leave at default (-1) to run as fast as the hardware allows, or set a specific value (e.g. 30).

Exposure-7Hardware-dependent exposure value. More negative = shorter exposure time. The valid range depends on your camera model.

Exposure ModeMANUALChoose between MANUAL, AUTO, or RECOMMENDED.

RotationNoneRotate the image in software after capture: 90° CW, 180°, or 90° CCW.

How RECOMMENDED exposure works

The RECOMMENDED mode does not simply set a default value. It cycles through multiple exposure settings and selects the one is one level lower than the setting puts the mean pixel luminance closest to half-maximum (approximately 127.5 out of 255). This results in an image that is slightly darker than what we would tend to pic for standard camera usage — a deliberate choice that balances visibility with low exposure times to minimize motion blur. Note: the UI remembers camera settings between sessions. Use Ctrl+R (hard refresh) to clear saved settings.

API

Camera configuration is sent as part of the camera group: POST /skellycam/camera/group/apply. See the API Reference for the full request schema.

## Recording with Audio​

Before starting a recording, you can optionally select a microphone to capture audio alongside video. The UI shows available audio input devices — select one to include audio in your recording.

API

Detect microphones: GET /skellycam/camera/microphone/detect. See the API Reference for details.

Click Record to begin. All cameras capture synchronized frames while audio is recorded in parallel. Click Stop to finish.

Audio recording is an active area of development:

## Viewing Recordings​

Navigate to the Recordings page to browse your saved sessions. Each recording shows metadata:

- Camera count

- File size

- Duration

- FPS

- Frame count

Recordings are sorted newest-first.

### Playback​

Select a recording to open the frame-locked playback viewer. Key features:

- Frame-locked synchronization — all cameras always display the same frame number, with no drift

- Frame stepping — step forward and backward one frame at a time

- Variable speed — adjust playback speed

- Keyboard shortcuts — control playback from the keyboard

## Where Recordings Are Saved​

By default, recordings are saved to ~/skellycam_data/recordings/. Each recording session gets its own folder with synchronized video files and timestamp data.

For a detailed look at the recording folder structure and data model, see the Advanced Tutorial.

- Selecting Cameras

- Configuring Cameras

- Recording with Audio

- Viewing Recordings

- Playback

- Where Recordings Are Saved
