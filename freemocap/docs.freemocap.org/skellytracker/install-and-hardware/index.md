# Install extras and hardware | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

PyPI skellytracker (2025.10.1024) vs freemocap uv.lock (git main at 6310005), 2026-10-14. Pointed the base install at GitHub.

2026-08-26

pyproject.toml's [project.optional-dependencies] section, re-read directly: mediapipe, onnx, onnx-cpu (with its Apple Silicon CoreML EP comment) extras confirmed exactly as described

2026-08-24

SkellyTracker source read directly (core package, README, CLAUDE.md, the pyproject config); FreeMoCap integration verified against FreeMoCap/core/tracking and FreeMoCap/core/pipeline in the FreeMoCap clone

More about how these docs are written

# Install extras and hardware

Base install covers the OpenCV detectors. Install from GitHub (uv add git+https://github.com/freemocap/skellytracker) to get the code FreeMoCap uses; pip install skellytracker installs an older PyPI release. Detector libraries and ONNX Runtime backends come via extras: mediapipe; onnx; and mutually exclusive session backends onnx-cpu, onnx-cuda (CUDA 12 + cuDNN 9 pip wheels, no system toolkit needed), onnx-trt (TensorRT, engines compiled on first run), onnx-directml (any GPU on Windows). Bundles: recommended-cpu, recommended-cuda, and all-* equivalents. See the repo README and GPU_SETUP_GUIDE.md for details.
