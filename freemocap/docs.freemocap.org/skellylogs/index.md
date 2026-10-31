# SkellyLogs | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

GitHub API and raw files checked 2026-10-14 (repo metadata, releases, branch comparisons), PyPI/npm metadata, and freemocap uv.lock at v2.0.0-alpha.25 for pinned commits. Added the At a glance section (role in the app, links, pinned version, install note).

2026-08-26

SkellyLogs source re-checked line-by-line (pyproject.toml, README.md, configure_logging.py, logger_builder.py, log_levels.py, default_paths.py, handlers/, formatters/, filters/); consumer git-dependency claims verified against freemocap and skellycam pyproject.toml files; all eight Contents link targets confirmed to exist and route at /skellylogs/ per docusaurus.config.ts stubRepos

2026-08-24

SkellyLogs source and README read directly; consumer usage verified in FreeMoCap and SkellyCam clones

More about how these docs are written

# SkellyLogs

SkellyLogs is the shared logging package for the FreeMoCap polyrepo. It is a small, opinionated wrapper around Python's stdlib logging module: one call to configure_logging() reconfigures the root logger so that every logging.getLogger(...) call in the process emits colorized console output, writes to a timestamped log file, and (optionally) pushes structured log records onto a multiprocessing.Queue that a websocket endpoint drains and relays to the frontend.

It has zero runtime dependencies (dependencies = [] in pyproject.toml) and is consumed as a git dependency by freemocap and skellycam. Its self-description in pyproject.toml: The logging module for freemocap (and skellycam). Part of the polyrepo's utility tier, infrastructure any of the pipeline repos can depend on.

## At a glance​

In the FreeMoCap app. Writes FreeMoCap's log files and feeds the log panel at the bottom of the app. Logs go to skellylogs_data/logs in your home folder; attach the newest one when you report a bug.

Codefreemocap/skellylogs

IssuesOpen issues

Version in FreeMoCap alpha.259114990 on main (0.1.0)

InstallNot on PyPI; use uv add git+https://github.com/freemocap/skellylogs

LicenseAGPL-3.0

These pages describe SkellyLogs' main branch, which is 11 commits ahead of the copy FreeMoCap alpha.25 uses. One difference you might notice: the SKELLYLOGS_LOG_DIR environment variable exists on main but not in FreeMoCap's copy, so the app's logs always go to ~/skellylogs_data/logs.

## Contents​

- How it works

- Custom log levels

- configure_logging reference

- The websocket log queue

- Log files

- Output format

- Module map

- How the rest of the polyrepo uses it

- At a glance

- Contents
