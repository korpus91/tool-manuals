# Maintainer tools | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

SkellyPings source re-read directly (test_ping.py, stats.py, root pyproject.toml, README.md, env.example) plus repo-root file listing

2026-08-24

SkellyPings source read directly (client package, server, infra, maintainer scripts, pyprojects); consumer integration verified in FreeMoCap and SkellyCam clones including their CI workflows and lockfiles

More about how these docs are written

# Maintainer tools

Both live at the repo root and require GCP application-default credentials for the telemetry project (freemocap-user-pings, per their docstrings); test_ping.py additionally needs a .env with SKELLYPINGS_SECRET and SKELLYPINGS_URL:

- test_ping.py, round-trip smoke test: sends one signed test_ping event, then reads it back out of Firestore (choosing the verified or unverified collection based on the server's response) and asserts the five identity fields it sent (event_type, app_name, app_version, os_platform, user_id) survived storage.

- stats.py, ad-hoc totals streamed from both collections: counts by app, event type, version, OS, unique users, and the 20 most recent pings.

These scripts import google-cloud-firestore, which the root pyproject.toml deliberately places in an admin dependency group rather than runtime dependencies, so pip install skellypings and downstream consumers stay lightweight.
