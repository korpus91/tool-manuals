# Module map | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

full recursive find across core_processes/, gui/, system/, utils/: every path in the table confirmed to exist exactly as listed, including core_processes/debugging/ and core_processes/video_functions/ subfolders and gui/widgets/run_button_widget.py; confirmed run_button_widget.py is not referenced anywhere else in the repo and pyproject.toml has no SkellyLogs dependency

2026-08-24

SkellySync source read directly (package code, README, the pyproject config, CI workflows)

More about how these docs are written

# Module map

PathContents

skelly_synchronize/__init__.pyExports the two sync functions plus the debug-plot helpers; configures logging at import time

skelly_synchronize/__main__.pyEntry point; launches the GUI

skelly_synchronize.pyThe two orchestration functions

core_processes/correlation_functions.pyFFT cross-correlation, lag finding/normalization, brightness-change detection

core_processes/audio_utilities.pyAudio extraction/loading/trimming (librosa, soundfile)

core_processes/normalize_framerates.pyLowest-common fps/sample-rate normalization via FFmpeg

core_processes/video_functions/video_utilities.pyVideo info dicts, parallel trimming, audio remux

core_processes/video_functions/ffmpeg_functions.pysubprocess wrappers: probe duration/fps/sample rate, extract audio, trim, normalize, attach audio

core_processes/video_functions/deffcode_functions.pyFrame-list trimming through deffcode + OpenCV writer, including rotation-metadata transpose handling (-noautorotate + filter chain)

core_processes/debugging/debug_output.pyTOML serialization

core_processes/debugging/debug_plots.pyMatplotlib before/after plots

utils/get_video_files.pyExtension-globbing video discovery (upper/lowercase dedupe for Windows)

utils/path_handling_utilities.pyDirectory creation, synced_ name builder (also strips a leading raw prefix if present)

system/Constants: folder/file names, VideoExtension/AudioExtension enums, default paths, logging configuration

gui/PySide6 MainWindow; widgets/run_button_widget.py is a leftover demo widget not referenced anywhere else

tests/pytest suite (below)

Logging note: importing skelly_synchronize calls its own configure_logging() (console at INFO plus a timestamped file under ~/skelly_synchronize_data/logs_info_and_settings/logs/). This is a self-contained stdlib-logging setup, not the polyrepo's shared SkellyLogs package, no SkellyLogs dependency exists here.
