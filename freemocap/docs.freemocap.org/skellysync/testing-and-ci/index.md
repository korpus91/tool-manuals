# Testing and CI | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

.github/workflows/ (lint-with-black.yml, publish_to_pypi_when_new_tag_is_pushed_to_main.yml, python-testing.yml, all confirmed to exist exactly) and pyproject.toml (current_version = "v2025.04.1037" and description = "Basic template of a python repository", both confirmed verbatim)

2026-08-24

SkellySync source read directly (package code, README, the pyproject config, CI workflows)

More about how these docs are written

# Testing and CI

tests/conftest.py downloads a sample multi-camera dataset from Figshare to ~/skelly_synchronize_sample_data on session start, then runs a full end-to-end audio synchronization before any test executes. The tests assert that the synchronized folder and its expected artifacts exist (debug_plot.png, synchronization_debug.toml, audio_files/, trimmed_audio/), that the video count is preserved, that all outputs share one frame count, plus unit tests for lag-dict normalization and deffcode trimming. Because of the conftest hook, any pytest invocation downloads data and processes video, expect slow first runs.

CI (.github/workflows/):

- python-testing.yml, on pull requests to main (and manual dispatch): Python 3.10 on Ubuntu, pip install -e ., apt-get FFmpeg, then pytest skelly_synchronize/tests.

- lint-with-black.yml, Black on every pull request.

- publish_to_pypi_when_new_tag_is_pushed_to_main.yml, publishes on new tags; versions follow bumpver's vYYYY.0M.BUILD pattern (current: v2025.04.1037).

License is AGPLv3+. One packaging caveat: pyproject.toml metadata still carries template boilerplate (description "Basic template of a python repository," generic keywords), and soundfile is imported directly by audio_utilities.py though only arrives transitively rather than being declared.
