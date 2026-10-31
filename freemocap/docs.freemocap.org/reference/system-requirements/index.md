# System requirements | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): release asset matrix (macOS arm64, Windows x64, Linux x64; CPU and CUDA variants), freemocap-ui electron-builder.json targets, skellytracker ort_session_utils.auto_detect_provider (trt, cuda, coreml on macOS, cpu). Python/Anaconda row removed: the installer bundles Python.

2026-08-25

live polyrepo code: freemocap pyproject.toml requires-python (>=3.11) plus noxfile.py and test.yml matrix (3.11/3.12) and .python-version (3.12); skellytracker pyproject.toml extras and requires-python cap (<3.13); skellytracker GPU_SETUP_GUIDE.md provider/extras table; searched all clones for notebook/ipynb generation (none found) and freemocap.spec excluding notebook/IPython as unused; linked pages re-read (hardware.md, gpu-setup.md, camera-setup.md, calibration concept, faq.md)

2026-08-21

this site's own hardware.md, gpu-setup.md, and camera-setup.md

More about how these docs are written

# System requirements

## Computer​

Supported

MacApple Silicon (M1 or newer)

Windows64-bit (x64) PC

Linux64-bit (x64) PC

## Cameras​

GoalCameras

Try it out, 2D trackingOne, such as a laptop's built-in camera

3D motion captureTwo or more, three recommended, plugged straight into the computer, not through a hub

For 3D you also need a printed ChArUco calibration board. See calibrate your cameras.

## Graphics card​

Not required. FreeMoCap runs on any supported computer, and a graphics card makes tracking faster:

ComputerSpeed-up

Mac with Apple SiliconUsed automatically

Windows or Linux with an NVIDIA cardInstall the CUDA version of FreeMoCap

Anything elseNone, tracking runs on the processor

## Optional software​

- Blender, to turn your recording into an animated 3D scene.

## Next steps​

- Install FreeMoCap

- Choose and set up your cameras

- Computer

- Cameras

- Graphics card

- Optional software

- Next steps
