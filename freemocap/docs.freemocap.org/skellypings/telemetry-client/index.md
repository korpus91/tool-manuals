# The telemetry client | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

Full re-read of polyrepo-clones/skellypings (skellypings package init and telemetry_client.py, pyproject.toml, README, server main.py): confirmed constructor parameters and defaults, the eight event fields, the telemetry-flush daemon thread, the 15 minute backoff cap, the events endpoint with a 10 second timeout, X-Telemetry-Signature HMAC-SHA256 signing, the 500 event buffer cap with oldest dropped, the 5 consecutive failure disable cutoff covering both auth errors and generic exceptions while other HTTP statuses keep retrying, and the atexit registered shutdown with a 5 second join

2026-08-24

SkellyPings source read directly (client package, server, infra, maintainer scripts, pyprojects); consumer integration verified in FreeMoCap and SkellyCam clones including their CI workflows and lockfiles

More about how these docs are written

# The telemetry client

```

from pathlib import Path

from skellypings import TelemetryClient

telemetry = TelemetryClient(

    server_url="https://your-cloud-run-url.run.app",

    secret="your-64-char-secret",

    app_name="my_app",

    app_version="1.0.0",

    user_id_file=Path.home() / "my_app_data" / "telemetry_uid",

)

telemetry.track("feature_used", payload={"feature": "export_csv"})

```

Constructor parameters:

ParameterDefaultBehavior

server_urlrequiredBase URL of the Cloud Run service (trailing slash stripped)

secretrequiredShared HMAC secret; never sent over the wire, only used to sign request bodies

app_namerequiredStamped onto every event

app_versionrequiredStamped onto every event

user_id_filerequiredPath where a persistent anonymous ID (a random uuid4().hex) is stored; created on first run and reused afterwards

flush_interval_seconds60.0Maximum time buffered events wait before flushing

flush_batch_size50Flush immediately once this many events are buffered

Behavior, all from telemetry_client.py:

- track(event_type, payload=None) builds an event containing event_type, app_name, app_version, os_platform (platform.system() platform.release()), user_id, timestamp (epoch float), timestamp_iso8601, and payload. Events accumulate under a lock; reaching the batch size triggers an immediate flush.

- Flushing happens on a daemon background thread named telemetry-flush, which sleeps for the interval (with exponential backoff on repeated failures, capped at 15 minutes) and POSTs to {server_url}/events with a 10-second timeout.

- Every request body is signed with HMAC-SHA256 and sent in the X-Telemetry-Signature header.

- Failures never crash the host app, they log warnings. Failed batches are returned to the front of the buffer for retry. If the buffer exceeds 500 events (_MAX_BUFFER_SIZE), the oldest are dropped.

- After 5 consecutive failures (_MAX_CONSECUTIVE_FAILURES), the client permanently disables itself and discards its buffer. Per the code, this cutoff applies to persistent auth errors (HTTP 401/403) and to generic exceptions (network failures); other HTTP error statuses keep retrying, bounded only by the 500-event buffer cap.

- shutdown() flushes remaining events, stops the thread, and joins it (5-second timeout). It is registered with atexit in the constructor automatically, so buffered events survive normal process exit even if the host forgets to call it.
