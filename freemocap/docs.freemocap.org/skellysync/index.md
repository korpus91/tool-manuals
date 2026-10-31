# SkellySync | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

GitHub API and raw files checked 2026-10-14 (repo metadata, releases, branch comparisons), PyPI/npm metadata, and freemocap uv.lock at v2.0.0-alpha.25 for pinned commits; freemocap sync_job.py and pyproject.toml (skellysync from branch philip/rewrite), philip/rewrite README and file tree. Added At a glance and a note that FreeMoCap runs the rewrite branch; fixed the 'nothing references it' claim.

2026-08-26

skelly_synchronize.py's two entry-point signatures and pyproject.toml, re-confirmed directly; no other polyrepo repo's pyproject/package.json references skellysync

2026-08-24

SkellySync source read directly (package code, README, the pyproject config, CI workflows)

More about how these docs are written

# SkellySync

SkellySync (skelly_synchronize) synchronizes videos of the same event after recording, without needing camera timestamps. Given a folder of videos that overlap in time, it computes the temporal offset between each video and the others, trims every video to the earliest moment all cameras were recording simultaneously, and writes the results out with matching frame counts. Two synchronization methods are available: audio cross correlation and first brightness change detection. Part of the FreeMoCap polyrepo's utility tier. Since FreeMoCap v2.0.0-alpha.23, the app uses it to synchronize imported videos.

## At a glance​

In the FreeMoCap app. Lines up videos that weren't recorded in sync. When you bring in videos with Playback > Import Videos and turn on synchronization, FreeMoCap uses SkellySync to align them by their audio or by a light flash. See process a recording after the fact.

Codefreemocap/skellysync

IssuesOpen issues

Version in FreeMoCap alpha.250231c41 on philip/rewrite

InstallFreeMoCap installs it from GitHub. The PyPI package is the older main-branch version

NeedsFFmpeg, installed separately

LicenseAGPL-3.0

FreeMoCap uses a rewrite that lives on the philip/rewrite branch, which reorganizes the package into core/, a CLI, and an optional FastAPI server and web UI. The other pages in this section were written from the older main branch, so module names and entry points there may not match what FreeMoCap runs.

## Contents​

- Install and run

- Python API

- How synchronization works

- Files created

- Module map

- Testing and CI

- At a glance

- Contents
