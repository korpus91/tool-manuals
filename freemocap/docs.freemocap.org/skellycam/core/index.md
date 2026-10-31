# Core Concepts | FreeMoCap

Skip to main content

# Core Concepts

The foundational design principles and features of SkellyCam.

## 📄️Frame Perfect Sync

A frame-count-gated capture protocol ensures all cameras stay in lock-step with identical frame counts during both runtime and recording.

## 📄️Generic USB Cameras

Works with any standard UVC-compliant USB webcam. No proprietary hardware needed.

## 📄️Precise Timestamps

High-resolution timestamps at every stage of the capture pipeline, stored in human-readable format.

## 📄️Real-Time Streaming

WebSocket protocol streams multi-camera frames to the frontend. The API treats a camera group like a single camera.
