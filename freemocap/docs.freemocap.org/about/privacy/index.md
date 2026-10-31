# Privacy policy | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): telemetry.py system fields, telemetry_config.py, SettingsModal.tsx (Privacy section, full checkbox label), welcome screen checkbox ticked by default (seen in the installed app), telemetry_uid and telemetry_config.json created in freemocap_data on first launch (seen on disk). No changes needed.

2026-08-25

SkellyPings telemetry implementation in freemocap v2.0.0-alpha.21 (system/telemetry/telemetry.py, system/telemetry/telemetry_config.py, api/http/telemetry/telemetry_router.py, build_info.py, freemocap-ui SettingsModal.tsx and WelcomeModal.tsx) and the skellypings repo (TelemetryClient and Cloud Run server)

2026-08-19

v1 (ported, not yet re-checked against v2)

More about how these docs are written

# Privacy policy

We respect and value your privacy. This Privacy Policy outlines how we collect, use, and protect any personal or anonymous data we may collect from users of our software. By using our software, you agree to the terms of this Privacy Policy. "We" refers to the FreeMoCap development team, which maintains the FreeMoCap software. "You" refers to the user of our software.

User data helps us understand how we can make our software better for you and allows us to demonstrate to agencies and corporations that people are using our software, which may help us to grow the project in the future.

## Collection of anonymous user data​

Leaving the "Send anonymous usage pings to help improve FreeMoCap" checkbox checked (checked by default, on the welcome screen shown at startup and in the Privacy section of the Settings menu) sends anonymous user data while FreeMoCap runs. That data goes out as batches of "pings" posted over HTTPS to

SkellyPings, a small open source telemetry service running on Google Cloud Run, which stores the pings in Google Firestore and backs them up daily to plain JSON files in Google Cloud Storage.

The data we currently collect includes:

- your IP Address (because each "ping" arrives as an ordinary HTTPS request, we cannot avoid receiving your IP address; the SkellyPings server uses it only to rate-limit abusive traffic)

- The time the "ping" was sent

- A random, anonymous user ID (a randomly generated identifier stored in a telemetry_uid file in your FreeMoCap data folder, so we can count unique users without knowing who they are)

- Anonymous details of your system, sent once per launch: operating system name, version, and release, CPU architecture, Python version, numbers of physical and logical CPU cores, and total RAM

- Which event occurred (for example "app opened," or, during the guided tutorial, which tour steps were viewed or skipped)

- Your FreeMoCap app version

You can view the code that collects this data in the FreeMoCap repository, and the SkellyPings client and server code in the SkellyPings repository.

If you do not wish to share your data, you may turn off "pings" at any point in time. To turn off user pings, clear the "Send anonymous usage pings to help improve FreeMoCap" box in the Privacy section of the Settings menu (or on the welcome screen), and restart FreeMoCap so the backend picks up your choice.

## Protection of user data​

We take the protection of your data seriously. We do not sell or distribute any personal or anonymous data we collect to third parties, except as required by law. We use industry-standard security measures to protect your data from unauthorized access, use, or disclosure. Currently, only core FreeMoCap developers (Jonathan Matthis, and Trenton Wirth) have access to the user data we have collected.

## Your control over your data​

As a user of our software, you have control over your data. You can choose to turn off "pings" at any point in time by unchecking the "Send anonymous usage pings to help improve FreeMoCap" box in the Privacy section of the Settings menu (or on the welcome screen), and restarting FreeMoCap.

If you wish to have your user data deleted, you may contact us at info AT FreeMoCap DOT org.

## Updates to this privacy policy​

We may update this Privacy Policy as our project evolves, so please check back periodically for changes. Continuing to use our software after changes to this Privacy Policy means you accept those changes.

## Contact us​

If you have any questions or concerns about this Privacy Policy or our use of your data, please contact us at info AT FreeMoCap DOT org, or reach out to us on our Discord.

- Collection of anonymous user data

- Protection of user data

- Your control over your data

- Updates to this privacy policy

- Contact us
