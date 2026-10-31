# Utilities | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

SkellyForge utilities re-read line-by-line on current main (get_files_from_folder.py glob patterns for .mp4 and *snapshot*.csv, get_unique_list dedupe and sort, package __init__), tree-wide search confirming the module is imported only by pipelines/dlc_pipeline.py, pyproject.toml packaging check, and a search of the pinned FreeMoCap clone showing no import of this module

2026-08-24

SkellyForge source read directly (full package tree, the pyproject config, README, tracker_info YAMLs); integration points verified in the FreeMoCap clone

More about how these docs are written

# Utilities

utilities/get_files_from_folder.py globs synchronized-video folders for .mp4 files and DeepLabCut export folders for *snapshot*.csv files, with dedupe and sorting.
