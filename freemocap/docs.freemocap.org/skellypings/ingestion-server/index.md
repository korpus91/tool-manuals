# The ingestion server | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

SkellyPings repo re-read in full (server/main.py, infra/main.tf, cloudbuild.yaml, server/Dockerfile, client package, README, stats.py, test_ping.py, pyprojects); env vars and defaults, routes, rate limiter and flush interval, backup flow, scheduler timing, and max_instances all re-confirmed against source

2026-08-24

SkellyPings source read directly (client package, server, infra, maintainer scripts, pyprojects); consumer integration verified in FreeMoCap and SkellyCam clones including their CI workflows and lockfiles

More about how these docs are written

# The ingestion server

Environment variables (read at startup in server/main.py):

VariableRequired / DefaultPurpose

SKELLYPINGS_SECRETrequiredShared HMAC secret for signature verification

BACKUP_BUCKETrequiredCloud Storage bucket for JSONL backups

FIRESTORE_COLLECTIONtelemetry_eventsCollection for signature-valid ("verified") events

FIRESTORE_COLLECTION_UNVERIFIEDtelemetry_events_unverifiedCollection for events with missing/invalid signatures

RATE_LIMIT_MAX_REQUESTS60Requests allowed per IP per window

RATE_LIMIT_WINDOW_SECONDS60Sliding-window length in seconds

MAX_EVENTS_PER_REQUEST100Reject larger batches with 413

MAX_BODY_BYTES262144 (256 KiB)Reject larger bodies with 413

Routes:

RouteAuthBehavior

POST /eventsOptional signatureValidates the batch against the TelemetryBatch Pydantic model, writes each event to Firestore (batched writes) with added ingested_at and verified fields. Valid signatures go to the verified collection; missing or invalid ones go to the unverified collection, this captures telemetry from-source/dev builds that lack the production secret. Responds {"stored": N, "verified": bool}.

POST /backupSignature required over the literal bytes "backup"Queries both collections for documents with ingested_at newer than the last run (tracked in a _meta/last_backup document), writes them to backups/{timestamp}_{collection}.jsonl in Cloud Storage (one JSON object per line, plus _firestore_id), and updates the checkpoint. Intended to be triggered by Cloud Scheduler daily at 03:00 UTC.

GET /healthnoneReturns {"status": "ok"}

Abuse and cost protection, from the same file:

- An HTTP middleware runs a thread-safe sliding-window per-IP rate limiter (keyed from X-Forwarded-For) before any route logic, returning 429 without reading the body or touching Firestore. Over-limit IPs are recorded and drained by a background thread every 30 seconds into the verified collection as synthetic rate_limited events shaped like TelemetryEvents (they use the same field names, though the synthetic events omit app_name), so they flow through the same backup pipeline instead of generating one Firestore write per blocked request.

- Oversized uploads are rejected early: a Content-Length pre-check in the middleware, and a body-size check inside /events.

- In-memory rate-limit state is safe here because the service runs a single container (max_instances=1); a container restart resets the counters, which is acceptable since a restart also interrupts any ongoing flood.
