# Deployment | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

SkellyPings source re-read directly (README.md, cloudbuild.yaml, infra/main.tf, infra/ directory listing); resource specs, service names, region defaults, env vars, scheduler config, and billing guidance independently re-verified

2026-08-24

SkellyPings source read directly (client package, server, infra, maintainer scripts, pyprojects); consumer integration verified in FreeMoCap and SkellyCam clones including their CI workflows and lockfiles

More about how these docs are written

# Deployment

The README documents three interchangeable setup paths, gcloud CLI, GCP web console, and Terraform, all producing the same resources: a Cloud Run service (256 MiB, 1 CPU, min 0 / max 1 instances, unauthenticated invocations), a native-mode Firestore database, a Cloud Storage backup bucket, and a Cloud Scheduler job hitting /backup daily at 03:00 UTC with an OIDC token. Notable repo-specific details:

- cloudbuild.yaml builds server/Dockerfile and deploys a Cloud Run service named skellypings in region northamerica-northeast1, setting SKELLYPINGS_SECRET and BACKUP_BUCKET from substitutions plus a hardcoded FIRESTORE_COLLECTION=telemetry_events. (The Terraform config and the README's CLI walkthrough instead name the service telemetry.)

- infra/main.tf provisions the Firestore database, a backup bucket with a lifecycle rule deleting objects after 365 days, the Cloud Run service definition with a placeholder image (the real container is deployed afterward via Cloud Build's GitHub integration or gcloud run deploy), the scheduler service account, and the daily job. The scheduler's X-Telemetry-Signature header cannot be computed at plan time. It must be set manually after deploy, as spelled out in the README's Option C steps and the scheduler_signature_command output.

- Billing guidance in the README: the design targets $0/month within GCP free tiers; capping Cloud Run at one instance bounds compute cost, but Google bills rather than hard-stops past free limits, so budget alerts are recommended.
