# WebSocket API | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): websocket_connect.py (/websocket/connect), websocket_server.py (300-frame backpressure warning and reset thresholds), freemocap-docs architecture/backend-websocket-server.mdx still present. No changes needed.

2026-08-25

freemocap v2.0.0-alpha.21 websocket source (api/websocket/websocket_server.py, websocket_connect.py, websocket_message_types.py, binary_keypoints_protocol.py, api/routers.py, app/app.py, api/server_constants.py), freemocap-ui ServerContextProvider.tsx and websocket-connection.ts, and freemocap-docs backend-websocket-server.mdx and api-boundary.mdx

2026-08-21

freemocap-docs architecture docs (v2.0.0-alpha.21, not yet re-checked against the running app)

More about how these docs are written

# WebSocket API

Alongside the REST API, FreeMoCap's backend keeps a single persistent websocket connection open (ws://localhost:53117/websocket/connect) for everything that needs to stream continuously: camera frames, live keypoints, logs, and processing progress. Like the REST API, this is the internal contract between the bundled frontend and backend, not a stable public interface.

## What flows over it​

DirectionMessageCarries

Server → clientFrame dataBinary JPEG frames per camera, plus keypoints, sent every processed frame

Server → clientframerate updatesbackend and frontend FPS, a few times a second

Server → clientPipeline progressPost-hoc calibration/mocap processing status

Server → clientLog recordsbackend log lines, for the in-app log viewer

Server → clientTracker schema handshakekeypoint names and connections for the active trackers, sent once on connect

Server → clientApp stateapp-state snapshot, sent on connect and again whenever the state changes

Client → serverFrame acknowledgmentConfirms a frame was received, see below

## Why acknowledgment matters​

The backend can produce frames faster than a client can render them. Each frame batch is tagged with a number, and the client sends that number back as soon as it receives it (well before it finishes decoding the frames); the backend won't send the next batch until it gets that acknowledgment. If a client falls 300 frames behind, the backend stops waiting and resets its counter instead of stalling forever. If you're writing your own client against this connection, skipping the acknowledgment message is the most common way to end up with a connection that appears to hang after the first few hundred frames.

## If you actually need to build against this​

The full binary frame protocol (exact byte layout), every message type, and the reconnection/heartbeat behavior are documented in the freemocap repository's own architecture docs (websocket Server). That's the version worth trusting, this protocol is still evolving and a page ported here would go stale faster than the source does.

## Next steps​

- REST API

- Recording folder structure

- What flows over it

- Why acknowledgment matters

- If you actually need to build against this

- Next steps
