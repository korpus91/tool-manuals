# SkellyForge | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

GitHub API and raw files checked 2026-10-14 (repo metadata, releases, branch comparisons), PyPI/npm metadata, and freemocap uv.lock at v2.0.0-alpha.25 for pinned commits. Added the At a glance section (role in the app, links, pinned version, install note).

2026-08-26

Re-read SkellyForge (ref main): pyproject.toml (requires-python >=3.10, AGPLv3+ classifier, deps numpy/scipy/pandas/toml/pyyaml/pyarrow, bumpver current_version v2024.12.1009, console script skellyforge = skellyforge.__main__:run), __init__.py/__main__.py placeholder check, undeclared tqdm imports in apply_filter.py and apply_interpolation.py, post_processing butter.py and linear_interp.py, biomechanics calculate_center_of_mass.py and enforce_rigid_bones.py, skellymodels bvh_exporter.py, Actor save_out_numpy/csv/parquet methods, tracker_info YAMLs and ModelInfo loaders, subpackage tree sizes; shared-model claim re-verified against skellyforge.skellymodels imports in the FreeMoCap clone; all 8 Contents links resolved

2026-08-24

SkellyForge source read directly (full package tree, the pyproject config, README, tracker_info YAMLs); integration points verified in the FreeMoCap clone

More about how these docs are written

# SkellyForge

SkellyForge is the posthoc processing and kinematic modeling package for FreeMoCap. It takes triangulated 3D marker data and turns it into an analyzed, annotated, exportable skeleton: gap interpolation, Butterworth smoothing, anatomical model construction, center of mass and rigid-bone calculations, and NumPy/CSV/parquet/BVH output. Part of the polyrepo's pantheon tier, alongside SkellyCam, SkellyTracker, and FreeMoCap itself.

Its largest subpackage, skellymodels, doubles as the polyrepo's shared skeletal data model: the tracker-output layouts (MediaPipe, RTMPose, ChArUco boards), the tracker-agnostic canonical body and hand models, and the Actor/Aspect/Trajectory object graph built on top of them.

Package facts, from pyproject.toml and __init__.py: pure Python (>=3.10), AGPLv3+, runtime deps NumPy, SciPy, pandas, toml, pyyaml, and pyarrow (code also imports tqdm without declaring it), version v2024.12.1009 via bumpver. The declared console script skellyforge = skellyforge.__main__:run is a placeholder, __main__.py contains a single comment, so there is no runnable CLI today.

## At a glance​

In the FreeMoCap app. Cleans up and organizes the 3D data. After triangulation, SkellyForge fills short gaps, smooths each point's path, builds the skeleton model, works out center of mass, and saves the output_data/ files. See filter and fill your data and find and read your output.

Codefreemocap/skellyforge

IssuesOpen issues

Version in FreeMoCap alpha.25ddf24f3 on main

InstallFreeMoCap installs it from GitHub. The PyPI package is an older release; for the current code use uv add git+https://github.com/freemocap/skellyforge

LicenseAGPL-3.0

The repository's own README still describes an older post-processing GUI from FreeMoCap 1.x, not the package these pages document.

## Contents​

- Data models

- Post-processing

- The skeletal data model

- Pipelines

- Logging

- Utilities

- How FreeMoCap uses SkellyForge

- Caveats for readers

- At a glance

- Contents
