# Generic USB Cameras | FreeMoCap

Skip to main content

# Generic USB Cameras
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

🎥
SkellyCam works with any standard USB webcam. If your camera is UVC-compliant, it will work out of the box. No proprietary hardware, no special drivers — grab whatever cameras you have and start capturing.

## The philosophy​

SkellyCam is part of the FreeMoCap ecosystem, which is built on a core principle: motion capture should be accessible to everyone. That means no expensive proprietary camera systems, no special drivers, no vendor lock-in.

If you have USB webcams — any USB webcams — you can do multi-camera synchronized capture.

Most research-grade multi-camera systems use hardware triggers — an external signal that fires all camera sensors simultaneously. This provides near-perfect synchronization but requires expensive, specialized cameras. SkellyCam is designed to deliver research-quality synchronization using software-side control of inexpensive consumer-grade USB cameras — making synchronized multi-camera capture accessible without proprietary hardware.

## What works today​

SkellyCam uses OpenCV's VideoCapture to interface with cameras. Any camera that presents as a UVC (USB Video Class) device will work. UVC is the standard protocol used by virtually all USB webcams, including:

- Budget webcams (Logitech C270, etc.)

- Mid-range webcams (Logitech C920, C922)

- Higher-end USB cameras (Logitech Brio, Razer Kiyo)

- Many industrial USB cameras that expose a UVC interface

- Most laptop built-in cameras

Camera models not explicitly tested

The cameras listed above are common examples of UVC-compliant devices. We have not explicitly tested every model and cannot guarantee that any particular camera will work perfectly. Cameras are weird and hard to predict! Future work aims to develop a community-maintained repository of tested camera models. If you encounter issues with a specific camera, please open an issue.

If your operating system recognizes the camera without installing special drivers, it's most likely UVC-compliant and will work with SkellyCam.

## Limitations of USB cameras​

Standard USB webcams are mostly optimized for video streaming, not scientific measurement. They have real limitations worth understanding:

- No hardware sync — Each camera runs on its own internal clock. SkellyCam's software synchronization protocol mitigates this (see Frame-Perfect Sync), but the physical capture moments still have some spread.

- No real timestamps — Most USB cameras do not provide accurate timestamps for when each frame was captured. SkellyCam works around this with its own timestamp system.

- Rolling shutter — Many webcams use rolling shutter sensors, which means fast motion can produce skew artifacts.

- USB bandwidth — Each camera consumes USB bandwidth. Running many cameras may require multiple USB host controllers.

These are inherent to the hardware — SkellyCam's job is to get the best possible results from the cameras you have.

## Multi-camera setup tips​

- Use separate USB controllers — Plug cameras into ports on different USB host controllers to avoid bandwidth contention. On desktops, ports on different sides of the machine are often on different controllers.

- Lower resolution if needed — If you're hitting bandwidth limits, configure cameras at a lower resolution. The synchronization will be tighter too, since smaller frames transfer faster.

- Consistent cameras — Using identical camera models simplifies configuration and produces more consistent results, though mixing models works fine.

- The philosophy

- What works today

- Limitations of USB cameras

- Multi-camera setup tips
