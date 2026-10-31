# Python API | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

skelly_synchronize/skelly_synchronize.py: both synchronize_videos_from_audio and synchronize_videos_from_brightness signatures confirmed to match exactly (param names, types, defaults, order); video_functions/video_utilities.py's multiprocessing.Pool(processes=min(len(video_info_dict), cpu_count()-1)) confirmed

2026-08-24

SkellySync source read directly (package code, README, the pyproject config, CI workflows)

More about how these docs are written

# Python API

Both entry points live in skelly_synchronize/skelly_synchronize.py and are exported from the package root:

```

synchronize_videos_from_audio(

    raw_video_folder_path: Path,

    synchronized_video_folder_path: Optional[Path] = None,   # default: <raw parent>/synchronized_videos

    video_handler: str = "deffcode",                         # or "ffmpeg"

    create_debug_plots_bool: bool = True,

) -> Path

synchronize_videos_from_brightness(

    raw_video_folder_path: Path,

    synchronized_video_folder_path: Optional[Path] = None,

    video_handler: str = "deffcode",

    brightness_ratio_threshold: float = 1000,

    create_debug_plots_bool: bool = True,

) -> Path

```

Both return the synchronized-video folder path. The video_handler argument selects only the trimming backend (deffcode decodes and re-writes selected frames through OpenCV; ffmpeg cuts with -ss/-t; anything else raises ValueError), video metadata probing always goes through ffprobe regardless. Trimming runs across a multiprocessing.Pool capped at min(num_videos, cpu_count - 1).
