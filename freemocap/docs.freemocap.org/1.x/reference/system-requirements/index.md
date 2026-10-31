# System requirements | FreeMoCap

Skip to main content

This is documentation for FreeMoCap 1.x (legacy), which is no longer actively maintained.

For up-to-date documentation, see the latest version (2.0 (alpha)).

Version: 1.x (legacy)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-21

this site's own hardware.md, gpu-setup.md, and camera-setup.md

More about how these docs are written

# System requirements

For the fuller explanation of why these matter, see choose and set up your cameras and set up GPU acceleration. This page is the terse version.

## Minimum​

RequirementDetail

CameraOne, even a laptop's built-in camera. Gives 2D tracking only, not reliable 3D.

PythonA recent Python, installed via a virtual environment manager (Anaconda recommended)

OSWindows, macOS, or Linux

GPUNone required, CPU inference works everywhere

## For reliable 3D data​

RequirementDetail

Cameras2 minimum, 3+ recommended, connected directly to USB ports (not through a hub)

Calibration boardA printed ChArUco board, see why calibration matters

## Optional​

SoftwareFor

BlenderGenerating an animated 3D scene from your recording

VS Code or JupyterLabWorking with the Jupyter notebooks generated per recording

A supported GPUFaster pose estimation, see set up GPU acceleration for which install to use

## GPU support by platform​

PlatformGPUWhat you get

Windows / LinuxNVIDIACUDA, or TensorRT for the fastest option

WindowsAMD, Intel, or any DirectX 12 GPUDirectML

macOSApple Silicon (M1 and newer)CoreML, automatic

AnyNoneCPU fallback, always available

## Next steps​

- Choose and set up your cameras

- Connect and configure cameras

- Set up GPU acceleration

- Minimum

- For reliable 3D data

- Optional

- GPU support by platform

- Next steps
