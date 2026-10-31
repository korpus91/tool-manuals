# Repository layout | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

Re-checked every row against SkellyPings on pinned ref main: skellypings/__init__.py (public API and version), telemetry_client.py (buffering, signing, flush thread), server/main.py (routes /events /backup /health, rate limiter), server/Dockerfile (base image, uv sync flags, port 8080), cloudbuild.yaml (build-push-deploy steps), infra/main.tf (provisioned resources), stats.py and test_ping.py (direct Firestore reads), plus README and root pyproject

2026-08-24

SkellyPings source read directly (client package, server, infra, maintainer scripts, pyprojects); consumer integration verified in FreeMoCap and SkellyCam clones including their CI workflows and lockfiles

More about how these docs are written

# Repository layout

PathContents

skellypings/__init__.pyPublic API: TelemetryClient, __version__ (0.1.0)

skellypings/telemetry_client.pyThe entire client: buffering, signing, background flush thread

server/main.pyThe entire server: /events, /backup, /health, rate limiter

server/Dockerfilepython:3.12-slim + uv sync --frozen --no-dev, runs uvicorn on port 8080

cloudbuild.yamlBuild-push-deploy pipeline used by Cloud Build

infra/main.tfTerraform alternative for provisioning the GCP resources

stats.py, test_ping.pyMaintainer-only scripts that read Firestore directly
