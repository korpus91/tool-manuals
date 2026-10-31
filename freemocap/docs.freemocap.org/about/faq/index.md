# Frequently asked questions | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): realtime pipeline and tour text in en-english.json. Shortened the realtime answer to plain English; donation and Discord links checked live. Rest unchanged.

2026-08-25

polyrepo-clones/freemocap (v2.0.0-alpha.21): LICENSE (AGPLv3), README.md (Discord invite, realtime pipeline), freemocap/core/pipeline/realtime/ and api/http/realtime/realtime_router.py (realtime pipeline exists), core/pipeline/realtime/camera_node_config.py (single-person cap), freemocap-docs/docs/architecture/backend-pipeline-architecture.mdx; polyrepo-clones/skellytracker main (multi_person_tracker.py, detector registry); polyrepo-clones/skellyforge main (pipelines/dlc_pipeline.py)

2026-08-19

v1 (ported, not yet re-checked against v2)

More about how these docs are written

# Frequently asked questions

## How is FreeMoCap free?​

FreeMoCap is completely free to use, but its also free in the sense of "freedom." You have the freedom to use FreeMoCap how you like, including copying, modifying, and redistributing the code.

For more information on free software, see this article from the GNU Operating System, What is Free Software?

And this classic essay - Why Open Source Misses the Point of Free Software

FreeMoCap is funded through external grants, and donations from users like you. If you would like to donate to FreeMoCap, please visit our donations page.

## What license does FreeMoCap use?​

FreeMoCap is licensed with the GNU Affero General Public License (v3), the most aggressively open source license available.

If you wish to work with FreeMoCap in a way not supported by the AGPLv3, please reach out to us at info AT freemocap DOT org, and we can discuss alternative licensing options.

## How can I contribute to FreeMoCap?​

We accept contributions of all kinds and sizes.

For contributions related to code or documentation, see our contributing page.

We also greatly appreciate anyone who helps answer questions on our Discord.

We also greatly appreciate financial contributions of any size, although the software is entirely free, now and permanently. You can donate through various platforms on our donations page.

## Does FreeMoCap work in realtime?​

Yes. While your cameras are streaming, FreeMoCap can track and display a 3D skeleton live. For the most accurate data, it also processes each recording after it's made.

## Can FreeMoCap track multiple people at once?​

Not yet. FreeMoCap currently only tracks one person at a time, but we are working on adding multi-person tracking capability.

## Can I track things that are not humans?​

Not yet. FreeMoCap currently only tracks humans. We have done some proof-of-concept projects using DeepLabCut and are currently working towards making this part of our standard pipeline.

- How is FreeMoCap free?

- What license does FreeMoCap use?

- How can I contribute to FreeMoCap?

- Does FreeMoCap work in realtime?

- Can FreeMoCap track multiple people at once?

- Can I track things that are not humans?
