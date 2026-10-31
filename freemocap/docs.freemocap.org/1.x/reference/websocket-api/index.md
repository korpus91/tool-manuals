# WebSocket API | FreeMoCap

Skip to main content

This is documentation for FreeMoCap 1.x (legacy), which is no longer actively maintained.

For up-to-date documentation, see the latest version (2.0 (alpha)).

Version: 1.x (legacy)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-21

freemocap-docs architecture docs (v2.0.0-alpha.21, not yet re-checked against the running app)

More about how these docs are written

# WebSocket API

Alongside the REST API, FreeMoCap's backend keeps a single persistent WebSocket connection open (ws://localhost:53117/websocket/connect) for everything that needs to stream continuously: camera frames, live keypoints, logs, and processing progress. Like the REST API, this is the internal contract between the bundled frontend and backend, not a stable public interface.

## What flows over it​

DirectionMessageCarries

Server → clientFrame dataBinary JPEG frames per camera, plus keypoints, sent every processed frame

Server → clientFramerate updatesBackend and frontend FPS, a few times a second

Server → clientPipeline progressPost-hoc calibration/mocap processing status

Server → clientLog recordsBackend log lines, for the in-app log viewer

Client → serverFrame acknowledgmentConfirms a frame was received, see below

## Why acknowledgment matters​

The backend can produce frames faster than a client can render them. Each frame is tagged with a number, and the client sends that number back once it's processed it; the backend won't send the next frame until it gets that acknowledgment. If you're writing your own client against this connection, skipping the acknowledgment message is the most common way to end up with a connection that appears to hang after the first few frames.

## If you actually need to build against this​

The full binary frame protocol (exact byte layout), every message type, and the reconnection/heartbeat behavior are documented in the freemocap repository's own architecture docs (WebSocket Server). That's the version worth trusting, this protocol is still evolving and a page ported here would go stale faster than the source does.

## Next steps​

- REST API

- Recording folder structure

- What flows over it

- Why acknowledgment matters

- If you actually need to build against this

- Next steps
