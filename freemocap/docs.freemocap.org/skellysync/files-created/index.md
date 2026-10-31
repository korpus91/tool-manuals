# Files created | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

Re-checked every artifact claim against skellysync main: skelly_synchronize.py, system/paths_and_file_names.py, file_extensions.py, correlation_functions.py, core_processes/debugging/debug_plots.py and debug_output.py, audio_utilities.py, normalize_framerates.py, video_functions (ffmpeg_functions.py, deffcode_functions.py), utils/path_handling_utilities.py, gui/skelly_synchronize_gui.py, tests/test_all_files_created.py, and README.md

2026-08-24

SkellySync source read directly (package code, README, the pyproject config, CI workflows)

More about how these docs are written

# Files created

Given a raw folder, SkellySync produces (names defined in system/paths_and_file_names.py):

PathWhenContents

<raw parent>/synchronized_videos/alwaysTrimmed videos named synced_<original stem>.mp4

synchronized_videos/audio_files/audio methodPer-camera extracted WAVs

synchronized_videos/audio_files/trimmed_audio/audio methodLag-shifted, length-matched WAVs

<raw>/normalized_videos/mixed framerates or sample ratesRe-encoded uniform-fps copies

<video>-adjacent/<stem>_brightness.npybrightness methodCached per-frame brightness arrays

synchronized_videos/synchronization_debug.tomlalwaysDebug info (below)

synchronized_videos/debug_plot.pngalways (create_debug_plots_bool=True)Before/after visualization

The debug TOML carries up to four sections: Raw_video_information, Synchronized_video_information, Audio_information (audio method only, with the bulky audio arrays stripped before saving), and Lag_dictionary, the offsets in seconds between each raw video's start and the first moment all cameras recorded. The debug plot overlays the raw vs. synchronized signals (audio waveforms or brightness curves, per method) in two stacked subplots.

One quirk worth knowing if you modify the brightness path: skelly_synchronize.py guards the plot-input folder with if Path(...).exists:, the bound method rather than a call, so the condition is always true and create_brightness_debug_plots always looks for brightness .npy files in normalized_videos/ whether or not that folder exists.
