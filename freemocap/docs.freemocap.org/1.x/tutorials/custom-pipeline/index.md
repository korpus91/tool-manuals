# Build a custom pipeline | FreeMoCap

Skip to main content

This is documentation for FreeMoCap 1.x (legacy), which is no longer actively maintained.

For up-to-date documentation, see the latest version (2.0 (alpha)).

Version: 1.x (legacy)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-20

freemocap-docs architecture docs (v2.0.0-alpha.21, not yet re-checked against the running app)

More about how these docs are written

# Build a custom pipeline

FreeMoCap's backend runs on two different pipelines, and understanding the difference is the useful starting point before you go looking for where to extend either one.

## Realtime vs. posthoc​

RealtimePosthoc

SourceLive camera feedsVideo files already on disk

PriorityLow latency: the latest frame, dropping stale ones if it falls behindAccuracy: every frame, in order, nothing dropped

Runs forAs long as the cameras are activeUntil the video ends, then stops

SeesOnly the current frameThe whole recording at once

OutputStreamed to the frontend liveWritten to disk, for playback afterward

Both pipelines process data through the same basic shape (a source feeds one or more per-camera nodes, which feed an aggregator node that triangulates and filters), the realtime version is just built for speed under an ongoing camera feed, and the posthoc version is built for completeness against a fixed set of video files. Neither is "better," they're solving different problems: recording live versus reprocessing something you already captured.

## If you want to go further​

The pipeline internals (individual node types, inter-process communication, the filtering chain) aren't documented yet at a level meant for extending them from outside the core freemocap repository. If you want to work at that level, the freemocap repository's own architecture docs are the current source of truth, ahead of anything ported to this site. Image tracking and pose models and the output data model cover the parts of the pipeline that are stable, documented, and safe to build against today.

## Next steps​

- Image tracking and pose models

- The FreeMoCap output data model

- Find and read your output

- Realtime vs. posthoc

- If you want to go further

- Next steps
