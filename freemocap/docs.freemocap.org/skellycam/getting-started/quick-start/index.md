# Quick Start | FreeMoCap

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

# Quick Start

This guide walks you through recording your first synchronized multi-camera session in five steps.

Screenshot coming soon

Screenshot of the SkellyCam app window on first launch, showing the main interface with camera detection and recording controls.

## 1. Install SkellyCam​

Download and install SkellyCam from the Download page. Run the installer for your platform — no additional dependencies needed.

Already a developer?

You can also run from source code.

## 2. Launch the App​

Open SkellyCam after installation. The server starts automatically in the background and the UI opens in the app window.

## 3. Connect and Detect Cameras​

Plug in your USB cameras (or use a built-in webcam). In the UI, click Detect Cameras to scan for available devices. SkellyCam will list all detected cameras.

Select the cameras you want to use and click Apply to create a camera group. You'll see a live preview from each camera.

API

Camera detection is also available via POST /skellycam/camera/detect. See the API Reference for details.

## 4. Record​

Click Record to start recording. All cameras will capture synchronized video — every camera produces the exact same number of frames.

Optionally, select a microphone to capture audio alongside video.

Click Stop when you're done.

API

Start recording: POST /skellycam/camera/group/all/record/start Stop recording: GET /skellycam/camera/group/all/record/stop

## 5. View Your Recording​

Navigate to the Recordings page in the UI. Your recording appears in the list with metadata (camera count, duration, FPS, frame count).

Select a recording to open the Playback viewer. All videos play back frame-locked — every camera always displays the same frame number, with no drift.

API

List recordings: GET /skellycam/playback/recordings Load a recording: POST /skellycam/playback/load

## Next Steps​

- Beginner Tutorial — Learn more about camera selection, configuration options, and recording with audio

- Advanced Tutorial — Explore the data model, recording folder structure, and server configuration

- 1. Install SkellyCam

- 2. Launch the App

- 3. Connect and Detect Cameras

- 4. Record

- 5. View Your Recording

- Next Steps
