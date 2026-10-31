# Security model | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

Re-checked every claim against the SkellyPings clone (server/main.py HMAC verification and unverified-collection routing, cloudbuild.yaml allow-unauthenticated and env-var injection, infra/main.tf allUsers invoker binding, telemetry_client.py signing, env.example); consumer secret-injection claims re-verified against the FreeMoCap and SkellyCam installer workflows, their build_info modules, and the telemetry wrappers that import them

2026-08-24

SkellyPings source read directly (client package, server, infra, maintainer scripts, pyprojects); consumer integration verified in FreeMoCap and SkellyCam clones including their CI workflows and lockfiles

More about how these docs are written

# Security model

From the README and mirrored in both codebases:

- The endpoint is publicly reachable (Cloud Run allows unauthenticated invocation), but authenticity comes from an HMAC-SHA256 signature computed over the raw request body using a shared secret, compared with hmac.compare_digest on the server. The secret never crosses the wire, only the digest does, and a valid signature cannot be forged without it. Rotating means changing the SKELLYPINGS_SECRET environment variable on Cloud Run, baking the new value into clients, and recomputing the static signature header on the Cloud Scheduler backup job, which signs the literal string backup.

- The secret is stored as a Cloud Run environment variable, not in any repository.

- Consumers inject their copy at CI build time, but only FreeMoCap does it effectively: its installer workflow writes the SKELLYPINGS_SECRET GitHub secret into freemocap/build_info.py, the module its telemetry wrapper actually imports. SkellyCam's workflow instead writes the secret to skellycam/build_info.py while its wrapper reads skellycam/system/telemetry/build_info.py, so shipped SkellyCam installers still sign with the committed placeholder and their events arrive as unverified regardless of how the secret is configured. Local development uses the placeholder ("not-configured"), which fails verification, so dev events simply land in the unverified collection rather than being rejected.
