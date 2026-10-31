# SkellyCam Documentation | FreeMoCap

Skip to main content

# SkellyCam Documentation
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

SkellyCam turns cheap USB webcams into a frame-perfect synchronized multi-camera system. It is the camera backend for the FreeMoCap motion capture project.

## What Makes SkellyCam Different​

A camera is, at its core, a device that captures light from a particular area at a particular time. It is a spatiotemporal measurement instrument — and when you use cameras for science, the temporal dimension becomes critical.

The image itself defines the spatial aspects of the data, with fidelity determined by the camera sensor, lens, environment, and settings. The timestamps define the temporal aspect of the empirical data represented by a video. Within the FreeMoCap pipeline, extracting quantified 2D spatial information (e.g. skeleton joint positions) is handled by skellytracker. SkellyCam's focus is the temporal dimension: ensuring multi-camera frames are precisely synchronized in time.

Most research-grade multi-camera systems use hardware triggers — an external signal that fires all camera sensors simultaneously. This provides near-perfect synchronization but requires expensive, specialized cameras. SkellyCam is designed to deliver research-quality synchronization using software-side control of inexpensive consumer-grade USB cameras — making synchronized multi-camera capture accessible without proprietary hardware.

When using multiple cameras, each one captures its own slice of the world at its own moment. If those moments aren't aligned, the measurements from different cameras can't be meaningfully compared or combined. Multi-view triangulation, 3D reconstruction, motion capture — all of these require that "frame N" from every camera corresponds to the same instant in time.

Most multi-camera setups cannot guarantee this. Each USB camera runs on its own internal clock, delivering frames at its own pace. The cameras drift apart over time, and there is no built-in mechanism to keep them synchronized. SkellyCam solves this with a frame-count-gated capture protocol that coordinates all cameras at the frame level.

SkellyCam is carefully designed to guarantee:

- All recorded videos have precisely the same frame count — corresponding frames across cameras are from the same temporal time slice

- Each multi-frame payload contains one image per camera, guaranteed to be captured at the same time slice

- Recording quality is protected from real-time streaming — variations in the live stream never cause blocking, lagging, or frame loss in the recording pipeline

## Quick Start​

- Download — Get the installer for your platform from the Download page

- Install and launch — Run the installer and open SkellyCam

- Connect cameras — Plug in USB cameras and click Detect Cameras

- Record — Click Record, then Stop when done

- Play back — Open the Recordings page and select your recording for frame-locked playback

See the Quick Start guide for more detail.

Run from source?

If you're a developer, see the Development section for instructions on running from source code.

## Documentation​

PageDescription

InstallationDownload and install SkellyCam

Quick StartYour first recording in five steps

Beginner TutorialCamera selection, configuration, and recording details

Advanced TutorialData model, folder structure, server configuration

ArchitectureSystem overview, process model, data flow

Frame SynchronizationDeep-dive into the capture loop and synchronization protocol

API ReferenceHTTP and WebSocket endpoint documentation

WebSocket ProtocolBinary frame format, JSON messages, backpressure

LoggingLog levels, WebSocket forwarding, log file locations

TelemetryWhat is collected, how to opt out

DevelopmentRunning from source, testing, linting, CI, and contributing

Design PhilosophyUniversal design and progressive disclosure principles

ContributingHow to report bugs and submit pull requests

TranslatingHelp translate the UI into your language

CommunityDiscord, GitHub Discussions, project roadmap

## Community​

- Discord — Conversations, support, and community discussions

- GitHub Discussions — Longer-form questions and ideas

- Community page — Roadmap links and more ways to get involved

- What Makes SkellyCam Different

- Quick Start

- Documentation

- Community
