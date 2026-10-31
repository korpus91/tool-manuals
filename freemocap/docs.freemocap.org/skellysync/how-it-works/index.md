# How synchronization works | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

Re-read SkellySync main: skelly_synchronize.py, correlation_functions.py, audio_utilities.py, video_functions/video_utilities.py, video_functions/ffmpeg_functions.py, normalize_framerates.py, utils/get_video_files.py, system/paths_and_file_names.py

2026-08-24

SkellySync source read directly (package code, README, the pyproject config, CI workflows)

More about how these docs are written

# How synchronization works

## Audio cross correlation​

- Collect videos (get_video_file_list), build a video-info dict, and read fps and audio sample rate via ffprobe.

- If framerates or sample rates differ across videos, re-encode copies into a normalized_videos/ subfolder at the lowest fps and lowest sample rate found, and continue from those copies.

- Extract each track to WAV into audio_files/ and load it with librosa.

- Cross-correlate every audio signal against the first file in the dictionary using scipy.signal.correlate(mode="full", method="fft"); the argmax lag, divided by the sample rate, gives that camera's offset in seconds.

- Normalize the lag dict by subtracting every value from the maximum, the latest-starting camera gets lag 0, all others get positive offsets.

- Trim: the shared length is min(duration_i - lag_i) across videos; each output starts at its own lag offset.

- Trim each camera's audio the same way (written as 24-bit PCM WAV into audio_files/trimmed_audio/) and mux it back onto the trimmed video (-c:v copy -c:a aac), replacing the silent copy via a temp-file move.

## First brightness change​

- Same collection step; normalize framerates only if they differ.

- For each video, compute the mean grayscale value of every frame (find_brightness_across_frames, cached beside the video as <stem>_brightness.npy).

- Take the first and second differences of that array; their product is a combined "how sudden and how large" metric, and the first frame where it crosses brightness_ratio_threshold is that video's sync point. If nothing crosses the threshold, the code falls back to the frame with the fastest detected change.

- Lags (frame index divided by fps) are passed to the trim step unnormalized, unlike the audio path, so each video is simply cut from its own sync-point frame onward. There is no audio handling in this mode.

In both modes a post-trim frame-count check requires all synchronized videos to come out the same length: the common count is logged, and unequal frame counts raise an exception instead.

- Audio cross correlation

- First brightness change
